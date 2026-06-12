---
title: "REISUB Disabled in 14.04?"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Wheel on 2014-04-27
Hello,

For some reason, the Alt+PrtScn +REISUB command no longer works.

I discovered this years ago and it has been an occassional Godsend.  Sure would like to get it enabled once again.

Is there any way to re-enable this? 

(Although I am able to execute this safe reboot in a Virtual Terminal. (Tested when the system was NOT frozen.)
However, both the R and the E yield a return of "This sysrq operation is disabled".  But it DOES reboot.)

---

### Post by egeezer on 2014-04-27
I know that  cat /proc/sys/kernel/sysrq returns the number 176 in 14.04.  That's strange, because in Wikipedia there's the note that:  On newer kernels (since 2.6.12[5]), it is possible to have a more fine-grained control.[6] On these machines, the number written to /proc/sys/kernel/sysrq can be zero, one, or a number greater than one which is a bitmask indicating which features to allow. Possible values are: 0 - disable SysRq  1 - enable SysRq completely  >1 - bitmask of enabled SysRq functions:  2 - control of console logging level  4 - control of keyboard (SAK, unraw)  8 - debugging dumps of processes etc.  16 - sync command  32 - remount read-only  64 - signalling of processes (term, kill, oom-kill)  128 - reboot/poweroff  256 - nicing of all RT tasks           Edited to add: I suppose you could open the file as root and replace the 176 with 1.  I But in a virtual machine first, of course!

---

### Post by ajgreeny on 2014-04-27
I believe this is a long term problem, though not always consistent in OSs.

See [http://ubuntuforums.org/showthread.php?t=1890355](http://ubuntuforums.org/showthread.php?t=1890355) for some possible ways round this.

---

### Post by Wheel on 2014-04-27
Thanks egeezer & ajgreeny,

Just for fun, I ran cat /proc/sys/kernal/sysrq.
The return was "No such file or directory".

So I looked through the file system and I did find sysrq living in that very folder.  Hmmm...

The really odd thing is that inside of that kernal folder are about 50 files and another 6 folders, each with a few more files.  Every single file in this entire folder is a ZERO BYTE sized file.  That seems pretty weird.

So it's kind of tricky to edit content that isn't there! (I haven't mastered inter-dimensional travel either.) ;)

Well, this is a good time for me to beef up my knowledge of Virtual Terminal use (not that I'll be able to use it to fix this particular problem, but this is something I've left on the back burner for too long).

Some good info in that link, ajgreeny. Your observation is right.   Widespread, but inconsistent.

Is it possible that all those empty files are intentionally empty?
Or maybe the iso I burned & installed was faulty/incomplete in some way.  I did not (nor do I know how to) run any sort of checksum type of validity test.  More stuff to learn.  I'll just keep reading until my head hurts.

---

### Post by Impavidus on 2014-04-28
> **Wheel said:**
> 
Just for fun, I ran cat /proc/sys/kernal/sysrq.
The return was "No such file or directory".

So I looked through the file system and I did find sysrq living in that very folder.  Hmmm...

Because it's kern**e**l, not kern**a**l.

/proc is a pseudo-filesystem. There are no real files in there, but it's an interface to variables in your running system. So it's all normal what you're seeing there.

---

### Post by Wheel on 2014-04-28
> **Impavidus said:**
> Because it's kern**e**l, not kern**a**l.

/proc is a pseudo-filesystem. There are no real files in there, but it's an interface to variables in your running system. So it's all normal what you're seeing there.

Thanks for that info.  I fixed my misspelling and retried the cat command.
This time it did return 176 as mentioned in an earlier post.

But I haven't had any luck in editing this to be 1 instead of 176.

In a virtual terminal, I tried sudo gedit /proc/sys/kernel/sysrq


I see this return:
error:XDG_RUNTIME_DIR not set in the environment
gedit:3741):Gtk-WARNING **: cannot open display:

I have no clue what any of that means.

So I took a look trying to edit it through the "normal" terminal.
I tried the same sudo gedit /proc/sys/kernel/sysrq 
Gedit window opens and I see this appear in terminal:

(gedit:3907): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

EDIT: The smiley face above is suppossed to be a colon; not sure why it copied as a smiley...?

And when I edit the sysrq file, I can't save it.
This is what shows in the Gedit window:

Could not create a backup file while saving /proc/sys/kernel/sysrq 
The "Save Anyway" button yields the same error.

My only option is to close without saving.  So no changes made.

I thought that if I owned the file, it would allow me to edit it, but "chown" didn't help.
In terminal--chown joe /proc/sys/kernel/sysrq  Yields: Operation not permitted

Any more thoughts or explanation would be greatly appreciated.

---

### Post by Sir_Ismicoo on 2014-04-28
You should be able to regain full control of SysRq by editing the file etc/sysctl.d/10-magic-sysrq.conf and changing the line *kernel.sysrq = 176*  to *kernel.sysrq = 1* and then rebooting after saving.

---

### Post by Impavidus on 2014-04-28
On pseudofilesystems things may work a bit differently.

Using sudo gedit can be a bit dangerous as it could cause some files in your home directory (.Xauthority, I think) to be root-owned, preventing you from logging in the next time. So we have gksu instead. But the usual way to write to "files" in /proc is using terminal commands```
echo "value" | sudo tee /proc/file
```Assuming of course that the normal user has no write access to /proc/file and root has.

In general, that is. I don't know whether it is desirable in this case.

The forum software converts some codes with : or ) etc. to smilies. Under the input box (not the quick reply) you can find the additional options. You can click "Disable smilies in text".

