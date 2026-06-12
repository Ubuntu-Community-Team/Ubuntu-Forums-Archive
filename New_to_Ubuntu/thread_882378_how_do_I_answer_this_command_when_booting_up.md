---
title: "how do I answer this command when booting up"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by kuuser on 2008-08-06
what do I type for the LAST command line?  
Thank You!

The [Kubuntu 8.04] conversation, when booting up......

*an automatic file system ck (fsck) of the root file system failed.  A manual fsck must be performed, then the system restarted.  The fsck should be performed in maintenance mode w/ the root file system mounted in read-only mode.

* the root filesystem is currently mounted in read-only mode.  A mainetenance shell will now be started.  After performing system maintenance, press CONTROL-D to terminate the maintenence shell and restart the system

bash: no job control in thhis shell
bash:  groups: command not found
bash:  lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@(name)-desktop:~#  "reboot" (passed)
(name)-desktop login: (passed)
Password:  (passed)

[FONT="Century Gothic"](name)@(name)-desktop:~$[/FONT]


(I'm guessing at which tag words to use)

---

### Post by Tanker Bob on 2008-08-06
Just hit Ctrl-D and it may boot through. That's worked for me a few times in the past.

---

### Post by Jack M. on 2008-08-07
If it still doesn't boot properly, try using the filesystem checker (fsck) as suggested by the error message.

```
sudo fsck
```

---

### Post by kuuser on 2008-08-07
I did Ctrl-D which resulted in:
Ubuntu 8.04 (name)-desktop tty1
then
(name)-desktop login: (checked)
Password:(c)
we're back at:
(name)@(name)-desktop:~$

Thank You...I'll try next suggestion!

---

### Post by kuuser on 2008-08-07
> **Jack M. said:**
> If it still doesn't boot properly, try using the filesystem checker (fsck) as suggested by the error message.

```
sudo fsck
```
"filesystem checker (fsck) as suggested by the error message."
I used code:
sudo fsck
then:
[sudo] password for (name): (c)
Pass 1, 2, 3, 4, 
then:
Unattachede inode 812
Connect to /lost+found<y>?
      What Do I Do Now?

---

### Post by Jack M. on 2008-08-07
Type 'y' and hit Enter to give fsck permission to place files in the /lost+found folder. It sounds like there are corrupted files on your hard drive, which could be a symptom of hard drive failure unless you recently had a system crash or lost power. Make sure all your files are backed up as soon as possible. More information [here]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html").

---

### Post by kuuser on 2008-08-07
Thank you for replying.But I didnt understand it
I havnet had system crash or haven't lost power recently.  By itself it entered Yes then Enter.
Inode 812 ref count is 2, should be 1, Fix<y>? yes [it did by itself.
Indoe 2150537 ref count is 1, should be 2, Fix<y>/ yes [i entered].
Pass 5: checking group summary imformation

Block bitmap differences:     followed by a lot of -(number groups).........  Fix<y>? [i entered yes].
Free blocks count wrong for group #0 (11339, counted=11338).
Fix<y>?

[Do i enter yes then enter?]

---

### Post by Jack M. on 2008-08-07
Yes, answer 'y' or 'yes' to any prompts about fixing something. Basically, what fsck (the tool we're using now) does is attempt to restore your hard drive's files to a normal state, since they have been corrupted. Hopefully, this will get things in order enough for you to be able to boot normally. fsck places anything it can't fix in the /lost+found folder, which is created when you install Linux.

---

### Post by kuuser on 2008-08-07
entered yes many times, to:  
Inode bitmap differences, and numerous "wrong inode counts"
then
/dev/sda5: *****FILE SYSTEM WAS MODIFIED ***** 
/dev/sda5: *****REBOOT LINUX *****
/dev/sda5: 241468/2231456 files (     % non-contiguous), "7 digit numbers /  .... " blocks

we're back at:
(name)@(name)-desktop:~$

Did a good thing happen to FILE SYSTEM?  
Do I have to REBOOT LINUX like it said?  
Do I repeat , as in post entry #5 , your [sudo fsck] entry now?

I don't know why the smilies are appearing.

OK, I keep entering [sudo fsck]
_this keeps repeating:_
fsck 1.40.8 (13-Mar-2008}
e2fsck 1.40.8 (13-Mar-2008}
/dev/sda5: clean, 241468/2231456 files, 1707342/4462045 blocks
(name)@(name)-desktop:~$

OK, I keep entering [sudo fsck]
Thanks for helping!

---

### Post by Jack M. on 2008-08-07
Hopefully, the file system was fixed. Reboot with Ctrl+D, yes.

(Oh, and the smilies appear because there's an '8' followed by an ')', which is converted by the forums software into 8). Similarly, ':' and '(' becomes :(.)

---

### Post by kuuser on 2008-08-07
[Ctrl+D]  and [yes]  return to (name)@(name)-desktop:~$
Thank you for all of your help; I appreciate your time and effort.
I think I click the Thank you button before I post quick reply?

Waiting for more input, to solve situation.

---

### Post by kuuser on 2008-08-07
I dont know if the replies appear automatically as they are submitted, by persons other than myself.   I keep going back to click on post...there must be a quicker way to see replies.

---

### Post by Jack M. on 2008-08-07
At this point, it seems like your Kubuntu installation is irreparably damaged (unless someone else can provide some insight). I would recommend booting to the Live CD and copying all of your personal files over to an external hard drive, USB stick, etc., then reinstalling completely. Again, your main hard drive could possibly be physically damaged, so be sure to keep everything important backed up.

(Just hit refresh to see new replies.)

---

### Post by kuuser on 2008-08-07
I'll do what you suggest; someone else can do reinstallation.  Need help finding the Refresh button!   **Thank you! **

---

### Post by Jack M. on 2008-08-07
By "the refresh button", I just mean the one on your browser's toolbar (the positioning varies from browser to browser). Failing that, F5 is the key combination for refresh/reload page in virtually every browser. If you do need any more help, we're all still here! :)

---

### Post by kuuser on 2008-08-07
OK, That button.  Wow - this forum is great; learned a lot.  Thanks again for your expertise, Jack!!  And Bob.
My appreciation to Everyone.

---

### Post by Bucky Ball on 2008-08-07
Boot recovery kernel and see what it tells you ...

---

### Post by kuuser on 2008-08-07
> **Bucky Ball said:**
> Boot recovery kernel and see what it tells you ...
 
[FONT=Arial]The bootup worked like normal, after shut down 11 hrs ago  :)[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Questions from this thread:[/FONT]
[FONT=Arial]File System was modified - did cmptr lose anything?[/FONT]
[FONT=Arial]Reboot Linux - should this be done?[/FONT]
[FONT=Arial]How do you boot recovery kernel?[/FONT]
[FONT=Arial][/FONT]

---

### Post by Tanker Bob on 2008-08-07
1) Did you lose anything? Hard to say. You could, especially if it was a hard drive issue. ext3 is a journaling file system and generally does a good job at recovering recent changes when crashes occur.

2) Linux can be rebooted w/o harm, it Linux doesn't require regular restarts unlike Windows. You can always just reload the x-server from the login screen or using ctrl-alt-backspace if you update your video drivers.

3) The recovery mode should be the second option on GRUB at bootup.

