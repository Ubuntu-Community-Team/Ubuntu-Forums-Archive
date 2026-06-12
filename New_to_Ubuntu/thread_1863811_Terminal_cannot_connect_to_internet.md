---
title: "Terminal cannot connect to internet"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by kilosierra on 2011-10-18
Hi, I just installed the 11.10 and am having similar problems. Ran sudo apt-get update && sudo apt-get upgrade and after about 30 min, the terminal stopped connecting to the internet. Now, i cant get the terminal to connect, cant get the software centre to connect and download but the browser works fine! This is my first time on Ubuntu/ any linux distro...please HELP!

---

### Post by nothingspecial on 2011-10-18
Post moved to it's own thread.

---

### Post by matt_symes on 2011-10-18
Hi

Run this command again. Post back the entire output so we can see the error messages.

```
sudo apt-get update
```

Can you try another software source mirror ?

Kind regards

---

### Post by ninjaaron on 2011-10-18
It may have to do with server clogging because of the new release.  The repos are always really slow for the first few weeks after a release.

---

### Post by Promille on 2011-10-18
Why dont you try the GUI update-manager? Press ALT+F2 and and type in 'gksu update-manager' without ''

---

### Post by kilosierra on 2011-10-19
hi, thanks for your inputs, ran GUI update manager...infact read your  posts after i started it. It connected fine, is running now. It seems,  all y problems started when downloading two softwares/updates, adobe  flash downloader and ttf mscorefonts-installer. Right now, its still  stuck (since the past 15 mins or so) on the fonts installer.
Ran the update command as suggested and its showing the following output:

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

i guess its due to the update manager already running. Anything I can do to get through this? The file name its trying to download is arialb32.exe (cant believe stupid arial font is causing me so much pain!)

All your help is much appreciated as I am very new to any Linux distro.

Regards,

---

### Post by matt_symes on 2011-10-19
Hi
> 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

i guess its due to the update manager already running.

You are correct about this.

Give it some time to download. If it's still stuck in a couple of hours then post back.

Kind regards

---

### Post by kilosierra on 2011-10-19
Hi,

It was stuck for about 2.5 hrs, killed updater, rebooted the system and decided no more updates for a week (the servers might be busy) cause it keeps trying to connect to cannonical or sourceforge servers and keeps either timing out or shows no network when actually, i am browsing!

But, to my dismay, as i tried watching "Thrill is Gone' at Crossroads on youtube, ifound that flash player isnt installed. So, I did it the windows way, went to adobe's website, it launched the software centre, authenticated the source, but now (for the past half an hour or so), its stuck at Adding Software Source and i have another entry, updating cache in que. Both show null on the progress bar. This is really frustrating. All I want is flash player to watch youtube videos! Why make it so complicated? Or am I being an idiot here and missing out something obvious?

please Help!

Thanks and Regards,

KS

---

### Post by matt_symes on 2011-10-19
Hi

Reboot yoiur PC so nothing has a lock on dpkg.

Follow my post #3. If there are error post back the entire output. That is what we need to see.

If there are no error from above type

```
sudo apt-get install htop
```

If  there are errors in this step then post them.

if there are no errors then type

```
software-center
```

and try to install something. If there are errors then post them back here.

Use copy and paste from the terminal into your next post.

If we cannot see the errors then we have next to no hope of helping you.

If there are no errors from the steps above then it points to a different problem.

Kind regards

---

### Post by kilosierra on 2011-10-21
Hi,

