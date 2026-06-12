---
title: "webcam and skype"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by graham shand on 2012-09-29
i have a webcam on my laptop with the cheese webcam booth and all is ok but the webcam will not work when i am on skype i can recieve video but no one can see me they can here me ok but no pictures.im pretty sure that everything is set up ok in the options/video devices , can anyone help pls
Graham

---

### Post by HermanAB on 2012-09-29
Are you running 64 bit Linux?  Skype is a 32 bit program, so you may need too install some libraries to make it work properly.

---

### Post by NikTh on 2012-09-29
Are you sure that you clicked the "Start my Video" option ? :)

---

### Post by graham shand on 2012-10-01
thanks for your help, i have been through the process several times and nothing changes ,still no picture and i have no idea if i downloaded 64 bit 0r 32bit i just followed the instruction via ubuntu,
cheers 
graham

---

### Post by shreepads on 2012-10-01
You will need to mention exactly which OS version and Skype version you're using...

---

### Post by NikTh on 2012-10-01
Skype for Linux has one version . 32bit. Thats it . End. 

If you have 64 bit OS and downloaded skype from site , then you must install 32bit libraries to install properly the skype.

You said that skype is installed but not work properly. So I assume you installed correctly , otherwise would not even open. 

I ask again , there is a camera icon , is this OK ? Enabled ? 

If yes and you still have no picture , you can try 1-2 commands and see if work. 

It depends from OS architecture . You can find OS architercture with these 2 commands 

```
lscpu | grep Arch
``````
uname -a
```X86_X64 = 64bit 
I686= 32 bit

For 64bit architecture 
```
sudo apt-get install ia32-libs
sudo apt-get install ubuntu-restricted-extras
```For 32bit architecture 
```
sudo apt-get install ubuntu-restricted-extras
```Then try this command 
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by Bryan55 on 2012-10-04
Hi
I'm a friend of Graham's and have been helping him to fix this problem. Which we have with you help. 

First I will clear up a couple of points. Then explain how we did it

He is on a 32bit system and the camera has definitely been turned on.

He hadn't installed ubuntu extras but now has.

We found that this code stated the webcam.
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

To get it to work every time we created text file by entering this into a terminal.
```
sudo gedit /usr/local/bin/skype
```
We entered this text then saved and closed

#!/bin/bash
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype

To make it executable we entered this into the terminal.
```
sudo chmod a+x /usr/local/bin/skype
``` 

Thanks
I will get Graham to make this as solved.

---

### Post by NikTh on 2012-10-04
Ok , glad you solved it. 

If he wants to make it more..... "beautiful" he can create a Launcher . 

How ? 

```
sudo apt-get install --no-install-recommends gnome-panel
``````
gnome-desktop-item-edit ~/.local/share/applications/ --create-new
```and at the opened window he can put

```
command:LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
Name : Skype 
Comment : anything he wants
```And he can set even an Icon by  clicking upon this square-susspension style  icon. 
Then he can find the launcher in applications.
Thanks

---

### Post by mjhouska on 2012-10-06
my webcam works in guvcview, cheese, and google chat. but not skype and kdenlive(just gives white screen when i hit record) but i bought it mainly for skype and videochatting.

I am running ubuntustudio 12.04 64 bit and skype 4.0.0.8 which i just downloaded from the software center. any ideas?

---

### Post by slumbergod on 2012-10-07
I was using an old static version of skype until today. Webcam worked perfectly in it and I preferred the older interface.

Today the webcam stopped working. Since nothing has changed at my end and it was working yesterday I can only conclude that it is something at the Skype server end. 

I purged the old skype and installed the new one and cam still fails to work now. It is weird because when I look in Skype's video settings my cam is listed there and even previews video correctly. The video button to send video is just dead. 

I even tried their 39mb static version of their latest build and that doesn't allow me to send my cam either.

I have to admit, I was always concerned when Microsoft bought Skype and I was pleasantly surprised that it continued working for as long as it did. The preload method doesn't work for me and I am not sure I can be bothered fighting very hard to make Skype work. I'll stick to google chat (even though Hangouts is an abortion of a video plugin). 

If anyone has found a simple solution to the Skype disaster other than the preload method I am all ears otherwise it is finally time to purge Skype forever.

---

