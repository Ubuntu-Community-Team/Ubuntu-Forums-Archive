---
title: "trying to boot and install from cd: Command prompt  ~$"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by kinetonat on 2013-09-01
[INDENT] 					HI,

Can anyone offer to assit me please? Sorry for such ignorance

I'm trying to install Lubuntu from an ISO cd disc I have burnt. I check  the DSUM number it matched, so I burnt the cd from the download  lubuntu-12.04-desktop-powerpc.iso  and hadno problem there. I already  use Ubuntu and have experience only of booting from live Cd's....as a  dummy basically. So i was hoping to be able to follow instructions that  usually appear andnot  with command line prompts. It kicked in from the  cd tray and bootd, giving me a black screen and boot prompt, so i typed  in 'live' and it proceeded to do something on a blue screen much like  when 12.04 starts up when installed with four dots that from right to  left progress.

Now the screen is back to black again and it says:

Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-powerpc-smp ppc)
*Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
[B]
lubuntu@lubuntu:~$[/B]

I was expecting the live screen to try it or the starting point for  installation as is usual form live cd's. As a dummy, what is the  commmand prompt all about, and what should i do here to further install  it etc? it seems i'm my ignorance is preventing me from some simple  operation to proceed.

I'm trying this live cd on an Apple Mac G4 graphics, PPC with low spec  but high enough spec for it to work according to my download source

Many thanks 				
[/INDENT] 			
  			   		
 			 			 			[INDENT] 				 					[Last edited by kinetonat]("http://ubuntuforums.org/posthistory.php?p=12775821"); 32 Minutes Ago at 05:21 AM. 				 				 			
[/INDENT]

---

### Post by cipherboy_loc on 2013-09-01
Two things come to mind as being the source of this issue: Xorg or the Linux Kernel. Xorg is the display server that powers graphics on most Linux systems. Other programs like LXDE (the display manager for Lubuntu) interface to it for their rendering needs. If Xorg had an error booting, you would likely get dropped to a command prompt like yours. To view the Xorg log, either use cat (*cat /var/log/Xorg.0.log*) or less (*less /var/log/Xorg.0.log*) if the output is too long and you want to manually scroll through it. If the Linux kernel is the issue, dmesg would show the error. In which case, simply run the *dmesg* command, or if the output is too long, pipe its output through less (*dmesg | less*). 

If you are not familiar enough to troubleshoot the errors yourself, no problem. Simply install pastebinit, a program that will take input and send it to Ubuntu's pastebin equivalent and display a link. Write down this link and post back. To install pastebinit and post relevant logs:
```

sudo apt-get update
sudo apt-get install pastebinit
pastebinit /var/log/Xorg.0.log
dmesg | pastebinit

```
Don't forget to write down the links and post them here.

Lastly, I would suggest taking a look at this guide, specifically step two. The guide's author provides some troubleshooting steps if a graphical display does not work.


Thanks,
Cipherboy

---

### Post by whitesmith on 2013-09-01
Consider the (admittedly slim) possibility of a bad CD or some form of defective hardware. Burn **U**buntu to a CD and try that. If it works, you've obviously got a problem with your Lubuntu disk. By continuing to narrow the problem domain, you'll eventually get the right answer.

---

### Post by kinetonat on 2013-09-01
with the command dmsg etc
I got the link [http://paste.ubuntu.com/6052842](http://paste.ubuntu.com/6052842)    also 6052861

---

### Post by kinetonat on 2013-09-01
i tried this command nano /var/log/Xorg.0.log
abd the problem seems to begin with lines saying No Layout section, No screen section available, No monitor specified for screen (default etc),and towards the end 162.990 EE Unable to find a valid framebuffer device

---

