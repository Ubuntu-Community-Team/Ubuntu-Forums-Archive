---
title: "EbookWise for Ubuntu not reading???"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by KaginMD on 2008-08-04
I bought a new Ebook Wise yesterday. When I tried to connect it to my computer it does not read the usb at all. Its like there is nothing plugged in. I have wine and tried to install the driver for the ebook using a windows based installation, but it didn't do anything either. When I click on the USB driver, it says starting program on the task bar, then it disappears (like all the programs I've tried in wine). Is there a command I can use to set this thing up?? Am I leaving something out?? And why don't wine work?? Lol, sorry everyone, but I love Ubuntu and refuse to go back to Windows just for an Ebook!:confused:

P.S. I'm running Hardy

---

### Post by collinp on 2008-08-04
Try running
```
lsusb
```and paste the output here.

---

### Post by ibuclaw on 2008-08-04
WINE does not use/provide a Windows Driver Layer for Linux to cooperate with. :)

You must use Linux to provide the hardware modules, if they exist.

```
lsusb
```
With the ebook plugged into your PC, what does the above output in the console?

Regards
Iain

---

### Post by KaginMD on 2008-08-04
kagin@kagin-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0993:0002 Gemstar eBook Group, Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
kagin@kagin-laptop:~$ 


Thats what the terminal give back.. What now? lol Thanks

---

### Post by collinp on 2008-08-04
Well, linux sees it at least. Is there any linux drivers for the EbookWise?

---

### Post by KaginMD on 2008-08-04
Nope, I wish there were.. But of course, its only Windows and Mac.. Is there a way to get around that? Like a dif. driver I can use instead.

---

### Post by collinp on 2008-08-04
Try running
```
sudo mount -a
```If your EbookWise is in your fstab, that command will mount it. The only reason why i recommend that command is by chance linux has added it to your fstab file, be aware that command mounts everything.

---

### Post by KaginMD on 2008-08-04
It asked me for my passoword, then it didn't do anything..

---

### Post by ibuclaw on 2008-08-04
Have a read here:
[http://www.ebookwise.com/servlet/mw?t=help_uploadcontent.htm&si=43#ETI](http://www.ebookwise.com/servlet/mw?t=help_uploadcontent.htm&si=43#ETI)

You may be able to do it through Firefox, just follow the instructions under the "**Uploading Content Through the ETI Personal Content Server**" section...

Regards
Iain

---

### Post by KaginMD on 2008-08-04
Lol, I think I'm cursed.. The info you gave me about the website was awesome, but I ordered it on Ebay, and the last person deleted the user name and everything, so I can't log onto the site.. AND I can't obtain a new one because the ebook is not coming up on my comp..Wow, Luck of the Irish right lolol

---

### Post by derrell on 2008-08-23
There is a usb driver that will let your eb-1150 connect through your pc.
See this thread
[http://ubuntuforums.org/showthread.php?t=35674]("http://ubuntuforums.org/showthread.php?t=35674")

There is a small fix to the code from source forge that had to be done before it would compile on Hardy for me.

See this Mobileread thread towards the bottom of the first page.
[http://www.mobileread.com/forums/showthread.php?t=27529]("http://www.mobileread.com/forums/showthread.php?t=27529")

I haven't used it much but it did allow me to connect to my online personal bookshelf.

As for registering your device it has an internal modem you can hook it to a phone line and register it that way instead of through the computers usb port.

---

