---
title: "Adsl usb"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by economy on 2008-09-22
Hi, 

Over the last week I've had a couple other threads, but they're long gone now (at least I've lost them). I've had a lot of help with this issue, from a couple of very helpful users, but I'm still stuck. My situation again:

I'm in China running a Conexant AccessRunner USB ADSL modem which with a great deal of difficulty I got working in Windows. Then I got fed up with Windows Vista and now I want to connect using Ubuntu. I have the firmware saved in /usr/lib/firmware and the modem has three lights: power, link and data. With the firmware, I am able to get the link light solid after about 20 seconds. 

Running **lsusb** in the terminal shows an ADSL modem with the Connexant signature on the right port.

**ifconfig** according to a couple of posts shows that the OS recognizes the modem

**pppoeconf**says that on two devices (eth0, wlan0) the Access Concentrator did not respond.

I have installed rp-pppoe and tried every reasonable configuration I can think of, but when it dials it times out.

I have installed usbadslmodemmanager and it doesn't recognize either firmware or usb modem (could be because the software was made for SpeedTouch 300's). 

I have created and edited files that start pppd on boot and provide pap-secrets and chap-secrets with the username and password appropriate for the proprietary software I normally use in Windows. When I boot Ubuntu, it asks me for permission to run pppd, and after I give it permission, nothing happens.

It seems to me that the OS knows I have a USB ADSL modem plugged in, but doesn't know how to provide it with the username and password that will allow access to the internet. I feel like I've exhausted my options, but then with each thread I get new information.

Help! I don't wanna go back to Vista!

---

### Post by lian1238 on 2008-09-22
Hi,

It's very troublesome to get a USB modem working in Ubuntu. I've been there. I have BIPAC 7000 which I got working by follow the instructions [here]("http://www.siamgeek.com/2008/04/getting-online-with-bipac-7000-in-ubuntu/"). I don't know if it's any help, but maybe you could "adapt" the technique for your modem.

Good luck.

---

### Post by economy on 2008-09-22
lian,

thank you for the information! every bit helps... and hopefully soon i'll find the bit that has the answer. i realize i have jumped in the deep end as far as learning how to negotiate connectivity with an OS that's frankly alien to me, but the real benefit of making the switch is driving me.

now that i'm looking... what is br2684ctl? i don't remember seeing anything about it, and i don't think i have it... and according to your link, it was the missing piece of the puzzle for these people!

---

### Post by lian1238 on 2008-09-22
Hi,

I do not know what br2684ctl is either. It could be specific to BIPAC 7000. You could try it though, and hope it works.

I had problems even with my BIPAC 7000. When I boot up, my modem would keep blinking and I could only connect after it stops blinking. In windows, the blinking process is "Connecting... Disconnected". Sometimes I need to take the USB out and plug in again.

I got tired of the USB modem. Now, I got a wireless router to avoid the USB altogether, (and to share my net with my friend).

---

### Post by economy on 2008-09-22
lian,

believe me, i'm all about easy. it's just impossible to buy a new modem when the internet connection is being managed by my company here and there is literally no hotline i can call to get information (and that's assuming my chinese is good enough to talk about advanced internet issues with someone in the first place).

like i said, it was finicky even getting the thing to run in vista. it took me the better part of 2 weeks to get through the chinese to install the software and dlls and all that windows crap to make it work. apparently i somehow stumbled upon the world's most unnecessarily complicated internet connection! 

i'm returning to the states in 4 months, and there are WiFi spots nearby which connect no problem, but i'd like to have connectivity at home so i can make the full switch.

thanks for the info, i'll keep trying

---

### Post by bhadotia on 2008-09-22
> **economy said:**
> 
Over the last week I've had a couple other threads, but they're long gone now (at least I've lost them).
You can find your threads by clicking on the search link in the bar on the top, there in the end you find a link "Find All Your Threads".

---

