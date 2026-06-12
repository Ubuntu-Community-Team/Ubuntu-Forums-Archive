---
title: "How to install Ubuntu on Asus 1015PX...for Dummies"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by Ateilu on 2012-04-12
I realize that it's highly likely that such a post had already been posted and solved, but I've owned my Asus 1015PX netbook for a month now, have tried to read and understand the posts on several forums, and I still can't really understand all the lingo in order to install Ubuntu onto my netbook.  I know how annoying it is to post a question that's been asked a thousand times, but please trust me when I say that I've really tried to read through everything!  So seeing as how there's an "Absolute Beginners" forum, I'm hoping there might be a step-by-step "How to install Ubuntu...FOR DUMB DUMB DUMMIES" like me.

So this is what I have so far:

Asus EeePC 1015PX, N570 -- it has Express GateCloud and an option to have Windows Assistant to install Windows (which I haven't installed and don't want to install)
I have another laptop, which runs Windows 7, to work off of to create the bootable USB drive and stuff like that
I have a 8GB USB pen drive (RALLY2, ocztechnology)
I've downloaded LinuxLive USB Creator onto my laptop
An ethernet cable so that my netbook doesn't have to go wireless

Some notes:
- On my netbook, pressing ESC never seems to work.  F2 works, and then I go to Boot and can prioritize the order there.  Is that okay?
- I was initially trying to install 11.10, but if you have step-by-step instructions on another version, that's fine too.

THANK YOU!!

---

### Post by mastablasta on 2012-04-12
> **Ateilu said:**
>  
Some notes:
- On my netbook, pressing ESC never seems to work. F2 works, and then I go to Boot and can prioritize the order there. Is that okay?
- I was initially trying to install 11.10, but if you have step-by-step instructions on another version, that's fine too.
 
THANK YOU!!
 
after you created USBlive disk using LinuxliveUSB then... 
 
well somehow you need to set the boot order to get the USB to boot first. what key to press in order to do that depends on BIOS (motherboard). it's best to check the manual to get the exact key. If pressing F2 on boot gives you a boot menu then i guess f2 is the one that needs to be pressed.
 
Once you boot from USB you can first select try it or you can immmediatelly start installing it. follow this guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
 
if it doens't want to boot form USB you need to check if the ISO you downloaded is exactly the same as on server. if oyu used torrents for download thi sis done for oyu but if you used normal download then you need to check the md5sum. and here is how you do it (scroll down to get the windows instructions):
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

