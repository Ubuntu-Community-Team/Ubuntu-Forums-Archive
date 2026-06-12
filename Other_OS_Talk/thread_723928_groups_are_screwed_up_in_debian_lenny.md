---
title: "groups are screwed up in debian lenny"
date: 2008-03-14
forum: Other OS Talk
---

### Post by myusername on 2008-03-14
i tryed to add myself to the Debian-exim group through the users & groups app and it said something along the lines of no uppercase letters and so i changed it to debian-exim and saved and then i try to use the terminal to install something and i get this:

andrew@Debian:~$ sudo apt-get ntfs-3g

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for andrew: 
exim: failed to find gid for group name "Debian-exim"


anybody know how to fix this?

p.s.: does anybody know how to mount ntfs hd through nautilus? i also need to know how to do it automatically

---

### Post by kerry_s on 2008-03-14
> **myusername said:**
> i tryed to add myself to the Debian-exim group through the users & groups app and it said something along the lines of no uppercase letters and so i changed it to debian-exim and saved and then i try to use the terminal to install something and i get this:

andrew@Debian:~$ sudo apt-get ntfs-3g

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for andrew: 
exim: failed to find gid for group name "Debian-exim"


anybody know how to fix this?

p.s.: does anybody know how to mount ntfs hd through nautilus? i also need to know how to do it automatically

look in your /etc/groups and see if it's there.
if not you can add it manually.

you would add the drive to your /etc/fstab and create the folder for it in /media.

this
sudo apt-get ntfs-3g
is suppose to be
sudo apt-get **install** ntfs-3g

you might want to save your self some typing, make aliases in ~/.bashrc
alias install="sudo apt-get install"
alias remove="sudo apt-get remove --purge"
alias search="apt-cache search"
alias update="sudo apt-get update"
alias upgrade="sudo apt-get upgrade"

#disable root-> sudo passwd -l root
#enable root-> sudo passwd -u root

alias su='sudo su'

---

### Post by souneedalink on 2008-03-14
> **myusername said:**
> 

p.s.: does anybody know how to mount ntfs hd through nautilus? i also need to know how to do it automatically
easiest way is to add the partition to /etc/pmount.allow

---

### Post by myusername on 2008-03-14
Thanks guys/girls I'll try this in the morning

---

### Post by myusername on 2008-03-14
> **kerry_s said:**
> look in your /etc/groups and see if it's there.
if not you can add it manually.

you would add the drive to your /etc/fstab and create the folder for it in /media.

this
sudo apt-get ntfs-3g
is suppose to be
sudo apt-get **install** ntfs-3g

you might want to save your self some typing, make aliases in ~/.bashrc
alias install="sudo apt-get install"
alias remove="sudo apt-get remove --purge"
alias search="apt-cache search"
alias update="sudo apt-get update"
alias upgrade="sudo apt-get upgrade"

#disable root-> sudo passwd -l root
#enable root-> sudo passwd -u root

alias su='sudo su'

i did what you said except its /etc/group not groups and i still get this:

andrew@Debian:~$ sudo apt-get install ntfs-3g

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for andrew: 
andrew is not in the sudoers file.  This incident will be reported.

and @ souneedalink there was no


/etc/pmount.allow

---

### Post by souneedalink on 2008-03-14
default or custom install?
etch or lenny/sid?

---

### Post by myusername on 2008-03-14
> **souneedalink said:**
> default or custom install?
etch or lenny/sid?

it was a lenny netinstall

---

### Post by souneedalink on 2008-03-14
Did you select the DESKTOP ENVIRONMENT software selection or install the base system and add stuff later? Why are you using sudo? What are you doing with exim?

---

### Post by myusername on 2008-03-14
yeah I installed the desktop enviroment. I'm using Sudo to install ntfs-3g and my groups were screwed up so I went and added myself to all of them... But exim is fixed now

---

### Post by souneedalink on 2008-03-14
If you havent setup sudo then su instead....
I think I have forgot half the thread, maybe I should go back and read

---

### Post by kerry_s on 2008-03-14
so did you add yourself to the sudoers list?

su
visudo

user    ALL=(ALL) ALL

user would be your log in name

then you should be able to use sudo

---

### Post by myusername on 2008-03-14
that solved the sudo thing...now i need to know how to automount my ntfs drives...right now it says:

You are not privileged to mount the volume 'Windows'

---

