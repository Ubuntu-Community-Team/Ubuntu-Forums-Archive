---
title: "I want to burn a Lubuntu iso, but I am stuck. Please help."
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Janas on 2012-03-02
Hi guys,

I am using Ubuntu 11.10 Unity. I would like to burn an iso of Lubuntu so I can try out this lightweight distro. But I cannot figure out how to do this. I have searched Google for a long time, and nothing works. I don't understand what I am doing wrong.

Using the terminal, I enter this in the command line:

mkisofs -o lubuntu-11.10-desktop-i386.iso /dev/cdrw

The shell appears to run the command, but then all the outputs show "0" files written, "0" MB, etc. It appears to execute the command but nothing is output. 

Can someone help me understand what is wrong? I am wondering if my device path is wrong. Is there a way to verify exactly what file path your computer is using?

Thank you so much for the help, I have been trying this forever, very frustrated.

---

### Post by whatthefunk on 2012-03-02
Have you tried using the GUI?

---

### Post by mikewhatever on 2012-03-02
Try the easy howto: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Hylas de Niall on 2012-03-02
download the iso

put a blank disk into the drive

open brasero

select 'burn image' from the left hand list

navigate to your downloaded iso

choose the slowest burn speed

click 'create image'

done!

---

### Post by Janas on 2012-03-02
Hey guys,

I tried using Brasero as well. It did not work either. It spun the CD and made some noises, but the CD has nothing on it. Brasero would not let me choose my device from tje drop down menu. So I tried to force it by clicking burn with no device selected. It did not work :-(

---

### Post by audiomick on 2012-03-02
Sounds like the computer is having trouble recognising the CD (DVD? ) drive. Can it read a finished CD from that drive?

---

### Post by lowbudgetlaptops on 2012-03-02
Download lubuntu iso file from distrowatch  to  your download folder then use Brasero disk burner  add that iso file data then burn away

---

### Post by audiomick on 2012-03-02
Janas did say he had already tried Brasero and it didn't work...

---

### Post by ts3 on 2012-03-02
k3b always seems to work for me when brasero wouldn't.  It's a KDE app but it runs on common-or-garden 11.10 with unity without a hitch, can be downloaded from the Ubuntu Software Centre.

---

