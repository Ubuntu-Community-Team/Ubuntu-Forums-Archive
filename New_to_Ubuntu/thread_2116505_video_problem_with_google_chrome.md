---
title: "video problem with google chrome"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by chriscw81 on 2013-02-16
just switched to ubuntu a few days ago...

most videos i watch online using chrome show up with little "speckles" all over the screen.  i dont have this problem with firefox.  i tried searching for this problem and couldnt find anything.  any ideas?  is there something i need to install so i dont have this problem with chromium?

chris

---

### Post by chriscw81 on 2013-02-16
sorry, i should have mentioned i'm running ubuntu 12.0.4

---

### Post by robenroute on 2013-02-22
> **chriscw81 said:**
> sorry, i should have mentioned i'm running ubuntu 12.0.4

Same here, chriscw81. I've search the Internet for solutions, but can't seem to find any.

Anyone similar experience? Or better yet, anyone a solution/workaround?

Many thanks in advance!


BTW chriscw81, it's 12.04 (without the second dot ;))

---

### Post by addegsson on 2013-02-22
> **robenroute said:**
> Same here, chriscw81. I've search the Internet for solutions, but can't seem to find any.

Anyone similar experience? Or better yet, anyone a solution/workaround?

Many thanks in advance!


BTW chriscw81, it's 12.04 (without the second dot ;))

[LEFT] It has to do with chromes Pepper Flash Plugin, this is a known bug.

[LEFT]  1. Install latest flash player 11.2 from software center.
 [/LEFT]

2. Open Chrome and type ***chrome://plugins*** in your address bar. [/LEFT]
 [LEFT] 
[/LEFT]
  3. Disable PepperFlash 11.3 plugin.

4. Restart browser.

---

### Post by chriscw81 on 2013-02-22
sorry, should have reported back.  the 3rd time reinstalled the problem went away.  I'll keep that fix in mind though.  thanks for the help.

---

### Post by robenroute on 2013-02-22
> **addegsson said:**
> [LEFT] It has to do with chromes Pepper Flash Plugin, this is a known bug.

[LEFT]  1. Install latest flash player 11.2 from software center.
 [/LEFT]

2. Open Chrome and type ***chrome://plugins*** in your address bar. [/LEFT]
 [LEFT] 
[/LEFT]
  3. Disable PepperFlash 11.3 plugin.

4. Restart browser.

Thanks for your response addegsson. However, PepperFlash seems to be not installed in, or known to Chrome. There's only the Adobe Flash plugin. Disabled that one, restarted Chrome and, as expected, flash videos weren't playable at all. Re-enabled the Adobe Flash plugin, restarted the browser and eveything works again, but with the speckled vids.

Any other suggestions? Many thanks in advance.

---

### Post by chriscw81 on 2013-02-22
> **robenroute said:**
> Thanks for your response addegsson. However, PepperFlash seems to be not installed in, or known to Chrome. There's only the Adobe Flash plugin. Disabled that one, restarted Chrome and, as expected, flash videos weren't playable at all. Re-enabled the Adobe Flash plugin, restarted the browser and eveything works again, but with the speckled vids.
 
Any other suggestions? Many thanks in advance.
 
i'm gonna change this back to unsolved so maybe you can find a solution, robenroute.

---

### Post by vasa1 on 2013-02-23
> **chriscw81 said:**
> sorry, should have reported back.  the 3rd time reinstalled the problem went away.  I'll keep that fix in mind though.  thanks for the help.
Chris, you may want to look at this: [http://askubuntu.com/a/250534/25656](http://askubuntu.com/a/250534/25656) just in case the problem reappears :)

---

### Post by vasa1 on 2013-02-23
> **robenroute said:**
> Thanks for your response addegsson. However, PepperFlash seems to be not installed in, or known to Chrome. There's only the Adobe Flash plugin. Disabled that one, restarted Chrome and, as expected, flash videos weren't playable at all. Re-enabled the Adobe Flash plugin, restarted the browser and eveything works again, but with the speckled vids.

Any other suggestions? Many thanks in advance.

Something's odd here.

Chrome comes with Pepper Flash. It is there by default.

The specks are a bug associated with the Pepper Flash only.

---

### Post by robenroute on 2013-02-26
> **vasa1 said:**
> Something's odd here.

Chrome comes with Pepper Flash. It is there by default.

The specks are a bug associated with the Pepper Flash only.

Vasa1, I'll purge chrome and see what happens after I reinstall it... (firefox uses Adobe's flash plug-in and that works fine all right).

Thanks anyway.

---

### Post by LLigetfa on 2013-02-26
I've seen the yellow snow as well in Chrome.  Switching to HTML5 changes it to orange snow.  Have yet to find joy.  Can find no reference to Pepper Flash in the Chrome preferences.

