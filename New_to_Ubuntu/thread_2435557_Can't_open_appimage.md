---
title: "Can't open appimage"
date: 2020-01-22
forum: New to Ubuntu
---

### Post by fidgety on 2020-01-22
Hi there, Im running Ubuntu 18.04.03.

Before installing Ubuntu, I started by installing Linux Mint by way of reccomendation from a friend. After not getting something to work the way I wanted, I installed Ubuntu. It turned out in the end Linux mint wasn't doing anything wrong, but I went through the hassle of changing to Ubuntu and couldn't be bothered reinstalling. The reason I mentioned Linux Mint, was because when I had that installed, one of the most important things I had to do straight away was see if I could get my Ledger working on Linux using the ledger live software. On linux Mint I downloaded the appimage and opened it. It worked straight away apart from the software not being able to detect my device. I did some research and found that I had to set permissions for the app to access my USB device. This was my first experience using a app image and I was very impressed that there was no installing like on windows. App images are awesome IMO.

Well, I was expecting to follow the same proceedure on Ubuntu, I thought Linux mint was basicly the same except for pre installed software, but, no, Ubunti says it cant open app images.
Can anyone tell me if its possible to open app images on Ubuntu? I'm hoping it's just a case of maybe having to download a dependency? 

The exact error that displays after attempting to open the app image is --- Could not display "*****************.appimage"

There is a challenge after asking if you would like to search for the application to open the file. After clicking this a box appears at the top of screen and lets you search software manager. Clicking that says nothing can be found and sends you to a website explaining repositorys.

Can someone tell me what it is I'm looking for to open app images.

Regards

---

### Post by CelticWarrior on 2020-01-22
You may need to run it from terminal because the new Ubuntu releases are somehow limited by the upstream Gnome's new way of handling executable files.

---

### Post by fidgety on 2020-01-22
Thanks for replying CelticWarrior. I figured it out. You have to right click the file, go to properties, and click "allow executing file as program" on permissions tab. I remember now I had to do this on Linux mint also, but I had forgotten. 
Would be nice if the pop up said something like this and didn't make you think you were missing something from the repository.

---

