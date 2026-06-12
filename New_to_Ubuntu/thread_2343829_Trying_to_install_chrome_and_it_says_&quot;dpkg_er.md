---
title: "Trying to install chrome and it says &quot;dpkg: error: need an action option&quot;"
date: 2016-11-19
forum: New to Ubuntu
---

### Post by juntjoo2 on 2016-11-19
I have no idea what I'm doing. I'm just following instructions from 

[http://howtogeek.com/203768/beginner-how-to-install-google-chrome-in-ubuntu-14.04]("http://howtogeek.com/203768/beginner-how-to-install-google-chrome-in-ubuntu-14.04")

Thanks

---

### Post by slickymaster on 2016-11-19
Can you please copy/paste into the thread the exact command you used, using code tags for the effect.

---

### Post by juntjoo2 on 2016-11-19
sudo dpkg –I google-chrome-stable_current_amd64.deb

Not sure what you mean by code tags

Thanks

I just copied the command from the site and pasted it directly

---

### Post by slickymaster on 2016-11-19
> **juntjoo2 said:**
> sudo dpkg [COLOR=#FF0000]**&#8211;**[/COLOR]I google-chrome-stable_current_amd64.deb
That's your culprit right there. The command you copied from the website contains non-ASCII characters. That dash in front of the i is not a hyphen (or minus), but an en-dash. Try using```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

---

### Post by slickymaster on 2016-11-19
> **juntjoo2 said:**
> ----

Not sure what you mean by code tags

Please, have a read at this post: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by juntjoo2 on 2016-11-19
thanks a lot. it worked but then this. any idea what it means?

```
[sudo] password for ben: 
Selecting previously unselected package google-chrome-stable.
(Reading database ... 173964 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (54.0.2840.100-1) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libappindicator1; however:
  Package libappindicator1 is not installed.

dpkg: error processing package google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160701-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 google-chrome-stable
```

---

### Post by slickymaster on 2016-11-19
Please run in a terminal window```
sudo apt-get install -f
```This will install missing dependencies and configure Google Chrome.

---

### Post by juntjoo2 on 2016-11-19
> **slickymaster said:**
> Please run in a terminal window```
sudo apt-get install -f
```This will install missing dependencies and configure Google Chrome.

thanks. I don't know what happened but it looked better than last time.

...yup, it installed.  Thank you!

---

### Post by slickymaster on 2016-11-19
> **juntjoo2 said:**
> thanks. I don't know what happened but it looked better than last time.

...yup, it installed.  Thank you!

Glad you got it working.

Now, please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution for the problem.

---

