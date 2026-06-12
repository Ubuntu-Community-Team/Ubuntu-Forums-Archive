---
title: "Sound Profile"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-06-28
I have Ubuntu 12.04 and Ubuntu 13.04 installed on two different partitions of the same computer.
When I open the sound settings i find the Hardware tab missing in 13.04 and there is just one profile in there. Kindly check the attached pics.
How can i add more profiles and the hardware tab in 13.04 ?[ATTACH=CONFIG]244236[/ATTACH][ATTACH=CONFIG]244237[/ATTACH]
It helps me controlling the sound recording and output etc.

---

### Post by 3dmatrix on 2013-06-29
Any advise from any one ?

---

### Post by 3dmatrix on 2013-06-29
I need help. Can any one give any advise !

---

### Post by mc4man on 2013-06-30
Things change - 
You may find what you want in pavucontrol
```
sudo apt-get install pavucontrol
```

Then open pavucontrol & look under "Configuration" tab

---

### Post by 3dmatrix on 2013-06-30
> **mc4man said:**
> Things change - 
You may find what you want in pavucontrol
```
sudo apt-get install pavucontrol
```

Then open pavucontrol & look under "Configuration" tab

Thanx for your reply. I would like to inform you that in my Ubuntu 12.04 pavucontrol is not installed but i am still geting all those options but not in 13.04. So what is missing in 13.04 and how can i find out ?

---

### Post by mc4man on 2013-06-30
> **3dmatrix said:**
> Thanx for your reply. I would like to inform you that in my Ubuntu 12.04 pavucontrol is not installed but i am still geting all those options but not in 13.04. So what is missing in 13.04 and how can i find out ?

As I said - things change
If you tried pavucontrol & it doesn't provide what you want then you could look into the sound settings panel provided in a gnome session vs. the one in a unity/ubuntu session, myself can't be bothered as pavucontrol provides all  I need & more
(have switched "Sound Settings" in the sound indicator to use pavucontrol here instead of unity/ubuntu's panel

---

### Post by 3dmatrix on 2013-07-01
Yes it does solve the problem.
But for screen video capture, if i use record my desktop then it works well but i am still not able to figure out why it is not working with command line. where as it works well with Ubuntu 12.04
I use the command :
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 700x500 -i :0.0+170,150 ~/output.m4v
It records the video but captures sound from inbuilt mic not from the sound card.

---

### Post by Frogs Hair on 2013-07-01
This is from the ffmpeg package description is synaptic 13.04, but I don't know if it is a factor in your case         

This package contains the deprecated ffmpeg program. This package also serves
as a transitional package to libav-tools. Users are advised to use avconv from
the libav-tools package instead of ffmpeg.

You might get one when installing the other, but I can't verify that without installing the packages. See this thread. [http://ubuntuforums.org/showthread.php?t=2148736](http://ubuntuforums.org/showthread.php?t=2148736)

---

### Post by mc4man on 2013-07-01
> **3dmatrix said:**
> Yes it does solve the problem.
But for screen video capture, if i use record my desktop then it works well but i am still not able to figure out why it is not working with command line. where as it works well with Ubuntu 12.04
I use the command :
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 700x500 -i :0.0+170,150 ~/output.m4v
It records the video but captures sound from inbuilt mic not from the sound card.
 
Take a look here, you need to do a one time setup so that it uses the 'monitor of...' when using ffmpeg for screen caps with sound
(one of the reasons I switched the sound indicator to use pavucontrol by default in Ubuntu
[http://ubuntuforums.org/showthread.php?t=2156877&p=12703878&viewfull=1#post12703878](http://ubuntuforums.org/showthread.php?t=2156877&p=12703878&viewfull=1#post12703878)

---

### Post by Bryan_Fischer on 2013-09-06
I would also like to know if there is a way of making the hardware tab appear, because so far everything that I've tried has failed.  Every piece of info I come across as far as making the echo from my mic vanish depends on that tab already being present from what I can tell.  Oh by the way pavucontrol has had no success for me.  I would really like to avoid whipping out my killdisk cd and preparing an hdd for a full reinstall of win7 to fix the problem. 

I have sound working.  I can shake the floor upstairs if I turn up the volume high enough and in the other tabs that display my sound card it shows up just fine, but that hardware tab is about as present as an electric car in the Black Forest.  I'm hoping there is some way to target that tab specifically and make it show up.

---

