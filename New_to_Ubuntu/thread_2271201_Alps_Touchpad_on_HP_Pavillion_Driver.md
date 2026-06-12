---
title: "Alps Touchpad on HP Pavillion Driver"
date: 2015-03-28
forum: New to Ubuntu
---

### Post by sushrutbhalla11 on 2015-03-28
Hi,

I am on an HP pavillion. I installed Ubuntu on it but I can't find the driver for my Alps touchpad. So everytime I type and my palm touches the trackpad, it selects the wrong window.
Here is the output of xinput
~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Truevision HD                        	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                     	id=12	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]

I can't see any options for disabling touchpad in my system settings either.

I installed pmouse driver and restarted but no luck. I also installed pointing devices from the "Ubuntu Software Center" but it didn't have the option either.

Thank you.

---

### Post by chopra on 2015-03-28
I've got an HP pavilion too, and faced the exact same problem. Most laptops have a hot key to disable the touchpad where F5 is, but not HP.
Try this: 

xinput set-prop "SynPS/2 Synaptics Touchpad" "Device Enabled" 0

To re-enable, just replace the 0 with a 1.  This will not survive a reboot, or logging off and logging back on, unless you place it in your .bashrc file.


Chopra

---

### Post by sushrutbhalla11 on 2015-03-31
Hello Chopra,

Thanks for your reply. But the issue is with Alps touchpad not with Synaptics Touchpad. Could you help me with the Alps touchpad??

Thanks

---

### Post by chopra on 2015-04-06
I've never used an alps touch pad, sorry. Maybe someone else here has.  In the meantime, there is a temporary fix, perhaps. One rather unsophisticated option that worked for me in the past (if there are no hot keys to disable it) is to just take a thick piece of cardboard and tape it over the touchpad.  I used a piece of cardboard from a box of chocholates.  One from a legal pad isn't thick enough.

It's crude, but it works, and it won't stop you from closing your laptop.

Chopra

---

