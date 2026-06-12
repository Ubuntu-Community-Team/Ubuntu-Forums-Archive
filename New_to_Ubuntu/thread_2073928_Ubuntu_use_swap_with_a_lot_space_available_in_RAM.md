---
title: "Ubuntu use swap with a lot space available in RAM"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by tariq al on 2012-10-20
[LEFT]hi , 

Ubuntu uses swap with space available in RAM :confused:

it show up when i use vmware player , and sometimes it can be slow 

ubuntu 12.04 64bit 

:mad:
[IMG]http://imageshack.us/a/img51/4002/selectionyuyyy002.png[/IMG]
[/LEFT]

---

### Post by Lisiano on 2012-10-20
Please use UbuntuOne for hosting images or just attach an image to the post as an attachment. (NVM, it wasn't visible when I looked at it)

Either way, when you use VMware or VirtualBox, ALL RAM that was allocated to a VM will be used up, if you set up VMware to swap RAM, it will be swapped. Linux won't swap until it needs to. It would help to know how much swap, RAM and how much RAM you have allocated to a VM. (Err, just how much RAM is allocated to your VM then)

---

### Post by tariq al on 2012-10-20
> **Lisiano said:**
> Please use UbuntuOne for hosting images or just attach an image to the post as an attachment. (NVM, it wasn't visible when I looked at it)

Either way, when you use VMware or VirtualBox, ALL RAM that was allocated to a VM will be used up, if you set up VMware to swap RAM, it will be swapped. Linux won't swap until it needs to. It would help to know how much swap, RAM and how much RAM you have allocated to a VM. (Err, just how much RAM is allocated to your VM then)

[COLOR=Red]i upload the image [/COLOR]
ram is 3.9G
usually i set the vm ram to 1.5G.

---

### Post by Lisiano on 2012-10-20
Did you modify the RAM Swapping in VMWare?

---

### Post by tariq al on 2012-10-20
> **Lisiano said:**
> Did you modify the RAM Swapping in VMWare?

i don't use linux in vm. i use windows . so there is no swap in there

---

### Post by Lisiano on 2012-10-20
[LIST=1]
[*]There is swap in Windows. It's called a Page File. I don't need to know this.
[*]In VMWare Options, there is a option to toggle RAM Swapping. I don't have VMWare installed atm so I can't show a screenshot.
[/LIST]

---

### Post by tariq al on 2012-10-20
> **Lisiano said:**
> 
[LIST=1]
[*]There is swap in Windows. It's called a Page File. I don't need to know this.
[*]In VMWare Options, there is a option to toggle RAM Swapping. I don't have VMWare installed atm so I can't show a screenshot.
[/LIST]



there is no option about swap !

---

### Post by Lisiano on 2012-10-20
Those are the VM options. The RAM Swapping is in VMWare options, not VM.

---

### Post by tariq al on 2012-10-20
> **Lisiano said:**
> Those are the VM options. The RAM Swapping is in VMWare options, not VM.

yah , i'm sorry 

but still no swap option ..

---

### Post by Lisiano on 2012-10-20
Ahh... Guess RAM Swapping is only available to VMWare Workstation. I am stumped then. I still think VMWare is swapping the VM but I don't know how to find out what exactly is in swap atm. Maybe someone else here knows.

---

### Post by tariq al on 2012-10-20
thank you [Lisiano]("http://ubuntuforums.org/member.php?u=1108763") 

i hope i find some one help me

---

