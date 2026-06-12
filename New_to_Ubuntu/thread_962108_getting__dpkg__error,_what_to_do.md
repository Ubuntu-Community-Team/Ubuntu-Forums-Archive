---
title: "getting  dpkg  error, what to do???"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Nascarnut on 2008-10-28
me again, I just installed Ubuntu and whenever I try to run the updates it keeps begging to install i get an error saying 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
:confused:
 I am new to this and the only OS I know is Windows, I have no clue what this means, when I go to terminal and type in "sudo dpkg --configure -a" and enter my password it says 

"Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--23:10:30--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.186.70
Connecting to fpdownload.macromedia.com|72.246.186.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .."
:confused:
I have no clue what to do after this, I also get this error when I try to  add programs. 
Any help would be nice,
thx,
Andrew

---

### Post by overdrank on 2008-10-28
> **Nascarnut said:**
> me again, I just installed Ubuntu and whenever I try to run the updates it keeps begging to install i get an error saying 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
:confused:
 I am new to this and the only OS I know is Windows, I have no clue what this means, when I go to terminal and type in "sudo dpkg --configure -a" and enter my password it says 

"Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--23:10:30--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.186.70
Connecting to fpdownload.macromedia.com|72.246.186.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .."
:confused:
I have no clue what to do after this, I also get this error when I try to  add programs. 
Any help would be nice,
thx,
Andrew

Hi and you can use the tab key to highlight the ok and the press the enter key and that should fix the issue.

---

### Post by Nascarnut on 2008-10-28
> **overdrank said:**
> Hi and you can use the tab key to highlight the ok and the press the enter key and that should fix the issue.

i hit tab and then hit enter and all that happens is that i get more ... ...

Again, im really new at this.

---

### Post by overdrank on 2008-10-28
> **Nascarnut said:**
> i hit tab and then hit enter and all that happens is that i get more ... ...

Again, im really new at this.

Please post the more that you are getting. It should be installing but if you get errors please post.

---

### Post by Nascarnut on 2008-10-28
what exactly is installing? it just says what I showed in the first post, nothing changes, I still cant install updates or programs. i hit tab then enter and the only thing i get is .. ..........

Sry about being a Ubuntu Noob:???:

---

### Post by macogw on 2008-10-29
Wait, is the OK in red and everything else is on a blue background?  Or is this just plain text in the terminal?

---

### Post by kansasnoob on 2008-10-29
I'm curious what version of Ubuntu you're running. Is it 8.04 aka Hardy?

The reason for my curiosity is this:

> "Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--23:10:30-- [http://fpdownload.macromedia.com/get...9_linux.tar.gz](http://fpdownload.macromedia.com/get...9_linux.tar.gz)
=> `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.186.70
Connecting to fpdownload.macromedia.com|72.246.186.70|:80... connected.

Why DL the Flash 9 tar.gz?

Flash 9 is in the repos, but it's junk anyway.

If this is 8.04 I'd do this:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

That should clear the flash tar.gz stuff (hopefully). To see try again:

```
sudo dpkg --configure -a
```

Then:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then to get the best flash:

```
sudo apt-get remove --purge flashplugin-nonfree
```

And install the Flash 10 .deb from here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Then you'll have to restart Firefox by going to File > Quit, then restart Firefox and hopefully the changes will have taken hold.

---

### Post by macogw on 2008-10-29
> **kansasnoob said:**
> I'm curious what version of Ubuntu you're running. Is it 8.04 aka Hardy?

The reason for my curiosity is this:



Why DL the Flash 9 tar.gz?

Flash 9 is in the repos

What's what he's DOING!  Flash isn't allowed to actually exist inside the repos.  The package just downloads the installer from adobe.com and installs it for you.

---

### Post by Nascarnut on 2008-10-29
> **macogw said:**
> Wait, is the OK in red and everything else is on a blue background?  Or is this just plain text in the terminal?

this is just the plain text in the terminal, is there somewhere else i should go for this? Again, as I said before, this is the first experience I've had with any OS other than windows, terminal is just like the run command in windows, right?

Yes I'm running 8.04.

again, I'm getting the "dpkg was interrupted..." error only when I try to install stuff, everything else works fine.

---

### Post by Nascarnut on 2008-10-29
ok kans, here's what I get when I try to run those commands,

"Downloading...
--09:47:43--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.82.70
Connecting to fpdownload.macromedia.com|72.247.82.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%    4.85 KB/s
   50K .......... ...."

Is that all? should I go and run the rest of the commands?
also, can someone explain exactly what I'm doing here? am I downloading something?

EDIT: the dots are getting longer, so I can only guess this is downloading flash player
EDIT: yea, its downloading, really slowly, but its downloading, should it be downloading at 43.44 B/s?

---

### Post by Nascarnut on 2008-10-29
this isn't working, at the download speed I'm getting, I'll be lucky if this is finished downloading by tomorrow night.  is there any other way to do this?

Also, did I hear that the stable release of Ubuntu 8.10 is going to be released tomorrow? if so, should I just install it tomorrow and see if that fixes my problem?

(sorry about the double, now triple post)

---

