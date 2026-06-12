---
title: "Aliases"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by xXx 0wn3d xXx on 2006-06-04
This tutorial will show you how to use aliases. Aliases allow you to have a custom command in terminal carry out a different command or task. For example I can type "upgrade" in terminal and apt will update it's package list and upgrade all existing packages. To learn how to use aliases, keep reading.

**1.** Open a terminal. (Applications > Accessories > Terminal)

**2.** Type:
> sudo gedit .bashrc
Note: you can replace gedit with your text editor of choice. (kate, leafpad, nano)

**3.** Go all the way to the bottom of the bash file, to a new line. Put something like:
> # Custom Aliases
To tell you that your aliases are here.

**4.** The format for an alias is as follows:
> alias commandyouwant="command to run"

**5.** So my upgrade alias would look like this:
> alias upgrade="sudo apt-get update && sudo apt-get dist-upgrade -y"

**6.** Add as many useful aliases as you want and in the future, to add them just run step 1.

Here are all the aliases I have. I hope you find them useful.

> # Custom Aliases
alias upgrade="sudo apt-get update && sudo apt-get dist-upgrade -y"
alias update="sudo apt-get update"
alias sources="sudo gedit /etc/apt/sources.list"
alias menu.lst="sudo gedit /boot/grub/menu.lst"
alias rootb="gksudo nautilus"
alias info="uname -a"
alias bz2="sudo tar -xvfj"
alias tgz="sudo tar -xvfz"
alias wget="sudo wget"
alias nano="sudo nano"
alias search="sudo apt-cache search"
alias remove="sudo apt-get remove"
alias gedit="sudo gedit"
alias synaptic="gksudo synaptic"
alias install="sudo apt-get install"
alias azureus="sudo /opt/azureus/azureus"
alias gimp="sudo gimp-2.2"
alias rootk="sudo chkrootkit"
alias rootkit="sudo rkhunter -c"
alias rk="sudo rkhunter -c"
alias clean="sudo rm -fr $HOME/.Trash/"
alias home="cd ~"
alias dl="sudo wget"
alias prelink="sudo /etc/cron.daily/prelink"
alias purge="sudo apt-get --purge remove"
alias lookup="gnome-dictionary"
alias defrag="sudo defrag"
alias run="sudo sysv-rc-conf"
alias disk="sudo hdparm -t /dev/hda"
alias azureus="sudo /opt/azureus/azureus"
alias xorg="sudo gedit /etc/X11/xorg.conf"

I hope you found this tutorial useful. Please notify me of any errors or typos. Thanks. :)

---

