---
title: "Trackpad now recognized as Generic PS/2 Mouse - how to get it back?"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by sendbrianspam on 2014-07-27
I've been using Linux for about a year now.  Let me start off by saying that I am a horrible computer user.  I run a lot of physics programs that are tricky to install.  When I run into issues, I search forums for solutions, and do a lot of copy paste of code into the terminal without fully understanding what I'm doing.  I keep at it until it works.  I've broken some things before, but have been able to recover with more searching until now.  This issue isn't terrible, but it's a bit annoying since the trackpad doesn't work as well and is missing features.
  I first noticed when the trackpad wasn't double clicking as well or started dragging things when I didn't want it to.  I went into settings and the "Mouse and Touchpad" no longer had the touchpad tab.  I have an Asus X202E with touchscreen and trackpad.  In searching, I've read that sometimes having a touchscreen causes issues, but this used to work just fine.  If I type xinput list, I get the following:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

Some things that recently happened that I think might be related,

1.  I got the message that the Hardware Enablement Stack was due to expire and the update manager suggested that I install the new hardware support.  I did, and ignored some dependency problems.

2. I can't remember what precipitated the issue, but something I did caused my trackpad to completely lose function.  I found a solution that said to add the following commands into /etc/rc.local :  "modprobe -r psmouse"  & "modprobe psmouse proto=imps".  This kind of "fixed" my mouse situation to get me where I am now, with it only recognized as a PS/2 mouse.




Just now, I removed those two lines and rebooted.  When I ran xinput list, I got:
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer          	id=10	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

Which correctly shows the touchpad, but at that point, the touchpad didn't work.  The only way I know how to make it work again is to type  "modprobe -r psmouse"  & "modprobe psmouse proto=imps", which makes it go back to being a PS/2 Mouse.

What else can I do to try to get my touchpad back as a touchpad?

---

