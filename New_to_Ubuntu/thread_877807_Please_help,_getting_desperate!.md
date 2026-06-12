---
title: "Please help, getting desperate!"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by jozmoz on 2008-08-02
I have bought an Atheros Wireless card for my laptop, but i can't get it working. I tried just plugging it in, as I thought the madwifi driver was already on xubuntu, but nothing happens. On the CD that came with the wireless card is a folder called madwifi v9, but I can see how you install this driver.How do I get this driver on my laptop? Please help Thanks:(

---

### Post by kpkeerthi on 2008-08-02
[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)

---

### Post by jozmoz on 2008-08-02
Sorry but i have already looked at this page, and i don't understand it, i'm an absolute beginner. How do I load the driver from the cd that came with my wireless card?

---

### Post by jozmoz on 2008-08-02
Also I haven't got a working internet connection for this laptop so I need to load the driver from the CD that came with my wireless card. If anyone knows how I can install this driver from th cd please help.Thank you:(

---

### Post by kpkeerthi on 2008-08-02
The CD probably has drivers for Windows. To install linux drivers, open a terminal (Application -> Accessories -> Terminal) and type this command:

```
sudo apt-get install linux-restricted-modules madwifi-tools 
```

Once the installation process completes, type this command
```
sudo modprobe ath_pci
```

Your device should be functioning now.

---

### Post by jozmoz on 2008-08-02
Thanks for your help. Do I insert the CD first then type this command?

---

### Post by jozmoz on 2008-08-02
Please could someone show me a step by step how to install the madwifi driver that came with my wireless card. I have no internet connection for this laptop. I can see the madwifi folder on the disk but I have abslolutely no idea how to install it. Please someone help me. thanks

---

### Post by gerben1 on 2008-08-02
that first command:
```
sudo apt-get install linux-restricted-modules madwifi-tools
```
will try to download and install two packages, namely these:
- linux-restricted-modules
- madwifi-tools

but since you do not have an internet connection on that computer, the command will fail unless you tell ubuntu to also search on the ubuntu cd for packages when you install something via apt-get.

To do this go to:
System->Administration->Software sources
in the tab:
"Third-part software"
check the line that says:
"cdrom:[Ubuntu etc..."

So now that apt-get command can find the packages on the Ubuntu install Cd and install those. So insert your Ubuntu install cd and then issue the two commands in a Terminal.

---

### Post by jozmoz on 2008-08-02
Thank you very much I will try this.:)

---

### Post by gerben1 on 2008-08-02
Just to clear this up. You cannot install the driver that came with your card as it is a Windows driver, you would install that in Windows, but it won't work in Linux. You need a Linux driver. Card manufacturers usually don't support Linux and offer only Windows drivers with their hardware, so you will have to download the Linux drivers or get them from the Ubuntu cd.

---

### Post by SunnyRabbiera on 2008-08-02
or use ndiswrapper, that may or may not help out.
Somewireless cards wont play nice, not our fault mind you.

---

### Post by jozmoz on 2008-08-02
There are 3 drivers on the cd that came with my wireless card, Windows XP, Vista, and madwifi v9

---

### Post by jozmoz on 2008-08-02
I've tried going into system source and checking 'Ububtu CD Rom..'
I then run the command again, but it still isn't finding the cd?

All I want to do is load the madwifi driver that is on a cd. How do I do this. Surely it can't be that complicated? Please could someone help me, i'm pulling my hair out here!

I have no internet connection for that laptop, so I must load the driver from the cd or even the xubuntu install cd.

---

### Post by philinux on 2008-08-02
> **jozmoz said:**
> I've tried going into system source and checking 'Ububtu CD Rom..'
I then run the command again, but it still isn't finding the cd?

All I want to do is load the madwifi driver that is on a cd. How do I do this. Surely it can't be that complicated? Please could someone help me, i'm pulling my hair out here!

I have no internet connection for that laptop, so I must load the driver from the cd or even the xubuntu install cd.

Can you connect the laptop to the router wired. Then use those commands listed above to install the linux driver.

Accesories Terminal then copy and paste

sudo apt-get install linux-restricted-modules madwifi-tools

---

### Post by jozmoz on 2008-08-02
no I cannot connect to the router wired. All I have is the cd-rom with the madwifi driver on it. Surely this has got to be a simple thing to do.  I have the driver on a cd, all I want to do is intall this driver from the cd. Please someone how do i do it?

---

### Post by mdsmedia on 2008-08-02
You need to understand that you are using Linux, not Windows. The drivers on the CD are for Windows. The drivers for Linux are probably available on the internet, but not on your CD. Therefore it is not as simple as you might like it to be.

---

### Post by barkalot on 2008-08-02
After you have enabled the option to use the CD, insert the CD which you used to install Ubuntu. Then type the commands from the previous page.

---

### Post by nuddernuby on 2008-08-02
Just happened to see your post 30 minutes after installing an Atheros card without any hassles.  Are you using Ubuntu Hardy Heron 8.04?  If so, have you tried installing the wireless via network setup? That worked for me. 

Go System>Administration>Network
Then Unlock first with your password.
Then configure your card - it should be at the top of the list.
Once done it should read your card automatically.
Try this and let us know.

---

### Post by jozmoz on 2008-08-02
hi there thanks for your help. 

I am running xubuntu. I went into networks and after entering my password is a screen showing under the header connections that wireless connection: roaming mode enabled. am i looking in the right place?

---

### Post by nuddernuby on 2008-08-02
Exactly right. Now disable roaming - uncheck the tick box. This will bring the other boxes 'to life'. You can enter the details of your wireless network as well as the password key.
In the section below that I suggest that you select DHCP and then close. It should configure your wireless link, after which it should be operational.

After this you only need to configure your actual access to your ISP. If you use ADSL or similar, you will open a terminal and type in 
```
sudo pppoeconf

```
This will bring up a little program that will guide you to enter all the details with which you need to connect to your internet service provider. If uncertain at any stage of the setup, it's probably OK just to press Enter.
Good luck

---

