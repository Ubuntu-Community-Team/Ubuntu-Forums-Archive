---
title: "Installing Kubuntu, Lubuntu, ect. on the same system?"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Zane Pepper on 2012-05-23
I have a Ubuntu and Windows dual boot system with a shared data drive set up right now and I am wondering if it would be possible to install the other Ubuntu variants on the same partition as Ubuntu side by side.

Here is how my drive is set up right now.
[IMG]http://sadpanda.us/images/976826-2T5AODP.png[/IMG]

---

### Post by MG&amp;TL on 2012-05-23
You can just install the desktop and applications. The core is the same.

Lubuntu:
```
sudo apt-get install lubuntu-desktop
```

Kubuntu:

```
sudo apt-get install kubuntu-desktop
```

Xubuntu:
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Zane Pepper on 2012-05-23
> **MG&TL said:**
> You can just install the desktop and applications. The core is the same.

Lubuntu:
```
sudo apt-get install lubuntu-desktop
```Kubuntu:

```
sudo apt-get install kubuntu-desktop
```Xubuntu:
```
sudo apt-get install xubuntu-desktop
```

And this will write over the standard Ubuntu desktop or install those along side it? It will make it so when I boot up my computer I will be able to choose them from the boot loader? Sorry for the questions, I am noob when it comes to Linux.

---

### Post by 2F4U on 2012-05-23
At the desktop login prompt you will be given an option to select the desktop environment, so you can select to start, for example, Lubuntu desktop.

---

### Post by sudodus on 2012-05-23
> **Zane Pepper said:**
> And this will write over the standard Ubuntu desktop or install those along side it? It will make it so when I boot up my computer I will be able to choose them from the boot loader? Sorry for the questions, I am noob when it comes to Linux.
I have such a system to evaluate *ubuntu 12.04.

At the log in screen you click on the Ubuntu logo symbol and get a long list with desktop environments to choose.
Every flavour has sub-flavours, more or less complete, it's like in a really good ice-cream bar ;-)

---

### Post by Zane Pepper on 2012-05-23
> **2F4U said:**
> At the desktop login prompt you will be given an  option to select the desktop environment, so you can select to start,  for example, Lubuntu desktop.

Sounds simple enough. Thanks.

> **sudodus said:**
> I have such a system to evaluate *ubuntu 12.04.

At the log in screen you click on the Ubuntu logo symbol and get a long list with desktop environments to choose.
Every flavour has sub-flavours, more or less complete, it's like in a really good ice-cream bar ;-)

That is what I plan on doing. I want to check out the other interfaces.

More like a flipping delicious ice cream bar :P

---

### Post by irv on 2012-05-23
The only problem you might run into is the k, l, and etc Ubuntu's all use different desktops and might overwrite files in your home directory on sda6. 
Looking at your gparted map of your drive I see you have a 500gig hd. This is the same as the one I have. This is just a suggestion but why don't you invest in a large external HD for all you media data and then partition your hard drive up so you can boot 4 or 5 OS'. Then setup Ubuntuone on each and keep all the files there that you want to share between OS'. Keeping all the media files seperate.
Also notice your screen shop was very large. Next time use the paper clip on the post screen to post your screenshot. Like this:  [ATTACH]218578[/ATTACH]
Just for the record, I have a 1TB external drive and as I remember I don't think I paid much over a $100 for it. It was a good investment. I use it for backups also.

---

### Post by MG&amp;TL on 2012-05-23
> **irv said:**
> The only problem you might run into is the k, l, and etc Ubuntu's all use different desktops and might overwrite files in your home directory on sda6. 


Just extending on this, the files overwritten are configuration files..personal data will not be touched. Unless I misunderstood, irv?

---

### Post by blackbird34 on 2012-05-23
Yes

---

### Post by irv on 2012-05-23
> **MG&TL said:**
> Just extending on this, the files overwritten are configuration files..personal data will not be touched. Unless I misunderstood, irv?

No you didn't misunderstand, Just the configuration files will change, not the data files. The data is safe. sorry if I was misleading.

---

### Post by Zane Pepper on 2012-05-24
What sort of configuration files will be overwritten?

@irv, I am on a laptop, so using a external HDD all the time is out of the question. Also, HDD are super expensive right now and I don't have much disposable income to spend on computer parts right now.

---

### Post by Zane Pepper on 2012-05-24
I installed the desktop interface for Kubuntu and now when I boot up my system the Kubuntu desktop is the default and I have to pick Ubuntu from the drop down box. Is there any way I can set Ubuntu back to to default?

On a releated question, is there any way I can uninstall a desktop interface if I don't want it any more?

---

### Post by sudodus on 2012-05-25
> **Zane Pepper said:**
> I installed the desktop interface for Kubuntu and now when I boot up my system the Kubuntu desktop is the default and I have to pick Ubuntu from the drop down box. Is there any way I can set Ubuntu back to to default?

On a releated question, is there any way I can uninstall a desktop interface if I don't want it any more?
The system MG&TL described in post #2 and I seconded in post #5 works like this for me:

- I started with 'vanilla' Ubuntu 12.04, and that original log in screen remains.

- When I log in, the system remembers which desktop environment I used last time, and it will be selected until I select another one.

I am surprised that it does not work like that for you. Maybe something happened at some upgrade between my installation and yours. I think that you can uninstall a desktop interface like you uninstall another program package

```
sudo apt-get install package
``` ...
```
sudo apt-get remove package
``` or
```
sudo apt-get purge package
``` to get rid of configuration files too

---

### Post by MG&amp;TL on 2012-05-25
[http://www.psychocats.net/ubuntu/pureubuntu]("http://www.psychocats.net/ubuntu/pureubuntu")

If you just want to make ubuntu the default screen, just run:

```
dpkg-reconfigure lightdm
```

and then select lightdm, from the options box that appears.

@sudodus-I think KDE's login manager is more prejudiced. ;)

---

