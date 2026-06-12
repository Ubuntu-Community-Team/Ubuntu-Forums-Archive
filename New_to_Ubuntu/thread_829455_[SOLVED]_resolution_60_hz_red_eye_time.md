---
title: "[SOLVED] resolution 60 hz: red eye time"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by simontaylor on 2008-06-14
This one is bound to identify me as an absolute tyro: I've tried to boost my screen resolution beyond 60 hz - running 8.04 - system>preferences>screen resolution (1280x1024) but I can't improve my refresh rate. 

Living in front of my monitor at the moment, having to write, human readable stuff, it's definitely red eye time. 

Is there a way of boosting hz without dropping from 1280 x 1024? 

I've tried ENVYNG ... which might have been a bit silly, because I don't know what type of graphics/video card I'm running. ENVYNG tells me it's neither API nor NVIDIA! 

Please save my eyes,

yours

Simon Taylor

[www.brazilcoffee.co.nz](www.brazilcoffee.co.nz)
[www.squarewhiteworld.com](www.squarewhiteworld.com)

---

### Post by icouldntfindausername on 2008-06-14
Have you got nvidia or amd/ati? I know for a fact that if you have nvidia you can easily change this by using this command:

> sudo nvidia-settings

Choose right resolution and refresh rate and save to your xorg.conf file.

---

### Post by cariboo on 2008-06-14
There is no way to do it with an LCD display the vrefresh and hsync are set in hardware. Have you tried System-->Preferences-->Appearance,
click on the fonts tab and selected sub pixel smoothing, to make the font look better? Another suggestion back in days of yore when Word Perfect was King, they used white text on a blue screen, the same blue as the MS BSOD screen, I talked to transcriptionists who set their MS Word screen to look the same way as they say it is way easier on the eyes.

Jim

---

### Post by simontaylor on 2008-06-15
here we go:

> simon@simon-desktop:~$ sudo nvidia-settings
[sudo] password for simon: 
sudo: nvidia-settings: command not found
simon@simon-desktop:~$ 


simon

---

### Post by simontaylor on 2008-06-15
thanks Jim,
I'm looking to lift the refresh rate of the screen from 60 hz up to where it's not burning out badly needed - because in short supply - brain cells.

simon

---

### Post by alienexplorers on 2008-06-15
make a modeline for your monitor section of your xorg.conf file.  A 70hz modeline in 1280x1024 would look like this:
> Modeline "1280x1024_70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
The modeline should be placed as shown:
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Delta" <--- insert model manufacturer
    ModelName      "DE-570" <--- insert monitor model number
    HorizSync       30.0 - 70.0 <--- enter you horz sync here
    VertRefresh     50.0 - 120.0 <--- enter you vert refresh here
    Option         "DPMS"
    Modeline       "1280x1024_70.00"  128.94  1280 1368 1504 1728  1024 1025 1028 1066  -HSync +Vsync
EndSection

---

### Post by simontaylor on 2008-06-15
dear alienexplorers,

I understand the principle behind your excellent proposal but I have little to no grasp on its practical implications: 

Do I go to file trees to find xorg.conf? (When I've tried to alter files in the past my box has told me I'm not permitted.)

If I go through Terminal, how do I get into xorg.conf file?

How do I compute Hsync and Vsync values for a 70hz overall refresh rate?

A little more help would be greatly appreciated,

Thanks,

simon

---

### Post by Pconfig on 2008-06-15
You can access your xorg.conf file threw the following command

```

sudo gedit /etc/X11/xorg.conf

```

Furthermore, i have no idea how to compute those Hsync and Vsync values.

---

### Post by simontaylor on 2008-06-15
hi Pconfig,
lost a reply I thought I'd posted: yep, sudo gedit /etc/X11/xorg.conf works to open the file. Wherein I read: > sudo dpkg-reconfigure -phigh xserver-xorg

will reconfigure/automatically update xorg. Sounded good to me: I was hoping for an automatic upgrade to faster refresh rate. Nope. 

The file came back simplified, culled of monitor references beyond this:
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

In order to interpellate alienexplorers' suggested modeline... well, I didn't know where to start. But I did see the manual for xorg.conf.

And I went there and read that Frequency is accepted as an Option, or "special keyword," and "Hz" in the required inverted commas is accepted as a value. So that tiny spark of inadequate knowledge lead me to add Frequency "70 Hz" to my monitor section in xorg.conf.

I restarted and got a blank black screen. ... ^%#$^%$^%$$^$

What an idiot!

Started in recovery. And tried to repair. No go. Restarted in recovery. Tried to fix Xserver. 

