---
title: "Weather applet quit working"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by Autodave on 2013-11-03
2 machines both running Xubuntu 12.04.  Both within the last week had the weather applet quit working.  Any ideas?

---

### Post by pqwoerituytrueiwoq on 2013-11-03
The applet it out of date, a update will fix it if it is compatible (as in pulling the [xfce4-weather-plugin](http://packages.ubuntu.com/saucy/xfce4-weather-plugin) package from saucy)
you may need to use xfce 4.10 for it to work
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

---

### Post by Autodave on 2013-11-03
> **pqwoerituytrueiwoq said:**
> The applet it out of date, a update will fix it if it is compatible (as in pulling the [xfce4-weather-plugin]("http://packages.ubuntu.com/saucy/xfce4-weather-plugin") package from saucy)
you may need to use xfce 4.10 for it to work
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

Package still installed, xfce4.8.3 installed.  No weather. :-(

---

### Post by pqwoerituytrueiwoq on 2013-11-03
run [FONT=courier new]xfce4-panel -r[/FONT]

---

### Post by Buntu Bunny on 2013-11-03
> **pqwoerituytrueiwoq said:**
> The applet it out of date, a update will fix it if it is compatible (as in pulling the [xfce4-weather-plugin](http://packages.ubuntu.com/saucy/xfce4-weather-plugin) package from saucy)
you may need to use xfce 4.10 for it to work
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

I have 4.10 installed and it's not working for me either.

---

### Post by pqwoerituytrueiwoq on 2013-11-03
it is working on saucy here
```
~$ apt-cache policy xfce4-weather-plugin 
xfce4-weather-plugin:
  Installed: 0.8.3-1
  Candidate: 0.8.3-1
  Version table:
 *** 0.8.3-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
```
after installing the version i linked above you will need to run the command i posted to apply the update
edit: you may need to reconfigure the applet, the config file changed at some point since 12.04 IIRC

---

### Post by Buntu Bunny on 2013-11-09
I really miss the Xfce weather plugin.

> **pqwoerituytrueiwoq said:**
> it is working on saucy here
```
~$ apt-cache policy xfce4-weather-plugin 
xfce4-weather-plugin:
  Installed: 0.8.3-1
  Candidate: 0.8.3-1
  Version table:
 *** 0.8.3-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
```
after installing the version i linked above you will need to run the command i posted to apply the update
edit: you may need to reconfigure the applet, the config file changed at some point since 12.04 IIRC

I fear this wouldn't work for 12.04(?)

Or, does anyone have an alternative desktop weather gadget they can recommend?

---

### Post by Buntu Bunny on 2013-11-09
It just started working! Just now. I clicked on properties to see if there was anything I could change, but there wasn't. Now it's working again. Huzzah!

---

### Post by BlinkinCat on 2013-11-09
> **Buntu Bunny said:**
> It just started working! Just now. I clicked on properties to see if there was anything I could change, but there wasn't. Now it's working again. Huzzah!

Great news Buntu Bunny - My plug in 0.8.3 works fine for me! - :p

---

### Post by Nouche on 2014-01-28
> **pqwoerituytrueiwoq said:**
> it is working on saucy here
```
~$ apt-cache policy xfce4-weather-plugin 
xfce4-weather-plugin:
  Installed: 0.8.3-1
  Candidate: 0.8.3-1
  Version table:
 *** 0.8.3-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
```
after installing the version i linked above you will need to run the command i posted to apply the update
edit: you may need to reconfigure the applet, the config file changed at some point since 12.04 IIRCThank you! I did not need anything else after "~$ apt-cache policy xfce4-weather-plugin" in Xubuntu 12.04 LTS.

---

### Post by Buntu Bunny on 2014-01-28
> **Nouche said:**
> Thank you! I did not need anything else after "~$ apt-cache policy xfce4-weather-plugin" in Xubuntu 12.04 LTS.

I tried this too. Input:

```

$  apt-cache policy xfce4-weather-plugin 
```

Output:

```
Installed: 0.8.3-1~precise~ppa2
  Candidate: 0.8.3-1~precise~ppa2
  Version table:
 *** 0.8.3-1~precise~ppa2 0
        500 http://ppa.launchpad.net/landronimirc/xfce/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     0.8.3-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main amd64 Packages
     0.7.4-3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

But it still doesn't work! :frown:

I even rebooted in hopes it would. 

Funny how used to the little things we become. I love this applet but it has been a bit of a bother lately.

---

### Post by robin7 on 2014-01-28
Here's what I did:

```
sudo add-apt-repository ppa:dtl131/mediahacks
sudo apt-get update
sudo apt-get install xfce4-weather-plugin
sudo add-apt-repository –remove ppa:dtl131/mediahacks
```

Enter password when prompted.  This was for Xubuntu 12.04, since the weather applet in Xfce 4.8 is no longer supported by the third party that was running it.   This works, but it unexpectedly "leaves the panel" sometimes when the screensaver activates so it isn't foolproof.

[http://adoptedsidekick.wordpress.com/2014/01/20/fixing-up-xubuntu-12-04-lts/](http://adoptedsidekick.wordpress.com/2014/01/20/fixing-up-xubuntu-12-04-lts/)

---

### Post by Buntu Bunny on 2014-01-29
> **robin7 said:**
> Here's what I did:

```
sudo add-apt-repository ppa:dtl131/mediahacks
sudo apt-get update
sudo apt-get install xfce4-weather-plugin
sudo add-apt-repository –remove ppa:dtl131/mediahacks
```

Enter password when prompted.  This was for Xubuntu 12.04, since the weather applet in Xfce 4.8 is no longer supported by the third party that was running it.   This works, but it unexpectedly "leaves the panel" sometimes when the screensaver activates so it isn't foolproof.

[http://adoptedsidekick.wordpress.com/2014/01/20/fixing-up-xubuntu-12-04-lts/](http://adoptedsidekick.wordpress.com/2014/01/20/fixing-up-xubuntu-12-04-lts/)

I have Xfce 4.10 installed on Ubuntu 12.04, so I don't suppose this would work for me, but I'm glad for the link.

---

### Post by robin7 on 2014-01-29
> **Buntu Bunny said:**
> I have Xfce 4.10 installed on Ubuntu 12.04.

I've read elsewhere that installing 4.10 on Precise causes some problems, though.  That's why I only installed the panel applet and nothing else from Xfce 4.10 on my Xubuntu Precise.  Is it working out for you pretty much trouble free?

---

### Post by Buntu Bunny on 2014-01-29
> **robin7 said:**
> I've read elsewhere that installing 4.10 on Precise causes some problems, though.  That's why I only installed the panel applet and nothing else from Xfce 4.10 on my Xubuntu Precise.  Is it working out for you pretty much trouble free?

For the most part, yes. Besides the weather applet, I have a occasional problems WhiskerMenu (which prompt updates from Gott Code always resolve), and with themes. I installed 4.10 after major problems with Thunar in 4.8 (that thread[ here]("http://ubuntuforums.org/showthread.php?t=2176186")). For my situation, that helped so much that the little things don't bother me. :)

I would also like to welcome you to the Ubuntu Forums, robin7!

---

### Post by Dennis N on 2014-01-29
Weather applet: FYI, Working correctly for me. Only differences I can see is mine is 32 bit - from post #11, yours is 64 bit system - and mine came from the other PPA (xubuntu-dev) . I also upgraded my 12.04 Xubuntu system to xfce-4.10 long ago.

```
dn@Kayleigh:~$ apt-cache policy xfce4-weather-plugin 
xfce4-weather-plugin:
  Installed: 0.8.3-0ubuntu1~ppa0.12.04.1
  Candidate: 0.8.3-0ubuntu1~ppa0.12.04.1
  Version table:
 *** 0.8.3-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     0.7.4-3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe i386
```

---

### Post by Bucky Ball on 2014-01-29
> **robin7 said:**
> Here's what I did:

```
sudo add-apt-repository ppa:dtl131/mediahacks
sudo apt-get update
sudo apt-get install xfce4-weather-plugin
sudo add-apt-repository –remove ppa:dtl131/mediahacks
```



I tried this a few days ago and it got me further. I can put a location in the properties window but as soon as I close that window the plugin crashes and quits. So doesn't work for me, Xubuntu 12.04.

---

### Post by Buntu Bunny on 2014-01-29
> **Dennis N said:**
> Weather applet: FYI, Working correctly for me. Only differences I can see is mine is 32 bit - from post #11, yours is 64 bit system - and mine came from the other PPA (xubuntu-dev) . I also upgraded my 12.04 Xubuntu system to xfce-4.10 long ago.

```
dn@Kayleigh:~$ apt-cache policy xfce4-weather-plugin 
xfce4-weather-plugin:
  Installed: 0.8.3-0ubuntu1~ppa0.12.04.1
  Candidate: 0.8.3-0ubuntu1~ppa0.12.04.1
  Version table:
 *** 0.8.3-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     0.7.4-3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe i386
```


Here's what I get

```
buntu_bunny@CM1740:~$ apt-cache policy xfce4-weather-plugin
xfce4-weather-plugin:
  Installed: 0.8.3-1~precise~ppa2
  Candidate: 0.8.3-1~precise~ppa2
  Version table:
 *** 0.8.3-1~precise~ppa2 0
        500 http://ppa.launchpad.net/landronimirc/xfce/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     0.8.3-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main amd64 Packages
     0.7.4-3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

I'm confused that there are 2 ppas listed in the output.

Seems like quite a few of us are still having problems with this.

UPDATE: I thought I'd start with a complete uninstall of the previous version via Synaptic. However, this wanted to uninstall Xfce goodies, which I don't think is what I want to do (?)

---

### Post by Elfy on 2014-01-29
[https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629](https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629)

SRU'd - the fix should be in -proposed, but you'd need to remove the PPA

[https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629/comments/29](https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629/comments/29)

---

### Post by robin7 on 2014-01-29
> **Buntu Bunny said:**
> 
UPDATE: I thought I'd start with a complete uninstall of the previous version via Synaptic. However, this wanted to uninstall Xfce goodies, which I don't think is what I want to do (?)

Xfce goodies includes all the nice little panel applets.  It doesn't take up much disk space, so why not?  It's listed as "dependency" so that might be the reason I had a little trouble with mine.  Go ahead and get the goodies!

> **Buntu Bunny said:**
> 
I would also like to welcome you to the Ubuntu Forums, robin7! 

Thanks!  I love this place!  So helpful, so much to learn from so many nice people!
:redface:

---

### Post by Buntu Bunny on 2014-01-29
> **Elfy said:**
> [https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629](https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629)

SRU'd - the fix should be in -proposed, but you'd need to remove the PPA

[https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629/comments/29](https://bugs.launchpad.net/ubuntu/+source/xfce4-weather-plugin/+bug/1244629/comments/29)

Elfy, thanks. Your help is greatly appreciated

Enabling precise-proposed in my repositories certainly updated quite a bit, except the weather applet. So, by removing the ppa I'm assuming you mean landronimirc?

UPDATE: Removed landronimirc ppa too, but no joy. 

> **robin7 said:**
> Xfce goodies includes all the nice little panel applets.  It doesn't take up much disk space, so why not?  It's listed as "dependency" so that might be the reason I had a little trouble with mine.  Go ahead and get the goodies!

Thanks!  I love this place!  So helpful, so much to learn from so many nice people!
:redface:

Well, I've already got the goodies (and hence the weather applet), but when I tried to uninstall the non-functioning applet I got the "will uninstall goodies" message, so I didn't. :P

I have to agree that this is one of the most helpful and friendly forums on the internet. Anything I need to know about Ubuntu (or Xubuntu) I will likely learn here.

---

### Post by Dennis N on 2014-01-29
> **Buntu Bunny said:**
> UPDATE: I thought I'd start with a complete uninstall of the previous version via Synaptic. However, this wanted to uninstall Xfce goodies, which I don't think is what I want to do (?)

xfce4-goodies is a metapackage, so when it gets uninstalled, none of the goodies will be removed other than the one you specifically uninstall.

As to the two ppas, personally I would have more trust in packages in the xubuntu-dev PPA.

---

### Post by Bucky Ball on 2014-01-29
There is a fix committed and should be in a 12.04 update soon as it is just going into the 'proposed' repo. See top of bug report:

[https://bugs.launchpad.net/ubuntu/precise/+source/xfce4-weather-plugin/+bug/1244629](https://bugs.launchpad.net/ubuntu/precise/+source/xfce4-weather-plugin/+bug/1244629)

The advice at the bottom of that thread is to add the proposed repo. This is not a good idea for the average user. Better to wait til the fix makes the updates if that is you. 

You can add the app from the proposed repo 'selectively' by following the instructions here if you just can't wait:

[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

Be careful or you will wind up with a bunch of testing updates and possibly much breakage!

---

### Post by Dennis N on 2014-01-29
> **Bucky Ball said:**
> There is a fix committed and should be in a 12.04 update soon as it is just going into the 'proposed' repo. 

Is there a reason not to continue using the one in the xubuntu-dev PPA, version 0.8.3-0ubuntu1~ppa0.12.04.1, since it seems to work correctly, as far as I can tell. The bug report seems to be about version 0.7.4-3.

---

### Post by Bucky Ball on 2014-01-29
> **Dennis N said:**
> Is there a reason not to continue using the one in the xubuntu-dev PPA, version 0.8.3-0ubuntu1~ppa0.12.04.1, since it seems to work correctly, as far as I can tell. The bug report seems to be about version 0.7.4-3.

Nope. No reason at all. The fix puts a functioning version back in the regular 12.04 kernel, though, which is all many want (particulary newcomers who know nothing about adding PPAs and shouldn't need to for a functioning system). ;)

---

### Post by Dennis N on 2014-01-29
Understood. I will leave it as is. Thanks.

---

### Post by Buntu Bunny on 2014-02-19
It's working again! What a relief. Funny how attached one becomes to the little things in life. This wasn't my thread but thanks to everyone for the help.

---

