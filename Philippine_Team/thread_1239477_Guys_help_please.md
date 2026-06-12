---
title: "Guys help please"
date: 2009-08-13
forum: Philippine Team
---

### Post by fatboy07 on 2009-08-13
guys I need help.. Ive already installed my ubuntu 8.10 dual boot with windows xp, can somebody tell me how I can do this... [http://news.softpedia.com/news/Ubuntu-8-10-Desktop-Customization-Guide-100830.shtml](http://news.softpedia.com/news/Ubuntu-8-10-Desktop-Customization-Guide-100830.shtml) the needed files is in my usb drive already extracted it in my usb, but my problem by following step 1 I cant use my files in my usb.. sorry guys totally noob/newbie in ubuntu...

---

### Post by doas777 on 2009-08-13
do you have internet? if so forget about the usb drive. you won't need it. just follow the instructions from the tutorial.

---

### Post by loell on 2009-08-13
can you indicate what part of the tutorial you have followed?

---

### Post by fatboy07 on 2009-08-13
Im still in step 1, I dont have an internet connection here @ home so I downloaded the files need also extracted it.. hope you can help me.. I really want to learn this kind of stuff, TIA!

---

### Post by doas777 on 2009-08-13
so you need to get your thumb drive mounted first. does it show up in Places -> Computer? if so, doubleclick it and give your password. hopefully that will do it.

if the drive does not show up, leave it plugged in and reboot. does it show up now?

if all that fails, open up a terminal (Applications -> Accessories -> Terminal) and paste in:
```
sudo fdisk -l
```
provide your password when prompted.
then post back with the output from fdisk.

I prolly can't help you get the packages installed (unless their .debs), but mounting the usb drive shouldn't be a problem. hopefully someone else will be able to assist from there.

---

### Post by loell on 2009-08-13
ubuntu isn't that much without internet connection. 

 do you really have the necessary deb files in your usb disk, may I ask how did you get them all and it's dependencies?  

Well anyway, regardless on how you got the deb files from the online repository to your usb disk, installing the deb files is fairly simple, you attach the usb disk, then navigate the directory of the usb device

**cd /media/name_of the_usb_disk**

then install the deb files

**sudo dpkg -i *.deb**

___________________________________________________

but given what you said that you're a new user, the unlikelihood that you got all the necessary files to your usb disk is probably higher, then may I suggest that you use [ultimate edition?]("http://ultimateedition.info/ultimate-edition-2-3/"), probably download it from one of your friends that  also has a DVD writer?

---

### Post by fatboy07 on 2009-08-13
> **loell said:**
> ubuntu isn't that much without internet connection. 

 do you really have the necessary deb files in your usb disk, may I ask how did you get them all and it's dependencies?  

Well anyway, regardless on how you got the deb files from the online repository to your usb disk, installing the deb files is fairly simple, you attach the usb disk, then navigate the directory of the usb device

**cd /media/name_of the_usb_disk**

then install the deb files

**sudo dpkg -i *.deb**

___________________________________________________

but given what you said that you're a new user, the unlikelihood that you got all the necessary files to your usb disk is probably higher, then may I suggest that you use [ultimate edition?]("http://ultimateedition.info/ultimate-edition-2-3/"), probably download it from one of your friends that  also has a DVD writer?


ok thanks hope this would work so I can follow the steps...

---

### Post by fatboy07 on 2009-08-13
.gz file is compressed file right? ive already extracted it in same usb drive im still in step 1 still i cant see the avant file when i open synaptic package manager.. TIA!

---

### Post by loell on 2009-08-14
> **fatboy07 said:**
> .gz file is compressed file right? 
yes, that's correct.


but the above link you provided didn't mention any steps about any **.tar.gz** file, so you may be following a different steps or "how to".

my guess is that, you downloaded the source  files for avant window navigator (which is the first topic of the "how to"). you see, program source files need to be compiled before the program can run, compiling program needs several hundred files that's mostly pulled online.

---

### Post by fatboy07 on 2009-08-14
> **loell said:**
> yes, that's correct.


but the above link you provided didn't mention any steps about any **.tar.gz** file, so you may be following a different steps or "how to".

my guess is that, you downloaded the source  files for avant window navigator (which is the first topic of the "how to"). you see, program source files need to be compiled before the program can run, compiling program needs several hundred files that's mostly pulled on line.


oh i see... can you help me? yeah your right I downloaded it by clicking the link and save it to my usb, and extracted it when im done installing ubuntu to my PC, so sorry Im totally noob or maybe an idiot...but i really want to know this kind of stuff hope you can help me...

---

### Post by loell on 2009-08-14
> **fatboy07 said:**
> oh i see... can you help me? yeah your right I downloaded it by clicking the link and save it to my usb, and extracted it when im done installing ubuntu to my PC, so sorry Im totally noob or maybe an idiot...but i really want to know this kind of stuff hope you can help me...

I'm not yet sure what i can do to help, like i said, ubuntu isn't much without the internet.

i think  you can create an ubuntu bootable usb disk , so you can use ubuntu at your work place, during lunch or break time.  download and install programs from there. So then you can also boot and use it at home.

---

### Post by fatboy07 on 2009-08-14
> **loell said:**
> I'm not yet sure what i can do to help, like i said, ubuntu isn't much without the internet.

i think  you can create an ubuntu bootable usb disk , so you can use ubuntu at your work place, during lunch or break time.  download and install programs from there. So then you can also boot and use it at home.


I hope i can all optical drive and usb  here is restricted.. so you mean if i have a bootable usb of ubuntu ill just plug it any pc have internet and click the download link? by the way can you help me how i can install my w200i as modem in ubuntu? thanks for reply sir loell...

---

### Post by loell on 2009-08-14
> **fatboy07 said:**
> I hope i can all optical drive and usb  here is restricted..

I see. that's rather unfortunate, as i couldn't see another lee way for you to install programs in ubuntu without an internet connection at home.

> **fatboy07 said:**
> 
 so you mean if i have a bootable usb of ubuntu ill just plug it any pc have internet and click the download link? 

partially yes but no, you see when you boot ubuntu, say on a usb stick, you practically run it on a pc without affecting the hard disk, it's more like a floating operating system. then from there, you can now follow the tutorial in your original post. no download links, just the instructions.

> **fatboy07 said:**
> 
 by the way can you help me how i can install my w200i as modem in ubuntu? thanks for reply sir loell...

sony ericson w200i seems to be incompatible with ubuntu, so ubuntu couldn't use it's modem feature.


I know this must be disappointing for you, that you couldn't try the things you like without having to use the internet in ubuntu, but such is the truth that ubuntu and linux in general is heavely dependent on the internet to install and or update programs.

---

### Post by fatboy07 on 2009-08-14
> **loell said:**
> I see. that's rather unfortunate, as i couldn't see another lee way for you to install programs in ubuntu without an internet connection at home.



partially yes but no, you see when you boot ubuntu, say on a usb stick, you practically run it on a pc without affecting the hard disk, it's more like a floating operating system. then from there, you can now follow the tutorial in your original post. no download links, just the instructions.



sony ericson w200i seems to be incompatible with ubuntu, so ubuntu couldn't use it's modem feature.


I know this must be disappointing for you, that you couldn't try the things you like without having to use the internet in ubuntu, but such is the truth that ubuntu and linux in general is heavely dependent on the internet to install and or update programs.


its more likely a bad news for me.. :( but by the way thank you so much for being helpful sir loell... thank you so much! oh wait how about using a usb modem like globe tattoo? is that posible?

---

### Post by loell on 2009-08-14
> **fatboy07 said:**
>  thank you so much! oh wait how about using a usb modem like globe tattoo? is that posible?

no problem :), glad I could shed some basic infos, yes globe tattoe can be used in ubuntu with the right configuration or tweak.

---

### Post by fatboy07 on 2009-08-15
> **loell said:**
> no problem :), glad I could shed some basic infos, yes globe tattoe can be used in ubuntu with the right configuration or tweak.


