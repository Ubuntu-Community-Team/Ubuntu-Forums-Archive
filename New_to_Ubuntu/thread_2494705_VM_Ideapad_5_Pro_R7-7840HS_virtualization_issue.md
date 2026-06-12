---
title: "VM Ideapad 5 Pro R7-7840HS virtualization issue"
date: 2024-01-24
forum: New to Ubuntu
---

### Post by garciax1671 on 2024-01-24
Hello,


I have the Ideapad 5 Pro with the AMD Ryzen 7 7840HS processor with W11, with the Virtualbox 7 program and I tried to install a VM (Virtual Machine) of an Ubuntu 23.10 OS, at the time of installing there comes a point where a message appears message "Freeing initrd memory: 105798K" and it stays blocked, I have tried everything. AMD-V is enabled in the BIOS, I updated the BIOS, I have tried other Linux distributions and there is no way, I have tried all the configurations in Virtualbox, several versions, I have searched for information everywhere and I have not found a solution.


I need to fix this problem, please.

---

### Post by TheFu on 2024-01-24
a) the dmesg command will show this as text.  Text is better than images here.  **journalctl -b ** will show it too. And you can get prior boot errors **journalctl -b -1**
b) we need to see the stuff _above_ what you've shown. That's higher in the stack strace.

If you create a boot flash drive, will the real hardware boot?  Don't need to install, just use the "Try Ubuntu" mode.

---

### Post by garciax1671 on 2024-01-24
El terminal está completamente congelado no funciona ninguna entrada, lo probé con VMware y si que virtualiza, pero cuando activo AMD-V, salta un error.

EDIT:  Translation into English for non Spanish speakers.
The terminal is completely frozen, no input works, I tried it with VMware and it does virtualize, but when I activate AMD-V, an error appears.

---

### Post by garciax1671 on 2024-01-26
I have tried with VMware Player and it works, the case is that I activate the AMD-V function and an error appears, in the BIOS it is activated I do not understand what could be happening, although Vmware manages to virtualize, I would like to fix the problem in Virtualbox which is much more convenient be able to work. I have attached the problems with virtualization with AMD-V on VMware, which I believe the problem eradicates on AMD-V

---

### Post by TheFu on 2024-01-26
The error is pretty clear.  Don't use nested virtualiation.  In fact, non-experts should only have 1 hypervisor installed on a VM host.

---

### Post by garciax1671 on 2024-01-26
Puedes explicarlo mejor, por favor, no lo entiendo exactamente que quieres decir, entiendo que no use virtualización anidada, pero ¿a que te refieres?

---

### Post by MAFoElffen on 2024-01-26
Well... Is a common problem with VirtualBox. It's an error about about what else is running in memory on that Host. 

When VirtualBox allocates memory for a VM, it needs that memory to be in a "Contiguous Block"... Which means that it needs to allocate memory in one single swipe, with nothing in between that needed area. VirtualBox allocates memory "strangely".

Reboot, and have VirtualBox as the only application running, and see what happens then.

Hyper-V and VMware Workstation (or Player) do not have that problem.

---

### Post by garciax1671 on 2024-01-26
No sé si te refieres a la imagen que adjuntado, pero tampoco funciona.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293352&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293353&stc=1[/IMG]

---

### Post by garciax1671 on 2024-01-26
Okay, he apagado y encendido el portátil, iniciado solo Virtualbox y la encendido la VM y nada sigo teniendo el mismo problema, he puesto está configuración que no se si se atiende mucho a tu indicación.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293354&stc=1[/IMG]

---

### Post by MAFoElffen on 2024-01-26
Traduce lo que dije al español.

> **MAFoElffen said:**
> 
Bueno... Es un problema común con VirtualBox. Es un error sobre qué más se está ejecutando en la memoria de ese Host.

Cuando VirtualBox asigna memoria para una VM, necesita que esa memoria esté en un "Bloque contiguo"... Lo que significa que necesita asignar memoria de un solo paso, sin nada entre esa área necesaria. VirtualBox asigna memoria "extrañamente".

Reinicie y tenga VirtualBox como la única aplicación en ejecución y vea qué sucede luego.

Hyper-V y VMware Workstation (o Player) no tienen ese problema.

Este foro es para inglés. Si va a publicar aquí, utilice Google Translate para traducirlo al inglés y publicarlo aquí.

Esta es la única publicación que traduciré...

Veo que intentaste lo que te pregunté, ¿Cuánta memoria libre tiene?

---

