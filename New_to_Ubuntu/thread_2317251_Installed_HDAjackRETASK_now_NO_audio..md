---
title: "Installed HDAjackRETASK now NO audio."
date: 2016-03-14
forum: New to Ubuntu
---

### Post by Jeffree_Homicyde on 2016-03-14
Hi all. Semi new to Ubuntu. been using very lightly since 11.04. 

I recently got sick of windows 10 on my HP Envy 15 and went back over to Ubuntu 14.04. Everything ran fine except I noticed it wasnt using ALL the Beats speakers. I found a thread that explained how to get it working, and I followed it to the letter. Now I have no audio whatsoever. 

I originally had a lot of issues installing hda-jack-retask but finally got it installed, just not 100% sure it was installed correctly. After I got into hda-jack-retask and did everything the tutorial told me I clicked apply and got 2 errors.

1. tee: /sys/class/sound/hwC0D0/reconfig: Device or resource busy

2. tee: /sys/class/sound/hwC1D0/reconfig: No such device

Here is a link to the tutorial 

[https://incognitech.wordpress.com/2013/10/27/beats-audio-hp-envy-15-on-ubuntu/](https://incognitech.wordpress.com/2013/10/27/beats-audio-hp-envy-15-on-ubuntu/)

I am at a total loss. Everything else runs amazing. I just want AUDIO BACK!!! 

Thanks so much in advance!

---

### Post by Jeffree_Homicyde on 2016-03-16
Nothing?? Really??

---

### Post by Geoffrey_Arndt on 2016-03-17
Have you tried to contact the Udit on his new blog?   His original instructions were for versions of Ubuntu prior to 14.04 . . . Seems not tested on current releases.

As a prelim-1st step, you might try installing QasMixer (a gui for Alsamixer) and see if that can help.

Also, if you install "inxi" and run via terminal "inxi -A", and reporting back output (via code tags . . .  after clicking on _"reply" - - click on the # character_ in reply menu to get the tag format . . post your output between the start and end tags).

"```
 your output here 
```"

---

