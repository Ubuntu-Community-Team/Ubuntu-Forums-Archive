---
title: "[SOLVED] ayuda con el menu.lst para booteo"
date: 2008-06-25
forum: Paraguay Team
---

### Post by Blacho on 2008-06-25
hola... q tal los perros... primero q nada..! q mucho busque el loco team paraguay! no se si es nuevo. pero por fin encontre!

segundo! Ubuntu triunfa!!! ya prohibi en mi casa que usen windows! jajaja

tercero... tengo un problemita con mi booteo....
tengo un hdd como primarymaster con ubuntu
y otro hdd como primaryslave con windows
en el archivo menu.lst agregue la opcion para que en la lista de boot tenga windows.. pero cuando selecciono windows dice "starting up" y no pasa nada.... no se si esta bien mi comando en el archivo menu.lst... sera eso nomas?

esto es lo q le agregue al archivo... no cambie el default porq quiero mantenerlo en ubuntu... pero de vez en cuando tengo q entrar a windows y no pasa nada... tengo q desconectar mi hdd primarymaster para poder entrar

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1


cualquier ayuda sera bienvenida!

---

### Post by Blacho on 2008-06-25
bueno! ya encontre la solucion... por si alguien tiene el mismo problema.. lo pongo para todos...

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

faltaba el map... ahi ya levanta windows tb....
gracias de todas formas

---

