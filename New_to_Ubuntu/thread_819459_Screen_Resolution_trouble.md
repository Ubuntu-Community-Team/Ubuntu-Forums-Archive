---
title: "Screen Resolution trouble"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by japhyr on 2008-06-05
Hello, this is my first post.  I was going to do a dual boot, but decided to jump in fully and do a linux-only setup.  I installed Ubuntu 7.04 on a dell 600m laptop yesterday, and things seem to be working except for the screen resolution.  I've read a bunch of threads, but haven't found anything that works yet.

Under Windows my video card was listed as just "ATI mobility radeon 9000".  When I look it up on ubuntu under system>preferences>hardware information, it says "Radeon R250 [Mobility FireGL 9000]".

When I go to system>preferences>screen resolution, the only option available is 1024x768.  I'm pretty sure I was using 1280xsomething under Windows, and I think the display/ driver is capable of 1400x1050.

I have only tried one thing, after reading so many possibilities.  I opened a terminal and wrote "sudo dpkg-reconfigure -phigh xserver-xorg", and kept the default vesa driver, and tried checking off more resolutions.  Then I hit enter, and ctrl-alt-backspace, and when I go back to preferences>screen resolution, the only option is still 1024x768.  One thing did change, however.  The refresh rate is now 61hz instead of 60hz, which makes a trail when I move some windows.

What should I do next?

---

### Post by SunnyRabbiera on 2008-06-05
Well you can try the screens and graphics app, a front end to the xorg configuration file.
With that in the first tab you can try to play around with monitor settings.
I was never able to use feisty but this app helped me with gutsy...
that app was around back then if I remember correctly.

---

### Post by issih on 2008-06-05
If you can't find the screens and graphics app, try editing the main menu(right click on menu and select it). In my case the screens and graphics app was listed but unselected, one click and there you go. Obviously you could also launch it from a terminal, but I don't know the command off the top of my head.

---

### Post by japhyr on 2008-06-05
Screens and Graphics is not available, even if I try to edit the menu.  I think that's because I'm using 7.04, and I think S&G was introduced in 7.10.

---

### Post by roger_1960 on 2008-06-05
Have you tried (in terminal) "sudo displayconfig-gtk" ? This GUI enabled me to sort out similar problems with a Trident graphics card.  After making each change you need to log out and log in again.

---

### Post by japhyr on 2008-06-05
When I try "sudo displayconfig-gtk", it says
"sudo: displayconfig-gtk: command not found".

Also, in other forums I've used there was a link to "new replies to your posts".  I haven't found that anywhere here, the closest I've found is subscribing to threads.  Is there a link like that here?

---

### Post by japhyr on 2008-06-05
I figured out the "new replies" stuff, but threads disappear quickly in this forum.  Is it okay to repost this in the Multimedia and Video forum?

---

### Post by avtolle on 2008-06-05
> **japhyr said:**
> When I try "sudo displayconfig-gtk", it says
"sudo: displayconfig-gtk: command not found".

Also, in other forums I've used there was a link to "new replies to your posts".  I haven't found that anywhere here, the closest I've found is subscribing to threads.  Is there a link like that here?
As you have discovered, this command is not available in 7.04, which you are running. Screens and Graphics is, to my knowledge, a graphical front-end to this application.

---

### Post by japhyr on 2008-06-05
Right, so I think my questions are:
 - How do I edit the right configuration file?
 - What changes do I make to that file?

I looked in a configuration file and saw a list of resolutions, but did not want to try changing things manually without knowing what I was doing.

---

### Post by japhyr on 2008-06-06
I changed part of the xorg.conf file, but I think I might have changed the wrong parts.  I saved a backup of the original file, though.  It started out:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I changed it to:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Then I did ctrl-alt-backspace, and when I went to system>preferences>screen resolution, the only option was still 1024x768.  Is there something else I need to change in xorg.conf, or do I need to change something else?

---

### Post by avtolle on 2008-06-06
I am by far not an expert in these things; but looking at your xorg.conf file posted above, there are two things that strike me: first, the Device under "Identifier" should not be "Generic Video Card" but rather some reference to your Raedon coard; and, the Driver should be at least "ati", not "vesa". Sorry, but I cannot tell you what should be under Identifier for the card description; maybe someone with the same ATI card as yours can give you the precise identification.

---

### Post by avtolle on 2008-06-06
Hold on; since you are still in 7.04, have you tried (from the terminal)```
sudo dpkg-reconfigure xserver-xorg
``` and tried to configure your card/monitor "the old way"? If not, give it a try.
EDIT: I see that you did do this from your first post, but selected the "vesa" driver. Try using the "ati" driver and see what happens.

---

