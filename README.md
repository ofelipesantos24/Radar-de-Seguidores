# 📡 Radar de Seguidores

Um app web (front-end puro, sem backend) que ajuda a descobrir **quem deixou de te seguir**, quem são seus **novos seguidores** e quem **não te segue de volta** — comparando snapshots das suas listas de seguidores/seguindo ao longo do tempo.

Todos os dados ficam salvos apenas no `localStorage` do seu navegador. Nada é enviado para nenhum servidor.

## Por que não é 100% automático?

Instagram, TikTok, X etc. não oferecem uma API pública gratuita para monitorar seguidores em tempo real sem login. Por isso o app funciona por **snapshots**: a cada vez que você importa sua lista atual, ele compara com a última importada e mostra o que mudou. Quanto mais frequente a importação, mais preciso o histórico.

## Funcionalidades

- Importação via **arquivo JSON exportado do Instagram** (`followers_1.json` e `following.json`)
- Importação **manual** (colar listas de usuários, uma por linha) — funciona para qualquer rede social
- Comparação automática entre o snapshot atual e o anterior:
  - **Deixaram de te seguir**
  - **Novos seguidores**
  - **Não seguem de volta** (quem você segue e não te segue)
- Histórico de todos os snapshots salvos
- Exportação de listas em `.txt`
- Backup/restauração completa dos dados em `.json`

## Como usar

### Opção 1 — Instagram (recomendado)

1. No Instagram: **Configurações → Central de Contas → Suas informações e permissões → Baixar suas informações**
2. Escolha o formato **JSON** e selecione ao menos "Seguidores e seguindo"
3. Abra o `.zip` recebido por e-mail e localize `followers_1.json` e `following.json`
4. No app, envie os dois arquivos na aba **Instagram (.json)** e clique em **Analisar**
5. Repita esse processo periodicamente (ex.: semanalmente) para acompanhar mudanças

### Opção 2 — Lista manual

Use a aba **Lista manual** para colar, um usuário por linha, sua lista de seguidores e/ou seguindo. Útil para outras redes ou para testar o app rapidamente.

### Backup

Como os dados ficam só no navegador (não sincronizam entre aparelhos ou sobrevivem a "limpar dados do site"), use **Exportar backup** regularmente e **Importar backup** para restaurar o histórico quando precisar.

## Estrutura do projeto

```
.
├── index.html   # aplicação completa (HTML + CSS + JS, sem dependências externas de build)
└── README.md    # este arquivo
```

## Tecnologia

- HTML, CSS e JavaScript puro (nenhum framework, nenhuma etapa de build)
- Fonte via Google Fonts (Roboto Slab)
- Persistência via `localStorage` do navegador

## Rodando localmente

Basta abrir `index.html` em qualquer navegador moderno. Para hospedar publicamente, envie os dois arquivos para GitHub Pages, Netlify, Vercel ou qualquer hospedagem estática.

## Privacidade

O app não faz nenhuma chamada de rede além de carregar a fonte do Google Fonts. Suas listas de seguidores nunca saem do seu navegador.

## Limitações conhecidas

- Não monitora em tempo real — depende de você importar novos snapshots
- O formato do arquivo exportado pelo Instagram pode mudar sem aviso; se a importação falhar, use a opção manual
- Os dados são armazenados por navegador/dispositivo; use o backup para não perdê-los
