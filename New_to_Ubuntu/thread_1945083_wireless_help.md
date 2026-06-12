---
title: "wireless help"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by RLMedia on 2012-03-22
I have been trying for four hours now to get my wireless to work. Any help would be greatly appreciated. I am using latest stable ubuntu release. I have very little knowledge of ubuntu, I am *hoping* once I get net connection, I can look stuff up on the fly, without having to restart every 2 seconds :D  Last one I tried before deciding to make a desperate plea for help was this one: ```
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers
```  Right off the bat at step one: ```
~$ lspci -vvnn | grep 14e4 
``````
~$: command not found
```  Another useful bit of info, connecting wired is not an option, I don't have physical access to the router.   It works fine under windows 7, so I guess it has to be a firmware or driver problem.  Thanks in advance for any help.

---

### Post by viipu on 2012-03-22
> **RLMedia said:**
> Right off the bat at step one: ```
~$ lspci -vvnn | grep 14e4 
``````
~$: command not found
``` 

Terminal thinks ~$ is a command, but it's just an instruction saying "type the following in Terminal", so type in just
```

lspci -vvnn | grep 14e4 
```instead. Once you get the output, if you can't make sense of it post it here and smarter people than I will probs be able to help :)


//edit fixed a few confusing terms there.

---

### Post by RLMedia on 2012-03-22
Thanks....  Noob lesson #1 lmao

```
02:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
dragon@dragon-Inspiron-530s:~$ 
```

---

### Post by Bucky Ball on 2012-03-22
Welcome.

Tried plugging in an ethernet cable, getting updates, then checking 'Additional Drivers'??? That driver should install auto-magically. It is an old one for  Broadcom cards. 

DON'T load any drivers manually via instructions from web pages or anything else, or starting messing with ndiswrapper (it can get messy), until you try what I have suggested ... ;)

'Latest stable release' is not very specific; which release are you using?

PS: You don't need to put hyperlinks inside code tags. Just copy and paste 'em in. That way they will remain clickable links. ;)

---

### Post by RLMedia on 2012-03-22
11.10 32 bit. Is that specific enough, or is more info needed?
The modem was installed when I was at the beach, and the idiot rogers technician put it in the basement.... That's 3 floors down, I don't have a cable that long.

---

### Post by viipu on 2012-03-22
Hehee I only know because I made the same mistake I dare not admit how many times.

Getting anywhere with the Ubuntu Documentation? Sorry I can't give any specific help, wireless is one of the few things that worked out of the box for me so never bothered to look into it.

---

### Post by Bucky Ball on 2012-03-22
> **RLMedia said:**
> 
The modem was installed when I was at the beach, and the idiot rogers technician put it in the basement.... That's 3 floors down, I don't have a cable that long.

I suggest getting down there with one because it will make this a whole lot easier and shouldn't take very long. It is going to be rather impossible without a wired connection. You need to download some software. You need to install:

b43-fwcutter
firmware-b43-installer

... then restart the machine and check 'Additional Drivers' if it doesn't start working before that. ;)

