---
title: "NVIDIA GeForce 6200: Sluggish graphic performance"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2012-05-08
First of all this is my specifications. AMD 3200+ 2.02GHz CPU, 3Gb RAM, 720Gb HDD, NVIDIA GeForce 6200 512Mb (Shares 256Mb from main memory) and a Gigabyte Motherboard.

I'm only using LTS version in my desktop earlier I was using 10.04 but I just did a clean install and after that I installed the preparatory drivers from NVIDIA web site.

After finishing that I booted into the OS to see that my graphic performance on Untiy3D is functioning barely but when I switch to Unity2D it's OK and responsive.

If I upgrade my VGA card to a NVIDIA 9200GT with a 512Mb VGA will my graphic performance improve. Please, fill me in with your advice thank you.

---

### Post by idoitprone on 2012-05-09
deleted everything that i posted because it was stupid info that me lol

---

### Post by sadaruwan12 on 2012-05-09
Any suggestions are welcome and nothing is stupid.

---

### Post by jtarin on 2012-05-10
Are you using Nvidia proprietary drivers? If yes try using the drivers provided by Ubuntu. I have heard that their drivers are less than hoped for.

---

### Post by UltimateCat on 2012-05-10
When I stopped using proprietary drivers my graphics associated with Ultimate Edition 2.7; Ubuntu 10.04 stopped crashing.

Folks at linuxquestions.org advised me (twice) that as long as I don't use them I won't have problems or conflicts with my graphics card.

The option to upgrade is there but maybe you could consider looking into the details of the newer GeForce-

Hope this helps

---

### Post by sadaruwan12 on 2012-05-10
Thank you very much guys, Can some please tell me how to remove the proprietary NVIDIA drivers from my system.

But when I was using the 10.04 the proprietary drivers there was no issues and it worked like a charm but after the upgrade every thing went nice to bitter.

But I'll try the drivers from the repo. Also I've ordered a VGA card the model NVIDIA 9500GT with 1Gb and this card is listed as a entry level gaming card so this will work I think.

---

### Post by Shadius on 2012-05-10
> **sadaruwan12 said:**
> Thank you very much guys, Can some please tell me how to remove the proprietary NVIDIA drivers from my system.

But when I was using the 10.04 the proprietary drivers there was no issues and it worked like a charm but after the upgrade every thing went nice to bitter.

But I'll try the drivers from the repo. Also I've ordered a VGA card the model NVIDIA 9500GT with 1Gb and this card is listed as a entry level gaming card so this will work I think.

I believe you go to System > Administration > Additional Drivers, and you'll be able to remove the drivers. Someone correct me if I'm wrong.

This might be helpful to you:  [Remove NVIDIA Proprietary Drivers]("http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers")

---

### Post by sadaruwan12 on 2012-05-10
> **Shadius said:**
> I believe you go to System > Administration > Additional Drivers, and you'll be able to remove the drivers. Someone correct me if I'm wrong.

That want do it 'cos these drivers are not installed from the ubuntu driver repository. I installed them using the NVIDIA driver installer that is not associated with driver installer.

---

### Post by mastablasta on 2012-05-10
there are some bugs in latest drivers. you need to know which one (version) to install so it works propperly.
 
links to manual install, bugs  etc: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by sadaruwan12 on 2012-05-11
Yesterday I uninstalled the drivers from nvidia and went to there site just see. For my amazement they have released another update for the driver 290.49 in this they have admitted that there is a slowness in graphic effect and they have claimed that issue has been dealt with.

So I downloaded that driver and installed it and yes the sluggishness of the graphics has been reduced but it's still there I reckon that this issue will get solved in time.

So for that I'll be marking this thread as solvedd.

---

### Post by brettg on 2012-07-09
Actually, it's not solved.

---

### Post by glennric on 2012-07-09
Try installing the nvidia-current-updates version of the proprietary nvidia drivers that are in the precise-updates repository.  The package version is 295.49-0ubuntu0.1.  Of course that package contains the 295.49 version of the proprietary nvidia drivers.  You may also need to completely uninstall the nvidia-current package (with the 295.40 version of the nvidia drivers).  Maybe the bug is fixed but there seemed to be conflicts with the two packages both installed when Ubuntu 12.04 was first installed.  If you have installed nvidia drivers using some other script you will have to figure out how to uninstall those.

I am using the nvidia-current-updates package above for an nvidia geforce 6150 le, and they work fine.

Most likely the nouveau drivers won't be better for you.  Those are the open source drivers that Ubuntu provides.  jtarin's comments are misinformed as nvidia provides better support for their video cards under linux than any other video card manufacturer, and their proprietary drivers generally work much better than the open source alternative.  Particularly if you use any 3d effects.

---

### Post by jtarin on 2012-07-09
> **glennric said:**
> 
 jtarin's comments are misinformed as nvidia provides better support for their video cards under linux than any other video card manufacturer, and their proprietary drivers generally work much better than the open source alternative.  Particularly if you use any 3d effects.jtarin's comments are misinformed as of recently....when Linus blasted Nvidia and they got back on the job of keeping current with Linux. I've been using Nvidia with Linux for over 13 years.....I have some knowledge of their driver development for Linux. Saying they provide better support than any other manufacturer is different than what I said.

---

### Post by glennric on 2012-07-09
jtarin: Yes, it is true that saying that NVidia provides better linux support than any other card manufacturer is different than saying that the open source drivers are better than the proprietary ones.  I have also been using Nvidia with linux for a long time, and there have been some rough spots over the years.  Generally speaking though the proprietary drivers perform better than the open source alternatives.  Particularly in regards to 3d acceleration.  In this regard the open source alternatives have not even been a viable alternative until quite recently.

---

### Post by sadaruwan12 on 2012-07-12
OK guys I got my self a new 9800GT 1Gb nvidia card and yes my graphic performance did got improved and became smoother.

I installed he drivers from the X-SWAT repo and they do keep things updated but with the proprietary drivers when a kernel update happens it's always better to reinstall the drivers so they can compile them self to suite the kernel.

And yes NVIDIA do support the Linux platform more than the other card vendors 'cos I have used the both other VGA's and found nvidia to be the best for the time being.

---

