---
title: "Screen Freezes"
date: 2022-12-17
forum: New to Ubuntu
---

### Post by gordon33 on 2022-12-17
Hello All

My HP 15t-da100 screen has been locking up. The Ubuntu 22.4 operating system has worked fine for a year until about a week ago. Since then the screen locks up. I have to shut the laptop down and restart it.

I can still move the mouse arrow. Some time I can right click and shut the computer down and other times I have to hold the power button down until it shuts down. T



Gordon33

---

### Post by TheFu on 2022-12-17
Can you ssh into the system from another machine?  That would tell us if it was just a GUI issue or the whole machine.
What do the system logs say at the time of the lockup.


Or do you want us to guess 10,000 things that could break a computer?

---

### Post by Impavidus on 2022-12-18
When the GUI freezes, can you still reboot using alt+SysRq+REISUB? Also known as the [magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key). Hitting the power button while the computer is installing some upgrade can have unpleasant side effects, even with journaling filesystems.

Or can you reach a text interface with ctrl+alt+F1 through ctrl+alt+F7? The exact function key varies among Ubuntu releases. One of the others should bring you back to the GUI.

See in the logs which packages were updated around the time when the problem began. The relevant log is /var/log/apt/history.log. Older logs are compressed in the same directory.

You can only ssh into the machine if you installed the ssh server, which isn't installed by default.

---

### Post by gordon33 on 2022-12-18
Hello  

Thank you the alt command got this thing to reboot and I sighed in

---

### Post by gordon33 on 2022-12-18
I will nave to post with a diffrent computewr.  this one keeps shutting down.

---

### Post by TheFu on 2022-12-18
> **gordon33 said:**
> I will nave to post with a diffrent computewr.  this one keeps shutting down.

That sounds like a hardware fault.
Or 100% out of storage.
Or both.

Bad hardware will often complain loudly in system logs and those logs, if they aren't restricted in size, will grow to fill the entire partition, which will crash the system.

To see how much disk is being used for logs:
```
$ journalctl --disk-usage
```

To remove all but 200MB:
```
$ sudo journalctl --vacuum-size=200M
```

You can change the maximum allowed log file size in  /etc/systemd/journald.conf . There's a manpage for that file and the settings it contains. Fairly easy to understand. Use "sudoedit /etc/systemd/journald.conf" to edit the file.  Be certain to have 2 terminals open - one with the manpage and the other for editing. You'll likely want to see both concurrently.

Of course, this is all guesswork, since no data has been provided.

---

### Post by gordon33 on 2022-12-18
h

---

### Post by gordon33 on 2022-12-18
Is this the part of the log that helps?

---

### Post by #&amp;thj^% on 2022-12-18
That's a bit better, we won't guess as much now. ;)
Are you using your bluetooth for anything? If not while your system is working try disabling it.
```
sudo systemctl disable bluetooth
```

---

### Post by gordon33 on 2022-12-18
I Disabled the blue tooth.

I only use blue tooth for the printer.

The screen froze right after I typed the 2 lines above.  I had to retype them.

---

### Post by TheFu on 2022-12-19
> **gordon33 said:**
> Is this the part of the log that helps?

Nope.  Those aren't errors.
Process of elimination of you can't look at system logs.

Step 1 - Is it the hardware or the OS?  Boot from a USB flash drive version of Linux.  The "Try Ubuntu" more that all Ubuntu-flavors support is ideal for this. The will remove person and system settings from the list of possible problems along with the disk storage hardware (except the USB part).  Use that for the rest of today (or until it crashes).  If it doesn't, we know it is something about YOUR system and not likely to be a software bug for everyone.  We sorta already know that because millions of users are running the OS today without lockups.

---

### Post by gordon33 on 2022-12-19
I will have to get a usb drive.

---

### Post by TheFu on 2022-12-19
> **gordon33 said:**
> I will have to get a usb drive.

I use a microSD to USB converter (USD 9), since I have lots and lots of 8GB microSD storage devices lying around.  Larger isn't better, since I think the most bloated distro uses 5G.  Some lite distros are under 700MB, so a 4GB microSD is fine.

---

### Post by ActionParsnip on 2022-12-20
You may also want to test your RAM health to make sure the RAM is healthy

---

### Post by gordon33 on 2022-12-20
I did check the ram with the terminal   Got all OK's

---

### Post by gordon33 on 2022-12-25
Hello All

The computer has been running fine since my last reply 5 days ago.  Could it have been a problem with blue tooth?  The last 2 things I did was sudo systemctl disable bluetooth then check the computer ram.

---