### Post by japhyr on 2008-06-06
Okay, I tried "sudo dpkg-reconfigure xserver-xorg" again, and selected "ati".  This time it took me through a whole series of questions, not just a list of resolutions.  When I got to resolutions, I checked 1280x1024 and 1280x960, in addition to the lower resolutions that were already selected.

When it finished asking questions, I did ctrl-alt-backspace.  Going to system>preferences>screen resolution, I found four resolutions:  1024x768, 800x600, 640x480, and 832x624.  Previously 1024x768 was the only option.  Also, the refresh rate is back to 60hz, where I think it should be.

Any thoughts on why it added the lower resolutions but not the higher ones?  I have used higher resolutions on this machine under Windows.

---

### Post by avtolle on 2008-06-06
Hmm, no real idea on why the higher resolutions didn't appear. Perhaps your monitor choice? I'm grasping at straws here, as is obvious.

---

### Post by avtolle on 2008-06-06
And, it could be the way you answered one of the series of questions you got. I'm wondering, and have no way of checking as I don't have the card you do and am running 8.04, if there is a raedon driver you might have selected in the process of the dpkg-configure xserver-xorg process rather than the straight ati driver.

EDIT: I arrived at the above idea by reviewing the various possibilities listed under the "Screens and Graphics" application for ati cards. It appears that there are some raedon drivers available thereunder, thus the idea to use "raedon" rather than "ati" when responding to the questions. HTH.

---

### Post by avtolle on 2008-06-06
I did a google search on your card and Ubuntu, and found that there have bees some problems in the past. Under 8.04 (which I hasten to acknowledge you are not using), it is to be automatically identified and the "radeon" driver used for it. Thus, I return to my suggestion that you do the ```
sudo dpkg-reconfigure xserver-xorg
``` again, this time selecting radeon for the driver rather than just ati.

---

### Post by japhyr on 2008-06-07
> I'm grasping at straws here, as is obvious.
Your straws are helping.

I tried a few things, going through the "sudo dpkg-reconfigure xserver-xorg" series of questions a bunch of times.  There is no option for a radeon driver.  I let it auto-detect some things, and then tried to specify them.  In the end, I am where I last described:  four options for screen resolution, but the highest is 1024x768.

Here is part of my current xorg.conf:
```
Section "Device"
	Identifier	"ATI RADEON 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9000"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Also, if it means anything, here is the line from "lspci" that refers to the video card:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)
```

I am at a loss as to what to try next.  I thought about downloading a driver, but I'm not sure what to look for.  Any more thoughts?

---

### Post by iaculallad on 2008-06-07
Replace the "Monitor" and "Screen" section of your current xorg.conf file with the lines of text below and restart gdm.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        HorizSync 30-110
        VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9000"
	Monitor		"Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

---

### Post by japhyr on 2008-06-07
Thanks for the suggestion.  I made the changes you suggested.  When I restarted and went to screen resolution, I found the same four options I keep finding, maxing at 1024x768.  I looked at the xorg.conf file to make sure the changes stuck, and they did.  It now looks like:
```
Section "Device"
	Identifier	"ATI RADEON 9000"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        HorizSync 30-110
        VertRefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9000"
	Monitor		"Generic Monitor"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

Any more thoughts?  And why would it still list those same options, when there's only one in the conf file?

---

### Post by N.N. on 2008-06-07
I think using the open source ATI driver is what's preventing you from enabling higher resolutions. Try installing the proprietary graphics driver from the Restricted Drivers Manager. The following link explains how to do so on 7.04: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882).

I've experienced that use of the open source nvidia driver prevented me from selecting my monitor's native resolution. In my case, switching to the proprietary driver resolved the issue.

---

### Post by japhyr on 2008-06-07
I'll take a look at the proprietary drivers.

By the way, I called the device "ATI RADEON 9000", but that's a name I chose.  Does that matter at all?  Is there any difference between naming it "ATI RADEON 9000" and "ATI RADEON R250 MOBILITY FIREGL 9000"?

---

### Post by japhyr on 2008-06-07
Looking at the [proprietary driver information]("https://help.ubuntu.com/community/BinaryDriverHowto"), it pretty clearly states that the proprietary driver only works for drivers 9500 and higher, or 400 and higher.  Is there any reason to try the driver despite this?

---

### Post by japhyr on 2008-06-07
I found one interesting, if not entirely promising, result.  I added a virtual setting under screen>display in xorg.conf:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9000"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
		Virtual		1280 960
	EndSubSection
EndSection
```

After restarting, I was able to select 1280x960 in preferences>screen resolution.  However, it just extended the desktop off the screen, at the 1024x768 resolution.  Any thoughts?

