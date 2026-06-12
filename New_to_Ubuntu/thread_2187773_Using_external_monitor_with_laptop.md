---
title: "Using external monitor with laptop"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by lesliek2 on 2013-11-13
I'm using Ubuntu 12.04.
The native resolution of my laptop is 1600x900.
The native resolution of my external monitor is 1920x1080.
When I plug my external monitor into my laptop, I get by default a mirrored display of 1440x900. It's the maximum resolution shown in the window called Display in System Settings.
I'm assuming that there's no way that I can have the external monitor mirror the laptop screen and have a resolution greater than 1600x900, my laptop's native resolution, but I don't understand why I'm not being given the option of setting the mirrored display to 1600x900.
Is there some way that I can get the option of a mirrored display at 1600x900?
If there is, is there any reason why I shouldn't be using that option?

Thanks,

Leslie

---

### Post by SeijiSensei on 2013-11-13
The external monitor may not support that resolution.  Look at the manual for the monitor and see what resolutions it supports.

---

### Post by alphacrucis2 on 2013-11-13
It makes much more sense to "extend display" when you have monitors with different resolution. Also gives you more screen territory. LCD and LED displays have a fixed native resolution and running anything else will degrade the image.

---

### Post by lukastexmiller on 2013-11-14
Have you checked your screen layout editor? ARandR under hardware in settings manager.

---

### Post by lesliek2 on 2013-11-14
Thank you to all who've replied.
After posting, I kept looking for answers myself and finally found [http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/).
Following its instructions, I was able to get my external monitor to run at 1600x900 at every boot-up, which it hadn't done before, so now have both of my monitors running at that resolution with a mirrored display, which is an improvement on my earlier situation.
alphacrucis2 mentioned using an extended, rather than mirrored, display and, in that way, being able to have my external monitor run at its native resolution (1920x1080), while my laptop ran at its native resolution (1600x900).
Before going the mirrored display route, I tried to figure out on my own how to use the Display window in System Settings to have the two monitors running each at its native resolution, but couldn't.
If anyone can point me to a SIMPLE how-to for having an extended display using Ubuntu 12.04, I'd appreciate it very much.
Thanks again to all those who took the trouble to reply.

---

### Post by Bucky Ball on 2013-11-14
As mentioned, arandr is your friend. You can install it from the repositories and set up your monitors how you like.

---

### Post by lesliek2 on 2013-11-14
Thanks for your reply, Bucky Ball.
I installed arandr yesterday and it ran when I tried it, but I wasn't sure what to do with it, so I just closed it.
After closing it, I found and followed the instructions that I mentioned in my last post, which, as I've already said, got me a mirrored display of 1600x900.
Now, after reading your post, I tried to run arandr again, but it would no longer run. Instead, I got the following message:

Traceback (most recent call last):
  File "/usr/bin/arandr", line 25, in <module>
    main()
  File "/usr/lib/pymodules/python2.7/screenlayout/gui.py", line 302, in main
    force_version=options.force_version
  File "/usr/lib/pymodules/python2.7/screenlayout/gui.py", line 143, in __init__
    self.filetemplate = self.widget.load_from_x()
  File "/usr/lib/pymodules/python2.7/screenlayout/widget.py", line 77, in load_from_x
    self._xrandr.load_from_x()
  File "/usr/lib/pymodules/python2.7/screenlayout/xrandr.py", line 134, in load_from_x
    o.modes.append(Size(int(a) for a in d.strip().split(" ")[0].split("x")))
  File "/usr/lib/pymodules/python2.7/screenlayout/auxiliary.py", line 37, in __new__
    arg = tuple(arg)
  File "/usr/lib/pymodules/python2.7/screenlayout/xrandr.py", line 134, in <genexpr>
    o.modes.append(Size(int(a) for a in d.strip().split(" ")[0].split("x")))
ValueError: invalid literal for int() with base 10: '900_60.00'

I suspect that arandr won't run anymore BECAUSE I followed the instructions that I mentioned in my last post. I say that because I recognise the bit in quotes in the last line as part of the resolution information that I was using yesterday. I think arandr is unhappy with the "_60.00" bit, but I'm afraid that if I go back to the file I added yesterday pursuant to the instructions and remove the "_60.00" bit, I'll lose the progress I made yesterday in changing my resolution on both monitors from 1440x900 to 1600x900.

What to do, what to do?

---

### Post by nerdtron on 2013-11-15
Maybe a dumb question but I assume you have are using a HDMI cable? I have problems in resolution before when I am using the regular VGA cable.

---

### Post by lesliek2 on 2013-11-15
Thanks for taking the trouble to reply, nerdtron.
I'm not using an HDMI cable, but a VGA one, and I think that all my problems have been solved.
When I began this exercise, I thought I thought that my only options were a mirrored display or an extended display.
Now, I've discovered that, by using the Display window in System Settings, I can turn off my laptop screen with my external monitor plugged in and have the external monitor screen as my only one, with it running at its native resolution.
That's just what I wanted.
I can even keep my laptop closed while using my external monitor.
I just wish there'd been a simple tutorial about how to use the Display window!
Thanks again,

Leslie

---

### Post by Bucky Ball on 2013-11-15
With the laptop lid closed and the monitor on it might be an idea to open the laptop after five minutes and check that the laptop screen is not getting too hot as it's closed against the hot body of the laptop. In other words, check nothing is overheating under the lid (this practice could also make your machine run hotter than it would thus shortening the life of hardware).

Might pay to get a few temperature checks with shut and open.

---

### Post by thesleash on 2013-11-15
maybe you could just try using the included keyboard shortcuts, super, or windows, button and p may be of use

---

### Post by lesliek2 on 2013-11-15
Thanks for your further reply Bucky Ball.
I don't have the laptop screen on when I have the laptop lid closed, but your point took me into a whole new area, the temperature at which my laptop runs.
I started reading about that and discovered that I have two VGA compatible controllers in my laptop: Mobility Radeon HD 4225/4250; and Radeon HD 6370M/7370M. I understand that the first is integrated, the second discrete.
I also read that my laptop might run cooler if I only used the discrete controller, not the integrated one.
That immediately makes me wonder: how do I find out whether both of the controllers are in use or only one and, if only one, which?
Should I be posting a separate question about that?
Thanks again,

Leslie

---

### Post by Bucky Ball on 2013-11-15
> **lesliek2 said:**
> Thanks for your further reply Bucky Ball.
I don't have the laptop screen on when I have the laptop lid closed, but your point took me into a whole new area, the temperature at which my laptop runs.
I started reading about that and discovered that I have two VGA compatible controllers in my laptop: Mobility Radeon HD 4225/4250; and Radeon HD 6370M/7370M. I understand that the first is integrated, the second discrete.
I also read that my laptop might run cooler if I only used the discrete controller, not the integrated one.
That immediately makes me wonder: how do I find out whether both of the controllers are in use or only one and, if only one, which?
Should I be posting a separate question about that?
Thanks again,

Leslie

Yes, post a new thread about that. ;)

Yes, I meant both, how cool the screen was (even though it's off it is against the heat of the running machine) and the machine itself.

Good luck.

---

