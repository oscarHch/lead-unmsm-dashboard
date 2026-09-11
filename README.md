# LEAD UNMSM - Analytics Dashboard & AI Assistant 📊

Un dashboard interactivo diseñado para visualizar, analizar y consultar las métricas de redes sociales (Meta Business Suite) de la comunidad estudiantil LEAD UNMSM. El proyecto incluye un asistente de inteligencia artificial integrado que responde preguntas sobre el rendimiento del contenido cruzando datos en tiempo real.

## 🚀 Características Principales

*   **Visualización de Datos:** Gráficos dinámicos (líneas, barras, dispersión) que muestran métricas clave como Alcance, Engagement Rate, Embudo de Conversión y Demografía.
*   **Asistente IA Integrado:** Un chatbot flotante estilo *glassmorphism* capaz de responder consultas complejas en lenguaje natural basándose estrictamente en los datos del dashboard.
*   **Interfaz Responsiva & Modo Oscuro:** Construido con Tailwind CSS, adaptándose a cualquier dispositivo y permitiendo alternar entre temas claro/oscuro.
*   **Tabla de Contenido Dinámica:** Registro detallado de publicaciones con funciones de ordenamiento (sort) por métricas individuales.
*   **Redimensión Personalizada:** El widget del chat incluye lógica nativa en JavaScript para redimensionar su altura hacia arriba con el cursor, sin dependencias externas.
*   **Renderizado Markdown:** Las respuestas de la IA se formatean automáticamente en la interfaz web utilizando tipografía limpia y estructurada.

## 🛠️ Stack Tecnológico

**Frontend (Client-Side)**
*   HTML5 / CSS3
*   [Tailwind CSS](https://tailwindcss.com/) (vía CDN)
*   [Chart.js](https://www.chartjs.org/) (Visualización de datos)
*   [Marked.js](https://marked.js.org/) (Renderizado de Markdown a HTML)
*   Despliegue: **Netlify**

**Backend & Base de Datos (Server-Side)**
*   [Google Apps Script (GAS)](https://developers.google.com/apps-script) (Actúa como API RESTful)
*   **Google Sheets** (Base de datos estructurada en tablas: Resultados, Contenido y Público)

**Inteligencia Artificial**
*   **Google Gemini API** (`gemini-3.5-flash`): Procesamiento de lenguaje natural y análisis estructurado del JSON devuelto por Apps Script.

## 🏗️ Arquitectura del Sistema (v1.3.0)

El proyecto utiliza una arquitectura *Serverless*. 
1.  El cliente (Frontend) realiza una petición `GET` mediante la función `fetch()` al endpoint público de Google Apps Script.
2.  La función `doGet(e)` en GAS actúa como enrutador:
    *   Si el parámetro es `action=getData`, GAS lee las hojas de cálculo y devuelve un JSON estructurado con toda la data para renderizar los gráficos.
    *   Si el parámetro es `action=chatIA`, GAS toma la pregunta del usuario, pre-procesa las fechas límite de las tablas, arma un payload con contexto temporal y consulta a la API de Gemini. La respuesta es devuelta en texto puro y parseada a HTML en el cliente.

## ⚙️ Instalación y Uso Local

1.  Clona este repositorio:
    ```bash
    git clone [https://github.com/tu-usuario/lead-dashboard-ia.git](https://github.com/tu-usuario/lead-dashboard-ia.git)
    ```
2.  Abre el archivo `index.html` en tu navegador de preferencia (no requiere Node.js ni servidor local al consumir APIs externas).
3.  *Nota:* Para replicar el backend, se requiere configurar un proyecto en Google Apps Script, vincularlo a un archivo de Google Sheets y configurar un *Script Property* llamado `GEMINI_API_KEY` con una llave válida de Google AI Studio.

## 👨‍💻 Autor

**Oscar Huamanchahua**
Estudiante de Ingeniería de Software | Universidad Nacional Mayor de San Marcos (UNMSM)
