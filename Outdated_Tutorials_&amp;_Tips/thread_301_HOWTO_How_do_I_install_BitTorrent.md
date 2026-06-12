---
title: "HOWTO: How do I install BitTorrent?"
date: 2004-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-12
The best way is via the apt respository. Make sure you have added the universe to your source list. Then run the following commands and this will install BitTorrent and also the plugin for firefox.

> sudo apt-get install bittorrent libwxgtk2.4

---

### Post by FLeiXiuS on 2004-10-12
I always loved Azureus!  Requires Java though.

---

### Post by ubuntu-geek on 2004-10-12
Feel free to make a HOWTO and post it :)

---

### Post by Michael on 2004-10-12
I have installed bittornado and bittornado-gui via apt-get but I can't seem to find how to run it.. or where it was installed..
do I need also 'bittorrent' package for that or what?

---

### Post by flygmaskin on 2004-10-12
[quote=Michael]I have installed bittornado and bittornado-gui via apt-get but I can't seem to find how to run it.. or where it was installed..
do I need also 'bittorrent' package for that or what?[/quote]

The bittornado packages seem to be broken. I would suggest using bittorent-gui instead.

---

### Post by Michael on 2004-10-13
I don't see "bittorrent-gui" in niether of the main nor in the universe repositories.. only "bittorrent".

---

### Post by johanvrt on 2004-10-15
sudo apt-get install bittornado-gui 
Make sure to have universe in your repository

btdownloadgui.bittornado is the command to open it from a console, 
but after clickin a .torrentlink in firefox/mozilla it should open automaticly (after dialogscreen).

Good luck , 
deFrysk

---

### Post by FLeiXiuS on 2004-10-16
For bit torrent installations I would have to include

Azureus Java Bit-Torrent Handler

