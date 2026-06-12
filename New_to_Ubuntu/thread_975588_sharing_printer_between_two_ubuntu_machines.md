---
title: "sharing printer between two ubuntu machines?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by jeromey on 2008-11-08
i have an hp deskjet 6122 installed on a machine running ubuntu 7.10

it works perfectly on ubuntu without any setup at all

now i want to share this printer with another of my machines that is running ubuntu 8.10


on the machine that is connected to the printer i went to system-administration-printers and marked the boxes that say share this printer


now with the other machine i have no idea how to find that shared printer

if i go to places-network the only thing that comes up is "Windows Network"

i dont even have any windows computers on the network!!

so how do i connect to this printer ?

---

### Post by JKBurton on 2008-11-08
Hi, Jeromey.

You're close; just one step away :)

In System/Administration/Printing, click on the Server menu, then Connect. Enter the name (or, if that doesn't work, the IP address) of the other box. Press the Connect button on the dialog, and you should get a list of the shared printers.

Best of luck!
Keith

---

### Post by phidia on 2008-11-08
How is the printer connected and what type network do you have?

Take a look at the "Sharing Printers" section from the wiki [here]("https://help.ubuntu.com/community/Printers").

---

### Post by jeromey on 2008-11-08
> 
Hi, Jeromey.

You're close; just one step away

In System/Administration/Printing, click on the Server menu, then Connect. Enter the name (or, if that doesn't work, the IP address) of the other box. Press the Connect button on the dialog, and you should get a list of the shared printers.

Best of luck!
Keith

thanks, now i found the priter

but now if i try to print to it everything freezes up

> How is the printer connected and what type network do you have?

Take a look at the "Sharing Printers" section from the wiki here. 

the printer is connected to the machine with a usb cord, then the machine is connected to my router with an ethernet cord

the computer i am trying to share with is connected to my router with wireless (WEP)

router is connected to verizon DSL


i think the reason my compter might be freezing up could be because the router is blocking the printer ports

does anybody know which ports i should open?

---