I did as you suggested. There were errors in sudo apt-get update. The following is the output i got in terminal from that command:
```

kshitij@DeviBhawan-HomeComp:~$ sudo apt-get update
[sudo] password for kshitij: 
Ign http://security.ubuntu.com oneiric-security InRelease                                           
Ign http://extras.ubuntu.com oneiric InRelease                                                      
Ign http://lk.archive.ubuntu.com oneiric InRelease
Ign http://lk.archive.ubuntu.com oneiric-updates InRelease
Ign http://lk.archive.ubuntu.com oneiric-backports InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Hit http://lk.archive.ubuntu.com oneiric Release.gpg                          
Hit http://security.ubuntu.com oneiric-security Release
Hit http://extras.ubuntu.com oneiric Release                          
Get:2 http://lk.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://security.ubuntu.com oneiric-security/main Sources                    
Hit http://extras.ubuntu.com oneiric/main Sources                    
Hit http://lk.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages                      
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Get:3 http://lk.archive.ubuntu.com oneiric-updates Release [28.2 kB] 
Hit http://security.ubuntu.com oneiric-security/main Translation-en        
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en  
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports Release
Hit http://security.ubuntu.com oneiric-security/universe Translation-en                     
Hit http://lk.archive.ubuntu.com oneiric/main Sources                
Hit http://lk.archive.ubuntu.com oneiric/restricted Sources
Hit http://lk.archive.ubuntu.com oneiric/universe Sources
Hit http://lk.archive.ubuntu.com oneiric/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric/main i386 Packages
Hit http://lk.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://lk.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://lk.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/universe TranslationIndex
Get:4 http://lk.archive.ubuntu.com oneiric-updates/main Sources [16.8 kB]
Get:5 http://lk.archive.ubuntu.com oneiric-updates/restricted Sources [14 B]
Get:6 http://lk.archive.ubuntu.com oneiric-updates/universe Sources [1,886 B]
Get:7 http://lk.archive.ubuntu.com oneiric-updates/multiverse Sources [14 B]
Get:8 http://lk.archive.ubuntu.com oneiric-updates/main i386 Packages [30.1 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Get:9 http://lk.archive.ubuntu.com oneiric-updates/restricted i386 Packages [14 B]
Get:10 http://lk.archive.ubuntu.com oneiric-updates/universe i386 Packages [8,908 B]
Get:11 http://lk.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [14 B]
Get:12 http://lk.archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:13 http://lk.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [70 B]
Get:14 http://lk.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [70 B]
Get:15 http://lk.archive.ubuntu.com oneiric-updates/universe TranslationIndex [72 B]
Hit http://lk.archive.ubuntu.com oneiric-backports/main Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted Sources
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Ign http://lk.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://lk.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://lk.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://lk.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric/universe Translation-en
Get:16 http://lk.archive.ubuntu.com oneiric-updates/main Translation-en [15.8 kB]
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:17 http://lk.archive.ubuntu.com oneiric-updates/universe Translation-en [6,093 B]
Ign http://lk.archive.ubuntu.com oneiric-backports/main Translation-en_US                                
Ign http://lk.archive.ubuntu.com oneiric-backports/main Translation-en                                   
Ign http://lk.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US                          
Ign http://lk.archive.ubuntu.com oneiric-backports/multiverse Translation-en                             
Ign http://lk.archive.ubuntu.com oneiric-backports/restricted Translation-en_US                          
Ign http://lk.archive.ubuntu.com oneiric-backports/restricted Translation-en                             
Ign http://lk.archive.ubuntu.com oneiric-backports/universe Translation-en_US                            
Ign http://lk.archive.ubuntu.com oneiric-backports/universe Translation-en                               
Fetched 108 kB in 8s (13.4 kB/s)                                                                         
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```After this, I ran the 'sudo dpkg --configure -a' command. It is now stuck whilst trying to download updates. The following is the current state:

```
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg --configure -a
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2011-10-22 11:47:19--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 1.0.0.0
Connecting to archive.canonical.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--2011-10-22 11:50:29--  (try: 2)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Connecting to archive.canonical.com|1.0.0.0|:80... failed: Connection timed out.
Giving up.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ttf-mscorefonts-installer (3.3ubuntu4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2011-10-22 11:53:40--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-22 11:54:40--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-22 11:55:41--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-22 11:56:41--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-22 11:57:41--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-22 11:58:42--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... 
```This is what goes on when I try to update, or install through the software centre. I downloaded about a gig of data yesterday through ftp, faced no problems, direct downloads, no problems, torrents - no problems. However, when I try to update through terminal, or through update manager or install through software centre, I get this problem.

