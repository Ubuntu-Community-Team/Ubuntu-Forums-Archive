---
title: "where is /var/run/lightdm/root/:0"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by seattle vic on 2011-10-30
I've been using x11vnc to remotely log into several other computers by first logging in via ssh and opening port 5900.  When I reboot a machine remotely where it's sitting at the greeter, I have to use the -auth command, like:


sudo x11vnc -forever -nomodtweak -auth /home/vic/.Xauthority -display :0 -usepw 

When I upgraded to 11.10, the greeter became lightdm (even though I installed gnome-panel for GDM), and I the figured out to use:

sudo x11vnc -forever -nomodtweak -auth /var/run/lightdm/root/:0 -display :0 -usepw

That works on one of my machines, however one other had no lightdm directory created in /var/run.  There is a gdm directory, but with no auth file that I can see; only a file called firstserver.stamp.

I tried using ~/.Xauthority like I used to with a GDM greeter, but that doesn't work.

So does anybody know why there's no lightdm/root/:0 directories and file created, and of course how I can create a new auth file?

Thanks in advance.

---

### Post by seattle vic on 2011-10-31
I guess I should add that what I believe I'm looking for is an auth file that contains the so-called MIT Magic Cookie.  I confess that I'm stumped as to where or how to create this and I've been searching for over a day now.  It was working before the upgrade to 11.10 and now it's not.

As before, there is a file called ~/.Xauthority and I've tried to refer to that in my X11vnc command, but it does not work to unlock X before the physical login.

It shouldn't be this hard as I've been doing it successfully on several computers for years...

---

