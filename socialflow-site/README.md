# SocialFlow

Site estático do SocialFlow, pronto para GitHub + Cloudflare Pages. Não precisa de build.

## Estrutura

```
index.html          página única (o site inteiro é renderizado por js/app.js)
css/style.css       todos os estilos
js/app.js           toda a lógica, páginas e navegação (rotas por #hash)
assets/img/crown.png  logo (coroa)
```

As páginas (#servicos, #novo-pedido, #adicionar-saldo, #updates etc.) não são arquivos HTML
separados: o site é uma aplicação de página única e a navegação é feita por `#hash`.
Por isso o único HTML é o `index.html`.

## Publicar na Cloudflare Pages (via GitHub)

1. Crie um repositório no GitHub e envie **o conteúdo desta pasta** (o `index.html` precisa ficar na raiz do repositório).
2. Na Cloudflare: **Workers & Pages → Create → Pages → Connect to Git** e escolha o repositório.
3. Configuração do build:
   - Framework preset: **None**
   - Build command: *(deixe vazio)*
   - Build output directory: `/` (raiz)
4. **Save and Deploy**. A cada `git push` o site é atualizado.

## Testar localmente

```
python3 -m http.server 8000
```
Abra http://localhost:8000 (abrir o `index.html` direto com duplo clique pode bloquear o logo 3D).

## Observações

- **Bibliotecas externas:** o three.js (logo 3D) e o qrcodejs são carregados do cdnjs.cloudflare.com,
  e as fontes Inter e JetBrains Mono, do Google Fonts. Funcionam normalmente na Cloudflare Pages,
  mas exigem internet. Para hospedar tudo localmente, baixe os arquivos para `js/vendor/` e troque as tags em `index.html`.
- **Dados:** contas, pedidos e saldo ficam no `localStorage` do navegador de cada visitante (não há servidor/banco de dados).
- **Recursos do claude.ai:** o código tenta usar banco compartilhado e IA do ambiente do claude.ai (`window.claude`).
  Fora de lá esses recursos não existem e o site usa o comportamento alternativo (por exemplo, o chat responde com respostas locais).
