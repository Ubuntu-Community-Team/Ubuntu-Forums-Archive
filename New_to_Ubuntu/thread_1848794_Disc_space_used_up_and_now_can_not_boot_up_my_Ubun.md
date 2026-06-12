---
title: "Disc space used up and now can not boot up my Ubuntu partition"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by Blackbettynepal on 2011-09-23
I am relatively new to Ubuntu as my friend recently put it on my computer as a partition within windows. I love it, but now I got a few messages saying I have very little disc space left. I had just recently downloaded "drop box" and was planning to get rid of it to free up my disc space. However, I shut my computer down before i got around to doing it and when I rebooted it up I got the following message.

"Your screen, graphics card, and input device settings could not be detected correctly. you will need to configure these yourself."

I clicked ok and tried the options given to me. I tried running it on Low Graphics mode, but that never got past a black screen with a courser. 

Does anyone have any advice for me on how to get back into my Ubuntu to empty up some disc space? Or should I create space by deleting files in my non-ubuntu side of the partition? Or is this a separate problem then a lack of disc space?

Thanks for the help. And please remember that I am a new Ubuntu user and thus need simple instructions. :)

---

### Post by sunRAHH on 2011-09-23
how far does the boot up sequence take you? if you can get into a terminal (e.g. Ctrl+Alt+1) you can log in and delete some stuff via the command line. then do a reboot.

maybe it helps

---

### Post by Blackbettynepal on 2011-09-23
Thanks SunRAHH. I can get into the command terminal and have signed in, but I do not know how to delete things via the command line.

---

### Post by nothingspecial on 2011-09-23
Hi,

First type

```
ls .local/share/Trash/files/
```

and check there is nothing in your trash that you might want. If not then delete the contents of your trash like so.
```

rm -r .local/share/Trash/files/*
```

See if that frees up enough space to boot.

---

### Post by HermanAB on 2011-09-23
Howdy,

In an emergency, you can delete everything in /var/log to make space:
$ sudo rm -rf /var/log/*

BUT, BUT, BUT, be sure not to make a typo with that command.

---

### Post by Elfy on 2011-09-23
Empty the apt cache 

sudo apt-get clean


BUT - if you're partition is small you'll need to deal with that in the end - likely this will happen again.

---

### Post by CharlesA on 2011-09-23
> **HermanAB said:**
> Howdy,

In an emergency, you can delete everything in /var/log to make space:
$ sudo rm -rf /var/log/*

BUT, BUT, BUT, be sure not to make a typo with that command.

Thanks for including the warning. ;)

I prefer using rm -ri so that it prompts for each file deletion. Just to make sure you are deleting what you think you are deleting.

> **forestpiskie said:**
> Empty the apt cache 

sudo apt-get clean


BUT - if you're partition is small you'll need to deal with that in the end - likely this will happen again.

That would probably help too.

I sometimes just clear out all the *.deb files from /var/cache/apt/ but that doesn't clear all that much space.

---

### Post by Elfy on 2011-09-23
> **CharlesA said:**
> I sometimes just clear out all the *.deb files from /var/cache/apt/ but that doesn't clear all that much space.

It can be enough to get in to do other clearing - been there :)

---

### Post by CharlesA on 2011-09-23
> **forestpiskie said:**
> It can be enough to get in to do other clearing - been there :)
This is true. :)

---

