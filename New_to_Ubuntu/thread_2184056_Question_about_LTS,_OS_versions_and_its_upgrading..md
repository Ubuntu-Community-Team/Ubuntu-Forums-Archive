---
title: "Question about LTS, OS versions and its upgrading."
date: 2013-10-27
forum: New to Ubuntu
---

### Post by Durabys on 2013-10-27
Hello.
I have a questions concerning "LTS".

If I have Xubuntu LTS 12.04.3 can it be upgraded to LTS 14.04 when it comes out in 2014 and how hard is it?
If I have Xubuntu 13.04 can it be upgraded to LTS 14.04 and how hard is it?

Thank you.

---

### Post by ikt on 2013-10-27
You can definitely upgrade both to the new LTS, it should be fairly easy for both. You will likely upgrade 13.04 to 13.10 shortly and then the same thing to get to 14.04.

On 12.04 there will be an option to upgrade direct to 14.04.

Both are fairly painless :)

---

### Post by pqwoerituytrueiwoq on 2013-10-27
there was a change in policy that allows you to upgrade from any version to the next lts, given the support dates for each version, you can do any of these w/ out having a unsupported OS installed
xubuntu 12.04 -> 14.04
xubuntu 12.10 -> 14.04
xubuntu 13.10 -> 14.04
personally i would use xubuntu 12.10 and add the xfce 4.10 ppa if i did not want to bother implementing workarounds in 13.10, i know of 4 bugs in it
termianl -> terminal (menu) -> go to set encoding and watch it crash (no known workaround)
weather applet text is not readable on mouse-over in the albatross theme (apply patch tha was somehow removed from the theme)
the volume icon does not work (see sticky in general help)
the mp3 decoder in gstreamer has a playback quality issue (fixed via downgrade to the 13.04 package)

---

### Post by Durabys on 2013-10-27
> **ikt said:**
> You can definitely upgrade both to the new LTS, it should be fairly easy for both. You will likely upgrade 13.04 to 13.10 shortly and then the same thing to get to 14.04.

 On 12.04 there will be an option to upgrade direct to 14.04.

 Both are fairly painless :)

Ah thanks. I currently have 13.04 and was thinking about downgrading to 12.04.3 because they say it is more stable.

> **pqwoerituytrueiwoq said:**
> there was a change in policy that allows you to upgrade from any version to the next lts, given the support dates for each version, you can do any of these w/ out having a unsupported OS installed
 xubuntu 12.04 -> 14.04
 xubuntu 12.10 -> 14.04
 xubuntu 13.10 -> 14.04
 personally i would use xubuntu 12.10 and add the xfce 4.10 ppa if i did not want to bother implementing workarounds in 13.10, i know of 4 bugs in it
 termianl -> terminal (menu) -> go to set encoding and watch it crash (no known workaround)
 weather applet text is not readable on mouse-over in the albatross theme (apply patch tha was somehow removed from the theme)
 the volume icon does not work (see sticky in general help)
 the mp3 decoder in gstreamer has a playback quality issue (fixed via downgrade to the 13.04 package)

I am completelly new to this so I plan to upgrade to 14.04 when comes out and stay with it for as long as possible.

---

### Post by ian-weisser on 2013-10-27
> **Durabys said:**
> I [...] was thinking about downgrading to 12.04.3 because they say it is more stable.

All released versions of Ubuntu are stable.
LTS releases are simply supported longer. Fixes that went into 12.04 have gone into the more recent releases, too.
Are you having some problem with a current release?

---

### Post by pqwoerituytrueiwoq on 2013-10-27
Upgrading is very easy, but for someone new to linux i would recommend xubuntu 12.10 until 14.04 becomes available in april
[http://cdimage.ubuntu.com/xubuntu/releases/quantal/release/](http://cdimage.ubuntu.com/xubuntu/releases/quantal/release/)
12.10 is supported till the end of april and 14.04 comes out mid april so it has a 2 week window to upgrade, the update manager will inform you of the LTS upgrade
just set the update manager to only inform you of LTS upgrades:
[ATTACH=CONFIG]247309[/ATTACH]

---

### Post by Durabys on 2013-10-27
> **ian-weisser said:**
> All released versions of Ubuntu are stable.
LTS releases are simply supported longer. Fixes that went into 12.04 have gone into the more recent releases, too.
Are you having some problem with a current release?

No.

> **pqwoerituytrueiwoq said:**
> Upgrading is very easy, but for someone new to linux i would recommend xubuntu 12.10 until 14.04 becomes available in april
[http://cdimage.ubuntu.com/xubuntu/releases/quantal/release/](http://cdimage.ubuntu.com/xubuntu/releases/quantal/release/)
 12.10 is supported till the end of april and 14.04 comes out mid april so it has a 2 week window to upgrade, the update manager will inform you of the LTS upgrade
 just set the update manager to only inform you of LTS upgrades:
[ATTACH=CONFIG]247309[/ATTACH]

So. You propose I should downgrade from 13.10 to the non-LTS 12.10?

---

### Post by ian-weisser on 2013-10-27
If you are not having a problem, then why change?
If you want to change to an LTS, you can simply wait until April and change to the newly-released 14.04 LTS.

---

### Post by Durabys on 2013-10-27
> **ian-weisser said:**
> If you are not having a problem, then why change?
If you want to change to an LTS, you can simply wait until April and change to the newly-released 14.04 LTS.

Exactly.

I was just being rhetorical for christs sake! :oops:

---

### Post by pqwoerituytrueiwoq on 2013-10-27
i was not aware you had a existing install or what version it was, i would not bother reinstalling if you already have 13.10 installed
i intend to stick with 14.04 for a few years (3-3.5 years) i had used 10.04 for around 3 years and was not happy with 12.04 and ended up going strait to 12.10

---

### Post by Durabys on 2013-10-28
Oh. It is ok.

Why then do you still have "Xubuntu 13.04 Raring Ringtail" in your distro column then?

---

