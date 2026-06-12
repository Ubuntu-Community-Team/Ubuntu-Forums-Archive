---
title: "[SOLVED] Audacious problem"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Norfeldt on 2008-11-19
Hey All

When I open mp3 files with Audacious it just open and import it in the playlist but doesn't play it. Not even if I press the play button.
I tried to uninstall it in synaptic and install it again in Add/Remove.. but still the same... what to do?

---

### Post by starcannon on 2008-11-19
Try this:
```
sudo apt-get install lame
```

after that completes installation, try playing an mp3 in audacious again, it should go ahead and work if your sound settings in audacious preferences are set up correctly.

---

### Post by Norfeldt on 2008-11-19
didn't help
[PHP]norfeldt@norfeldt-laptop:~$ audacious 
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:18496): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:18496): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:18496): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:18496): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed
[/PHP]

---

### Post by starcannon on 2008-11-19
Googled your error message and came up with a solved post, try this out:
[http://ubuntuforums.org/showthread.php?p=4723700](http://ubuntuforums.org/showthread.php?p=4723700)

GL let us know if it worked, if not we'll find another way.

---

### Post by Norfeldt on 2008-11-20
> **starcannon said:**
> Googled your error message and came up with a solved post, try this out:
[http://ubuntuforums.org/showthread.php?p=4723700](http://ubuntuforums.org/showthread.php?p=4723700)

GL let us know if it worked, if not we'll find another way.

Thanks for the help. Didn't think about googleing the error..
I came as fare as this
[PHP]norfeldt@norfeldt-laptop:~$ apt-get remove audacious
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
norfeldt@norfeldt-laptop:~$ sudo apt-get remove audacious
[sudo] password for norfeldt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libartsc0 libgconf2-ruby libaudclient1 kdelibs-data libatk1-ruby1.8
  openoffice.org-hyphenation-en-us liblualib50 libflac++6 libcddb2
  libservlet2.4-java ruby1.8 bsh libjaxp1.3-java libgconf2-ruby1.8
  libaudid3tag1 libjline-java libxerces2-java libuser1 libglib2-ruby1.8
  libcairo-ruby1.8 libmowgli1 libxalan2-java libgdk-pixbuf2-ruby1.8
  libgtk2-ruby1.8 libhsqldb-java libemeraldengine0 libmcs1 liblua50 libruby1.8
  libpango1-ruby1.8 libneon27-gnutls
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  audacious audacious-plugins
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4825kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146997 files and directories currently installed.)
Removing audacious ...
Removing audacious-plugins ...
norfeldt@norfeldt-laptop:~$ rm -r .a
.acetoneiso/           .audacity1.3-norfeldt/ 
.adobe/                .audacity-data/        
norfeldt@norfeldt-laptop:~$ rm -r .a
[/PHP]

But Im in doubt about finding the .audacious/ as adyhasch said
> [PHP]adyhasch@jenna:~$ rm -r .audacious/ /home/adyhasch/.config/audacious /home/adyhasch/.cache/audacious home/adyhasch/.local/share/audacious /home/adyhasch/.local/share/applications/audacious-usercustom-usercustom-1.desktop[/PHP]

PS. Should I use the 'apt-get autoremove'?

---

### Post by mikewhatever on 2008-11-20
You need to use sudo with these commands, that is <sudo apt-get remove audacious>, etc.

---

### Post by Norfeldt on 2008-11-20
okay I did this
[PHP]locate audacious[/PHP]
and removed all the files..
Installed it again and now it's :guitar:

Thanks for the help

---

### Post by Norfeldt on 2008-11-20
> **mikewhatever said:**
> You need to use sudo with these commands, that is <sudo apt-get remove audacious>, etc.

I did
[QUOTE=Norfeldt]```
norfeldt@norfeldt-laptop:~$ apt-get remove audacious
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
norfeldt@norfeldt-laptop:~$ sudo apt-get remove audacious
```[/QUOTE]

---

### Post by Norfeldt on 2008-11-26
Okay... Now it's beginning to do it again... I can't uninstall and remove all the files every time it does this..
How do I find out the name of the bug and report it?
Or do anyone have a solution?

---

### Post by vbhavsar on 2008-12-18
Try this:
In Audacious Preferences, change the output plugin to ALSA Output Plugin. Worked for me.

---

### Post by Norfeldt on 2008-12-26
hmm... didn't try it..  it's not making any troubles now..
Ill try it if it begins again..

---

