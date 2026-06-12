---
title: "HOWTO: Adjust Touchpad Speed"
date: 2006-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by adds2one on 2006-08-05
This HOWTO is for people who are using synaptics for their laptop touchpad. Please someone correct me if I am wrong, but I believe that synaptics is installed by default for your laptop touchpad when you install Ubuntu 6.06.

I decided to make this HOWTO after solving my own touchpad problem. The issue was that when I adjusted the mouse speed in Gnome via System->Preferences->Mouse->Motion there was no affect on the motion of my touchpad.

Some quick searching revealed a lot of people having the same issue and I could not find any information on how to resolve it. A little sleuthing in my machine and I found the answer!

Below I will show you how to adjust the way your touchpad reacts by editing your /etc/X11/xorg.conf file. I will also show you where to find more information on customizing your touchpad's behaviour.

**EDITING /etc/X11/xorg.conf**

There are many ways to edit files in Linux. To make it really easy I will use a text editor called gedit. (Normally I use vi but you can use whatever text editor you are comfortable with.)

1. Open a terminal

2. Type: ```
sudo gedit /etc/X11/xorg.conf
```

3. You will be prompted for your password. Enter it.

4. gedit will now open. You should scroll down until you see a section that looks somewhat like this:
```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"	
EndSection
```

5. What we need to do is add a couple of options. We will add one for MinSpeed, one for MaxSpeed and one for AccelFactor. The values that you give these options will determine the sensitivity of your touchpad. Here is my /etc/X11/xorg.conf entry for the touchpad:
```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "MinSpeed" "0.5"
	Option	    "MaxSpeed" "0.5"
#      Option      "AccelFactor" "0.0010"
EndSection
```

6. You can play with different values for MinSpeed, MaxSpeed and AccelFactor but keep in mind that they must be floating point values (decimal numbers) and that an entry of 1.0 is *very* fast! If you want acceleration then set the MinSpeed lower than the MaxSpeed and play with different values for AccelFactor. 

If you do not want acceleration then make your MinSpeed and MaxSpeed the same. (For good measure you can see that I have also commented out the AccelFactor option. Whenever you see a line with a # at the start of it that means that the rest of that line will be ignored by the system as a 'comment'.)

7. Now you need to save the changes you have made to /etc/X11/xorg.conf and then close the file and reboot.

8. Once you reboot try your new touchpad settings and make further adjustments to the /etc/X11/xorg.conf file until you have the perfect settings for you.

For more information on other options for the touchpad type:```
man synaptics
```

or 
```
gedit usr/share/doc/xserver-xorg-input-synaptics/README.Debian
```

or ```
gedit /usr/share/doc/xserver-xorg-input-synaptics/README.alps

```

I hope that this HOWTO has been helpful to you. If you have any questions please post them and I will do my best to help. 

Good luck and happy mousing!:D

---

### Post by skecherkid on 2006-08-06
Thanks for this information - I am a real n00b and this is the first forum help that I have been able to use -  its clear, no assumptions, and best of all it solved my problem first try!

---

### Post by adds2one on 2006-08-07
I am happy to know I helped you. :D

By the way here is the /etc/X11/xorg.conf settings that I have finally settled on for my touchpad. I find this works well for me on my laptop but you will have to see for yourself:

```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "MinSpeed" "0.5"
        Option      "MaxSpeed" "0.7"
        Option      "AccelFactor" "0.0350"
EndSection

```

---

### Post by JacobRogers on 2006-10-29
This guide helped me a lot.

---

### Post by adds2one on 2006-10-29
Glad to have helped!:)

---

### Post by Rob2687 on 2006-10-29
Another way to do it is to just add this to xorg.conf
Option          "SHMConfig"             "on"

Then apt-get install gsynaptics/qsynaptics/ksynaptics.

---

### Post by dpm on 2006-10-31
> **Rob2687 said:**
> Another way to do it is to just add this to xorg.conf
Option          "SHMConfig"             "on"

Then apt-get install gsynaptics/qsynaptics/ksynaptics.

That's a killer tip, many, many thanks.

And thanks also to **adds2one** for the original HOWTO.

Cheers.

---

### Post by kelbizzle on 2006-11-01
I'm curious....before you guys did that did you mouse kinds jiggle back and forth is short movments really fast when you rested your finger on it?

---

### Post by adds2one on 2006-11-02
Mine never did that. I just didn't like the 'action'.

---

### Post by mike_pasara on 2008-01-26
Thank you everyone.

I kept my min the same and my max is 0.8 and acceleration is the same adn i'm happy.

---

### Post by NovaAesa on 2008-01-27
I used the following settings in xorg,conf and it worked great xD

```
        Option      	"MinSpeed" 		"0.5"
        Option      	"MaxSpeed" 		"0.7"
        Option      	"AccelFactor" 		"0.0350"
```

Many thanks to adds2one, I was resorting to using an external mouse before. This has helped heaps!

---

### Post by Philo1 on 2008-01-30
Awesome! This is exactly...hmm one thing that I've been looking for. I am working with a dell and this works great, thanks.

Option		"MinSpeed" "0.5"
Option		"MaxSpeed" "0.5
Option		"AccelFactor" "0.0010"

---

### Post by fsr_elite on 2008-02-04
Great. One additional thing -- rather than restarting your PC, just restart the XServer. Hit ctrl-alt-backspace to do this -- makes iterating through settings faster.

---

### Post by fuwkej on 2008-02-19
Worked great, thanks!

---

### Post by redseventyseven on 2008-03-28
I tried Rob2687's suggestion first. I was attracted to it because I didn't fancy having to edit settings by hand in xorg.conf and restart the X-server every time I wanted to test it out.

Unfortunately I found that this solution caused a conflict as the system thought a non-GNOME element was interfering with the GNOME settings. So I removed the...

```
Option "SHMConfig" "on"
```

...line and then went with the OP's first solution. No conflicts, and in fact the suggested settings further down this thread worked very well indeed with very little tweaking. Much better than the rather obscure gsynaptics program (not to be confused with synaptic!)

---

### Post by aidave on 2008-04-02
Thanks, I was about to whine and complain about this.

Why do we have to REBOOT to change the mousepad speed? Thats silly.  People told me Linux doesnt need to reboot ... except when changing mouse speed!! LOL

---

### Post by Daboo on 2008-07-08
Thanks for this - the manual config worked, but gsynaptics' sensitivity adjustment slider did nothing. I added that line inside the touchpad config, maybe it was supposed to go elsewhere? It was useful for disabling vertical scroll though. _So_ irritating!

---

### Post by frodon on 2009-04-27
It works like a charm, thanks for the tutorial.

BTW killing X (Ctrl+Alt+Backspace) is enough no neEd to reboot.

---

### Post by frodon on 2009-04-27
It works like a charm, thanks for the tutorial.

BTW killing X (Ctrl+Alt+Backspace) is enough no neEd to reboot.

---

