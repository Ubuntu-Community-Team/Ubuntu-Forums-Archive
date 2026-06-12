---
title: "Beginning Ubuntu  Linux 8.04 Questions"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by rab2140 on 2008-07-03
Hello all, I am new to world of Ubuntu and i have a few questions that i hope you can answer.

Let me start by saying first of all, Ubuntu is a fantastic Os and it has a great User Interface and everything it does, it does very well.  

Being a total windows user for a long time, I find Linux VERY foreign. In terms of Updating drivers and installing files.

My first question is : How do i install files i download?

When i download files for example a driver from nvidias website it links me to a page with all this writing on it! how do i actually make the file i'm trying to get executable?

2: How do i update drivers for my gfx card and mobo? I find trying to update annoying because i don't know if linux updates the hardware for you or you have to do it yourself.

3: Is there any applications that i can use on linux that lets me take pictures with my webcam. I use ebay and i need to take pictures with my webcam. 

If all these problems where sorted i would really consider making linux my full time os :D

Thanks alot

---

### Post by powerpleb on 2008-07-03
1. In Applications >> Add/Remove Applications look for any software you wish to install (make sure the drop down menu at the top is on 'All available applications') select it and click 'Apply Changes' (installing software in Linux is usually a lot easier than in Windows). The Nvidia drivers are in there as well as lots of other software. Applications >> Administration >> Synaptic Package Manager has more software if you need it.
2. Everything will be updated automatically if you install software with the previous method.
3. Yes, 'Cheese' which you can find by doing a search in Add/Remove Applications or Synaptic Package Manager

---

### Post by Muhammad on 2008-07-03
> **powerpleb said:**
> 3. Yes, 'cheese'

Just wanted to confirm that this member is not joking, there really is an app called "Cheese"

---

### Post by Sef on 2008-07-03
> My first question is : How do i install files i download?

Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

> 3: Is there any applications that i can use on linux that lets me take pictures with my webcam. I use ebay and i need to take pictures with my webcam.

Cheese.  It is in the repositories.  Applications > Add/Remove > Search for: Cheese > Click on box next to Cheese > Apply Changes > Apply > close


> Just wanted to confirm that this member is not joking, there really is an app called "Cheese"

The name comes from taking pictures.  When you are taking pictures, you tell the one or ones in the photo to say 'Cheese' to get them to smile.

---

### Post by iaculallad on 2008-07-03
> **rab2140 said:**
> My first question is : How do i install files i download?

That would depend on the type of file you downloaded and want installed, visit this [link]("http://monkeyblog.org/ubuntu/installing/#source") for the complete guide.

> **rab2140 said:**
> 
When i download files for example a driver from nvidias website it links me to a page with all this writing on it! how do i actually make the file i'm trying to get executable?


Usually, nvidia drivers comes with the extension of .run, all you have to do is download the file and change directory to where the downloaded file resides (.run): Using the terminal:

```
sudo sh NVIDIA-Linux-x86-177.13.pkg1.run
```


> **rab2140 said:**
> 2: How do i update drivers for my gfx card and mobo? I find trying to update annoying because i don't know if linux updates the hardware for you or you have to do it yourself.

Usually, with this question, you can always use the Restricted Driver Manager.

> **rab2140 said:**
> 3: Is there any applications that i can use on linux that lets me take pictures with my webcam. I use ebay and i need to take pictures with my webcam.

Try camstream or camorama

---

### Post by rab2140 on 2008-07-03
LOL Cheese, I will look it up, Thanks for the information.

---

### Post by hyper_ch on 2008-07-03
well, it might be that the webcam isn't supported... then you have bad luck... you could then boot into windows, use the cam there and then share the pics with the ubuntu install - as an option...

besides, it is adviced to use seperate threads on unrelated questions and it's also adviced to do some research on the problem first ;)

---

### Post by AiBo on 2008-07-03
I used this all the time when i first started out:

[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Muhammad on 2008-07-03
> **Sef said:**
> The name comes from taking pictures.  When you are taking pictures, you tell the one or ones in the photo to say 'Cheese' to get them to smile.

Dude! I know that. [img]http://ubuntuforums.org/images/icons/icon7.gif[/img]

---

