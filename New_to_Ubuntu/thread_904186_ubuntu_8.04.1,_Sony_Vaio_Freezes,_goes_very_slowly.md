---
title: "ubuntu 8.04.1, Sony Vaio: Freezes, goes very slowly"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by ideaton on 2008-08-29
Hey guys, 

I installed the newest version of Ubuntu on my Sony Vaio VGN-S580 today.  installation went very smoothly, and I have to say, I'm very enthusiastic.  But, suddenly I can't do *anything*.  

[I should say that I haven't installed any codecs: I installed Ubuntu on a completely blank hard drive, no partitions.]

I went from System: Appearance Preferences: Visual Effects.  There are three choices---no effects, moderate effects, lots of effects (can't remember exactly and can't look).  

I clicked on the most graphics intensive choice.  Immediately I was prompted to install my nvidia driver.  Okay, I thought, no prob.  I clicked obligingly and the driver was installed.  Upon completion of the installation, I restarted the computer.  

When it booted back up, I tried again to set my system to the most graphics-intensive visual effects setting.  It went ahead and let me choose that setting, but, now, I can't do anything.  The computer is not completely frozen (inasmuch as I CAN move the cursor around, haltingly), but, I can't open any programs (or, if I do manage to open a program, it won't let me do anything with it).

I don't think this can be attributed to a lack of system resources (I expanded my RAM to 2GB).  

Ideally, I'd like to roll back the visual effects, but, since I can't do anything once Ubuntu actually starts, I'm kinda stuck. I'm not super computer proficient and I don't know anything about linux, but, I'm definitely savvy enough to get around. Suggestions, help?  Thanks much in advance!

---

### Post by swoll1980 on 2008-08-29
I have heard there's issues with the sonys running Ubuntu you may want to look into compatibility

---

### Post by ideaton on 2008-08-29
Hey swoll, thanks for the response.  I've looked into it a little bit and haven't seen any serious red-flags for Sony Vaios & Ubuntu at large.  As far as compatibility, I was pleasantly surprised for the most part---wireless and sound are perfect, and the driver for nVidia did *install* without any problems.  

If I can't do anything to fix this problem once Ubuntu loads, is there anything I can do at the BIOS level or before I login?  I'm prepared to reinstall Ubuntu, if it comes down to it, but, I'd like to find out if there's some history of problems with visual effects.

---

### Post by ideaton on 2008-08-29
I'm not attached to visual effects, I should say.

---

### Post by ideaton on 2008-08-29
hey, I think I solved it.  Thanks.

---

### Post by SunnyRabbiera on 2008-08-29
Vaio's are usually considered crap by many and with good reasons, I have heard too many horror stories with them
In terms of DVD players, boomboxes, VCRS and such Sony is mostly top notch but for computers they suck.
If I were you I would just dump the vaio period even without the ubuntu issue... there are far better computer companies out there like HP, Dell, Toshiba, hell I would reccomend a gateway over a vaio... a old crappy tandy > a vaio.
What kind of vaio is this?
Laptop
desktop?
I say its a ripoff in any case.

---

### Post by Nepherte on 2008-08-29
I can't agree with SunnyRabbiera. I have a Sony Vaio as well (see signature). The laptop screen is actually the best I've seen so far, and trust me on this one, I've see a lot of laptop screens (lenovo/ibm, acer, hp, apple, dell). The quality is way ahead of the others. The keyboard types very well too, but I guess you can get that as well with other brands. In my case, the laptop is very sturdy as well; the case is made of carbon though this is not the case with most vaios I must say. If I'd have to say something negative about it, I'd say the technical specs aren't top notch but I wonder who really needs the very latest processor. I've heard a lot of negative things about the warranty as well, but my experiences (and others in my surroundings) were pretty ok.

More importantly, my laptop worked out of the box with Ubuntu (fingerprint reader not accounted for). The only things I had to fix were headphone jack and brightness, which are easily fixed. The rest works, such as wireless (how many wireless issue topics aren't there here on the forums?), suspend and hibernation (same remark as wireless), external monitor, etc...

I really wonder what ghost stories you've heard about vaios. Did you actually use one?

---

### Post by SunnyRabbiera on 2008-08-29
> **Nepherte said:**
> I can't agree with SunnyRabbiera. I have a Sony Vaio as well (see signature). The laptop screen is actually the best I've seen so far, and trust me on this one, I've see a lot of laptop screens (lenovo/ibm, acer, hp, apple, dell). The quality is way ahead of the others. The keyboard types very well too, but I guess you can get that as well with other brands. In my case, the laptop is very sturdy as well; the case is made of carbon though this is not the case with most vaios I must say. If I'd have to say something negative about it, I'd say the technical specs aren't top notch but I wonder who really needs the very latest processor. I've heard a lot of negative things about the warranty as well, but my experiences (and others in my surroundings) were pretty ok.

More importantly, my laptop worked out of the box with Ubuntu (fingerprint reader not accounted for). The only things I had to fix were headphone jack and brightness, which are easily fixed. The rest works, such as wireless (how many wireless issue topics aren't there here on the forums?), suspend and hibernation (same remark as wireless), external monitor, etc...

I really wonder what ghost stories you've heard about vaios. Did you actually use one?

Well I know about 6 people in real life that I meet up every day that had constant issues with a vaio, from hardware issues to general dislike of the brand.
Only a few times I hear a good story about a vaio, but its rare as I know about 10 other people who own a vaio and about 3 report positive news.

---

### Post by ideaton on 2008-08-29
update: 

I don't think this is a problem specific to vaios.  That said, here's where I'm at and why I don't think it's specific to sony.  (maybe Nvidia, but that's another story).  

I thought I'd solved the problem but, well, same problem: crawling crawling slow, couldn't do anything.  I'm a total newbie, so, rather than find a way to disable the Nvidia driver without booting up all the way(if there is a way to do that), I just reinstalled ubuntu.  My harddrive doesn't have anything on it, so, why not?  I didn't bother with creating a new partition; I just installed the Ubuntu right on top of the old one.  Again, installation went without a hitch.  I really like what I'm seeing from Ubuntu----the aps are just phenomenal.  

Downloaded AWN and tried to set it up.  Oh, well, I have to enable desktop effects?  Gave me pause.  I downloaded Envy; manual install; legacy driver for Nvidia.  It worked just fine, except that the resolution was tiny (maxed out at 800x600).  Uninstalled that driver and loaded up the newest version, automatically selected by Envy.  

Unfortunately, when I enabled desktop effects: bam, same problem-----computer slows to a crawl, won't do anything, can't navigate or open *anything*.  

Clearly, this is an Nvidia problem.  But I don't know what, exactly.

---

### Post by ideaton on 2008-08-29
as for my computer.  I'm really asking for trouble, but, my old laptop got stolen and I thought I should try to save some money----so I bought it on ebay.  1.5 ghz ez-bake-oven processor [celeron m], 2gb ram, 320 gb hd.  I love that it's small [13.3"] and still has a fullsize keyboard.  I'm not sure what graphics card comes with it except that Ubuntu wants to install Nvidia and google tells me that it's likely I've got a Nvidia geforce go6200/6400 built in to the motherboard.  

I'm wondering if the chipset is what's going wrong?  Or is Envy/Hardy trying to download the wrong driver?  Worst case scenario, I can live without 3D effects, so, it's not a total wash in any case.  But at this point, i'd lose. and who wants that?

---

### Post by AN@S on 2008-09-02
I've recently got a brand new Vaio VGN-CR520, I have to say that it's simply perfect, everything worked out of the box with Ubuntu 8.04 except for Suspend/Hibernate which needed a small fix. I'm totally impressed with Vaio, when I look at other brands at the stores (Dell, HP, ..), and compare them to my pretty look and feel of my laptop I say to myself :"Oh thanks God I didn't get one of those".
I know I didn't help you solve your problem, I don't have an experience with this type of problems but I think it was a good chance to talk about my experience with my Vaio. :)

---

### Post by itmanvn on 2008-09-03
> **AN@S said:**
> I've recently got a brand new Vaio VGN-CR520, I have to say that it's simply perfect, everything worked out of the box with Ubuntu 8.04 except for Suspend/Hibernate which needed a small fix. I'm totally impressed with Vaio, when I look at other brands at the stores (Dell, HP, ..), and compare them to my pretty look and feel of my laptop I say to myself :"Oh thanks God I didn't get one of those".
I know I didn't help you solve your problem, I don't have an experience with this type of problems but I think it was a good chance to talk about my experience with my Vaio. :)

can you show me how can you fix your suspend/hibernate problem?:confused:

---

### Post by AN@S on 2008-09-04
> **itmanvn said:**
> can you show me how can you fix your suspend/hibernate problem?:confused:

Of course .. this worked for me:

```
sudo rmmod uvcvideo
```

I got this solution from here:

[http://ubuntuforums.org/showthread.php?t=712331](http://ubuntuforums.org/showthread.php?t=712331)

---

