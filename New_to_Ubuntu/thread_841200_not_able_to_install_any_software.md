---
title: "not able to install any software"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by mental on 2008-06-26
I am not able to go to the root directory...
"su"  command is not working for me....

---

### Post by _sphinx_ on 2008-06-26
What happens when you type "su". Post the output. I think that would be necessary.
Why don't you try:```
sudo <command>
```

---

### Post by rolnics on 2008-06-26
the root account is locked by default in Ubuntu. You need to use sudo. you can use either sudo apt-get install (program name here) if you know the program you want to install or you can use Synaptic Program Manager. Which is found via the System -> Administration menu

---

### Post by wormser on 2008-06-26
Ubuntu does not set up root by default.  Instead Ubuntu uses [sudo and gksudo]("https://wiki.ubuntu.com/RootSudo").  What exactly are you trying to do?

---

### Post by mental on 2008-06-26
i was trying to do a ***[COLOR="Red"]make install[/COLOR]*** of the software.... my understanding id that the make install step needs to be performed as root

---

### Post by Lod on 2008-06-26
you can do "sudo su" which turns the session into a root session.

---

### Post by t0p on 2008-06-26
> **mental said:**
> I am not able to go to the root directory...
"su"  command is not working for me....

You don't need su (or sudo) to go to the root directory.  Open a terminal and give the command
```
cd /
```
This will take you to the root directory.  Of course, you'll need to use sudo to change anything in the root directory.

---

### Post by Lod on 2008-06-26
:) He probably meant /root directory.

---

### Post by Canis familiaris on 2008-06-26
If you want to use su

```
sudo su
```

Keep in mind you can damage your system with a bad command here.

---

### Post by brettg on 2008-06-26
Alternate solution;

sudo -i

---

### Post by mcduck on 2008-06-26
> **brettg said:**
> Alternate solution;

sudo -i
This is actually better way than using 'sudo su', as 'sudo -i' loads root's environment variables and other stuff correctly while 'sudo su' doesn't.

Most of the time there's no difference, but you'll certainly notice when your home or setting files end messed up.. Better learn the habit of using 'sudo -i'.. ;)

---