*Requirements*
Java: [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
Azureus: [http://sourceforge.net/project/showfiles.php?group_id=84122](http://sourceforge.net/project/showfiles.php?group_id=84122)

Select the appropriate ones which apply to your machine.

Installing this was a jiffy.  I downloaded [http://aleron.dl.sourceforge.net/sourceforge/azureus/Azureus_2.1.0.4_linux.GTK.tar.bz](http://aleron.dl.sourceforge.net/sourceforge/azureus/Azureus_2.1.0.4_linux.GTK.tar.bz) .

**Installation**
```
tar -xvjf Azureus_version.tar.bz2
cd Azureus_version/
./azureus
```

This should load up immediately.  If errors exisit try configuring the azureus script file to locate your java installation.  To do so...

```
 $EDITOR azureus 
```
Edit the configurable lines.

If Azureus doesn't load immediately you can try starting it manually...

**GTK:**

```
java -cp swt.jar&#58;swt-pi.jar&#58;Azureus2.jar -Djava.library.path=./org.gudy.azureus2.ui.swt.Main
```


**Motif:**

```
java -cp swt.jar&#58;Azureus2.jar -Djava.library.path=./org.gudy.azureus2.ui.swt.Main
```

If any other problems exist please setup a post. I'll be glad to introduce answers upon request.
[/code]

---

### Post by tanari on 2004-10-27
```
andrei@ubuntu:~/progi/azureus $ ./azureus
Starting Azureus...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE [java = SableVM]
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)
 
```

how to install java for azureus?

---

### Post by FLeiXiuS on 2004-10-27
Install Java's JRE from java.com

---

### Post by mrchocobo on 2004-10-30
[QUOTE=FLeiXiuS]Install Java's JRE from java.com[/QUOTE]
 azureus eats too much resources being a java app

---

### Post by silverkhan on 2004-11-02
How do i make a menu entry for azureus?

---

### Post by Loptr on 2004-11-02
```
loptr@vincent:~ $ sudo apt-get install bittorrent libwxgtk2.4
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package libwxgtk2.4

``` 

Could someone please advice me on this? 
(Running freshly installed Ubuntu 4.10 Warty Warthog)

---

### Post by FLeiXiuS on 2004-11-02
Make sure the universe repo is enabled.

---

### Post by bazder on 2004-11-03
Hi,

Can you tell me if you need to open ports in a router to enable
bittorrent to work?  I tried aMule and some FAQ suggested you'd
get slower download speeds if you didn't allow ports to be forwarded.

Is anything like that true for bittorrent?

What kind of a security risk is it to run p2p apps in Linux?

Would it be safer to run bittorrent (or others) from a LiveCD?  

How hard is it to re-package the Warty LiveCD to do this?

---

### Post by jdodson on 2004-11-03
i run bittorrent from behind two firewalls(dont ask its a lame setup) and i have no problems and did not have to open any ports.  and as far as i can tell bitorrent is secure(it has the occasional security flaw as all software does, so keep up to date), so at least for bitorrent you dont need to run it from a live cd.  i have no idea for anything else.

---

### Post by mattyh on 2004-11-07
Is there a way to make azureus the default app for .torrent? I can't seem to figure out how to get that done.  Thanks

---

### Post by FLeiXiuS on 2004-11-07
[QUOTE=mattyh]Is there a way to make azureus the default app for .torrent? I can't seem to figure out how to get that done.  Thanks[/QUOTE]

I haven't figured that out...setting default programs for file extensions in gnome 2.8.

Then again I haven't looked around much.

---

### Post by mattyh on 2004-11-07
A Guy on the #ubuntu channel (lt_kije to be exact) just told me how to do it.  Here are his words:

<lt_kije> for firefox, make sure that in the downloads section of the preferences menu, you have "ask me where to save every file" checked -- it will prompt you for what to do next time you click on a .torrent
<lt_kije> when you do that, click "do this every time" or sth like that.
<lt_kije> in gnome, right click on the file (eg movie.torrent).
<lt_kije> select "properties"
<lt_kije> the right-most tab is called "open with" -- you should be able to add azureus to that list.

Looks pretty straight forward.

---

### Post by Jewseph on 2006-01-15
When I installed bitornado in windows it would never find other seeders or leechers and I couldn't download it, I eventually found what the problem was but I have long since forgotten. Now that I switched to Ubuntu 5.10, I have encountered the same problem as before, the torrents I try will time out, even though the site where I got them listed well over 1000 seeders and 3000 leechers. Any help for this problem in linux would be greatly appreciated.

---

### Post by bored2k on 2006-01-15
[QUOTE=Jewseph]When I installed bitornado in windows it would never find other seeders or leechers and I couldn't download it, I eventually found what the problem was but I have long since forgotten. Now that I switched to Ubuntu 5.10, I have encountered the same problem as before, the torrents I try will time out, even though the site where I got them listed well over 1000 seeders and 3000 leechers. Any help for this problem in linux would be greatly appreciated.[/QUOTE]
Are you firewalled? Router? Did you forwarded 'em bittorrent ports? If you did, are you sure your ISP isn't blocking bittorrent?

---

### Post by Jewseph on 2006-01-15
How would I go about this in linux?

---

### Post by bored2k on 2006-01-15
[QUOTE=Jewseph]How would I go about this in linux?[/QUOTE]
You don't do this in linux. [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) <-- Search for your router and go to the part where it helps you enable BT ports.

---

### Post by WelterPelter on 2006-03-31
Can't get Azureus running right on 64-bit Dapper. 

Bittorrent is working, but slowly. Normally my download rates are around 300 kB/s, but it's crawling at 30 kB/s right now. 

Any help appreciated.

---

### Post by gullyhole on 2006-04-02
I receive this error when I try to install.

Package libwxgtk2.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libwxgtk2.4 has no installation candidate

Now i have made many stupid mistakes. So it may be something dumb. Someone mentioned turning on the Universe repo or something and i dont know how to do that.

---

### Post by Draddy on 2007-03-26
so like everyone said in this dead thread...

I installed bittorrent and Ktorrent and tried opening a top gear torrent... in bittorrent I get a "client installs banned" warning, or something along those lines... 

and in ktorrent the download "stalls" before it starts..

what do I do?

---

### Post by jimbo2150 on 2007-04-30
> **mattyh said:**
> Is there a way to make azureus the default app for .torrent? I can't seem to figure out how to get that done.  Thanks

Download (or create) a .torrent file anywhere on you drive (possibly desktop). Then right-click on file and go to Properties. Then choose "Open With" tab and select the program you want to open that type of file.

---

### Post by marcstylzzz on 2009-05-01
why does my terminal say couldn't find package>? please help, i want bittorrent on this, thanks
P.S: I am very new to linux system, whats "universe" and how do i add it? thanks

---

### Post by sama_j on 2009-05-01
Try using this. Very easy to configure and use.

---

### Post by xx58 on 2009-05-01
Hello Everybody,
I never use any Torrent before, but Yesterday I starting Interesting about Torrens. I AM VERY NEW IN lINUX TOO, so can anybody say do:" Difference of BitTorrent & KTorrent? Which one is better ? I have Linux Ubuntu 8.10. How I can use any Torrent to download Linux 9.04 (I kn ow where I can Linux usually), I want download using Torrent. Thanks

---

### Post by sama_j on 2009-05-01
Try this page. It has information about torrenting and installing Ubuntu.
I haven't used Ktorrent or Bit-torrent myself. The standard torrent client in Ubuntu is quite capable. See my post above for info on finding the program.

> [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

---

### Post by xenosaga456 on 2009-06-15
ya but i think that bittorrent would be nicer:p

---

### Post by greenspeed on 2009-07-22
I've been trying to get either bittorrent or bittornado to work for a few days now.  I downloaded them via get-apt and that was success full.  Now I don't know how to get bittorent or bittornado to actually function. 

When i click on a torrent it wont launch either of the programs and if I try to save the file it won't open. I've never had an issue on windows.  Like most in this thread I'm new to ubuntu.  Running 9.04 on a EEE netbook

---

