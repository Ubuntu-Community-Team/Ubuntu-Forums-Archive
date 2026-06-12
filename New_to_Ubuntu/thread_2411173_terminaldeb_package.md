---
title: "terminal/deb package"
date: 2019-01-26
forum: New to Ubuntu
---

### Post by ignarein on 2019-01-26
hello community,

i am a rookie on lubuntu and have two question.

1.installing via terminal.

 i try to install xed editor but i become the message
E: Unable to locate package xed
I have enable    repository main
                          repository universe
                          repository restricted
                          repository multiverse

2. About deb package

i use the GNOME Terminal 3.28.2
If i use which command for example(which php) it's no reaction
i think i have to install a deb package but wish i need or is there a other way?

many thanks in advanced for you help:p
ignarein

---

### Post by Impavidus on 2019-01-26
I don't know xed, neither does wikipedia and I can find no package or file in the Ubuntu repositories named xed.

If which gives no output, then the command you searched for is not available on the system. So you don't have an executable with the name php. Which makes sense.

---

### Post by Holger_Gehrke on 2019-01-26
The editor 'xed' is not in the standard repositories. To install it you need to add a personal package archive to the sources from which to install software ('sudo add-apt-repository ppa:embrosyn/xapps'). The usual caveats about PPAs apply.

'which' doesn't show any output if it can't find what you're looking for. There's a reason for that: 'which' is often used in scripts to check whether a tool needed by the script is available and doing any error output would probably foul up the output of the script, so 'which' doesn't do that and only sets it's exit status to a non-zero value. You can check the exit status of the last command with 'echo $?'. If 'which' wasn't installed, you'd get an error from the shell ('which: command not found' or - more likely if the package command-not-found is installed - a list of commands similar to what you entered and the package(s) you'd need to install to get these).

Holger

---

### Post by kc1di on 2019-01-26
Hello ignarein and welcome to Ubuntu forums,
xed is a mint editor and I don't believe it's available on Ubuntu.  You can install it along with other xapps by adding this ppa to your repositories. in a terminal copy and paste ```
sudo add-apt-repository ppa:embrosyn/xapps
``` hit enter when that finishes.  type ```
sudo apt update
``` when that finishes type ```
sudo apt install xed
``` Good luck.

bye the way I believe lubuntu comes with a good tex editor why do you want xed?  I think in lubuntu it is leafpad which is a good editor so if that one works why would you want to add xed?

---

### Post by Dennis N on 2019-01-26
@ignarin,

> i think i have to install a deb package

If you have Lubuntu 18.10 (cosmic), You are right. The most recent ppa packages are for 18.04 (bionic). 

I used the bionic packages for **xed** (and also **pix**, which is like gthumb) and they work correctly in Lubuntu 18.10. You just have to know how to manually install the .deb packages. Ask if you use 18.10 and don't know how - it's simple with the help of **gdebi** package installer. Important: You have to install the **xapps-common** package with them, and it has to be installed first or it's a no-go for the others.

---

