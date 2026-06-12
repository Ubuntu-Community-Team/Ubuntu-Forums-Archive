---
title: "Switch to power-saving graphics card"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by yopabuntu on 2013-03-10
I am an absolute newbie to Ubuntu but I managed to instal it :)
I have a HP DV7-6080eb pavilion laptop with 6 GB Ram, Core i7 processor and two video cards, and there it's going wrong. I've got a ATI Radeon Videocard which is a performance card, and an Intel Mobile Graphics video card, which is power-saving. I've been searching Google to find any solutions to switch between the cards because when using Ubuntu my fan keeps spinning crazy and my CPU temp is about 75 °c all the time... 

I've found this:
[http://techhamlet.com/2012/05/ubuntu-how-to-fix-over-heating-of-laptops-with-switchable-graphics/](http://techhamlet.com/2012/05/ubuntu-how-to-fix-over-heating-of-laptops-with-switchable-graphics/)
and tried to apply the settings but I don't know how to save the rc.local file in the terminal. It says that ^0 is for saving but where should I put ^0? 

Can anyone help me with this issue or just tell me how to save the rc.local file?

Thanks!

---

### Post by RoosterHam on 2013-03-10
^ is the control symbol. what they mean is to hold the control key down and hit the letter 'o.' then control+x will exit.

you will see along the bottom, nano will ask you after hitting control+o what name you want to save the file to. if you modified an existing file you could press enter.

I recommend saving a backup of any files your modify first. If you are using the terminal, type:

:~$ cp /file/you/are/modifying /file/you/are/modifying.backup

then make your changes to the original file, hit control+o, hit control+x, reboot.

Please note that if the changes break the system, even to the point of not booting, you can recover this with your install media. Selecting 'fix broken system' and restoring the file you saved as .backup 

It helps if you have a second system you can use to google the fix if your change stops your system from booting.

---

