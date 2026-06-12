---
title: "Error when installin .deb files O_o"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by zloygame on 2008-09-14
Im trying to install Deluge (latest version), I downloaded latest version from the official deluge website (my Ubuntu version is 8.04), I double click on the .deb file and it starts unpacking and then error occurs - "Wrong i386 architecture". 
Same thing when im trying to install Skype. 
what is the problem? Am i doing smth wrong? Is smth wrong with my computer?
Thank u in advance.

---

### Post by kk0sse54 on 2008-09-14
It sounds like you are downloading the package for the wrong processor arch. Also Deluge should be available from the repos

---

### Post by k33bz on 2008-09-14
are you getting the right file structure for your computer

i386 deb file for an i386 computer

64 bit file for a 64 bit computer?????

---

### Post by zloygame on 2008-09-14
well i dont have any idea what i386 is, but i definetely have a 32bit computer...

btw, i dont know why, but when i try to edit source.list file it says that i dont have the permision..
how's that possible if i'm the only account on the computer?

---

### Post by Gannon8 on 2008-09-14
Root owns the file. You have to use:
```
gksudo gedit /path/to/file.txt
```
And that will open gedit as root and will allow you to edit the file.

---

### Post by aomlives on 2008-09-14
You need root permissions for that.

```
sudo gedit /etc/apt/sources.list
```

And then type the password you entered during the install.

---

### Post by kk0sse54 on 2008-09-14
You have to have root access in order to edit it. Try typing sudo in front of your command. This is done in order to increase security in Linux by restricting the access of the normal user you can't screw your computer up as easily. Read this over if you want some more info [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) or typing man sudo in terminal will  give you the man documents

---

### Post by howefield on 2008-09-14
Deluge is in the repositories, but it look like a few versions behind the one on the Deluge website.

If you are downloading from the website you need the one for Hardy, i386 which is this one....

Ubuntu 8.04 (Hardy Heron) package for i386 systems

That should install if you have a 32 bit install.

---

### Post by Sef on 2008-09-14
>  		well i dont have any idea what i386 is, but i definetely have a 32bit computer...

Let's double check that.  Applications > Accessories > Terminal

then type or paste in this command:

```
uname -a
```

Paste the results in here.


Also paste in the package name in full here.

---

### Post by zloygame on 2008-09-14
2Sef
Linux mazafaker-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

one more question there, i have a folder that only ROOT can delete, how do i do that? I mean what command should i type in to the terminal in order to delete it?=)

Thank u guys for such quick response :P

---

### Post by kk0sse54 on 2008-09-14
What folder would that be, if root access is needed to delete I can almost assure you that you probably won't want to delete it otherwise use sudo rm (type the usual man rm if you need more help on the command) but be VERY careful when removing anything with root access cause once it's gone it's gone.

---

### Post by zloygame on 2008-09-14
its qutim folder:) i have no clue how it got protected so i cant delete it in an "easy" way =)

what about information that I pasten in here from my terminal?

---

### Post by zloygame on 2008-09-14
btw, this is what i get when i try to delete this folder: 

root@mazafaker-desktop:/home/mazafaker# sudo rm qutim
rm: cannot remove `qutim': Is a directory

---

### Post by kk0sse54 on 2008-09-14
"By default, rm does not remove directories.  Use the --recursive (-r or
       -R) option to remove each listed directory, too, along with all of  its contents." -man doc :)
I cannot stress this enough to be very careful and make sure you get the exact path because sudo rm has the ability to cause a lot of damage.

---

### Post by zloygame on 2008-09-14
hey, do u have ICQ or MSN? can we talk there? It would be much faster and effecient :P 
u can PM me it=)

PS what does this mean?

> root@mazafaker-desktop:/home/mazafaker# uname -a
Linux mazafaker-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux


---

### Post by howefield on 2008-09-14
means you have a 64 bit install,

---

### Post by aomlives on 2008-09-14
Which means you either have to download the 64 bit version from the Deluge site, or type in the terminal:

```
sudo apt-get install deluge-torrent
```

---