Rebooted: entire orientation of screen altered but as you can see I'm up and running again.

This is a long way of saying: unless I have full and clear instructions I'm not touching a thing; I just don't have the technical grasp, the symbolic understanding to deal with Terminal talk. My talk to my terminal almost proved terminal.

Then.... Is usplash an option for higher refresh rate?

simon

---

### Post by alienexplorers on 2008-06-15
What monitor make and model are you using?  What screen resolution are you shooting for? What video card are you using?  And I know you want a refresh rate of 70Hz.

---

### Post by Jazzy_Jeff on 2008-06-15
Tell us which monitor you are using. I have an LG flat panel and 60 hz is what it is set at internally. I cannot change it.

---

### Post by simontaylor on 2008-06-15
hi alien, jazz, 

Philips 107S21 monitor ... hold on, check on the backside and says 50 - 60 Hz... that would be crap ... if it couldn't handle higher... and I would just have to say thank you for your patience! (and save my money for a better monitor!)

VGA Integrated VIA ProSavage8 Graphics

Regardless of refresh rate, onboard card hasn't appeared to run to optimum. 

Jumping over to other thread now: Serpentine won't do the do on my CD/DVD writer - this after nixing K3b and Gnomebaker and Brasero... another issue.

Tell me what you think. Input appreciated.

best, 
simon

---

### Post by alienexplorers on 2008-06-15
Your monitor is capable of 70HZ  Just copy this section to your monitor section of your xorg.conf file using:
> gksudo gedit /etc/X11/xorg.conf

> Section "Monitor"
Identifier "Monitor0"
VendorName "Phillips"
ModelName "107S21"
HorizSync 30 - 71
VertRefresh 50.0 - 160.0
Option "DPMS"
Modeline "1280x1024_70.00" 128.94 1280 1368 1504 1728 1024 1025 1028 1066 -HSync +Vsync
EndSection 

---

### Post by alienexplorers on 2008-06-15
Your monitor is capable of 70HZ  Just copy this section to your monitor section of your xorg.conf file using:
> gksudo gedit /etc/X11/xorg.conf

> Section "Monitor"
Identifier "Monitor0"
VendorName "Phillips"
ModelName "107S21"
HorizSync 30 - 71
VertRefresh 50.0 - 160.0
Option "DPMS"
Modeline "1280x1024_70.00" 128.94 1280 1368 1504 1728 1024 1025 1028 1066 -HSync +Vsync
EndSection 

---

### Post by simontaylor on 2008-06-15
Alienexplorers,

ok. have cut and pasted it in. nervous about crashing the display. 

I assume I should replace the existing section "monitor"?
I further assume I should reformat to fit the xorg.conf? or perhaps this doesn't matter.

I penultimately assume that I should restart/reboot?

I ultimately assume that I will find the new resolution under System>Preferences>Screen Resolution? (And, of course, full responsibility!) 

Small point: will it actually appear as an option under the aforementioned Screen Resolution? i.e. how do I check the fix has taken?

these are the final questions before I bite the bullet... 

thanks,
simon

---

### Post by alienexplorers on 2008-06-15
Replace you current monitor section.  Yes, you can format it to fit in with the rest of the file.  Save the file and reboot.  You should be able to check screen resolution under Screen Resolution.

---

### Post by simontaylor on 2008-06-15
I'm going to thank you for patience anyway: thank you. 

Now. Rebooted. And yes, lights and colours. Excellent. No sign of 70 Hz under screen resolution in Preferences. But checking the xorg.conf file I find the graft has taken: the replaced section has stuck.

Any idea how I test the refresh rate... apart from gauging the colour saturation of my eyeball after 6 hours writing?

simon

---

### Post by alienexplorers on 2008-06-15
I have no way to check my 70Hz on my system either.  All I know is that if the screen ain't flickering then you must be OK.  Thanks for sticking with me.

---

### Post by simontaylor on 2008-06-15
another curious thing: System>Hardware Testing tells me - and Launchpad - that I'm running 1280 x 960 @ 60 Hz.

Is this the work of Envyng?

I should possibly remove the latter anyway. 

Further: no noticeable change to screen. I expected at least my custom stretching and dollying to fit to have been mucked up by the lift in refresh rates.

simon

---

### Post by simontaylor on 2008-06-15
And Alienexplorers,

Did I say that you were a scholar and a gentleman? 

A thoughtless omission. You are both.

Thank you.

simon

---

### Post by alienexplorers on 2008-06-15
You may need the drivers for the VIA graphics card.  I don't know anything about them.  Post another thread and as if someone knows how to install the drivers for you graphics board.

---

