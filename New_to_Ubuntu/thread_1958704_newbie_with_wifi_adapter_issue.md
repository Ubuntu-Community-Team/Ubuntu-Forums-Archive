---
title: "newbie with wifi adapter issue"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-04-14
Hullo you lot! I've just got my Ubuntu box up and running and know  nothing about how to make it work. So, having said that, I'm trying to  load through  the  CD drive the install and drivers for a USB wireless  adapter. When I click on the autorun to install the software, it opens a  reader and does not install. All that I can find in the help files  tells me to go online to install software, but how can i go online when I  cannot install the bloody adapter?
Below is the message that I get when clicking on the autorun.exe file.
Any help will be appreciated.):P

[I]Archive: /media/cdrom0/autorun.exe
Zipfile size: 1490432 bytes, number of entries: 5202

warning  [/media/cdrom0/autorun.exe] end-of-central-directory claims this is  disk 17291 but that central directory starts on disk 35632; this is a  contradiction. Attempting to process anyway

error[/media/cdrom0/autorun.exe]: missing 3908585799 bytes in zipfile ( Attempting to process anyway)

error  [/media/cdrom0/autorun.exe]: attempt to seek before beginning of  zipfile (please check that you have transferred or created the zipfile  in the appropriate binary mode and that you have compiled Unzip  properly)[/I]

---

### Post by theknightlinux on 2012-04-14
Do you know the model of the usb adapter?

---

### Post by TFSinclair on 2012-04-14
> **theknightlinux said:**
> Do you know the model of the usb adapter?

Yes, sorry to not have mentioned that in my previous post.\
it is a CE SL-1504N adapter

---

### Post by Bucky Ball on 2012-04-14
Have you plugged in an ethernet cable (with the dongle plugged in) and gotten updates then checked 'Additional Drivers'?

---

### Post by theknightlinux on 2012-04-14
So if you got a CD, I assume the drivers should be in there. Can you find some folder where the driver should be found for Linux, or some folder in a compressed or regular format that says something like rltk8191? You cannot install the drivers for a Linux system as you install them with a .exe application like you do in Windows. That's why you get those errors.

---

### Post by theknightlinux on 2012-04-14
[FONT=Verdana]OK, I'll assume you got the drivers from the CD. If not go to: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

Download the most recent. Try to get it somehow to a CD, USB Flash or something and extract all files in a folder in your /home folder. Name it to something like RTL8191. Open up a terminal, press ctrl-alt-t simultaneously and type: sudo su
now after that type: cd      do not press enter yet, grab your folder RTL8191 and drop it to the terminal and press enter.
Now type: make
Let the terminal do its thing and then type: make install
Again, let the terminal do its thing.
Now type: modprobe rtl8192se
This last command is to load the driver to the system. But you're not done yet. Because you don't want to do this every time you restart your computer we need to make the system load the driver every time you start your computer. To do in the terminal type:
[/FONT][COLOR=#333333][FONT=monospace][FONT=Verdana]gksudo gedit /etc/modules
A text file should be open, at the end of this file type: rtl8192se
Save the file and close it. Restart your computer and your USB Wireless Adapter should be working.
This is basically the same process for every card when you got the drivers in hand, and sometimes you have to download the latest driver. Hope it loads your Adapter, if that doesn't work please let me know.
[/FONT][/FONT][/COLOR]

---

### Post by TFSinclair on 2012-04-15
> **theknightlinux said:**
> [FONT=Verdana]OK, I'll assume you got the drivers from the CD. If not go to: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE)

Download the most recent. Try to get it somehow to a CD, USB Flash or something and extract all files in a folder in your /home folder. Name it to something like RTL8191. Open up a terminal, press ctrl-alt-t simultaneously and type: sudo su
now after that type: cd      do not press enter yet, grab your folder RTL8191 and drop it to the terminal and press enter.
Now type: make
Let the terminal do its thing and then type: make install
Again, let the terminal do its thing.
Now type: modprobe rtl8192se
This last command is to load the driver to the system. But you're not done yet. Because you don't want to do this every time you restart your computer we need to make the system load the driver every time you start your computer. To do in the terminal type:
[/FONT][COLOR=#333333][FONT=monospace][FONT=Verdana]gksudo gedit /etc/modules
A text file should be open, at the end of this file type: rtl8192se
Save the file and close it. Restart your computer and your USB Wireless Adapter should be working.
This is basically the same process for every card when you got the drivers in hand, and sometimes you have to download the latest driver. Hope it loads your Adapter, if that doesn't work please let me know.
[/FONT][/FONT][/COLOR]
hullo, and thanks for your assistance in trying to get my WIFI working. Here is what happened when I did as you said. Seems I may have mucked it up.

[I]human@human:~$ sudo su
cd'/home/human/Desktop/92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz
[sudo] password for human:
Sorry, try again
[sudo] password for human:
Sorry, try again
[sudo] password for human
Unknown ID: CD/home/human/Desktop/92ce_se_de_linux_mak80211_0005.1230.2011.tar gz
human@human-Desktop~sudo su cd
file:///media/Cruzer/ 92ce_se_de_linux_mac80211_0005.1230.2011.tar gz
Unknown ID: CD
human@human-Desktop"~$ make make install
make*** No rule to make target "make". Stop
human@human-Desktop:~$
[/I]

---

### Post by Bucky Ball on 2012-04-15
These two are separate commands, one at a time:

```
human@human-Desktop"~$ make make install
```... should be:```
make
make install
```

---

### Post by TFSinclair on 2012-04-19
The issue is now solved! this does not mean that I will not have other issues  as I go about learning Ubuntu.
The issue was a bad wi-fi adapter.
This computer is now direct wired on my Ethernet system

Thank you all for your replies and assistance in this matter.
Slainte!
TFSinclair

---

### Post by wildmanne39 on 2012-04-19
Hi, how do you know that> The issue was a bad wi-fi adapter.you were not given a command to list your device so we would know what driver you needed or if it was installed already.

Most of the time the driver on an install cd is to old to compile on a newer kernel and you would have to have linux kernel headers and build essentials installed first anyway.

With your adapter plugged in please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mwkeeler on 2012-04-19
> **wildmanne39 said:**
> Hi, how do you know thatyou were not given a command to list your device so we would know what driver you needed or if it was installed already.

Most of the time the driver on an install cd is to old to compile on a newer kernel and you would have to have linux kernel headers and build essentials installed first anyway.

With your adapter plugged in please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

I just purchased a new Patriot Wireless N USB adapter.  I cannot get it to work either.  I was not sure how to install the drivers with the CD.  Are this the method to get the drivers to download?  I have an ethernet Internet connection.  I would rather have the latests drivers.  Is there a way to get the correct drivers through an automatic update?

Thanks for this help.  This forum rocks!

---

### Post by wildmanne39 on 2012-04-20
Hi, please post the information from the commands in my last post so we can see what chip you have in you adapter and other important information.
Thanks

---

### Post by Bucky Ball on 2012-04-20
> **mwkeeler said:**
> I just purchased a new Patriot Wireless N USB adapter.  I cannot get it to work either.  I was not sure how to install the drivers with the CD.  Are this the method to get the drivers to download?  I have an ethernet Internet connection.  I would rather have the latests drivers.  Is there a way to get the correct drivers through an automatic update?

Thanks for this help.  This forum rocks!

Please post your own thread with a title describing your issue rather than jumping onto to this one. You will get more and more specific help. It just makes it confusing for everyone attempting to solve two problems on the same thread and limits your chances of help, too. ;)

---

