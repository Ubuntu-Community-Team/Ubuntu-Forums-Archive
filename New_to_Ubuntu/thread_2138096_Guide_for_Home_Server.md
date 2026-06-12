---
title: "Guide for Home Server"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by thenewasbo on 2013-04-22
I'm new to Ubuntu. I couldn't get it working properly last time but I have a new setup and I'll be installing Ubuntu on it. I'm looking for guides for an absolute beginner, and not just a list of random commands. I'm also looking for a guide on what hardware is needed for a home server. I have an older PC I'd like to use. A guide for how to configure an Ubuntu server would also be useful to me. I need to know how to prevent some files from being deleted or modified, because I want everyone to be able to access the files on the server and stream the video, which means my little brother should be able to watch his cartoons without deleting my documents.

---

### Post by deadflowr on 2013-04-22
cat

No wait, no more random commands.

You should look at the official wiki's on getting yourself situated.

[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

This is for 12.04.

Servers can be all over the place in terms of their function, but I'd start out with something like a file server.

---

### Post by slickymaster on 2013-04-23
Another good support you can grab is the [New Docs]("https://help.ubuntu.com/community/NewDocs"). It's a alphabetical listing within a Contents Wiki for available Community Ubuntu Documentation. In your case I would recommend you to take a look at the entries for servers, under the letter [S]("https://help.ubuntu.com/community/S").
It was created by a forum contributor, [BlinkinCat]("http://ubuntuforums.org/member.php?u=1392276").

---

### Post by thenewasbo on 2013-04-23
Thanks. I'm still kind of looking for a guide on basic commands that we should all know. I just got Ubuntu 12.04 installed. I was also wondering how I could set Windows 7 to be my default OS instead of Ubuntu. I sometimes turn my PC on and walk out of the room while it's booting up.

EDIT: And now, it seems that Ubuntu won't boot. It get's to the Grub loader, then after I choose Ubuntu, it just hangs on this flashing little horizontal line. All I did when I first installed Ubuntu was update the driver to the recommended one. Any idea what I should do?

---

### Post by slickymaster on 2013-04-24
> **thenewasbo said:**
> Thanks. I'm still kind of looking for a guide on basic commands that we should all know. I just got Ubuntu 12.04 installed.
[Bash Reference Manual]("http://www.gnu.org/software/bash/manual/bash.html")
[Learning the shell]("http://linuxcommand.org/learning_the_shell.php")
[Ubuntu manual]("http://ubuntu-manual.org/")
[NewDocs - A Ubuntu Documentation Search Tool]("https://help.ubuntu.com/community/NewDocs")
> **thenewasbo said:**
>  I was also wondering how I could set Windows 7 to be my default OS instead of Ubuntu. I sometimes turn my PC on and walk out of the room while it's booting up.

An easy way to switch back to using Windows as the default operating system in the Grub loader is to edit your **/etc/default/grub**
At a terminal window run the following:
```
gksudo geany /etc/default/grub
```Note that if you don't have geany, you'll have to use your installed notebook.
When prompted, enter your password, as you'll be editing a system file. In the file, look for the following line **GRUB_DEFAULT=0 **which means Ubuntu is the default boot entry, as it is the 0th entry. You will need to change that number 0 to match the Windows boot section. Typically it’s always going to be 4 on a default dual-boot configuration. Change this value to 4, and then save and close the file.
After that, again at a terminal window, run the following command:
```
sudo update-grub
``` and reboot your machine. You should go into Windows instead of Ubuntu automatically.

---

### Post by slickymaster on 2013-04-24
> **thenewasbo said:**
> EDIT: And now, it seems that Ubuntu won't boot. It get's to the Grub loader, then after I choose Ubuntu, it just hangs on this flashing little horizontal line. All I did when I first installed Ubuntu was update the driver to the recommended one. Any idea what I should do?
What driver did you update? What is you computer's graphics card?

---

### Post by Paqman on 2013-04-24
> **thenewasbo said:**
>  I'm looking for guides for an absolute beginner, and not just a list of random commands. I'm also looking for a guide on what hardware is needed for a home server.

That really depends on what you're going to do with it. What do you want to use the server for? File server? Print? Mail? Firewall/proxy? Gaming? What clients have you got on the network? How would you prefer to maintain it (SSH into the command line or a GUI tool like Webmin?).

Let us know some more about what you'd like to set up first and we can point you at the relevant information.

---

### Post by mastablasta on 2013-04-24
> **thenewasbo said:**
> . I'm also looking for a guide on what hardware is needed for a home server. I have an older PC I'd like to use. 

what kind of older PC? for server you need motherbaord, RAM, CPU, PSU and hard disk, network card or chip. that's about it

> 
A guide for how to configure an Ubuntu server would also be useful to me. I need to know how to prevent some files from being deleted or modified, because I want everyone to be able to access the files on the server and stream the video, which means my little brother should be able to watch his cartoons without deleting my documents.

you do that with users and permissions. each user can have different permisison. in this case your little brother will have access only to his home folder and maybe some place where his data (cartoons) are if they are not in his home folder.

if you are not into command line have a look at
webmin - administer your server via browser
zentyal  - another GUI interface as well as ubutnu based distribution. i htink their community verison is free. anyway it's ment for us newbies.

---
if you are looking for out of the box solution have a look at openmediavault - debian based server with GUI for file server and such.

if you plan to use the server only for media files then have a look at XBMC and openelec solutions.

> **thenewasbo said:**
> 
EDIT: And now, it seems that Ubuntu won't boot. It get's to the Grub loader, then after I choose Ubuntu, it just hangs on this flashing little horizontal line. All I did when I first installed Ubuntu was update the driver to the recommended one. Any idea what I should do?
you need to use boto options maybe (try nomodeset). if not ...
...wrong driver then. boot into recovery mode and remove the driver. what are your system specs?

> **slickymaster said:**
> Note that if you don't have geany, you'll have to use your installed notebook.
.

replace geany with gedit (gedit is default i htink. anyway you are looking to open this in some notepad / text file editor

---

### Post by thenewasbo on 2013-04-24
I reinstalled Ubuntu. All works well now.

---

### Post by thenewasbo on 2013-04-25
Before I try to set up a server I was wondering what they can do. I'd like to be able to open video files through that computer. I'd also like to host Teamspeak Server Software and video game dedicated server software. Could I manage and configure that server from a remote computer, even from one on the same network?

---

