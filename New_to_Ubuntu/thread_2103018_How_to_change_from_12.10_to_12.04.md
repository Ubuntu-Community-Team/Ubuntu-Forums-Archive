---
title: "How to change from 12.10 to 12.04 ?"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by Kanahau on 2013-01-08
Hi,
    i am ABSOLUTELY new to this. I installed 12.10 with WUBI on my DELL inspiron mini 10 (running XP home edition). Its great, but a but clunky especially calling up the dash, i read somewhere 12.04 works a bit smoother on this netbook. How do i change it and when i do will i have the option of increasing the partition or getting rid of windows completely? (was it a real installation with wubi?) i would like to install it properly? this time but my netbook has no dvd???? or is it just as good using wubi?

A thousand thanks for your help on my road to recovery from windows...........

---

### Post by Wim Sturkenboom on 2013-01-08
The best way to chance is by doing a clean install; there is no easy way to 'downgrade'.

If you want to get rid of Windows, don't use the wubi installer but do a normal install.

You can use a USB memory stick and 'burn' the downloaded ISO on there; instructions can e.g. be found on the Ubuntu download page.  Next boot from it (you might have to change the boot order in the BIOS to boot from USB first).

During the partitioning phase, select manual partitioning, delete all partitions and create new ones. One for swap (size of RAM), one for the root partition (about 25GB) and the rest for /home. If your HD is small (50GB or less), I would only make a swap partition and a root partition.

I don't know if 12.04 is much lighter on resources than 12.10; if you want something lighter, use Lubuntu, Xubuntu or another lightweight distro.

---

### Post by dolphin194 on 2013-01-09
Your Dell Inspiron Mini 10 will run Ubuntu 12.04 quite nicely. I have not tried Ubuntu 12.10 on my Inspiron Mini 10v (which is running Xubuntu 12.04 at the moment), but when I had Ubuntu 12.04 installed it ran fine.

Like the other poster said, there is no easy way to "downgrade" Ubuntu (as you can see on [this page]("https://help.ubuntu.com/community/DowngradeHowto")). Your best bet is to re-install Ubuntu.

Also, you are running a Wubi install from what you posted. When you install Ubuntu with the Wubi installer, your computer can lack the performance of a fresh install.

Back up your data, then grab a USB stick and follow the steps here to install Ubuntu (It also works for Ubuntu 12.04):
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

---

### Post by snowpine on 2013-01-09
Welcome to the forums!

Dell actually made 3 different computers with the name "Inspiron Mini 10." If we figure out which one you have, then maybe we can help with your sluggishness issue. 

1. Open a terminal (Ctrl+Alt+T or tap Super/Windows key and type "terminal")
2. Copy & paste the following command:

```
lspci | grep VGA
```

3. Copy & paste the output into your reply here.

Based on the answer, I will try to give you good advice. Please don't be hasty and wipe your 12.10 install to reinstall 12.04 until you have explored all your options. :)

---

### Post by tlhIngan on 2013-01-09
> **Wim Sturkenboom said:**
> The best way to chance is by doing a clean install; there is no easy way to 'downgrade'.


> **snowpine said:**
> Welcome to the forums!
Dell actually made 3 different computers with the name "Inspiron Mini 10." If we figure out which one you have, then maybe we can help with your sluggishness issue. 


Both of these are very good recommendations.
If your computer is sluggish, you should perhaps try the lighter versions of Ubuntu, like Lubuntu (that's what I'm running on my 9-year-old and 7-year-old PCs), or Xubuntu.
They are essentially the same as the official releases of Ubuntu, but they are packaged with a lighter interface. Often, that's where the sluggishness comes from.

---

### Post by Kanahau on 2013-01-09
Hi Snowpine, 
                         Thanks for your answer, I am happy to wait and see your further advice, i would rather do this right once than mess things up, do you think i should completely remove windows? i have already backed up all my work and deleted as much as i know how from my windows er...bit. 
