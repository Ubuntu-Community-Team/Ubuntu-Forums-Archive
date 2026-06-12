---
title: "Problem during updation"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by ck007 on 2008-07-23
Hi,

I am currently usin ubuntu 7.10 with all updates upto date.But yesterday only i downloaded alternate cd image to upgrade my system to 8.04 n tried to upgrade through the image burned on cd.

The updation started n also downloaded some files from internet durin updaion process but it kept on closin while in creating new software channels option (hope remember the option correctly) and then a notification started to appear as new updates available.this also came up wit giving option to partial update which i tried 3-4 times but again same,closin in channel part.

Now i went wit updation process instead of partial upgradation procedure and it shhowed 627 updates available n 88.7 mb of files to b downloaded.I downloaded all n started off wit update process but in middle only system got off due to power failure n updation process got interupted.

Now when starting ubuntu i am seeing different different windows opening n closing by itself n after that it shows option to delete ** OAFIID: DeskBar_Applet **. I didnt delete n chose to keep it but everytime this poped up,so deleted it.In both case before n after deletion  I cant access anythin,Place->Computer or anythin.Cant open anythin n also dvd rom is gettin locked.

Please help wat to do,no much idea about linux as completely new here.Please help me out.

Thanks.

---

### Post by roquefilipe on 2008-07-24
hum, sounds to me that it might be easier to just reinstall Ubuntu from scratch. Just make sure you backup all your data. 

If you choose to go this way, I advise to create a separate partition for /home. This way, is possible to reinstall your system many times without loosing your data. Many Linux users disagree but I found it to be simpler for beginners who are always experimenting.

---

### Post by ck007 on 2008-07-28
> **roquefilipe said:**
> hum, sounds to me that it might be easier to just reinstall Ubuntu from scratch. Just make sure you backup all your data. 

If you choose to go this way, I advise to create a separate partition for /home. This way, is possible to reinstall your system many times without loosing your data. Many Linux users disagree but I found it to be simpler for beginners who are always experimenting.

But I cant do anythin in my system...how do i take back up???
Will install Ubuntu 8.04 once i can get back my files..Have windows also but that cant access linus so if posible provide any alternative.

---

### Post by PmDematagoda on 2008-07-28
Usually partial updates are not given unless:-
1) You are using a development version(which is also unlikely).
2) The packages to be updated have improper dependencies or dependencies on packages that have not been uploaded yet.
3) You are using incompatible repositories where the dependencies for packages are vastly(or even slightly) different from the official repositories. 

So the fact that you were given partial updates in the first place may have been the problem. But about recovering Ubuntu, try this:-
1) Boot Ubuntu in Recovery Mode.
2) Once you reach the terminal, execute:-
```
apt-get install -f
```
and
```
dpkg --configure -a
```
after all that is done, reboot Ubuntu with:-
```
reboot
```
and see if that fixes the problems.

---

### Post by GaretJax on 2009-05-24
I never heard from the original poster's success or failure on this topic but I will tell you that this fixed my problem very well!

I basically ran into the same problem.  I am running Ubuntu 8.04 and my system fell asleep while installing updates.  I would then get this OAFIID: Deskbar_Applet error message everytime I logged in and most programs would not run.  So I followed your advice by booting into recovery mode and running those commands.  I took all the defaults when asked for any input and everything went smooth.

I want to really thank you for you help because I read some other posts before I got to yours and they said to reinstall  :o

---

