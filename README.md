# Linux_Shell

Este proyecto desarrolla un intérprete de comandos o Shell de aspecto similar al ya existente en Linux, que permite al usuario lanzar sus programas y ejecutar comandos de manera personalizada. Se proporciona una versión inicial implementada en lenguaje C, ProyectoShell.c, que se apoya en funciones de otro fichero auxiliar, ApoyoTareas.c (junto a su cabecera, ApoyoTareas.h).

## Uso

1. Para compilar:
   
   ```bash
   gcc ProyectoShell.c ApoyoTareas.c-o MiShell
2. Para ejecutar:
   
   ```bash
   ./MiShell
3. Para salir pulsar `Control+D`

## Funcionalidad Básica
El Shell soporta la ejecución de comandos de manera similar a los shells tradicionales de Linux. Las funcionalidades principales incluyen:

1. **Ejecución de Comandos**: Los usuarios pueden introducir comandos que el Shell ejecutará. Los comandos pueden ejecutarse en primer plano (foreground) o en segundo plano (background).
    - **Comandos en Primer Plano**: Se muestra el PID del proceso, el nombre del comando y su estado final.
    - **Comandos en Segundo Plano**: Se muestra únicamente el PID del proceso y el nombre del comando.

2. **Manejo de Errores**: Si se introduce un comando incorrecto, el Shell mostrará un mensaje de error.

## Comandos Internos
Además de los comandos externos, el Shell soporta varios comandos internos:
1. **cd**: Cambia el directorio de trabajo actual.
2. **logout**: Sale del Shell.

## Gestión de Procesos
El Shell gestiona los procesos de manera eficiente mediante las siguientes funciones del sistema:
1. **fork()**: Crea un proceso hijo.
2. **waitpid()**: Espera a que termine un proceso hijo.
3. **execvp()**: Lanza un programa.
4. **exit()**: Termina un proceso.

## Ejecución de Comandos en Primer y Segundo Plano
- **Primer Plano (FG)**: El comando ejecutado en primer plano toma el control del terminal.
- **Segundo Plano (BG)**: El comando ejecutado en segundo plano no toma el control del terminal, permitiendo a el Shell seguir aceptando nuevos comandos.

## Manejo de Señales
El Shell maneja las señales para evitar procesos zombies y controlar la suspensión y reanudación de procesos:
- **SIGCHLD**: Maneja la terminación o suspensión de procesos en segundo plano.
- **SIGINT, SIGQUIT, SIGTSTP, SIGTTIN, SIGTTOU**: Controla estas señales para gestionar el terminal.

## Comandos Adicionales
1. **jobs**: Imprime una lista de comandos que están siendo ejecutados en segundo plano o que han sido suspendidos.
2. **fg**: Permite pasar a primer plano un comando que estaba en segundo plano o suspendido.
3. **bg**: Permite pasar a segundo plano un comando que estaba suspendido.

## Diagram de flujo del Shell
La siguiente imagen representa un diagrama de flujo que describe los distintos procesos que maneja el shell:
<p align="center">
   <img src="https://github.com/rorro6787/rorro6787/blob/main/Images/shell.png" width = 100%/>
</p>
