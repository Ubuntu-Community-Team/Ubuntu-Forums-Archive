---
title: "HOWTO: Install and run Shareaza on Ubuntu"
date: 2007-01-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Yopo on 2007-01-02
Because I think there are people that would like to use Shareaza on Ubuntu but don't know that it's possible or how to do it (also regarding the posts I've seen about Shareaza on this forum) I've written this HOWTO that I hope will help people enjoying Shareaza on Ubuntu.

This HOWTO is tested on Ubuntu Edgy (6.10) i368 (32-bit).

Needed to install are:
    - Wine
    - Shareaza

Because Shareaza works with Wine you have to have Wine installed and it's always best to have the latest version of Wine . 

So if you don't have the latest version of wine already, add the Wine repository and install it, in a terminal do:
```
sudo nano -w /etc/apt/sources.list
```

And add these lines at the bottom of the list:
```
##Wine##
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
```
Save it: [Control-o] -> [Enter] 
Exit: [Control-x]

Then download and install Shareaza and Wine: 
Copy and paste these three lines in a terminal (you can copy-paste the three all at once):
```
sudo apt-get wine
wget http://www.shareaza.com/mirror_beta.php
wine Shareaza_2.2.3.0.exe
```

While installing just choose the default menu and directory options. Wine will create menu-items for you and it will install Shareaza in the directory of wine: /home/yopo/.wine/drive_c/Program Files/Shareaza. 

In the menu you'll find Shareaza at: Applications -> wine -> Programs -> Shareaza. 
It's recommended to choose (tabbed mode) for more detailed options in Shareaza (power mode) or otherwise choose normal. Under wine it will not remember the last mode you chose at Shareaza so that's why you can choose it at launch.

If everything went fine you are now in Shareaza on Ubuntu!

At first launch of Shareaza you'll get the the wizard. At the first step, choose your network settings.
Now after that: To share files, after you click the Add..-button you can now just browse My documents to select directories from your home directory in Ubuntu and off course you can browse from the root /.

But as you can see Shareaza isn't able to connect yet so we have to help her a little...
The first time you have to add someone (a hub) manually to connect to.
So you now have to look for a hub in a list of a gnutella-webcache.
For Gnutella2 (the default network of Shareaza, so recommended) look at:
[http://bazooka1.servehttp.com/g2/bazooka.php?showhosts=1&net=gnutella2](http://bazooka1.servehttp.com/g2/bazooka.php?showhosts=1&net=gnutella2)
And copy the ip-adress of a hub together with the port the hub can be reached on. Something like this:
88.106.228.31:6346

In Shareaza:
```
Press [F11] -> [control-T] (or [Connect To])
```
And paste the whole line you just copied in the left column and leave the right one blank. Alternatively you can paste the ip-address in the left column (the number before ':') and fill in the ip-address in the right column (the number after ':'), it has  exactly the same effect. 

At 'Network Protocol' choose Gnutella2 and click [Connect].
Shareaza will now try to connect to the hub. If she succeeds, a line will stay in the network screen, if not the lines will disappear. But nothing is lost yet, just try again with another address from the list until she succeeds to connect.


To connect to Gnutella1, look at:
[http://gwc.downloadmusicinc.com/gcache.cgi](http://gwc.downloadmusicinc.com/gcache.cgi) for a hub to connect to and do exactly the same as you did with gnutella2 except that you choose Gnutella1 at [Network Protocol] off course.

To connect Edonkey to you can now try to query an existing server.met list since you are already connected:
Press [F9] -> look at column [Type] for [Server.met], right-click on a line and choose [query now].

Congratulations, if everything went well you're now connected! Enjoy!        


To uninstall Shareaza. 
Go to: 
```
Applications -> wine -> Programs -> Shareaza -> Uninstall 
```

Or in Terminal do:
 ```
uninstaller
```
And select Shareaza to uninstall.


There's a bug affecting the behavior of the menu's, if you go from one menu to the next one at the left or right, the previous one can stick on your screen. To avoid it, you can press escape before going to the next menu.

Please let me know if this was helpful to you or if you need some help.

---

### Post by H.E. Pennypacker on 2007-03-13
How well does it work under Wine?

---

### Post by cub on 2007-03-16
> **Yopo said:**
> Then download and install Shareaza and Wine: 
Copy and paste these three lines in a terminal (you can copy-paste the three all at once):
```
sudo apt-get wine
wget http://www.shareaza.com/mirror_beta.php
wine Shareaza_2.2.3.0.exe
```

While installing just choose the default menu and directory options. Wine will create menu-items for you and it will install Shareaza in the directory of wine: /home/yopo/.wine/drive_c/Program Files/Shareaza. 

In the menu you'll find Shareaza at: Applications -> wine -> Programs -> Shareaza. 
It's recommended to choose (tabbed mode) for more detailed options in Shareaza (power mode) or otherwise choose normal. Under wine it will not remember the last mode you chose at Shareaza so that's why you can choose it at launch.

If everything went fine you are now in Shareaza on Ubuntu!

At first launch of Shareaza you'll get the the wizard. At the first step, choose your network settings.

Everything goes as planned until I try to start Shareaza. It begins to start, the splash screen shows but then everything just disappears.
I only got hold of the Shareaza_2.2.5.0.exe.

---

### Post by Yopo on 2007-04-04
> **H.E. Pennypacker said:**
> How well does it work under Wine?

Except for the menu's that can stick that i mentioned before and the media player that doesnt seem to work yet under wine it works fine.

---

### Post by Yopo on 2007-04-04
> **cub said:**
> Everything goes as planned until I try to start Shareaza. It begins to start, the splash screen shows but then everything just disappears.
I only got hold of the Shareaza_2.2.5.0.exe.


I didn't test Shareaza 2.2.5.0 under wine myself  yet. Do you use the latest version of wine? Especially with a new version it's important to use the most recent version of wine. If not, add the wine repository like I mentioned in the howto and try to install Shareaza again after updating wine.

---

### Post by Jonne on 2007-09-23
There's a guide on [Shareaza's wiki](http://shareaza.sourceforge.net/wiki/ShareazaLinux). In the guide there's a link to a (nightly updated) hostcache.dat file you can use to get connected, without having to do it manually.

---

### Post by Loevborg on 2007-09-26
Remeber to do:

aptitude install msttcorefonts

to get decent fonts.

---

### Post by ljs662 on 2007-10-14
works fine for me, running ubuntu gutsy beta, 7.10

---

### Post by Yuliya on 2007-10-21
I get a message saying "there is no response" and "you cannot connet to shareaza.com"(or something like that)

---

### Post by Jonne on 2007-10-21
The site's been down for a while, here's the [google cached](http://64.233.183.104/search?q=cache:fJeJYcRNsT8J:wiki.shareaza.com/static/ShareazaLinux+http://wiki.shareaza.com/static/ShareazaLinux&hl=nl&ct=clnk&cd=1&gl=be&client=firefox-a) version

---

### Post by Yuliya on 2007-10-28
I clicked on your link, and they send me to shareaza.com and I ALWAYS get this message:

Unable to connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at [www.shareaza.com](www.shareaza.com).

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




      ... it's the onyl page where I get it too, why?

---

### Post by Jonne on 2007-10-28
shareaza.com is down, there's a mirror available at [shareaza.sourceforge.net](http://shareaza.sourceforge.net/)

I'd also like to note that in Gutsy WINE has been fixed so Shareaza can connect to gwebcaches on its own, without having to do it manually.

---

### Post by Docter on 2008-01-03
wine-0.9.41
Shareaza 2.3.0.0 and 2.2.1.0

upon trying to run it I get x11 errors followed by a register dump.
```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:win:AnimateWindow partial stub
err:x11drv:X11DRV_CreateWindow invalid window width -55
err:x11drv:X11DRV_CreateWindow invalid window height -189708
err:x11drv:X11DRV_CreateWindow invalid window height 3370484
err:x11drv:X11DRV_CreateWindow invalid window width -593861
err:x11drv:X11DRV_CreateWindow invalid window width -9262320
err:x11drv:X11DRV_CreateWindow invalid window height -264
err:x11drv:X11DRV_CreateWindow invalid window width -9262320
err:x11drv:X11DRV_CreateWindow invalid window height -476
err:x11drv:X11DRV_CreateWindow invalid window width 6226856
err:x11drv:X11DRV_CreateWindow invalid window height -3400381
err:x11drv:X11DRV_CreateWindow invalid window height -6175789
err:x11drv:X11DRV_CreateWindow invalid window height -26
err:x11drv:X11DRV_CreateWindow invalid window height -26
err:x11drv:X11DRV_CreateWindow invalid window height -26
err:x11drv:X11DRV_CreateWindow invalid window height -26
err:x11drv:X11DRV_CreateWindow invalid window height -26
wine: Unhandled page fault on read access to 0x00000023 at address 0x4c4099 (thread 0034), starting debugger...
Unhandled exception: page fault on read access to 0x00000023 in 32-bit code (0x004c4099).
Register dump:
```

From this guide:
[http://shareaza.sourceforge.net/wiki/ShareazaLinux](http://shareaza.sourceforge.net/wiki/ShareazaLinux)

It suggests to delete these keys from the registry:
> 
Sometimes Shareaza's GUI will fail to appear when starting up. This has something to with Shareaza having problems with either virtual desktops or Beryl/Compiz (it stores negative values for the keys that control Shareaza's location on your desktop). If this happens, you need to start regedit, and delete the following keys:

HKCU/Software/Shareaza/Shareaza/Windows/CMainWnd.Bottom
HKCU/Software/Shareaza/Shareaza/Windows/CMainWnd.Left
HKCU/Software/Shareaza/Shareaza/Windows/CMainWnd.Right
HKCU/Software/Shareaza/Shareaza/Windows/CMainWnd.Top

But they do not exist. So I tried creating them giving the bottom and right values as 100 and leaving the others as 0. But it gave the same error. This seems the most likely cause but I have no idea how to rectify it, any suggestions?


I've also tried following the instructions in:
[http://wiki.jswindle.com/index.php/Wine_Shareaza](http://wiki.jswindle.com/index.php/Wine_Shareaza)

Which gives instructions to install the tahoma font:

> Installing the font
```

$ wine tahoma32.exe
```


When that is done installing, we need to edit the Wine config file so it will use the new font nicely.


```
Editing Wine Config

$ cd ~/.wine
$ <your editing program> config

Add this anywhere below the [DllOverrides] area;

;;; Per-Program Settings Area

;; Shareaza
[AppDefaults\\Shareaza.exe\\x11drv]
"ClientSideAntiAliasWithRender" = "Y"

```

Thus, it won't affect the other applications ran with Wine. It does not have to go below [DllOverrides], but it just makes it easy fix it everyone places it in one spot.

Once done, you have a working Shareaza, unless your firewall is blocking it. 

But the version ofwine I'm running doesn't have a config file there instead it uses winecfg. Any idea how to acheive the same effect?

I don't think that this is what is giving me the exception but you never know with this kind of thing.

Any help greatly appreciated.

---

### Post by Jonne on 2008-01-03
I added the registry keys thing only for cases where Shareaza starts and runs fine, but you can't bring up the gui because it's rendered somewhere out of your screen area. It won't fix crashes.
 In any case, try getting a more recent version of WINE (gutsy comes with 9.46), and get Shareaza 2.3.1.0 (which is the latest version as of two days ago).

---

### Post by Docter on 2008-01-03
Many thanks! 

My aversion to upgrading was most definately the problem.

wine version 9.52 and shareaza 2.3 works well.

---

### Post by gleble on 2008-07-10
The links to access hubs don't work. How can I find others?

---

### Post by Jonne on 2008-07-10
Shareaza should be able to connect by itself. Otherwise try asking someone for a working hub on irc://irc.p2pchat.net/#shareaza .

---

### Post by forger on 2008-07-10
a lot of people marked shareaza as bad:
[http://www.mywot.com/en/scorecard/www.shareaza.com/](http://www.mywot.com/en/scorecard/www.shareaza.com/)

---

### Post by Jonne on 2008-07-10
That's because the original shareaza.com domain was taken over by scammers (they're still trying to get it back, but it's not easy). Only get it from shareaza.sourceforge.net. It's been said before in this thread.

---

### Post by stafio on 2008-08-19
As Jonne mentioned, Shareaza has run into some problems with scammers. The creators have started fresh and created a new program called Panthera (to be released next week) that will run on Linux natively. You can read all about it [here]("http://torrentfreak.com/shareaza-team-fight-back-with-panthera-project-080818/").

---

### Post by Jonne on 2008-08-19
Panthera (and Sharelin, which is another promising project) are far from complete or even functional, but feel free to help out with testing either of those. For now Shareaza on WINE is your best bet, though.

---

