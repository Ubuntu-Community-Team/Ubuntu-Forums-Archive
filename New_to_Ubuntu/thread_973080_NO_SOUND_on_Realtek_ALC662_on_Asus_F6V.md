---
title: "NO SOUND on Realtek ALC662 on Asus F6V"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Shabbir Ahmed on 2008-11-06
I am a beginner on UBUNTU.. i loaded it on my laptop Asus F6V, which has the following chip-set

Codec: Realtek ALC662 rev1

I have no sound on UBUNTU. Have been reading through a number of forums. There is not much thread that gives a solution to my problem. ALSA in ubuntu not working. i tried downloading the latest driver from Realtek website. but still no sound. I NEED HELP!! i need linux on my laptop.. and i need sound.. plz help...

---

### Post by bscbrit on 2008-11-06
Try

System->Preferences->Sound

It will allow you to select different audio subsystems and then, by clicking on the 'Test' button, see if they work.  

If none of them appear to work, check once again that your speakers are plugged in to the correct socket of the computer. (I've never never made this mistake, of course!)

---

### Post by bscbrit on 2008-11-08
Shabbir Ahmed

Did that solve your problem?

---

### Post by Cryptonome on 2008-11-08
If you need to have the audio running on the Asus F6V just need to read the alsa-manual.

BTW, if you can not read the alsa manual, you can add the following line to the file alsa-base

options snd-hda-intel model=eeepc-ep20

You can select what ever model indicated on the alsa manual, related to the ALC662.

Kind regards

---

### Post by rootk1t on 2009-01-16
Have you solved the problem?

I've got the same problem :(

---

### Post by cabralhenrique on 2009-04-12
Hey guys

I'm also using an Asus F6v and I WAS struggling with the no-sound problem for one week. I think the problem is that the sound chip isn't supported by ALSA (it's not listed here [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)). I tried all suggestions I could find online and in the end, what worked for me was to remove both ALSA and PulseAudio and install OSS (just follow the instructions here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound))

Also, to get skype to work properly I had to isntall a skype-static-oss version (available here: [http://packages.medibuntu.org/intrepid/skype-static-oss.html](http://packages.medibuntu.org/intrepid/skype-static-oss.html)) and play around with the sound properties until I had the microphone working (in Options in Volume Control, select <front> for the jack-int speaker mode and <input> for jack int-mic mode.

Hope this works for you too!

Cheers,
Henrique

---

### Post by cabralhenrique on 2009-04-13
Turns out that OSS has one major backdraw. it only allows one application using sound at the same time. otherwise, it will give an error...
I uninstalled OSS and went back to my ALSA attempts and now I have everything working as it should. But I had to install the latest versions of alsa packages (nto the same ones that show up in synaptics...).
if you want to try this, just go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and download all the packages on the right hand side. untar them and browse to the folder directory and do:
./configure
make
sudo make install 
make clean
and that's it. restart and voila: sound

h

---

### Post by shanekerr on 2009-04-28
I got an Asus F6V on Saturday, and the Realtek worked with Jaunty amd64 without any problems.

The only thing I had to do to get any hardware to work was install the proprietary ATI graphics drivers.

---

