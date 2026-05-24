# Dashboard

# 🦺 Riesgo Laboral, Municipio a Municipio

**Análisis Exploratorio de Datos — Positiva Compañía de Seguros (ARL) · Colombia 2025**

> Proyecto académico desarrollado en el curso *Programación para Ciencia de Datos* (NRC 2479)  
> Universidad Tecnológica de Bolívar · Cartagena de Indias · Mayo 2026

---

## 📋 Descripción

Este repositorio contiene el análisis exploratorio de datos (EDA) del registro público [**Estadísticas Riesgos Laborales Positiva 2026**](https://www.datos.gov.co/Salud-y-Protecci-n-Social/Estad-sticas-Riesgos-Laborales-Positiva-2026/kwqa-xugj) disponible en el portal Datos Abiertos Colombia.

El dataset reúne **60.684 registros** de afiliación y siniestralidad laboral desagregados por departamento, municipio y actividad económica (CIIU), con corte a noviembre de 2025. El objetivo es caracterizar la distribución territorial y sectorial del riesgo laboral y evaluar críticamente las limitaciones del propio registro como insumo analítico.

---

## ✨ Hallazgos principales

| Métrica | Valor |
|---|---|
| Registros analizados | 60.684 |
| Variables | 14 |
| Departamentos cubiertos | 33 |
| Municipios con reporte | 1.033 |
| Actividades económicas (CIIU) | 987 |
| Trabajadores afiliados | 3.498.895 |
| — Dependientes | 3.019.740 · 86,3 % |
| — Independientes | 479.155 · 13,7 % |
| Accidentes de trabajo presuntos | 8.597 |
| **Tasa nacional de accidentalidad** | **24,57 / 10.000 trab.** |
| Depto. de mayor tasa | Antioquia · 39,24 |
| Depto. de menor tasa* | Atlántico · 13,53 |
| Top-10 actividades (% de accidentes) | 35,6 % |

*\* Entre departamentos con más de 40.000 trabajadores afiliados.*

> **Conclusión clave:** el tamaño de la fuerza laboral **no predice el riesgo**. Bogotá concentra el 31 % de los afiliados pero registra una tasa de accidentalidad (19,2) muy por debajo de la media nacional, mientras Antioquia, Meta y Caldas la superan ampliamente.

---

## 🗂️ Estructura del repositorio

```
.
├── datos.csv                # Dataset original (Positiva 2026)
├── dashboardf3.qmd          # Dashboard Quarto (fuente reproducible)
├── dashboardf3.html         # Dashboard renderizado
├── custom2-1.css            # Estilos del dashboard
├── poster_riesgo_laboral_A1.pdf   # Póster presentado en la Feria
├── ficha_tecnica.pdf        # Ficha técnica para jurados
└── README.md
```

---

## 🛠️ Tecnologías

- **Python 3** — análisis y procesamiento
- **pandas** — carga y manipulación del dataset
- **Plotly / Plotly Express** — visualizaciones interactivas
- **Quarto** — dashboard reproducible
- **Biblioteca propia** — estadística descriptiva implementada desde cero *(sin `describe()`)* :
  - Media, mediana, cuartiles por interpolación lineal
  - Desviación estándar y desviación media absoluta
  - Moda y tablas de frecuencia
  - Detección de duplicados y calidad de datos

---

## 🚀 Cómo reproducir el análisis

### 1. Clonar el repositorio

```bash
git clone https://github.com/<usuario>/<repo>.git
cd <repo>
```

### 2. Instalar dependencias

```bash
pip install pandas plotly numpy
```

> Requiere **Quarto** instalado: [quarto.org/docs/get-started](https://quarto.org/docs/get-started/)

### 3. Renderizar el dashboard

```bash
quarto render dashboardf3.qmd
```

El archivo `dashboardf3.html` se genera en el mismo directorio y puede abrirse en cualquier navegador.

---

## ⚠️ Problemas de calidad identificados

El dataset presentó las siguientes limitaciones relevantes:

1. **Columnas idénticas** — `PRESUACCIDETRASUCE`, `MUERTES_REPOR_AT` y `NUEVAPENSIOINVA_R_AT` contienen valores exactamente iguales en los 60.684 registros; solo una aporta información.
2. **Formato numérico inconsistente** — `RELA_DEP` y `RELA_INDEP` usan coma como separador de miles, lo que impide su lectura numérica directa.
3. **Variable constante** — `CODIGO_DE_LA_ARL` solo contiene el valor `1423`, sin variabilidad analítica.
4. **Varianza casi nula** — `INCAPERMAPARCIAR_AT` e `INCAPERMAPARCIAR_EL` registran aproximadamente 100 % de ceros.
5. **Sin variabilidad temporal** — `AÑO_DE_INFORME` y `MES_DE_INFORME` son constantes; no permiten análisis de serie de tiempo.
6. **Alta dispersión de ceros** — `NUEVAPENSIOINVA_R_EL` registra solo 23 valores distintos de cero sobre 60.684 registros (99,96 % ceros).

---

## 📐 Referencias

- Datos Abiertos Colombia. *Estadísticas Riesgos Laborales Positiva 2026*. [datos.gov.co](https://www.datos.gov.co/Salud-y-Protecci-n-Social/Estad-sticas-Riesgos-Laborales-Positiva-2026/kwqa-xugj)
- Montgomery, D.C. & Runger, G.C. (2014). *Applied Statistics and Probability for Engineers*, 6.ª ed. Wiley.
- Hyndman, R.J. & Fan, Y. (1996). Sample Quantiles in Statistical Packages. *The American Statistician*, 50(4), 361–365.
- Mendenhall, W., Beaver, R.J. & Beaver, B.M. (2013). *Introduction to Probability and Statistics*, 14.ª ed. Cengage.

---

## 👥 Equipo

| Integrantes | |
|---|---|
| Simón Bedoya |
| Isaac Navarro | 
| Daniel Villalba |
| José Machacón |
---

## 📄 Licencia

Uso estrictamente académico. Los datos provienen de una fuente pública (Datos Abiertos Colombia) y se usan sin fines comerciales, con la fuente debidamente citada.
