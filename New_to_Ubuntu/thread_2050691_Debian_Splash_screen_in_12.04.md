---
title: "Debian Splash screen in 12.04"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by hypnot0ad on 2012-08-31
Hello, I have been using Ubuntu 12.04 for 
the last three or four months. I have installed
it on a [Toshiba Satellite L505D-ES5025]("http://www.toshibadirect.com/td/b2c/retail-product.jsp?poid=460984").
A few days ago I had to put on 'x' operating system because 
I'm to lazy to get the programs I need to work for school in Linux.
After I have both, 'x' and Ubuntu installed I now have a Debian splash screen instead of that nice pleasant purple one right after the bios screen, where I have the options to choose which operating system I would like to boot to. The point of this post is
1.) if someone has this similar problem they can find a fix here.
2.) to find out hopefully why this happened(s).

Any info on this is much appreciated.

---

### Post by NikTh on 2012-08-31
Hello , 

probably it happened cuz you installed the X (linux) O.S. , AFTER the Ubuntu. So the X (linux) O.S. installed its grub in first disk (/dev/sda) and you don't even noticed. Now Ubuntu is the second operating system in the list. 

Don't you have a list ? Don't you have a grub menu ? Login in X O.S and open a terminal and give
```
sudo update-grub
``` 
reboot to see if you have a menu list. If not then try during PC boot to hold down the "Shift" key. 

If you manage to login to Ubuntu , then Open a Terminal and give bellow commands
```
sudo grub-install /dev/sda
sudo update-grub
```
Hopefully the Grub bootloader will be installed in /dev/sda and Ubuntu will recognize the X O.S. 
Also Ubuntu will be the first on the list.

Thanks

---

### Post by hypnot0ad on 2012-08-31
The 'x' os in my post ins't Unix/Linux based. Not sure if that makes a difference here. 
I installed 'x' first because it wouldn't give me the option to duel boot (without looking around to much that I knew of at the time.) So first I put on 'x' followed by Ubuntu 12.04. 
The first time the system restarted I still had the purple splash, but not since after that.

---

### Post by bogan on 2012-08-31
Hi!, **hypnotOad,**  

I have had this happen to me twice, the first time was with 11.10, and the Debian background eventually went away after one of the routine updates. I never did find out what caused it.

The second time was after a clean install of 12.04.1 which did not include the Gnome login option, so I installed gnome-shell, and that put the Debian screen in place of my chosen Grub Customizer Menu background.

I found a work-round for this, with a clue from Daniel Richter's & drs305's  'Grub Customizer How To' that the highest priority for selecting the Grub background was the  entry: "GRUB_BACKGROUND=<IMAGEPath>" in /etc/default/grub. I added that line following the GRUB_GFXMODE line; [ which I  de-commented and set to my choice ]. I set <IMAGEPath> to the same  as set in Grub Customizer.```
gksu gedit /etc/default/grub # and Saved, exit
sudo update-grub # and reboot
``` 

That got rid of the Debian Logo screen.

Chao!, **bogan.**

---

### Post by vasa1 on 2012-08-31
> **hypnot0ad said:**
> ...
After I have both, 'x' and ... The point of this post is
1.) if someone has this similar problem they can find a fix here.
2.) to find out hopefully why this happened(s).

Any info on this is much appreciated.

What's the idea behind writing 'x'? It certainly doesn't help people help you more easily.

---

### Post by NikTh on 2012-08-31
> **hypnot0ad said:**
> **The 'x' os in my post ins't Unix/Linux based. Not sure if that makes a difference here. **
I installed 'x' first because it wouldn't give me the option to duel boot (without looking around to much that I knew of at the time.) So first I put on 'x' followed by Ubuntu 12.04. 
The first time the system restarted I still had the purple splash, but not since after that.

Of course it makes a difference. You should mentioned that in your First Post. 

Try to boot from a Live CD of Ubuntu and follow this solution : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) **2nd option**. 

Thanks

---

### Post by Petro Dawg on 2012-08-31
I had a similar issue posted, now solved.  See my thread [here]("http://ubuntuforums.org/showthread.php?t=2043534&highlight=xfce+splash").

---

### Post by hypnot0ad on 2012-09-01
Sorry I named it x as to not create a bias for people who come here from Google etc...
I named it x because this can probably happen with multiple operating systems and Ubuntu. If people find this in the future x shouldn't matter (I would think (._.))

---

### Post by hypnot0ad on 2012-09-01
Sorry x is unsurprisingly win7.

---

### Post by critin on 2012-09-01
> **hypnot0ad said:**
> Sorry x is unsurprisingly win7.

I knew it was windows from your first post.  lol  Relax.

Why hide it?  No one is going to care.  Most of the users of ubuntu duel boot or have second computers with Windows.   Dual booting with windows and dual booting with another linux system is very different and it does make a difference when asking for support.   Supporters are doctor-like, they must know what is inside your system's box before they can prescribe a fix.   :P

---

### Post by vasa1 on 2012-09-01
In which case, it's very difficult to understand how the Debian splash appears. I got it **after** installing the xfce desktop. If you have only installed Win 7 and vanilla Ubuntu, you shouldn't have the Debian splash.

---

### Post by hypnot0ad on 2012-09-03
> **vasa1 said:**
>  If you have only installed Win 7 and vanilla Ubuntu, you shouldn't have the Debian splash.

I don't fully understand what you mean by this.

---

