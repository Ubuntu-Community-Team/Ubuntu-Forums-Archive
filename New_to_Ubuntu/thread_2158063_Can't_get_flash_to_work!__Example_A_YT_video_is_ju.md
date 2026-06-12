---
title: "Can't get flash to work!  Example: A YT video is just Blank."
date: 2013-06-27
forum: New to Ubuntu
---

### Post by Paradoxicated on 2013-06-27
Hello Everyone, I'm new here.

I recently got a computer (HP Pavilion a610e; pre-installed with Linux) from someone, and it has Ubuntu 12.04 on it.  It seems factory-reset, which is good, but no flash on it.  First time using Linux at all, and after doing all sorts of things I still can't get flash to work.

Please help!
 - Paradoxicated

---

### Post by ajgreeny on 2013-06-27
Start by using command ```
sudo apt-get install ubuntu-restricted-extras
``` which will install flash as well as several other restricted codecs needed for such as mp3 playback etc etc.

---

### Post by Paradoxicated on 2013-06-27
I went into terminal and used that command: "

sudo apt-get install ubuntu-restricted-extras
"
And when it finished I closed terminal and closed firefox, reopened firefox and it still has the same result.  A youtube video is just a big white rectangle. (Blank, basically)

---

### Post by Autodave on 2013-06-27
> **Paradoxicated said:**
> Hello Everyone, I'm new here.

I recently got a computer (HP Pavilion a610e; pre-installed with Linux) from someone, and it has Ubuntu 12.04 on it.  It seems factory-reset, which is good, but no flash on it.  First time using Linux at all, and after doing all sorts of things I still can't get flash to work.

Please help!
 - Paradoxicated


[http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube](http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube)

 Go there and do as it says.  Do not install the getdeb repository since it is closed: at least the last time I checked.

---

### Post by Paradoxicated on 2013-06-27
> **Autodave said:**
> [http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube](http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube)

 Go there and do as it says.  Do not install the getdeb repository since it is closed: at least the last time I checked.

Do I even have to do the WinFF thing?  All I want is flash.

---

### Post by Vormeph on 2013-06-27
Unfortunately, flash has been discontinued for development on Linux for unknown reasons. Installing the <*buntu> restricted extras package will allow you to use flash. Make sure you have it enabled under 'Plugins' when you access your addons through Tools >> Addons. I am aware that installing Google Chrome would solve the problem since the browser uses pepper flash which simply gives you flash for use on YouTube.

---

### Post by Paradoxicated on 2013-06-27
I actually have google chrome, and I'd prefer to use it but it crashes.  I'll make another thread regarding that issue.

Thannks for the help, everyone.  I will update if it works or not once I do what Vormeph said

---

### Post by Paradoxicated on 2013-06-27
I went into firefox, went to Tools -> Plugins.  The only thing there is "Shockwave Flash 11,2,202,291" and is not disabled.  I tried a youtube video but it still is blank.

---

### Post by Paradoxicated on 2013-06-27
(sorry for triple-post)

As of now, I am using Google Chrome (successfully).  Now, flash things aren't blank.  They're grey and have the puzzle piece icon.  When I roll over the flash thing (A YT video, for example) it shows text under the puzzle piece icon: "Couldn't load Plug-in".

---

### Post by Vormeph on 2013-06-27
I just realised you were using Xubuntu. I thought you used Ubuntu, in which case ubuntu-restricted-extras would be your prime goal. You need to completely remove ubuntu-restricted-extras and install the xubuntu-restricted-extras instead. Your problem should then be solved.

---

### Post by ajgreeny on 2013-06-28
> **Vormeph said:**
> I just realised you were using Xubuntu. I thought you used Ubuntu, in which case ubuntu-restricted-extras would be your prime goal. You need to completely remove ubuntu-restricted-extras and install the xubuntu-restricted-extras instead. Your problem should then be solved.

I do not think that will make a scrap of difference, I'm afraid.  The dependencies of both packages are just about identical for ubuntu* and xubuntu* packages, and in fact on my Xubuntu 12.04 I have both installed with no problem.

Can we assume you do not have another add-on that is stopping flash from working, eg** flash-block** or **no-script**?

---

### Post by Paradoxicated on 2013-06-28
How do I remove ubuntu-restricted-extras?

---

### Post by Paradoxicated on 2013-06-28
I'm running google chrome now.  I also have chromium if I should use that.

Flash doesn't work.  What to do?

---

### Post by Vormeph on 2013-07-01
Install synaptic package manager, and search for the relevant packages there. Ubuntu/xubuntu restricted extras should be listed.

---

### Post by smd0665 on 2013-07-06
Bump. I'm having the same problem with Lubuntu here. I had to re-install the OS and I followed the Pepper Flash installation described here: [https://launchpad.net/~skunk/+archive/pepper-flash](https://launchpad.net/~skunk/+archive/pepper-flash)
In chrome://plugins, the Pepper Flash plugin is listed as version 11.8.800.96, however, when I try to do anything flash-related, it says "Could not load Shockwave Flash." The plugin location is listed as /usr/lib/pepflashplugin-installer/libpepflashplayer.so, however, there is no libpepflashplayer.so in that folder, only the files install_plugin and pepflashplayer.sh. I do have lubuntu-restricted-extras installed. Does anyone have any idea what might be happening here?

---

### Post by smd0665 on 2013-07-06
I've discovered a workaround using the procedure found here: [https://bbs.archlinux.org/viewtopic.php?pid=1127489](https://bbs.archlinux.org/viewtopic.php?pid=1127489)
Instead of the .rpm file, I downloaded the .deb file, extracted it and copied libpepflashplayer.so from the extracted folder /Downloads/opt/google/chrome/PepperFlash to /usr/lib/pepflashplugin-installer, where it's supposed to be on my system. It works for now.

---

