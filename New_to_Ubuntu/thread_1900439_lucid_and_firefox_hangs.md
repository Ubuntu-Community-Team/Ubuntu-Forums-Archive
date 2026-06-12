---
title: "lucid and firefox hangs"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by Ed W. on 2011-12-26
Have OS 10.04.3 LTS and Firefox 3.6.24 and the browser hangs once or twice and hour.  Rebooting will bring me back to the same website and unfreeze the browser.  Nothing else I've tried seems to unfreeze it.  Created xkill shorcut and it didn't solve the issue.  Neither did trying Ctrl + Alt + F1 or Ctrl + Alt + F2.  I really don't have a  clue.  Any help would be greatly appreciated.  Couldn't find this using the search function either.
Thanks for any help.

---

### Post by BC59 on 2011-12-26
Try installing a newer Firefox version

```
gksu add-apt-repository ppa:mozillateam/firefox-stable
```
```
gksu apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by mikodo on 2011-12-26
> **BC59 said:**
> Try installing a newer Firefox version

```
gksu add-apt-repository ppa:mozillateam/firefox-stable
``````
gksu apt-get update
``````
sudo apt-get upgrade
```

Why do you use **gksu **apt-get update, and then **sudo** apt-get upgrade?

I always have been shown to use 

```
sudo apt-get update && sudo apt-get upgrade
```

Basically, does it not matter which one uses?

---

### Post by 2F4U on 2011-12-26
My understanding is that gksu is for GUI programs started out of a terminal. For terminal applications, just using sudo is perfectly fine.

---

### Post by BC59 on 2011-12-26
According to Ubuntu documentation:
> You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).

---

### Post by Ed W. on 2011-12-27
Thanks BC59, that seems to have solved my problem.  Thank you very much.  It's very nice of you to take the time to help out the noobs.  Without people like you the world would be a much harder place.

---

### Post by Zill on 2011-12-27
> **Ed W. said:**
> Thanks BC59, that seems to have solved my problem...
I am pleased that you have now "solved the problem".  However, I am concerned that, by simply upgrading Firefox, the original problem *seems* to have gone away.

Some problems with Firefox (and possibly other browsers) *may* be caused by user-installed add-ons or extensions.  These *can* cause very strange symptoms, including freezing or crashing the browser.  If your problems re-occur, I suggest the first thing to do is to disable all the add-ons/extensions and see if things improve.  If so then just gradually re-enable them one-by-one to establish the guilty party!

See [Firefox Help]("http://support.mozilla.com/en-US/kb/Firefox%20hangs") for more details.

Regarding Firefox 3.6.24 this remains the "default" version for Ubuntu Lucid 10.04.3 LTS.  As I use a similar configuration myself on a daily basis I can confirm that I have had no problems at all with Firefox 3.6.24.

---

### Post by Zill on 2011-12-27
> **BC59 said:**
> According to Ubuntu documentation:
"You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs..."
Apt (and associated commands) is a *terminal* (CLI) application and, as such should be prefixed with sudo, not gksudo or gksu.

Of course, if a GUI package manager, such as Synaptic, is used then this should be started with the gksudo prefix.

---

