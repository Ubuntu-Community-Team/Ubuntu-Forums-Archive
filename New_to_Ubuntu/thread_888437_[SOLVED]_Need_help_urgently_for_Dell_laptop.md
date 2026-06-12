---
title: "[SOLVED] Need help urgently for Dell laptop"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-13
Disclaimer: I'm almost computer retarded, so when answering my questions, please have a lot of patience and try to provide idiot-proof answers that even my grandma would be able to understand without much difficulty ;) Thanks.

I'm currently installing Ubuntu 8.04 on another laptop (yes the installation is going on *right now*). It's a Dell Inspiron 640m. I'm currently using my friend's Windows laptop.

1. Here's the problem, I realized I haven't downloaded drivers for anything (after I clicked the install button) which was a huge mistake. So does that mean all my hardware would be dead/unusable?

2. I tried Dell.com, but all the drivers there were only for Windows XP or Vista. Can anyone tell me where I can find drivers for the most basic stuff like sound and wifi?

3. Right now I desperately need to know how to get the WIFI going, because I think most of my problems would be solved once I can get online and seek help using my own computer; it's not very convenient to have to borrow a laptop to seek help every time. When I did a test run by booting from CD, I couldn't turn the wireless thing on with Fn+F2 Hotkey, in fact, none of the LEDs were lit up and couldn't be lit up, and I don't even know how to scan for available wireless networks in the area, can anyone tell me how to do this?

So what do I do now? I'm stuck with a machine that's got Linux and nothing else on it :( Any help appreciated. Thanks in advance.

---

### Post by shae on 2008-08-13
Linux is unlike windows.  Most drivers are installed by default.  The one problem you may face is wireless depending on who made your wireless chipset.  Did wireless work on the live CD?  If it did then it will work out of the box!  If it did not, what Wireless card do you have?

---

### Post by hyper_ch on 2008-08-13
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by nothingspecial on 2008-08-13
You shouldn`t need to download drivers. 
Don`t panic until the install has finished. Hopefully everything will work straight away. 
If something dosen`t post back here.

---

### Post by zzzonked on 2008-08-13
Wow! I didn't expect a response this fast! Thanks.

Wireless didn't work on the live CD. I don't even know whether it worked or not actually, all I know is when I opened Firefox it gave me a Page Load Error, so I suppose I wasn't connected. How do I even check whether I'm connected? The "connection" logo has a small exclamation point at its bottom right, which I suppose means something's not right with my connection. This is what it says on my Device Manager: Intel PRO/Wireless 3945ABG Wireless Connection.

The laptop that's running the installation now used to be a Vista laptop, until a few minutes ago when I installed Ubuntu. I'm just saying this so you know it's not designed for Linux, but for Vista. Yeah.

Edit: Sorry for the vague title. Changed it :)

---

### Post by Dill on 2008-08-13
I actually have the same wireless card and it worked out of the box for me on a Dell Inspiron e1405. Do you have lights to indicate whether or not the wireless card is turned on? You should see them grouped with the Caps Lock and Num Lock lights above the keyboard, just below the screen (you'll probably have a green light labeled "Wifi" and a blue light for Bluetooth). You should be able to toggle the wireless card with the Function key (labeled "Fn", neat the bottom-left of your keyboard) and F2. Try holding Fn and F2 simultaneously and let me know if you see any lights come on.

If you do see any lights come on, try clicking on the Network manager icon near the top-right hand corner of your screen (the two computers), click on "Manual Configuration", and let me know if your wireless card shows up among the list.

---

### Post by scotcella on 2008-08-13
Go to System -> Administration -> Network and see if you can type in the wireless Essid and password. Shouldn't be that hard to set it up. 

Give that a try.

---

### Post by scotcella on 2008-08-13
I have a Dell myself, even though I'm not using it, from memory the light never came on for me, but I always knew it worked when i turned it on/off using the normal function buttons but the lights never worked- but worked fine in windows..  maybe yours is the same?

---

### Post by zzzonked on 2008-08-13
I'm sorry if I confused anyone with misleading sentences or something, but here's what I was trying to say:

I'll just give you the exact scenario. I'm now sitting in a public library which provides free wireless internet access without a password. In Windows, this is what I would've done: Double-click on the network manager icon on bottom right of the screen, choose the option that says "LibraryWiFi" among 10 others that my computer has detected, and click connect. Then I'd be connected. Now how do I do that in Ubuntu? Does this make the question clearer?

---

### Post by Dill on 2008-08-13
If you click on the icon that looks like two juxtaposed computers near the top-right hand corner of your screen, you should see a menu pop down. If your wireless card is on and if everything worked out of the box (which it very well may have), you should see the network under the heading "Wireless networks." Is that clear?

Cheers, 
Dylan

---