so this is what i got from the terminal 

steve@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
steve@ubuntu:~$ 

i hope it means something to you cause its left me scratching my head..........

i await eagerly your reply

---

### Post by Kanahau on 2013-01-09
my thanks to Wim Sturkenboom,  dolphin194 and tlhIngan too, this is the first time i have used a forum for anything, thank you for making me feel noticed and of course your advice

---

### Post by blackbird34 on 2013-01-09
The command ```
lspci | grep VGA
``` was to see what graphics card you had to see if it's the problem.
I can't really tell you anything about that, but I can already say that
1) If you're new, switching to 12.04 is a good idea because it will be more than 4 years before support runs out (upgrades are free but still, it's less hassle to sit on the same OS for a while)
2) I'd advise you to keep Windows, you never know if you'll need it, but you should get used to Ubuntu quick, so you can reduce the Windows XP partition to be quite small (but still make sure there's room for XP and whatever files you have). 
3) Detailed installation instructions [if you are using a live CD]("http://www.psychocats.net/ubuntu/installing") or [if you are installing from a USB stick]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick"). Both are very easy and straightforward, and (I findà much simpler than when i had to reinstall Windows.

EDIT: You may find the links in my signature useful :)

---

### Post by snowpine on 2013-01-09
> **Kanahau said:**
> Hi Snowpine, 
                         Thanks for your answer, I am happy to wait and see your further advice, i would rather do this right once than mess things up, do you think i should completely remove windows? i have already backed up all my work and deleted as much as i know how from my windows er...bit. 
so this is what i got from the terminal 

steve@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
steve@ubuntu:~$ 

i hope it means something to you cause its left me scratching my head..........

i await eagerly your reply

Hi, you are in luck, because Intel 945GSE is well-supported by Linux. But, paired with the Atom processor, it is simply rather weak hardware to get the best performance with a full-featured "bells and whistles" distribution like Ubuntu.

For a performance boost, you might consider installing the lightweight Xfce or LXDE desktop environment. Here is a page with screenshots of Xfce (Xubuntu) and easy instructions to install it:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

Installing LXDE is a similar concept.

---

