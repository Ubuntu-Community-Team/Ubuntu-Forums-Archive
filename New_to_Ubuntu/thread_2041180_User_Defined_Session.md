---
title: "User Defined Session"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by BlackDynamite on 2012-08-12
Hello, I would like to know what "User Defined Session" is, what it's for.

Does it load any of the startup apps from normal session?

Can I tell it to run startup apps at all and how?

---

### Post by Buntu Bunny on 2012-08-12
> **MrTwinkletits said:**
> Hello, I would like to know what "User Defined Session" is, what it's for.

Does it load any of the startup apps from normal session?

Can I tell it to run startup apps at all and how?

I was wondering the same thing. Since no one seems to be answering, maybe it's one of those things one has to try for oneself. :P

---

### Post by BlackDynamite on 2012-08-13
Bump



I cant believe noone on forum knows what its for.

---

### Post by critin on 2012-08-13
This may help.

[http://manpages.ubuntu.com/manpages/natty/man1/xsm.1.html](http://manpages.ubuntu.com/manpages/natty/man1/xsm.1.html)

---

### Post by NikTh on 2012-08-13
Hi , 
read this [http://askubuntu.com/questions/23932/how-do-i-replace-the-desktop-by-an-application](http://askubuntu.com/questions/23932/how-do-i-replace-the-desktop-by-an-application)

I never use it , but explains some things
Thanks

---

### Post by diesch on 2012-08-13
"User Defined Session" doesn't run any desktop environment, window manager or similar but just the shell script *$HOME/.xsession*. The session ends when the script ends.

You can use this to define your own session: Usually you'll start some panels, docks, applications etc in the background and then your window manager in the foreground, maybe followed by some clean up code.

---

### Post by XiaolinDraconis on 2012-10-01
> **diesch said:**
> "User Defined Session" doesn't run any desktop environment, window manager or similar but just the shell script *$HOME/.xsession*. The session ends when the script ends.

You can use this to define your own session: Usually you'll start some panels, docks, applications etc in the background and then your window manager in the foreground, maybe followed by some clean up code.

i am trying this session right now for the first time, and seeing what you wrote made me look for that file, its not there. :???:

---

### Post by diesch on 2012-10-02
Just create it and make it executable.

---

### Post by newb85 on 2012-10-03
You can see the files for each session in /usr/share/xsessions.

The user-defined session is xsession.desktop.  Simply removing that file will take the option off the login screen.

---

### Post by vasa1 on 2012-10-03
> **newb85 said:**
> You can see the files for each session in /usr/share/xsessions.

The user-defined session is xsession.desktop.  Simply removing that file will take the option off the login screen.
I see my usual log-in options listed as .desktop files in this folder. I don't see xsession.desktop here and I don't see it as a log-in option either.

---

### Post by newb85 on 2012-10-03
> **vasa1 said:**
> I see my usual log-in options listed as .desktop files in this folder. I don't see xsession.desktop here and I don't see it as a log-in option either.

I don't think it's there by default.  If I remember right, it only appeared when I installed a different DE.  (I currently have Cinnamon, Gnome, Cairo-Dock, and LXDE installed, and I haven't the foggiest which one it was.)

---

### Post by Buntu Bunny on 2012-10-04
I appreciate this discussion. Looks like something I probably won't experiment with.

---

### Post by vasa1 on 2012-10-04
> **newb85 said:**
> I don't think it's there by default.  If I remember right, it only appeared when I installed a different DE.  (I currently have Cinnamon, Gnome, Cairo-Dock, and LXDE installed, and I haven't the foggiest which one it was.)
I have ten:
GNOME
GNOME Classic
GNOME Classic (No effects)
GNOME / Openbox
Lubuntu
Lubuntu Netbook
Openbox
Ubuntu
Ubuntu 2D
Xfce Session

I think the GNOME ones snuck in with GNOME Tweak Tool. The Openbox came with the Lubuntu Desktop and Xfce Session is there because I installed Xfce 4.10.

---

