---
title: "new to ubuntu"
date: 2019-09-26
forum: New to Ubuntu
---

### Post by zinzin112 on 2019-09-26
[COLOR=#141414][FONT=Georgia]Hi there,[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]I installed ubuntu 19.4 e few these ago..and its working great![/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]But there a few question that i want to ask. i hope some can help out there.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]This ubuntu pc is not connected to internet and for now on it will not be connected to the internet.[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]So i will need to do some installations without internet. [/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]I need to install VLC and adobe reader.[/FONT][/COLOR]
[COLOR=#141414][FONT=Georgia]So what i'm trying to tell is i need the "installer" to put them on a usbstick. and install them on the machine.[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]I have visited many sites but what i get is the command line to do the installation ( i guess you need internet to do it or not) but i dont get the installer to download so i can put it on a stick.[/FONT][/COLOR]

[COLOR=#141414][FONT=Georgia]I hope i have been clear enough.
Thank[/FONT][/COLOR]s!
Zin.

---

### Post by Holger_Gehrke on 2019-09-26
Welcome to Ubuntu and to the forum !

You really don't want (or need) Adobe Reader. Development and maintenance of the Linux-version was stopped by Adobe several years ago. The "Document Viewer" (the actual program behind that generic name is 'evince', I believe) that should be included in Ubuntu can view pdf-files, but lags behind in features a bit. So if you regularly need to open pdf-files which make use of the "latest  and greatest" features of the pdf-format, you've got a problem ...

Installing on an offline computer is more difficult because of the way programs are packaged. 

The "normal" way to install software uses package files in the Debian-format. The programs are split rather finely into multiple files to enable re-use of libraries and other components. There is a dependency mechanism in play, so if you install one package with 'sudo apt install "packagename"', the package-manager downloads all the needed packages and installs them in the right order. You can use 'apt install --dry-run "packagename"' in the terminal on the offline machine to find out what packages you need for a given program. Then search and download the packages from [https://packages.ubuntu.com](https://packages.ubuntu.com) on a machine connected to the internet. Install the downloaded packages in the reverse order they were listed using 'sudo dpkg -i "packagefilenames"'.

Alternatively you could use snap-packages, those are not split up and should contain everything the program needs to run in one or two files. The problem with this is finding actual download links, all sites offering snaps assume you're going to use either gnome-software with the snap-plugin or the snap command-line tool to download and install ... You need access to an online machine with Ubuntu to run 'snap download "packagename"' to get the packages.

Holger


Holger

---

### Post by mastablasta on 2019-09-26
snaps or.
if they have appimage, these are apps with all libraries needed. so you would download them and use them.

instead of Adobe there are many good PDF readers on linux. but if you need a commercial one then have a look at Foxit reader.

---

### Post by Impavidus on 2019-09-26
I've never used a permanently offline Ubuntu computer.

As Holger_Gehrke indicates, offline it's harder. I think that instead of installing the packages with dpkg in reverse order, you can also store them in the cache directory (/var/cache/apt/archives/) and then use apt as usual. Synaptic, a good GUI package management tool, has the option to create a download script, which you can execute on a different computer to download the packages. It can then import them from a usb drive. The next problem is updating the lists of available software in /var/lib/apt/lists/.

There are several pdf readers available from the Ubuntu repositories. All of them ultimately depend on either libpoppler or ghostscript, so if neither of those two libraries support the features you need, none of the pdf readers will work for you. Third-party pdf readers may be different.

---

### Post by oldrocker99 on 2019-09-26
These days, **EVERY** computer needs to be online. If yours is not, you'll never get updates or be able to install any software. Bear in mind that every Linux distribution is *very* secure from malware. There is a very effective firewall built-in. You do have to enable it, so:
```
sudo ufw enable
```
IF you have no access to the Interwebs, I understand. Otherwise, get online. This is not Windows; even getting a ransomware popup will not threaten any version of Linux. I know; I've been attacked that way, and I did have to kill Firefox, but you can't encrypt a disk without the user's permission, unlike That Other Operating System. It also only reboots when you tell it to reboot. And, it CAN update files while they are  in use. That's a lot smarter than M$.

Windows users ARE system administrators; they have root access. Linux users are NOT administrators; they only have temporary root access.

If a Windows user has the power to add  and remove programs, malware can do the same thing.

---