### Post by Kanahau on 2013-01-09
Actually, like a kid on Christmas day i went ahead and installed ubuntu 12.04.1, removed windows completely (although maybe i should have taken blackbird34's advice there..........). Everything seems fine. I am no gamer and only really work on the computer (docs,emails and work on my website). Of course i watch a few films too but i don't think i use he machine hard. 
Thanks to you all for your help.

 i do have one more small question i want to install Barry but... the instructions say :-

To install the latest version of Barry onto Debian Squeeze, add the following line to your /etc/apt/sources.list file:  
deb [http://download.barry.netdirect.ca/barry-latest/](http://download.barry.netdirect.ca/barry-latest/) squeeze main

What is my "/etc/apt/sources.list file:" ? 

also a little further down it says:-

Finally, you will need to update your apt keyring with the following key:  
        82DE DE11 74C1 0EA7 C55D  5679 3B52 35AE B6C2 250E

 One way to fetch this key is by using gpg: 



        gpg --keyserver pgp.mit.edu --recv-key B6C2250E 
        gpg --armor --export B6C2250E > barry.key         
apt-key add barry.key 

is that last bit in the terminal?

---

### Post by sandyd on 2013-01-09
> **Kanahau said:**
> Actually, like a kid on Christmas day i went ahead and installed ubuntu 12.04.1, removed windows completely (although maybe i should have taken blackbird34's advice there..........). Everything seems fine. I am no gamer and only really work on the computer (docs,emails and work on my website). Of course i watch a few films too but i don't think i use he machine hard. 
Thanks to you all for your help.

 i do have one more small question i want to install Barry but... the instructions say :-

To install the latest version of Barry onto Debian Squeeze, add the following line to your /etc/apt/sources.list file:  
deb [http://download.barry.netdirect.ca/barry-latest/](http://download.barry.netdirect.ca/barry-latest/) squeeze main

What is my "/etc/apt/sources.list file:" ? 

also a little further down it says:-

Finally, you will need to update your apt keyring with the following key:  
        82DE DE11 74C1 0EA7 C55D  5679 3B52 35AE B6C2 250E

 One way to fetch this key is by using gpg: 



        gpg --keyserver pgp.mit.edu --recv-key B6C2250E 
        gpg --armor --export B6C2250E > barry.key         
apt-key add barry.key is that last bit in the terminal?
No need.
Just run the below, and barry will be installed
```

sudo apt-get install barry-util barrybackup-gui
```

It is always best to install programs from the repository if they already exist there. Though Ubuntu is based on Debian unstable, I have seen odd, and sometimes very difficult to reverse issues for people who combine debian and ubuntu packages.

---

### Post by Kanahau on 2013-01-09
Thanks, 

ran the code and got this response

[sudo] password for iam: 

but it wont let me type in my password or copy and paste it there ??

---

### Post by snowpine on 2013-01-09
I agree with sandyd's advice above. Here is a tutorial that explains a bit more about installing software in Ubuntu, and why we do not generally install apps the "Windows way" of surfing the web and downloading untrusted installers from random websites. Rather, the Ubuntu Software Center is kind of like the Apple App Store, where you can easily install thousands of trusted & tested applications with a few mouse clicks.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you really, really want to follow the instructions on the Barry website (which I do not recommend at this stage in your Linux learning) you have made a big mistake already, which is that you are not running Debian Squeeze. As the instructions say, you **must** use the correct repos for your release, which would be in your case:

```
deb http://download.barry.netdirect.ca/barry-latest/ ubuntu1204 main
```

If you must edit the important system file /etc/apt/sources.list then be very careful!

```
gksu gedit /etc/apt/sources.list
```

To reiterate, this is an important system file that the user should not typically need to edit on a regular basis (if at all). How to recover from typos/errors/mistakes in this file is one of the most frequently-asked questions I see on these forums. Be safe and use the Software Center! :)

---

### Post by deadflowr on 2013-01-09
> **Kanahau said:**
> Thanks, 

ran the code and got this response

[sudo] password for iam: 

but it wont let me type in my password or copy and paste it there ??

The password will be invisible. Type it out at the prompt as you best remember it and hit enter.

---

### Post by Kanahau on 2013-01-09
snowpine: I will take your advice and not mess with dodgy stuff.

 However i cant find barry in the Software center?

i read your link to psychocats ....

 i downloaded - barry-util_0.18.3-1_i386.deb - 
but when i try to install it i get told "Dependency is not satisfiable: libbarry18" 

i just want to tether my blackberry !

any other suggestions?

and why cant i type my password into the terminal?

---

### Post by Kanahau on 2013-01-09
ah ha, you guys are great
secret invisible passwords - never would have guessed
awesome 
thanks deadflowr

---

### Post by snowpine on 2013-01-09
> **Kanahau said:**
> snowpine: I will take your advice and not mess with dodgy stuff.

 However i cant find barry in the Software center?

i read your link to psychocats ....

 i downloaded - barry-util_0.18.3-1_i386.deb - 
but when i try to install it i get told "Dependency is not satisfiable: libbarry18" 

i just want to tether my blackberry !

any other suggestions?

I do not recommend to download anything from Barry website (the Windows Way), but rather to follow sandyd's instructions (post #11) exactly, or install the packages **barry-util** and **barrybackup-gui** with the Software Center (the Ubuntu Way).

---

### Post by Kanahau on 2013-01-10
I did as sandyd suggested using the invisible password technique of deadflowrs and it seems to have worked a treat, lovely thanks for all your advice and help ........... i may be posting more tomorrow but i can sleep well tonight :-)

---

