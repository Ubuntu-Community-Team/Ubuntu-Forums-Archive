---
title: "logging in issue plus nothing is now happening"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by 3blaxcatz on 2008-09-14
Hello,
I installed Ubuntu 3 weeks ago and as it it on a 2nd computer i have'nt been on since - I tried to log into today using the username and password - it was not accepted - assuming I'd just got it wrong i tried all variants - nothing

saw on one of the FAQ's advise to try live cd which i did and got in as far (using i think the password and username that i had when i used the live cd) as the orange screen with bird thing!

1. I am assuming that I set a new password when i installed as I have a different password and username written down

o.k so left it for many hour now back with time to sort it out

i have now logged on using the password and username that was accepted when i put in the live cd i get as far as the orange screen again with bird thing - it told me that the clock was wrong and asked me to correct but when i put in the password to authenticate  it said that there was an error

clock then disappeared 

nothing else
I can move the mouse but there are no options that I can choose

please can some one tell me in very very plain english what the problem might Be and how i can fix it and i would appreciate simple as I can not understand or even attempt to follow some of the suggestions that I have seen

---

### Post by pytheas22 on 2008-09-14
It sounds like there's a problem with your Ubuntu installation.  If I were you, I'd try first checking your Ubuntu installation CD for defects.  If there are no problems found, then reinstall Ubuntu again and hopefully the problem will be fixed.  If not, let us know.

You can try troubleshooting the problem on the existing installation, but since it takes only 30 minutes to reinstall, I think that's the easiest way to go.

---

### Post by 3blaxcatz on 2008-09-14
thanks so much for your response - which i can understand

i appreciate that you say it will take just 30 minutes to re-install  but the thought of going through  the installation process again ( i had a lot of difficulty with the network settings on set up) is not something i would choose to do IF there is another option

first (and yes i know it is a really stupid question)how do i re-install?

I'm use to windows that did everything for me - so I can't figure out how I force the computer to re-boot again from the live cd?  

and is there something i can do BEFORE i attempt to re-install?

I have now been able to log in using the safe mode - but don't know what to look for :confused:

---

### Post by pytheas22 on 2008-09-14
So you were able to log in using safe mode (not the live CD)?  Do you see the taskbar and menus in safe mode?  Can you run applications without a problem?  Can you reset your password (System>Users and Groups, or use the command 'passwd' from the command-line) so that you are sure of the correct one?  Let me know these things if you want to try to fix the existing system.

If you do want to reinstall, put your live CD in the drive, then restart your computer.  Immediately after it restarts, you need to press a key to bring up a boot menu so that you can select to boot to the CD--on most computers this key is F8, delete, escape, F2 or F12.

Then simply boot to the live CD and choose to install Ubuntu.  In the partitioning section (step 4 or 5 I think), choose 'manual partitioning.'  Then delete your existing Linux partition (it will be the one using the file system 'ext3'), and choose to create a new partition and install Linux there--this will overwrite your existing installation with a fresh one.  If you reinstall I can help you get the networking to work.

---

### Post by 3blaxcatz on 2008-09-14
wow - now that seems easy - I think even i can follow these instructions

yes I can see the menus and open applications
re applictions I'd only used firefox so far and yes this will open but not connect to the internet (this could simply be the network setting or a factor of being in safe mode)

just done a quick check of the applications and they all open o.k

re the password
I think i got it wrong when i logged in (yes I know you all knew that already :))
I make notes as I go along when i do something new including all of prompts as a reminder

If I check the user and group bit - there is only the one account - the one I set up when I installed  yes silly me!  I can if i want change the password but now I've got it I'll leave it as it is

I will attempt to log out and log in as usual and see what happens

---

