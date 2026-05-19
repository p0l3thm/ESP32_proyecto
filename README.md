  El protocolo UART define la mensajería serial asíncrona entre el servidor Web (ESP32) y el actuador (Arduino Nano).
        *   **Velocidad:** 9600 baudios.
        *   **Bits de Datos:** 8
        *   **Paridad:** Ninguna (None)
        *   **Bits de Parada:** 1
        *   **Formato del Paquete:** Carácter único codificado en ASCII (1 byte).
      type: object
      properties:
        Mensajes_Soportados:
          type: array
          items:
            type: string
            description: >
              **Tabla Detallada de Comandos UART:**
              
              | Comando | ASCII (Hex) | Acción | Motor Afectado | Descripción |
              |:---:|:---:|---|---|---|
              | `F` | `0x46` | Adelante | DC Motor A (Carro) | Mueve el carro de traslación hacia el frente. |
              | `B` | `0x42` | Atrás | DC Motor A (Carro) | Mueve el carro de traslación hacia la base. |
              | `U` | `0x55` | Subir | DC Motor B (Elevación) | Recoge el cable del gancho (Sube). |
              | `D` | `0x44` | Bajar | DC Motor B (Elevación) | Suelta el cable del gancho (Baja). |
              | `L` | `0x4C` | Izquierda | Stepper (Rotación) | Gira la grúa en sentido antihorario. |
              | `R` | `0x52` | Derecha | Stepper (Rotación) | Gira la grúa en sentido horario. |
              | `S` | `0x53` | Stop | Todos | Detiene inmediatamente cualquier movimiento activo. |
              
              *Nota de Seguridad:* El firmware del Arduino incorpora un timeout (500 ms por defecto). Si no se recibe repetidamente el carácter de un comando activo antes del timeout, el sistema transiciona automáticamente al estado `Stop`.
