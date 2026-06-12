---
title: "Can't Start Ubuntu &quot;No Resume Image&quot;"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by oranges on 2008-05-04
Hello! I recently upgraded ubuntu to 8.04 *Hardy Heron* and have had the usual trifect of troubles - trouble, trouble, and more trouble!

I was then trying to fix a problem with my sound, which had stopped working after I upgraded (despite ubuntu recognizing my sound card). I was following some help I found [post=4810371]here[/post], and after finishing all the commands with no trouble, I went to reboot and got the following after the startup screen:

```
kinit: trying to resume from dev/disk/by-uuid/[a-bunch-of-numbers-and-letters]
kinit: No resume image, doing normal boot...
```

And then it loads BASH and, yeah, while it's a fine interface... can anyone help?

Oh, and the sound still doesn't work. :X

---

### Post by gjj391 on 2008-05-04
Did you find a fix to this? I have the same problem

---

### Post by oranges on 2008-05-04
I found a thread in the Feisty Fawn development forum with the same issue and several happy customers, but it didn't do me any good.

You might want to take a look anyways. [thread=385869]Here[/thread]. [post=4407352]Here[/post] is another thread with the same thing.

---

### Post by UnknownFear on 2008-05-04
I had this problem when I upgraded to 8.04, so I just uninstalled Ubuntu and reinstalled it with 7.10. I want to upgrade o 8.04.. but I'm afraid I'll get the same problem you are all having with the monitor turning off :(

---

### Post by fontenot_1031 on 2008-05-11
I have the exact same problem too on Hardy.  Arrgh this is so irritating.

---

### Post by louieb on 2008-05-11
> **oranges said:**
> 
```
kinit: trying to resume from dev/disk/by-uuid/[a-bunch-of-numbers-and-letters]
kinit: No resume image, doing normal boot...
```

Thats a normal startup message. Its just checking to see if you put the PC in hibernation.

try a couple of things an see what messages pop out. 
```
startx
```or 
```
/etc/init.d/gdm start
```

---

### Post by erginemr on 2008-05-11
@louieb,

I was just about to say the same thing. This is a normal message for resume check from possible hibernation. 

You should look for the other messages that will reveal the cause of failure for the graphical desktop.

---

### Post by WombatForest on 2008-07-20
Thank you so much Louieb.
This problem was stumping me big time.
I still don't know why I had the problem in the first place but the startx command allowed me to access the desktop again and get my data off the machine. Thank you very much 
Wombat

---

