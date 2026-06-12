---
title: "No sound?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by FLCL on 2008-07-28
after i installed virtualbox, and restarted my system i lost all my sound.

I get these messages wen i click the audio icon.
[IMG]http://imagedash.com/images/jdv1217187097x.png[/IMG]

[IMG]http://imagedash.com/images/arx1217140254z.png[/IMG]

This is the icon shown:
[IMG]http://imagedash.com/images/opt1217140116i.png[/IMG]

Can anyone please help me get audio back? :(

---

### Post by ChildOfMana on 2008-07-28
Did you by any chance install something called virtualbox-ose-modules?

---

### Post by FLCL on 2008-07-28
Yeah, i think so. I followed this help document. Im running Hardy 8.04
[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

---

### Post by ChildOfMana on 2008-07-28
Okay. I had more or less the same problem. Fairly easy to fix though so let's have a go...

Firstly though, can you type; 

> sudo uname -r

into a terminal to see what kernel is currently in use?

Post the output here.

---

### Post by FLCL on 2008-07-28
I get  2.6.24-19-generic

---

### Post by ChildOfMana on 2008-07-28
Hmmmm? That's as it should be - so your problem doesn't lie with the kernel version (which mine did).

Back to basics!

Have you tried a complete purge and re-install?

---

### Post by ChildOfMana on 2008-07-28
> Have you tried a complete purge and re-install?

Sorry, I should be more specific - I meant a complete purge of the kernel module you installed.

---

### Post by FLCL on 2008-07-28
No, thats my last resort. Im trying to avoid that bit.

---

### Post by FLCL on 2008-07-28
Do you mean the sound module? Or something else?
If it's the sound module, i believe i have, but i could be mistaken.

---

### Post by ChildOfMana on 2008-07-28
Okay you might be best checking this thread:

[http://ubuntuforums.org/showthread.php?t=855544](http://ubuntuforums.org/showthread.php?t=855544)

Check the posts by kansasnoob and see if that turns up any useful info.

I'm afraid I'm no authority on sound in Linux (or anywhere for that matter!!).

It sounded at first like you had exactly the same problem I once had but it seems yours is different.

However, post back here if you can't find a more gentle solution and I'll help you to purge and remove the offending packages.

After that you can check this thread [http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745) out for an alternative way to install and configure virtualbox (which worked for me post-sound crisis).

Sorry I couldn't be of more help.

---

### Post by ChildOfMana on 2008-07-28
You could also try here too;

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Hope this helps.

---

### Post by FLCL on 2008-07-28
alright, thank you. Ill check back if i cant get anything

---

### Post by kitplayer on 2008-07-28
Comprehensive Sound Problem Solutions Guide v0.5e
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


posted by ChildOfMana

is the best audio solution ive found so far. easy to follow, use, and fixed my prob instantly.

this should be highlighted as the best audio solution for newbies as i have only been using ubuntu for 15mins

---

### Post by FLCL on 2008-07-28
Meh..i already followed it and it didnt work. Tried compiling my own drivers, that failed too.Posted in the thread, no reply yet, it's on page 106.  This is a disaster.

What could be the cause of this problem? 
Some specs: Asus A7V400-MX mobo, using onboard sound. Soudmax is what the card uses i guess. 
> -multimedia UNCLAIMED
description: Multimedia audio controller
product: VT8233/A/8235/8237 AC97 Audio Controller
vendor: VIA Technologies, Inc.
physical id: 11.5
bus info: pci@0000:00:11.5
version: 50
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0

Also running the command "aplay -l"
returns the following: 
> aplay: device_list:205: no soundcards found...

So yeah. Please somebody help me. It's horrible without sound.

---

### Post by FLCL on 2008-07-28
oops. *double deleted*

---

### Post by FLCL on 2008-07-28
bump

---

