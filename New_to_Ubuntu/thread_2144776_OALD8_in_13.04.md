---
title: "OALD8 in 13.04"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by sokyoto on 2013-05-13
Hello guys, how are you doing? :)
I'm a newbie to Ubuntu and I've installed 13.04 version
I used to run windows 7 and now I switched to Ubuntu; but I have a problem with installation of Oxford Advanced Learner's Dictionary8
I need it in my studies. I checked some links but they are outdated. 
Can you help with a complete guide to how? 

Thank you ^_^

Note: when I try to launch it from the commands I get this error : The setup program seems to have failed on amd64/unknown

---

### Post by dino99 on 2013-05-13
install synaptic :
>  sudo apt-get install synaptic
> sudo synaptic

then search about "festlex" and install the packages you need

---

### Post by sokyoto on 2013-05-13
> **dino99 said:**
> install synaptic :



then search about "festlex" and install the packages you need

I installed all this and I still get the same error:

The setup program seems to have failed on amd64/unknown 
Fatal error, no tech support email configured in this setup

Also; I use this command to install setup.sh : Desktop/linux/setup.sh

When I tried to run it using setup.sh itself it turned to open as a txt containing a lot of commands.....

Can you please help me!!!

---

### Post by sokyoto on 2013-05-13
Any replies please!!!!!!!!!! 
I can't find a solution.

---

### Post by QIII on 2013-05-13
Hello and welcome to the forums!

We all understand that every question asked here is very important to the person asking it.

But please don't bump your threads so quickly.  You have to understand that we are a community of volunteers who come here on our own time as we have time.  The person with the very best answer may live in Tokyo or Mumbai or Berlin or Des Moines.  They may be sleeping, having a meal, playing with their children, watching a movie with their spouse or even just sitting in front of the TV with glazed eyes right now.

Please give your post 24 hours to make the journey around the world before you bump it.

Thanks, and I hope someone is able to help you soon.

---

### Post by ipeters61 on 2013-05-13
> **sokyoto said:**
> I installed all this and I still get the same error:

The setup program seems to have failed on amd64/unknown 
Fatal error, no tech support email configured in this setup

Also; I use this command to install setup.sh : Desktop/linux/setup.sh

When I tried to run it using setup.sh itself it turned to open as a txt containing a lot of commands.....

Can you please help me!!!

You should open the Terminal and navigate to the directory that way, typing in:
```
cd ~/Desktop/linux
```
Then you should type the command below, which runs the script to install the software:
```
./setup.sh
```
That should help you, but if the above command doesn't do anything, you should type (while in the linux directory) the command below, which makes the script executable...
```
chmod +x setup.sh
```

Hopefully that will help you, but I know installations with scripts can be kind of a pain.

---

### Post by sokyoto on 2013-05-14
> **QIII said:**
> Hello and welcome to the forums!

We all understand that every question asked here is very important to the person asking it.

But please don't bump your threads so quickly.  You have to understand  that we are a community of volunteers who come here on our own time as  we have time.  The person with the very best answer may live in Tokyo or  Mumbai or Berlin or Des Moines.  They may be sleeping, having a meal,  playing with their children, watching a movie with their spouse or even  just sitting in front of the TV with glazed eyes right now.

Please give your post 24 hours to make the journey around the world before you bump it.

Thanks, and I hope someone is able to help you soon.

 Thank you ^^ It is my first time at a forum, so I don't know the rules :(

> **ipeters61 said:**
> You should open the Terminal and navigate to the directory that way, typing in:
```
cd ~/Desktop/linux
```
Then you should type the command below, which runs the script to install the software:
```
./setup.sh
```
That should help you, but if the above command doesn't do anything, you  should type (while in the linux directory) the command below, which  makes the script executable...
```
chmod +x setup.sh
```

Hopefully that will help you, but I know installations with scripts can be kind of a pain.

Thank you for your response. But it doesn't work. this is a screen shot of what problem I have:

[IMG]http://i43.tinypic.com/2yypevt.png[/IMG]

I have downloded the OALD8 from torrent BTW! 

Thank you :)

---

### Post by ipeters61 on 2013-05-14
Okay, the *chmod *command isn't your issue then.  Can you upload the setup.sh for us to diagnose?

---

### Post by sokyoto on 2013-05-15
> **ipeters61 said:**
> Okay, the *chmod *command isn't your issue then.  Can you upload the setup.sh for us to diagnose?

Thank you :) 

The file is in the attachement. 

Thank you for the cooperation :D

---

### Post by sokyoto on 2013-05-17
Bump!! Please help

---

### Post by Cheesemill on 2013-05-17
Are you running the 32 or 64 bit version of Ubuntu? Also you should have received instructions when you purchased the CD, what do they say?

If you are running a 64-bit version of 13.04 then try this....
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl dpkg-dev
linux32 ./setup.sh
```

---

### Post by sokyoto on 2013-05-17
> **Cheesemill said:**
> Are you running the 32 or 64 bit version of Ubuntu? Also you should have received instructions when you purchased the CD, what do they say?

If you are running a 64-bit version of 13.04 then try this....
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl dpkg-dev
linux32 ./setup.sh
```

Thank you ^^

I'm running a 64bit of Ubuntu

And I didn't receive any instruction because I downloaded it from Torrent. It contained also a linux installation folder but I reckon it is the same as the CD! 

I'll try that method

---

### Post by CharlesA on 2013-05-17
We don't support pirated software here.

---