In the meantime I'm using FireFox instead of Chrome.

---

### Post by LLigetfa on 2013-02-27
Further on this.  I recently installed Ubuntu 12.10 on a bunch of older laptops.  I followed the exact same procedure on all of them except that one of the laptops was newer and had a 64 bit CPU, so that one got the 64 bit version instead.  It is only that 64 bit machine that exhibits this issue.  Today I sparked up a few of the 32 bit laptops and they are fine.

On Friday I should be getting another 64 bit laptop back and will see what that one does.

---

### Post by LLigetfa on 2013-03-02
So much for the 64 bit theory.  I installed the 64 bit version on another HP laptop, this time an EliteBook 8540w and it is on its best behaviour.

On Friday I got anther 6510b back that is identical to the one I have yellow/orange snow on. I removed Windows from it and started to install 12.10 on it but ran out of time to test.  When I get back to it Monday I will have to see if I can repro the issue.

---

### Post by LLigetfa on 2013-03-04
OK, got back at the 6510b today... didn't install anything else except Ubuntu and Chrome this time.  No backports... no updates.

It has the same snow as the other 6510b so it's something specific to this model.

---

### Post by Frogs Hair on 2013-03-04
I believe chrome defaults to pepper if there is no other flash version installed. There was another thread started about this problem with in the last couple of weeks so it may help if you can locate it . I just revived a chrome update moments 3-4-13 a ago so up to date before doing anything if not already.

See the link. [http://askubuntu.com/questions/243313/why-is-google-chrome-displaying-artifacts-in-youtube](http://askubuntu.com/questions/243313/why-is-google-chrome-displaying-artifacts-in-youtube)

---

### Post by LLigetfa on 2013-03-05
I have installed Ubuntu onto several laptops using the exact same steps so except for hardware specific differences, they all have essentially the same software and the same config.

This are the chrome://flash report for the 8540w which works:
Google Chrome	25.0.1364.97 ()
OS	Linux
Flash plugin	11.6.602.171 /opt/google/chrome/PepperFlash/libpepflashplayer.so
Flash plugin	11.2 r202 /usr/lib/flashplugin-installer/libflashplayer.so (not used)

The 6510b is identical but produces snow.  The second more recently built 6510b has a slightly newer version of Chrome but it still doesn't work.

I also installed Ubuntu/Chrome on models nc4200, nc4400, nc6220, and nc6320 and they all work fine.  It is only the 6510b that does not.

---

### Post by robenroute on 2013-03-16
> **robenroute said:**
> Vasa1, I'll purge chrome and see what happens after I reinstall it... (firefox uses Adobe's flash plug-in and that works fine all right).

Thanks anyway.


Still, even wit hthe latest chrome updates, videos are still speckled...

---

### Post by robenroute on 2013-03-30
And the story continues: release 26 is out and the annoying artifacts are still here. What is going on? Might it be a video driver issue? I'm on a laptop with the Intel 965 chipset sporting Intel X3100 integrated graphics and I have run into several graphics issues (instability in general).

---

### Post by kc1di on 2013-03-30
Hi Chris this is a known issue with some installations with google's flashplayer.  [here's some info]("http://askubuntu.com/questions/246595/youtube-yellow-snow-screen-on-google-chrome") on how you can fix it.

---

### Post by robenroute on 2013-03-30
> **kc1di said:**
> Hi Chris this is a known issue with some installations with google's flashplayer.  [here's some info]("http://askubuntu.com/questions/246595/youtube-yellow-snow-screen-on-google-chrome") on how you can fix it.

Thanks for the response and link, but there is no "pepper-flash" or "out-of-process" plugin listed in my chrome plugins list/page...

---

### Post by LLigetfa on 2013-04-10
> **LLigetfa said:**
> I have installed Ubuntu onto several laptops using the exact same steps so except for hardware specific differences, they all have essentially the same software and the same config.

This are the chrome://flash report for the 8540w which works:
Google Chrome	25.0.1364.97 ()
OS	Linux
Flash plugin	11.6.602.171 /opt/google/chrome/PepperFlash/libpepflashplayer.so
Flash plugin	11.2 r202 /usr/lib/flashplugin-installer/libflashplayer.so (not used)

The 6510b is identical but produces snow.  The second more recently built 6510b has a slightly newer version of Chrome but it still doesn't work.

I also installed Ubuntu/Chrome on models nc4200, nc4400, nc6220, and nc6320 and they all work fine.  It is only the 6510b that does not.

Recent updates on the 6510b resolved this yellow snow problem.

---

### Post by vasa1 on 2013-04-10
> **Frogs Hair said:**
> I believe chrome defaults to pepper if there is no other flash version installed. ...
Even if both Flash versions are installed and enabled, the Pepper Flash will take precedence.

---

