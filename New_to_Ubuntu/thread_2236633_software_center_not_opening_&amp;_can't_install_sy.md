---
title: "software center not opening &amp; can't install synaptic"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by nylemalik1992 on 2014-07-28
hello everyone this is my first ever post on Ubuntu Forums and I would really appreciate a Linux experts help right now as I am just learning the ropes of the Linux worId. I have been running Ubuntu 14.04 on my laptop for a few months now and have loved every aspect of it so far. I went as far as completely erasing Windows 8 from my laptop and now solely have Ubuntu. However I have run into my first problem and I have no idea how to fix it and I've even searched threads but have not seen a problem similar to mine. Basically my software center is not opening and up top next to my wifi icon is a red circle with a line through it and when I try to run it through the terminal the text at the beneath this paragraph. I've tried to run Synaptic and it says "extra junk at end of file" and I can't remove or reinstall the software center through the terminal. I really need the software center for apps and programs to help me with video editing and music transfer. Please any help on this problem would be greatly appreciated.


adilnylemalik92@AdilNyleMalik:~$ software-center
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 21, in <module>
    from apt.debfile import DebPackage
  File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 34, in <module>
    apt_pkg.init_config()
SystemError: E:Syntax error /etc/apt/apt.conf.d/70debconf:6: Extra junk at end of file
INFO:softwarecenter.ui.gtk3.app:setting up proxy 'None'
2014-07-28 01:48:01,951 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 291, in __init__
    self.cache = get_pkg_info()
  File "/usr/share/software-center/softwarecenter/db/pkginfo.py", line 245, in get_pkg_info
    from softwarecenter.db.pkginfo_impl.aptcache import AptCache
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 39, in <module>
    class GtkMainIterationProgress(apt.progress.base.OpProgress):
AttributeError: 'module' object has no attribute 'progress'

---

### Post by ajgreeny on 2014-07-28
Try running commands
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic
```
and report back here the output and any error messages that appear.

Please use code tags for the output by copying it into the reply box (not the quick reply box) then highlight it with the mouse and click on the # icon in the toolbar above.

---

### Post by mc4man on 2014-07-28
You should also post the contents of /etc/apt/apt.conf.d/70debconf

---

### Post by nylemalik1992 on 2014-07-28
```
adilnylemalik92@AdilNyleMalik:~$ sudo apt-get update
[sudo] password for adilnylemalik92: 
E: Syntax error /etc/apt/apt.conf.d/70debconf:6: Extra junk at end of file
adilnylemalik92@AdilNyleMalik:~$ sudo apt-get upgrade
E: Syntax error /etc/apt/apt.conf.d/70debconf:6: Extra junk at end of file
adilnylemalik92@AdilNyleMalik:~$ sudo apt-get install synaptic
E: Syntax error /etc/apt/apt.conf.d/70debconf:6: Extra junk at end of file

```

I hope I replied right. But here is the output I receive when I run those codes.

---

### Post by coffeecat on 2014-07-28
mc4man asked you to post the contents of /etc/apt/apt.conf.d/70debconf . We need to see this. Open a terminal and post the output of this:

```
cat /etc/apt/apt.conf.d/70debconf
```

---

### Post by nylemalik1992 on 2014-07-28
```
adilnylemalik92@AdilNyleMalik:~$ cat /etc/apt/apt.conf.d/70debconf
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};APT::Cache-Limit "100000000"

```

Sorry for the delay.

---

### Post by coffeecat on 2014-07-28
Well - that's very curious. I think you've found a hen's tooth. I tried googling "E: Syntax error /etc/apt/apt.conf.d/70debconf:6: Extra junk at end of file" and came up with only four hits: this thread, a thread from 2007 in the Linuxquestions forum, a thread from 2009 in a German language forum, and something in Facebook, none of which really explained what the fundamental problem was. I think we are on our own!

This is the contents of my /etc/apt/apt.conf.d/70debconf from Ubuntu 14.04:

```
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
```

I have no idea how the extra ' APT::Cache-Limit "100000000" ' got there in yours, but I think it is reasonable to assume that is what is causing the problem. You need to edit /etc/apt/apt.conf.d/70debconf . Normally, I would suggest you install the package gksu so that you can run the gedit text editor with root privileges, but you won't be able to install gksu. So you'll need to run a more basic editor, therefore please take extra care with the following.

Open a terminal and run this command:

```
sudo nano /etc/apt/apt.conf.d/70debconf
```

You will be prompted for your password but when you type it in you won't see anything happening. Don't worry - it is going in, but not being echoed to the screen. After you press enter, the nano text editor will open in the terminal showing the contents of your /etc/apt/apt.conf.d/70debconf as you posted earlier. If it doesn't show that, you have made a typo in the command, so ctrl-x to quit and try again.

If the nano text editor shows what you posted earlier, remove the ' APT::Cache-Limit "100000000" ' bit and then double-check that what is remaining is exactly as I posted. Be aware that nano is a really basic editor - you cannot use the mouse and you have to navigate around with the arrow keys. Once you are sure that the text is as it should be press ctrl-o to save and then ctrl-x to exit.

Now try these commands that ajgreeny suggested and tell us how you get on:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic
```

