---
title: "Ubuntu wireless issues"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by LinX_User on 2008-11-26
I'm completly new to Ubuntu, and I have recently installed 8.10, but I am having issues with it detection my wireless network. It doesn't even reconize that there is a wireless, network at all. Please tell me how to fix this. Thanx in advance :D

---

### Post by Tea4all on 2008-11-26
Can you connect to the internet with a wire. If you can, just connect to the internet, go to System > Administration > Hardware Drivers. Then highlight the driver you want and press activate. You should now be able to connect with wireless. Otherwise post the output of ```
lspci; lsusb; lsmod
``` Do this by going to Applications > Accessories > Terminal, copy and paste the command, and press the enter key.

---

### Post by Olivier2371 on 2008-11-26
Hello and Welcome,

Open up the terminal.
Applications-Accessories->Terminal

then type:

sudo lspci -v | less

post the the answer.

Then type :

iwconfig

post the reply.

Sorry we wrote our post in the same times.

---

