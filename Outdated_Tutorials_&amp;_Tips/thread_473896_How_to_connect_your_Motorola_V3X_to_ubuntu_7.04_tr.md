---
title: "How to connect your Motorola V3X to ubuntu 7.04 trough USB"
date: 2007-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by octavio on 2007-06-14
First of all, i want you to forgive my english. This is my first how to, and will tell you all the steps i have had to take to connect my ubuntu 7.04 to my V3X.


First of all, we will downlad the moto4lin utility from the repositories.

```

sudo aptitude update
sudo aptitude install moto4lin

```

Once installed, we need to change the configuration file of moto4lin.

```

cd $HOME/.qt
gedit moto4linrc

```

We change the old values to this ones. The most important values are, the device, product and vendor values. Those values are for the motorola V3X. Other motorola have different values. I'm sure you may look in web for those values or you may get them inside the moto4lin using inside preferences the update list button. 

I have activated the autoconnect option too.

```

[device]
cfgACMdevice=/dev/ttyACM0
cfgATproduct=3002
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
cfgP2Kproduct=3001
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0
cfgLoadList=0


```

Now we are going to make a little script in our home directory to load the module and launch moto4lin. 

moto4lin as long as i know need root access to work, so we make a sudo launch. 

```

cd $HOME
gedit motorola

```

This will be the script:

```

sudo modprobe cdc_acm
sudo moto4lin

```

now we only need to allow execution for the script with chmod and we have our script.

```

chmod 700 motorola
./motorola

```

If all has gone right we will be able to connect our Motorola V3X by USB.

This how to, only have the steps i need to do. If anybody may complete this how to, or know any other way to make things, fell free to post. I just try to give the comunity a little of the knowledge i have taken from comunity.

PD: ahchong has told us that it is necesary to have installed g++. So if you get any problem try that.

---

### Post by Computer-Geek on 2007-06-27
Good Man!!!

---

### Post by fendora on 2007-07-23
Nice bro ... u make Motorola world with Ubuntu  :guitar:

---

### Post by ahchong on 2007-07-30
Nice bro. i not yet try it.
after i finish update i try.
u guys know the best firmware for v3x?
i just got my 2day.. hehehhe..XD!!!

---

### Post by octavio on 2007-07-30
i use the firmware it came with.

Tell me if this works for u.

---

### Post by ahchong on 2007-07-31
em.. it ok now.
seem that my latop doesnt install g++..
so i took a long way to install it. 
can u add it in ur guide?

---

### Post by octavio on 2007-07-31
Done. 

Thanks for your colaboration.

---

### Post by richard270384 on 2008-08-28
This works in 8.04 as well.

---

### Post by nardo on 2008-09-28
Hello,
I need to get the phonebook from my motorola V3, but It seems that it can't be done with moto4lin.
I know that you can send AT commands to the phone and get some data.
like 
echo at+cpbs=? > /dev/ttyACM0 
My question is, How you can read the anwser to this AT commands?

Thanks

Nardo

---

### Post by octavio on 2008-10-18
Sorry for the delay.

I haven't tried this with a phone, but i have done with gprs and gsm modules for arduino and with SAMBA 55 GPRS module with USB conectivity.

Just install gtkterm from repositories.

```

sudo aptitude update
sudo aptitude install gtkterm

```

After this open gtkterm from console, just tipping gtkterm, or in applications/accesories in the gnome panel.

Once opened gtkterm you should connect to the motorola by choosing the apropiate port. If gtkterm don't show the appropiate /dev/ttyACM0 just make a link to it and give it a name like this. (Please ensure what are you doing here before doing it on your pc)

```

ln -s /dev/ttyACM0 /dev/ttyS21

```

Now restart gtkterm if needed, and choose port ttyS21. Speed must be the apropiate, usually 115200 but don't know for sure.

Check in gtkterm local echo too, so you can see what you are tipping.

Now, whatever you write on gtkterm will be send to your mobile, so just try first with at command and you should receive an ok. If that happens, you can send whatever at command you need.

I hope this can help you.

---

