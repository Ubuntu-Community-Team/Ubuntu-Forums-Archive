---
title: "how to install the graphic and sound  card driver"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by ashish_envy on 2008-10-07
i m using nvidia graphic card 7300LE . i m new to ubuntu so i don't know how to install the graphic card driver and the sound card driver .
please help me 
please .....
please ..

---

### Post by ductinhbk on 2008-10-07
to install driver you type this on terminal: lshw
after that you will see your mainboard maker and search google for your driver, i think it is the easiest way for beginner.

---

### Post by kpkeerthi on 2008-10-07
> **ashish_envy said:**
> i m using nvidia graphic card 7300LE . i m new to ubuntu so i don't know how to install the graphic card driver and the sound card driver .
please help me 
please .....
please ..

From the GNOME menu, go to System -> Admin -> Hardware Drivers. Your drivers should be already listed there. Click on the check box to enable the driver.

[More Info]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Graphics_cards_and_displays")

---

### Post by sisco311 on 2008-10-07
To enable the video driver go to System > Administration > Hardware Drivers.


The sound card driver should be installed by default.

Go to Menu -> Sound&Video -> Volume Control and
make sure the sound is unmuted.

---

### Post by 3rag0n on 2008-10-07
If you want all the s00perb effects linux users are raving about, you might wish to download the latest 18.9 MB driver from nvidia's own site.
Store it in your home dir and rename to nvidia.run
now reboot and go to recovery mode.
login as root and navigate to your home dir and type *sh nvidia.run*

Follow the instructions.
Finished.

---

### Post by halitech on 2008-10-07
> **3rag0n said:**
> If you want all the s00perb effects linux users are raving about, you might wish to download the latest 18.9 MB driver from nvidia's own site.
Store it in your home dir and rename to nvidia.run
now reboot and go to recovery mode.
login as root and navigate to your home dir and type *sh nvidia.run*

Follow the instructions.
Finished.

ummmmm nope, that doesn't wok on Ubuntu as the root account is disabled. If the driver isn't listed in the hardware drivers box, they would simply open a terminal (Applications - accesories - terminal) and type```
sudo sh nvidia.run
```

---

### Post by sisco311 on 2008-10-07
> **halitech said:**
> ummmmm nope, that doesn't wok on Ubuntu as the root account is disabled. If the driver isn't listed in the hardware drivers box, they would simply open a terminal (Applications - accesories - terminal) and type```
sudo sh nvidia.run
```
In recovery Mode (single user mode) you are logged in as root.

OP: you can use Envy to install the latest driver:
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by phantomgunex on 2008-10-07
Go to System > Administration > Hardware drivers.Your sound card driver should be listed there. Thats how i installed my graphics card driver.
If thats not the prob, then maybe you might want to reset your sound card by turning off your computer, pulling off the plug, open the chassis (your computer case) take out and put in the sound card, then on your computer again hope that helps.( i did that went my network card failed and it is now working perfectly).:KS

---

### Post by halitech on 2008-10-07
never had to log in recovery mode but the poster made it sound like you actually log in like you would normally and I know that doesn't work and why do that when you can just run the command as sudo?

Envy probably would be easier then running the file though

---