What do you recommend?

By the way, Thank you so much for all your efforts. You guys have been most helpful, specially Matt. Hopefully we can get this problem solved?

Warmest Regards,

---

### Post by matt_symes on 2011-10-21
Hi

Now i think we may be getting somewhere. We now know the root cause of the problem. That means we can start tackling a solution. It make take a couple of attempts so bear with me.

> 
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg --configure -a
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2011-10-22 11:47:19--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz)
Resolving archive.canonical.com... 1.0.0.0
Connecting to archive.canonical.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--2011-10-22  11:50:29--  (try: 2)   [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz)
Connecting to archive.canonical.com|1.0.0.0|:80... failed: Connection timed out.
Giving up.
<snip>

This is wrong.

> Resolving archive.canonical.com... 1.0.0.0

The  resolved ip address is incorrect It cannot connect to 1.0.0.0:80 and  hence it is failing. The same with the other package and this is what is  causing all your problems.

So the first thing i suggest we do is to try to remove the offending packages and then take it from there.

Open a terminal and type these two commands

```
sudo dpkg -r ttf-mscorefonts-installer
sudo dpkg -r adobe-flashplugin

```

If this fails due to dependency problems (or any other  problems) then post back the results. If it fails also type these two  commands

```
dpkg -l  adobe-flashplugin
dpkg -l ttf-mscorefonts-installer
```

That is a small L after dpkg. Post the results back here.

Next from the terminal type these two commands if it fails or succeeds.
```

nslookup archive.canonical.com
nslookup switch.dl.sourceforge.net
```

Post back results.

Kind regards

---

### Post by kilosierra on 2011-10-21
Hi,

I was able to remove mscorefonts-installer, but wasnt able to do the same for adobe-flashplugin.
Then, I ran the '-l' command like you asked in terminal for flash-plugin and the nslookup commands for both the websites. The results were as follows:

```
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg -r ttf-mscorefonts-installer
[sudo] password for kshitij: 
(Reading database ... 126690 files and directories currently installed.)
Removing ttf-mscorefonts-installer ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg -r adobe-flashplugin
dpkg: warning: there's no installed package matching adobe-flashplugin
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg -r adobe-flashplugin
dpkg: warning: there's no installed package matching adobe-flashplugin
kshitij@DeviBhawan-HomeComp:~$ dpkg -l  adobe-flashplugin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  adobe-flashplu <none>         (no description available)
kshitij@DeviBhawan-HomeComp:~$ nslookup archive.canonical.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    archive.canonical.com
Address: 91.189.92.191
Name:    archive.canonical.com
Address: 91.189.88.33

kshitij@DeviBhawan-HomeComp:~$ nslookup switch.dl.sourceforge.net
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    switch.dl.sourceforge.net
Address: 130.59.138.21
```So, I understand that we removed mscorefonts-installer but it couldnt find adobe flash-plugin. Also, if it gives a correct response for nslookup, why does it connect to a different ip address when updating? Could Port 80 be busy? (Sorry if its a stupid question)

Thanks again for your help in trying to resolve this issue.

Warmest Regards

kshitij

---

### Post by matt_symes on 2011-10-21
Hi

> **kilosierra said:**
> Hi,

I was able to remove mscorefonts-installer, but wasnt able to do the same for adobe-flashplugin.

Sorry my mistake.... Try this...

```
sudo dpkg -r flashplugin-downloader
```

...if no errors then type...

```
sudo apt-get update
```

...if no errors then type...

```
sudo apt-get install htop
```

Post back any errors.

> 
 nslookup commands for both the websites. The results were as  follows:

 kshitij@DeviBhawan-HomeComp:~$ nslookup archive.canonical.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    archive.canonical.com
