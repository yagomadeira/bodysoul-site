# Body & Soul Fitness — Site + Painel Admin

## Estrutura do projeto
```
bodysoul/
├── index.html          ← Site principal
├── admin.html          ← Painel administrativo
├── images/             ← Fotos e logo
│   ├── logo-bodysoul.png
│   ├── fachada.jpeg
│   ├── recepcao.jpeg
│   ├── interior-1.jpeg
│   ├── ... (demais fotos)
└── README.md           ← Este arquivo
```

---

## 1. Configurar o Firebase (banco de dados gratuito)

### Passo 1 — Criar projeto no Firebase
1. Acesse [console.firebase.google.com](https://console.firebase.google.com/)
2. Clique em **"Adicionar projeto"**
3. Nome: `bodysoul-site` → Avançar
4. Desmarque Google Analytics (não precisa) → **Criar projeto**

### Passo 2 — Criar o banco de dados
1. No menu lateral, clique em **"Realtime Database"**
2. Clique em **"Criar banco de dados"**
3. Localização: `us-central1` (ou a mais próxima)
4. Selecione **"Iniciar no modo de teste"** → Ativar
5. **IMPORTANTE:** Após ativar, clique na aba **"Regras"** e cole:
```json
{
  "rules": {
    "site": {
      ".read": true,
      ".write": "auth != null || true"
    }
  }
}
```
   → Clique em **Publicar**

### Passo 3 — Pegar as credenciais
1. Clique na engrenagem ⚙️ → **Configurações do projeto**
2. Role até **"Seus apps"** → clique no ícone **Web** `</>`
3. Apelido: `bodysoul-web` → Registrar app
4. Copie o objeto `firebaseConfig` que aparece

### Passo 4 — Colar no código
Abra **ambos** os arquivos e substitua o bloco `firebaseConfig`:
- `index.html` (linha ~607, procure por `COLE_AQUI`)
- `admin.html` (linha ~220, procure por `COLE_AQUI`)

Exemplo de como vai ficar:
```javascript
const firebaseConfig = {
  apiKey: "AIzaSyB...",
  authDomain: "bodysoul-site.firebaseapp.com",
  databaseURL: "https://bodysoul-site-default-rtdb.firebaseio.com",
  projectId: "bodysoul-site",
  storageBucket: "bodysoul-site.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc..."
};
```

### Passo 5 — Trocar a senha do admin
No arquivo `admin.html`, procure a linha:
```javascript
const ADMIN_PASSWORD = "bodysoul2026";
```
Troque `"bodysoul2026"` pela senha que o Eduardo quiser.

---

## 2. Hospedar no Vercel (gratuito)

### Passo 1 — Criar conta no Vercel
1. Acesse [vercel.com](https://vercel.com)
2. Clique em **Sign Up** → entre com GitHub, GitLab ou email

### Passo 2 — Subir o projeto pelo GitHub (recomendado)
1. Crie uma conta no [github.com](https://github.com) (se não tiver)
2. Crie um novo repositório: `bodysoul-site`
3. Faça upload de toda a pasta `bodysoul/` para o repositório
4. No Vercel, clique em **"Add New Project"**
5. Conecte seu GitHub → selecione o repositório `bodysoul-site`
6. Clique em **Deploy** — pronto, o site já está no ar!

### Passo 2 (alternativa) — Subir pelo Vercel CLI
```bash
# Instalar Vercel CLI
npm i -g vercel

# Na pasta do projeto
cd bodysoul
vercel

# Siga os prompts — ele vai publicar automaticamente
```

### Passo 3 — Conectar o domínio bodysoul.com.br
1. No painel do Vercel, vá em **Settings → Domains**
2. Adicione: `bodysoul.com.br`
3. O Vercel vai mostrar os **registros DNS** que você precisa configurar
4. No **Registro.br**, acesse o domínio e configure o DNS:
   - Tipo: **CNAME** → `cname.vercel-dns.com`
   - Ou os registros **A** que o Vercel indicar
5. Aguarde propagação (até 48h, geralmente menos de 1h)

---

## 3. Como o Eduardo usa o painel admin

1. Acessa `bodysoul.com.br/admin.html`
2. Digita a senha
3. Edita os campos que quiser (preços, horários, contato)
4. Clica em **"Salvar todas as alterações"**
5. O site principal atualiza **em tempo real** — sem precisar mexer em código

---

## Custos

| Item | Valor |
|------|-------|
| Domínio bodysoul.com.br (Registro.br) | R$ 45/ano |
| Hospedagem Vercel | **Gratuita** |
| Banco de dados Firebase | **Gratuito** (até 1GB) |
| **Total** | **R$ 45/ano** |

---

## Suporte
Dúvidas → Yago: (27) XXXXX-XXXX
