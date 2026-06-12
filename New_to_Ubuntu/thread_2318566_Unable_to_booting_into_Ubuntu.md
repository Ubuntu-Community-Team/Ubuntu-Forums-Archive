---
title: "Unable to booting into Ubuntu"
date: 2016-03-27
forum: New to Ubuntu
---

### Post by nikhil16 on 2016-03-27
I have Ubuntu 15.10 alongside a Windows 10 OS. My issues has nothing to do with the latter btw (I hope).

I had few tutorial videos in the Videos folder in Ubuntu, which I wanted to move to another folder (which I wanted to be at /, called videotutorials (or whatever)). I successfully created the folder, at /, and performed sudo mv to that folder, and the whole computer froze. I left it there for almost half hour, even then, nothing. Then I performed **RIESUB **on it, after which, every time the computer was booted, it shows attachment file #1, named 1.jpg.

If I exit it (by tying *exit*), it exists and shows the second attachment, called 2.jpg

The only way I can enter Windows is by opting the last option. If I hit the fourth, it just goes back to the first screenshot.

Please can you help?

---

### Post by TheFu on 2016-03-27
Try boot repair. That's the first step. If it doesn't fix it, post the generated URL here for more help. Instructions below.

This also demonstrates running commands with sudo that aren't understood is a bad idea.  Working off / is a dangerous thing. I would just restore from the last backup and chock this up as a learning experience.

---

### Post by Bucky Ball on 2016-03-27
You'd need to be more specific with the commands you used to gauge what the breakage is ...

---

### Post by nikhil16 on 2016-03-27
If my memory serves me right, it was "sudo mv (path to default Videos folder) * /videotutorials". It's either that, or "sudo mv (path to default Videos folder)/* /videotutorials" (notice there's a / before the *.

Path to default Video folder is /home/username/Videos, if I am not wrong. Thnx

---

### Post by grahammechanical on 2016-03-27
Do you by any chance have a separate /home partition? If you do, then did the Ubuntu partition ( / ) have enough space to hold those video files?

Do you get a Grub boot menu? If you do not then it is most likely that Grub cannot find it configuration file which should be at /boot/grub/grub.cfg. The question is, why not? Moving files from the home folder to the root folder should not over-write grub.cfg. But something nasty happened during the moving of those files and the subsequent restart.

Regards

---

### Post by Impavidus on 2016-03-27
> **nikhil16 said:**
> If my memory serves me right, it was "sudo mv (path to default Videos folder) * /videotutorials"...

That would do. Because of the space before the asterisk this would move all files and directories in the current directory (presumably /, as that's where you just created the new directory) to /videotutorials. That will certainly break your system. You may still be able to move it back if you boot from a live disk.

---

### Post by Bucky Ball on 2016-03-27
As above. Boot from the install media, 'Try Ubuntu', once at a desktop start looking around and trying to move or get rid of those files. What you've done, as stated above, will cause unpredictable breakage. You moved everything to the /videotutorial folder basically and not sure if there's any coming back from there. 

Here's hoping ...

---

### Post by nikhil16 on 2016-03-28
Here's the boot-repair log: [http://paste.ubuntu.com/15537217/](http://paste.ubuntu.com/15537217/) Hope this helps. Thnx!

---

