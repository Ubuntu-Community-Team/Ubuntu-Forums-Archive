---
title: "image viewer, has black band. through photos"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Chasmo on 2012-01-14
I have been using ubuntu for a couple of years and it has been so trouble free that I have forgotten some of the most basic things. How do you take a screenshot? I am having an issue with image viewer since I installed 11.10. all of my photos have a big black band through the middle of them. I know the photos are ok because I can look at them using other photo software. anyone know what is up with image viewer?

---

### Post by lechien73 on 2012-01-14
A screenshot is just the *PrtScrn* key, or *Alt+PrtScrn* if you want to just capture the active window :)

I don't know about the reason for the black band yet, but I'd be interested to see an example :)

---

### Post by Chasmo on 2012-01-14
/home/charlie/Pictures/Screenshot at 2012-01-14 14:43:54.png[IMG][/IMG]

I don't know how to get the screenshot to post here

---

### Post by lechien73 on 2012-01-14
Click **Reply**, then scroll down and choose **Manage Attachments**, you can upload the image from there as an attachment :)

---

### Post by Guilden_NL on 2012-01-14
I've had the same problem on my wife's primary laptop running 10.10 Ubuntu.  I haven't had a chance to look at it, but she's bugging me to fix it, so I guess it's time for me to upgrade her to 11.10 Lubuntu.

But will be interested in hearing if there is an easy fix!

---

### Post by Chasmo on 2012-01-15
[ATTACH]210902[/ATTACH]ok I will try this 
. I have uploaded the screen shot and see it in attach files[ATTACH]210902[/ATTACH]

---

### Post by Chasmo on 2012-01-15
I stumbled on to a fix. I was really hating the unity interface on 11.10 and saw that you could download gnome and when I did then started image viewer it worked like always.

---

### Post by Chasmo on 2012-01-15
I think that was  (sudo apt get-install gnome shell)  It gives you the option at log on of unity gnome or gnome classic. I like the classic. I don't have any idea why image viewer wont work in unity and will in gnome. does any one have an Idea?

---

### Post by Guilden_NL on 2012-01-19
Chasmo,
Thanks!  I planned to move my wife's laptop to Lubuntu soon, here's another reason to do it.  I hate Unity for many reasons!

---

### Post by Torrbrook on 2012-06-03
Since installing 12.04 (64-bit) I have black bands through images in both Image Viewer and Shotwell, whether using Unity or Gnome Classic.  They were not present with 11.10.  The bands stretch right across the image at varying heights and widths, typically 2" deep.  Grateful for any suggestions.

---

### Post by eric-yorba on 2012-06-04
My guess is these are window manager or graphics driver issues.  Have you filed bugs via Apport about this?

---

### Post by Torrbrook on 2012-06-08
Thanks, Eric-yorba.  I haven't reported it but will do so.

---

### Post by Torrbrook on 2012-06-17
I find that the nvidia driver didn't install with 12.04.  I've now installed it and the problem has gone away.

---

