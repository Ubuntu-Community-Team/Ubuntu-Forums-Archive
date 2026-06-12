---
title: "Ubuntu 18.04 frequent problem reporting happening.  How to diagnose cause."
date: 2019-02-23
forum: New to Ubuntu
---

### Post by richard378 on 2019-02-23
Hi,
I am running Ubuntu 18.04 LTS on a Desktop. It works fine on my laptops, but on my desktop, I get frequent pop-ups of error reporting. They just say cancel or report the problem, and I don't know how to determine the cause to address the frequent popup that happens every boot on my Desktop. Where can I find the error log and how do I diagnose the error. I need to know if I need an updated kernel or what the problem may be that I need to fix on this one machine. I have checked to make sure intel-microcode was installed. I don't know what else to try. My logs show only an error with Boxes VM which is a known issue with Boxes currently.  This happens also when I uninstall Boxes so I know this error reporting is not the Boxes error. Why is my system reporting errors constantly?

---

### Post by Risperix on 2019-02-23
See if this helps you :D

[https://ubuntuforums.org/showthread.php?t=2413082](https://ubuntuforums.org/showthread.php?t=2413082)


> [COLOR=#000000]Happened to me after the last update.[/COLOR]

[COLOR=#000000]Try this[/COLOR]

[COLOR=#000000]$ ls /var/crash/[/COLOR]

[COLOR=#000000]You will see something like this:[/COLOR]

[COLOR=#000000]_opt_google_chrome_chrome.1000.crash[/COLOR]
[COLOR=#000000]_opt_teamviewer_tv_bin_TVGuiDelegate.1000.crash[/COLOR]


[COLOR=#000000]and then type :[/COLOR]

[COLOR=#000000]sudo rm /var/crash/*[/COLOR]


[COLOR=#000000]Hope it help you [/COLOR]:razz:

---

### Post by richard378 on 2019-02-24
There was a crash report. I delted it and will see if the pop-up will stop. I will get back to you. Thanks.

---

### Post by richard378 on 2019-02-24
It worked.  That was the fix I needed.  No more error reporting is appearing.  Thanks.

---

### Post by Risperix on 2019-02-24
Great!
You're welcome :smile:

---

