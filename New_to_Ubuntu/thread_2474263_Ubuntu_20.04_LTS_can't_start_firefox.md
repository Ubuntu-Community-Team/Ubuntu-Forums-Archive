---
title: "Ubuntu 20.04 LTS: can't start firefox"
date: 2022-04-25
forum: New to Ubuntu
---

### Post by maketopsite on 2022-04-25
[I]Firefox is already running but not responding. To use Firefox, you must first stop the existing Firefox process, restart your device or use a different profile.

[/I]but
```
$ ps aux | grep firefox
maketopsite         22126  0.0  0.0   8868   724 pts/7    S+   11:11   0:00 grep --color=auto firefox
$
```

Anyone know please what is wrong ?

---

### Post by ActionParsnip on 2022-04-25
What is the question here please?

---

### Post by mIk3_08 on 2022-04-25
> **maketopsite said:**
> [I]Firefox is already running but not responding. To use Firefox, you must first stop the existing Firefox process, restart your device or use a different profile.
[/I]but
```
$ ps aux | grep firefox
maketopsite         22126  0.0  0.0   8868   724 pts/7    S+   11:11   0:00 grep --color=auto firefox
$
```
Anyone know please what is wrong ?
Hi, can you elaborate more about your situation issue so that the people here in Ubuntu forum community that is willing to help you may easily know what the situation and can response immediately to your needs. regards and cheers.

---

### Post by maketopsite on 2022-04-25
> **ActionParsnip said:**
> What is the question here please?

Hello,

Why can't I start firefox ? (I'm trying to run firefox from terminal and I get message I posted in first post: "*Firefox is already running but not responding. ...*"). There is no visible firefox window in IceWM taskbar or in Window list. 

[FONT=courier new]ps[/FONT] command line utility says that firefox is not running (see code output in first post) - can I be 100 % sure about it ?

Is it a firefox bug ? How can I start it without rebooting Ubuntu ?

---

### Post by &amp;KyT$0P# on 2022-04-25
Please open a Terminal in your Firefox profile folder and post the output from running
```
ls -la
```
If you have multiple sub-folders in [FONT=Courier New]~/.mozilla/firefox/[/FONT] and are not sure which one is your Firefox profile folder, you can find out by checking the [FONT=Courier New]profiles.ini[/FONT] file.

---

### Post by maketopsite on 2022-04-25
> **mIk3_08 said:**
> Hi, can you elaborate more about your situation issue so that the people here in Ubuntu forum community that is willing to help you may easily know what the situation and can response immediately to your needs. regards and cheers.

Hi, my apology, is please info I posted here [https://ubuntuforums.org/showthread.php?t=2474263&p=14092286#post14092286](https://ubuntuforums.org/showthread.php?t=2474263&p=14092286#post14092286) enough ?

---

### Post by ajgreeny on 2022-04-25
The thread you linked to in post #6 is this thread so it does not help at all.

The only firefox showing in your ***ps aux*** output is the grep search, not an instance of firefox at all so I'm a bit baffled about what is going on here.
However, it may be worth trying command ***killall firefox*** to close any hidden firefox instances, though why they're hidden is beyond me.

---

### Post by TheFu on 2022-04-25
It could be that firefox crashed, but didn't properly clean up a PID file somewhere?
I haven't seen that.  If the pid file is in /var/run, then a reboot of the system should clean that up, just as all tmpfs file systems are cleaned up by a reboot.

If it doesn't clean up the files that firefox is internally looking at to see whether it is running, I'd start looking under your ~/.mozilla/firefox/ directory somewhere.

You can also use a command line option to allow multiple instances to run.  The firefox manpage is extremely sparse, but it has that option.  I use it all the time.

And for systems that don't have firefox running inside a snap environment, you can run it inside a firejail environment, so that different instances of firefox are in different kernel namespaces. They don't see each other.

Just a few ideas to try. I don't know if any will actually work.

---

### Post by maketopsite on 2022-04-28
problem was caused by loading firefox profile from partition on which is Windows 8.1 in hibernation mode. This partition is mounted in read only mode so firefox message is wrong.

---

