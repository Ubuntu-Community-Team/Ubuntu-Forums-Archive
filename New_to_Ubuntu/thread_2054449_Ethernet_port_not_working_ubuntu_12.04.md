---
title: "Ethernet port not working ubuntu 12.04"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by paulf5791915 on 2012-09-07
Hi,
I have a problem with my cable connection : when I plug in the cable I cannot see the light.
To be precise I see the light only for a moment when I switch my notebook on and then it disappears. If I check the network settings it says that the cable is unplugged.
I have a HP dv6 notebook with ubuntu 12.04...I tried to understand the problem reading some previous posts on this forum but it didn`t help.
Also I`m not so good with the terminal so...I would really like if someone could guide me through the solution.
Thanks in advance.

---

### Post by Epodx64 on 2012-09-07
Check your systems bios and make sure your onboard lan is turn on.

---

### Post by gordintoronto on 2012-09-07
Can you be more specific than "DV6," which is a large family of computers?

Do you dual-boot?

In the manual for the computer, does it describe how to disable and enable the Ethernet port? Probably with a keypress of some sort, which may or may not work in Ubuntu.

---

### Post by Carl.Spackler on 2012-09-07
> **Epodx64 said:**
> Check your systems bios and make sure your onboard lan is turn on.

^^^ This

...and make sure that if you have an option for "LAN switching" in you BIOS that it is turned _off_. This is a function that says if you have a wifi connection available or if you wifi adapter is on, the LAN port is turned off (power savings reasons I suppose).

---

### Post by paulf5791915 on 2012-09-08
I'm sorry for not answering but only now I have the connection(wifi).
Anyways, I checked the bios and the lan option but still it doesn't work and the light disappears as soon as the OS loads.
My PC is an HP pavilion dv6-3117sl. 
What does it mean dual-boot?(sorry but with technical stuff I'm an absolute beginner).

---

### Post by gordintoronto on 2012-09-08
When you turn on the computer, can you choose to run either Windows or Ubuntu? That is "dual boot."

As a comment, you should not put too much faith in the lights on HP laptops. I have a G62 which, according to the lights, has the wireless disabled. However, that is how I connect to my network.

Does your WiFi work?

---

### Post by paulf5791915 on 2012-09-09
No, I don't dual boot. I have only ubuntu on. The wifi works pretty well.
Apart from the lights, the Network Manager still says the cable is unplugged so...

---

### Post by paulf5791915 on 2012-09-09
I heard some people saying that I may have to install additional drivers but I don't know which drivers and how to get it(if that is the problem).

---

### Post by gordintoronto on 2012-09-09
When you are in Ubuntu, click on the Dash (top-left) and type addit

Additional Drivers should appear. When you run it, just wait for a minute, and if there is a relevant driver available, it will appear. Then you can click on "Activate." If a video driver appears, you can leave it for now.

If you run Terminal and type in the command: lspci

a list of devices should appear. One or two of them should begin "Ethernet controller." If only the wireless one shows up, then the wired Ethernet controller is disabled or not functioning. If the wired one appears, could you please copy and paste what it says into a message?

---

### Post by paulf5791915 on 2012-09-10
That's what it says about ethernet:
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

---

### Post by gordintoronto on 2012-09-10
I have a very similar Ethernet controller (rev 02) but I have always used wireless.

This blog post might help you:
[http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

It's a lot more complicated than I had hoped. Let me know if you get stymied at any point.

---

### Post by Hadaka on 2012-09-10
Hi , i did a search for your computer and came up with this, The page also
stated you have an automatic setup/detect once the connection is seen.

[LIST=1]
[*]Unplug the power to the router and the modem, and turn off the computer. 
[*]Reconnect power to the modem and wait while the modem resets the connection.  LEDs will glow when connection is established.
[*]Reconnect power to the router and wait while the router resets the connections.   LEDs will glow when connection is established.
[*]Turn on the computer and wait while it starts into. 
[*]Open the Internet  browser and connect to a web site on the internet. 
[/LIST]
also you really should load the updates, there may be updated files that
will eliminate this problem, not to mention security issues.

---

### Post by paulf5791915 on 2012-09-12
Hi, sorry for not answering in the last few days but I have very few chances of getting a decent connection until I fix this problem.
Anyway, I tried to follow the instructions from the link. I managed to install the new driver(r8168) but now the problem is that I can't get rid of the old one.
I tried to blacklist it from the terminal but it reports an error (-1 file detected..something like that). I also tried manually from blacklist.conf(opening it with a text editor) but it says I don't have the permission to modify it because I'm not the owner. Now, I'm the only user of this PC and "the administrator", so why does it say so? 
Have you got any suggestion to make r8168 work instead of r8169?

---

### Post by Wim Sturkenboom on 2012-09-12
> 
I also tried manually from blacklist.conf(opening it with a text editor) but it says I don't have the permission to modify it because I'm not the owner. Now, I'm the only user of this PC and "the administrator", so why does it say so? 

Because root is the owner (I guess). So use something like *_sudo vi yourblacklistfile_* to edit the file; replace vi with the editor that you're comfortable with.

Can't help further, sorry.

---

### Post by paulf5791915 on 2012-09-12
Ok, thank you...but how can I edit it?? I mean, there is no editor I am comfortable with.

---

### Post by Wim Sturkenboom on 2012-09-12
What did you use the previous time? vi, nano, ...., gedit?

For gedit, I think the command in a terminal is gksudo gedit .....

---

### Post by gordintoronto on 2012-09-12
+1

If you cd to the folder where the file lives,
gksudo gedit blacklist.conf

---

### Post by varunendra on 2012-09-13
Please tell us exactly where you got the driver from, its version and how you installed it. The autorun.sh script provided by realtek along with the driver should have automatically done the required blacklisting.

You can manually do so with :
```
gksu gedit /etc/modprobe.d/blacklist.conf
```Enter the above command in terminal as suggested above or in the standard 'Run' dialogue by pressing Alt+F2.

Hope blacklisting is all you need. Else you may find this post by *abriano* helpful : [http://ubuntuforums.org/showthread.php?p=12169651](http://ubuntuforums.org/showthread.php?p=12169651)
You may also wish to look at original troubleshooting steps provided by *praseodym* or others in that thread.

---

### Post by paulf5791915 on 2012-09-13
Thank you very much, I managed to edit the file and now the driver is up and running!

---

### Post by gordintoronto on 2012-09-13
And is it working? If so, please mark this thread as "solved." I think it's under "Thread Tools."

---

