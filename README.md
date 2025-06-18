validacion-credito/
│
├── main.py                   # Backend FastAPI principal
├── crear_lead_odoo.py        # Envío de lead a Odoo
├── mimoto_api.py             # Integración con mimoto.express
├── templates/
│   └── formulario_validacion.html
├── static/                   # JS/CSS del formulario
├── tests/
│   └── test_main.py
├── .env.example              # Plantilla de configuración
└── .github/workflows/deploy.yml



# 🛡️ validacion-credito

Sistema automatizado de validación para solicitudes de tarjetas del Banco de Costa Rica.  
Desarrollado por [YovoyTech SRL](https://yovoytech.com).

[![CI/CD - GitHub Actions](https://github.com/yovoyTecSRL/validacion-credito/actions/workflows/deploy.yml/badge.svg)](https://github.com/yovoyTecSRL/validacion-credito/actions)
[![FastAPI](https://img.shields.io/badge/FastAPI-🚀-green)](https://fastapi.tiangolo.com/)
[![Odoo](https://img.shields.io/badge/Odoo-CRM-purple)](https://www.odoo.com/)
[![Made by YovoyTech](https://img.shields.io/badge/Made%20by-YovoyTech-blue)](https://yovoytech.com)

---

## 📌 Descripción

Este proyecto valida automáticamente clientes para tarjetas usando APIs costarricenses:

- 🔹 CCSS
- 🔹 Hacienda
- 🔹 SUGEF
- 🔹 Protectora
- 🔹 Score del BCR

Y si es aprobado:

✅ Crea un lead en Odoo  
✅ Genera orden de entrega con mimoto.express  
✅ Devuelve un tracking ID para seguimiento  
✅ Integra IA (GPT-4) para decisión automática

---

## ⚙️ Tecnologías utilizadas

- [FastAPI](https://fastapi.tiangolo.com/) + Pydantic
- HTML5 + Bootstrap 5 (Frontend)
- Odoo 16 Community (CRM Lead API)
- [Mimoto.express](https://mimoto.express/) API (órdenes de entrega)
- Docker / GitHub Actions (CI/CD)
- OpenAI GPT-4 API

---

## 🧪 Endpoints principales

| Método | Ruta         | Descripción                              |
|--------|--------------|------------------------------------------|
| `GET`  | `/formulario`| Formulario visual para validación        |
| `POST` | `/procesar`  | Procesa datos del formulario             |
| `POST` | `/validar`   | Ejecuta validación completa + GPT + mimoto |
| `GET`  | `/ping`      | Prueba de vida del servidor              |

---

## 🛠️ Instalación local

### 🔧 Requisitos

- Python 3.10+
- pip
- Git
- (opcional) Docker

```bash
git clone https://github.com/yovoyTecSRL/validacion-credito.git
cd validacion-credito
pip install -r requirements.txt
uvicorn main:app --reload --port 8100
🔐 Variables de entorno
Crear un archivo .env basado en este template:

env
Copiar
Editar
OPENAI_API_KEY=sk-xxx
ODOO_API_URL=https://mi-odoo.com/api/leads
ODOO_API_KEY=mi_token_secreto
MIMOTO_API_KEY=token_mimoto
🧪 Pruebas automáticas
bash
Copiar
Editar
pytest test_main.py
Incluye pruebas para:

/ping

Validaciones de cédula/teléfono

Flujo de decisión de GPT

🚀 Despliegue con CI/CD
Este proyecto se despliega automáticamente a Azure Web App usando GitHub Actions.

Archivo de configuración: .github/workflows/deploy.yml

📦 Funcionalidad avanzada
📍 GPS vía Traccar API (pendiente integrar)

🧠 Decisión de aprobación usando GPT-4 (contextual, explicada)

📬 Envío automatizado con mimoto.express

✉️ Registro de resultado y seguimiento
