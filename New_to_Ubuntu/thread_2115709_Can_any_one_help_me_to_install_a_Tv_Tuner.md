---
title: "Can any one help me to install a Tv Tuner"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by willbrimmer on 2013-02-13
Hello,

I am trying to install a TV tuner card on to Ubuntu 12.10 but am having lots of problems.  i have looked through lots of the previous posts on here and across the web but still don’t seem to have managed to solve me problem yet so was really hoping someone might be able to help.

I have brought a usb tv card which when i run lsusb tells me it is : Integrated Technology Express, Inc. Zolid Mini DVB-T Stick


so i have followed this thread: [http://ubuntuforums.org/showthread.php?t=1898046](http://ubuntuforums.org/showthread.php?t=1898046)  particularly post 5.  However i am unsure at the end of the post where it mentions :and the device /dev/dvb/ should exist.

After i did post 5 i rebooted and used ME TV which would download a channel list but then only plays BBC1 (Channel 1) which ever channel you select.  If i try to use Kaffine or MythTV it dosn't seem to beable to find the tv tuner card.

Please help! Many thanks

Will

---

### Post by Mark_in_Hollywood on 2013-02-13
Too little information. For future responders your post, please give make, or manufacturer of your device, model, software/firmware infos, too. Also, state the country you are in. That matters a lot for MythTV.

Have a look at this: 

[http://ubuntuforums.org/showthread.php?t=2028123](http://ubuntuforums.org/showthread.php?t=2028123)

If your model/firmware are similar enough, it could work.

---

### Post by willbrimmer on 2013-02-13
Sorry i didnt know what information was needed.

The device is this one: [http://www.amazon.co.uk/Digital-Freeview-Receiver-Recorder-Supports/dp/B007SME3A6/ref=sr_1_6?s=computers&ie=UTF8&qid=1360798317&sr=1-6](http://www.amazon.co.uk/Digital-Freeview-Receiver-Recorder-Supports/dp/B007SME3A6/ref=sr_1_6?s=computers&ie=UTF8&qid=1360798317&sr=1-6)

Sofware/firmware i am unsure of.   i think i have installed 
dvb-usb-it9135-02.fw but i am not sure?

I am in the Uk

Thanks
Will

---

### Post by Mark_in_Hollywood on 2013-02-14
Please copy the terminal output of 

lsusb

I only need the line that is your TV tuner. If you cannot make it out, paste all of them here.

I looked carefully at the Amazon listing. I cannot read the name of the maker or any identifying info.

If I said I could help you without that, I'ld be joking. If you can find any information on the dongle that plugs on or under the battery compartment of the remote, we could give it another shot, but if there is -no- more info, I would suggest waiting for someone who may have your device. Got a good magnifying glass?

If you have the package it came in scour that for Manufacturer name, model number, any number other than say 1 or 2. 

It took me over 2 years before I realized that the AverMedia Duet card I had would never have the Linux support it deserved. Excellent product (hardware) but will never work in Linux.

---

### Post by willbrimmer on 2013-02-15
Hello,

Thanks for helping me.

lsusb : Bus 002 Device 005: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

The packaging doesn't have a lot of info.  The brand is Digital Energy but unhelpfully there is not serial number or model number.  

I think it is the third one down from this list:  [http://linuxtv.org/wiki/index.php/ITE_IT9135](http://linuxtv.org/wiki/index.php/ITE_IT9135)

Many Thanks

---

### Post by Zill on 2013-02-15
No guarantees but it might be worth trying the "Linux Installation" instructions posted by Rachael Bond for the [ClimaxDigital DTV395 USB 2.0 DUAL DVB-T TV Tuner]("http://www.amazon.co.uk/product-reviews/B004F1MPYY") on the Amazon website.  Although the chipset quoted is different to yours (048d:9006), the driver appears to be the same as for the 048d:9135.

HTH.

---

### Post by Mark_in_Hollywood on 2013-02-17
Thanks for posting that LinuxTV page. I can use that myself.

The third item in the list, probably your device, is supported with a new kernel. In order to know whether you have that kernel, or an even more recent one, in a terminal, type:

uname -r


Mine looks like this:

mark@Lexington-19:~$ uname -r
3.2.0-37-generic-pae

As you can see, I have a kernel that is .2 places away from the one you should use. As I also have the most recent Ubuntu standard release (that is the one most users have), if you do not have this

"Yes, in kernel since **3.4**" 

you will have to post another time, as I have no skills in upgrading the kernel to one that doesn't come through the distribution-upgrade repositories.

I did try to upgrade my kernel, a long time ago, there are three parts (packages?) and they must be installed in a particular order. That was true back then, now? I dunno. So, please post a question, maybe in the Installations forum and somebody there will be better able to help.

---