Address: 91.189.92.191
Name:    archive.canonical.com
Address: 91.189.88.33

kshitij@DeviBhawan-HomeComp:~$ nslookup switch.dl.sourceforge.net
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    switch.dl.sourceforge.net
Address: 130.59.138.21

dns resolution looks good here.

> Also, if it gives a correct response for nslookup, why does it connect to a different ip address when updating? Could Port 80 be busy? (Sorry if its a stupid question)

There are no dumb questions. The issue is not with the port. The issue is with the ip address. We can look at that later when we get flash installed for you. At the moment the steps are to get you to the stage where you can install something such as htop.

Kind regards

---

### Post by kilosierra on 2011-10-22
Hi,

I already ran the remove command for adobe flash-plugin. The result was posted in the terminal window output. It was as follows:

```
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg -r adobe-flashplugin
dpkg: warning: there's no installed package matching adobe-flashplugin
```Also ran the '-l' command on the same package. The result was as follows:

```
kshitij@DeviBhawan-HomeComp:~$ dpkg -l  adobe-flashplugin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  adobe-flashplu <none>         (no description available)
```I ran sudo apt-get update and there were no errors. I am posting the result, if you would like to have a look:

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get update
[sudo] password for kshitij: 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://lk.archive.ubuntu.com oneiric InRelease                             
Ign http://lk.archive.ubuntu.com oneiric-updates InRelease
Ign http://lk.archive.ubuntu.com oneiric-backports InRelease
Ign http://extras.ubuntu.com oneiric InRelease                       
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://lk.archive.ubuntu.com oneiric Release.gpg
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Hit http://security.ubuntu.com oneiric-security Release                       
Hit http://lk.archive.ubuntu.com oneiric-updates Release.gpg          
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://security.ubuntu.com oneiric-security/main Sources          
Hit http://lk.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric Release                     
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates Release             
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports Release
Hit http://lk.archive.ubuntu.com oneiric/main Sources                          
Hit http://lk.archive.ubuntu.com oneiric/restricted Sources          
Hit http://lk.archive.ubuntu.com oneiric/universe Sources
Hit http://lk.archive.ubuntu.com oneiric/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://lk.archive.ubuntu.com oneiric/multiverse i386 Packages    
Hit http://lk.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://lk.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://lk.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://lk.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/main Sources
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-backports/main Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Ign http://lk.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://lk.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://lk.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://lk.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric/universe Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://lk.archive.ubuntu.com oneiric-backports/main Translation-en_US      
Ign http://lk.archive.ubuntu.com oneiric-backports/main Translation-en         
Ign http://lk.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
Ign http://lk.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Ign http://lk.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
Ign http://lk.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Ign http://lk.archive.ubuntu.com oneiric-backports/universe Translation-en_US  
Ign http://lk.archive.ubuntu.com oneiric-backports/universe Translation-en     
Fetched 72 B in 7s (9 B/s)                                                     
Reading package lists... Done

```Then, like you suggested,I ran the install htop command. This brought the terminal back to the familiar screen. However, it lasted a short duration. The output was:

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 64.3 kB of archives.
After this operation, 221 kB of additional disk space will be used.
Get:1 http://lk.archive.ubuntu.com/ubuntu/ oneiric/universe htop i386 0.9-4 [64.3 kB]
Fetched 64.3 kB in 1s (33.4 kB/s)
Selecting previously deselected package htop.
(Reading database ... 126683 files and directories currently installed.)
Unpacking htop (from .../archives/htop_0.9-4_i386.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Setting up flashplugin-downloader (11.0.1.152ubuntu1) ...
Downloading...
--2011-10-23 11:31:27--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Resolving archive.canonical.com... 1.0.0.0
Connecting to archive.canonical.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--2011-10-23 11:34:38--  (try: 2)  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
Connecting to archive.canonical.com|1.0.0.0|:80... failed: Connection timed out.
Giving up.

download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:
  Package flashplugin-downloader is not configured yet.
dpkg: error processing flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up htop (0.9-4) ...
Errors were encountered while processing:
 flashplugin-downloader
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
kshitij@DeviBhawan-HomeComp:~$ 

```Is there an error in flashplugin-downloader due to which the installer isnt running? What can we do further?

