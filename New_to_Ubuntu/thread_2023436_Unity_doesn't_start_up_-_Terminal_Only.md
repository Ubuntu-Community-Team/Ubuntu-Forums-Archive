---
title: "Unity doesn't start up - Terminal Only"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Houmie on 2012-07-12
Hey guys,

I just came home and can see Unity doesn't startup any longer.

I get a terminal screen

```
Ubuntu 12.04 LTS PC tty1

PC login:
```

I am posting this with my laptop. Please help, what shall I do?

Thanks,
Houman

---

### Post by Houmie on 2012-07-12
Ok I entered startx and can see it tries to start the unity and it seems to hang

last entry is:

```
saned disabled; edit /etc/default/saned
* checking battery state...   [OK]
```

---

### Post by lukeiamyourfather on 2012-07-12
Have you changed anything lately, like installed updates?

---

### Post by Houmie on 2012-07-12
> **lukeiamyourfather said:**
> Have you changed anything lately, like installed updates?


yeah i install the System updates every day. I did this morning and it was fine. Until I shutdown to go to a meeting.

Now coming back, it has problems.  I use the ATI proprietary drivers.  Maybe something was updated that affected it?

---

### Post by lukeiamyourfather on 2012-07-13
> **Houmie said:**
> yeah i install the System updates every day. I did this morning and it was fine. Until I shutdown to go to a meeting.

Now coming back, it has problems.  I use the ATI proprietary drivers.  Maybe something was updated that affected it?

Did you install them using the repositories or did you install them manually from the download on AMD's website? If you installed them from AMD's website that's the issue, when the kernel gets updated the kernel module doesn't so the drivers break. The drivers from the repositories take care of this for you (and are otherwise the same driver as the ones on AMD's website).

---

### Post by NikTh on 2012-07-13
Hi , 
@**lukeiamyourfather **has right [B]. 
[/B]When you be in terminal screen login with username & password and give these commands one-by-one . Hit Enter after each command. Write them down to a paper if you want 

```
sudo service lightdm stop 
sudo apt-get install dkms 
sudo update-initramfs -u -k all 
sudo apt-get install -f 
sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade
sudo reboot
```Last command will reboot you pc. See if something corrected. 
Thanks

---

### Post by Houmie on 2012-07-13
Thank you guys. I wished I had seen this yesterday.  I have already reinstalled Ubuntu :)

Something I have differently this time. I didn't just download the driver from Ati website and installed it from Script.

Instead I compiled it into a Ubuntu package and installed the packages instead. This way I hope at least the integrity of the data and dependencies are better guaranteed.

---

### Post by d4m1r on 2012-07-13
tty1 leads me to believe you hit ctrl+alt+1....Next time this happens, just try hitting ctrl+alt+7.

tty1 and tty2 (ctrl+alt+2) are recovery consoles.

---

### Post by Houmie on 2012-07-13
Thanks I keep that i mind.

---

### Post by Ubun2to on 2012-07-13
I know the issue is solved, but I have a question. Did you ever try this?:
```
unity restart
```
Or
```
unity
```

---

### Post by Houmie on 2012-07-23
> **Ubun2to said:**
> I know the issue is solved, but I have a question. Did you ever try this?:
```
unity restart
```
Or
```
unity
```

No, I didn't try this.  Just restarted PC several times. sudo reboot

---