---

### Post by bapoumba on 2014-07-28
One thing to be careful about, please make sure you end the last line with a semi-colon **;** ie do not take it out, you need to only remove **APT::Cache-Limit "100000000"**. From your file, there is no space between ; and A, leave the **;** in place to be the last char of the line .
See coffeecat's file as an example :)

---

### Post by mc4man on 2014-07-28
Sounds like this came from some suggestions about lagging in youtube & increasing the cache for APT., except the OP forgot/missed the ;
(- [http://ubuntuforums.org/showthread.php?t=1987116&p=11969359&viewfull=1#post11969359](http://ubuntuforums.org/showthread.php?t=1987116&p=11969359&viewfull=1#post11969359) 

edit: just to note - while the ^ post is ok for 12.04,  running sudo gedit in 13.04+ is a bad idea...

add info (basically as mentioned above, make sure all uncommented lines end with a ;
[http://askubuntu.com/questions/342179/how-to-solve-extra-junk-at-end-of-file-when-using-apt](http://askubuntu.com/questions/342179/how-to-solve-extra-junk-at-end-of-file-when-using-apt)

---

### Post by coffeecat on 2014-07-28
> **mc4man said:**
> Sounds like this came from some suggestions about lagging in youtube & increasing the cache for APT., except the OP forgot/missed the ;
(- [http://ubuntuforums.org/showthread.php?t=1987116&p=11969359&viewfull=1#post11969359](http://ubuntuforums.org/showthread.php?t=1987116&p=11969359&viewfull=1#post11969359) 

Nice find! I wonder if that is what the OP did. However....

There's a strong smell of fish coming from that thread, imo. Until someone can explain rationally how increasing the apt cache improves flash performance, I'm with the poster who said there was something odd about the thread. I wonder if all those who proclaim a miracle cure are simply experiencing a co-incidence, such as their ISP increasing their download speed.

---

### Post by mc4man on 2014-07-28
> **coffeecat said:**
>  However....

There's a strong smell of fish coming from that thread, imo. Until someone can explain rationally how increasing the apt cache improves flash performance, I'm with the poster who said there was something odd about the thread. I wonder if all those who proclaim a miracle cure are simply experiencing a co-incidence, such as their ISP increasing their download speed.
Seems unlikely that it could have any effect.  While certainly unscientific I see no difference here from youtube, either in playback or caching. (but I've no issue with lagging to begin with.
One change I've noticed in youtube is in the past it used to cache at a consistent speed & fully. Now it caches about 20% or so very quickly then slows down to 'realtime' 
(- if you pause the vid then caching stops altogether though I was never too convinced that caching from youtube mattered in the first place to any great extent.

---

### Post by nylemalik1992 on 2014-07-29
well coffeecat's codes did the trick and now my software center is back up and running. thanks everyone for the help as I seem to have had a very unique problem but you guys were kind enough to help a linux beginner like me out.

---

### Post by bapoumba on 2014-07-29
> **mc4man said:**
> Sounds like this came from some suggestions about lagging in youtube & increasing the cache for APT., except the OP forgot/missed the ;
(- [http://ubuntuforums.org/showthread.php?t=1987116&p=11969359&viewfull=1#post11969359](http://ubuntuforums.org/showthread.php?t=1987116&p=11969359&viewfull=1#post11969359) 

<snip>

> **coffeecat said:**
> Nice find! I wonder if that is what the OP did. However....

There's a strong smell of fish coming from that thread, imo. Until someone can explain rationally how increasing the apt cache improves flash performance, I'm with the poster who said there was something odd about the thread. I wonder if all those who proclaim a miracle cure are simply experiencing a co-incidence, such as their ISP increasing their download speed.

> **mc4man said:**
> Seems unlikely that it could have any effect.<snip>
Had to play around back in the days where mmap would run out of room. Not sure this is the original bug report I followed and used, but here is an old one as an example :
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24626](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24626)
I did miss out the trailing semi-colon at the end at the time :)

That said, having to increase the apt cache limit is usually linked to large repository lists or not cleaning often enough nowadays. I cannot think of any reasonable reason why increasing apt cache would help playing flash videos other than some packages not installing due to hitting the size limit, but that would show up as a specific error message. I'm quite concerned this Firefox thread comes up at the top of searches.. Typical of how the internet works, I could not trace back the original recommendation because people rarely link back and give credits to where they found a fix. Then you can find it all over the place as it gets spread out and reused, when it is on search engines, it much be true..

Increasing the cache size is one of the routine steps LP answers recommends to troubleshoot package managers problems : [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_5_List_of_Terminal_commands_to_execute_and_send_to_Launchpad_Answers_forum](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_5_List_of_Terminal_commands_to_execute_and_send_to_Launchpad_Answers_forum)
I'm not sure why this is within the normal troubleshooting procedure.

---

