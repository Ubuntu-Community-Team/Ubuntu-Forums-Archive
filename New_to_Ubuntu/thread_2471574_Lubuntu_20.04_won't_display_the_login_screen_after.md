---
title: "Lubuntu 20.04 won't display the login screen after upgrading"
date: 2022-02-03
forum: New to Ubuntu
---

### Post by marian-io12 on 2022-02-03
Hello, 

I am new to this forum so please be patient with me. 

Short story: i have a machine for remote access running Lubuntu 18.04 for almost a year. It is a headless unit that has teamviewer on it. In order to be able to connect i used "xrandr" in a script, setting a virtual display. 
All worked fine until yesterday when i hit the partial upgrade button. The unit restarted and i got black screen before login screen. The OS is now Lubuntu 20.04 but i have no login screen. 

All similar issues found advised me to use the dummy xorg display driver ([COLOR=var(--black-800)][FONT=var(--ff-mono)]xserver-xorg-video-dummy[/FONT][/COLOR]). This did not help. The unit will not boot into login screen at all. 
My script is now advising me that "Can't open display". 

Teamviewer is starting and allows me to connect to a black 640x480 screen. I can use Ctrl+Alt+F1 to get the tty1 on screen. 

After further reseach, i found the following command: "killall Xorg"
Running this command brings me the login screen and then i can login and do my stuff without any issues. But rebooting the computer, i get the same black screen. Before this "partial upgrade" all went fine and i had no need to "killall Xorg".
 I am using lightdm. 

Can you, please, guide me to fix this? 
I am a beginner and i want to understand why this is now broken. Also, i need to understand why does this "killall Xorg" command really does and how to script it in order to be executed automatically (if this is best practice, of course). 

Please feel free to ask any other information you may need. 

Thank you!
Best regards, 
Marian

---

### Post by grahammechanical on 2022-02-03
I do not understand why your received an offer to do a partial upgrade. I have only ever received that offer when I have been running the development version. The latest version of Ubuntu/flavours of Ubuntu is transitioned into the next stable release over a 26 week period. When running the development version and we update/upgrade there will be package conflicts. If we use Software Updater (Ubuntu name) then we always get the offer of a partial upgrade and we should always refuse the offer. Partial upgrade resolves package conflicts by removing packages which can and does often break the OS.

I am guessing that you first decided to do an online upgrade of Lubuntu 18.04 to Lubuntu 20.04 and then received the offer for a partial upgrade. Lubuntu 18.04 reached end of its support life 30 April 2021. Please read this post by the Lubuntu developers as to why they do not recommend an online upgrade from Lubuntu 18.04 to Lubuntu 20.04. They do in fact recommend a fresh install of Lubuntu 20.04. Which maybe your simplest solution.

[https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

Regards

---

### Post by marian-io12 on 2022-02-04
Hello, 

Thank you for replying on this. I had not idea of that "partial" upgrade. The systems always asked about full upgrade. In this case, i won't spend any time to fix it. I'll just install it from scratch. 

Best regards, 
M.

---

