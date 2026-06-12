---
title: "sound &amp; microphone problem in skype"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by bekirs on 2012-07-22
[FONT=Arial][SIZE=2]Hi,

I'm an absolute beginner and have Xubuntu 12.04 installed on my [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Arial][SIZE=2]HP 635 (A1E51EA)[/SIZE][/FONT][FONT=Arial][SIZE=2] Laptop.

Although there is no problem with the sound in several applications,  in the test call of Skype 2.2(Beta) I don't hear anything. Moreover, there's no response when I try to adjust microphone settings in "PulseAudio Volume Control" and of course it also does not work in the test call of Skype.

Do you have any idea about how to solve that problem?
[/SIZE][/FONT]

---

### Post by ub07 on 2012-07-22
I use Skype every day, and I don't have any problems. Have you checked "Sound Devices" under "Options?"

---

### Post by motorcity909 on 2012-07-22
I had a similar issue and started a thread which got me a fix that worked - see the third post here - 

[http://ubuntuforums.org/showthread.php?t=1974799](http://ubuntuforums.org/showthread.php?t=1974799)

Good luck
Dave

---

### Post by bekirs on 2012-07-22
> **ub07 said:**
> I use Skype every day, and I don't have any problems. Have you checked "Sound Devices" under "Options?"

Under "Sound Devices > Options" Default device (default) is selected for both Microphone and Speakers. Any suggestion for what should it be selected?

---

### Post by bekirs on 2012-07-22
> **motorcity909 said:**
> I had a similar issue and started a thread which got me a fix that worked - see the third post here - 

[http://ubuntuforums.org/showthread.php?t=1974799](http://ubuntuforums.org/showthread.php?t=1974799)

Good luck
Dave

In the third post of your link, it is recommended to select USB camera from the list. Such an option is not available in my drop-down list since both my camera and mic are built-in...

---

### Post by cmcanulty on 2012-07-22
I had to make sure the sound options were correct in gnome and skype options, then it worked fine

---

### Post by NikTh on 2012-07-22
Hi , 
try to download and install [Skype 4.0 for Linux](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/) . 

Its a new version (its not in Ubuntu Repositories yet) , and say how several bugs (sound included) have been corrected.

Thanks

---

### Post by bekirs on 2012-07-23
> **NikTh said:**
> Hi , 
try to download and install [Skype 4.0 for Linux]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/") . 

Its a new version (its not in Ubuntu Repositories yet) , and say how several bugs (sound included) have been corrected.

Thanks

I've downloaded it (compatible with Ubunutu 10.04 64-bit) but it is failed at the installation stage.

---

### Post by NikTh on 2012-07-23
Hi , 
try to remove the old one first.. 
```
sudo apt-get purge skype skype-bin
``` 
Then try again to install .. 
And if errors occur , post them here.

Thanks

---

### Post by bekirs on 2012-07-23
> **NikTh said:**
> Hi , 
try to remove the old one first.. 
```
sudo apt-get purge skype skype-bin
```Then try again to install .. 
And if errors occur , post them here.

Thanks

the removal of the older version was not successful:

```
sudo apt-get purge skype skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype-bin
```

---

### Post by NikTh on 2012-07-23
Hi , 
then only skype package is installed.. 
```
sudo apt-get purge skype
```

---

### Post by bekirs on 2012-07-23
> **NikTh said:**
> Hi , 
then only skype package is installed.. 
```
sudo apt-get purge skype
```

After the installation of **Skype 4.0.0.8**, the sound and microphone problem in Skype has been solved.

Thanks...

However I still do not understand why the microphone settings do not respond to the adjustments I perform in **PulseAudio Volume Control.**

---

### Post by NikTh on 2012-07-23
> **bekirs said:**
> After the installation of **Skype 4.0.0.8**, the sound and microphone problem in Skype has been solved.

Thanks...

However I still do not understand why the microphone settings do not respond to the adjustments I perform in **PulseAudio Volume Control.**

Hi , 

Glad it worked. 

Maybe it was skype's problem (bug). 

So its nothing to do with your settings. Maybe your settings was correct , but skype cannot adjust them .

---

