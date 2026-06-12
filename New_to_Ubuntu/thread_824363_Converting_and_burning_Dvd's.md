---
title: "Converting and burning Dvd's"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by kjswimmer on 2008-06-10
Ok so im completely new and im lost so help would be appreciated but i need u to walk me threw each step cause i dont know where everything is and all that suff  

So problem is that im trying to Download a program that will convert avi files to mpeg2 so that i can burn them onto a dvd to watch on a dvd player. 
I've tried downloading dvdauthor with "sudo apt-get install dvdauthor" and it goes threw just fine no errors but then it wont show up on my hard drive. 
I've never burned a dvd before so if someone would walk me threw this that would be great thanks for the help

---

### Post by MockY on 2008-06-10
Install DeVeDe. It converts your mpg or avi files into an ISO that you simply can burn onto a DVD so watch it via your DVD player.

```
sudo aptitude install devede
```

---

### Post by kjswimmer on 2008-06-10
will all dvd players play an dvd stored as an iso?

---

### Post by cjv8888 on 2008-06-10
ISO is just an image which you use to burn to a DVD.  Use a program like Gnomebaker or K3B to burn the DVD when you have authored the ISO

---

### Post by billgoldberg on 2008-06-10
> **kjswimmer said:**
> will all dvd players play an dvd stored as an iso?

Yes, it's pretty much the standard.

---

### Post by kjswimmer on 2008-06-10
do u have to put the iso image in a certain structure or something like i remember reading about it on another page and i was completley lost about what it was trying to tell me

---

### Post by kjswimmer on 2008-06-10
oh sorry about posting twice but i forgot will the audio work to once i converted it to an iso image? or do i hvae to do something different for the audio?

---

### Post by cariboo on 2008-06-10
Devede automagically creates the iso image for you, the only thing you have to do is burn it to an appropriate size disk, and load it into your dvd palyer and grab the popcorn:).

Jim

---

### Post by halitech on 2008-06-10
Devedee works great if you just have a single movie you want on a DVD. If you are looking for something that will allow you to put multiple video files on a single dvd, try ManDVD ( [http://www.getdeb.net/app/ManDVD](http://www.getdeb.net/app/ManDVD) ) it will require getting some dependencies manually but it works great for me.

---

### Post by MockY on 2008-06-10
> **kjswimmer said:**
> oh sorry about posting twice but i forgot will the audio work to once i converted it to an iso image? or do i hvae to do something different for the audio?

It is all done automatically for you. Once done converting, pop in the DVD disc in your burner and just right-click the iso and select "burn to disc" (assuming you run Gnome). Once that's done, I would follow cariboo907 advice... grab the popcorn.

---

