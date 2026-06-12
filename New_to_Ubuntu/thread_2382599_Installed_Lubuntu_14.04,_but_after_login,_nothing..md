---
title: "Installed Lubuntu 14.04, but after login, nothing..."
date: 2018-01-15
forum: New to Ubuntu
---

### Post by clfry on 2018-01-15
I am 100% new to Ubuntu... I installed Lubuntu 14.04 on an old Toshiba laptop (1.6 Mhz, 512MB, 80GB) alongside Windows XP. When I boot, select Ubuntu from the menu, then login; it accepts my login, but then only displays a command prompt: 
(login name@computer name):~$

I can only assume this is not normal... Where do I go from here?

---

### Post by RobGoss on 2018-01-15
I believe you're using a unsupported version of Lubuntu please try a supported ISO like 16.04 and see how that works

---

### Post by clfry on 2018-01-15
> **RobGoss said:**
> I believe you're using a unsupported version of Lubuntu please try a supported ISO like 16.04 and see how that works
I don't believe this machine meets the system requirements for 16.04, but should be ideal for 14.04... from what I've been reading, I'm not even sure 16.04 will install.

---

### Post by RobGoss on 2018-01-15
I think you should bump that Ram up to a least 2-GB that way you will be able to enjoy Lubuntu with out having to much lagging, Of course it always depends what graphic card you're using as well

---

### Post by clfry on 2018-01-15
> **RobGoss said:**
> I think you should bump that Ram up to a least 2-GB that way you will be able to enjoy Lubuntu with out having to much lagging, Of course it always depends what graphic card you're using as well

I haven't cracked the back of this laptop yet, but I would be surprised if it would take more than 1GB (it may be maxed out at 512). I don't really want to invest any money in this old machine, just wanted to use it as a clean, simple internet/email and light-duty task tool.

Regardless, I let it update to 16.04, we'll see what happens.

---

### Post by cruzer001 on 2018-01-15
Sounds like you need an ultra-lite system.  Bodhi Linux claims to run on as little as 128M of ram.  I have not used it, but have read good reports about it through the years.

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

And there are other ultra-lites like Puppy Linux.

---

### Post by DuckHook on 2018-01-15
Lubuntu 16.04 should run on your system. I have ancient systems with almost identical specs and Lubuntu runs on them. Lubuntu itself is not resource heavy (on my machine it takes up 192 MB of main memory). It's apps like modern web browsers that are. So, while you may be able to run the OS itself, your experience doing even the most basic tasks will likely be frustrating.

OTOH, Puppy is a fine distro. Nothing wrong with trying it out. Bodhi also has a soft spot in my heart, but be aware that it is based on Ubuntu, so you won't realize a lot of savings over Lubuntu.

---

### Post by sidzen2 on 2018-01-16
+1 DuckHook -- Puppy Linux is likely your best choice, especially since the old Toshiba is not worth investing in further.  antiX would work, but likes at least a gig of RAM.  So go with a 32bit pup.

---

### Post by RobGoss on 2018-01-16
+1 DockHook

I also have older machines that run Lubuntu just fine, But I moves away from the 32 bit for many reasons and added more Ram to all my older machines for better performance. At least 2-gig of Ram if possible  would do well just my opinion

---

### Post by Rex Bouwense on 2018-01-16
Adding more RAM here will never hurt.  I keep a very old Dell Inspiron 1000 (circa 2004) running with Lubuntu as its OS (16.04.3).  It came with 256 MBs of RAM and I added another 256.  While it is not the fastest thing, it does function well and has done so for fourteen years.  I just keep it around because it was my first Ubuntu machine and to show our newly converted that an old machine is not necessarily something that can only be used as a door stop.  If Linux can breath life into one this old, it certainly can speed up your 3 or 4 year old model.  So clfry continue to use it but do install 16.04.3 on it since Lubuntu 14.04 has reached End Of Life (back in April 2017).  Lubuntu LTS releases are only supported for 3 years unlike Ubuntu which are supported for 5.

---

### Post by kate.t on 2018-01-16
Rex Bouwense,

I'm a newbie, too, and I'm a bit confused.

I thought LTS releases get 5 years of support. Wouldn't 14.04 still be supported (until 2019)?

Thanks in advance,
Kate

---

### Post by clfry on 2018-01-16
Thanks for the input; looks like the 16.04 update fixed whatever it was, but it seems very lethargic compared to XP on the same machine, so I'm going to look into the above suggestions.

---

### Post by vasa1 on 2018-01-16
> **kate.t said:**
> Rex Bouwense,

I'm a newbie, too, and I'm a bit confused.

I thought LTS releases get 5 years of support. Wouldn't 14.04 still be supported (until 2019)?

Thanks in advance,
Kate
I'm posting [a link about Ubuntu Mate 16.04]("https://ubuntu-mate.community/t/why-can-t-we-get-5-years-support-for-16-04/5098/12") but the same logic may apply to other flavors which have 3yr LTS instead of the full 5yr LTS. From there: > 

What does this mean? We will support Ubuntu MATE 16.04 up to the 16.04.5 release. After that, the Ubuntu MATE bits won't get updates and fixes but the underlying Ubuntu base will. &#65279;I'm guessing the same applies to Lubuntu 1_4_.04 (and the Lubuntu devs may not provide support for the LXDE/Lubuntu specific bits since the three years have passed). I can't say for sure because I moved to 16.04!

On the bright side, not much changes happen to LXDE; it's fairly stable. One issue users staying with Lubuntu 14.04 may face is that of audio with the Firefox browser because Firefox has dropped ALSA support and Lubuntu 14.04 has only ALSA. See [https://ubuntuforums.org/showthread.php?t=2355092](https://ubuntuforums.org/showthread.php?t=2355092) for workarounds or just post a question in the support forum here for help from our audio experts!

---

### Post by cruzer001 on 2018-01-16
> **DuckHook said:**
> Lubuntu 16.04 should run on your system. I have ancient systems with almost identical specs and Lubuntu runs on them. Lubuntu itself is not resource heavy (on my machine it takes up 192 MB of main memory). It's apps like modern web browsers that are. So, while you may be able to run the OS itself, your experience doing even the most basic tasks will likely be frustrating.

OTOH, Puppy is a fine distro. Nothing wrong with trying it out. Bodhi also has a soft spot in my heart, but be aware that it is based on Ubuntu, so you won't realize a lot of savings over Lubuntu.

Yep, Lubuntu would be first choice.  I recently installed Lu on a 11 year old laptop (PentiumM) and it was very fast, but it did have 2G of ram.

I just wanted to lay out other options on the table.  And really my next choice would be LXDE, but its pretty bear bones (software wise) out of the box and helpful to know what packages are better for keeping it light.

---

### Post by kate.t on 2018-01-16
vasa1,

Thanks for the thorough explanation! :KS

Kate

---

