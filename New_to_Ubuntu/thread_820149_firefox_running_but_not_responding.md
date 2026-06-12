---
title: "firefox running but not responding?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by scholzilla on 2008-06-06
I recently "upgraded" to the 32 bit Hardy to take care of some wireless problems I was having with the 64 bit distro. Firefox doesn't work for me. When I try to launch it, I get a message that says:

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

This is when I wish I had a "no it's not" button that would override everything. This message appears even after restart upon the initial launch of firefox. I've tried *complete* removal of firefox and reinstallation and get the same problem. Strangely, even after I "completely remove" firefox via synaptic, firefox-3 is still on my box. I know there are multiple versions (firefox, ff-2, ff-3) and none of these is shown as installed on synaptic, yet <locate> in term shows ff-3 is still there in my /etc, /bin, and so on folders. Very irritating.

Help?

---

### Post by aysiu on 2008-06-06
Try Alt-F2 ```
killall firefox-bin
```

---

### Post by scholzilla on 2008-06-06
All i get is:

firefox-bin: no process killed

Just for added info, I have no problem using epiphany for web browsing or any other app. Just firefox.

---

### Post by Phonan on 2008-06-06
Open your system monitor (System-> Administration-> System Monitor) and look for any processes with "firefox" in them (be careful not to kill anything you don't know about). Select each individually and click "End Process" for each. Hope it works!

---

### Post by cariboo on 2008-06-06
You could still have a lock file. Search ~/.mozilla for lock and just delete it.

Jim

---

### Post by DM was on fire! on 2008-06-06
Firefox is evil.
Stay with Epiphany. XD

With all kidding aside, whenever I have that problem, I do what Phonan says. ^^

---

### Post by scholzilla on 2008-06-06
Thanks for the responses. System monitor doesn't show any firefox processes running. Jim, how do I find that lock file you're talking about? If I do <locate /.mozilla> I get a million file output, but don't see a lock file. What is it's name exactly?

---

### Post by aysiu on 2008-06-06
I think this problem is specific to Firefox 3, and I haven't found a satisfactory solution to it yet (apart from rebooting).

---

### Post by scholzilla on 2008-06-06
thanks, but rebooting doesn't work for me either, which makes this even stranger to me.

---

### Post by aysiu on 2008-06-06
Try deleting the ~/.mozilla/firefox/*profilename*/.parentlock file

---

### Post by SteveNorman on 2008-06-06
```
ps auxwww | grep firefox
```

```
kill (whatever job number you get)
```

I always start firefox like this:
firefox &

becuase it gives you a jobnumber to use if you need to kill it

---

### Post by alienexplorers on 2008-06-06
Just create a new firefox profile.  start firefox from terminat with the command:
> firefox -profilemanager
follow the prompts and start firefox from the profile manager.
stop firefox and load as normal.

---

### Post by scholzilla on 2008-06-09
deleting the ~/.mozilla/firefox/profilename/.parentlock file didn't work for me. Somehow I missed your response, alienexplorers, so I can't say if this works. I ended up just locating all files related to firefox and deleting them as root. Then I reinstalled firefox. This brute force approach worked. Hopefully I didn't screw anything else up in the process, but so far so good.

---

### Post by cariboo on 2008-06-09
Just for future reference the lock file is locate in: .mozilla/firefox/xxxxxx.defautl and it is just called **lock**, xxxxxx.default will be your default directory. I'm a bit lazy so I use Midnight Commander for a lot of functions, it is a clone of Norton Commander from back in the pre-Symantec days. It is available in the repositories as mc.

Jim

---

### Post by svachalek on 2008-08-04
My computer crashed and I had to do a hard reboot and after coming back up Firefox would just not run no matter what I did until I deleted the .parentlock file, so thanks for that tip, I think.  Now unfortunately I have no bookmarks and other aspects of the profile seem to be messed up so I think I'm going to have to delete and recreate the profile, but I'm gonna blame that on the crash and not the parentlock.  Still, I recommend trying that only as a last resort.

---

### Post by grimpeur on 2011-11-13
I have this problem since a couple of month with firefox 3.6.24 Of course I kill the application in order to restart it.
I tried to create a new profile, without success. 
I tried also this code
```
sudo mv ./.mozilla/firefox/profiles.ini ./.mozilla/firefox/profiles.old
``` nothing occured. Also deleting the file lock was not useful.
What shall I do? Please simple step-by-step instructions: I am still a newbie (after 3 years..)

---