---

### Post by bodhi.zazen on 2008-08-07
You can not check a mounted file system ...

so, boot a live CD

open a terminal and enter :

```
sudo e2fsck -C0 -pfv /dev/sda5
```

If that fails :

```
sudo e2fsck -fvy /dev/sda5
```

Modify that command if sda5 is not your root partition.

=========

Usually this problem is indicative of a potentially failing HD. If that works make sure your data is backed up and backups are working.

---

### Post by kuuser on 2008-08-07
in reply to: "recovery mode should be the second option on GRUB at bootup.recovery mode should be the second option on GRUB at bootup".
 
my bootup shows numerous rows:  Ubuntu 8.04, kernel 2.6.24-19-generic
followed by Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
then
Ubuntu 8.04, kernel 2.6.24-18-generic
and its recovery mode
each row repeated, in descending #, to 
Ubuntu 8.04, kernel 2.6.24-16-generic
then
Ubuntu 8.04, memtest86+
Other operating systems:
Microsoft Windows XP Professional
 
I always open the top row: Ubuntu 8.04, kernel 2.6.24-19-generic
I havent opened...   Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode) yet.
I'm reading Bodhi.zazen reply... & don't know what it means, so decided to wait opening this way,for now.
 
Some background about my computer: I have both Kubuntu & Windows XP.  My system contains Ubuntu, with GNOME.
 
replying to Bodhi next.

---

### Post by kuuser on 2008-08-07
> **bodhi.zazen said:**
> You can not check a mounted file system ...
 *I'm looking into what this means in older postings. Sorry learning a new language here.  Found informative  [http://www.dedoimedo.com/computers/install_kubuntu.html](http://www.dedoimedo.com/computers/install_kubuntu.html) *
 
so, boot a live CD
 *I'm researching where to obtain such a precious creature...*
 
open a terminal and enter :
 sorry, *looking up what a terminal is...yes I am an absolute beginner, but am Learning, with all of your help.  *
 
```
sudo e2fsck -C0 -pfv /dev/sda5
```
 
If that fails :
 
```
sudo e2fsck -fvy /dev/sda5
```
 
Modify that command if sda5 is not your root partition.
 
*Researching how to _first_ do a backup by reading my own computers tutorials (I'm learning)* then I'll proceed with above instructions.
 
*Do we consider this case solved, at this point?  I'm following up on all this.*
=========
 
Usually this problem is indicative of a potentially failing HD. If that works make sure your data is backed up and backups are working.
*I'll have it looked at.  Thank You.*

---

