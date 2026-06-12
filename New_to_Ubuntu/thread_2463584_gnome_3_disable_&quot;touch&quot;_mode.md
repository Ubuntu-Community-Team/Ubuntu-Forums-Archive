---
title: "gnome 3 disable &quot;touch&quot; mode"
date: 2021-06-14
forum: New to Ubuntu
---

### Post by jwenge on 2021-06-14
Hello,


Hope to be in the right place with my post (sorry if not). I have a problem with an Epson beamer model (695wi). I imagine that's the same with all touch devices that support multi-touch with the Ubuntu 20.04 (gnome version). It goes into touch mode (no more cursor, applies different gesture recognition etc. ). This mode is very interesting except that it does not work as well as it should work (random click, gesture rarely understood by the system etc.)! Maybe it's an hardware problem (695wi). Anyway this problem occur with all 695wi beamers i tried (something like 10 or more..) and my users can't use their computers like this. 


Do you have any idea how to turn off this feature while still keeping the touch of my screen ? -> on my previous configuration (mint 18.3) the (touch) screen was considered as a mouse and ubuntu (mint) did not switch to its "touch" mode and everything worked correctly. 


- I tested with xinput, I can't remove this mode .. I can see several pointing devices but despite deactivation nothing happens until the pure and simple deactivation of the touch screen.
- tested with the evdev conf and nothing to do. it's either everything or nothing .. 


Thank you for your help.

---

### Post by MAFoElffen on 2021-06-15
I must be confused. 

By your post content as a whole, I initially assumed that you where talking about a tablet, or a 2-In-One... Where it is going into Tablet mode. But When I look up "Epson 695wi", all I see is a projector. Am I wrong with that? What is Ubuntu running on?

From what you are asking and trying, I interpret that as can the Tablet mode by disabled, while still keeping touch screen input, as with the modes of a touch screen laptop or notepad. Right? That is what I am looking into.

In the meanwhile, you said you tried to use xinput... What was the results of 
```
xinput --list

```

---

### Post by jwenge on 2021-06-23
Thank you very much for your answer. It is a projector with a touch unit (laser scanning sensor) used for teaching primary classes. A kind of "next gen blackboard".

xinput --list :

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Primax HP USB Keyboard Consumer Control 	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Wireless Mouse PID:003f        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Wireless Keyboard PID:0045     	id=14	[slave  pointer  (2)]
&#9116;   &#8627; PixArt HP USB Optical Mouse             	id=15	[slave  pointer  (2)]
&#9116;   &#8627; EPSON EPSON EPSON 695Wi/695WT Mouse     	id=16	[slave  pointer  (2)]
&#9116;   &#8627; EPSON EPSON EPSON 695Wi/695WT Mouse     	id=17	[slave  pointer  (2)]
&#9116;   &#8627; EPSON EPSON EPSON 695Wi/695WT Mouse     	id=18	[slave  pointer  (2)]
&#9116;   &#8627; EPSON EPSON EPSON 695Wi/695WT           	id=19	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Primax HP USB Keyboard                  	id=10	[slave  keyboard (3)]
    &#8627; Primax HP USB Keyboard System Control   	id=12	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=20	[slave  keyboard (3)]
    &#8627; Primax HP USB Keyboard Consumer Control 	id=21	[slave  keyboard (3)]
    &#8627; Logitech Wireless Keyboard PID:0045     	id=22	[slave  keyboard (3)]

---

### Post by jwenge on 2021-06-23
> **MAFoElffen said:**
> 
From what you are asking and trying, I interpret that as can the Tablet mode by disabled, while still keeping touch screen input, as with the modes of a touch screen laptop or notepad. Right? That is what I am looking into.


The problem is that a lot of content is unusable with this "tablet mode" because the click, double click etc ... actions are too risky. Until now I used a mint 18 version and this beamer was recognized by the system as a mouse so no multi-touch but a more reliable behavior. the goal is to find out how i can keep the touchscreen function like a mouse and force ubuntu not to go into "tablet" mode.

---

### Post by jwenge on 2021-08-10
any idea ??

---

### Post by jwenge on 2021-08-18
I found a solution that worked for me. Thanks to : 


[https://askubuntu.com/questions/927022/how-can-i-disable-touchscreen-while-using-wayland](https://askubuntu.com/questions/927022/how-can-i-disable-touchscreen-while-using-wayland)


If I disable the hid_multitouch driver the beamer is not recognized as a touch screen by the system but as a mouse. This does not enable the touch mode.


==========


create the file hid_multitouch.conf in /etc/modprobe.d


Inside the file :


# Use the following syntax
# blacklist driver-name
blacklist hid_multitouch

---

