---
title: "Delete root-owned files from console login"
date: 2014-08-28
forum: New to Ubuntu
---

### Post by nathanbotas on 2014-08-28
Hi everyone,

Let me start by saying I can't express my gratitude for your help in this matter. I have another thread open, but my problem has changed since then so I'm starting this thread with the specific new problem, which is a result of the first one, so to speak, but should have the same solution. Some of my previous post is in grey below:

[COLOR=#000000]I let the foremost extraction command run for 8 hours, and it filled up my recovered folder with so many documents that there is now less than a GB left on my 270GB hard drive. Now, when I start the computer I get this error message "The system is running in low/graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself. When I click on, I have the options to 1. run in low-graphics mode for just one session (but when I try this option the computer is never able to start). 2. reconfigure graphics. 3. troubleshoot the error. 4. exit to console login."

[/COLOR]I need to delete the root-owned files in the folder that Foremost was extracting to so that I can free up my HD and, hopefully, get the computer back to normal. Can the folder containing root-owned files be deleted from console login? If so, I would need someone's help to run those commands. Again, I greatly appreciate any help.

---

### Post by nathanbotas on 2014-08-28
Actually, now when I attempt to "exit to console login", the computer goes to the black screen and I get the message " sd 6: 0 :0 :0 : [sdb] Asking for cache data failed" which is followed by a new line with the same numbers and the message "Assuming drive cache: write through"

---

### Post by The Cog on 2014-08-28
You need to precede the remove command with the word sudo (think SuperUser do, like run as administrator). e.g.
```
cd /recovered-files
sudo rm unwanted-file.txt

```
If you want to delete the entire folder:
```
sudo rm -rf /unwanted-folder
```

Be careful with this - you could accidentally wipe the lot - beware of typing errors.

---

### Post by nathanbotas on 2014-08-28
How can I do this now that I can access neither the console login nor the normal bootup? Is there a way I can get to some kind of place where I can do a command when I'm having these kinds of problems?

---

### Post by The Cog on 2014-08-28
> **nathanbotas said:**
> Actually, now when I attempt to "exit to console login", the computer goes to the black screen and I get the message " sd 6: 0 :0 :0 : [sdb] Asking for cache data failed" which is followed by a new line with the same numbers and the message "Assuming drive cache: write through"

I think that's a message from the driver for your SD card slot. It's very annoying and the only way to get rid of it is to blacklist the driver which leaves the slot non-functional of course. Aha! Googling for a link for you, I found what's claimed to be a fix.
[http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled/162942#162942](http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled/162942#162942)

---

### Post by nathanbotas on 2014-08-28
The problem seems to be now, however, that I can't get anywhere to use a command line. How can I do that? F2 for setup or F12 for boot options? Any ideas?

---

### Post by grahammechanical on 2014-08-28
You can get to a root shell prompt by means of Recovery mode. Which in 14.04 is in the Advanced Options for Ubuntu sub-menu.

Regards

---

### Post by nathanbotas on 2014-08-28
I've only got 12.04. Similar process?

---

### Post by yancek on 2014-08-28
On my Ubuntu 12.04 boot menu, the second Ubuntu boot option is recovery mode.  If you see that, give it a try.

---

### Post by nathanbotas on 2014-08-28
Thank you guys, problem solved. When people ask me why I use Linux, having this kind of community is my reason.

---

