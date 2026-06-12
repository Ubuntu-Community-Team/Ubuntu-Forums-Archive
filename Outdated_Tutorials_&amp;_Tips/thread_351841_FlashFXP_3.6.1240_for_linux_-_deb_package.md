---
title: "FlashFXP 3.6.1240 for linux - deb package"
date: 2007-02-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Sir_Yaro on 2007-02-02
UPDATE!
2009-09-02
*flashfxp_3.6.1240-4_all.deb*
[LIST]
[*] Works with 32bit and 64bit releases
[*] Patched wine removed from package
[*] Wine added as dependency

[/LIST]

#-----------------------------------------------------------#

UPDATE!
2009-07-11
*flashfxp_3.6.1240-3_i386.deb*
[LIST]
[*] Jaunty 32bit release
[/LIST]

#-----------------------------------------------------------#

UPDATE!
2008-05-04
*flashfxp_3.6.1240-2_i386.deb*
[LIST]
[*] Hardy release
[/LIST]

#-----------------------------------------------------------#

UPDATE!
2007-09-13
*flashfxp_3.6.1240-1_i386.deb*
[LIST]
[*] FlashFXP 3.6.0 used (build 1240)
[/LIST]
Know issues:
[LIST]
[*] It's impossible to delete local file or dir (delete option doesn't work anymore)
[/LIST]


#-----------------------------------------------------------#

UPDATE!
2007-09-13
*flashfxp_3.4.1145-4_i386.deb*
[LIST]
[*] Still existing "wine client error:10: version mismatch yyy/xxx." problem fixed
[*] Old setting overwrite partialy(?) fixed
[/LIST]

#-----------------------------------------------------------#

UPDATE!
2007-04-05
> **Bradl3yJ said:**
> There is an easy fix for the Edit and View bug [...]. In FlashFXP go to Options>File Associations and Click "Add". File Mask, type *. Open with 'Select Program, and browse to your wine/drive_c/windows/notepad.exe. Check the boxes for edit and view. Thats it, windows notepad is not the best editor but hey it is better than flashfxp locking up! And you could use another, better windows program to edit using this method i would imagine.

You could get more specific with spefic files such as images if you want to open in mspaint or whatever.
> **Sir_Yaro said:**
> I've tried this before and it did work for me. FF got hang up anyway. Did u actually check if this works for u or u just assume it will?
> **Bradl3yJ said:**
> Yes, fully works for me with notepad, able to edit/view, i can save the file, upload the saved version, rinse and repeat.

#-----------------------------------------------------------#

UPDATE!
2007-06-22
*flashfxp_3.4.1145-3_i386.deb*
[LIST]
[*] Backup fix (licence key)
[*] New settings directory (~/.flashfxp)
[*] Wine included in flashfxp package now works even if different wine version run atm
[/LIST]

#-----------------------------------------------------------#

UPDATE!
2007-06-01
"File View" and "File Edit" doesn't work. :( Do not use this functions. Use external viewer/editor instead.

#-----------------------------------------------------------#

UPDATE!
2007-05-26
*flashfxp_3.4.1145-2_i386.deb*
[LIST]
[*]Small start-script fix (in backup option)
[/LIST]

#-----------------------------------------------------------#

