---
title: "Acpi bios error , muerte y formateo , mi pc no quiere windows"
date: 2024-02-24
forum: New to Ubuntu
---

### Post by valantain on 2024-02-24
Hola buenas soy nuevo , antes que nada saludaros a todos , bueno el titular resume un poco lo que me ha pasado , os pondre al dia lo mas resumido posible sobre mi historia.
Me regalan un pc del año 2017 (1,55ghz ,4gb ram)
Windows bloqueado por contraseña olvidada , imposible recuperarla , me dispongo a restaurar , falla al 99x100 tras horas y horas y horas decido quitar la corriente , despues de esto solo se arranca y se apaga , intento instalar windows usb booteable , no lo coge y una que ll coge sale una pantalla azul con interferencias superpuesta al simbolo de hp , pruebo con lubuntu , este si arranca despues de darme el error acpi bios , (no se como subir capturas perdonen mi torpeza) total que me inicia y no me va nada mal , actualizo la primera vez y empieza a actualizar , luego empezaron los primeros problemas possible missing frimware , bueno no pasa nada , consigo instalar la version actualizada de python (ahora a la vejez me ha dado por aprender a programar, llevo 1 mes) total me da problemas pero la actualizo , actualizo el pib y me dice que la conexion ssl no me deja , reinstalo python y ahora si me deja pip 24.0 , total digo mira ya que estoy lo actualizo todo y reinicio , aqui es donde sucedio la tragedia: Possible missing firmware en cascada al final de la instalacion y algo del kernel , total reinicio y esta vez algo cambio en el arranque , empieza salir como comprueba cosas y todo (OK) en verde , pero al iniciar ya no hay interfaz grafica. Solo una terminal que me pide mi nombre de usuario y contraseña , la introduzco y estoy en el pc , pero sin interfaz xD.
Total digo voy a probar si puedo instalar windows desde el usb booteable y no me deja lo mismo pantallita azul con interferencias , total que estoy condenado a usar Lubuntu , lo que no se es si a futuro me va a pasar lo mismo o no , creo ue al ordenador se le ha jodido algo o igual se desconfiguro el acpi bios(no puede resolver el simbolo) ni idea , siento enrrollarme tanto y ser un plasta , pero se aceptan todo tipo de sugerencias . Gracias por dedicar su tiempo a leer este tocho.

---

### Post by valantain on 2024-02-24
Usted
10.4724541 ACPI BIOS Error (bug): Could not resolve symbol IN SB.WLBU. STA. LUDI, WE NOT FOUND (20230331/psargs-330)

0.4725181 ACPI Error: Aborting method SB.WLBU. STA due to previous error

0.5570421 ACPI BIOS Error (bag): Could LUBI, RE NOT FOUND (20230331/psargs-330) not resolve symbol [N_SB.WLBU._STA.W

8.5570651 ACPI Error: Aborting method (RE NOT FOUND) (20238331/psparse-529) SB.WLBU. STA due to previous error

0.6590631 ACPI BIOS Error (bag): Could not resolve symbol [_SB.WLBU._STA.W

LUDI, HE NOT FOUND (26230331/psargs-330) 0.6591351 ACPI Error: Aborting method SB.MLBU. STA due to previous error

(RE NOT FOUND) (29238331/psparse-529) 0.7414961 tpa crb MSFT0101:00: can't request region for resource [mem 0xe7b76000-0xe7b79fff]

Este es el error que me da al inicio , deberia de preocuparme o hacer algo?

---

