---
title: "Keyboard stopped working in Terminal?"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by crazypj10 on 2013-10-13
Hi all,
First of all, sorry if this has been covered, I already feel like an idiot for asking
I'm Using Ubuntu 12.04 LTS
This was the very first time I've tried to use 'Terminal' and couldn't get keyboard to work?
I copied a link and pasted into terminal to get  Java 7 update. (it was correctly formatted for terminal, sudo aptget, etc. I'm still not sure of the syntax)
After pasting, I couldn't add anything as keyboard 'stopped working' Mouse continued to work fine
As a workaround, I opened LibreOffice Writer, did another copy and paste which worked fine, got the update plus various extra's I didn't get when I tried through GUI in Software center 
Is this a bug or did I do something wrong?
I tried opening a terminal and keyboard works fine without anything being pasted first

---

### Post by heir4c on 2013-10-13
Hello, Welkom to the forum,
Your keyboard works fine. One thing you must know: If you add a command in the terminal and you use 'sudo' than you need your password. But when you click in your password than you can't see that you typing that password in the terminal. That is normal for safety. So if you type your password in, you must do that 'blind'. And after that you click Enter.

---

### Post by crazypj10 on 2013-11-23
Hi heir4c, 
Thanks for reply, I found I have a problem with terminal, since an update the defauly colours became black on black and so 'invisible' 
As a 'workaround I changed default grey to yellow and can now see whats going on
 I tried virtual terminal (Ctrl-Alt-F1) but it refuses to allow me to log in?
sudo apt-get install--reinstall gnome terminal did not work to re-install terminal, virtual terminal will not accept password or user account name (not sure which, just get error message saying one is wrong)
I an now use terminal but still have no idea what went wrong?

---

### Post by heir4c on 2013-11-23
The command for the reinstall is:
```
sudo apt-get install --reinstall gnome-terminal
```
there is a space between install and the 2 - in front of reinstall and it is gnome-terminal with a hyphen. 


The correct name of a program that you want to use in terminal (or anywhere else) can you find in the UbuntuSoftwareCenter 
When you click on a program and than on the "more info" button below the title. 
Than in the info you will see something like this (This is for FireFox):

[IMG]http://i.imgur.com/gU1MqP6.png[/IMG]

If you have synaptic you can use that. There are all the real name's of the programs.

---

