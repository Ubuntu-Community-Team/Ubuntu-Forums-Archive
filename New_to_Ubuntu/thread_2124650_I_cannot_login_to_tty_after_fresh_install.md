---
title: "I cannot login to tty after fresh install"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by rompelstilchen on 2013-03-11
hello

after a fresh xubuntu (quetzal) inlstall , i wanted to install the nvidia drivers
but i cannot login to tty1 with my regular login name
lthough it works in xfce terminal emulator (with sudo for instance)

pls help ... :-(

---

### Post by Bashing-om on 2013-03-11
rompelstilchen; Hi ! Welcome to the forum .

It is unclear to me the nature of your problem. Do you mean that the key combo ctl+alt+f1 does not yield tty1 console, or once to tty1 your username and/or password is not accepted ? What are you attempting to do and what steps are you taking to attempt to do so ?[INDENT=2]try'n to help

[/INDENT]

---

### Post by solarghost on 2013-03-12
What username are you trying to log in with? Best way to check that you are logging in with the correct username is in your UI session open the terminal and type the command ```
whoami
``` then make sure you are trying to login with whatever whoami returns.

---

### Post by rompelstilchen on 2013-03-13
i go to the tty1 with alt+ctrl+F1
and i use my regular user (the one who works with sudo)
so i use my user name/my password
the only user i created at install time

---

### Post by sudodus on 2013-03-13
Do you have some special characters in your user name or your password, I mean some character with a higher ascii number than 127?

---

### Post by rompelstilchen on 2013-03-13
well it says that i am logged with the user i created at intall time
so i guess that user is created for x sessions, not for tty sessions, but i dont know how to achieve this, and if it is a good idea(security reasons)

the plan is to install nvidia drivers for an old geforce 4200

i found the drivers, but it requires to be done with no x running
so i guess i would have to turn off lightdm too

but i need to be able to login in tty1/2/3...

---

### Post by rompelstilchen on 2013-03-13
nop 4 regular letters

---

### Post by sudodus on 2013-03-13
- Do you get the prompt to log in after ***ctrl + alt + F1*** ?

- What is written, after you enter your user name?

- What is written, after you enter your password? There is no output while you type your password, just finish with the ENTER key.

---

### Post by rompelstilchen on 2013-03-13
look i have used termi,nals for years, i just put my question in the beginner question cos it is an easy first attemp question
i installed xubuntu (and on the xubuntu web page, i got redirected here)

so it is like



login : i type my 4 letters login then enter]
password : i type my password [enter]

wrong login and password

login :

---

### Post by sudodus on 2013-03-13
I see that you know what to do. And I have to admit that I don't understand what is happening.

There is something wrong, your system should allow this.

1. Do you use some special locale (national keyboard setting), that would be different between the graphical user interface and the text screen?

2. Try to log in via the ***recovery mode*** at the grub menu.

3. Maybe you can try this work-around: (If you need, you can restore it when booted from the Xubuntu install drive.)

Backup these two files (to be restored if necessary).

```
sudo cp -p /etc/default/grub /etc/default/grub.sav
sudo cp -p /boot/grub/grub.cfg /boot/grub/grub.cfg.sav
```

edit your ***/etc/default/grub*** file. Change the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```
(save the file) and run
```
sudo update-grub
```
and reboot. Now you should arrive directly at a text screen. I hope you can log in.

---

### Post by rompelstilchen on 2013-03-13
ok, i dont know why but it does not work with the num pad (num lock is on)
so from what you wrote me back, i just gave
it a try with the other numbers from the keyboard(SHIFT+1 /2 /3 ...) and  it worked)
wtf ???

anyway thx for your precious help :-)

---

### Post by rompelstilchen on 2013-03-13
can you chenge this to solved ? i cant edit the title of this thread
thx

---

### Post by BlinkinCat on 2013-03-13
Hi,

Here's how -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by sudodus on 2013-03-13
> **rompelstilchen said:**
> ok, i dont know why but it does not work with the num pad (num lock is on)
so from what you wrote me back, i just gave
it a try with the other numbers from the keyboard(SHIFT+1 /2 /3 ...) and  it worked)
wtf ???

anyway thx for your precious help :-)

Congratulations, you found it :KS

---

### Post by rompelstilchen on 2013-03-13
well i tried that
cant edit tile as mentioned earlier ;-)

---

### Post by sudodus on 2013-03-13
> **rompelstilchen said:**
> well i tried that
cant edit tile as mentioned earlier ;-)

This is a temporary solution, but it works.

Go to the first post in this thread. Click the ***edit*** button to open an editing window. Then click on ***advanced*** and, above the editing window you will find a small window, where you can change the prefix to SOLVED. Click the ***save*** button, and it's done.

---