Thanks and Regards,

Kshitij

---

### Post by matt_symes on 2011-10-22
Hi

We are getting there.

```
sudo dpkg -r flashplugin-installer
```If that does not work then we will look at manually editing the dpkg files otherwise we will look at installing flash for you again.

Kind regards

---

### Post by kilosierra on 2011-10-23
Done

```
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg -r flashplugin-installer
[sudo] password for kshitij: 
(Reading database ... 140202 files and directories currently installed.)
Removing flashplugin-installer ...
kshitij@DeviBhawan-HomeComp:~$ 
```

Now, reinstall flash? Using software center or terminal?

Also, in the process, we removed ms corefonts and flash plugin...do we reinstall them together?

Regards,

---

### Post by matt_symes on 2011-10-23
Hi

> **kilosierra said:**
> Now, reinstall flash? Using software center or terminal?

Also, in the process, we removed ms corefonts and flash plugin...do we reinstall them together?

Excellent. Now we install flash and ms fonts.

Open a terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```and

```
sudo apt-get install ttf-mscorefonts-installer
```Use the tab key on the font install page to select the EULA.

Post back any errors.

Kind regards

---

### Post by kilosierra on 2011-10-23
Hi,

Couldn't even GET to the EULA! Its trying to connect to the wrong IP address again!
Heres the output for the restricted extras command:

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for kshitij: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And following for what i could copy from the ms corefonts:

```
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-23 21:18:53--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-10-23 21:19:53--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving ufpr.dl.sourceforge.net... 40.1.0.130, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|40.1.0.130|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|2801:82:80ff:8000::3|:80... failed: Network is unreachable.
--2011-10-23 21:20:54--  http://internode.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:21:54--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.16, 208.122.31.17, 208.122.31.18, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/georgi32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2011-10-23 21:22:15--  http://downloads.sourceforge.net/sourceforge/corefonts/georgi32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:23:15--  http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:24:15--  http://internap.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2011-10-23 21:24:55--  http://downloads.sourceforge.net/corefonts/impact32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:25:57--  http://switch.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-23 21:26:58--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:27:58--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-23 21:28:59--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-23 21:30:00--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-23 21:31:00--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-10-23 21:32:00--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving ufpr.dl.sourceforge.net... 40.1.0.130, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|40.1.0.130|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|2801:82:80ff:8000::3|:80... failed: Network is unreachable.
--2011-10-23 21:33:02--  http://internode.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:34:02--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.22, 208.122.31.24, 208.122.31.26, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.22|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/impact32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2011-10-23 21:34:23--  http://downloads.sourceforge.net/sourceforge/corefonts/impact32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:35:24--  http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:36:24--  http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2011-10-23 21:37:04--  http://downloads.sourceforge.net/corefonts/times32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:38:04--  http://switch.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-23 21:39:04--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:40:04--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-23 21:41:04--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-23 21:42:04--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-23 21:43:04--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-10-23 21:44:04--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving ufpr.dl.sourceforge.net... 40.1.0.130, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|40.1.0.130|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|2801:82:80ff:8000::3|:80... failed: Network is unreachable.
--2011-10-23 21:45:05--  http://internode.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:46:05--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.18, 208.122.31.22, 208.122.31.24, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.18|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/times32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2011-10-23 21:46:26--  http://downloads.sourceforge.net/sourceforge/corefonts/times32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:47:26--  http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:48:26--  http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2011-10-23 21:49:06--  http://downloads.sourceforge.net/corefonts/trebuc32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:50:07--  http://switch.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-23 21:51:07--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:52:07--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-23 21:53:07--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-23 21:54:07--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-23 21:55:07--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-10-23 21:56:07--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving ufpr.dl.sourceforge.net... 40.1.0.130, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|40.1.0.130|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|2801:82:80ff:8000::3|:80... failed: Network is unreachable.
--2011-10-23 21:57:08--  http://internode.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:58:08--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.24, 208.122.31.26, 208.122.31.27, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.24|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2011-10-23 21:58:29--  http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 21:59:29--  http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:00:29--  http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2011-10-23 22:01:09--  http://downloads.sourceforge.net/corefonts/verdan32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:02:09--  http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-23 22:03:09--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:04:09--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-23 22:05:09--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-23 22:06:09--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-23 22:07:09--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-10-23 22:08:09--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving ufpr.dl.sourceforge.net... 40.1.0.130, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|40.1.0.130|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|2801:82:80ff:8000::3|:80... failed: Network is unreachable.
--2011-10-23 22:09:10--  http://internode.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:10:10--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.4, 208.122.31.11, 208.122.31.12, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.4|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2011-10-23 22:10:31--  http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:11:32--  http://kent.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:12:32--  http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2011-10-23 22:13:12--  http://downloads.sourceforge.net/corefonts/webdin32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:14:12--  http://switch.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-23 22:15:12--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:16:12--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-23 22:17:12--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-23 22:18:12--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-23 22:19:12--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2011-10-23 22:20:12--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving ufpr.dl.sourceforge.net... 40.1.0.130, 2801:82:80ff:8000::3
Connecting to ufpr.dl.sourceforge.net|40.1.0.130|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|2801:82:80ff:8000::3|:80... failed: Network is unreachable.
--2011-10-23 22:21:13--  http://internode.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:22:13--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.11, 208.122.31.12, 208.122.31.13, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.11|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2011-10-23 22:22:34--  http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:23:34--  http://kent.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-23 22:24:34--  http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
The following fonts failed to install :  andale32.exe arialb32.exe arial32.exe comic32.exe courie32.exe georgi32.exe impact32.exe times32.exe trebuc32.exe verdan32.exe webdin32.exe.
The fonts are NOT installed.
Please run 'dpkg-reconfigure ttf-mscorefonts-installer' to perform the installation again

