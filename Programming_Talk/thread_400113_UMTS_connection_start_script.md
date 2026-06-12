---
title: "UMTS connection start script"
date: 2007-04-03
forum: Programming Talk
---

### Post by geraner on 2007-04-03
Hi,

I finally got my UMTS Card running on my Ubuntu Laptop.
Card: Option GT (Ready 7.2)

To get it running, I downloaded the icon_switch tool and installed it.
Instructions can be found on [this page]("http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewforum/f,12/sid,17ecb92fee91135422f0460a6734b1df/").

To get it running, I'm always opening a terminal window.
Then I'm entering:
> 
me@ubuntu-laptop:~$ sudo /usr/bin/icon_switch
Password:**writing my password here**

Followed by:
> 
me@ubuntu-laptop:~$ sudo modprobe serial_cs
me@ubuntu-laptop:~$ sudo modprobe usbserial vendor=0x0af0 product=0x6701
me@ubuntu-laptop:~$ sudo wvdial

And then my UMTS card is connecting to the Internet.

Is it somehow possible, to create an entry in the Menu under "Applications -> Internet" so that I just have to click on then. Then it is automatically opening the terminal and writing all my commands and connecting to the internet?

I thought this would be possible with a script or something like that. I don't know.
I would be glad if someone could help me with it.

Thanks in advance.

Regards
Geraner

---

### Post by MikeDX on 2007-04-24
Sadly this doesnt even work in edgy so I cannot help..

---

### Post by geraner on 2007-04-26
Yes it was possible. I got help from the local Linux UserGroup.

I created a text file on my desktop with the following data.
> 
sudo icon_switch
sleep 4
sudo modprobe serial_cs
sudo modprobe usbserial vendor=0x0af0 product=0x6701
sudo wvdial

I right clicked on the file and selected "Properties" -> "Permissions" -> "Execute: Allow executing file as program".

Then I startet the a terminal and wrote **sudo gedit /etc/sudoers**.
In this file I added at the end the following data:
> 
me ALL=(ALL) NOPASSWD: /usr/bin/icon_switch
me ALL=(ALL) NOPASSWD: /sbin/modprobe serial_cs
me ALL=(ALL) NOPASSWD: /sbin/modprobe usbserial vendor=0x0af0 product=0x6701
me ALL=(ALL) NOPASSWD: /usr/bin/wvdial

Where I have written "me" there you shoud write your username with which you are logged in when you want to run the start-script.
With this data entered in the sudoers file, my Ubuntu is not longer asking for a sudo-password when I'm entering those comands when I'm logged in.

To start the script, I just dubble click on the created file on my desktop, and then I select **Run in Terminal**. That's everything. Then the script is doing the rest and creates a connection with my UMTS card. :)

Regards
Geraner

---

