---
title: "How to Install Firefox-20"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by swarup on 2013-04-08
I am using Ubuntu 9.04 (I know it is old, but I love it!), and want to update my firefox. It is currently running Firefox 3.6.11 and many web pages complain that "your browser is old". So I downloaded 
firefox-20.0.tar.bz2 and as per [these instructions]("http://www.libre-software.net/how-to-install-firefox-on-ubuntu-linux-mint") installed it. Here is what they instruct to do:

> If you already had a previous Firefox version installed in the /opt directory, remove it with the following command:
sudo rm -r /opt/firefox

Now move the firefox directory (which was created in your Downloads folder during extraction) to /opt:
sudo mv firefox /opt/firefox20

If you want to use Firefox 20 as your default browser:

&#8220;Backup&#8221; the old Firefox launcher:
sudo mv /usr/bin/firefox /usr/bin/firefox-old

Create a symbolic link pointing to the new Firefox version:
sudo ln -s /opt/firefox20/firefox /usr/bin/firefox

No need to update your icons/shortcuts, they should now launch the new version of Firefox.

Your old Firefox version is still installed. If you want to use it, run firefox-old in a terminal or create shortcuts/icons referring to firefox-old.

I did exactly what it said to do. Actually there my current Firefox was not installed in the /opt directory, so I just placed the new one there and then did as it says in these instructions. But after so doing, the Firefox installer in my applications -> internet, would not open *any* Firefox. So I had to revert to the old one by doing 

```
sudo mv /usr/bin/firefox-old /usr/bin/firefox  
```

Now the old one is again working fine. But how do I make the new one i.e. Firefox-20 active as my current browser?

---

### Post by jeSah8ci on 2013-04-08
From what I understand, you're manually uncompressing and replacing. But, have you tried to check if it has unmet dependencies? Maybe Synaptic Package Manager can help you there!

---

### Post by jeSah8ci on 2013-04-08
Also, have you tried running Firefox 20 from the un-tarballed folder? E.g:

```
rolandog@rolandog-HP-Notebook:~/Downloads/firefox$ ./firefox
```

---

### Post by cortman on 2013-04-08
> **rolandog said:**
> From what I understand, you're manually uncompressing and replacing. But, have you tried to check if it has unmet dependencies? Maybe Synaptic Package Manager can help you there!

If not unmet dependencies, it may be depending on later versions of different libraries.
@OP, it's your choice, but 9.04 is prett outdated :) If your holdup is that you like gnome2, you can use a distro that uses gnome2 (Debian squeeze, CentOS, Scientific Linux) or you could try X|Lubuntu.

---

### Post by Dennis N on 2013-04-08
You can check that the new version works by navigating to the /opt/firefox20 directory and double clicking on firefox (not firefox-bin). It should start up.

The instructions given look good to me. You may have made an error. When following them, check that everything is typed correctly, and all paths are correct. Be sure firefox is not capitalized in the file or directory names.

Alternately, you can edit the main menu firefox launcher (or even create a new launcher) so that the path in the command box is to the new version. If you also have a panel launcher, you would need to fix that too.

---

### Post by swarup on 2013-04-08
Dennis, I went into the firefox20 directory you pointed me to, and clicked on firefox. It did not open. Now, my old Firefox 3.6.11 is already open; I do not know whether that would have prevented the new one from opening. But if that was not a factor, and if your technique of starting up the new firefox20 is correct, then firefox20 is nor working in Ubuntu 9.04. And if course, 9.04 is no longer supported by Ubuntu so there are no repositories for downloading anything such as dependencies. rolandog mentioned about using Synaptic Package manager for fulfilling dependencies. Can this be done in a distro which is not longer supported i.e. does not have repositories? Does it sound like firefox20 will be able to run in Ubuntu 9.04?

(Upgrading to a later version of Ubuntu is in my plans, although not just this minute. That is another issue. For now, I was hoping to just get a newer browser running.)

---

### Post by mamamia88 on 2013-04-08
Extract it to somewhere and create a launcher that points to the file firefox-bin.   Just make sure you have the prerequisites listed here [http://www.mozilla.org/en-US/firefox/20.0/system-requirements/](http://www.mozilla.org/en-US/firefox/20.0/system-requirements/) which you should since firefox comes with ubuntu by default anyway.   It's really quite simple

---

### Post by swarup on 2013-04-08
Hi mamamia88-- I extracted it to the desktop and created a launcher pointing to the file you mentioned. By clicking on the launcher, firefox20 does not open. Perhaps it is the dependencies? I went to the website you mentioned and saw the dependencies, but really do not know how to check whether I have them or not in my system.

---

### Post by mamamia88 on 2013-04-08
Open synaptic and search for them. It will tell you what version you have.  Just tried it myself everything but xorg you have to put lib in front of when searching in synaptic.  For example pango is libpango

---

### Post by snowpine on 2013-04-08
When you (try to) run it from the command line as rolandog suggested in post #3, you will get error messages that may be useful in troubleshooting the problem.

---

### Post by swarup on 2013-04-08
Snowpine, here is the output when I run it from the terminal window as directed in post#3. Does this give us useful info for solving the matter?

```
swarup@swarup-laptop:~$ cd /home/swarup/Desktop/firefox 
swarup@swarup-laptop:~/Desktop/firefox$ ./firefox
XPCOMGlueLoad error for file /home/swarup/Desktop/firefox/libxpcom.so:
libxul.so: cannot open shared object file: No such file or directory
Couldn't load XPCOM.
swarup@swarup-laptop:~/Desktop/firefox$ 
```

---

### Post by snowpine on 2013-04-08
I googled the error messages and found some bugs on the Mozilla site such as: [https://bugzilla.mozilla.org/show_bug.cgi?id=723487](https://bugzilla.mozilla.org/show_bug.cgi?id=723487)

You will have to do the research from there, as I am unable to support you with an end-of-life release.

---

### Post by Dennis N on 2013-04-08
If you are unable to get **Firefox 20** to work because of some unmet requirement, you can certainly get a newer version than 3.6.11. I still have Ubuntu 8.04 installed on one partition of a computer (for historical reference and research purposes), and it is using **Firefox 16.02** with no problem, so that version at least should work since you have Ubuntu 9.04.  I haven't tried anything more recent than that, and I don't get any warnings about that version being considered too old.

My method was to just extract and put the firefox folder from the downloaded archive into my home folder, and modify the launchers for that location. I like the general method in your first post, however as is more elegant.

---

### Post by Victor43 on 2013-04-16
Hello 

Were you able to resolve your issue and getting FF-20 to install on Ubuntu 9.0.4 ? I have the exact same post here see below. However I cannot get it to work. Please either reply here or send me a PM.

Thanks

Victor

[http://ubuntuforums.org/showthread.php?t=2135776&p=12604693](http://ubuntuforums.org/showthread.php?t=2135776&p=12604693)

---

