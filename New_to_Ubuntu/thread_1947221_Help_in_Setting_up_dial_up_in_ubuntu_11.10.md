---
title: "Help in Setting up dial up in ubuntu 11.10"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by Black Phoenix on 2012-03-26
I switched over to ubuntu a couple of days ago.(Ubuntu 11.10 with the new Unity interface or something).I had installed it from a live CD. This is the first time I'm using any linux distro. 
I only use dial-up. However with Ubuntu I don't see any option to make a connection with a dial-up modem. The 'edit connections' from the network menu only gives options for wireless, vpn, wired and dsl. Furthermore when I try to use the alternate method 1 from here
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f80f2865d7f29664a8506ef25b0e40eaf4420c10](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f80f2865d7f29664a8506ef25b0e40eaf4420c10) 
It says that there is no command wvdial. Do I have to download wvdial or anything else?
(am posting this from someone else's pc)
Thank you.

---

### Post by audiomick on 2012-03-26
If you get the message in a terminal that there is "no command such-and-such", it generally means that the program in question is not installed.

I don't know if wvdial is supposed to be installed by default. Have a look for it in the software centre. That should tell you if it is installed and let you install it if it is not.

Open the software centre and type "wvdial" in the search box. It should show up straight away.

---

### Post by roger_1960 on 2012-03-26
Hi

I'll try to help.

Open the Ubuntu software center.  Select edit>software sources and tick te box at the bottom allowing you to use the Ubuntu CD you have.  Then search for gnome-ppp and install it from the cd.

You have to run the following two commands (one at a time) in a terminal window to give you permissions to use a dialup connection.  Open a terminal window by doing CTR+ALT+T and copy and paste the commands (edit your username)

> $ sudo adduser $USER dip
 $ sudo adduser $USER dialout

where $USER is you username.  You will have to enter your password after each return (it does not appear, but keep typing and press return)

When you have done this, you should be ready to go.  Run gnome-ppp by searching for it in the dash and selecting it. Then run setup and press "detect".  This should find your modem and leave you ready to enter your phone number, username, password.

The pitfall, possibly non fixable (at least not easily) is if you have a "winmodem" rather than a real modem on a board or externally.  Linux is not good with many winmodems.  (I gave up and bought an external "proper" modem to overcome that problem.)

Hope this helps

---

### Post by Black Phoenix on 2012-03-27
Thanks for the replies, :)
@audiomick,
It isn't installed and the software centre can't find it either.
@roger_1960,
I ticked the ubuntu CD option in software sources and searched for 
gnome-ppp in the software centre through the search option in top-
right corner.The when I click it, it shows the source as universe and 
the button is greyed out (is it because I don't have access to the 
internet?). And I can't find gnome ppp on the cd manually either.Can I 
download it as a package on another PC and then install?

---

### Post by Black Phoenix on 2012-03-27
Alright. I got gnome ppp, its dependancy wvdial and all its dependancies from the CD or downloaded them. Then installed them trough the terminal with dpkg. Now just as you had said, modem driver is posing a problem. All I can get from the scanModem's Modem Data file is that it is a 'conexant soft56K Data/Fax modem and its subsystem id (whatever it is) is 14f1:205d. 
Can I get a driver for it online? I have its driver cd which has a linux driver from linuxant.com (test version limited to 14.4 kbps), but it is in .rpm format. Can I instal it on ubuntu?
 
Plus is there any easy, gui way of installing .deb packages?
Thanks in advance.

---

### Post by audiomick on 2012-03-27
> **Black Phoenix said:**
> Thanks for the replies, :)
@audiomick,
It isn't installed and the software centre can't find it either.

Sorry, I wasn't thinking. It can't find it because you don't have an internet connection.](*,)

I haven't installed .rpm files on Ubuntu, but there is this in the documentation

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

There is a reference in there to gdebi for installing .deb files via a gui, but that is not installed by default, I believe. However, I think if you click on a .deb file, the software centre should open and install it for you. Otherwise, there is also a command on the page that the link leads to for installing .deb files from the terminal.

---

### Post by Black Phoenix on 2012-03-27
Thank you, audiomick.
 
The drivers at linuxant.com are for kernel 2.6..... Mine has 3.0..... Does anyone know if I can find a driver for my modem (Conexant softk56 Data/Fax, PCI ID, 14f1:205d)? 
 
If not is there any list of modems which are compatible with linux and their drivers are easily found and free? Or at least given along with it? I'd appreciate it if it is a long list. I live in Pakistan and the chances of getting a modem by choice are really slim. The more names I know, the better the chance I'll find one.
 
Thank you.

---

### Post by roger_1960 on 2012-03-27
Hi again

In your last post, is that the PCI ID or subsytem ID?  They are not normally the same and scanmodem gives both.

Suggest you go to linuxant.com and search for the driver (HSF?) with the right PCI ID

Don't have a list, but I use a USR 5637  [http://www.usr.com/support/product-template.asp?prod=5637](http://www.usr.com/support/product-template.asp?prod=5637) which works well using gnome-ppp

---

### Post by Black Phoenix on 2012-03-27
You were right, roger_1960, I was calling the subsystem ID the PCI ID. :) With that correction I've found the correct driver on linuxant. I hope th difference in kernel versions wouldn't make a problem. If it does, I'll go for a new more compatible modem (hopefully the model you showed mentioned).
 
So thanks a MILLION for your answers. It helped a lot. :)

---

### Post by roger_1960 on 2012-03-27
Hi

Glad it helped - hopefully you can get your existing modem going.

Have a look at [https://help.ubuntu.com/community/DialupModemHowto/Modems](https://help.ubuntu.com/community/DialupModemHowto/Modems) for more info and a few links to lists if you have to buy one.

Once you are sorted, you could mark this thread as solved using the thread tools at the top.

Good luck!

---

