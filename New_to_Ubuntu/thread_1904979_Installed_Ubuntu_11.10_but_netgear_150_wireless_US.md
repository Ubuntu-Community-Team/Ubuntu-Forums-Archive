---
title: "Installed Ubuntu 11.10 but netgear 150 wireless USB micro adapter WNA 1000M won't wor"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by LinuxRevolt on 2012-01-05
I installed **Ubuntu 11.10** on a **Dell Inspiron 8000 laptop** but can't get on the Internet.
I bought a netgear 150 wireless USB micro adapter WNA 1000M, but the installation CD is only for windows.
I thought I would be able to find a driver for this on the Internet, on my other computer, download it to my flash drive and then move it to the Dell Inspiron with Ubuntu and install the driver. Then I thought I could plug in the Netgear wireless adapter and it would take off. But I cannot find any such driver. I am a complete beginner and this is my first time to even see a linux installation. So please give me the simplest instructions possible. Thank you

[B]new hardware: netgear 150 wireless USB micro adapter WNA 1000M
version: UBUNTU 11.10[/B]

Check if already posted said: Sorry - no matches.

---

### Post by sandyd on 2012-01-05
> **LinuxRevolt said:**
> I installed **Ubuntu 11.10** on a **Dell Inspiron 8000 laptop** but can't get on the Internet.
I bought a netgear 150 wireless USB micro adapter WNA 1000M, but the installation CD is only for windows.
I thought I would be able to find a driver for this on the Internet, on my other computer, download it to my flash drive and then move it to the Dell Inspiron with Ubuntu and install the driver. Then I thought I could plug in the Netgear wireless adapter and it would take off. But I cannot find any such driver. I am a complete beginner and this is my first time to even see a linux installation. So please give me the simplest instructions possible. Thank you

[B]new hardware: netgear 150 wireless USB micro adapter WNA 1000M
version: UBUNTU 11.10[/B]

Check if already posted said: Sorry - no matches.
Post output of
```

sudo lsmod

```The WNA 1000M uses a Realtek RTL8188CUS Chipset.
Should be supported by rtl8192cu or the drivers at realtek
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS)

---

### Post by LinuxRevolt on 2012-01-07
Thank you. I'm really a raw beginner. What do I do with this information:
sudo lsmod
Do I find a prompt in Ubuntu 11.10 somewhere and put that into it?
You also said:
"The WNA 1000M uses a Realtek RTL8188CUS Chipset.
Should be supported by rtl8192cu or the drivers at realtek"
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS]("http://www.realtek.com.tw/downloads/...rue#RTL8188CUS")

I went to that website that I have no idea which thing to download. Can you give me a specific link for the netgear 150 wireless USB micro adapter WNA 1000M, to use on my Ubuntu 11.10 on a Dell Inspiron 8000 laptop?

Sorry for being a such a newbie.
Thanks again.

---

### Post by sandyd on 2012-01-08
> **LinuxRevolt said:**
> Thank you. I'm really a raw beginner. What do I do with this information:
sudo lsmod
Do I find a prompt in Ubuntu 11.10 somewhere and put that into it?
You also said:
"The WNA 1000M uses a Realtek RTL8188CUS Chipset.
Should be supported by rtl8192cu or the drivers at realtek"
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS]("http://www.realtek.com.tw/downloads/...rue#RTL8188CUS")

I went to that website that I have no idea which thing to download. Can you give me a specific link for the netgear 150 wireless USB micro adapter WNA 1000M, to use on my Ubuntu 11.10 on a Dell Inspiron 8000 laptop?

Sorry for being a such a newbie.
Thanks again.
Go to the Unity Launcher
Type in "Terminal"

Click "Terminal"

type in ```

sudo lsmod
```
and press enter

---

### Post by gNOLE81 on 2012-01-09
Were you ever able to install this?  I bought a Rosewill RNX-miniN2 and have the same problem.  I am a complete beginner, so I'm all thumbs when it comes to getting drivers into Ubuntu...

---

### Post by wildmanne39 on 2012-01-09
Hi gNOLE81m you should start your own thread that way you can get the help you need and so can the person that created this thread.
Thanks

---

### Post by LinuxRevolt on 2012-01-16
I found terminal and ran the code. It gave me a string of technical code. Thank you, but now what?

---

### Post by wildmanne39 on 2012-01-17
Hi, post all the output of that command here by clicking on new reply and click # and paste the information between the brackets.
Thanks

---

### Post by Fernhill Linux Project on 2012-01-17
Here is a tip for complete beginners with wifi problems. 
Try making a wired internet connection and then run 'additional drivers' from the dash, as this may resolve the problem.

---

