---
title: "Problem with Streaming Content"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by jordan55 on 2015-11-07
Im having problems viewing certain streaming video sites. HBOGO. Certain Comcast.net channels. Netflix is fine but these others wont work at all. New to Ubuntu. Appreciate any help.

---

### Post by Bucky Ball on 2015-11-07
Welcome. :)

Try installing ubuntu-restricted-extras, if you are using Ubuntu, of course (you will find *buntu-restricted-extras for the various other flavours, for instance xubuntu-restricted-extras, etc. Please state the flavour and release number. Presuming you are using Firefox?

Also, go to Software and Updates and make sure you have the Canonical Partners repo enabled in 'Other Software' (you only need to enable the first one, not the (source code) one underneath it, unless you fancy doing some tweaking with the source code). Your machine will be updated and try again. Just to make sure your machine is completely up to date, try these commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by deadflowr on 2015-11-08
Seems like HBOGO uses flash with protected content set. (from what I can gather)
If so, then you can only get that using Firefox + a special package called hal.

hal is a deprecated package, which has been pulled from the official repositories.
But you can get it from here: [https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)

This only works with Firefox.
(Or browsers which can use the old NPAPI plugin system)

Chrome on linux does not support flash/protected content, and they have no plans to change that.
(this goes for browsers that use chrome's PPAPI plugin system)

Hope it helps.

---

### Post by jordan55 on 2015-11-09
ubuntu 15.10 just upgraded to wiley werewolf. some channels on comcast come thru like ESPN but only on Chrome. Seems like nothing worked on FIrefox

couldnt quite figure out how to download that hal special package

---

### Post by sandyd on 2015-11-09
You will need to add the PPA that was linked ([https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal/+packages](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal/+packages))

Run the following in the terminal
```

sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal 
```

The first line adds the repository, the second updates all repositories, and the third installs hal.

---

### Post by jordan55 on 2015-11-09
how do I enter source code?

where do I go on that link? Im brand new to this, need to dumb it down lol?

ok, I entered the code into the terminal and it seemed to have done something but it still wont work.

---

### Post by Bucky Ball on 2015-11-09
You don't go to the link, you just run the commands Sandy provided, one after the other hitting return after each (and inputting your password, which will be invisible, but that's normal).

```
sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal
```

---

### Post by jordan55 on 2015-11-09
how do I go about adding that file from that link, their were several to choose from and Im not sure how to get them or which one

I did that and its still not working

says ****[h=3]Uh-Oh...You need to update Flash!![/h]We have detected that your computer needs an updated version of Adobe Flash Player to properly view this video.
The minimum required version of Flash for this video is 11.8.0. Your current version is 11.2.202.
I click the link I go to update and it still doesnt work

---

### Post by Bucky Ball on 2015-11-09
Flash support for Linux stops at 11.2. That is it. You've gone as far as you can go.

Your only options are to install Chrome or Chromium (and pepperflash in the latter) or, apparently, there is a method for getting the pepperflash to work with Firefox. Never needed it so don't know, but you will find it with some digging.

---

### Post by jordan55 on 2015-11-09
ok. from what I hear flash is being phased out. I have chrome and it works better with streaming sites but very selective

does anyone know about chrome that could help me out?

---

### Post by Bucky Ball on 2015-11-09
Not unless you can give more specific information about your issue than:

> **jordan55 said:**
> I have chrome and it works better with streaming sites but very selective

:)

What sites? What errors? What's happening on the ones where it doesn't work?

---