really? can you help me for the configuration? maybe next week I have my tattoo or globe visibilty, also if i have time Ill finish my desktop made just for ubuntu! thanks you so much sir loell,

---

### Post by rjmdomingo2003 on 2009-08-16
> **fatboy07 said:**
> really? can you help me for the configuration? maybe next week I have my tattoo or globe visibilty, also if i have time Ill finish my desktop made just for ubuntu! thanks you so much sir loell,
guess even with the tattoo you would need to install packages: 
[http://neildecapia.wordpress.com/2009/07/05/globe-tattoo-on-ubuntu-jaunty-9-04/](http://neildecapia.wordpress.com/2009/07/05/globe-tattoo-on-ubuntu-jaunty-9-04/).

you can also check this out: [http://ubuntuforums.org/showthread.php?t=1237229](http://ubuntuforums.org/showthread.php?t=1237229)

---

### Post by rjmdomingo2003 on 2009-08-16
Hope this helps: [http://keryxproject.org/](http://keryxproject.org/)

...and this: [http://ubuntuforums.org/showthread.php?t=1235477&highlight=offline+install+packages](http://ubuntuforums.org/showthread.php?t=1235477&highlight=offline+install+packages)

---

### Post by edyeeh on 2009-08-23
aha.. avant window navigator. astig yan.

dahil tar.gz ang nakuha mo. malamang source files yan. Mas hassle install yan kasi may kukunin ka pang mga -dev files. compile and install pa. mas madali kung .deb files.

May paraan para mag install ng files nang hindi gumagamit ng synaptic. Kuha ka lang ng mga .deb files na na download galing sa isa pang computer. (baka sa computer shop). tapos install mo na parang mga single .exe files sa Windows. I-double click mo lang ang ng deb files tapos mag uumpisa na ang install GUI style.

may site ang ubuntu ng lahat ng packages nila na pwedeng makunan. Ito yung packages ng avant-window-navigator sa site:

[http://packages.ubuntu.com/jaunty/avant-window-navigator](http://packages.ubuntu.com/jaunty/avant-window-navigator)

try mo nalang isakto sa tamang distribution. at tignan yung related packages para sa mga dagdag na applets.

pagkakaalam ko kasi madalas kasama na rin mga requirements sa isang *.deb file. okay yan kasi pwde kang magdownload galore sa isang computer na may internet,lagay mo sa usb tapos install galore ka na rin sa computer mo. Importante lang na dapat na tamang architecture type yung gamit. amd64 or i386 o hindi siya gagana.

---

### Post by EXCiD3 on 2009-08-23
If you're having trouble with downloading packages and dependencies for an offline machine, check out [Keryx]("http://keryxproject.org").

---

### Post by fatboy07 on 2010-08-01
naku sir thank you po sa response nyo,  so desperate tlga.. mag 1year na tong post ko hindi na nabisita.. salamat po ng marami..

---