```

I ran it again and got the following:

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Please advice further course of actions. 

Thanks and Regards

---

### Post by matt_symes on 2011-10-25
Hi

Let's check your source.list file. Can you post the output of

```
cat /etc/apt/sources.list
```and 

```
ls /etc/apt/sources.list.d/
```Can you open software center again ? Can you install software through the terminal ?

Can you also post the contents of

```
apt-config dump
```Kind regards

---

### Post by kilosierra on 2011-10-26
Hi,

Got the following output for cat /etc/apt/sources.list :

```
kshitij@DeviBhawan-HomeComp:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://lk.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://lk.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
kshitij@DeviBhawan-HomeComp:~$ 



kshitij@DeviBhawan-HomeComp:~$ ls /etc/apt/sources.list.d/
medibuntu.list
kshitij@DeviBhawan-HomeComp:~$ 
```
And the following for ls /etc/apt/sources.list.d/ :
```

kshitij@DeviBhawan-HomeComp:~$ ls /etc/apt/sources.list.d/
medibuntu.list
kshitij@DeviBhawan-HomeComp:~$ 
```Opening software centre is not a problem, recently installed Amarok and vlc using software centre. Also, installed Synaptic Package Manager using Terminal just now, to check if I can do so. That went without a hitch, the output was as follows:

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get install synaptic
[sudo] password for kshitij: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  libept1 synaptic
0 upgraded, 2 newly installed, 0 to remove and 124 not upgraded.
Need to get 2,284 kB of archives.
After this operation, 7,549 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://lk.archive.ubuntu.com/ubuntu/ oneiric/main libept1 i386 1.0.5build1 [134 kB]
Get:2 http://lk.archive.ubuntu.com/ubuntu/ oneiric/universe synaptic i386 0.75.2ubuntu8 [2,150 kB]
Fetched 2,284 kB in 1min 30s (25.2 kB/s)                                                                 
Selecting previously deselected package libept1.
(Reading database ... 141017 files and directories currently installed.)
Unpacking libept1 (from .../libept1_1.0.5build1_i386.deb) ...
Selecting previously deselected package synaptic.
Unpacking synaptic (from .../synaptic_0.75.2ubuntu8_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Setting up libept1 (1.0.5build1) ...
Setting up synaptic (0.75.2ubuntu8) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
kshitij@DeviBhawan-HomeComp:~$ 

```Also, the following was the output of the config dump:

