## O Sorriso em Jogo

## Índice

- [Introdução](#introdução)  
- [Explicação do Problema](#explicação-do-problema)  
- [Alternativas de Solução](#alternativas-de-solução)  
  - [3.1. Análise de Imagens para Detecção de Cáries](#31-análise-de-imagens-para-detecção-de-cáries)  
  - [3.2. Sistema RAG Multimodal](#32-sistema-rag-multimodal)  
- [Ferramentas e Bibliotecas](#ferramentas-e-bibliotecas)  
- [Conceitos e Técnicas Implementadas](#conceitos-e-técnicas-implementadas)  
- [Implementação na Sprint 4](#implementação-na-sprint-4)  
  - [6.1. Alterações Principais](#61-alterações-principais)  
  - [6.2. Funcionalidades da Versão Beta](#62-funcionalidades-da-versão-beta)  
- [Demonstração](#demonstração)  
- [Repositório](#repositório)  

## Introdução

**O Sorriso em Jogo** é um protótipo de aplicação web voltada para a **OdontoPrev**, focada em monitoramento preventivo da saúde bucal. Desenvolvida em **Streamlit**, esta versão demonstra duas principais funcionalidades:

1. Registro de prontuários odontológicos.  
2. Detecção de cáries em imagens enviadas pelos usuários.  
3. Consulta multimodal via sistema RAG (texto e imagem).  

## Explicação do Problema

Pacientes frequentemente só procuram o dentista quando há dor ou agravamento de problemas bucais, o que gera custos maiores e reduz eficácia dos tratamentos. Operadoras de convênio enfrentam sinistralidade elevada e dificuldade de engajamento. Este protótipo busca incentivar monitoramento regular e fornecer insights rápidos tanto para usuários quanto para dentistas.

## Alternativas de Solução

### 3.1. Análise de Imagens para Detecção de Cáries

- O usuário envia uma foto da região bucal.  
- Um modelo **YOLO** pré-treinado identifica áreas suspeitas de cárie.  
- Resultados são exibidos no próprio navegador e, se houver detecções, os recortes anotados são armazenados.  

### 3.2. Sistema RAG Multimodal

- Prontuários e embeddings de imagem/texto são indexados via **FAISS**.  
- Consultas de texto aproveitam um modelo de linguagem para respostas contextuais.  
- Perguntas com indicação de análise de imagem disparam um prompt multimodal ao **GPT-4o-mini**, retornando diagnóstico baseado na foto armazenada.  

## Ferramentas e Bibliotecas

- **Streamlit**: Interface web interativa.  
- **Pillow (PIL)**: Processamento básico de imagens.  
- **Ultralytics YOLO**: Detecção de objetos (cáries).  
- **FAISS**: Índice vetorial para buscas semânticas.  
- **SentenceTransformers**: Geração de embeddings de texto (`all-MiniLM-L6-v2`) e de imagem (`clip-ViT-B-32`).  
- **OpenAI API**: Geração de respostas via ChatGPT (modelos `gpt-3.5-turbo` e `gpt-4o-mini`).  
- **dotenv**: Carregamento de variáveis de ambiente.  

## Conceitos e Técnicas Implementadas

- **Detecção de Anomalias com YOLO**: Identificação de possíveis cáries em imagens 2D.  
- **Embeddings e Busca Semântica**: Conversão de prontuários e imagens em vetores, facilitando recuperação de informações.  
- **RAG (Retrieval-Augmented Generation)**: Combinação de contexto semântico com geração de linguagem para respostas específicas.  

## Implementação na Sprint 4

### 6.1. Alterações Principais

- Aprimoramento do modelo Yolo, conseguindo agora detectar cavidades e dentes quebrados além das cáries.
- Simplificação do pipeline de imagens usando **Pillow** ao invés de OpenCV.  
- Remoção de componentes não utilizados (Cross-Encoder, AutoEncoders, LangChain, gamificação mobile).  

### 6.2. Funcionalidades

- Formulário para cadastro de dados pessoais e histórico médico.  
- Upload de foto bucal com detecção automática de cáries.  
- Armazenamento de prontuários e imagens anotadas em índices FAISS.  
- Consulta ao sistema RAG via texto ou multimodal.  

## Demonstração

Vídeo: https://youtu.be/JwB65k8M5Ao  

## Repositório

Código-fonte: https://github.com/rafaelnxd/IoT-Sprint04  
