---
title: "Access shared hardrive from windows machine"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by TRLOS on 2012-10-30
So, Here is my second thread & question. I have searched around and not found anything that is exact to my situation or anything I can extrapolate an answer from. 

SITUATION:

I have Ubuntu running beautifully as a streaming server on an old Dell Dimension 8300. Media being streamed is on an external 3 TB HDD. I Still use Windows 7 on my laptop which is my primary computer and as such I am constantly adding music, movies, shows, and pictures to my laptop. The previously mentions 3 TB external is (apart from the media container for my system) also my backup hardrive when I store everything I don't want to lose.

DILEMMA:

I want to be able to access the shared drive from my Win7 laptop without having to unplug the stupid thing and switch it to the laptop. Now, I already made the drive shareable and I can see it on my laptop as well as click on the hardrive to access it but when I click to access it I get a windows credentials prompt. I have tried my laptops username and password as well as my ubuntu machines user name and password. Heck, I even tried Root, Root (Not that I expected it to work (because it didnt)). So thats the problem.

QUESTION:

How do I either find/make the credentials I need or otherwise sidestep them so I can update my system backup without having to physically handle the medium?

all HELP is appreciated,
     Thanks in advance

Also sorry in advance if this does end up being a repeat topic.

Scratch question...Im an idiot, Solved by checking Guest Access box under allow others to create and delete files...Share tab in properties.

---

### Post by newb85 on 2012-10-30
It would be much more secure to follow the instructions at
[http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/]("http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/")

---

