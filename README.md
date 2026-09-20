# Valor Log — Tempos de Operação

App web de controle de tempos de operação em doca (chegada, carregamento,
liberação/expedição de veículos), usado pelo time de armazém da Valorlog.

## Como isso é publicado

Este repositório está ligado ao site `valorlog-tempos-operacao` no Netlify
por **deploy contínuo**: sempre que o arquivo `site/index.html` muda aqui no
GitHub, o Netlify publica a nova versão sozinho, em cerca de 1 minuto — sem
precisar baixar zip nem arrastar nada no painel do Netlify.

- **App em produção**: http://valorlog-tempos-operacao.netlify.app
- **Publish directory** configurado no Netlify: `site`
- Não tem build (é um app de arquivo único, sem framework) — o Netlify só
  publica o conteúdo da pasta `site/` como está.

## Estrutura

```
site/
  index.html               ← o app inteiro (HTML+CSS+JS num arquivo só).
                              É ESTE arquivo que o Netlify publica.
cloud-function-contagem/    ← backend opcional (Cloud Function no Firebase)
                              que faz a contagem de caixas por câmera via IA.
                              NÃO é publicado pelo Netlify (fica fora da
                              pasta site/) — o deploy dele é separado, veja
                              cloud-function-contagem/LEIA-ME.md.
netlify.toml                ← diz ao Netlify pra publicar a pasta site/
```

## Como atualizar o app

Toda vez que o Claude entregar um novo `index.html`:

1. Neste repositório no GitHub, entre na pasta `site/`.
2. Clique no arquivo `index.html` → ícone de lápis (editar) → ou use
   "Add file > Upload files" arrastando o novo arquivo para substituir o
   antigo.
3. Confirme o commit ("Commit changes").
4. Pronto — o Netlify detecta a mudança e publica sozinho. Acompanhe em
   Netlify > Deploys (leva ~1 minuto).

Não precisa mexer em mais nada: nem no painel do Netlify, nem baixar zip.

## Sobre o backend de contagem por câmera

A pasta `cloud-function-contagem/` fica versionada aqui, mas o deploy dela
é manual e separado (ela roda no Firebase, não no Netlify) — siga
`cloud-function-contagem/LEIA-ME.md` quando quiser ativar a contagem
automática de caixas por IA no app.
