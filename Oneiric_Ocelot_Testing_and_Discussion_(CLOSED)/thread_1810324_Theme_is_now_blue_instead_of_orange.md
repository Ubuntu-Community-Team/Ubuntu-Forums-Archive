---
title: "Theme is now blue instead of orange"
date: 2011-07-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2011-07-22
Anyone know why my theme is now blue in 11.10? Is this a known issue at the moment? I couldn't seem to find any other related posts about this.

[IMG]http://img11.imageshack.us/img11/6521/96518640.png[/IMG]

---

### Post by christoph411 on 2011-07-22
I don't know what's wrong with your theme that it's blue (sorry I can't help) but I wish it would happen to my computer haha! :D

---

### Post by godhika on 2011-07-22
Hmm I have seen it from someone else lately - unfortunately it was at the comment thread of Andrea Cimitan's (Canonicals man for the light-themes) announcement of the new dark toolbar style on his google+ page. So at least theres one other case out there ;).Did you try to reinstall the light-theme package?

---

### Post by lucazade on 2011-07-23
@kyleabaker

The issue is not related to light-themes. Reinstalling them won't help.

There is some problem in videodrivers or pixbuf that handles png files.
mc4man had this issue swithing from nvidia to nouveau:
[http://ubuntuforums.org/showpost.php?p=11063870&postcount=11](http://ubuntuforums.org/showpost.php?p=11063870&postcount=11)

---

### Post by VinDSL on 2011-07-23
> **lucazade said:**
> mc4man had this issue swithing from nvidia to nouveau [...]
Yep!  Exactly!

Until a few minutes ago, I was running Nouveau drivers, and the buttons were BLUE.


[IMG]http://vindsl.com/images/Screenshot at 2011-07-23 00:41:39.png[/IMG]


I just switched to nVidia drivers, and the ORANGE is back.


[IMG]http://vindsl.com/images/Screenshot at 2011-07-23 01:39:26.png[/IMG]

---

### Post by lucazade on 2011-07-23
> **VinDSL said:**
> Yep!  Exactly!

Until a few minutes ago, I was running Nouveau drivers, and the buttons were BLUE.



I just switched to nVidia drivers, and the ORANGE is back.




Thanks VinDSL!

I believe we should open a bug against Nouveau. I can't do myself because I'm in virtualmachine and cannot reproduce it. :)

---

### Post by mc4man on 2011-07-23
This may be another oddity - on my p4 nividia desktop, the X button is blue with nouveau, red w/ nvidia-current (been happening for a few weeks
On a much newer nvidia laptop normal with both nouveau and nvidia
(on both have set custom for the selected color

---

### Post by lucazade on 2011-07-23
> **mc4man said:**
> This may be another oddity - on my p4 nividia desktop, the X button is blue with nouveau, red w/ nvidia-current (been happening for a few weeks
On a much newer nvidia laptop normal with both nouveau and nvidia
(on both have set custom for the selected color

wonderful! easy to debug so!
ok.. going to try a livecd on my gts250, just to be sure i'm affected as well.

---

### Post by mc4man on 2011-07-23
> **lucazade said:**
> wonderful! easy to debug so!
ok.. going to try a livecd on my gts250, just to be sure i'm affected as well.
One thing I'm seeing this week on both machines, (since the compiz/compizconfig/libdecoration/unity upgrades) is no window decoration on most modal windows
 Similar to what is in post 1, see if that's happening on the live cd - some more Ex. here
[http://ubuntuforums.org/showthread.php?p=11066433#post11066433](http://ubuntuforums.org/showthread.php?p=11066433#post11066433)

---

### Post by lucazade on 2011-07-23
Installed Oneiric on my machine with a Nvidia 250Gts to test out this issue with colors.
I don't see the issue with both nouveau and nvidia-current, i'm not able to reproduce here.

Also the issue about modal windows seems not present, maybe I haven't played a lot.

Unfortunately I had other issues during installation.. nouveau driver hard freeze after some minutes and I have to hard reset pc. This prevent from installing ubuntu to hd, because I have not enough time before the freeze!

So I tried to startup livecd with vesa by using "xforcevesa" as kernel params but it ends up in a flickering vt.
Only way to employ vesa is to brutal unload nouveau module by passing some fake params like "nouveau.dummy=1".. ugly!

Once installed I tried to install nvidia-current from jockey but at the reboot nvidia binary drivers were not in use, so a "sudo nvidia-xconfig" did the trick.

This should be the nouveau bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/553789](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/553789)

Wondering why there is not thread about it, no body else get this?

---

### Post by kyleabaker on 2011-07-23
> **lucazade said:**
> @kyleabaker

The issue is not related to light-themes. Reinstalling them won't help.

There is some problem in videodrivers or pixbuf that handles png files.
mc4man had this issue swithing from nvidia to nouveau:
[http://ubuntuforums.org/showpost.php?p=11063870&postcount=11](http://ubuntuforums.org/showpost.php?p=11063870&postcount=11)

Thanks for the update. That looks like it worked for VinDSL, but unfortunately I will have to hold off on installing nvidia drivers until nVidia fixes an issue with the 7300le series cards.

...or I could install 173 rather than current I suppose. I'll give that a try! :popcorn:

---

### Post by kyleabaker on 2011-07-23
Thanks all. That worked. Marking as solved...

---

### Post by EgoGratis on 2011-07-24
I can confirm this behavior with nouveau driver. Color.

---

