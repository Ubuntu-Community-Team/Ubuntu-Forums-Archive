---
title: "Unable to download flash plugin-installer"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by ankita indeed on 2013-04-13
Hi,
I have been regularly updating my update information ever since I started using ubuntu-12.04 but I have regularly been facing problems with downloading the flash plugin and now I am not able to play videos directly from the youtube site.The youtube page says that I need to install additional plugins and upgrade my flash player version.
I have tried removing and re-installing the flash-player but that is not working.Please help.

---

### Post by rrich1974 on 2013-04-13
try to install "ubuntu-restricted-extras" and the flash will be installed automatically for you. you will have the 11.2.xxx version. 

but my take will be to install "google-chrome" (not chromium) and you will have the latest flash (11.7.xxx) embeded in browser. 
no need to say that chrome is the best browser in the known universe.

---

### Post by ankita indeed on 2013-04-13
Thanks it works now :D

---

### Post by claracc on 2013-04-13
> **rrich1974 said:**
> 
no need to say that chrome is the best browser in the known universe.

I disagree, I think it is firefox

---

### Post by rrich1974 on 2013-04-13
no, no.....chrome is the best.

---

### Post by ankita indeed on 2014-02-07
Hi,
As adviced in previous posts in the stream I downloaded all the restricted downloads and the flash-plug-in was fine for some days but now again in the updating of the system the flash plug-in updates are not getting downloaded.This is the message the update manager generally displays.


Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.


If I try to run the action at that point in time the terminal opens and requests authentication and this is all that happens in the terminal and then later the same message gets displayed when I connect to the internet again.


flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.336.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.336.orig.tar.gz)

---

### Post by Gnusboy on 2014-02-08
Hey ya'll
I have the same problem. The flash plugin installer was d/l with the regular new updates, but won't install. This is the message:

[B]Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.[/B]

I got the message to authenticate as a super user, put in my password an a terminal opened, hit enter, but nothing happened. It just stayed there. Tried enter a couple more times, but it only added a blank line.

I just now d/l the package from the link above here and tried again to install it. However, as the dummy of the week, for 162 weeks running, I still have never learned how to unpack a tarball.
I tried a few times back when, but couldn't get it. I just looked it up in the "installing software" documentation, which was interesting, but complex.

 Is that the only way to handle the Flash package install? It seems to me that as often as Flash gets updated, that there must be an easier way. Any ideas?

Thanks.






flashplugin-installer: downloading  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.336.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.336.orig.tar.gz)

---

### Post by Gnusboy on 2014-02-08
rrich1974

RE: "ubuntu-restricted-extras" comment,
Where do I look for this package and does it need to be installed via the terminal?

Thanks.

---

### Post by Vladlenin5000 on 2014-02-08
> **Gnusboy said:**
> rrich1974

RE: "ubuntu-restricted-extras" comment,
Where do I look for this package and does it need to be installed via the terminal?

Thanks.


You can install it from the Software Center as well.

---

### Post by Gnusboy on 2014-02-09
Vladlenin5000

I downloaded the  "ubuntu-restricted-extras" from the Software Center  which also included the Adobe Flash plugin (flashplugin-instaler)
and the Fluendo MP3 decoder package.

I ran the primary restricted install. I was AFK for a while and when I looked again I got the same message as before:
[B]Failure to download extra data files
The following packages requested additional data downloads after package   installation, but the data could not be downloaded or could not be   processed.
flashplugin-installer

The download will be attempted again later, or you can try the download again now.
[/B]I didn't run it again yet. So, my question is - did Flash not  install as part of the package and I can go back and get the original  tarball to run under the installed restricted program?
Or did it not install everything in the package?

Do I need to delete the program and start over?
I am befuddled again.

---

### Post by monkeybrain20122 on 2014-02-09
Try install instead adobe-flashplugin from the repository. Sometimes when people have problem with downloading one the other appears to work, I never know why there are two packages for the same thing.

---

### Post by Gnusboy on 2014-02-09
To everyone who helped Thank you.
I think I've fixed the problem. Despite the failure messages, the Firefox troubleshooter data shows that I have the newest Flash.[h=2]Shockwave Flash[/h]File: libflashplayer.soPath: /usr/lib/flashplugin-installer/libflashplayer.soVersion: 11,2,202,336State: EnabledShockwave Flash 11.2 r202

---

