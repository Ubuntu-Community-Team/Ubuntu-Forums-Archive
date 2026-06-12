---
title: "X-Server Crashes when running certain programs"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Luhood on 2012-07-02
I'm running Ubuntu 12.04 (or the latest one) on an Acer Aspire 5737Z Laptop, and have done so since the update was released. But a few days ago me and a friend tried to connect my computer to his TV via HDMI-cable, but after we failed to get it to work the way we wanted it to we decided to let bygones be bygones and restore things to the way they were.

However, now my X-Server crashes at certain moments: 

[LIST]
[*]When I try to open anything in Skype other than the main window (options, conversations, etc.);
[*]When I start SMPlayer (while VLC works perfectly fine);
[*]When I try to run the System Testing application;
[/LIST]
And if there are others, I haven't discovered them yet. And I don't really feel the need to search for more crashing programs unless I have to. Though I will do so if anyone think I need to in order to solve this.

So, hence I wonder:

[LIST=1]
[*]Which logs do I need to upload/paste here in order to enable you all to help me?
[*]Why is it doing this?
[*]Can I fix it without reinstalling my entire system? How?
[/LIST]
Please, I'm desperate! I'm very much a beginner in the world of Linux, most certainly so when it comes to debugging and such, and thus any help to find out why it doesn't work anymore is appreciated.

---

### Post by spikoley on 2012-07-03
It sounds like something is wrong with xorg.conf, but I am not familiar with the newer version.  This [page]("https://wiki.ubuntu.com/X/Config/") might help you.  It should be able to be fixed by editing a file.

Try starting one of the programs that crash from the terminal and post any errors here.  Skype's command is skype.

The xorg files look like they were moved to /usr/share/X11/xorg.conf.d/.  Post the HDMI file if there is one.  I think the solution might to delete that file, but I would check with somebody else.  

Sorry, I can resolve it for you.  But, I did give you some things to work with and a bump!

---

### Post by Luhood on 2012-07-04
So I tried starting SMPlayer, and it all crashed. I checked some of the logfiles (in /var/log/, right?), and found some stuff I hope is important.

In apport.log:
```
ERROR: apport (pid 1945) Wed Jul  4 13:54:34 2012: called for pid 1309, signal 6
ERROR: apport (pid 1945) Wed Jul  4 13:54:34 2012: executable: /usr/bin/Xorg (command line "/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch")
ERROR: apport (pid 1945) Wed Jul  4 13:54:34 2012: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 1945) Wed Jul  4 13:54:37 2012: wrote report /var/crash/_usr_bin_Xorg.0.crash
```Found this line is syslog.1:
```
Jul  4 13:54:38 Deathstar gnome-session[1470]: Gdk-WARNING: gnome-session: Fatal IO error 104 (Connection reset by peer) on X server :0.#012
```And though I'm not sure if it's relevant or not, in the end of kern.log.1:
```
Jul  1 23:33:33 Deathstar kernel: [   25.569400] NVRM: Your system is not currently configured to drive a VGA console
Jul  1 23:33:33 Deathstar kernel: [   25.569405] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Jul  1 23:33:33 Deathstar kernel: [   25.569408] NVRM: requires the use of a text-mode VGA console. Use of other console
Jul  1 23:33:33 Deathstar kernel: [   25.569411] NVRM: drivers including, but not limited to, vesafb, may result in
Jul  1 23:33:33 Deathstar kernel: [   25.569413] NVRM: corruption and stability problems, and is not supported.
```I'm gonna try starting Skype now, and see what the logs tell me!

-----------------------------------------------

So, crashed with Skype! The logs

apport.log:
```
ERROR: apport (pid 8226) Wed Jul  4 14:29:56 2012: called for pid 1971, signal 6
ERROR: apport (pid 8226) Wed Jul  4 14:29:56 2012: Unhandled exception:
Traceback (most recent call last):
  File "/usr/share/apport/apport", line 282, in <module>
    info.add_proc_info(pid)
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 438, in add_proc_info
    assert os.path.exists(self['ExecutablePath'])
AssertionError
ERROR: apport (pid 8226) Wed Jul  4 14:29:56 2012: pid: 8226, uid: 0, gid: 0, euid: 0, egid: 0
ERROR: apport (pid 8226) Wed Jul  4 14:29:56 2012: environment: {}
ERROR: apport (pid 8233) Wed Jul  4 14:29:57 2012: called for pid 8181, signal 6
ERROR: apport (pid 8233) Wed Jul  4 14:29:57 2012: executable: /usr/bin/skype (command line "skype")
ERROR: apport (pid 8233) Wed Jul  4 14:29:57 2012: gdbus call error: Error connecting: Could not connect: Connection refused

ERROR: apport (pid 8233) Wed Jul  4 14:29:57 2012: debug: session gdbus call: 
ERROR: apport (pid 8233) Wed Jul  4 14:30:38 2012: wrote report /var/crash/_usr_bin_skype.1000.crash
```Found this in syslog:
```
Jul  4 14:29:57 Deathstar gnome-session[2109]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012
```What is interesting is that the Xorg.#.log (replace # with number) files don't seem to turn up anything unusual. Though I wonder, should I upload the two crash reports somewhere too?

-----------------------------------------------

Double Edit:
It works. I'm not sure what I did, but now it works. What did I do to make it work? D:

---

### Post by spikoley on 2012-07-05
I'm glad to hear that it works.  Too bad we don't know why, but the important thing is it works.

---

### Post by eklikeroomys on 2012-07-24
I am having the exact same issue at the moment.. Any idea how you managed to fix it?

---

### Post by NikTh on 2012-07-24
Hi , 
can you post more info ? 
```
gedit /var/log/Xorg.0.log 
gedit .xsession-errors
``` 

Thanks

---

### Post by eklikeroomys on 2012-07-24
I have managed to fix the problem by commenting out the following lines in my /etc/X11/xorg.conf:

Section "Files"
       FontPath        "unix/:7100"
EndSection

---

### Post by NikTh on 2012-07-25
Hi , 
glad you fixed this .. 
can you please mark this **thread as solved** ? from **thread tools**. 

Thanks

---

### Post by eklikeroomys on 2012-07-25
I don't have the option for marking it solved. I did not start this thread.

---