```
kshitij@DeviBhawan-HomeComp:~$ apt-config dump
APT "";
APT::Architecture "i386";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "1";
APT::Install-Suggests "0";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^firmware-linux.*";
APT::NeverAutoRemove:: "^linux-firmware$";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^kfreebsd-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::NeverAutoRemove:: "^gnumach$";
APT::NeverAutoRemove:: "^gnumach-image.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT::Never-MarkAuto-Sections:: "oldlibs";
APT::Never-MarkAuto-Sections:: "restricted/oldlibs";
APT::Never-MarkAuto-Sections:: "universe/oldlibs";
APT::Never-MarkAuto-Sections:: "multiverse/oldlibs";
APT::Periodic "";
APT::Periodic::Update-Package-Lists "2";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Update "";
APT::Update::Post-Invoke-Success "";
APT::Update::Post-Invoke-Success:: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Update::Post-Invoke-Success:: "[ ! -f /var/run/dbus/system_bus_socket ] || /usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged || true";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
APT::Changelogs "";
APT::Changelogs::Server "http://changelogs.ubuntu.com/changelogs";
APT::Architectures "";
APT::Architectures:: "i386";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::extended_states "extended_states";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache::pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::netrc "auth.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Etc::preferencesparts "preferences.d";
Dir::Etc::trusted "trusted.gpg";
Dir::Etc::trustedparts "trusted.gpg.d";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::solvers "";
Dir::Bin::solvers:: "/usr/lib/apt/solvers";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Media "";
```I'm afraid this is a bit above my head (expected output vs actual), so, if you see any problems with any of the outputs, please let me know how to correct them!

Again, Thanks a bunch for your help,

Warmest Regards,

kshitij

---

### Post by matt_symes on 2011-10-26
Hi

I think we are almost there then. 

You can install packages - apart from the two we have had problems with. 
You can update correctly and can use software center and synaptic.

I think the last think we may need to do is to clean all your caches for apt and dpkg as that seems to be where the problem is.

Open a terminal and type these commands
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg --clear-avail
```

Then type

```
sudo apt-get update
```

Hopefully that will remove the problem.

Kind regards

---

### Post by kilosierra on 2011-10-27
Hi,

We're still stuck I'm afraid :(

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get clean
``````
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
``````
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.3ubuntu4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2011-10-27 10:44:12--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-27 10:45:12--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2011-10-27 10:46:12--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2011-10-27 10:47:12--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 32.1.6.56, 2001:638:d:c101:acdc:1979:2:1001
Connecting to dfn.dl.sourceforge.net|32.1.6.56|:80... failed: Connection timed out.
Connecting to dfn.dl.sourceforge.net|2001:638:d:c101:acdc:1979:2:1001|:80... failed: Network is unreachable.
--2011-10-27 10:48:12--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2011-10-27 10:49:12--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 32.1.2.0, 2001:200:141:feed::feed
Connecting to jaist.dl.sourceforge.net|32.1.2.0|:80... failed: Connection timed out.
Connecting to jaist.dl.sourceforge.net|2001:200:141:feed::feed|:80... failed: Network is unreachable.
--2011-10-27 10:50:12--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... 
```
I cant understand why this bugger wants to always connect to 1.0.0.0 for downloads!