---

### Post by Wheel on 2014-04-28
@impavidus
Thanks.  Before today I didn't even know there *were* pseudo-filesystems. 
Somewhere along the way (a few hours back now) I did use gksu when sudo was not helping.  It yielded essentially the same errors (I don't remember exactly).

I took a look in my home folder and .xauthority is still owned by me as are all of the other files in there.
I did see however that 2 folders (.dbus and .gvfs -- both empty folders) are showing as owned by root.
I'm not sure if these were previously set as such or if this is the result of this tinkering.  I just did not notice that before.
I chown both back to my ownership (Hey, it's MY home foder, right?)

@Sir_Ismicoo
Outstanding tip!
While I did have a minor issue or two, this has returned functionality to alt+sysrq+REISUB.
After the edit of 10-magic-sysrq.conf, I tested it.
At "E" I got a message about running in Low Graphics Mode (never saw this before, but I have read about this in other threads). I completed the rest of the sequence and...nothing...
So I repeated it.  Still nothing. Then typed cntl+alt+del and it rebooted! 
NICE!
Except it booted me back into a blank desktop.  No top bar; no launcher. Uh-oh....
Rebooted (via REISUB) and returned to my normal desktop.  Yay!
So then I changed my graphics driver (Nvidia) from Nouveau to a recent proprietary driver. 
Rebooted normally.
And I re-tested the command.
Now I'm no longer seeing that Low Graphics Mode message and the REISUB trick works.
But I must run the REISUB sequence twice, followed by ctl+alt+del.
But that works.
Thanks again

---

### Post by s1wood on 2014-04-29
I know this is marked SOLVED but I have the same problem and I don't understand how you solved it. Could you post a simplified version please?

Susan

---

### Post by Wheel on 2014-04-29
Hi Susan,

Look at post #7.
That's what got my alt+sysrq+REISUB working.

This is what I did, as close as I can remember (I'm near the end of 4 days or so of re-installing 2 OS's and all of each OS's content, so I've done about 100 different things during these past few days, but I'll give you as close to exact as I remember):

The file which has this setting you need to change is sysrq.conf

You need to navigate to this file and open it to edit it.

Open Terminal 
(type ctl+alt+T to open it)

Navigate to /etc/sysctl.d 
(type cd /etc/sysctl.d)

Then type in:
sudo gedit 10-magic-sysctl.d

It'll ask for your Password.  Provide it.
Then the gedit window opens with that file.

The line you need to find is near the bottom. It reads "kernel.sysrq=some number" (Mine was on 176, but it might be something different for you).
Edit your number to read 1.
(The "1" setting should allow for complete function of the sysrq "magic" function.)
Save the edited file.  Reboot the machine.  Should be working.

As you can see from my last post I had to enter the sequence twice followed by ctl+alt+del to engage it.
Not sure why (your experience may be different -- it may work as soon as you do it the first time.) 

But it did reboot me.

Of course I tested this on a machine which was functioning just fine, but it should work on a frozen system. (I've got my fingers crossed there!)

Disclaimer -- I don't understand lots of this; I'm no expert.;)
I find knowlegable people and listen to them.

---

### Post by Sir_Ismicoo on 2014-04-29
You may have encountered this already but just in case, I'll just add that entering your password in a terminal looks like nothing is happening; but it is.

---

### Post by s1wood on 2014-04-30
Thanks, very clear, but when I tried it the gedit file came up blank! 
Looking at the terminal again it warns that I am not root which maybe why it wouldn't show the file.
I think perhaps I'll stick with 12.04.....

Susan

---

### Post by Wheel on 2014-04-30
Are you sure you used "sudo" prepended to the command in terminal?

I've had terminal thumb its nose at me many times because of small typos, too many spaces, or some other syntax error.
Please re-try the command once again.

Just to see what would happen, I opened terminal, navigated to the /etc/sysctl.d folder and ran gedit 10-magic-sysctl.d (without using sudo).  Gedit opened 10-magic-sysctl.d. to a blank screen.  Zero content.

One difference here (not sure what the difference means): I saw the "You don't have permission to do this" message at the top of the gedit window rather than in terminal.

The use of "sudo" is what grants you temporary root privilege (along with providing your password when requested)
This should allow you to edit the file.

You may also try using "gksu" in place of "sudo".

Here's a decent primer on sudo & gksu if you care to read.  It outlines different situations when different versions of obtaining root privilege are needed:

[http://ubuntu.paslah.com/sudo-and-gksu/](http://ubuntu.paslah.com/sudo-and-gksu/)

Good luck!

---

### Post by Wheel on 2014-05-02
Just a quick follow-up.

I've Had a chance to test REISUB while my system was actually frozen.

It works!

Of course, as I mentioned earlier, I had to invoke that sequence twice followed by Ctl+Alt+Del (still don't know why), BUT IT WORKS!

---

