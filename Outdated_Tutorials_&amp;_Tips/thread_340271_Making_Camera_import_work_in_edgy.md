---
title: "Making Camera import work in edgy"
date: 2007-01-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Polygon on 2007-01-17
When i installed edgy, whenever i plugged my digital camera in to import photos, i always got this message when i tried to import them

> An error occurred in the io-library (&#8217;Could not claim the USB device&#8217;): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

This remain unfixed for me for a long time, until i came across this blog post:

[http://commandline.org.uk/2007/my-day-with-ubuntu-edgy-eft/#comment-18946](http://commandline.org.uk/2007/my-day-with-ubuntu-edgy-eft/#comment-18946)

He provides a fix for this, which i will restate here

**_step 1_**: plug in your camera

**_step 2:_** try to import the photos, and when it gives you the error, just exit out

**_step 3:_** open up the terminal, and type ```
lsusb
```

**_step 4:_** find the entry that looks like it belongs to your camera. It usually has the vendor name somewhere in there. For example, my camera is a kodak easy share c315, and when i typed "lsusb" i got this:

> mark@ubuntu:~$ lsusb
Bus 003 Device 004: ID 05ac:1205 Apple Computer, Inc. 
Bus 003 Device 003: ID 0d49:3210 Maxtor 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 040a:059a Kodak Co. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
mark@ubuntu:~$ 


My camera is listed on the 4th line down, with "kodak co." after.

**_Step 5:_** type 
```
sudo cp /etc/udev/rules.d/45-libgphoto2.rules /etc/udev/rules.d/45-libgphoto2.rules_backup
```

If you use **_ubuntu_** or **_xubuntu_**:
```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```
Then go to step 6

If you use **_Kubuntu_**:

```
sudo kate /etc/udev/rules.d/45-libgphoto2.rules
```


**_Step 6:_** Go to the bottom of the file, where it says 

> LABEL="libgphoto2_rules_end"

Above that, hit enter a few times and then, using the numbers preceding the vendor name that you got from the lsusb command, paste and fill out the following line into the file

where VENDORID is the first half of numbers in the "key" and PRODUCTID is the second half of numbers. Example, my camera's line was "Bus 001 Device 004: ID 040a:059a Kodak Co.". VENDORID is "040a" and my PRODUCTID is 059a. 

```
SYSFS{idVendor}=="VENDORID", SYSFS{idProduct}=="PRODUCTID", MODE="0660", GROUP="plugdev"
```

**_Step 7:_** save the file, and make sure it works. Try taking a few pictures with your camera and try importing them, and if it works, then it will let you import them rather then give you that error message. If it doesn't work, make sure you got everything right, and if it still doesnt work, just delete the line and look for a different solution

hoped this helped someone!

---

### Post by WBAC88 on 2007-01-20
I tried to follow this, but it stopped working at about the second half of step 5. I backed up the rules, but when I typed in the gedit part, it told me that "sudo: gedit: command not found" and I don't know what is wrong. I really know very little about this, so very basic help would be greatly appreciated, since this is exactly the problem I have. All of the other fixes for this assume that you know how to add rules into a file, so thanks for this detailed approach. Thanks,

Andy

---

### Post by bbarrons on 2007-01-22
which ubuntu are you using? ubuntu or kubuntu? if you are using ubuntu then gedit should work. if you are using kubuntu then use kate in place of gedit. kate is your editor in kubuntu.....

---

### Post by RhysU on 2007-01-22
Interesting problem with a Canon PowerShot A510 that seems kind of related.  I've got a Dapper -> Eft upgraded system with two users: me and my fiance.  When I plug our Canon PowerShot A510 into the USB port when I am logged in, I see the usual import photos popup from gnome-volume-manager-gthumb.  When I plug the camera in while logged in as my fiance, nothing happens.  As my fiance's user, I can manually run gnome-volume-manager-gthumb and import photos just fine.

I cannot isolate what the difference is-- both users are members of group plugdev.  dmesg shows no noticeable differences.  dbus-monitor shows the same messages.

Any suggestions for where to start looking greatly appreciated.  It's driving me batty.

---

### Post by shakma on 2007-01-25
Fantastic, Polygon!  You've saved the day here at my job... which is at a school.  Now we can print out the graduation photos!

Peace.

---

### Post by mmuzzy on 2007-02-05
This worked like a charm for me too. My Kodak z710 just sprang to life in Ubuntu. 

Thanks!
-Mike

---

### Post by Polygon on 2007-02-06
> **RhysU said:**
> Interesting problem with a Canon PowerShot A510 that seems kind of related.  I've got a Dapper -> Eft upgraded system with two users: me and my fiance.  When I plug our Canon PowerShot A510 into the USB port when I am logged in, I see the usual import photos popup from gnome-volume-manager-gthumb.  When I plug the camera in while logged in as my fiance, nothing happens.  As my fiance's user, I can manually run gnome-volume-manager-gthumb and import photos just fine.

I cannot isolate what the difference is-- both users are members of group plugdev.  dmesg shows no noticeable differences.  dbus-monitor shows the same messages.

Any suggestions for where to start looking greatly appreciated.  It's driving me batty.

it sounds like some configuration file in your fiance's home folder got borked somewhere and its not bringing up the "import photos" popup. Unless you can figure out which config file it is and fix it, i guess the only way to fix it is to get all your data off of that account, delete the account and recreate a new one

and ill edit it to put "kate" (if your using kubuntu)

and im glad that this guide has helped some people, and even with something as important as printing graduation photos :D

But the real credit goes to the guy who wrote the blog, i just posted it here in the how to section :D

And other questions, you might just want to PM me as i dont check this topic every day.

---

### Post by ginapi on 2007-02-12
Thank you!

this make my **Canon PowerShot Pro1** working again.

The line you need to add to [FONT="Courier New"]/etc/udev/rules.d/45-libgphoto2.rules[/FONT] for this camera is :```


SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="309d", MODE="0660", GROUP="plugdev"
```

ginapi

---

### Post by lonewolf72 on 2007-03-03
Just wanted to say thanks.  Using your examples I was able to get my new Kodak C533 working under Ubuntu Edgy.... :)

---

### Post by Wega on 2007-03-11
Thank you, it vorks. The line for Canon A530 is 
```

SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3126", MODE="0660", GROUP="plugdev"
```

---

### Post by Queas on 2007-03-13
I'm using a PowerShotA530 and I'm still getting this same error using the fix above.  Any other thoughts on a fix for this?

---

### Post by roi on 2007-03-15
it will work only after you add # or delete the second line that says :
BUS!="usb*", GOTO="libgphoto2_rules_end"
otherwise i guess it doesn't read the added rule.

---

### Post by funkysod on 2007-03-27
> **WBAC88 said:**
> I tried to follow this, but it stopped working at about the second half of step 5. I backed up the rules, but when I typed in the gedit part, it told me that "sudo: gedit: command not found" and I don't know what is wrong. I really know very little about this, so very basic help would be greatly appreciated, since this is exactly the problem I have. All of the other fixes for this assume that you know how to add rules into a file, so thanks for this detailed approach. Thanks,

Andy
reinstall "text editor"--> search for gedit in "add/remove", add and roberts your fathers brother!
lost gedit too when i was mocking about with something..

---

### Post by pt123 on 2007-04-09
> **roi said:**
> it will work only after you add # or delete the second line that says :
BUS!="usb*", GOTO="libgphoto2_rules_end"
otherwise i guess it doesn't read the added rule.

Thank you that is so crucial, hopefully the creator of this thread will update the first post.

 \\:D/

---

### Post by sh4d3z on 2007-04-09
> **roi said:**
> it will work only after you add # or delete the second line that says :
BUS!="usb*", GOTO="libgphoto2_rules_end"
otherwise i guess it doesn't read the added rule.

thank you! and to the the thread starter
i was litterally an inch away from falling back to dapper or switching distro entirely(this is the first thing i have gotten to work on edgy lmao still haven't gotten mplayer to work correctly)
i'm using an ancient powershot a60 btw lol
again thanx

---

### Post by Somenoob on 2007-04-11
> **roi said:**
> it will work only after you add # or delete the second line that says :
BUS!="usb*", GOTO="libgphoto2_rules_end"
otherwise i guess it doesn't read the added rule.

Thank you. The solution in the original post didn't work for my Canon IXUS 60 but this did.

---

### Post by dogeatery on 2007-04-12
This still isn't working for me... I have read seemingly every post on this topic and nothing seems to work!  my Kodak DX3900 is even recognized when I run usbdisk and lusb but it never gets assigned a mountpoint (sda, sda1, etc.)  When I first ran Breezy it worked seamlessly one time and then never worked again.  Any other ideas???

---

### Post by Polygon on 2007-04-15
i researched this bug after i found out about it and its marked as fixed, so wait 4 days for feisty to come out and if you switch to that it should be fixed.

---

### Post by jmkaza on 2007-04-15
Worked Perfectly, Thanks.:KS

---

### Post by shakma on 2007-05-14
> **roi said:**
> it will work only after you add # or delete the second line that says :
BUS!="usb*", GOTO="libgphoto2_rules_end"
otherwise i guess it doesn't read the added rule.

This original post worked for me back in January (as I gleefully posted), but then it didn't.  Now, with this additional tweak, I'm back in business.  This extra little tidbit should be bumped up with the original post to solve many headaches like my own.  

Thanks to all.

Peace.

---

### Post by robinPain on 2008-05-23
After installing 8.04 (Hardy) my Fuji FinPix was no longer recognised giving the above error.

But in this case the 

45-libgphoto2.rules

file was missing from

/etc/udev/rules.d

Then I found this link

[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/90724](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/90724)

and copied and pasted this from it

sudo sh -c '/usr/lib/libgphoto2/print-camera-list udev-rules mode 0660 group plugdev > /etc/udev/rules.d/45-libgphoto2.rules'

which created the missing 45-libgphoto2.rules file and that was all I needed to do - the camera then worked immediately.


Rob

---

### Post by shreepads on 2008-08-26
Polygon and Rob.. Thanks a ton! Got my old Canon Powershot A60 working instantly...

Didn't have to mess around with the rules files, (as none existed having just installed Hardy!!) just created a new one as per Rob's post and all working fine!!!

Hopefully this will get my dad to start using Ubuntu....

=D>

PS: How does one thank posters? Can't find the link here....

---

### Post by halitech on 2009-07-19
just a note to say that this even worked in Debian Lenny for a Kodak Easyshare C813

---

### Post by ericinwisconsin on 2009-10-17
None of the stuff listed in this message thread works for my Ubuntu 9.04 and my Kodak CX7430. No joy here. :(

---

### Post by saporito on 2010-03-14
I have a kodak easy share camera and I added the line ```
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05c1", MODE="0660", GROUP="plugdev"
``` my camera still doesn't work and I am not sure what to do. The file you said to edit was empty and didn't have that bottom line so I added it.

---

### Post by monaleilani on 2010-06-29
I am echoing saporito and ericinwisconsin here. I have Karmic Koala and my Kodak CX7330 will not work with the advice specified here. Also, I am not sure, but the file that needs to be edited in Karmic is 40-libgphoto2-2.rules? There is no 45-libgphoto2.rules in Karmic, it seems. I ended up copying this other file to /etc/udev/rules.d from /lib/udev/rules.d. **Would really, really appreciate the help here!** I am being forced to use my Mom's Windows computer... :(

---

