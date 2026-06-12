---
title: "Problems with my touchpad"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by solongsoho on 2011-11-22
I don't know if it's the laptop's problem or ubuntu's but every time after i open ubuntu, my touch pad only works for less than 1 minute. After this I have to reset the computer in order to having it work again. What can I do besides trowing my laptop on the window?

---

### Post by mikewhatever on 2011-11-22
You can provide some info about the laptop, like make and model (for example HP Pavilion 5269). You can also post the outputs of the following from a terminal window:

```

xinput --list

dmesg | grep 'touch\|mouse'

```

---

### Post by audiomick on 2011-11-22
Have you some way of finding out if the behaviour is the same with a different Operating System? Have you got Windows on there as well, for instance? You could also boot from a live CD of something else and see what happens there.

If the behaviour remains the same, then it is most likely something to do with the hardware (or maybe BIOS?), and if it doesn't it is probably only your Ubuntu install that is broken.

---

### Post by solongsoho on 2011-11-22
Compaq Mini 700

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; HID 04d9:0499                           	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Webcam-101                              	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]

And I haven't tried with another operating system as I don't really have a portable Cd-rom.

---

### Post by audiomick on 2011-11-22
Can you boot to a USB stick? Information about making one here
[https://help.ubuntu.com/community/Installation/FromUSBStickhttps://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStickhttps://help.ubuntu.com/community/Installation/FromUSBStick)

But wait and see what mikewhatever says about that output. Maybe he can see a problem there.

---

### Post by mikewhatever on 2011-11-22
The touchpad seems to be recognized as such, so I don't know why it doesn't work. Have you checked the configuration interface? Perhaps  the touchpad is just off? What version of Ubuntu do you use? Is it Ubuntu or one of the derivatives, for example Lubuntu?

Can you also post the output of **synclient | grep TouchpadOff**.

PS: Compaq Mini 700 is not known to have touchpad problems according to the wiki.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Compaq_Mini_700EF](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Compaq_Mini_700EF)

---

### Post by solongsoho on 2011-11-23
solongsoho@soho-Compaq-Mini:~$ synclient | grep TouchpadOff
    TouchpadOff             = 1

I am using the latest version of 11.10 so maybe there is a problem with it. Last night it worked all for more than 1 hour and today it doesn't work for 2 minutes. Thank you for helping me.

---

### Post by solongsoho on 2011-11-23
It works now, it looks like it was a bug from "disable touch pad while typing". It was deactivated even if i didn't type. Very strange, but it's solved. Thank you all for your help.

---

### Post by mikewhatever on 2011-11-24
Glad you figured it out. For the benefit of the community, you might want to post the solution. Others might have the same problem, and will stumble upon this thread when searching.

---

### Post by solongsoho on 2011-11-24
"Disable touch pad while typing" was enabled by default and it looks like from time to time it was disabled even though i wasn't typing. I just disabled it and now everything is fine.

---

### Post by RayArdia on 2011-11-30
Touchpad inoperative. Using Ubuntu 11.10 on an Acer 5735 laptop and have not had any prior problems.
Disabling the 'disable touchpad whilst typing' didn't work for me.
Don't know if it will throw any light on problem bu included below are the outputs of  'xinpùt --list


ray@ray-Aspire-5735:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Trackball                      	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Acer Crystal Eye webcam                 	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

and from  dmesg | grep 'touch\|mouse'

ray@ray-Aspire-5735:~$ dmesg | grep 'touch\|mouse'
[    1.054955] mousedev: PS/2 mouse device common for all mice
ray@ray-Aspire-5735:~$ synclient | grep TouchpadOff
    TouchpadOff             = 1

I don't know whether to try rebooting from my iso disk. Can I ask for some advice please?

Ray

---

### Post by RayArdia on 2011-12-02
This am touchpad worked OK for a few minutes (whilst writing/reading emails
then stopped being able to place the cursor even though the arrow can be moved from place to place. Just discovered that a sharp tap on the mousepad positions the cursor OK, so perhaps it's just that the contact suafaces are dirty. Is it relatively easy to dismantle and clean (I'm reasonably competant  with a small screwdriver!
Ray

---

### Post by ZamoraD on 2011-12-02
> **solongsoho said:**
> I don't know if it's the laptop's problem or ubuntu's but every time after i open ubuntu, my touch pad only works for less than 1 minute. After this I have to reset the computer in order to having it work again. What can I do besides trowing my laptop on the window?

You're lucky to have that one minute, man!
Mt touch pad doesn't work at all! I mean those two buttons work at random time, but what it means when touch pad failed to work?

_______
[mp4 to mp3 converter](http://mp4tomp3converter.org/)

---

### Post by Muscogulus on 2011-12-20
I have installed Ubuntu for the first time on an HP Pavilion DV6000. I wiped the drive and installed on a single partition. The version is 11.0.4. 

Once the login screen appeared the touchpad ceased working. I cannot move the cursor at all and I cannot enter text or select a text field with the keyboard. 

When I rebooted from the install CD, the touchpad also failed to work. (Of course it worked during the installation.) 

The touchpad never gave trouble when the machine was running Windows Vista. The hard drive is very healthy so I can rule out file corruption. 

I am out of ideas. :confused:

---

### Post by Muscogulus on 2011-12-21
Following up: I was stuck for a long time because I did not have a USB mouse for testing, as recommended [here]("https://wiki.ubuntu.com/DebuggingTouchpadDetection"). So I tried following the information gathering steps that follow. The documentation is confusing and internally contradictory, and I was stymied for a while by the [instructions for evtest]("https://wiki.ubuntu.com/DebuggingTouchpadDetection/evtest") which tell the user to "upload the log file" without explaining *which* log file or where it is located. 

Those pages desperately need some editorial attention. If I ever figure out what I'm doing, and am allowed to access the pages, I'll do it myself. 

Anyway, I finally located a USB mouse and am able to use it. So I now know that my problem is definitely not a bug in the kernel, and is probably not a bug in xserver (and I have a rudimentary understanding of what those are). The kernel is detecting the touchpad properly. Xserver may be detecting it properly. I can't be sure because ```
xinput --list
``` gives the result **Unable to connect to X server**

I am able to log in to the GUI, so I don't understand that error. (Maybe I don't really understand what X Server is.) 

P.S. Was I in error to post this to a thread that is flagged as SOLVED?

---