So are we back to square one? Or is there hope still?

Thanks & Regards,

kshitij

---

### Post by matt_symes on 2011-10-27
Hi

What nameserver are you using ?

```
cat /etc/resolve.conf
```You are getting different ns resolution than i am.
```

matthew@matthew-Aspire-7540:~$ nslookup switch.dl.sourceforge.net
Server:         8.8.8.8
Address:        8.8.8.8#53

Non-authoritative answer:
Name:   switch.dl.sourceforge.net
Address: 130.59.138.21

matthew@matthew-Aspire-7540:~$
```You are getting [FONT=monospace]
[/FONT]> [FONT=monospace]
[/FONT]Resolving switch.dl.sourceforge.net... **32.1.6.32**, 2001:620:0:1b::21When i try to a reverse lookup on 32.1.6.32 i get

```
matthew@matthew-Aspire-7540:~$ nslookup 32.1.6.32
Server:         8.8.8.8
Address:        8.8.8.8#53

** server can't find 32.6.1.32.in-addr.arpa.: NXDOMAIN

matthew@matthew-Aspire-7540:~$ 
```This may explain your timeout. Can you ping 32.1.6.32 ?

```
ping -c3 32.1.6.32
```

I am behind a firewall that will not currently let me ping out and check if i can see it.

Change your name server (i am using Googles 8.8.8.8 ) in your /etc/resolv.conf file or in network manager and clear any dns cache you may have.

The run the commands again.

Kind regards

---

### Post by kilosierra on 2011-10-30
Hi,

Sorry for the delay, was traveling.

The problem seems to lie wit name server. It was set to 192.168.1.1. My ISP has dynamic IP and auto-ip assign, which I have now changed to address only and manually appended the DNS to google's 8.8.8.8.

Now, I ran the last commands you suggested, clean, autoclean and auto remove followed by dpkg -clear --avail and update. The result was:

```
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get clean
[sudo] password for kshitij: 
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kshitij@DeviBhawan-HomeComp:~$ sudo dpkg --clear-avail
kshitij@DeviBhawan-HomeComp:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease                      
Ign http://lk.archive.ubuntu.com oneiric InRelease                  
Ign http://lk.archive.ubuntu.com oneiric-updates InRelease
Ign http://lk.archive.ubuntu.com oneiric-backports InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Hit http://lk.archive.ubuntu.com oneiric Release.gpg                          
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://extras.ubuntu.com oneiric Release   
Hit http://lk.archive.ubuntu.com oneiric-updates Release.gpg          
Hit http://security.ubuntu.com oneiric-security Release               
Hit http://lk.archive.ubuntu.com oneiric-backports Release.gpg        
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://security.ubuntu.com oneiric-security/main Sources
Hit http://lk.archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates Release
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-backports Release           
Hit http://lk.archive.ubuntu.com oneiric/main Sources                          
Hit http://lk.archive.ubuntu.com oneiric/restricted Sources          
Hit http://lk.archive.ubuntu.com oneiric/universe Sources            
Hit http://lk.archive.ubuntu.com oneiric/multiverse Sources          
Hit http://lk.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://lk.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://lk.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://lk.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://lk.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://lk.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://lk.archive.ubuntu.com oneiric-updates/main Sources        
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted Sources  
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-backports/main Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://lk.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://lk.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://lk.archive.ubuntu.com oneiric/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric/universe Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://lk.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Fetched 72 B in 5s (14 B/s)
Reading package lists... Done

```Is the problem solved do you think? How do we test that its still not connecting to bogus IP addresses when trying to download updates?

Thanks a bunch mate,
Warm Regards,
Kshitij

---

### Post by matt_symes on 2011-10-31
Hi

That's looking better.

Just keep on installing things and if they fail then post back.

Kind regards

---

### Post by kilosierra on 2011-11-07
Hi Matt,

Everything looks sweet this end mate! Thanks a ton for your help!

Regards,

Kshitij

---

