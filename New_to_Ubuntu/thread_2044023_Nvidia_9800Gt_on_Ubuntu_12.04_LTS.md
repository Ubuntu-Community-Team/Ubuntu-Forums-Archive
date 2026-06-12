---
title: "Nvidia 9800Gt on Ubuntu 12.04 LTS"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by hitndahedfred on 2012-08-17
Ok,, Here we go.

I have dabbled with Ubuntu at various times in the past but always went back to Win-doze, but now I am back for good as I am truly tired of the worsening personal experiences I have encountered with Micros products.

Before I am flamed I will say my experience with Linux is very minimal at best so I know I have quite a bit of work ahead of me. And yes,,, I have searched for an answer to my issue but the detail was way over my knowledge base at this time ,,,so thus I begin my real journey here.

My issue is this. 
New install of 12.04 LTS and I am trying to get my flat TV to show movies from my PC.  As I used to do until today. My video card is an Nvidia 9800GT. 
I installed the recommended driver and rebooted but when I went to use the application to define the video for the TV all that was in the Graphics was "DRIVER UNKNOWN" and  "STANDARD EXPERIENCE". And yes,,,, I did reboot after the install.

Could someone please steer me in the right direction so I can enjoy my movies again that I have accumulated over the years?

I am using HDMI only for the video. The audio is carried on separate cabling from the PC.

Thanks ahead guys n gals

---

### Post by cariboo on 2012-08-17
You need to use nvidia-settings, to set up dual-screen, or any other screen for that matter. Click the Dash icon in the top left corner and type:

```
nv
```

I'm running Quantal (12.10), and nvidia hasn't created a working driver yet, or I'd show you a screenshot of the program.

---

### Post by hitndahedfred on 2012-08-21
> **cariboo907 said:**
> You need to use nvidia-settings, to set up dual-screen, or any other screen for that matter. Click the Dash icon in the top left corner and type:

```
nv
```I'm running Quantal (12.10), and nvidia hasn't created a working driver yet, or I'd show you a screenshot of the program.

============================================

Thank you very much,, I am setting this PC up as a dual boot until I firmly understand what I am doing. Seems strange ,,,honestly. 

As I have been doing IT work for 15+ years.
Between my father,,myself and my son we have a combined total of over 70 years in this industry. At this point in time I am just taking it easy doing some "babysitting" on a set of IBM Z's plex with several Petas of EMC and HDS dasdi... 
I really felt "uncomfortable" asking for assistance.     ](*,)

I THANK YOU for your response.

Hit

---

### Post by Anirut on 2013-01-22
> **cariboo907 said:**
> You need to use nvidia-settings, to set up dual-screen, or any other screen for that matter. Click the Dash icon in the top left corner and type:

```
nv
```I'm running Quantal (12.10), and nvidia hasn't created a working driver yet, or I'd show you a screenshot of the program.

hi, have a question if you can answer, i would be appreciated,  im running 12.10 and graphic card is nvidia 9800 gt, every things is running great using auto driver which is Nouveau, should i try different driver? am i going to gain anythings? Thanks..

---

