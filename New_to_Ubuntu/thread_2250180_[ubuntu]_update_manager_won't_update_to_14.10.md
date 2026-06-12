---
title: "[ubuntu] update manager won't update to 14.10"
date: 2014-10-27
forum: New to Ubuntu
---

### Post by flex567 on 2014-10-27
I have ubuntu 14.04 alongside with Win7 and I Want to upgrade to 14.10 and I followed these instructions and I get the message: "Your system is up to date" ??
```

[LIST]
[*]Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. 
[*]Update Manager should open up and tell you: New distribution release '14.10' is available. 
[*]Click Upgrade and follow the on-screen instructions.
[/LIST]

```

---

### Post by slickymaster on 2014-10-27
Before upgrading, you need to update your system. Open up the terminal window and enter the following commands```
sudo apt-get update && sudo apt-get upgrade
```The above command will download and install the available latest packages. Once that done, and again at a terminal window, run```
sudo do-release-upgrade
```

---

### Post by grahammechanical on 2014-10-27
Please run these two commands and tell us what they report;

```
lsb_release -a
cat /etc/os-release
```

Another thing you can do is to open System Settings>Software and Updates>Updates tab and make sure that you have chosen "For any new version" in the panel "Notify me of a new version of Ubuntu." If it is set to "For Long Term Support versions" then the message that you are getting is normal for having that setting.

But do you really want to upgrade to 14.10? It only has 9 months support. That means that you will have to upgrade to 15.04 and then to 15.10 and then to 16.04 to get back on to a long Term Support Release. It is your choice.

Me? I have already switched from 14.10 on to Vivid Vervet (15.04 development branch). This is my choice. Just so we know the consequences of our decisions. There is no going back from an upgrade except by re-installing.

Regards

---

### Post by flex567 on 2014-10-27
Why should i need long term support?

---

### Post by slickymaster on 2014-10-27
Long term support releases (LTS) are designed to be stable platforms that you can stick with for a long time. Ubuntu guarantees LTS releases will receive security updates and other bug fixes as well as hardware support improvements (in other words, new kernel and X server versions) for five years. 

In comparison, a regular release will only be supported for nine months. Considering new versions of Ubuntu are released every six months, you’ll have three months after a new version is released to upgrade to it or you won’t receive security patches anymore. You’ll probably want to upgrade to every LTS version — new LTS versions are released every two years. If you stick with the LTS version, you’ll still get a new Ubuntu release every two years.

LTS versions are designed to be more polished, while the standard releases bring you the latest features that may not be completely finished yet. When you use the latest release, you’ll end up upgrading every six to nine months. When you use the LTS version, you can upgrade every two years or even hold on for five years.

---

### Post by flex567 on 2014-10-27
Another reason that I wanted to upgrade my OS is because i get this error every time I login to Ubuntu, Is there a way to fix this error?
System program problem detected
Do you want to report the problem now?

---

### Post by mc4man on 2014-10-27
> **flex567 said:**
> Another reason that I wanted to upgrade my OS is because i get this error every time I login to Ubuntu, Is there a way to fix this error?
System program problem detected
Do you want to report the problem now?
Well if you haven't already try 'doing' yes, maybe it'll stop bothering you after that.
If you have already & it keeps popping up then remove the apport files, maybe it will stop
```
sudo rm /var/crash/*.*
```
Edit: the above code should be carefully used, a full copy & paste advised

---

### Post by flex567 on 2014-10-27
I decided not to upgrade 14.04 just jet. 
Should I stil  use this command to repair the error?
 ```
sudo rm /var/crash/*.*
```

---

### Post by slickymaster on 2014-10-27
> **flex567 said:**
> I decided not to upgrade 14.04 just jet. 
Should I stil  use this command to repair the error?
 ```
sudo rm /var/crash/*.*
```

That command won't repair any errors, it will delete all the error reports held in the **/var/crash/** directory.

If you want to view the error report go to the **/var/crash/** directory and there you will find the error reports which you can view with any text editor. If you can't figure out the problem and the message keeps coming up, it is possible that this error only happened once, but the error report got stuck and pops-up on every boot. So just delete the error reports from **/var/crash/** using the command mc4man provided for the effect.
If after this the error message doesn't come back then all is good. If the error message is not from a stuck report, but the errors are constantly happening and you can't figure out the problem on your own then submit a bugreport. See: [How do I report a bug?]("http://askubuntu.com/questions/5121/how-do-i-report-a-bug")

---

### Post by flex567 on 2014-10-27
This is the part of that file, the whole file is 512 lines long  ```
 ProblemType: Crash Architecture: i386 CrashCounter: 1 Date: Sun Oct 26 23:09:05 2014 DistroRelease: Ubuntu 14.04 ExecutablePath: /usr/sbin/unity-greeter ExecutableTimestamp: 1398907033 ProcCmdline: /usr/sbin/unity-greeter ProcCwd: /var/lib/lightdm ProcEnviron:  LC_TIME=sl_SI.UTF-8  LC_MONETARY=sl_SI.UTF-8  PATH=(custom, no user)  XDG_RUNTIME_DIR=  LC_ADDRESS=sl_SI.UTF-8  LANG=en_US.UTF-8  LC_TELEPHONE=sl_SI.UTF-8  SHELL=/bin/false  LC_NAME=sl_SI.UTF-8   
```

---

### Post by slickymaster on 2014-10-28
> **flex567 said:**
> This is the part of that file, the whole file is 512 lines long  ```
 ProblemType: Crash Architecture: i386 CrashCounter: 1 Date: Sun Oct 26 23:09:05 2014 DistroRelease: Ubuntu 14.04 ExecutablePath: /usr/sbin/unity-greeter ExecutableTimestamp: 1398907033 ProcCmdline: /usr/sbin/unity-greeter ProcCwd: /var/lib/lightdm ProcEnviron:  LC_TIME=sl_SI.UTF-8  LC_MONETARY=sl_SI.UTF-8  PATH=(custom, no user)  XDG_RUNTIME_DIR=  LC_ADDRESS=sl_SI.UTF-8  LANG=en_US.UTF-8  LC_TELEPHONE=sl_SI.UTF-8  SHELL=/bin/false  LC_NAME=sl_SI.UTF-8   
```

If you want to report that bug against the correct package, which is in your case unity-greeter, first you'll have to [create an account at Launchpad]("https://launchpad.net/"), if you don't already have one.
Then, and before reporting it, make sure the bug hasn't been already reported by [searching the existing reported bugs against the package]("https://launchpad.net/ubuntu/+bugs?field.searchtext=unity-greeter&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package="). If you found an existing bug, you can answer **'Does this bug affect you'** with _'This bug affects me'_ and add any additional information as comments.

If not, open a terminal window and run```
ubuntu-bug unity-greeter
```enter your password when prompt to it and Apport (Ubuntu bug-reporter) will collect the necessary data. A window will then pop up, asking you if you want to report the bug. Click "Send Report" to proceed and Apport will then upload the problem information to Launchpad, and a new browser window will then open to inform you that the bug report is being processed. Follow the instructions given and when you're done, click "Submit bug report".

---

### Post by Penguin360 on 2014-10-28
> **flex567 said:**
> Why should i need long term support?

In my opinion, the LTS release is for regular users including newbies, while the non-LTS release is for geeks, adventurers, bug crushers, and some impulsive installers. :p

---

### Post by QIII on 2014-10-28
I would hardly label myself a newbie or a regular user, even though I use LTS versions on my server and primary machine.  That is a pretty broad brush.

I keep up with the interim releases and dev releases on other machines.

---

