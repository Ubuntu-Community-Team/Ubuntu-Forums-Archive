---
title: "Hardy frequent freezes and USB issues"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-31
I am using Hardy amd64
It frequently freezes up, like for example, often when I click on any video file, the Totem window opens and everything freezes. I can move the mouse pointer but nothing responds, not even Ctrl+Alt+Backspace
Today, when I clicked on a new IM on pidgin, Hardy froze again.
I don't remember doing a Kernel upgrade.
[codeglade@Mean-Machine:~$ uname -a
Linux Mean-Machine 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux
glade@Mean-Machine:~$ [/code]

Am I the only one having these problems?

Also, after I wake the PC from suspend, my USB devices don't function until I reboot the PC. Is this a bug?

---

### Post by InfinityCircuit on 2008-05-31
What kind of graphics card are you using?  Your drivers and x.org might not interact well so you might have to downgrade.

---

### Post by sayakb on 2008-05-31
Hardy freezes on my laptop which has an Intel onboard GPU (GMA950). I guess that doesn't even need extra drivers..

---

### Post by shifty_powers on 2008-05-31
some intel chipsets are notorious for not working well with ubuntu...

---

### Post by CameO73 on 2008-05-31
I have had no stability problems with Hardy (yet). Is it only with certain applications or more random? Is it after a specific period (say, 1 hour after boot) or random? What kind of hardware are you using (especially video and memory size)?

Oh, I see your running the 64-bit version ... I'm using the i686 one.

[edit]
You could take a look in [this thread](http://ph.ubuntuforums.com/showthread.php?t=765510&page=12). Two possible solutions are mentioned: disabling the PowerNow daemon or installing the 2.6.25 kernel from Intrepid (though that last one will probably cause you more troubles...)
[/edit]

---

### Post by sayakb on 2008-05-31
Well, I can't disable compiz :( 
Also, Intel is the only natively supported GPU for Ubuntu.. we can atleast expect Intel to work fine, can't we :(
Does this have a solution?

---

### Post by shifty_powers on 2008-05-31
does

[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

apply?

---

### Post by sayakb on 2008-05-31
```
glade@Mean-Machine:~$ compiz --replace &
[1] 23573
glade@Mean-Machine:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```
And intel graphics are not blacklisted methinks.. :)

---

### Post by shifty_powers on 2008-05-31
well yes, some are. thats the point of that post ;)

---

### Post by sayakb on 2008-05-31
Oh right.. sorry didn't notice (how careless I am!);)
No, I have i945 graphics.. So no blacklisting problem I guess..

---

