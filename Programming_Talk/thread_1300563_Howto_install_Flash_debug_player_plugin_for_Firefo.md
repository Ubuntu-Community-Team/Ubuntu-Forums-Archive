---
title: "Howto install Flash debug player plugin for Firefox in Ubuntu 9.04 64 bit"
date: 2009-10-25
forum: Programming Talk
---

### Post by rajder on 2009-10-25
Hi everyone,
This took me the better part of the day so I thought this might be a good opportunity to give something back to this great forum! : o )
There's a lot of articles and blog posts out there about 64 bit flash **debug** player plugin and how to do it, but none worked for me.

Bad news, the problem is, which you probably know if you have found this article, that there is no 64 bit flash **DEBUG** player, and as of now Adobe has no plans to make one.
Good news, if you install the flash plugin via apt-get you will get a 32 bit plugin and the nspluginwrapper which makes it possible to run 32 bit plugins in a 64 bit browser, niice. All we have to do now is to replace the flash players shared object file with the **32 bit** debug version.
Step by step:

[LIST=1]
[*]uninstall any kind of flash plug you have at the moment, make sure it's gone. (this was my problem, probably had the real 64 bit plug installed and there were multiple libflashplayer.so spread all over the place. Make sure you clean out any flash plugin related files from your system)
search for installed flashplugin packages:
```
**aptitude search flash**
p   flashblock                                                - mozilla extension that replaces flash elements with a button        
i A flashplugin-installer                                     - Adobe Flash Player plugin installer                                 
i   flashplugin-nonfree                                       - Adobe Flash Player plugin installer (transitional package)          
p   flashrom                                                  - Universal BIOS/ROM/flash programming utility                        
p   flashybrid                                                - automates use of a flash disk as the root filesystem                
p   libroxen-flash2                                           - Flash2 module for the Roxen Challenger web server                   
p   m16c-flash                                                - Flash programmer for Renesas M16C and R8C microcontrollers          
p   vrflash                                                   - tool to flash kernels and romdisks to Agenda VR                     

```
you will get a list of packages with flash in the package name, remove them from your system.(flashplugin-nonfree, flashplugin-installer) using the command: sudo apt-get purge [PACKAGE NAME], e.g. **sudo apt-get purge flashplugin-nonfree**
I always do **sudo apt-get autoremove** after purge, to get rid of remaining junk, not sure if it's important, but it feels good :)


[*]install the flash plugin using the command: **sudo apt-get install flashplugin-nonfree**


[*]download the debug player from Adobe: **[http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz](http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz)**
if they moved the file google for: **flash debug player linux**


[*]replace the installed shared object file /usr/lib/flashplugin-installer/libflashplayer.so with the one you downloaded


[*]**_EDIT: see post #9 by lviggiani_**
[/LIST]




This works for me, hope it works for you too!

---

### Post by Yaba on 2009-11-04
Thank you very much. Also works on 9.10 Karmic Koala.

---

### Post by blz on 2010-04-03
Thank you very very much! Worked for me too! :))) 
(I'm using Ubuntu 9.10 - the Karmic Koala - 86x)

---

### Post by pterion on 2010-08-06
In Lucid (10.04) there is only the npwrapper.libflashplayer.so
How can one install the debugger version of the 32bit player in this case?

---

### Post by Yaba on 2010-08-06
> **pterion said:**
> In Lucid (10.04) there is only the npwrapper.libflashplayer.so
How can one install the debugger version of the 32bit player in this case?

Just follow the instructions above. It still works for me.

---

### Post by opiumpoetry on 2011-02-19
or you could just get rid of Adobe Flash and install Gnash. i've heard it works same as Adobe, correct me if i'm wrong.

---

### Post by srijith_bhandary on 2011-03-18
I am not clear about the last step.

Exactly which file we have to replace ?  
The downloaded file is a tar.gz file. 

Should I have to replace with libflashplayer.so that is found in flash_player_10_linux_dev/plugin/debugger/install_flash_player_10_linux  in downloaded package ?


And one more thing , After doing  [B]sudo apt-get install flashplugin-nonfree 

[/B]I am gettingSetting up flashplugin-installer (10.2.152.27ubuntu0.9.10.1) ...
Downloading...
--2011-03-18 12:37:33--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.2.152.27.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.2.152.27.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4967098 (4.7M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.2.152.27.orig.tar.gz'

     0K .......... .........
. ..Is it done ? or should I still wait ?

---

### Post by cawo on 2011-04-12
Still works for 10.10 too.

---

### Post by lviggiani on 2011-08-22
Confirm it works on 11.04 too.
With latest version of flash player, you should also copy (merge) the folder "usr" that you'll find in the download package with yours. This will include the plugin off-line control panel.

@rajder:
Perhaps you may want to change this thread title to "Howto install Flash debug player plugin for Firefox in Ubuntu 9.04 **(and above)** 64 bit"

---

### Post by wcastrillon on 2011-10-24
works for 11.10 too.
You have to do  what @[SIZE=2][I]lviggiani says at the end :popcorn:
[/I][/SIZE]

---

