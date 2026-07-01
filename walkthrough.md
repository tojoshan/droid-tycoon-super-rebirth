# Walkthrough - Tracker de Super Rebirth (Ciclo 3) - Corrección Rebirth 14

He aplicado una corrección de datos importante en el listado de requisitos del **Rebirth 14** para adaptarlo a la realidad del juego en lugar de la imagen de la guía original, la cual presentaba una discrepancia.

## Corrección de Requisitos en Rebirth 14

*   **Problema:** La infografía de la guía del Ciclo 3 indicaba que para el Rebirth 14 se requerían *B2 Heavy (Arcoíris)*, *B2-RP (Base)* y *R7 (Oro)*. Sin embargo, en el juego real, el Rebirth 14 exige volver a usar los mismos tres droides del nivel 12 en niveles superiores: **Bal-Core (Diamante)**, **Groundmech (Diamante)** y **TRAK-R (Arcoíris)**.
*   **Consecuencia del error:** Al estar en Rebirth 12, la aplicación marcaba erróneamente a Bal-Core, Groundmech y TRAK-R para "VENDER", provocando que los jugadores se deshicieran de ellos antes de tiempo y tuvieran que volver a construirlos para el nivel 14.
*   **Solución:** Se actualizó el array de requisitos del nivel 14 en `src/App.tsx`:
    ```typescript
    {
      level: 14,
      credits: "8.45 Billion Credits",
      droids: [
        { name: "Bal-Core", tier: 3 },
        { name: "Groundmech", tier: 3 },
        { name: "TRAK-R", tier: 4 }
      ]
    }
    ```

## Impacto en el Comportamiento de la App

1.  **Protección en Rebirth 12:** Al estar en Rebirth 12 (camino al 13), el motor de recomendación detecta que estos tres droides son necesarios en el futuro (R-14) y, por lo tanto, **ya no los marca para vender**. En su lugar, les asigna el estado de conservación:
    *   *Groundmech / Bal-Core:* `🔒 R-13 OK (Futuro R-14 Diamante)`
    *   *TRAK-R:* `🔒 R-13 OK (Futuro R-14 Arcoíris)`
2.  **Objetivos Claros en Rebirth 13:** Al estar en Rebirth 13 (camino al 14), los tres droides se destacan automáticamente en la parte superior como metas activas inmediatas para el Rebirth 14.

---

## Verificación

1.  **Compilación y Construcción:** exitosa y limpia.
2.  **Persistencia en Repositorio:** Guardé la imagen de guía en el directorio `images/` y se subieron todos los cambios a la rama `main` de GitHub.
