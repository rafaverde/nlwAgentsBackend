# NLW Agents

Este projeto foi desenvolvido durante o evento NLW da Rocketseat.

## Tecnologias e Bibliotecas Utilizadas
- **Node.js** (runtime)
- **TypeScript** (tipagem estática)
- **Fastify** (framework web)
- **@fastify/cors** (CORS middleware)
- **Zod** (validação de esquemas)
- **fastify-type-provider-zod** (integração Zod + Fastify)
- **Drizzle ORM** (ORM para PostgreSQL)
- **drizzle-kit** (migrations)
- **drizzle-seed** (seed de dados)
- **PostgreSQL** (banco de dados)
- **pgvector** (extensão para vetores no PostgreSQL)

## Padrões e Organização
- Organização por responsabilidade: `src/http/routes`, `src/db/schema`, `src/db/connection`.
- Validação de dados e tipagem forte com Zod.
- Migrations e seeds automatizados com Drizzle.
- Variáveis de ambiente tipadas.

## Setup do Projeto

### 1. Clone o repositório
```bash
git clone <repo-url>
cd nlwAgents/server
```

### 2. Instale as dependências
```bash
npm install
```

### 3. Configure o banco de dados
Utilize o Docker Compose para subir o PostgreSQL já com a extensão pgvector:
```bash
docker-compose up -d
```

As credenciais padrão estão em `docker-compose.yml`:
- Usuário: `docker`
- Senha: `docker`
- Banco: `agents`
- Porta: `5432`

### 4. Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto com:
```
DATABASE_URL=postgresql://docker:docker@localhost:5432/agents
PORT=3333
```

### 5. Rode as migrations e o seed
```bash
# (Opcional) Gere as migrations com drizzle-kit, se necessário
npx drizzle-kit migrate

# Popule o banco com dados iniciais
npm run db:seed
```

### 6. Inicie o servidor
```bash
npm run dev
```

O servidor estará disponível em `http://localhost:3333`.

## Endpoints Principais
- `GET /health` — Health check
- `GET /rooms` — Lista as salas cadastradas

## Estrutura da Tabela `rooms`
- `id` (uuid, PK)
- `name` (texto, obrigatório)
- `description` (texto)
- `created_at` (timestamp)

---

Desenvolvido com 💜 durante o NLW Agents da [Rocketseat](https://rocketseat.com.br)