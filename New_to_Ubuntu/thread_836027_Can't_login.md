---
title: "Can't login"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2008-06-21
I installed language support for arabic language yesterday. And when the onstallation was complete the OS prompted me to restart my machine. Now the problem is I can't login from GDM becuase the input language is arabic, and my username is in english. I want my default language to be english. I think the default language now is arabic instead of english. I can't change the language at all. Basically I can't use my laptop at all.

I thought I had the solution when I choosed recovery mode in grub menu, and logged in using a shell, then I wanted to stop GDM from appearing, so I can change the default language settings after logging in successfuly. Well,... then I realized I don't know how to do it (stop GDM from starting) from the command line. Can anyone help?

---

### Post by housam on 2008-06-21
we will suppose that you forgot your password. follow this guide it may help :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/resetpassword_[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by Abu_Dayya on 2008-06-21
Thanks housam. But I don't think that will do the trick. Cause even if I changed my password, I still have to login through GDM, and my problem is wrong default language.

I think I know the solution, I just don't know how to do it using recovery mode from the grub menu. The solution could be either:

- Change default language to English USA (using CLI)
or
- Stop GDM from autostarting, like when you do it from (System -> Admin -> Sessions) using gnome, but this time through CLI

Guys?

---

### Post by MasterSander on 2008-06-21
You can always login in the terminal by pressing ctrl+alt+f<1-6>, the problem is you will also be prompted to login, else you could uninstall the language pack through the terminal.

---

### Post by Abu_Dayya on 2008-06-21
> **MasterSander said:**
> else you could uninstall the language pack through the terminal.

Yea, thats plausable. How do I find the name of the language pack

sudo apt-get remove "What is the name of the Arabic language pack" ??

---

### Post by Abu_Dayya on 2008-06-22
Again Guys, Does anyone know the command to :

- Change default language from whatever it is now to English USA

- Stop GDM from autostarting, like when you do it from (System -> Admin -> Sessions)

- uninstall the arabic language pack

---

### Post by MasterSander on 2008-06-22
You don't have to remove gdmgreeter from the sessions, just type top in the terminal and killall gdmgreeter. The language pack is language-pack-ar-base or language-pack-ar-gnome-base (replace by KDE if you got kubuntu)

---

### Post by MasterSander on 2008-06-22
type startx in terminal to start GUI also.

---

### Post by WitchCraft on 2008-06-22
You could try to boot with the live-cd and then change the language in the gdm config file...

---

### Post by sujoy on 2008-06-22
edit your xorg.conf in /etc/X11/

Option		"XkbLayout"	"us"

that should change the default keyboard layout to us.

---

