---
title: "Can't Boot to LiveCD"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by brian_hayward on 2008-09-30
I am extremely new to linux, and i downloaded the LiveCD (Ubuntu 8.04.1) from the internet ([https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)), and burned the image to a CD.  I insert the cd into my computer and it boots to the initial screen with the different options (run ubuntu from cd, install ubuntu, etc.) I select the run ubuntu without any changes to my computer, i hear the cd rom fire up but nothing else happens, and then the computer freezes, i can't even use the keyboard to scroll through the menu options.  I did a little searching on the internet and found a post on how to burn the iso image to a cd ([https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)).  After reading through the text i found a couple of links that lead me to information on what to do when ubuntu doesn't boot from the cd.  On this particular link ([https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)) it explains to change the boot parameters.  It explained to delete the "quiet splash--" at the end of the boot options line.  i did that and it still didn't work.  The webpage went on to explain that there are other options that could be used, but it doesn't explain if i need to type tack them onto the back of the boot options line manually or do i just select one of the options after i hit F6 which puts an "x" next to one of the options.  Also, do i need to delete the "quiet splash--" text when using the alternate options or do i need to keep it.  Also under the Common Problems Booting from a CD ([https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)) link from the previous website, it shows a screenshot of a CD which had the ISO image burned to it and it shows files that aren't on my CD.  Could this be the problem?  Please see the attachments to compare the screen shots i am referring to.  Any suggestions or tips are greatly appreciated.  Thanks.

---

### Post by sancho panza on 2008-09-30
To make sure that the iso image was downloaded correctly, use the MD5SUM number of the downloaded file and compare it with that given on the ubuntu download page. [Details here]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by uberdonkey5 on 2008-09-30
try to download with a fast connection (I have many problems with bad images) or use a disk of a friend for whom you know the disk works. Is it a very old computer? sometimes this can be a cause, though maybe not unsurmountable.

---

### Post by snowpine on 2008-09-30
If you get the initial screen with the different options (run ubuntu from cd, install ubuntu, etc.) then you are on the right track. Please check your md5sum using Sancho Panza's directions and also make sure your system meets the hardware requirements (384mb of ram minimum is the most important thing). It's also possible you have a video card issue, but unfortunately I'm not an expert on that, so I will defer to others' experience there.

If you delete the 'quiet splash' option, you will get detailed output that may help you diagnose the problem--does it always hang at the same spot?

---

### Post by Crafty Kisses on 2008-09-30
You may want to try the alternate CD.

---

### Post by maruthi_s@infosys.com on 2008-09-30
[COLOR="Blue"]
click on Umenu.exe
Click on Install Inside windows option. 
It will choose a drive with relevant space. 

Just click nexta and once the install is complete, do not remove the CD, just reboot the machine. 

It will ask for the OS option. Choose Ubuntu and press Esc. 

choose the 1st option of boot from CD. 

It will boot and take you to the ubuntu world. 

Let me know whether this works. 
[/COLOR]

---

### Post by brian_hayward on 2008-10-01
> **uberdonkey5 said:**
> try to download with a fast connection (I have many problems with bad images) or use a disk of a friend for whom you know the disk works. Is it a very old computer? sometimes this can be a cause, though maybe not unsurmountable.

Thanks for the suggestion.  I downloaded the distribution from the Ubuntu website (instead of re-downloading from the LiveCD site, i'm not sure if both sites provide the same download so I can't know for sure if it was actually the download that was messed up for me).  Anyway it works now and I'm happy.  Thanks again.

---

### Post by brian_hayward on 2008-10-01
> **sancho panza said:**
> To make sure that the iso image was downloaded correctly, use the MD5SUM number of the downloaded file and compare it with that given on the ubuntu download page. [Details here]("https://help.ubuntu.com/community/HowToMD5SUM").

Thanks for your suggestion.  I went to the Ubuntu website and downloaded the desktop distro and burned that image to a cd on the same computer that i did my original burning on (instead of going to the LiveCD website to re-download it, I'm not sure if both downloads are the same thing but the new cd works and the old one doesn't)  I am going to try your suggestion though on the old cd just to learn some stuff...good story, i know...anyway thanks again.

---

### Post by brian_hayward on 2008-10-01
> **maruthi_s@infosys.com said:**
> [COLOR="Blue"]
click on Umenu.exe
Click on Install Inside windows option. 
It will choose a drive with relevant space. 

Just click nexta and once the install is complete, do not remove the CD, just reboot the machine. 

It will ask for the OS option. Choose Ubuntu and press Esc. 

choose the 1st option of boot from CD. 

It will boot and take you to the ubuntu world. 

Let me know whether this works. 
[/COLOR]


I did not try this method, but thanks so much for the suggestion..like i mentioned to sancho panza I am going to try your suggestion just so i can learn more about Ubuntu.  thanks again.

---

