---
title: "finger-reader problem lenovo t60"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by cseljatib on 2008-06-30
hello there

i am using ubuntu 8.04, and i have followed the following step-by-step ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60#The_Fingerprint_Reader](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60#The_Fingerprint_Reader)) regarding how to set up the finger reader of a lenovo t60 under ubuntu.
i did follow the same tread in the past for the same laptop but with a different version of ubuntu [it worked perfectly], but now, after that i finish the configuration and i need to restart ubuntu, as soon as i enter my username, ubuntu just keep rebooting over and over. I mean i enter my username, enter, then ubuntu goes black screen for some seconds, and give me again the same screen where i have to type my usename.

Somehow, i was able to just login with the terminal [selecting recovery mode, and then select drop to shell mode or someting like that], then itype my name, and then the terminal ask me for my finger, which is successfully accepted and then i am able to shee my folders etc, neverthelles, when i tried to do it in normal start [not terminal], it just gave me the same problems

somebody can help me??

is there any way that i can uninstall all this???, and just return as i was before?

PLEASE help me

---

### Post by sayakb on 2008-06-30
[http://ubuntuforums.org/showthread.php?t=503928](http://ubuntuforums.org/showthread.php?t=503928)

---

### Post by cseljatib on 2008-06-30
?
i cannot see how to uninstall what i have done in that tread?, please give me some more details, in a basic-manner please, i am not an expert at all
thanks

---

### Post by Inxsible on 2008-06-30
Its funky that the finger-print reader works in CLI mode and not in GUI. once you login to the CLI...can you issue a ```
startx
``` command and start the GUI. If yes, then its probably interfering with the GDM....if that doesn't start the GUI then its probably interfering with xorg.

Unfortunately, I don't have a solution.

You can uninstall those packages by doing a ```
sudo apt-get purge *package-name*
```

---

### Post by cseljatib on 2008-06-30
hi 
i tried with "startx" and it worked, nevertheless, if i restart the problem is still there, then i preferred to uninstall this thing, the only thing that i did was
$sudo apt-get purge bioAPI

and then 
$sudo gedit /etc/fstab
and delete the line with 
none /proc/bus ......

now i am back as i was before, thanks

but i wonder if i should uninstall other things, and more important: how can i activate the finger-reader capability of lenovo t60 under ubuntu 8.04?

---

### Post by Inxsible on 2008-06-30
> **cseljatib said:**
> hi 
i tried with "startx" and it worked, nevertheless, if i restart the problem is still there, then i preferred to uninstall this thing, the only thing that i did was
$sudo apt-get purge bioAPI

and then 
$sudo gedit /etc/fstab
and delete the line with 
none /proc/bus ......

now i am back as i was before, thanks

but i wonder if i should uninstall other things, and more important: how can i activate the finger-reader capability of lenovo t60 under ubuntu 8.04?Glad that it works for you.


Unfortunately I have no clue about getting fingerprint readers to work. Never had one on my machines, so never bothered to look it up :)

You will have to wait for someone else to answer that :)

---

### Post by PinkFloyd102489 on 2008-06-30
[http://ubuntuforums.org/showthread.php?t=760018&highlight=fprint](http://ubuntuforums.org/showthread.php?t=760018&highlight=fprint)

Fingerprint reading in Ubuntu using Fprint.

---