There could be alternatives to this (I think the STA driver is on the LiveCD but doesn't always work and may not for this) so hopefully someone else might chime in with another angle.

---

### Post by RLMedia on 2012-03-22
No luck so far. just got done trying this one [http://linuxforums.org.uk/index.php?topic=5842.0](http://linuxforums.org.uk/index.php?topic=5842.0)  > dragon@dragon-Inspiron-530s:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
[sudo] password for dragon: 
sudo: b43-fwcutter: command not found 
dragon@dragon-Inspiron-530s:~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o 
sudo: b43-fwcutter: command not found 
dragon@dragon-Inspiron-530s:~$ sudo chmod 775 /lib/modules/b43 
chmod: cannot access `/lib/modules/b43': No such file or directory 
dragon@dragon-Inspiron-530s:~$ sudo chmod 775 /lib/modules/b43legacy 
chmod: cannot access `/lib/modules/b43legacy': No such file or directory 
dragon@dragon-Inspiron-530s:~$ 

---

### Post by tbhatia4 on 2012-03-22
As suggested Wired Network is the only way out

---

### Post by Bucky Ball on 2012-03-22
> **RLMedia said:**
> No luck so far.

No, you wouldn't have.

As I say, think the STA driver is on the disk but you really want b43-fwcutter. The update would probably tell you about your Broadcom card and ask if you wanted to install the appropriate firmware/software without you doing much if you could get a cable in. If it didn't you could then install the two drivers I suggested and that would be pretty much that.

---

### Post by leMasoud on 2012-03-22
sorry if i'm not making sense but i think i heard you saying it was working....even if it wasn't load your ubuntu live and see if it recognizes your wireless card...if it does then you have the driver and so the thing you need to do is to install it from the ubuntu CD.
log back into your installed ubuntu and insert the ubuntu CD into the drive and do as instructed in here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Packages_.28Without_Internet_access.29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Packages_.28Without_Internet_access.29)

---

### Post by wildmanne39 on 2012-03-22
Hi, if you can not plug it in you can put this firmware on an usb drive using a computer with internet access.

Download the b43 zip file to your flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Then it should be working unless you installed a conflicting driver.

---

### Post by RLMedia on 2012-03-22
> **leMasoud said:**
> sorry if i'm not making sense but i think i heard you saying it was working....even if it wasn't load your ubuntu live and see if it recognizes your wireless card...if it does then you have the driver and so the thing you need to do is to install it from the ubuntu CD.
log back into your installed ubuntu and insert the ubuntu CD into the drive and do as instructed in here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Packages_.28Without_Internet_access.29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing_Packages_.28Without_Internet_access.29)

 Tried that one, got to 3.4. Installing Windows driver  Graphical interface: windows wireless drivers asks for password, then just dissapears  terminal: > dragon@dragon-Inspiron-530s:~$ sudo ndiswrapper -i ~/drivers/bcmwl6.inf  [sudo] password for dragon:  installing bcmwl6 ...  sh: SUB.5.conf: not found  dragon@dragon-Inspiron-530s:~$ 

---

### Post by RLMedia on 2012-03-22
> **wildmanne39 said:**
> Hi, if you can not plug it in you can put this firmware on an usb drive using a computer with internet access.

Download the b43 zip file to your flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```Then it should be working unless you installed a conflicting driver.

  Ok gonna give it a go, thanks

---

### Post by wildmanne39 on 2012-03-22
Ok, it should work I have seen it fix many peoples issues exactly the same as yours.
Thanks

---

### Post by RLMedia on 2012-03-22
> **wildmanne39 said:**
> Ok, it should work I have seen it fix many peoples issues exactly the same as yours.
Thanks

Ok, did that, rebooted. Before it showed up as firmware disabled, I think that is what it said. Now the wireless option isn't on the list anymore at all. I am sure I screwed something up lol.  I hate being a newbie

---

### Post by wildmanne39 on 2012-03-22
Hi, did you just copy and pasted all commands?

Did you put the zip file on your desktop and extract it there?

Where there any errors when you ran the commands?
Thanks

---

### Post by RLMedia on 2012-03-22
Well, I just copy pasted all the commands again. Got errors for every one but the last this time. No errors before. But for some reason it worked! Typing from ubuntu now, you kick *** dude! Thanks a lot for the help!

---

### Post by wildmanne39 on 2012-03-22
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by RLMedia on 2012-03-22
Sure thing. Any way to give you some points or something for the solution? :D

---

### Post by wildmanne39 on 2012-03-22
Hi, no we do it just because we like to help and we know what it is like to be new.
Thanks

---

### Post by RLMedia on 2012-03-22
:guitar:

Much appreciated. I try to pass on knowledge when I can too ):P

---

### Post by Bucky Ball on 2012-03-22
> **RLMedia said:**
> :guitar:

Much appreciated. I try to pass on knowledge when I can too ):P

Well, you're in the right place! Glad it's sorted. Told you b43 would fix things in a jiff. Just a matter of getting drivers/firmware into your machine. 

Incidentally, ndiswrapper obsolete for that card which is why I said don't manually install it a few posts ago. If you managed to install that and a not working driver the b43 route could have been a world of pain as the two would conflict and you'd need to go through the rigmarole of disabling ndiswrapper and blacklisting the driver ... blah, blah. ;)

Nice work (yet again) Wildmanne. ;)

---

