---
title: "How can I make my own Ubuntu ISO?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by Zonack on 2013-06-28
Hey guys, recently I installed Ubuntu 13.04 and installed a couple of programs that the company developers need and also graphically configured so it would have company colors and logos and stuff like that. A company themed Ubuntu.

[ATTACH=CONFIG]244243[/ATTACH]


Now I was asked to make an .ISO so that everytime we install it in a new machine it will have all those programs and graphical configurations.
Is there a way to do such thing? Or I can just save some settings and have to modify the rest manually?

Thanks in advance.

---

### Post by cub on 2013-06-29
I haven't tried it myself but seems to be a guide at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) .

---

### Post by amjjawad on 2013-06-30
> **cub said:**
> I haven't tried it myself but seems to be a guide at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) .

Have not tried it yet too but I was about to post the same link so +1

---

### Post by gordintoronto on 2013-07-02
Have a look at remastersys, I think it is exactly what you need.

---

### Post by mastablasta on 2013-07-02
remastersys or system imager as it is now known will create an installable image (i.e. your very own distribution).

another option is to simply clone the image with clonezilla or redobackup and then copy it on all computers you need to copy it too. clonezilla has a bit more options but interface is not so user friendly. you can also distribute the image via net.

---

### Post by HermanAB on 2013-07-02
Hmm, +1 for remastersys.  

This is why Redhat is more popular - they have kickstart.  Kickstart can be used to do a scripted network install - super easy deployments.

---

### Post by Zonack on 2013-07-03
Remasterys doesn't seem to have repositories for Raring Ringtail, should I use the Quental Quetzal one?

Thanks for all the answers by the way.

---

### Post by cub on 2013-07-03
> **Zonack said:**
> Remasterys doesn't seem to have repositories for Raring Ringtail, should I use the Quental Quetzal one?

Thanks for all the answers by the way.
In that case I would go for 12.04, Precise Pangolin, since it Long Time Support.

Did you try the [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) solution?

---

### Post by Zonack on 2013-07-08
I am trying now the LiveCDCustomization. I will update on how it goes, sorry for the delay but work has been crazy busy.

---

### Post by Zonack on 2013-07-08
Ok wow, seems I got stuck way too fast.
While following the instructions on how to make Chroot by typing the command



sudo debootstrap --arch=$ARCH $RELEASE chroot 
I am making a 13.04 version so according to the guide (and to what I understand) it should be


sudo debootstrap --arch=i386 13.04 chroot
However when I type it, it says.

E: No such script: /usr/share/debootstrap/scripts/13.04

Man, using Ubuntu for the first time and be asked to do this right away is kinda hard. :/

---

### Post by holycow131415 on 2013-07-08
I would really just use clonezilla. Its easy, just follow the prompts.

---

### Post by BR8 on 2013-07-08
I'm not sure how in-depth it gets, but you could check out Ubuntu Builder. It should be in the Software Center. You'll need an .iso to edit.

---

### Post by 2Stoned on 2013-07-09
> **BR8 said:**
> Ubuntu Builder. It should be in the Software Center. You'll need an .iso to edit.

Ubuntu builder is very simple to use with the GUI, it works great. It is not available from the software center tho..

First download Ubuntu Builder: [https://code.google.com/p/ubuntu-builder/](https://code.google.com/p/ubuntu-builder/)

After that you should download the 12.04 version of the mini remix: [http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)


Check out these tuts, very helpfull.

[http://askubuntu.com/questions/48535/how-to-customize-live-ubuntu-cd](http://askubuntu.com/questions/48535/how-to-customize-live-ubuntu-cd)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

If you need any help, just shout!

---