UPDATE!
2007-05-22
*flashfxp_3.4.1145-1_i386.deb*
[LIST]
[*]Patched wine (with bugfix #5131) added into package.
[*]FlashFXP 3.4.0 used (build 1145)
[*]Licence agreement added
[*]Minor attributes fix
[*]Simple weekly backup added (into ~/.flashfxp directory)
[/LIST]

#-----------------------------------------------------------#

UPDATE!
2007-05-04
*flashfxp_2.1.924-2_i386.deb*
Ubuntu Feisty compilation, bug fixes, package now depend on wine and is 6x smaller

###############################################

Addons:
[LIST]
[*]for **KDE** desktop shortcut run:
```
cp /opt/flashfxp/FlashFXP/FlashFXP\ 3.4.1145.desktop ~/Desktop/
```
[*]for **other** [windows managers]("http://en.wikipedia.org/wiki/Window_managers") run:
```
flashfxp
```

[*]**Latest **bookmarks, sites etc can be find in ~/.flashfxp/backupXY directory. XY stands for current week number. Every backup is made when FlashFXP starts.

[*]_It won't run if you running other wine app at the same time_. To be more specific  it won't run if other than /opt/flashfxp/bin/wine wine run. Sorry! I'll try to fix this in a next release.
[/LIST]

###############################################
###############################################

Download it   [[SIZE="5"][COLOR="SandyBrown"]HERE[/COLOR][/SIZE]]("http://www.mandrivalinux.eu/downloads.php?do=file&id=183&langid=1")
or you can try one of these repositories:
[http://deb.yaro.at/](http://deb.yaro.at/)
[http://yaro.gdi.pl/deb/](http://yaro.gdi.pl/deb/)

##################################################
##################################################


Hi.
I've created package contains FlashFXP 2.1.924 (it works thanks to wine).

You can download it here:
xxxx (use link above)

> FlashFXP is the most powerful and popular FTP & FXP Client for Microsoft Windows 9x/Me/NT/2000/XP on the market today. It is loaded with features for the power user, but has an intuitive user interface that takes only minutes to master. Using the FTP protocol, you can transfer files from remote servers to your computer, or even to another remote server!!! FlashFXP makes it easy to update your web site, download files from the company server, or even download files from the internet that always seem to FAIL using your web browser. It allows you to transfer files between two sites (FXP), resume incomplete downloads, synchronize directories, schedule multiple tasks, and much, much more!


Program isn't free so you will need a proper serial key.

In kde package creates shortcut in a internet menu. In a other WM you have to run it with command ```
flashfxp
``` in console or add your own shortcut.

Compiled on/for Ubuntu Edgy

Any comments are warm welcome

if you have wine already instaled on your desktop replace content of /usr/bin/flashfxp file by this:

```
#!/bin/bash
if [ `which wine` != "" ]
then
wine /opt/flashfxp/flashfxp/FlashFXP.exe
else
/opt/flashfxp/bin/wine /opt/flashfxp/flashfxp/FlashFXP.exe
fi

```
[IMG]http://66.7.200.176/~mandriva/images/rozne/1.png[/IMG]
[IMG]http://66.7.200.176/~mandriva/images/rozne/2.png[/IMG]

mirrors:
Edgy: [http://yaro.gdi.pl/deb/edgy/](http://yaro.gdi.pl/deb/edgy/)
Feisty: [http://yaro.gdi.pl/deb/feisty/](http://yaro.gdi.pl/deb/feisty/)
Gutsy: [http://yaro.gdi.pl/deb/gutsy/](http://yaro.gdi.pl/deb/gutsy/)  [http://deb.yaro.at/gutsy/](http://deb.yaro.at/gutsy/)

---

### Post by glabouni on 2007-02-02
nice! 
I've yet to find a gui ftp client under linux that meets my requirements.
I used flashfxp under windowsand haven't found any equivalent under linux.
but still, I'm wondering why did you choose such an old version . what's the point of porting a few years old version ? 
flashfxp is now v3.4, the version you've chosen to package is useless to me, just too old. 
but thanks anyways

---

### Post by Sir_Yaro on 2007-02-02
Because other (newer) versions doesn't work with wine or are not available.
If someone can find anything beetween 2.1.924 and 3.0.0 I promise to try with them.
Any version above 3.0.0 (including it) has bloken directory listing so they ain't work with wine. Afaik they work sometimes with native windows libraries (which I don't want to include in this package) but not for me.

Anyway, I think even this version has more functions than most (if not all) linux ftp clients.

---

### Post by machoo02 on 2007-02-02
I actually prefer [Filezilla]("http://filezilla.sourceforge.net/") for a gui ftp client in windows.  It [works great in WINE]("http://appdb.winehq.org/appview.php?iVersionId=1322"), and the next version (3.0 currently in beta) will have a native Linux port.

---

### Post by Aurdal on 2007-02-03
Edit, nvm.

---

### Post by Sir_Yaro on 2007-02-03
I've checked this filezilla app and I still think flashfxp is far ahead... :/
But filezilla has at least tsl and ssl support. That's something but still not enought. And from a major defects there is no fxp transfer at all in filezilla.... :/

---

### Post by hnfmr on 2007-02-07
I'm sorry but I got this error message when trying to execute flashfxp in terminal afer installing.

root@will-desktop:~/downloads# flashfxp
/opt/flashfxp/bin/wine: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /opt/flashfxp/bin/../lib/libwine.so.1)
root@will-desktop:~/downloads#

Anyone got any idea? :(

---

### Post by Sir_Yaro on 2007-02-07
install libc6-i686 package

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libc.so.6&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libc.so.6&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

---

### Post by aspen on 2007-02-09
hi there,
its really nice that u have manged to get flashfxp working with wine, 
but is there a possibility to offer also a dapper package?
i`m still using 6.0.6.1 LTS and don`t want/can`t to update.

cheers
Aspen

---

### Post by Sir_Yaro on 2007-02-14
[QUOTE="aspen"]hello Sir_Yaro,* 
 
i have just a small question. 
i have read your post about flahsfxp on ubuntforums.org and that you have manaed to get it working with wine, 
i`m still using dapper 6.0.6.1 LTS and i`d like to ask if there also exists a package for this. 
if there is no package for dapper, i`d like to know if flashfxp is also working with ssl connections. 
thx 
cheers 
Aspeb
[/QUOTE]

I didn't create package for dapper but this version should work with it. Did you tried it?
I just don't have access to such box :(
flashfxp fully support ssl, tsl (including fxp transers) and - i'd say - everything else what man can expect from ftp client :D

> Security:  
FlashFXP offers some of the most secure transfers you can find, including the ability to work with client certs, SSL site&#8211;to&#8211;site transfers, SSL/TLS encryption and firewall support. This software also works with HTTPS connections and Checkpoint FW&#8211;1 type firewalls.

The security features we would really like to see added to this program are more verification methods and Secure Shell (SSH) support.


Connectivity/ Transfer Abilities:  
This program offers several tools to help ensure complete transfers including a &#8220;keep connections alive&#8221; tool, auto reconnect and auto resume. It can open up two connections at once but does not have the ability to run multiple threads.

iniCom.Network&#8217;s FlashFXP is compatible with more protocols and proxies than most FTP programs. FlashFXP supports FTP, HTTP, Socks (4, 4a &5), WinProxy, Squid and WinGate.

FlashFXP has some unique transfer options, such as scheduling a large transfer when you are not in front of the computer. The program can be set to disconnect, hang up, log off, turn off or hibernate after the transfer is complete.


User Tools:  
With the program you can set general, connection, queue, transfers and interface options. You can also change the interface language into simplified/traditional Chinese, Czech, Dutch, European Portuguese, French, German, English, Italian, Korean, Spanish or Swedish.

This software has all of the user tools that we were looking for including a drag & drop tool, scheduling, list/directory options, refresh and priority lists. FlashFXP has a unique collection of directory tools such as mask, invert, view raw directory, copy to clipboard, synchronized browsing and flush directory cache.

In terms of additional tools, this program has a text editor, folder bookmarks, a clipboard monitor, backup/restore tools and compare folders. This program also enables users to change file permissions (CHMOD) and apply filters (such as by extension type).


---

### Post by aspen on 2007-02-15
hi, thx4reply,

i installed the *.deb package without errors, but when i tried to start, i get the same error msg about glibc like 3 post above ;)
the package is allready installed but in version 2.3 and not in version 2.4.
there is also no option to upgrade this package... so no chance to get it working with dapper.

thx anyway
cheers
Aspen

---

### Post by Sir_Yaro on 2007-02-15
Just find (or give) me an access to dapper box an I'll compile it for u. 
Try to consider to give me an access to your computer.

cheers!

---

### Post by rhum on 2007-02-24
syr_yaro u rocks  ... 

i was dreaming about getting flashfxp on my ubuntu  

thank you so much  

note : it works here on ubuntu 6.10

---

### Post by MockY on 2007-03-15
Installed and runs great. Awesome job. Thank you.

However, I can only connect properly to ftp servers running on Linux platform. I can't connect to any of the windows sites that I regularly connect to. I get list error, just like the PASSV mode on the server is not set up correctly. IN window, I connect with FlashFXP just fine, as well as with all of the clients I have tried on Linux. Therefore, I suspect there is a setting specifically to this old version of FlashFXP but don't know what. Any ideas?

---

### Post by Sir_Yaro on 2007-03-15
O don't know any windows ftp servers so i've tried microsoft ftp server.
```
[12:44:50] Delaying for 90 seconds before reconnect attempt #2
[12:45:31] Connecting to ftp.microsoft.com
[12:45:31] Connected to ftp.microsoft.com -> IP=207.46.236.102 PORT=21
[12:45:31] 220 Microsoft FTP Service
[12:45:31] USER anonymous
[12:45:31] 331 Anonymous access allowed, send identity (e-mail name) as password.
[12:45:31] PASS (hidden)
[12:45:32] 230-Welcome to FTP.MICROSOFT.COM. Also visit http://www.microsoft.com/downloads.
[12:45:32] 230 Anonymous user logged in.
[12:45:32] SYST
[12:45:32] 215 Windows_NT
[12:45:32] PWD
[12:45:32] 257 "/" is current directory.
[12:45:32] TYPE A
[12:45:33] 200 Type set to A.
[12:45:33] PORT 192,168,0,100,217,150
[12:45:33] 200 PORT command successful.
[12:45:33] LIST
[12:45:33] 150 Opening ASCII mode data connection for /bin/ls.
[12:45:33] 226 Transfer complete.
[12:45:33] List Complete: 809 bytes in 1,28 (0,62 KBps)
```
and it works with out problems. Options were set as in attachment.

---

### Post by MockY on 2007-03-15
Ok, so now we know it's not a platform issue.
The servers I have issues with is servers that listens to other ports than 21. It is acting exactly like FlashFXP did on Windows when the specific PASSV ports were tunneled through the router. However, that got solved and it works great with any FTP client. On Linux, every single FTP client works to 100% when connecting to those servers, but FlashFXP does. I am using the same setting as you showed, but you connected to a port 21. Try a different server that listens to another port. If you don't have one, I'll privatly give you a temp account to one of them to see if it works for you.

---

### Post by Sir_Yaro on 2007-03-15
I don't have it. Not windows one :)
u can pm me with details

---

### Post by Sir_Yaro on 2007-03-15
It works without problems for me.
Just change an options as I've shown on attached picture
```
[22:49:23] Connecting to eee.qwe
[22:49:23] Connected to xxx.xxx -> IP=xx.xx.xx.xx PORT=28
[22:49:23] 220 Serv-U FTP Server v6.3 for WinSock ready...
[22:49:23] USER xxxx
[22:49:24] 331 User name okay, need password.
[22:49:24] PASS (hidden)
[22:49:24] 230 User logged in, proceed.
[22:49:24] SYST
[22:49:24] 215 UNIX Type: L8
[22:49:24] PWD
[22:49:24] 257 "/" is current directory.
[22:49:24] TYPE A
[22:49:24] 200 Type set to A.
[22:49:24] PASV
[22:49:25] 227 Entering Passive Mode (xx,xxx,xx,xx,195,83)
[22:49:25] LIST
[22:49:25] 150 Opening ASCII mode data connection for /bin/ls.
[22:49:25] 226 Transfer complete.
[22:49:25] List Complete: 253 bytes in 1,25 (0,20 KBps)

```

---

### Post by MockY on 2007-03-15
Ahh sweet. Thank you very much.

---

### Post by Sir_Yaro on 2007-03-16
[QUOTE="MockY"]This is not just FlashFXP related, but it is a Wine issue. I have to be sudo in order to install Wine, and I have also have to be root when installing anything with Wine. As a result, I have to be root when running it as well. What happens in FlashFXP's case is that everything that is downloaded belongs to root and cant be altered unless I'm root.

How can I bypass this?
[/QUOTE]
Why do u think that u need to be root to run wine ??? Every single package was instaled by root but u don't have to be root to run them. Same story with wine....
Please explain and don't PM me (just use this thread) cause those informations might be useful to someone else...

---

### Post by MockY on 2007-03-16
This is what I get if I don't run it as root (see attachment).

This is the case with every single software that needs to run under Wine, such as Dreamweaver, photoshop, and other windows applications. My guess is that I did something wrong when initially installed Wine. And as a result of me running in as root is that every single file is read only and if put on the desktop, with it comes the lock symbol.

---

### Post by Sir_Yaro on 2007-03-16
try:
```

cd ~
sudo chmod -R 700 .wine
sudo chown -R LOGIN.LOGIN .wine
```
replace LOGIN of course

eventually try to remove .wine directory or:
```

sudo chown -R LOGIN.LOGIN /home/LOGIN
```

---

### Post by Sir_Yaro on 2007-03-16
please show output of:
```
which wine
```

u can also purge wine package and instal it again

---

### Post by MockY on 2007-03-17
Absolutely fantastic. Many many thanks. *bows*

It would be great if it showed icons to distinguish easy between files, but a very minor "issue".

Again, thanks.

---

### Post by MockY on 2007-03-19
I noticed something when we solved this issue. I can only run program at a time with Wine. This is obviously not how should be. This is the output I get from terminal when trying to execute the second software via Wine:

```

wine client error:15: version mismatch 275/263.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

---

### Post by Maetrik on 2007-03-25
directory listing is not working for me here while connecting to SSL ftp servers :(
anyone else with same problem?

---

### Post by Sir_Yaro on 2007-03-25
> **Maetrik said:**
> directory listing is not working for me here while connecting to SSL ftp servers :(
anyone else with same problem?
Try to switch between passive/active/half passive mode.
Take a look here
[http://ubuntuforums.org/attachment.php?attachmentid=27493&d=1173998958](http://ubuntuforums.org/attachment.php?attachmentid=27493&d=1173998958)
and try to set option like i did it might help

Anyway i've found i can connect everywhere with correct options combination.
I'll check this issue about wednesday cause i'm abroad right now.

---

### Post by Sir_Yaro on 2007-03-25
> **MockY said:**
> I noticed something when we solved this issue. I can only run program at a time with Wine. This is obviously not how should be. This is the output I get from terminal when trying to execute the second software via Wine:

```

wine client error:15: version mismatch 275/263.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

i was able to reproduce this message so I'll try to fix it somehow, any ideas how?
Simply flashfxp package contains it own wine. 
```
$ /opt/flashfxp/bin/wine --version
wine-0.9.29
$ wine --version
wine-0.9.33

```
and if system's wine version is different, wine try to connect to different wineserver version and it gets confuse and refuse to work.

Only sollution that i see right now is to separete wine from flashfxp. But it's agains the main idea of creating one package contains everything.

Any idea?

---

### Post by Sir_Yaro on 2007-03-25
> **MockY said:**
> I noticed something when we solved this issue. I can only run program at a time with Wine. This is obviously not how should be. This is the output I get from terminal when trying to execute the second software via Wine:

```

wine client error:15: version mismatch 275/263.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

replace content of /usr/bin/flashfxp file by this:
```
#!/bin/bash
if [ `which wine` != "" ]
then
wine /opt/flashfxp/flashfxp/FlashFXP.exe
else
/opt/flashfxp/bin/wine /opt/flashfxp/flashfxp/FlashFXP.exe
fi

```

---

### Post by MockY on 2007-03-26
Once again, you are the best. Works without any issues.
An extreme amount of thanks.

MockY

---

### Post by Sir_Yaro on 2007-04-09
> **Maetrik said:**
> directory listing is not working for me here while connecting to SSL ftp servers :(
anyone else with same problem?

it works for me 
```
[12:16:25] 220 MrRobby (glFTPd 2.01 Linux+TLS) ready.
[12:16:25] AUTH TLS
[12:16:25] 234 AUTH TLS successful
[12:16:25] Negotiating SSL/TLS session...
[12:16:25] SSL/TLS negotiation successful...
[12:16:25] SSL/TLS connection using cipher EDH-DSS-DES-CBC3-SHA (168 bits)
[12:16:25] PBSZ 0
[12:16:25] 200 PBSZ 0 successful
[12:16:25] USER !yaro
[12:16:26] 331 Password required for yaro.
[12:16:26] PASS (hidden)
[12:16:26] 230- No dead connections found.
[12:16:26] PWD
[12:16:26] 257 "/" is current directory.
[12:16:26] TYPE A
[12:16:26] 200 Type set to A.
[12:16:26] PROT P
[12:16:26] 200 Protection set to Private
[12:16:26] PASV
[12:16:27] 227 Entering Passive Mode (xxx,xx,xxx,xxx,xxx,xxx)
[12:16:27] LIST -al
[12:16:27] Negotiating SSL/TLS session...
[12:16:27] 150 Opening ASCII mode data connection for directory listing using SSL/TLS.
[12:16:27] SSL/TLS negotiation successful...
[12:16:27] SSL/TLS connection using cipher DHE-DSS-RC4-SHA (128 bits)
[12:16:27] 226- [Ul: 827.9MB] [Dl: 29621.8MB] [Speed: 0.00K/s] [Free: 2964MB]
[12:16:27] 226  [Section: DEFAULT] [Credits: 14.6MB] [Ratio: Unlimited]
[12:16:27] List Complete: 381 bytes in 0,96 (0,37 KBps)
```
with options set as it's shown in an attachments.

---

### Post by Sir_Yaro on 2007-05-04
UPDATE!
2007-05-04
Ubuntu Feisty compilation, bug fixes, package now depend on wine

[http://www.mandrivalinux.eu/downloads.php?do=file&id=159&langid=1](http://www.mandrivalinux.eu/downloads.php?do=file&id=159&langid=1)
Also mirror available.

---

### Post by Dekadence on 2007-05-05
Getting list error on non-anonymous ftp :(

```

[19:48:44] 200 PORT Command successful.
[19:48:44] LIST
[19:48:44] 150 Opening ASCII mode data connection for /bin/ls.
[19:49:05] 426 Data connection closed, transfer aborted.
[19:49:05] List Error

```

Anyone knows what to do? btw, passive off/on doesn't work! Thanks

---

### Post by Sir_Yaro on 2007-05-06
Please check my previous posts. It's a matter of seting good options combination.

---

### Post by MockY on 2007-05-11
This version works like a charm, like expected. Great job!

However, the FlashFXP window only has a close option. I can't minimize it, nor maximize it. Why is that?

And another thing, something that both version had was that if you transfered multiple files, you have to right click and select transfer. When doing that, the select box will be visible until the last file is transfered. Very annoying but something I learned to live with. Is there something I can do about that?

---

### Post by Sir_Yaro on 2007-05-11
> **MockY said:**
> This version works like a charm, like expected. Great job!

However, the FlashFXP window only has a close option. I can't minimize it, nor maximize it. Why is that?
There is something wrong on your system. And it has nothing to do with FFXP. Unfortunatelly I can't help you with this. I don't event have gnome. But it's not default behavior. Try to search for some settings in wine config on more likely in windows manager settings.

> 
And another thing, something that both version had was that if you transfered multiple files, you have to right click and select transfer. When doing that, the select box will be visible until the last file is transfered. Very annoying but something I learned to live with. Is there something I can do about that?
Yup, confirmed. That is also wine and ffxp incompability. But fortunatelly there is easy way out. Almost all actions has key binding. Inser for new dir, ctrl+q to add files to queue, ctrl+t for transfer, ctrl+z to start queued transfer and so on. 
My only advise is to learn  this few conbination and use it. I know it's not perfect solution but i don't have anything else... :)
Yet....

---

### Post by mester on 2007-05-20
Hey great work Sir_Yaro :)

Got auth ssl to work so thats great :)

Got a few other problems u might be able to help with!

If i change setting in flashfxp its not saved how do fix that ? I know i need to change some setting so I can write to those files in /root dir but is just new to ubuntu so got a lot to learn :)

I cant save skiplist settings and get: 
[22:26:31] An internal error has occurred.
[22:26:31] Cannot create file Z:\opt\flashfxp\favorite.dat


Would be great if newer version of flashfxp could work with wine any thing u might work on sometime ? :)
Those making ffxp should really start making a linux compatible versions :)

Thx again for great work.
/mester

---

### Post by Sir_Yaro on 2007-05-20
> **mester said:**
> 
I cant save skiplist settings and get: 
[22:26:31] An internal error has occurred.
[22:26:31] Cannot create file Z:\opt\flashfxp\favorite.dat

What version did u use ?
flashfxp_2.1.924**-2**_i386.deb or flashfxp_2.1.924**-1**_i386.deb ??
This shouldn't happen with *-2...

Try 
```
sudo chmod a+w /opt/flashfxp/
sudo touch /opt/flashfxp/favorite.dat
sudo chmod a+w /opt/flashfxp/favorite.dat

```

> 
Would be great if newer version of flashfxp could work with wine any thing u might work on sometime ? :)
I try every new version FF with most recent wine. Be sure if that will start to work I'm gonna let you know :D

Anyway there is good news:
> Tom Kistner on Monday March 26th 2007, 16:48
I attached a patch to Bugzilla #5131 to make FlashFXP 3.4 work with the builtin comctl32.dll
So there is chance that newest version will work soon

---

### Post by Sir_Yaro on 2007-05-20
Just few minutes ago I've run 3.4 version without problems!

**Yeaaa!**
Unfortunately it require patched wine so it will take day or two before I made proper package....

---

### Post by mester on 2007-05-21
I should be running flashfxp_2.1.924-2_i386.deb if i have installed it properly, but it works nicely now when i can save settings :>

Looking forward to your new package with newer version of ffxp :P

Would be nice if settings like Secure File Transfers (Uplad/Download) and SSL Site to site Transfers [not supported by all servers) could be workable aswell if possible? :)

Now that i can run my favorite programs (ffxp and mirc) on ubuntu im sure im all done with windows(XP) for good :) 

One more thing how do i make a shortcut for ffxp on desktop ?

PS. Got some trouble with mirc + wine which have some bugs if i minimize a window and tile it just closes program down. If anyone know a package or something working let me know :)

---

### Post by Sir_Yaro on 2007-05-22
> One more thing how do i make a shortcut for ffxp on desktop ?
Make standard shortcut and use  *flashfxp* command

---

### Post by Sir_Yaro on 2007-05-22
UPDATE!
2007-05-22
[LIST]
[*]Patched wine (with bugfix #5131) added into package.
[*]FlashFXP 3.4.0 used (build 1145)
[*]Licence agreement added
[*]Minor attributes fix
[*]Simple weekly backup added (into ~/.flashfxp directory)
[/LIST]
Few addons

[DOWNLOAD]("http://www.mandrivalinux.eu/downloads.php?do=file&id=161&langid=1")
Also mirror available.
Check [first post]("http://ubuntuforums.org/showthread.php?p=2096969#post2096969") for more details.

---

### Post by mester on 2007-05-25
Hey nice work with new package. got some bugs issues.

tab with name, size, modified, attrib etc is not working (is just white) would be real nice if that could be fixed! (use that tab very much, to sort by modified).

The I got trouble with registration which i cant get working: registration Failed (#83) Please contact our help desk at [email]support@inicom.net[/email]. Dont know if that can be fixed ?

And a minor thing could it be possible to get terminal font in for example Status Window ? Just nicer to look at :) 

cheers
/mester

---

### Post by Sir_Yaro on 2007-05-25
> **mester said:**
> Hey nice work with new package. got some bugs issues.

tab with name, size, modified, attrib etc is not working (is just white) would be real nice if that could be fixed! (use that tab very much, to sort by modified).
Switch to local browser then back to FTP view. There is no path for that yet so it can't be fixed atm :(

> 
The I got trouble with registration which i cant get working: registration Failed (#83) Please contact our help desk at [email]support@inicom.net[/email]. Dont know if that can be fixed ?

I'll send question to flashfxp support 'bout that. I having a same problem. But until evaluation version works its a minor problem. And it's very easy to reset this 30 day counter...
> And a minor thing could it be possible to get terminal font in for example Status Window ? Just nicer to look at :) 

F6 --> Colors and Fonts

---

### Post by gesquive on 2007-05-26
Thanks a ton for making this package, it's great to have FlashFXP working under linux. :D
Hey, just a quick fix, the /usr/bin/flashfxp script has the following line:
```
cp /opt/flashfxp/FlashFXP/*dat ~/.flashfxp/`date +%U`
```
That line should be changed too:
```
cp /opt/flashfxp/FlashFXP/*dat ~/.flashfxp/*week*`date +%U`
```
in order for it to properly copy files, otherwise you just get a directory doesn't exist error and nothing copies

---

### Post by Sir_Yaro on 2007-05-26
U're right. That's a typo. I'll fix it tomorrow.

---

### Post by Sir_Yaro on 2007-05-26
package updated

---

### Post by Sir_Yaro on 2007-05-28
> **mester said:**
> The I got trouble with registration which i cant get working: registration Failed (#83) Please contact our help desk at [email]support@inicom.net[/email]. Dont know if that can be fixed ?


Answer was:
In 99% it's a illegal key problem...

---

### Post by Sir_Yaro on 2007-06-01
I went through registration proces without problems. Take a look at [first post]("http://ubuntuforums.org/showthread.php?p=2096969#post2096969")'s attachment (second one).

So I'd say all problems with registration are related to illegal, suspended or outdated keys...

---

### Post by Sir_Yaro on 2007-06-22
UPDATE!
2007-06-22
*flashfxp_3.4.1145-3_i386.deb*
[LIST]
[*] Backup fix (licence key)
[*] New settings directory (~/.flashfxp)
[*] Wine included in flashfxp package now works even if different wine version run atm
[/LIST]

---

### Post by Bradl3yJ on 2007-06-27
> **Sir_Yaro said:**
> UPDATE!
2007-06-22
*flashfxp_3.4.1145-3_i386.deb*
[LIST]
[*] Backup fix (licence key)
[*] New settings directory (~/.flashfxp)
[*] Wine included in flashfxp package now works even if different wine version run atm
[/LIST]

I am responding to this update: "Wine included in flashfxp package now works even if different wine version run atm"

I have wine installed (wine 0.9.33-0ubuntu1 from Synaptic), and when I have this installed, your FlashFXP will not run. If i uninstall wine with Synaptic, it runs find. I tried even updating to the latest official wine release ( 0.9.39 ) by adding the official wine repositories, and still I have the same problem.

---

### Post by Sir_Yaro on 2007-06-27
Could anyone else confirm that? And show me some logs, please! 
I had three different wine version installed and I could run them simultaneously without any problems. Few minutes ago I have tried wine-0.9.37 (flashfxp) and wine-0.9.38 (any other app) and it works without problems.

---

### Post by Bradl3yJ on 2007-07-02
I found when i manually execute the following command it works:

```
/opt/flashfxp/bin/wine /opt/flashfxp/FlashFXP/FlashFXP.exe
```


However, when i use your flashfxp launch script (/usr/bin/flashfxp) I get the following:

```
/home/brad/.flashfxp updated successfully.
wine client error:10: version mismatch 280/304.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```

I looked at your flashfxp script and it is the same command used to launch, so it is over my head on what the problem with the script might be.

---

### Post by Sir_Yaro on 2007-07-02
That is REALLY strange....
I'll take a look at this.

---

### Post by Bradl3yJ on 2007-07-03
> **Sir_Yaro said:**
> That is REALLY strange....
I'll take a look at this.

Ok, figured out why i was getting this error. I was running another application using the latest wine that I installed using apt-get. Apparently two applications can not run on two different versions of wine at the same time. If i make sure no apps are running under my wine installation, flashfxp will launch right up using this script

There is an easy fix for the Edit and View bug as well. In FlashFXP go to Options>File Associations and Click "Add". File Mask, type *. Open with 'Select Program, and browse to your wine/drive_c/windows/notepad.exe. Check the boxes for edit and view. Thats it, windows notepad is not the best editor but hey it is better than flashfxp locking up! And you could use another, better windows program to edit using this method i would imagine.

You could get more specific with spefic files such as images if you want to open in mspaint or whatever.

---

### Post by Sir_Yaro on 2007-07-04
> **Bradl3yJ said:**
> Ok, figured out why i was getting this error. I was running another application using the latest wine that I installed using apt-get. Apparently two applications can not run on two different versions of wine at the same time. If i make sure no apps are running under my wine installation, flashfxp will launch right up using this script
I knew that and I though i've fixed that. That's why I'm so confused. I'll need to check this on some other host....
> 
There is an easy fix for the Edit and View bug as well. In FlashFXP go to Options>File Associations and Click "Add". File Mask, type *. Open with 'Select Program, and browse to your wine/drive_c/windows/notepad.exe. Check the boxes for edit and view. Thats it, windows notepad is not the best editor but hey it is better than flashfxp locking up! And you could use another, better windows program to edit using this method i would imagine.

You could get more specific with spefic files such as images if you want to open in mspaint or whatever.
I've tried this before and it did work for me. FF got hang up anyway. Did u actually check if this works for u or u just assume it will?

---

### Post by Bradl3yJ on 2007-07-05
> **Sir_Yaro said:**
> 
I've tried this before and it did work for me. FF got hang up anyway. Did u actually check if this works for u or u just assume it will?

Yes, fully works for me with notepad, able to edit/view, i can save the file, upload the saved version, rinse and repeat.

---

### Post by kigol on 2007-07-09
i converted this to a .rpm for the Fedora folks.

[http://rapidshare.com/files/42031431/flashfxp-3.4.1145-4.i386.rpm.html](http://rapidshare.com/files/42031431/flashfxp-3.4.1145-4.i386.rpm.html)

---

### Post by trv4gr on 2007-09-12
I am using wine 0.9.44~winehq0~ubuntu~7.04-1
 from the famous "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main" repository.

When this is installed, even if i dont run at the time any wine applications and wine is not running, i get this:

$ flashfxp 
~/.flashfxp updated successfully.
wine client error:10: version mismatch 309/304.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

If i remove wine package, then flashfxp runs normally.

What is wrong / How can this be fixed?

Thank you!

---

### Post by Sir_Yaro on 2007-09-13
I wrote about it some time ago. Two different wine version can't run at the same time. :( Fortunatelly I just found the solution. New version will be available in the next few minutes...

---

### Post by ]tux[cHriz on 2007-09-29
Hi,

any news?

Want use FlashFXP ;)

In Gutsy it isnt rockstable (maybe it has something to do with Compiz)

I will post my testing results soon!

regards
chris

---

### Post by Sir_Yaro on 2007-09-30
> **']tux[cHriz said:**
> Hi,

any news?

Want use FlashFXP ;)

In Gutsy it isnt rockstable (maybe it has something to do with Compiz)

I will post my testing results soon!

regards
chris

what do u mean?
New nersion is available since two weeks now.
Read first post.

---

### Post by Karahana on 2007-09-30
I just installed the 3.4.1145 deb package and it won't start. It looks like it's loading (CPU usage goes up) but then just exits with no error message. I tried removing wine and it's the same. Help really appreciated since there really isn't a decent GUI FTP for linux. :)

---

### Post by Sir_Yaro on 2007-09-30
What revision did you use ?

flashfxp_3.4.1145**_-4_** or flashfxp_3.4.1145_**-3**_ ?
Try to start it from command line and tell me if there's something wrong there.

---

### Post by Karahana on 2007-09-30
Lol I just figured it out... My bad, I tried to start it from a screen and that's why it didin't work! Great package, tnx! :D

---

### Post by ]tux[cHriz on 2007-10-06
I have a bug. When I'm clicking on "onqueue" or "transfer", the contex-menue dont go away. It hangs. Anyone else have this bug??

chris

---

### Post by Sir_Yaro on 2007-10-10
it was quite common bug in flashfxp on wine. What wersion do u use ?
btw IMO easiest way to deal with it is to use keyboard shotcuts...

---

### Post by goonies on 2007-10-10
Does it run better than the previous 2.* versions with wine?

How is the cpu usage while using it via wine?

---

### Post by biasquez on 2007-10-26
EDIT:

quote, with last version of wine,compiz, ubuntu gutsy and flashfxp (deb -4), flashfxp works but randomly, gui crash and i must restart flashfxp. moreover, i tried to install flashfxp from classic setup (trial version), flashfxp works well, gui not crash but when i'm connecting to site, flashfxp crash to LIST or STAT -AL and cpu run at 100%.

---

### Post by ilantz on 2007-11-17
Sir yaro , you are a ROCK :KS !!!

this is by far my most "linux" quest ever ;) i have been "compromising" with kasablanca / KFTPgrabber < that's the best native linux ftp client i've seen.

anyway how the hell have you overcome the wine bug ??!  i've saw that tom's bug fix wasn't approved because no test case was filled.

if you did built this wine by yourself and added his patch you should file this ! 

Thanks again ! i'll be testing your package this week extensively ;)

---

### Post by Nigggo on 2007-12-01
this version doesn't run with my amd64 system... is there any possibility to solve this problem? i tried to install the latest version of flashfxp the normal way but it works verry instable.

---

### Post by Sir_Yaro on 2007-12-01
> **ilantz said:**
> Sir yaro , you are a ROCK :KS !!!

this is by far my most "linux" quest ever ;) i have been "compromising" with kasablanca / KFTPgrabber < that's the best native linux ftp client i've seen.

anyway how the hell have you overcome the wine bug ??!  i've saw that tom's bug fix wasn't approved because no test case was filled.

if you did built this wine by yourself and added his patch you should file this ! 

Thanks again ! i'll be testing your package this week extensively ;)

i took patch from wine web site and just compile it. thats all... :)

---

### Post by Sir_Yaro on 2007-12-01
> **Nigggo said:**
> this version doesn't run with my amd64 system... is there any possibility to solve this problem? i tried to install the latest version of flashfxp the normal way but it works verry instable.

Sorry but I don't have any 64bit processor so I can't compile wine for u. I've attached patch file. Use it to patch wine and build your own 64bit version.

---

### Post by Sir_Yaro on 2007-12-01
> **biasquez said:**
> EDIT:

quote, with last version of wine,compiz, ubuntu gutsy and flashfxp (deb -4), flashfxp works but randomly, gui crash and i must restart flashfxp. moreover, i tried to install flashfxp from classic setup (trial version), flashfxp works well, gui not crash but when i'm connecting to site, flashfxp crash to LIST or STAT -AL and cpu run at 100%.

That's what is different in my version. It has special patch applied to overcome this problem.

---

### Post by Nigggo on 2007-12-01
sorry but i am completely new to linux. what do i have to do with this file?

---

### Post by Sir_Yaro on 2007-12-02
* decompress to wine source directory.
* do:
```
patch -p1 < filename.patch
```
* compile wine as usual.

---

### Post by Nigggo on 2007-12-02
sorry but i have installed linux since 3 days xD

if i try to do what you said:
```

nigggo@nigggo-desktop:~$ patch -pl /home/nigggo/Desktop/wine-0.9.50/listview_ownerdata_loop_fix.patch
patch: **** strip count l is not a number
```
what is my mistake? i downloaded wine as sourcecode extracted it and pasted the patch file into this folder...

---

### Post by Sir_Yaro on 2008-01-13
wrong directory
```
[yaro]@d[/tmp]$ cd wine-0.9.53/dlls
[yaro]@d[/tmp/wine-0.9.53/dlls]$ ls list*
listview_ownerdata_loop_fix.patch
[yaro]@d[/tmp/wine-0.9.53/dlls]$ patch -p1 <listview_ownerdata_loop_fix.patch
patching file comctl32/listview.c
Hunk #1 succeeded at 3404 (offset 7 lines).
Hunk #2 succeeded at 5316 (offset 21 lines).
[yaro]@d[/tmp/wine-0.9.53/dlls]$
```

---

### Post by untzuntz on 2008-02-28
Any chance that the new v3.6 1240 might show up here soon? :)
edit: Big thank you btw! Finally no need for VMWare anymore.

---

### Post by Sir_Yaro on 2008-02-28
UPDATE!
2007-09-13
flashfxp_3.6.1240-1_i386.deb
FlashFXP 3.6.0 used (build 1240)

check first post !

---

### Post by MurDoK on 2008-03-29
Thanks for your work. flashfxp doesn't work at all with the wine version of gutsy repositories, but yours does it perfect. 
:)

---

### Post by romracer on 2008-04-18
Thanks very much for putting this together.  I get the strange freezing when I have menus open too, but at least for the most part it works.

Any plans to build this for Hardy?  I had to edit the control file in the .deb to be able to install it peacefully.  libldap2 is now renamed to libldap-2.4-2 so it was missing that dependency.

If you can provide the .diff or other files you used to build the deb, I'd be happy to rebuild it on my Hardy install if you have not yet upgraded.

Thanks again!

---

### Post by Sir_Yaro on 2008-04-18
> **romracer said:**
> 
Any plans to build this for Hardy?  
Gimme week or two. I waiting for stable release....

---

### Post by r0bb3d on 2008-04-21
Tnx Yaro, that would be great! 

Just switched to Hardy only to come to the conclusion my trusted flashfxp doesn't install here! Ill have to boot XP atm which toly makes me sad :D

---

### Post by romracer on 2008-04-21
I've put up the .deb file I made for Hardy.  Its nothing more than the current one on this thread with one minor change.  I've updated debian/control to refer to libldap-2.4-2 instead of libldap2.  All else is exactly as Yaro put it.

Hopefully this will keep you out of Windows until Yaro builds us an "official" one :)

[http://xbins.org/~romracer/flashfxp_3.6.1240-1_i386.deb](http://xbins.org/~romracer/flashfxp_3.6.1240-1_i386.deb)

---

### Post by r0bb3d on 2008-04-24
Tnx romracer, much appreciated!!

---

### Post by Sir_Yaro on 2008-05-04
UPDATE!
2008-05-04
[LIST]
[*]Hardy relase
[/LIST]

Check [first post]("http://ubuntuforums.org/showthread.php?p=2096969#post2096969") for more details.

---

### Post by r0bb3d on 2008-05-08
Tnx man, and I speak for a bunch of guys that had m$ windows running in VMs and stuff untill your Flashfxp fix! :D

---

### Post by Ticko on 2008-05-14
Great fix! 
The first program i bought to my ubuntu :-)
This works great!
Thanks.

---

### Post by Draky on 2008-06-27
Hello.
Nice work.
Anyway, can we use a beta executable flashfxp.exe with this ? Replacing the one installed through the .deb package with a private one.

---

### Post by Sir_Yaro on 2008-06-28
> **Draky said:**
> Hello.
Nice work.
Anyway, can we use a beta executable flashfxp.exe with this ? Replacing the one installed through the .deb package with a private one.

Check it... But I think it will work without problems.

---

### Post by Draky on 2008-06-29
Working :)
But in fact, FFXP freezes when I reduce the program in taskbar :(

---

### Post by Sir_Yaro on 2008-06-29
> **Draky said:**
> Working :)
But in fact, FFXP freezes when I reduce the program in taskbar :(

Can't help with that.  For now I'm happy that most important functions works quite well. ;]

---

### Post by Draky on 2008-06-30
Ok.

---

### Post by polare on 2008-08-09
flash fxp for linux x64?

---

### Post by mikehammer on 2008-08-26
I'm actually using Mint, but wanted you to know that I registered for the fora here just to thank you for porting this. FlashFXP was one of the "have to have" apps for me. Thank You!!! Thank You!!! Thank You!!!

---

### Post by nemodx on 2008-09-24
I tried it, and it worked at first. And then after a reboot, it did not work at all anymore. When I login to a site, it logs in, does something, the app goes grey, freezes and then it crashes.

Any ideas what this might be?

Using Ubuntu 8.04

Thank you very much in advance for any help :)

```
lestat@ESKLIN-01:~/pftp/src$ flashfxp 
mv: cannot stat `/home/lestat/.flashfxp/week*': No such file or directory
/usr/bin/flashfxp: line 10: +%U: command not found
cp: target `2008' is not a directory
/usr/bin/flashfxp: line 12: +%U: command not found
cp: target `2008' is not a directory
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
/home/lestat/.flashfxp updated successfully.

```
Thats what I get when I try to run it.

Another thing that I found was that once connected to a site, (when it was working) the sort by name (sort by) etc just disappeared :(

---

### Post by nemodx on 2008-09-24
First problem solved. Well by removing wine, removing flashfxp and then re-installing it all. Dont know what happened there, but the sort by still remains a problem.

---

### Post by MockY on 2008-11-17
If entering the code for locking up the software but then canceling out of that action, FlashFXP totally freezes and uses 99% of the cpu. Known issue? I guess it's not a big issue, but I figured I would let you know...unless someone else already mentioned it.

---

### Post by decat on 2008-12-09
Hello guys & girls


i'm new to this board which I found by using google.

I installed ubuntu 08.10 yesterday which went without a glitch on my intel E6600.
As i'm a daily flashfxp user I immediatly started looking if flashfxp works on ubuntu and apparently it does (seeing this thread).

The problem is I can't find the link to the flashfxp file in order order to install it.
Can someone point me out to the correct link please?

thanks in advance

decat

---

### Post by Sir_Yaro on 2008-12-10
> **decat said:**
> Hello guys & girls


i'm new to this board which I found by using google.

I installed ubuntu 08.10 yesterday which went without a glitch on my intel E6600.
As i'm a daily flashfxp user I immediatly started looking if flashfxp works on ubuntu and apparently it does (seeing this thread).

The problem is I can't find the link to the flashfxp file in order order to install it.
Can someone point me out to the correct link please?

thanks in advance

decat
Check my first post:
[http://ubuntuforums.org/showpost.php?p=2096969&postcount=1](http://ubuntuforums.org/showpost.php?p=2096969&postcount=1)

---

### Post by decat on 2008-12-10
I did yesterday.

That link 'download here' did not work when I clicked it yesterday!

anyhow, it seems to work now


thanks

---

### Post by tehk on 2008-12-18
using wine-1.0.1 under kubuntu 8.10, amd_64, and ffxp always runs, but hangs when it gets to the directory listing irregardless of whether or not the server is using TLS/SSL or nothing at all.

i tried the earlier post which describes setting notepad as the default editor for * and *.*, but this didn't work either.

would love to get this app running so i can stop using vmware as well :popcorn:

---

### Post by Sir_Yaro on 2008-12-19
> **tehk said:**
> using wine-1.0.1 under kubuntu 8.10, amd_64, and ffxp always runs, but hangs when it gets to the directory listing irregardless of whether or not the server is using TLS/SSL or nothing at all.

i tried the earlier post which describes setting notepad as the default editor for * and *.*, but this didn't work either.

would love to get this app running so i can stop using vmware as well :popcorn:

:lolflag: 
This is main and only reason why this package with wine fix was made. You didn't discover _anything_ new... 
For your explanation. Wine has some bugs in two or three places since year or year and a half and stupid/stuborn wine developers refuse to fix it (even when a patch was created by one of the wine comunity volunteers). Strange but real.

Anyway what was your question? :D

---

### Post by tehk on 2008-12-31
well, if this package doesn't correct the problem... and the workarounds don't fix the problem... whats the solution for amd64 users?

maybe the i386 package needs to fork to an amd64 branch...

---

### Post by Sir_Yaro on 2009-01-01
> **tehk said:**
> well, if this package doesn't correct the problem... 
This package DOES correct the problem - that's the only reason why I create it.

>  whats the solution for amd64 users?
Give me a remote access to amd64 computer then I'll be able to create such package...

---

### Post by tehk on 2009-01-11
> **Sir_Yaro said:**
> This package DOES correct the problem - that's the only reason why I create it.


Give me a remote access to amd64 computer then I'll be able to create such package...

Sorry, dont give out shell access...

However, if you provide a step by step on the build process, I'll build/package it for the group.

---

### Post by Sir_Yaro on 2009-09-02
UPDATE!
2009-09-02
*flashfxp_3.6.1240-4_all.deb*
[LIST]
[*] Works with 32bit and 64bit releases
[*] Patched wine removed from package
[*] Wine added as dependency

[/LIST]

Check first post for more details.

---

### Post by MockY on 2010-01-30
I just upgraded Wine to 1.1.37 but when trying to install the latest .db you released, all I get is: "**Status:** [COLOR="Red"]**Error: Cannot install 'wine**'[/COLOR]. I get the same message when completely removing Wine.

---

### Post by Sir_Yaro on 2010-02-03
Please install this wine package:
[http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.37~winehq0~ubuntu~9.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/jaunty/wine_1.1.37~winehq0~ubuntu~9.04-0ubuntu1_i386.deb)

flashfxp depends on "wine" package but in karmic there isn't wine >= 1.1.25
There is only wine1.2 package.... :(

I'll fix that soon

---

### Post by darkrad on 2011-02-13
Hi, does anybody got the identd feature to work on flashfxp? it keeps saying "unable to connect to port 113". I tried to install oidentd or pidentd but i got the same result.
any help?
thanks

---

### Post by darkrad on 2011-02-24
> **darkrad said:**
> Hi, does anybody got the identd feature to work on flashfxp? it keeps saying "unable to connect to port 113". I tried to install oidentd or pidentd but i got the same result.
any help?
thanks

It seems to work if it's executed as superuser

---

### Post by darkrad on 2011-02-24
Has anybody noticed that when the flashfxp is maximised, if any other window of the systray is clicked it won't show? Like the flashfxp window is locked. The only way to show other applications windows is to minimise flashfxp panel.
Any workarounds for that?

---

