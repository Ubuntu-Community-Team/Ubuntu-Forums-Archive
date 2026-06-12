---
title: "Ubuntu 11.10 Clean Install wont Boot Up! (More Info In Video)"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by HydroCity on 2012-02-25
This Video Explains my Issue: [http://youtu.be/lhZwVz_waeM](http://youtu.be/lhZwVz_waeM)
Last  weekend I installed Ubuntu with the same disk in the video, worked  perfectly. after a few days i decided to switch back to windows XP which  i had the disk with me as well, Due to (Too Many) Issues, i'm switching  back to Ubuntu, But when i Re-Install It does the same thing no matter  how hard i try (Look in Video). If anyone could help me, it would be  mighty appreciated :confused:

---

### Post by 23dornot23d on 2012-02-25
Does Ubuntu still run ok from the CD ..... when you boot from it .....

The thing is with the black screen at start - it probably is not detecting the graphics card
as it should ..... 

either hold the shift key down as it boots up or try pressing esc repeatedly ......

to get grub to come up .....

How do you boot it from the CD do you use the nomodeset option ?

---

### Post by HydroCity on 2012-02-25
The CD will boot fine when i ask it to do so from the Start up "F12" Menu.
And ill try the Shift Key Method, ill reply back when possible

---

### Post by HydroCity on 2012-02-25
Shift didnt do anything. and Escape starts to make a loud beep sound whenever i press it

---

### Post by 23dornot23d on 2012-02-25
What graphics card is in the computer , is it Nvidia or Ati ..... ?

---

### Post by HydroCity on 2012-02-25
All i know is that its Intel Centrino Duo with 954GM Video Controller.. I think its Nvidia

---

### Post by 23dornot23d on 2012-02-25
When you installed linux 

How much room did you allocate for Linux and did you leave the existing windows on the machine ?

What size hard drive is in it too .... 60 Gig or bigger ?

---

### Post by HydroCity on 2012-02-25
I removed Windows. And the only drive i could install it on had 80 GB.

---

### Post by HydroCity on 2012-02-25
**Drives**

                                             
[LIST]
[*]Primary hard drive : 100 GB
[/LIST]
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    **Processor**

                                             
[LIST]
[*]Processor type : Intel Core Duo
[*]Processor speed : 2 GHz
[/LIST]

---

### Post by josephmills on 2012-02-25
could you please boot a live cd thn use it as a LIVE(TRY) one. 
then open terminal and enter 
```
lspci -nn | grep VGA 
```
then please paste that here. thanks

---

### Post by HydroCity on 2012-02-25
> **josephmills said:**
> could you please boot a live cd thn use it as a LIVE(TRY) one. 
then open terminal and enter 
```
lspci -nn | grep VGA 
```then please paste that here. thanks

Can you explain how to do that?

---

### Post by 23dornot23d on 2012-02-25
Try to reinstall it again - my advice - just so we know its installed ok
and watch for any errors on the install

Allocate .....

40 Gig root (ext4) - 4 Gig swap - the rest as /home (ext4)

Boot Install on sda if its your only drive.

Let me know if this is what you would like to do - as the situation at the moment seems
we cannot check anything easily .... and a quick re-install could fix things ....

It takes around 30 mins to do .... then let me know what the situation is ......

I just want to ensure we have a good install then we can go from there.


Beat me to it ....  ( can check it all out ) .... but if it worked once before for the user it
should really work again .... unless ( The install CD is naff - or it did not install properly )

Can spend some time tracking down if it is just a graphics problem though ..
but difficult to sort from the LiveCD .... and a fresh install may solve it ....

---

### Post by josephmills on 2012-02-25
> **HydroCity said:**
> Can you explain how to do that?

1) insert cd(ubuntu) into computer 
2) boot the cd from the bios 
3)choose TRY ubuntu 
4)press ctrl+alt+t (this will open terminal)
5) enter in code above 
6) open firefox or whatever browser is installed aka firefox
7) paste what the output in the terminal says. 
8) Please keep running on live cd 
9) enter ```
sudo fdisk -l 
```
10) paste the out out here 
hope that this helps 
joseph

---

### Post by josephmills on 2012-02-25
> **23dornot23d said:**
> Try to reinstall it again - my advice - just so we know its installed ok
and watch for any errors on the install

Allocate .....

40 Gig root (ext4) - 4 Gig swap - the rest as /home (ext4)

Boot Install on sda if its your only drive.

Let me know if this is what you would like to do - as the situation at the moment seems
we cannot check anything easily .... and a quick re-install could fix things ....

It takes around 30 mins to do .... then let me know what the situation is ......

I just want to ensure we have a good install then we can go from there.


Beat me to it ....  ( can check it all out ) .... but if it worked once before for the user it
should really work again .... unless ( The install CD is naff - or it did not install properly )

Can spend some time tracking down if it is just a graphics problem though ..
but difficult to sort from the LiveCD .... and a fresh install may solve it ....

hi there sorry I must have been posting while you where this sounds like a great idea   ):P

---

### Post by ahiung on 2012-02-25
I KNOW THAT !!!!!!!!!!!! REALLY!

This incident happened in my small laptop year ago.
The thing is...you really need to clean reinstall your Ubuntu, delete all partition as clean as you can.

THIS WILL LET YOU ACCESS YOUR COMPUTER FOR (DEPENDS) TIME.
Sometimes it will let you access it untill you open a browser, sometimes it will let you access it untill you write something in wordpad or something.
AFTER THAT.....YOU WILL OUT OFF THE DESKTOP and lead you to DOS screen.
like this

askdhfjkjasf
sdhfjasfhas
kjhsalkfjasklfjaslkdf
sahjflksajflksdajfsa
\salkfklsajf
sahjfasjfd
something@user: Login
Enter your ID
Enter your Password

HOW TO ACCESS YOUR DESKTOP?
When you reboot and goes to the blinking _ screen
press between F1 to F3 or F4 as fast as many times as you can.
sometimes it will stuck in DOS screen and sometimes it lead you to desktop.

HOW I GOT THIS PROBLEM?
I DON'T KNOW! maybe the LXDE messed up my system.

---

