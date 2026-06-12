---
title: "ATi Video Issue - Locked out"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by vineline on 2008-04-28
I installed Ububtu 7.1 without a problem and it worked worked well. It seemed a bit slow.  I saw that the video card was not being accelerated and did not have the ATi driver. I was able to find the ubuntu ATi driver.I downloaded and installed what turned out to be the wrong driver. I have a ATi Radeon 9550 and I think I installed the Radeon 8500. The problem is the computer boots OK but the display is totally distorted (broken horizontal lines). Is there a way to boot in a mode to reverse what I did. I pressed esc during boot and several options became available one of which brought me to a command line. I have no Linux experience so I had no idea what to enter.  The other option brought me to a big X in the screen. Again I have no idea if this is a good thing. Any help for a newbe would be appreciated. Please go easy on the command line strings.
Thanx in Andvance

---

### Post by Jammin80503 on 2008-04-28
if you can get to your normal interface, instal envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) and configure your card with that.

---

### Post by vineline on 2008-04-28
Problem is I can not get to a normal interface. I can get to the command line if I press "esc" at boot and select "Ubuntu 7.10, Kernal 2.6.22 - 14 Generic (Recovery mode)".  The other option is "Ubuntu 7.10, Kernal 2.6.22 - 14 Generic" which gets ne to the broken up lines ( out of sync monitor) I am using a Samsung Sync Master monitor.

---

### Post by Tatty on 2008-04-28
```
sudo dpkg-reconfigure xserver-xorg
```

make sure you select the "ati" driver, not the fglrx.  Then when you are back in a gui search synaptic for "fglrx" and remove the packages with "fglrx" in the name.

---

### Post by vineline on 2008-04-28
Attempted the above command. It walked me through a number of questions.  When I got to the color depth (this happened several times at the same place) the gui changed back to the command line, "Fatal error Inserting Battery" (???) I tried to boot to the GUI. There was no distortion but after a few seconds a tag of "Greeter application Appears to be Crashing" appeared when I press OK this repeated 6 times then told me to try again in 2 min. Tried this at least 4 times same result.

---

### Post by vineline on 2008-04-29
Thank you for your help.  The sudo command finally worked after a number of trys.  I'm not even sure what finally tipped it.

After it worked and I could use the GUI I searched synaptic per your suggestion and for "fglrx" it would not allow me to remove the packages - "remove" was grayed out and said it was not installed.

Thanx again!!!

---

