---
title: "Beginner Who Needs Help."
date: 2012-02-29
forum: New to Ubuntu
---

### Post by atm1092 on 2012-02-29
Hey there, a few months ago i had installed ubuntu 11.10 and began enjoying the experience very much. One day i started my computer after an update and the computer experienced some type of problem that caused it to crash at the loading screen with 4 dots. As best as i can remember, the error stated something like a DMA status error. PCE  ? MY question is, where and how can i find all of the information i need to post here in order to get my pc back into working order. 

Thanks!

Signed,
A Determined N00b

---

### Post by atm1092 on 2012-02-29
Hey there, a few months ago i had installed ubuntu 11.10 and began enjoying the experience very much. One day i started my computer after an update and the computer experienced some type of problem that caused it to crash at the loading screen with 4 dots. As best as i can remember, the error stated something like a DMA status error. PCE ? MY question is, where and how can i find all of the information i need to post here in order to get my pc back into working order. 

Thanks!

Signed,
A Determined N00b

---

### Post by QIII on 2012-02-29
That's a hardware error in the DMA (Direct Memory Access) controller.   It could be the motherboard itself or something you have plugged into  it.

Unplug the machine.  Open the case.  Touch some bare metal inside to discharge any static.  


Disconnect the HDDs, DVDs, floppies, dedicated video cards and memory from the motherboard (not the processor) then turn it on and see if you hear POST beeps. (You'll get some weird ones, most likely.  The POST won't like the fact that it can't find anything.)

Put everything back in and try again.

---

### Post by daslinkard on 2012-02-29
> **atm1092 said:**
> Hey there, a few months ago i had installed ubuntu 11.10 and began enjoying the experience very much. One day i started my computer after an update and the computer experienced some type of problem that caused it to crash at the loading screen with 4 dots. As best as i can remember, the error stated something like a DMA status error. PCE  ? MY question is, where and how can i find all of the information i need to post here in order to get my pc back into working order. 

1st Question....can you give some details on your system....because it sounds like to me that it could be some faulty hardware....I'm thinking it could be a range from a HD issue, possibly Power Supply...just need a little more info about your system....BTW the DMA stands for Direct Memory Access.

Don't start crying just yet....we're here to help.

---

### Post by imachavel on 2012-02-29
Boot to the live cd. There should be some logs you can check. Sorry I'm a little too busy to help you right now. What error do you get after bios runs, and OS tries to load at boot? Sorry about your update error. Does OS load at all?

---

### Post by imachavel on 2012-02-29
Oh wow disconnect it all, ram, hdd interface, expansion slot cards, disconnect power cables from psu to board, the reseat it all, and see if bios corrects itself?

---

### Post by coolman98 on 2012-02-29
take it apart put it back together and reinstall :(

---

### Post by HeroOfCanton on 2012-02-29
First, specify what you mean by the loading screen. On boot? Splash screen? After entering your password?

Then start her up and write down the EXACT error message.

We'll go from there... :)

---

### Post by daslinkard on 2012-02-29
Didn't you make the same post [here]("http://ubuntuforums.org/showthread.php?t=1933660")?  It looks like there have already been several suggestions made.

---

### Post by atm1092 on 2012-02-29
my apologies for being so vague.

boot screen


Im loading from grub to Ubuntu with linux 3.0.0-12-generic-pae

Goes to boot screen and i get 

25.024004 NMI : PCI system error (SERR) for reason b1 on CPU  0

25.024004 Dazed and Confused but trying to continue.

Waiting for netowrk confiuguration for a few mins then to booting system wihtout full network configuration. Stuck here

---

### Post by atm1092 on 2012-02-29
wow sorry for the double post. internet is super slow when using ym backup computer. didnt even see that my first thread went through. let me check there. sorry guys

---

### Post by atm1092 on 2012-02-29
thanks for the replies. i accidentally created two threads because im on my backup computer. ill copy what i said in there about the status of my system as of right now.

Im loading from grub to Ubuntu with linux 3.0.0-12-generic-pae

Goes to boot screen and i get 

25.024004 NMI : PCI system error (SERR) for reason b1 on CPU 0

25.024004 Dazed and Confused but trying to continue.

Waiting for netowrk confiuguration for a few mins then to booting system wihtout full network configuration. Stuck here

---

### Post by QIII on 2012-02-29
No, imachavel.

Looking for the hardware error the BIOS is reporting.

It would be a little difficult to run the LiveCD with a hardware error keeping him short of getting there.

---

### Post by daslinkard on 2012-02-29
First thing I would do would be to check and see if there is a BIOS update for your system..

---

### Post by 23dornot23d on 2012-02-29
Google the error .....

Seems there are a few reports on this ....... [[COLOR=Blue]_**Link to search I just did**_[/COLOR]]("https://www.google.com/search?q=PCI+system+error+%28SERR%29+for+reason+b1+on+CPU+0#hl=en&sclient=psy-ab&q=PCI+system+error+b1+on+CPU+0&pbx=1&oq=PCI+system+error+b1+on+CPU+0&aq=f&aqi=g-b1&aql=&gs_sm=3&gs_upl=15829l17427l0l17832l18l9l0l0l0l3l421l2017l0.5.1.2.1l9l0&gs_l=serp.3..0i8.15829l17427l0l17833l18l9l0l0l0l3l421l2017l0j5j1j2j1l9l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=9300c40edbea2b3a&biw=1099&bih=495") .....

---

### Post by atm1092 on 2012-02-29
i have made all attempts possible at self help over the last 2 months lol. 

keeps getting a DMA error on eth1.

---

### Post by QIII on 2012-02-29
On board ethernet?

---

### Post by imachavel on 2012-02-29
Remove all cards from pci slots on main board then reboot.

[http://www.google.com/#sclient=tablet-gws&hl=en&tbo=d&source=hp&q=mainboard+expansion+slot&pbx=1&oq=mainboard+expansion+slot&aq=f&aqi=g-v1&aql=&gs_sm=12&gs_upl=2046292l2055193l1l2057204l24l15l0l8l8l0l1010l5527l0.6.2.2.2.1.1.1l24l0&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=631c35b7a88461da&biw=1024&bih=672](http://www.google.com/#sclient=tablet-gws&hl=en&tbo=d&source=hp&q=mainboard+expansion+slot&pbx=1&oq=mainboard+expansion+slot&aq=f&aqi=g-v1&aql=&gs_sm=12&gs_upl=2046292l2055193l1l2057204l24l15l0l8l8l0l1010l5527l0.6.2.2.2.1.1.1l24l0&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=631c35b7a88461da&biw=1024&bih=672)

make sure your mobo looks like that. I mean the processor and heat sink and ram and power cables and hd controller should all be connected. But everything in those expansion slots should be bare. Now when you reboot, hopefully you can connect all the i/o devices (video, audio, network) to onboard ports. Boot up and if the DMA error goes away you found the culprit

---

### Post by imachavel on 2012-02-29
> **QIII said:**
> On board ethernet?

You mean is there a network card in an expansion slot??

---

### Post by 23dornot23d on 2012-02-29
It seems to be reported as a kernel bug ..... 

can you get to a terminal and do (LSPCI) lower case) as below

**lspci**

and post back the results at all or is the terminal / console unreachable too .... does it run
ok without the ethernet connected .....  so you can get more info and then re-connect.

---

### Post by atm1092 on 2012-02-29
i removed all pci cards except for the video card and i am still getting the same error. terminal is unreachable. only select able interface i can reach is the grub

---

### Post by QIII on 2012-02-29
Is your ethernet card built into the mobo?

Elminate simple facepalm hardware fault first, then look at OS.

---

### Post by atm1092 on 2012-02-29
no i have an nvidia 7950gt. there is no video slot on the mobo

---

### Post by QIII on 2012-02-29
Sorry.  See correction.

---

### Post by QIII on 2012-02-29
This could very well be the suggested kernel bug, which I was not aware of.  And I must apologize -- in your first post I didn't realize you were past POST.

---

### Post by atm1092 on 2012-02-29
no. there is an ethernet plug on the mobo, but right now the pci ethernet card is removed. 

right now the sound card, ethernet card, and tv tuner card are removed. Only the video card is connected to the mobo along with HDDs


EDIT: like i said. i made all of these attempts a while back until i gave up completely and have revived the effort today. I will take all steps necessary to bring this computer back into order, except costing me $$$

---

### Post by 23dornot23d on 2012-02-29
My advice would be to try a liveCD using a different kernel to the one being reported with
the Bug for that error - you are receiving ..... if you are still getting the same error with different LiveCDs .... and different kernels .... then it may well be a hardware fault. 

( possibly on the motherboard itself if everything else has been removed )

It does not appear to be a graphics card problem .... but to test that you would have to remove the graphics card and
use the onboard vga graphics.

Do you run another Operating System on this machine .....  ?

kernel 2.6.39.1 and 2 seem to be the ones it happens on ....

---

### Post by atm1092 on 2012-02-29
im not sure how to use a different kernel... sorry im such a amateur. Do you mean load up a different version of ubuntu? like 10. or 11.04 ? 

no other operating systems by the way.
Is there no simple way to reformat these HDDs and start fresh from bios?

---

### Post by 23dornot23d on 2012-02-29
Yep 11.10 is a later kernel ..... but looking back through the posts - you have already tried it too .....

[[COLOR=Blue]_**LINK**_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11729055&postcount=12")

> 
Im loading from grub to Ubuntu with linux 3.0.0-12-generic-pae
[COLOR=Red]**Try 10.04 or 10.10 ...... maybe it is hardware if these too give the same error. .......**[/COLOR]

first check by booting from liveCDs before altering the hard drives ..... if it will not boot from the
liveCDs and gives the same error .... then there may be another problem ....

but not seeing anything related to the hard drive - with the error you get .....

Update there are some errors related to overheating of the Graphics Card .... is this machine used for
high intensive graphics ..... gaming .....  and did the error start after it getting hot .... just a thought after
some threads I have been reading .... 

( there are a couple of Bugs that do relate to hard drives too - after doing some deeper searches on this )

and seeing that all you have plugged in now is the graphics card and the hard drives .....

Check that all the seatings and all the connectors are good ...... is the CPU fan working ok

Has the CPU or GPU overheated ..... look for burn marks .... you only have graphics built into
the motherboard when reading this ..... 

> 
no i have an nvidia 7950gt. there is no video slot on the mobo


So we cannot do anything with the graphics ....

How many hard drives ? and what type ......

---

### Post by QIII on 2012-02-29
> **atm1092 said:**
> I will take all steps necessary to bring this computer back into order, except costing me $$$

That's always the desired outcome! :)

OK.  Looking back at your original post, you said this started after an update.  Was it the first time you started the machine immediately after the update?

---

### Post by HeroOfCanton on 2012-03-01
> **atm1092 said:**
> im not sure how to use a different kernel... sorry im such a amateur. Do you mean load up a different version of ubuntu? like 10. or 11.04 ? 

no other operating systems by the way.
Is there no simple way to reformat these HDDs and start fresh from bios?

First, let's explain the kernel a bit... While another version will normally have a differnt kernel, it's not guaranteed. Also, you **can** run a different kernel while keeping your current OS (although in Ubuntu linux specifically this is not recommended).

BIOS does not hold your operating system so you cannot "reset" Ubuntu from there. You would need to reinstall from a CD or USB. BIOS simply holds the hardware information your computer needs to operate.

In human terms:
While the kernel is commonly referred to as "the brain" I don't like that comparison at all. I'd say it's more like the specific sections of the brain that control the most basic functions like breathing, heartbeat, temperature regulation, etc. The most "core" part of the system.

BIOS (firmware) would be more like your nervous system. Connecting the hardware (body) to the software (brain).

Not trying to crack on your posts or anything, just trying to make sure you understand the differences before accidentally causing damage to your system. We all had to learn sometime. I learned by accidentally breaking  many things... Trying to save you that heartache. :)

Now onto your problem.
As 23d said please try a live cd next. That would be an Ubuntu installation cd, but instead of selecting to install choose the option that says "Run Ubuntu from CD" or something like that.

Even if it boots right up, you're not done! To eliminate hardware issues you need to browse the web (test networking card), open some files on your hard drive (test the drive for operation), and try running a few programs just to be sure everything is going well. Let us know how that goes and we'll have a much better idea of what may be happening.

If you get problems from the live CD, it may be hardware. I'll make one more suggestion at the risk of being beaten up... :D Try a Windows CD if you have one. Every single listing in the search 23d listed was a linux system. I'm wondering if it could be a hardware compatibility problem with linux only. If both OS's have a problem, we can be 100% sure it's hardware. Then we'd just have to find out which part.

(Sorry for the long post, but problems aren't always simple and the lessons will do you good in the long run)

---

### Post by atm1092 on 2012-03-02
> **HeroOfCanton said:**
> First, let's explain the kernel a bit... While another version will normally have a differnt kernel, it's not guaranteed. Also, you **can** run a different kernel while keeping your current OS (although in Ubuntu linux specifically this is not recommended).

BIOS does not hold your operating system so you cannot "reset" Ubuntu from there. You would need to reinstall from a CD or USB. BIOS simply holds the hardware information your computer needs to operate.

In human terms:
While the kernel is commonly referred to as "the brain" I don't like that comparison at all. I'd say it's more like the specific sections of the brain that control the most basic functions like breathing, heartbeat, temperature regulation, etc. The most "core" part of the system.

BIOS (firmware) would be more like your nervous system. Connecting the hardware (body) to the software (brain).

Not trying to crack on your posts or anything, just trying to make sure you understand the differences before accidentally causing damage to your system. We all had to learn sometime. I learned by accidentally breaking  many things... Trying to save you that heartache. :)

Now onto your problem.
As 23d said please try a live cd next. That would be an Ubuntu installation cd, but instead of selecting to install choose the option that says "Run Ubuntu from CD" or something like that.

Even if it boots right up, you're not done! To eliminate hardware issues you need to browse the web (test networking card), open some files on your hard drive (test the drive for operation), and try running a few programs just to be sure everything is going well. Let us know how that goes and we'll have a much better idea of what may be happening.

If you get problems from the live CD, it may be hardware. I'll make one more suggestion at the risk of being beaten up... :D Try a Windows CD if you have one. Every single listing in the search 23d listed was a linux system. I'm wondering if it could be a hardware compatibility problem with linux only. If both OS's have a problem, we can be 100% sure it's hardware. Then we'd just have to find out which part.

(Sorry for the long post, but problems aren't always simple and the lessons will do you good in the long run)


now i understand perfectly because of this reply

Let me mention that i have attempted to install Windows XP media center ed. but my attempt was foiled when the OS asked for the product key. i look down and notice that 4 digits had been rubbed away leaving me with a partial key. 

As for hardware; i have a 2X maxtor 250 gb hdds, nvidia as stated above and some type of network card as well. i have some experience with building computers but none with OS.

THe update began a few days after 11.04 and shortly after the update finished it had crashed. what live cd do you recommend to try?

---

