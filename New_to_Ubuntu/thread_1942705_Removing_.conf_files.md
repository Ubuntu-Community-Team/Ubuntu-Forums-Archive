---
title: "Removing .conf files"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by PashConscious on 2012-03-18
Hello all,

 I am a Windows veteran and have recently installed Ubuntu 11.1 (like yesterday) and due to my inquisitive and hasty nature I have buggered it up already.

Was trying to create a driver .config file for my ALC1200 RT Sound card and now it won't shutdown :( I used;

sudo gedit /etc/modprobe.d/hda_intel.conf

I then typed blah blah *typical nonsense text-based system file* and it made no difference. Sound may be a hardware problem however so NM.

Point is that now I don't have permission to delete etc/modprobe.d/hda_intel.conf and I can't find a command to do so for love nor money.

Please help me stop being a Lvl 1 Human :D thank you

---

### Post by Carborundum on 2012-03-18
Did you try 'sudo rm /etc/modprobe.d/hda_intel.conf'?

Regardless, it seems strange that this file would keep your machine from shutting down. What exactly is in the file, and what happens when you attempt to shut down?

---

### Post by PashConscious on 2012-03-18
rm was probably what I was looking for. 

the config file contained ----- options snd-hda-intel model=auto probe_mask=1

I can only assume its this because its the only real under-the-hood tinkering i've done with it

it just hangs on the ubuntu logo screen. Am i just being impatient?

---

### Post by PashConscious on 2012-03-18
sudo rm worked. Just need to get to grips with commands and syntaz and stuff :D

---

### Post by PashConscious on 2012-03-18
yh definitely was that, just removed it and shut down in a flash. Thanks boss, you're a star

---

### Post by winh8r on 2012-03-18
Always be extremely careful when running the ```
sudo rm
``` command as one little typo can render your system unusable.

If you are unsure of any command and exactly what it does, do not run it until you have checked up on it.

There are numerous resources here:

[http://ubuntuforums.org/showthread.php?t=1909108]("http://ubuntuforums.org/showthread.php?t=1909108")

for learning about commands.

Also take a look at the "Make using the terminal easy" link in my sig below for an excellent resource for beginners and experienced users alike.

Hope this helps.

---

### Post by PashConscious on 2012-03-18
^^^ also awesome, cheers :D

---

### Post by ajgreeny on 2012-03-18
I would suggest that rather than using the **rm** (remove) command you use the **mv** (move/rename) command with for example```
sudo mv filename.conf filename.confbak
```then if things go completely wrong and you appear to have hosed the system, you can always boot to a live system and reverse things back to the original, which you can not do if you remove the file.

---

