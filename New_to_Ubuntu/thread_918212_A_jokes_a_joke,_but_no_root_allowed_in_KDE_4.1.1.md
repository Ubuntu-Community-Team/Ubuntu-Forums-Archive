---
title: "A jokes a joke, but no root allowed in KDE 4.1.1?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by gregphil on 2008-09-12
So I just installed the brand new flashy KDE 4.1.1 to try out today.

It won't let me login as root, and it won't let me 'su' to root (claims authentication failed).

This makes the whole install basically worthless because I can't change (fix) anything.

So what is the secret? I am using the password I provided at install time for the one (1) user it let me make.  This is the same (the only) password I use to login with the one user that exists.  That user does not seem to have any ability to edit anything outside his home directory.

Help ?

---

### Post by slmouradian on 2008-09-12
did you try
```
sudo su
```
and then type in your password?

---

### Post by The Cog on 2008-09-12
Use sudo to launch your commands. For an extended session, **sudo -i** gives you a root prompt.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by gregphil on 2008-09-12
I bow down to the master.     (sudo su worked)

But....why do I have to use "sudo" to invoke "su", I never have had to do that in any previous releases?  (su alone used to work just fine)

BTW what is the KDE 4.1.1 command for a graphical sudo? (sort of like gksu for gnome).  For example if I want to use kate to edit a system file....

Thank You   again !

---

### Post by Oldsoldier2003 on 2008-09-12
> **gregphil said:**
> 

BTW what is the KDE 4.1.1 command for a graphical sudo? (sort of like gksu for gnome).  For example if I want to use kate to edit a system file....

Thank You   again !

kdesu

---

### Post by t0p on 2008-09-12
> **gregphil said:**
> 
But....why do I have to use "sudo" to invoke "su", I never have had to do that in any previous releases?  (su alone used to work just fine)


You used to use *su* in previous versions of kubuntu?  Surely not!  Root login has been disabled in *ubuntu since... well, since forever!  And as root login is disabled, so is the use of *su* by itself... cos it requires the user to type in the root password, and in *ubuntu there is no root password.

---

### Post by gregphil on 2008-09-12
Ah, but that is one of the first things I fix,  to allow root logins: 

 Just edit /etc/kde4/kdm/kdmrc and in the [x-*-core] section add the line AllowRootLogin=true

If I don't do this I spend at least one third of my command time re-entering commands with "su" in front of them, so being able to login as root when I know I am going to be doing a lot of system configuration just makes sense.  I have been operating computers for too long to think about, and have never "erased all my files" or made any other serious errors.  It is like the trash can, if I delete a file I don't expect the operating system to let me change my mind later. 

Thanks for the response.

---

### Post by anjilslaire on 2008-09-12
While that may be fine for yourself, it's certainly not appropriate to endorse for everybody. Lets hope you're not giving that advice out to everyone you give assistance to.

---

### Post by Rolcol on 2008-09-12
The root user is still there but with a randomized password.  Using "sudo" escalates your user to root privileges.  Invoke the passwd command to change the root password if you want to "activate" it.
```
sudo passwd root
```

---

### Post by cwsnyder on 2008-09-12
> **gregphil said:**
> Ah, but that is one of the first things I fix,  to allow root logins: 

 

If I don't do this I spend at least one third of my command time re-entering commands with "su" in front of them, so being able to login as root when I know I am going to be doing a lot of system configuration just makes sense.
OK, I am confused.  In what way is Linux more secure than Windows if you spend 1/3 of the time as a Super User (Administrator) which is capable of crashing your system?  Or are you talking about time when you are not connected to the outside world?  I thought that was the reason to use Ubuntu instead of PCLinuxOS or Freespire.

---

### Post by dhtseany on 2008-09-12
> **Rolcol said:**
> The root user is still there but with a randomized password.  Using "sudo" escalates your user to root privileges.  Invoke the passwd command to change the root password if you want to "activate" it.
```
sudo passwd root
```

Agreed. Use:

```

user@localhost$: **sudo passwd root**
Password for <username>:
Enter New Unix Password:**<new password>**
Re-enter New Unix Password:**<new password>**
Password successfully updated.

$: **su root**
Password for root: **<new password>**
root@localhost$:

```

---

### Post by t0p on 2008-09-12
> **cwsnyder said:**
> OK, I am confused.  In what way is Linux more secure than Windows if you spend 1/3 of the time as a Super User (Administrator) which is capable of crashing your system?

Just in case you haven't realised this, cwsnyder: you're just as capable of crashing your computer when using *sudo*.  The only difference is, *sudo* asks if you're sure you want to accidently annihilate your system... ;)

---

### Post by Sef on 2008-09-12
What happens when you run this code from Konsole:

```
sudo apt-get update
```

---

### Post by gregphil on 2008-09-12
I never said, and don't believe, Linux is "more secure" and it is definately not "more stable".   But it is free.  The whole crash-proof issue depends on the operator.  I have also never destroyed a Windows installation (or even broken a significant feature) and I have been using computers daily since before DOS 3.3.  If you think computers are "hard to use" these days, you should have tried to get a network up and running during the "Windows for Workgroups" days (the alpha days of Microsoft's version of  TCP/IP).  Four hours of up-time was considered a blessing, and you had to "save you work" every few minutes or risk loss of all your data.

If you can "use" a computer while never changing a file outside your home directory, go for it.  I find I am almost never in my home directory tree.  This week I installed two new hard disks (and an external USB disk) and got ubuntu, kbuntu, and KDE 4.1.1 kubuntu running on these three disks.  And during all this I managed to keep the original Windows XP disk untouched and bootable (the MBR was not over written etc).  Almost none of this can be done from the "user" login.

I can also say that if Linux keeps adding unneeded and unwanted security road blocks, that Linux will become as popular as Windows Vista is today.  Have you ever tried to "use" Vista?  Who cares if it is "more secure" if it is unusable.

Thank You.

---

### Post by t0p on 2008-09-12
> **gregphil said:**
> If you think computers are "hard to use" these days, you should have tried to get a network up and running during the "Windows for Workgroups" days (the alpha days of Microsoft's version of  TCP/IP).


You mean it's in beta now? :p

---

### Post by LowSky on 2008-09-12
> **gregphil said:**
> 

If you can "use" a computer while never changing a file outside your home directory, go for it.  I find I am almost never in my home directory tree.  This week I installed two new hard disks (and an external USB disk) and got ubuntu, kbuntu, and KDE 4.1.1 kubuntu running on these three disks.  And during all this I managed to keep the original Windows XP disk untouched and bootable (the MBR was not over written etc).  Almost none of this can be done from the "user" login.
No actually it can all be done safely from the Install LiveCD
For a guy who knows what he's doing he doing a lot of stuff he doesn't need to.
First off I think I need "Sudo" maybe once/twice a week. Once you get all the apps and programs you need, root access isn't needed often.
Second, why install Ubuntu and Kubuntu, and Kubuntu  with KDE4. The great thing about Linux is that you can have multiple desktop managers installed all on the same partition/kernel, saving space.
Third keeping Windows untouched and bootable without messing with its MBR is very easy, just keep it on a separate hard drive and make sure the Linux drive is the first bootable drive from BIOS. Problem solved. No need to access root as the installation should put it onto Grub with no issues (at least I know mine was). So For me who has a Ubuntu/OpenSolaris/Windows booting machine, I think I know what I'm talking about...

:guitar: ROCK ON!!!

---

