---
title: "Completely new to Ubuntu: Internet issues"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by CeolanM on 2012-08-15
Hey guys, I'm new to the forum.

I installed Ubuntu a while back, about a year ago, but I remember having internet issues with it. I was presuming it was because i was running it on a netbook with 1gb memory :)

Anyway, i got a new proper laptop and I'm having EXACTLY THE SAME issue. I log onto ubuntu, and i try connect to my wireless internet and it doesn't show up. There is an option to add an internet connection, but it has me putting in alot of info about the network that i frankly dont know where to get, and if i do, i'd want to make sure it works if i do that,

I literally only installed it only an hour so apologies if i sound completely unsavvy to ubuntu language

Thanks in advance! :)

---

### Post by Kickinthedoor on 2012-08-15
Ive had that problem too. Search the forum.... I know there is alot of threads on how to fix the issue. Last time all it took was one line of code in terminal. I believe it wss the a package manager or somthing along those lines. Good luck

---

### Post by cogier on 2012-08-15
Welcome to the forum.

If you tell us which computer you are using I am sure you will find someone who has a solution.

There is a lot of help and advice here [http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")

---

### Post by CeolanM on 2012-08-15
> **cogier said:**
> Welcome to the forum.

If you tell us which computer you are using I am sure you will find someone who has a solution.

There is a lot of help and advice here [http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")
Its a Dell Inspiron 15r, 6gb, I searched the forum but some of the instructions either didn't work or i didn't understand them, i don't want to only run ubuntu on ethernet as i am doing now :/ 
Can anybody just help me along with this. Sorry bout this, I'm very new to coding, i only know a bit of java and python.

---

### Post by TheFu on 2012-08-15
> **CeolanM said:**
> Hey guys, I'm new to the forum.

I installed Ubuntu a while back, about a year ago, but I remember having internet issues with it. I was presuming it was because i was running it on a netbook with 1gb memory :)

1GB of memory is HUGE for ubuntu.  When you are less than 384MB, that's when I'd start worrying, but only for the GUI, not networking.

> **CeolanM said:**
> Anyway, i got a new proper laptop and I'm having EXACTLY THE SAME issue. I log onto ubuntu, and i try connect to my wireless internet and it doesn't show up. There is an option to add an internet connection, but it has me putting in alot of info about the network that i frankly dont know where to get, and if i do, i'd want to make sure it works if i do that,

First, can you plug in the laptop to an ethernet cable on the network? Does that work?
Wifi networking is tougher since most wifi chips in laptops are not vendor supported for Linux.  To find the easiest solution to the wifi setup for your laptop, google "{laptop model} {laptop maker} wifi ubuntu"

If that doesn't find the solution, then you need to know the exact wifi chips used inside the latop.  'lshw' will tell you that.  Open a terminal and type "lshw|more" into the prompt.  Look for the specific chip used and write that down. Now google again with the "{specific chip model} wifi ubuntu" for the answer.

Good luck.

If you want to get that netbook wifi working - follow the same google methods. There is nothing wrong with using ubuntu on a netbook. NOTHING, though you might prefer xubntu or lubuntu which need less graphics resources.

---

### Post by cortman on 2012-08-15
You should post the output of

```
lspci
```

---

### Post by TheFu on 2012-08-15
> **CeolanM said:**
> Dell Inspiron 15r, 6gb,

That tells us the family of PC, but not enough details to know what is inside.  I have a Dell Inspiron 15 too - it is a "1558".

I don't believe anyone has asked you to code anything here. Perhaps I missed something?

> There is an option to add an internet connection, but it has me putting  in alot of info about the network that i frankly dont know where to get,  and if i do, i'd want to make sure it works if i do that,

To make a wifi connection you will need to know:
* SSID for the network
* Pre-shared Key and if it is WPA, WPA2 or WEP.
If the network support DHCP, then that should be all you need to know, assuming your wifi drivers are working correctly.

If there isn't a DHCP server, then you'll need to know all those things plus these:
* IP address for **your** PC
* Netmask for the network
* Default gateway
* DNS Server(s)

Most networks run DHCP, however, so you should be in luck.

I hate to say this but "help my network doesn't work" really does not explain the problem so that anyone here can help. You can help us by explaining exactly what you press, type in and click on step-by-step.  Also, if we knew exactly which version of Ubuntu you are running and exactly which hardware you are using, that would be a big help for us to help you.

To run **lshw**, press the <atl>-F2 key, type "**xterm**", then inside that terminal, type "lshw -c network" - find the wifi network adapter in that list, copy and paste the output into a response inside this forum thread.  Something like this:```

       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0

``` Sorry, no wifi controller inside my machine.

---

### Post by wildmanne39 on 2012-08-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

