---
title: "Veracrypt on ubuntu"
date: 2021-10-27
forum: New to Ubuntu
---

### Post by uros-likar on 2021-10-27
Hi,

I just migrated from Windows to Ubuntu (KDE) and I more or less successfully installed and configured all I need. 

On windows I used Vera crypt to store some sensitive data. I checked if veraCrypt exist on linux and it does, so I installed it. I didn't got any errors on install but when I try to start it, window just opens for a half second and then immediately is closed. 

This happened me on some other program I tested, but then I found alternative for it. 

My question is how to debug this, how to find what is the cause and how to fix it. Not specifically for veraCrypt (that too) but in general.

Thanx for all suggestions

---

### Post by ActionParsnip on 2021-10-27
How did you install it? What steps did you take, please?

---

### Post by ActionParsnip on 2021-10-27
I found this online
[https://kifarunix.com/install-and-setup-veracrypt-on-ubuntu-20-04/](https://kifarunix.com/install-and-setup-veracrypt-on-ubuntu-20-04/)

---

### Post by uros-likar on 2021-10-27
Good question :) I+m not 100% sure, because at that time I tested various things but I downloaded it from [https://www.veracrypt.fr/en/Downloads.html](https://www.veracrypt.fr/en/Downloads.html) extract it and then ran that .deb file inside with whatever ubuntu program advised me to.

---

### Post by aeronutt on 2021-10-27
I've used veracrypt and ubuntu for years, and it's usually pretty stable and problem free.

On a command line, type:

> veracrypt -t --version

> which veracrypt

Then, run veracrypt from the command line (which normally will launch the GUI), and report any results in the terminal.

> veracrypt

---

### Post by uros-likar on 2021-10-27
Thanx for info. Apparently something is missing:

[FONT=monospace][COLOR=#000000]/lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by veracrypt)[/COLOR]

Now I'm searching what is this and how to install it :)
[/FONT]

---

### Post by Butthead on 2021-10-27
What's the matter with  using "vaults" in Kubuntu? :confused:

---

### Post by uros-likar on 2021-10-28
As linux noob I don't have a clue what you mean by "using vaults in Kubuntu" :)

---

### Post by Impavidus on 2021-10-28
It appears that the version of veracrypt you downloaded was compiled for libc6 version 2.33. That version is only used on Ubuntu 21.04. Have you made sure you downloaded the right .deb package for the version of Ubuntu you run?

---

### Post by Butthead on 2021-10-28
> **uros-likar said:**
> As linux noob I don't have a clue what you mean by "using vaults in Kubuntu" :)

It allows you to store sensitive subject material in Kubuntu as (apparently?) VeraCrypt does.

Check to see if it's installed already in task manager (click on arrow head pointing up next to clock in task bar).

Might be version dependent (20.04 & higher?) though.

---

### Post by uros-likar on 2021-10-29
I uninstalled my version and installed new one from the link provided by [**[COLOR=#000000]ActionParsnip[/COLOR]**]("https://ubuntuforums.org/member.php?u=1079078") 

Thank you all for help

---

