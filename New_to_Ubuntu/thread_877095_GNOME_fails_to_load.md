---
title: "GNOME fails to load"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by kuxpac383 on 2008-08-01
I've rarely had problems with GNOME until yesterday.  I have 8.04 and I am able to log in.  However, it doesn't bootup my desktop enviorment and just stays in a brown screen with my mouse pointer present.  I have tried to run in recovery mode but that doesn't do the trick either.  When I hit CRTL+Alt+F1 or F2 or even backspace it resets Gnome but than I get a bunch of error messages.  Any possible solutions for this? and if not, how can I reinstall GNOME? I'm on XP right now and it keeps asking me to update and restart my computer! I want my Ubuntu back! Any help would be much appreciated.

Thanks,

---

### Post by kuxpac383 on 2008-08-01
By the way, this is for Ubuntu. I don't know why it chose Kbuntu as a tag. This is for Ubuntu...NOT KBUNTU!

---

### Post by dca on 2008-08-01
Did you change anything relative to your theme?

---

### Post by kuxpac383 on 2008-08-01
I recently changed the theme, icons etc.  But, it was running fine for about a week.  This just came out of the blue.

---

### Post by Paqman on 2008-08-01
You could try removing and reinstalling ubuntu-desktop.

---

### Post by kuxpac383 on 2008-08-01
how do you do that?

---

### Post by kuxpac383 on 2008-08-01
If I have to I will reinstall GNOME.  But would I have to totally reinstall Ubuntu?

---

### Post by unutbu on 2008-08-01
kuxpac383, you may want to try moving your GNOME dot config files: [http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)
This may solve your problem, as long as you don't mind redo-ing all your GNOME configuration settings.

---

### Post by Troll_the_Great on 2008-08-01
No, you won't have to reinstall Ubuntu.
To reinstall gnome do this:
```
sudo apt-get remove gdm
```
then 
```
sudo apt-get install gdm
```
Reboot
```
sudo reboot
```
Hope that works.
Cheers!

---

### Post by kuxpac383 on 2008-08-01
When I try to reinstall GNOME I get this message, "Unable to fetch some archives maybe run apt-get update or try --fix-missing."  I try this and it doesn't work

---

### Post by kuxpac383 on 2008-08-01
Ok, right now I have no GNOME and when I try and install GNOME it won't let me.  Anyone have any ideas?

---

### Post by kuxpac383 on 2008-08-01
Looks like I may be alone on this one.

---

### Post by Paqman on 2008-08-01
> **kuxpac383 said:**
> When I try to reinstall GNOME I get this message, "Unable to fetch some archives maybe run apt-get update or try --fix-missing."  I try this and it doesn't work

So you've tried:
```

sudo apt-get update

```
and
```

sudo apt-get update --fix-missing

```

Can you post the actual error messages you get?

---

### Post by Troll_the_Great on 2008-08-01
> **kuxpac383 said:**
> Ok, right now I have no GNOME and when I try and install GNOME it won't let me.  Anyone have any ideas?

What do you mean it won't let you?Post the error that you see and we will try to help you.
Cheers!

---

### Post by kuxpac383 on 2008-08-06
Ok so it's been a few days since I've been able to tackle this problem, but I'm ready to get my Ubuntu back!  

When I typed the above commands I got the following, "Some index files failed to download, they have been ignored, or old ones used instead.  You may want to run apt-get update."

Well I've tried apt-get update and that doesn't do anything either.   All I want to do is reinstall Gnome.  Or, if I have to I will reinstall Ubuntu if it is easier to do.  Help would be much appreciated.  

Thanks,

---

### Post by kuxpac383 on 2008-08-06
I'm going to boot up and hit Alt+F1 and see what happens

---

### Post by cgkades on 2008-08-06
are you issuing the command sudo before apt-get?

---

### Post by kuxpac383 on 2008-08-06
Yes.

---

### Post by kuxpac383 on 2008-08-06
Ok, forget messing with this.  New question.  How do I safely re-install Ubuntu without losing my data? Meaning my /home?

---

### Post by kuxpac383 on 2008-08-06
Right now I am on my Live CD. Can anybody point me to the right direction on re-installing Ubuntu without destroying my /home.

---

### Post by kansasnoob on 2008-08-06
I've only been at this since about February or March so I may not have a good answer, but I'd at least like to ask some questions if you don't mind.

First, since you're thinking about backing up your /home I'd like to see a screenshot of your drive. Just go to System > Administration > Partition Editor and take a screenshot of that screen. You'll probably have to use Photo Bucket or Image Shack or something like that since you're running on the live CD.

But don't give up just yet I'll try to help. I'd also like to know if Ubuntu is the only OS on this machine and if you have more than one hard drive. (In fact, if you have more than one hard drive I'd like to see screenshots of all hard drives).

I'm thinking if you haven't been able to boot at all and you've been trying to run commands to fix your gnome desktop from the live CD nothing is actually getting done ............... but I'm a nOOb!

---

### Post by kansasnoob on 2008-08-06
Also the output of:

```
sudo fdisk -l
```

would be helpful.

That -l is a lower case L.

---

### Post by kansasnoob on 2008-08-06
It appears that I'll be gone for a while and I never know how long, so just to explain what I was looking for:

(1)Is your drive/partition out of room? things act up when that happens.

(2)If you've been using the live CD to run the commands previously mentioned you may be making no real changes so you probably need to enter the command line at boot and do something like:

```
 sudo apt-get install --reinstall ubuntu-desktop
```

I'm pretty sure that's right for Ubuntu 8.04.

But I must run for the moment.

---

