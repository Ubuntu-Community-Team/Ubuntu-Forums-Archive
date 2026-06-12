---
title: "Help :("
date: 2012-08-24
forum: New to Ubuntu
---

### Post by yamandude on 2012-08-24
OK , so this is my query , which i asked everywhere ( except here ) and couldnt be answered in a way by which i can get positive results .

I have a HP dv6-7010tx laptop with 8Gigs of RAM . I want to dual boot my laptop with ubuntu ( mainly because its better battery efficiency , new UI , less distracting ) . 

The problem that i'm facing is that , if i try to do the regular install ( the ' Something Else ' option ) , on further installtion i get some ' Kernel ' related error and on rebooting , i cant boot into my windows -> resulting in a completely fresh Recovery ( Factory Reset ) .

On trying the WUBI option , Ubuntu is booted , but it gets stuck when the initial ' Installing ' window comes . The progress bar vanishes and it just stays there . 

So , there you go . Thats my query and i am actually hoping that someone will actually help me on this .

Having High Hopes . And waiting to experience the awesomeness of UBUNTU . :D

---

### Post by moore.bryan on 2012-08-24
Do I understand you right: you tried installing Ubuntu the "traditional" way and chose "Something Else" rather than the standard "Install Ubuntu alongside Windows" option, happened upon a kernel error, and then tried installing via Wubi--which also failed? Why didn't you just choose the install alongside Windows option?

Also, for the future, please try and make your help subject a little more descriptive than "help." ;-)

---

### Post by Kopkins on 2012-08-24
How many times have you tried this? Did you use the same installation media each time? If your liveCD was bad then it could cause issues. 

Ubuntu 12.04.1 was released today. Using the new install media could solve your issue. 

For when you do get it working, I suggest using a program called Jupiter for battery life. I'm not sure what made you think that Ubuntu has great battery efficiency. I think it is pretty much average. Jupiter is a program that lets you easily manage how much power is used. 

To install:
```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter

```

Best of luck, I highly suggest trying the new media released. The download is now by default 12.04.1 LTS [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Kopkins

---

### Post by Finnicella on 2012-08-24
Hi, I think your problem is due to the fact that you already have 4 primary partitions on your HD.
Check it out and tell us.
I have an HP and to install Ubuntu I must delete the HP Tools partition.
Bye and sorry for my english.):P

---

### Post by black veils on 2012-08-24
please do what [this little tutorial]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") says, so we have more technical information to help you.

---

