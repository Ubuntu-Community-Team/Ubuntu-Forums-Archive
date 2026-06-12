---
title: "Java application crashes"
date: 2008-03-02
forum: Programming Talk
---

### Post by sergiomr88 on 2008-03-02
After installing ubuntu I installed java jdk and java jre through the terminal. After installing java I installed eclipse from the synaptics package manager. After restarting my computer, I found that websites  that were asking for java plugins to work were already working and that eclipse was also working properly. So far so good, but when I imported a project to eclipse and tried to open it as a java application, I only get a window with an unresponsive interface of the application. Then, after a few seconds the window will turn gray and I have to force the application to quit.

What should I do to solve this?

---

### Post by a9bejo on 2008-03-02
> **sergiomr88 said:**
> What should I do to solve this?

try recompiling and running your project from a terminal.  This will hopefully give you/us some error messages so we can figure out what is going wrong. Also, use the command 

```
update-java-alternatives
``` to make sure you got the latest jdk from sun running.

---

### Post by sergiomr88 on 2008-03-02
When using the terminal I get this:

```

sergiomr88@inspiron6400:~$ cd /home/sergiomr88/Projectos/n3_avion/source/uniandes/cupi2/avion/interfaz/
sergiomr88@inspiron6400:~/Projectos/n3_avion/source/uniandes/cupi2/avion/interfaz$ javac InterfazAvion.java
----------
1. ERROR in InterfazAvion.java (at line 20)
        import uniandes.cupi2.avion.mundo.*;
               ^^^^^^^^^^^^^^^^^^^^^^^^^^
The import uniandes.cupi2.avion.mundo cannot be resolved
----------
2. WARNING in InterfazAvion.java (at line 25)
        public class InterfazAvion extends JFrame
                     ^^^^^^^^^^^^^
The serializable class InterfazAvion does not declare a static final serialVersionUID field of type long
----------
3. ERROR in InterfazAvion.java (at line 35)
        private Avion avion;
                ^^^^^
Avion cannot be resolved to a type
----------
4. ERROR in InterfazAvion.java (at line 44)
        private PanelAvion panelAvion;
                ^^^^^^^^^^
PanelAvion cannot be resolved to a type
----------
5. ERROR in InterfazAvion.java (at line 49)
        private PanelBotonesAvion panelBotones;
                ^^^^^^^^^^^^^^^^^
PanelBotonesAvion cannot be resolved to a type
----------
6. ERROR in InterfazAvion.java (at line 54)
        private DialogoAsignacion dAsignacion;
                ^^^^^^^^^^^^^^^^^
DialogoAsignacion cannot be resolved to a type
----------
7. ERROR in InterfazAvion.java (at line 67)
        avion = new Avion( );
        ^^^^^
avion cannot be resolved
----------
8. ERROR in InterfazAvion.java (at line 67)
        avion = new Avion( );
                    ^^^^^
Avion cannot be resolved to a type
----------
9. ERROR in InterfazAvion.java (at line 73)
        panelBotones = new PanelBotonesAvion( this );
        ^^^^^^^^^^^^
panelBotones cannot be resolved
----------
10. ERROR in InterfazAvion.java (at line 73)
        panelBotones = new PanelBotonesAvion( this );
                           ^^^^^^^^^^^^^^^^^
PanelBotonesAvion cannot be resolved to a type
----------
11. ERROR in InterfazAvion.java (at line 74)
        add( panelBotones, BorderLayout.NORTH );
             ^^^^^^^^^^^^
panelBotones cannot be resolved
----------
12. ERROR in InterfazAvion.java (at line 77)
        panelAvion = new PanelAvion( avion );
        ^^^^^^^^^^
panelAvion cannot be resolved
----------
13. ERROR in InterfazAvion.java (at line 77)
        panelAvion = new PanelAvion( avion );
                         ^^^^^^^^^^
PanelAvion cannot be resolved to a type
----------
14. ERROR in InterfazAvion.java (at line 77)
        panelAvion = new PanelAvion( avion );
                                     ^^^^^
avion cannot be resolved
----------
15. ERROR in InterfazAvion.java (at line 78)
        add( panelAvion, BorderLayout.CENTER );
             ^^^^^^^^^^
panelAvion cannot be resolved
----------
16. ERROR in InterfazAvion.java (at line 96)
        dAsignacion = new DialogoAsignacion( this, avion );
        ^^^^^^^^^^^
dAsignacion cannot be resolved
----------
17. ERROR in InterfazAvion.java (at line 96)
        dAsignacion = new DialogoAsignacion( this, avion );
                          ^^^^^^^^^^^^^^^^^
DialogoAsignacion cannot be resolved to a type
----------
18. ERROR in InterfazAvion.java (at line 96)
        dAsignacion = new DialogoAsignacion( this, avion );
                                                   ^^^^^
avion cannot be resolved
----------
19. ERROR in InterfazAvion.java (at line 97)
        dAsignacion.setLocation( calculaPosicionCentral( this, dAsignacion ) );
        ^^^^^^^^^^^
dAsignacion cannot be resolved
----------
20. ERROR in InterfazAvion.java (at line 97)
        dAsignacion.setLocation( calculaPosicionCentral( this, dAsignacion ) );
                                                               ^^^^^^^^^^^
dAsignacion cannot be resolved
----------
21. ERROR in InterfazAvion.java (at line 98)
        dAsignacion.setModal( true );
        ^^^^^^^^^^^
dAsignacion cannot be resolved
----------
22. ERROR in InterfazAvion.java (at line 99)
        dAsignacion.setVisible( true );
        ^^^^^^^^^^^
dAsignacion cannot be resolved
----------
23. ERROR in InterfazAvion.java (at line 121)
        Pasajero pasajero = new Pasajero( cedula, "no importa" );
        ^^^^^^^^
Pasajero cannot be resolved to a type
----------
24. ERROR in InterfazAvion.java (at line 121)
        Pasajero pasajero = new Pasajero( cedula, "no importa" );
                                ^^^^^^^^
Pasajero cannot be resolved to a type
----------
25. ERROR in InterfazAvion.java (at line 122)
        if( !avion.desasignarSilla( pasajero ) )
             ^^^^^
avion cannot be resolved
----------
26. ERROR in InterfazAvion.java (at line 137)
        porcentaje = avion.calcularPorcentajeOcupacion( );
                     ^^^^^
avion cannot be resolved
----------
27. ERROR in InterfazAvion.java (at line 160)
        Pasajero pasajero = new Pasajero( cedula, "no importa" );
        ^^^^^^^^
Pasajero cannot be resolved to a type
----------
28. ERROR in InterfazAvion.java (at line 160)
        Pasajero pasajero = new Pasajero( cedula, "no importa" );
                                ^^^^^^^^
Pasajero cannot be resolved to a type
----------
29. ERROR in InterfazAvion.java (at line 162)
        Silla silla = avion.buscarPasajero( pasajero );
        ^^^^^
Silla cannot be resolved to a type
----------
30. ERROR in InterfazAvion.java (at line 162)
        Silla silla = avion.buscarPasajero( pasajero );
                      ^^^^^
avion cannot be resolved
----------
31. ERROR in InterfazAvion.java (at line 166)
        VentanaDatosPasajero vDatos = new VentanaDatosPasajero( silla );
        ^^^^^^^^^^^^^^^^^^^^
VentanaDatosPasajero cannot be resolved to a type
----------
32. ERROR in InterfazAvion.java (at line 166)
        VentanaDatosPasajero vDatos = new VentanaDatosPasajero( silla );
                                          ^^^^^^^^^^^^^^^^^^^^
VentanaDatosPasajero cannot be resolved to a type
----------
33. ERROR in InterfazAvion.java (at line 183)
        String respuesta = avion.metodo1( );
                           ^^^^^
avion cannot be resolved
----------
34. ERROR in InterfazAvion.java (at line 192)
        String respuesta = avion.metodo2( );
                           ^^^^^
avion cannot be resolved
----------
35. ERROR in InterfazAvion.java (at line 201)
        remove( panelAvion );
                ^^^^^^^^^^
panelAvion cannot be resolved
----------
36. ERROR in InterfazAvion.java (at line 204)
        panelAvion = new PanelAvion( avion );
        ^^^^^^^^^^
panelAvion cannot be resolved
----------
37. ERROR in InterfazAvion.java (at line 204)
        panelAvion = new PanelAvion( avion );
                         ^^^^^^^^^^
PanelAvion cannot be resolved to a type
----------
38. ERROR in InterfazAvion.java (at line 204)
        panelAvion = new PanelAvion( avion );
                                     ^^^^^
avion cannot be resolved
----------
39. ERROR in InterfazAvion.java (at line 205)
        add( panelAvion, BorderLayout.CENTER );
             ^^^^^^^^^^
panelAvion cannot be resolved
----------
39 problems (38 errors, 1 warning)sergiomr88@inspiron6400:~/Projectos/n3_avion/sz$ ce/uniandes/cupi2/avion/interfaz


```

---

### Post by a9bejo on 2008-03-02
you did not set the classpath with your javac call, so the compiler does not know where to find your  uniandes...mundo package. 

if you are not familiar with using java from the command line, you should really learn this  first  before you work with an IDE like eclipse..

---

