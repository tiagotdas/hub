# Central Operacional Contábil — Hub & Cofre de Clientes

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-10b981?style=for-the-badge&logo=github)](https://www.produtocontabil.com.br/hub/)
[![Architecture](https://img.shields.io/badge/Arquitetura-100%25%20Client--Side-3b82f6?style=for-the-badge)](#arquitetura-e-segurança)
[![Crypto](https://img.shields.io/badge/Criptografia-AES--256--GCM%20%2B%20PBKDF2-8b5cf6?style=for-the-badge)](#segurança-e-privacidade)
[![Offline](https://img.shields.io/badge/Offline--First-localStorage-f59e0b?style=for-the-badge)](#execução-local)

> **Aplicação web single-file (zero-backend) projetada para a rotina operacional de escritórios e profissionais de contabilidade.** Centralize CNPJs, CPFs de sócios, inscrições, códigos de acesso, senhas de portais, certificados digitais e parâmetros fiscais/DP em um único lugar com cópia em 1 clique.

🔗 **Acesse a aplicação ao vivo:** [https://www.produtocontabil.com.br/hub/](https://www.produtocontabil.com.br/hub/) *(espelho GitHub Pages: `https://tiagotdas.github.io/hub/`)*

---

## 🎯 O Problema Resolvido

Na operação diária de serviços contábeis, informações críticas dos clientes costumam ficar espalhadas entre planilhas antigas, blocos de notas, e-mails, mensagens de WhatsApp e pastas de contratos sociais. Isso gera perda de tempo e retrabalho toda vez que é preciso acessar o **e-CAC**, **PGDAS-D**, **Prefeituras (NFS-e)**, **SEFAZ**, **FGTS Digital** ou **eSocial**.

A **Central Operacional Contábil** resolve essa fragmentação reunindo todos os dados essenciais em uma interface única **Master-Detail**, otimizada para **localização instantânea e cópia rápida sem pontuação** (ou formatada).

---

## ✨ Principais Funcionalidades

### 1. Painel Operacional 360° (Master-Detail)
- **Filtros rápidos** por regime tributário (`Simples Nacional`, `Lucro Presumido`, `Lucro Real`, `MEI`, `PF / Autônomo`, `Imune/Isenta`), status operacional (`Ativo`, `Em Constituição`, `Paralisado`, `Baixado`) e favoritos (`⭐`).
- **Busca global instantânea (`Ctrl + K` ou `/`)**: pesquisa em tempo real por Razão Social, Nome Fantasia, Código Interno (sistema contábil), CNPJ/CPF (com ou sem pontuação), Inscrição Estadual/Municipal, tags, nome/CPF de sócios, portais e certificados — indicando exatamente onde o termo foi encontrado.
- **Barra de Cópia Ultra-Rápida (1 clique)**:
  - `CNPJ / CPF` em modo **Só Números** ou **Formatado** (com seletor global no cabeçalho).
  - `Inscrição Estadual (IE)` (limpa ou original) e `Inscrição Municipal (IM / CCM)`.
  - `Código de Acesso do Simples Nacional` e `Código de Acesso e-CAC`.
  - `NIRE`, `CNAE Principal`, e-mail, telefone e caminho da pasta do cliente.

### 2. Cofre Geral de Senhas e Portais
- Armazenamento organizado por cliente e visão consolidada global filtrável por categoria:
  - `Prefeitura / NFS-e`, `SEFAZ / Estadual`, `Gov.br`, `e-CAC`, `Simples Nacional`, `FGTS Digital / Conectividade`, `eSocial`, `Junta Comercial`, `Sistema / ERP`, `Banco` e `Outro`.
- Link clicável direto para abrir o portal, exibição controlada (`Ver / Ocultar`), cópia individual de usuário, senha e código auxiliar/2FA.

### 3. Radar de Certificados Digitais & Procurações
- Cadastro de `e-CNPJ A1`, `e-CNPJ A3`, `e-CPF A1`, `e-CPF A3`, `Procuração e-CAC`, `Procuração FGTS Digital` e `Procuração SEFAZ`.
- **Monitoramento automático de vencimentos** ordenado por urgência:
  - 🔴 **Vencidos**
  - 🟡 **Vencem em até 30 dias**
  - 🔵 **Vencem em 31–60 dias**
  - 🟢 **Vigentes (+60 dias)**
- Cópia em 1 clique de **PIN**, **PUK** e CNPJ/CPF do titular diretamente no radar.

### 4. Quadro Societário & Responsáveis Legais (CPF)
- Registro completo por sócio/titular: qualificação, participação societária, CPF (limpo e formatado), data de nascimento, senha e nível do **Gov.br** (`Ouro`, `Prata`, `Bronze`), número do último **Recibo IRPF**, Título de Eleitor e RG.

### 5. Parâmetros Fiscais, DP, Campos Extras & Notas
- Resumo de Folha/DP (`Possui Funcionários`, `Dia Fechamento Folha`, `FAP`, `RAT`, `FPAS`, `Sindicato`) e Fiscal (`Alíquota ISS`, `Sistema ERP`, `Bancos`).
- **Campos Personalizados (Snippets)**: adicione qualquer par chave-valor (ex.: código DTE, inscrição SUFRAMA, chave API) com opção de marcá-lo como dado sigiloso.
- **Observações Operacionais** com salvamento automático enquanto você digita.

### 6. Captura Rápida Inteligente (Colar Texto Solto)
- Cole qualquer texto bruto copiado de e-mail, WhatsApp, contrato social ou ficha cadastral.
- O analisador extrai automaticamente **CNPJs, CPFs, IEs, IMs, códigos do Simples/e-CAC, e-mails, telefones, datas e possíveis senhas/PINs**, permitindo:
  - Criar um **Novo Cliente** já pré-preenchido com os dados detectados; ou
  - **Anexar** o texto às observações de um cliente existente.

---

## 🔒 Arquitetura e Segurança

### Zero-Backend & Isolamento Local
- A aplicação é **100% client-side** (um único arquivo HTML autossuficiente, sem bibliotecas externas obrigatórias e sem servidor backend).
- **Nenhum dado de cliente trafega pela rede**: todas as informações permanecem exclusivamente no `localStorage` do seu navegador na máquina local.

### Segurança e Privacidade
- **Criptografia Opcional com Senha Mestra (`AES-256-GCM`)**:
  - Ao configurar uma Senha Mestra em **Proteger Cofre**, todo o estado da aplicação passa a ser criptografado antes de ser gravado no `localStorage` usando a **Web Crypto API** nativa do navegador (`PBKDF2` com `SHA-256`, 150.000 iterações e salt aleatório de 16 bytes + `AES-GCM` de 256 bits com IV de 12 bytes).
  - Permite bloquear a tela imediatamente (`Alt + L`).
- **Modo Privacidade / Desfoque (`Alt + P`)**:
  - Aplica `filter: blur(5px)` em documentos, senhas e dados sensíveis visíveis na tela — ideal para calls, atendimentos presenciais ou acesso remoto, mantendo os botões de **Copiar** operacionais em 1 clique.
- **Tema Claro e Escuro**: alternância rápida no cabeçalho com persistência automática.

> **Importante sobre isolamento por origem:** o `localStorage` do navegador é isolado por domínio/origem. Dados cadastrados ao abrir o arquivo localmente (`file://`) não aparecem automaticamente na URL publicada (`https://www.produtocontabil.com.br/hub/`). Para transferir sua base entre dispositivos ou origens, utilize o recurso de **Backup JSON**.

---

## ⌨️ Atalhos de Teclado

| Atalho | Ação |
| :--- | :--- |
| `Ctrl + K` ou `/` | Focar na busca global instantânea |
| `Alt + P` | Ativar / desativar o Modo Privacidade (Blur) |
| `Alt + L` | Bloquear o cofre (ou abrir configurações de Senha Mestra) |
| `Esc` | Fechar modais abertos |

---

## 💾 Backup e Portabilidade

No menu **Backup**, você conta com:
- **Baixar Backup Completo (.json)**: exporta toda a base (clientes, sócios, credenciais, certificados, notas e configurações) para armazenamento seguro em nuvem (Google Drive, OneDrive) ou servidor interno.
- **Restaurar / Importar (.json)**: restaura integralmente um backup em qualquer navegador ou computador.
- **Exportar Resumo de Clientes (.csv)**: gera planilha compatível com Excel/Google Sheets (UTF-8 com BOM, separada por `;`) contendo código interno, razão social, documento, regime, inscrições e contatos.

---

## 🚀 Execução Local

Como não há dependências externas ou processo de build, você pode rodar a ferramenta localmente em segundos:

1. Clone este repositório ou baixe o arquivo [`index.html`](./index.html):
   ```bash
   git clone https://github.com/tiagotdas/hub.git
   ```
2. Abra o arquivo `index.html` diretamente no seu navegador (Google Chrome, Microsoft Edge, Firefox, etc.).

*(Opcional)* Para servir via servidor HTTP local:
```bash
npx serve .
```

---

## 🛠️ Tecnologias Utilizadas

- **HTML5** semântico em arquitetura single-file
- **CSS3** moderno (Custom Properties, Flexbox, CSS Grid, temas Dark/Light)
- **JavaScript (ES6+)** Vanilla puro
- **Web Storage API** (`localStorage`)
- **Web Crypto API** (`PBKDF2` + `AES-256-GCM`)
- **Clipboard API** com fallback automático para ambientes `file://`

---

## ⚠️ Boas Práticas Recomendadas

1. **Faça backups `.json` regulares**, pois limpar o cache/dados do site no navegador apaga o `localStorage`.
2. **Ative a Senha Mestra** caso utilize a ferramenta em computadores compartilhados.
3. **Nunca armazene dados reais de clientes neste repositório GitHub** — mantenha o repositório apenas com o código-fonte da interface.
