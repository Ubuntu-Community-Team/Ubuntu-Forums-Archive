---
title: "terminal with mouse capability in ubuntu server inside virtual box"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by svee on 2012-11-22
I am on lubuntu 12.10 (Host OS) AMD E.350 processor Sony VAIO VPCY.

Installed Ubuntu 12.10 server in a virtual box  4.2.4. Status in virtual box shows mouse integration is on. I have a touchpad...

My main purpose is to be able to cut and paste some installation commands inside the terminal. But the mouse does not work on default login terminal. On host OS, I use Lxterminal...

What I should be installing/running in server to have mouse capability inside the terminal ?

---

### Post by nothingspecial on 2012-11-22
gpm lets you use the mouse on the console.

Also things like screen and tmux let you copy and paste with the keyboard. The keybindings are cumbersome at first but like anything, once you get used to them, it's very easy.

---

### Post by svee on 2012-11-22
Thank you...

After going through server gui page, I figured out about byobu which is built into server. ([https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI))

However, my copy buffer is not intact when I move from host (where I am browsing online document for some set up commands) and virtual box guest where my terminal/byobu is running on server.

may have to setup remote login to take care of that. Don't know if there any way to keep the contents of Ctrl-C and paste it inside terminal of virtualbox.

---

### Post by Cheesemill on 2012-11-23
Just install openssh-server on the VM and then ssh into into it, you can then copy and paste commands into the terminal.

---

### Post by oldgraf on 2012-11-23
Yes, I think copy/paste required vbox guest additions installed

---

### Post by svee on 2012-11-23
ssh works for my purpose.... marking it solved.

However guest additions did not work for me with copy paste. Installed guest additions and enabled clipboard option in VM but was not able to paste whatever I copied on host OS.

---

