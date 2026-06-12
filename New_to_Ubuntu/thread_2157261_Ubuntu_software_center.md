---
title: "Ubuntu software center"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by maneatingbunny on 2013-06-24
I am very new to Ubuntu ( less than 24 hours ) 
My os was installed from a cd. 
I was able to download one application.
Now when I try to download this is the message I get. 
I am connected to the internet.
I have the correct password. 

Thank you for the assistance.

---

### Post by sanderj on 2013-06-24
Which Ubuntu version did you install? What does the CD say?

---

### Post by Halpm on 2013-06-24
When I got that message, it was because I had a defunct link in your software sources, but it's odd happening when you're trying to download, rather than update a program.

---

### Post by snowpine on 2013-06-24
Welcome to the forums (and to Ubuntu)!

We can assist you better if you open a Terminal (under Applications, Accessories I believe) and copy & paste the output of the following command:

```
sudo apt-get update
```

---

### Post by deri on 2013-06-24
and after that type sudo apt-get upgrade

---

### Post by maneatingbunny on 2013-06-24
this is the terminal 
I typed in the command.....however, I realized I don't know how to enter the code?
I am not sure if that is the right word.

---

### Post by maneatingbunny on 2013-06-24
How do I know what the password is?

---

### Post by snowpine on 2013-06-24
You specified your password when you installed Ubuntu.

If you forgot your password and need to reset, see here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by maneatingbunny on 2013-06-24
I figured out my password.This is the result.

---

### Post by snowpine on 2013-06-24
You have installed an obsolete Ubuntu release. All support for Maverick ended in April 2012. [http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)

You should do a fresh download and reinstall of a supported release (12.04 if you prefer long-term support; 13.04 if you want the latest and greatest but shorter support) following the easy 1-2-3 instructions at [ubuntu.com]("http://ubuntu.com/download/desktop").

---

### Post by MidnightGrey on 2013-06-24
edit: snowpine beat me to it.

---

### Post by maneatingbunny on 2013-06-24
Thank you. 
Side note....what are the beans?

---

### Post by oldos2er on 2013-06-24
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by maneatingbunny on 2013-06-24
Okay, went to ubuntu.com 
Downloaded 
saved file
now my file won't open?

---

### Post by MidnightGrey on 2013-06-24
The file you downloaded is a .iso format. It needs to be burnt to a CD, or if you do not have a CD burner you can create a bootable USB (Instructions are on [this website](https://help.ubuntu.com/community/Installation/FromUSBStick))

---

### Post by maneatingbunny on 2013-06-24
Found I have 10.10 Maverick Meerkat.
Do I have to upgrade to 11 or can I go straight to 12.4?

---

### Post by monkeybrain2012 on 2013-06-24
Forget about "upgrade", just download the 12.04 ISO, make a live usb with 10.10 startup disk creator (it will work) and then do a clean reinstall and wipe 10.10 off the hard drive. But before doing that remember to save your data.

---

### Post by snowpine on 2013-06-24
> **maneatingbunny said:**
> Okay, went to ubuntu.com 
Downloaded 
saved file
now my file won't open?

You must follow the instructions exactly.

for 12.04:  [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

For 13.04: [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

Follow Step 1, then Step 2, etc. and if you get stuck/lost, we're here to help. :)

---

### Post by maneatingbunny on 2013-06-24
I am trying to make a usb 
I don't seem to have a Startup Disk Creator.
I have looked in application-accessories as well as the other tabs. 
I have read through [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
tips?

---

### Post by maneatingbunny on 2013-06-24
Of course, just as I post this I found it......face palm
Thanks for the patient .

---

### Post by MidnightGrey on 2013-06-24
> **maneatingbunny said:**
> I am trying to make a usb 
I don't seem to have a Startup Disk Creator.
I have looked in application-accessories as well as the other tabs. 
I have read through [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
tips?

Unfortunately that link was designed for newer Ubuntu versions so the images and instructions do not match your system.
Have you looked in System > Administration menus?

edit: okay nevermind...

---

### Post by maneatingbunny on 2013-06-24
I finally made a USB stick ( super happy face ) 
However, my computer won't boot from the usb.
When I hit F12 nothing happens and my computer starts up like normal.

---

### Post by snowpine on 2013-06-24
Is F12 the correct key for boot menu? (it should say when you turn the computer on) Some machines it is F2, Esc, Del, etc.
What is your computer make and model number, maybe one of us can help you find this info?

If you can't get it working, tell us:
How did you make the USB stick?
Which version did you choose (12.04 or 13.04)?
Is this your only computer or do you have another computer you can test if the USB boots?

---

