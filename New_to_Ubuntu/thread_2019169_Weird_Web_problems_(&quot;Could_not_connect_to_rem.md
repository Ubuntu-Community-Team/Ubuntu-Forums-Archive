---
title: "Weird Web problems (&quot;Could not connect to remote server&quot;)"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by George99 on 2012-07-07
After testing a lot of Linux distributions I finally stranded at LUBUNTU, it was the fastest. But still I often have some weird problems with the connection to the web using [COLOR="Red"]Thunderbird[/COLOR], [COLOR="red"]Firefox[/COLOR], [COLOR="red"]Opera[/COLOR] or [COLOR="red"]Google Earth[/COLOR] (sometimes all at once).

The weird about this is if I'm listening to a live web radio, it will not disconnect while I get the message "[COLOR="red"]Could not connect to remote server[/COLOR]" no matter which of the above named programs I'm using, this message comes on every one of them, but only randomly. I even waited a long time, in case the buffer of that received radio data stream would be very large, but it keeps on playing and playing. So I can't tell if this error vanishes by itself.
When this error happens while I'm trying to send a mail, I retry to send it up to 15 times, than normally it works, sometimes sooner. Just like any browser, pressing F5 as often as necessary until I receive data.
And often the system runs nuts, the processor goes up to 100%, but the system monitor doesn't show any job that uses that much CPU, but I can't tell if this another error. It happens that the system freezes in, power button is the only solution.

[COLOR="Red"][SIZE="3"]**How can I find out what is causing this problem? **[/SIZE][/COLOR] [img]http://www.greensmilies.com/smile/smiley_emoticons_daumendreh2.gif[/img]

The web connection works per WLAN. Until now I couldn't reproduce that error, it comes randomly only, but daily. If you need any further information to help, let me know.

Please and thank you.

---

### Post by doctorbighands on 2012-07-07
> **George99 said:**
> After testing a lot of Linux distributions I finally stranded at LUBUNTU, it was the fastest. But still I often have some weird problems with the connection to the web using [COLOR="Red"]Thunderbird[/COLOR], [COLOR="red"]Firefox[/COLOR], [COLOR="red"]Opera[/COLOR] or [COLOR="red"]Google Earth[/COLOR] (sometimes all at once).

The weird about this is if I'm listening to a live web radio, it will not disconnect while I get the message "[COLOR="red"]Could not connect to remote server[/COLOR]" no matter which of the above named programs I'm using, this message comes on every one of them, but only randomly. I even waited a long time, in case the buffer of that received radio data stream would be very large, but it keeps on playing and playing. So I can't tell if this error vanishes by itself.
When this error happens while I'm trying to send a mail, I retry to send it up to 15 times, than normally it works, sometimes sooner. Just like any browser, pressing F5 as often as necessary until I receive data.
And often the system runs nuts, the processor goes up to 100%, but the system monitor doesn't show any job that uses that much CPU, but I can't tell if this another error. It happens that the system freezes in, power button is the only solution.

[COLOR="Red"][SIZE="3"]**How can I find out what is causing this problem? **[/SIZE][/COLOR] [img]http://www.greensmilies.com/smile/smiley_emoticons_daumendreh2.gif[/img]

The web connection works per WLAN. Until now I couldn't reproduce that error, it comes randomly only, but daily. If you need any further information to help, let me know.

Please and thank you.

I seem to recall running into something very similar to this some time ago, and it had something to do with IPv6 settings in Firefox (in the about:config area) and in Network Manager. I don't remember exactly what the fix was, but hopefully this sets you along the right path.

---

### Post by gordintoronto on 2012-07-07
Instead of using System Monitor, try a command-line window: top

---

### Post by George99 on 2012-07-09
> **doctorbighands said:**
> I seem to recall running into something very similar to this some time ago, and it had something to do with IPv6 settings in Firefox (in the about:config area) and in Network Manager. I don't remember exactly what the fix was, but hopefully this sets you along the right path.

Thanks for that tip. 
I found these settings in Firefox and Thunderbird and even in the network management and changed the settings. Didn't find anything for Opera.

I changed at Firefox and Thunderbird:
ntwork.dns.disableIPv6, user set, boolean, **true** (from false)

At network connections, editing connection
IPv6 Settings, Method, **Ignore ** (from Automatic)

But it still happens (randomly) that the connection only works after multiple retries. Perhaps do these settings have to be changed in the WLAN router, I don't know, but I couldn't do that because it is not my network.

---

### Post by George99 on 2012-07-09
> **gordintoronto said:**
> Instead of using System Monitor, try a command-line window: top

Thanks for that tip, this is something new for me again. I will try it out at the next CPU overload.

UPDATE:
OK, didn't take long.
In my panel of Lubuntu I got the item "CPU usage Monitor" to see if the CPU is in stress. I had an overload again and nothing worked anymore. After a reboot, I started the LXTerminal and entered "top" and set the layer to "always on top".
But it happened again, the CPU usage monitor was completely in green (100%), even the system clock didn't count up regularly anymore, but the "top" display didn't show me anything abusing the system. 
That's weird.

---

### Post by George99 on 2012-07-09
Update:

I think the reason for this is not in the single applications. It is either the WLAN or the operating system itself.
It can't be that Firefox, Opera, Thunderbird, Google Earth and Pidgin have the same problem.

I will try to start some web applications on Windows. If this problem comes from the WLAN, the connection problem should appear there, too.

---

### Post by George99 on 2012-08-19
I made several tests with Windows XP, no connection problems there. Than I tried to sign on with "Openbox" instead of Lubuntu or LXDE. No problems with Openbox.
So it seems that I have to wait until Lubuntu 12.10 is available, to make a complete new installation. :icon_frown:

---

### Post by George99 on 2012-09-08
[CENTER][SIZE="4"][B][COLOR="Red"]Just installed LUBUNTU 12.10
Problems vanished[/COLOR][/B][/SIZE]
[[img]http://www.greensmilies.com/smile/smiley_emoticons_hurra2.gif[/img]](http://www.greensmilies.com/)[/CENTER]

---

