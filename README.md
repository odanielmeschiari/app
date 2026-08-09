# SuperVest — PWA

Este pacote contém tudo o que é necessário para publicar o SuperVest como um
Progressive Web App (PWA) instalável no celular ou computador.

## Conteúdo do pacote

- `index.html` — o app em si
- `manifest.json` — metadados do PWA (nome, cores, ícones)
- `sw.js` — service worker (permite uso offline e cache do app)
- `icon-16.png`, `icon-32.png`, `favicon.ico` — ícones de aba do navegador
- `icon-180.png` — ícone para tela inicial do iOS (apple-touch-icon)
- `icon-192.png`, `icon-256.png`, `icon-384.png`, `icon-512.png` — ícones do Android/desktop
- `icon-512-maskable.png` — versão "maskable" (com margem de segurança), usada pelo Android para recortar em formatos variados (círculo, quadrado arredondado, etc.)

## Como publicar

Um PWA **precisa ser servido via HTTPS** (ou `localhost` durante testes) para o
service worker e a instalação funcionarem — abrir o `index.html` direto do
disco (`file://`) não é suficiente.

Formas simples e gratuitas de publicar:

1. **GitHub Pages**: crie um repositório, suba todos os arquivos desta pasta
   na raiz, ative o GitHub Pages nas configurações do repositório.
2. **Netlify / Vercel**: arraste esta pasta inteira para o painel de deploy
   (drag-and-drop) — ambos servem HTTPS automaticamente.
3. **Cloudflare Pages**: mesma ideia, upload direto da pasta.

Importante: todos os arquivos devem ficar **na mesma pasta/nível**, exatamente
como estão aqui, pois o `index.html` referencia `manifest.json`, `sw.js` e os
ícones com caminhos relativos (ex.: `icon-192.png`, não `/icon-192.png`).

## Como instalar no celular depois de publicado

- **Android (Chrome)**: abra o site publicado → menu (⋮) → "Adicionar à tela
  inicial" / "Instalar app".
- **iPhone (Safari)**: abra o site publicado → botão de compartilhar →
  "Adicionar à Tela de Início".
- **Desktop (Chrome/Edge)**: abra o site → ícone de instalação na barra de
  endereço → "Instalar".

## Observações

- O app salva os dados localmente no dispositivo (`localStorage`), então cada
  instalação/navegador tem seus próprios dados. Use a função de backup dentro
  do app (aba Ajustes) para exportar/importar entre dispositivos.
- Se você atualizar o `index.html` no futuro, é recomendável trocar o nome
  `CACHE_NAME` dentro de `sw.js` (ex.: de `supervest-cache-v1` para `v2`) para
  forçar os usuários a receberem a versão nova em vez da versão em cache.
