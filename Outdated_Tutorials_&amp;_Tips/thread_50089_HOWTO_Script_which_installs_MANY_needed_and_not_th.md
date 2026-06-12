---
title: "HOWTO: Script which installs MANY needed and not that needed programs! A Must Have!"
date: 2005-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by hannes_ on 2005-07-19
Hi every1 out there.

I just finished this small script.

Well i do have to install my and other ubuntus very often and i hated it to install every package, so I made this little script.

This is what i can install by now:
```

Please verify what you just entered.

Do you want to update your apt sources?:   n
Do you want to update your system right now?:   n
Do you want to install KDE Desktop environment?:   n
Do you want to install a DVD and CD Ripper?:   n
Do you want to use the standart Firefox icons?:   n
pressing strg+alt+entf --> System Monitor like in windows?:   n
Do you want to install SMEG?:   n
Do you want to install Java Sun?:   n
Do you want to install FireFox Flash plugin?:   n
Do you want to install Acrobat Reader with all its plugins?:   n
Do you want to install licq?:   n
Do you want to install Download Manager d4x?:   n
Do you want to install FTP Client gftp?:   n
Do you want to install Bitorrent Client Azureus?:   n
Do you want to install Skype?:   n
Do you want to install ALL multimedia Codecs?:   n
Do you want to install Xine for video playback?:   n
Do you want to install Mplayer with Firefox integration?:   n
Do you want to install XMMS for music playback?:   n
Do you want to install Realplayer?:   n
Do you want to install Xchat including systray integration:   n
Do you want to install CD and DVD burner gnomebacker?:   n
Do you want to install Firestarter as your personal Firewall?:   n
Do you want to update rar and unrar?:   n
Do you want to install extra Fonts including Microsoft Core Fonts?:   n
Do you want to install Tuxracer, Supertux, Frozen Bubble?:   n
Do you want to install standart compilers?:   n
Do you want to install the NVIDIA Kernel Module? [ONLY 4 NVIDIA CARDS]:   n
Do you want to install ssh support?:   n
Do you want to install Proftpd Server?:   n
Do you want to install Teamspeak Client?:   n
Do you want to install IglooFTP Client?:   n
Do you want to install FireFox 1.1 Beta?:   n
Do you want to install Midnight Commander?:   n
Do you want to install XQF Server Browser?:   n
Do you want to install Splashy?:   n
Do you want to install Wine?:   n
Do you want to install Opera?:   n
Do you want to install Amsn?:   n
All Settings ok [y/n]?

```

every little package can be selected to be installed or not to be installed.

I did update the apt sources, optimized for germany, but they should work for everyone. Just for your knowledege: Your ubuntu will use universe and multiverse sources.

INSTALL:

Just unpack the tar file to your home directory:

thats what it should look like.
> 
/home/your_username/ubuntu_install_light

> 
cd /home/your_username/ubuntu_install_light
sh install.sh

any questions or hints, pls write them here or mail me

[email]hannes@ma-scripts.org[/email]

thx to ubuntuguide.org and the whole ubuntuforums.

gl and hf with it.

---

### Post by hannes_ on 2005-07-19
Please be carfull with the kernel update option, pls only do this if u know what you are doing.

use this script @ your own risk

---

### Post by bored2k on 2005-07-19
[QUOTE=hannes_]use this script @ your own risk[/QUOTE]
Totally agree.

Also, teh script has some typos like Bitorrent instead of BitTorrent. And Its best to include Beep media player instead of XMMS.

---

### Post by Seer on 2005-07-25
[QUOTE=bored2k]Totally agree.

Also, teh script has some typos like Bitorrent instead of BitTorrent. And Its best to include Beep media player instead of XMMS.[/QUOTE]
 This looks like a very handy little script with just about every important (to me!) app :)

Thanks for the time and effort!! :D

---

### Post by mike998 on 2005-07-25
Nice work - Very similar to my own reinstall/reconfigure process!

---

### Post by hannes_ on 2005-07-25
[QUOTE=mike998]Nice work - Very similar to my own reinstall/reconfigure process![/QUOTE]
 there will be a new version soon, i will update this thread asap.

greets

---

### Post by ubuntp on 2005-07-25
[QUOTE=hannes_]
pressing strg+alt+entf --> System Monitor like in windows?:   n[/QUOTE]
That's Ctrl+Alt+Del in english ;)

---

### Post by hannes_ on 2005-07-26
[QUOTE=ubuntp]That's Ctrl+Alt+Del in english ;)[/QUOTE]
 thx for the hint, i will update this :)

---

### Post by sevenroot on 2005-07-26
Its works for ubuntu 64?

---

### Post by charlieg on 2005-07-27
I'd go with vsftpd over Proftpd, personally. :)

---

### Post by hannes_ on 2005-07-31
[QUOTE=charlieg]I'd go with vsftpd over Proftpd, personally. :)[/QUOTE]
 i can add vsftpd :)

no idea with ubuntu64 just give it a try :)

---

### Post by Pizza the Hutt on 2006-03-03
I have tried your script, but realized too late that it was for Hoary. I have Breezy and it completely killed my GUI. I can only use the console now, but that is like driving blindfolded through the city. Without a GUI I am absolutely helpless. Please tell me how to recover my GUI and please be specific.

---

### Post by bored2k on 2006-03-03
Try sudo dpkg-reconfigure xserver-xorg , then reboot or startx.

---

### Post by Pizza the Hutt on 2006-03-04
Thanks for trying to help me, but it didn't work. I got a message that x-server-xorg is not installed.

Every time I try apt-get update I get the following message:

```
couldn't stat source package list http:// ftp2.caliu.info hoary-
backports/multiverse Packages(/var/lib/apt/lists/ftp2.caliu.info_pub
_mirror_ubuntu_backPorts_dists_hoary-backports-restricted_binary_i386
_packages_stat(2 no such file or directory)
```

I got the same message many times when running the script. I think it means that the caliu.info server doesn't work anymore. That might be the reason why everything is screwed up.
Now please tell me someone what to change and how to change it that it uses a different server, so I can make my GUI work again.

---

### Post by Gracye on 2006-04-05
wow, this script is awesome! Thanks so much for writing it :)

---