---

### Post by N.N. on 2008-06-07
> **japhyr said:**
> Looking at the [proprietary driver information]("https://help.ubuntu.com/community/BinaryDriverHowto"), it pretty clearly states that the proprietary driver only works for drivers 9500 and higher, or 400 and higher.  Is there any reason to try the driver despite this?

Sorry, I overlooked that. It seems the proprietary fglrx driver doesn't provide support for your graphics card, and thus there's no reason to try it. The only thing I can suggest, then, is that you try to specify the refresh rate of the monitor more accurately. I haven't been able to find the official values for the monitor's vertical or horizontal refresh rates, but I found some values in a post on the MEPIS forums (see [http://www.mepis.org/node/4036](http://www.mepis.org/node/4036)).

In the "Monitor" section of your xorg.conf file, try changing HorizSync to 31.5-90 and VertRefresh to 59-75:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        HorizSync 31.5-90
        VertRefresh 59-75
EndSection
```

Having done that, save the file and press CTRL+ALT+BACKSPACE to restart X. With luck, that should solve your problem. If it doesn't, I don't know how to solve the problem. :(

---

### Post by japhyr on 2008-06-07
I tried changing the refresh rate, with and without the virtual setting.  No luck; the higher resolution still extends the desktop off the screen.

Here's a simple possibility:  I installed from a dvd I got with the book "Ubuntu for Non-Geeks", second edition.  When I click on system>administration>update manager, it says "You can install 208 updates".  I am guessing I should let these updates run.  Would that just update the 7.04 version I have running?  I am assuming it would not update me to a whole new version, 7.10 or 8.04, right?  Could be a very simple fix, but I'd like to hear a thought on whether that's an appropriate thing to do before trying it.

Thanks everyone for all the ongoing suggestions, by the way.

---

### Post by N.N. on 2008-06-07
Installing available updates is always a good idea as they might fix bugs or security vulnerabilities. I don't think the updates will solve your problem, however. :-|

The update manager shouldn't attempt to upgrade your distribution to a newer version unless you explicitly tell it to do so.

---

### Post by avtolle on 2008-06-07
I'd run the updates, but as N.N. posted, this will likely not resolve your problem. However, hope springs eternal....

---

### Post by japhyr on 2008-06-08
I installed all the updates, but it did not affect screen resolution at all.  I'm putting a lot of time into this, but I don't want to accept low resolution just to switch to linux.

I looked at the /var/log/Xorg.O.log file and found these lines:
```
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Valid Mode from Detailed timing table: 1024x768
(II) RADEON(0): Valid Mode from Detailed timing table: 1024x768
(II) RADEON(0): Total of 2 mode(s) found.
(II) RADEON(0): Total number of valid DDC mode(s) found: 2
(WW) RADEON(0): Mode 1280x960 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768
```

I looked at my monitor specs, and it says max resolution is 1024x768 XGA, and 1400x1050 SXGA+.  Am I running into a brick wall by trying to go against BIOS settings?  Is there some way to switch between XGA and SXGA modes?


I found one other idea, regarding dpi.  I want a resolution of 96 dpi.  Using this number, I calculated a display size that would get this resolution:  1280 pixels x 25.4 mm / 96 dpi = 339 mm.  Similarly, I get a display height of 254mm.  So I set DisplaySize 339 254.  When I restart, I have the resolution I want on the login screen only.  Once I'm on the gnome desktop, the resolution is low again.  Here is a relevant section of the log after that change:

```
(**) RADEON(0): Display dimensions: (339, 254) mm
(WW) RADEON(0): Probed monitor is 290x210 mm, using Displaysize 339x254 mm
(**) RADEON(0): DPI set to (76, 76)
```

Any thoughts from all this?

---

### Post by japhyr on 2008-06-08
Can anyone shed some light on whether this information from BIOS is giving me trouble?  Or, if anyone can make anything from the line "Valid Mode from Detailed Timing table: 1024x768"?  Is there some way to calculate a combination of resolution, display size, refresh rate, etc. that will allow the higher resolution of 1280x960 (which I ran on this machine under Windows) to work?

from Xorg.O.log:
```
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Valid Mode from Detailed timing table: 1024x768
(II) RADEON(0): Valid Mode from Detailed timing table: 1024x768
(II) RADEON(0): Total of 2 mode(s) found.
(II) RADEON(0): Total number of valid DDC mode(s) found: 2
(WW) RADEON(0): Mode 1280x960 is out of range.
(WW) RADEON(0): Valid modes must be between 320x200-1024x768
```

---

### Post by the.scarecrow on 2008-12-27
I feel your pain. Yep I have the same problem, have you made any progress on this problem?

---

