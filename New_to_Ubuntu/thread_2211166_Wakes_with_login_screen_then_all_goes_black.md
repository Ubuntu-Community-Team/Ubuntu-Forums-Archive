---
title: "Wakes with login screen then all goes black"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by valle2 on 2014-03-14
Hi All,  Thank you in advance for any help and for lots of patience!  I am an absolutely beginner with no computer savy!  My computers keep getting viruses in Windows that require complete reformatting from corruption so my son recommended Ubuntu and I took the plunge.  I don't know anything except how to use it on the surface BUT I can follow directions!  Just please make the directions explicit so I know exactly what to do.

I love it so far, but here's my only problem:  BTW I am using 12.04.4 32 bit (only 2G RAM.)  When I select "suspend" or shut my laptop lid it goes to "sleep" which is perfect, then when I open the lid it starts up and gives me a "login" screen in the center of the page - all fine still.  After I enter my login information everything disappears and a completely black screen (but "live" black not "off" black) comes up and nothing else ever happens.  Then I have to press the power button and re-boot, which I don't really think I should have to do each time.  

I am starting a new thread because this seems different than the other posts I've read where they have the black screen from the time the lid opens.  My situation is different because I DO get the login page.  But note that this login page is DIFFERENT than the login page at initial reboot.  The re-boot login page has white dots on it and the login spaces are on the left side, not the center.  I don't know if that helps anybody know what's happening or not, I hope so!  

I am on an unmodified Dell D630 Latitude with a Nvidia Quadro NVS135M video card. 

When I installed Ubuntu yesterday I did not install anything extra, it all seemed to work from just the iso file that I downloaded on my desktop and burned to a DVD then booted from on my laptop.  

Thanks!
Valle

---

### Post by r.stiltskin on 2014-03-14
Problems with resuming after suspend are fairly common, and very distribution- and hardware-specific.  Your best bet may be to try a newer distribution.  You can wait a month or so until the official release of 14.04, or if you're impatient try the [Kubuntu 14.04 Beta]("https://wiki.kubuntu.org/TrustyTahr/Beta1/Kubuntu") (it's beautiful).  You can try running it directly from the Live USB & see if it helps before you bother to install it.

In the meantime, shut the computer down before you close the lid.

---

### Post by r.stiltskin on 2014-03-14
It occurs to me that there is a sort of "solution".  It doesn't correct the underlying bug, but it will eliminate your improper shutdowns.

You can change your system settings so that the system shuts down (rather than suspend) when you close the lid.  I'm not sure where it is in Ubuntu.  In Kubuntu it's  in System Settings/Power Management/Energy Saving Settings.  There's a dropdown menu that lets you choose what happens when the laptop lid is closed.  I'm sure there must be an equivalent setting someplace in Ubuntu's system settings.

---

### Post by valle2 on 2014-03-15
Thank you for your replies.  

In Ubuntu Wiki I found this with regard to the BlankScreen problem:  If it occurs *after* entering your password on the login page, you have  some different class of issue, such as an issue with 3D / DRM.  Try  disabling compiz (sudo chmod a-x /usr/bin/compiz), logging in as a different user, or turning off DRI."  But the only thing I understand of that is logging in as a different user..........what are these other things and how do I do them?

---

