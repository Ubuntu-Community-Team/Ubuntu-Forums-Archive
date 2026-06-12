---
title: "Replace Windows 8 with Ubuntu"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by fahdozi on 2014-03-28
HI how are u ? i just want to know if i can do this !!!!!

/ i want to completely replace Windows 8 with Ubuntu :P i have my laptop "   toshiba satellite c850-b765 "

system info : [IMG]http://i.imgur.com/psPJYrR.png[/IMG]

---

### Post by Kris_Spencer on 2014-03-28
I was running Windows 8.1 pro w/media centre on my desktop until Windows tried to update and died. So after Windows leathally updating AGAIN, I said "I'm done" and now all my computers run Linux. The only reason I used Windows was because I game with my desktop. Anyway, the point is that you can totaly do it! I've worked off of Linux for years. I use it on my laptop for college work all the time.

---

### Post by mastablasta on 2014-03-28
what is the GPU? 

yes, you can do it.

to test it out and see if everythign work first you can run it in live session (no install).

---

### Post by Impavidus on 2014-03-28
CPU and RAM are fine. I can't find the graphics/wifi card/chipset of that computer. Those are sometimes problematic, but usually solvable. Try running Ubuntu from a live disk, without altering your system.

Do you have Linux experience? Cold turkey conversions often end in disappointment.

---

### Post by pyrotheseus on 2014-03-28
Definitely, your computer seems to be able to handle it. So far after replacing windows 7 with it the only problems i've had are with my graphics driver, but I probably just did something wrong :P

---

### Post by pqwoerituytrueiwoq on 2014-03-28
> **mastablasta said:**
> what is the GPU? 

yes, you can do it.

to test it out and see if everything work first you can run it in live session (no install).
hd7610m
basically a amd HD7000 series gpu
you may want to wait a week for the release candidate of 14.04 so you can have the latest kernel with a good driver for that gpu out of the box

---

### Post by Mark Phelps on 2014-03-28
You really need to try the LiveCD route before making the switch.  

Lots of folks with Toshibas have reported problems on the forums and the HD7xxx series doesn't appear to work very well with AMD drivers.  

One of the main reasons I strongly recommend dual-booting before making the switch is so that folks have a fallback position, should the conversion not go well.

---

### Post by oldfred on 2014-03-28
In addition we get several users every day who just erase Windows and then find one game or application or school needs for Windows and want to reinstall Windows in dual boot.
If really wanting Ubuntu best to start with dual booting. Then make full backup of Windows if you do decide to erase it.

       Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by pqwoerituytrueiwoq on 2014-03-28
if it is a school application you can install windows in a virtualbox, any AMD cpu or intel CPU that is at least a i3 support vitalization
but with resource intensive games, you should keep windows for that

---

### Post by whitesmith on 2014-03-28
> **fahdozi said:**
> HI how are u ? i just want to know if i can do this !!!!!You *can*, but before you do I would suggest carefully examining the pros and cons discussed in the first site listed in my sig line.

At the very least play around with a live CD or USB. Get to know something about the operating system before you make a commitment. Remember one thing: Linux is **not** free Windows. 
There's a non-monetary price to be paid for switching. The site referenced explains most of the details. Read before you leap. And the best of luck to you!

---

### Post by slooksterpsv on 2014-03-28
Lots of good answers here. Be sure to take heed into what people are saying/explaining. Dual-boot Ubuntu, it will allow you to dual-boot. I can provide Windows support if you'd like but that will have to be in a private message.

To give an example of another Linux OS (not Ubuntu) that is Debian based read on:
Some have jumped and thought "OMG Steam OS I can play games and not deal with Windows" only to find out that, 90% of the games they own don't have Linux counterparts. It also came at a bad time cause some people didn't read the threads they had posted about it completely deleting all partitions (and I tried it personally even though I had read it thinking advanced install will work) only to find that they lost everything. 
I attempted to do this, but I knew the risks and knew how to recover my data, if I needed it. I sometimes have to have Windows (as much as I hate it) to fix issues with Ubuntu (like I install a graphics driver and can't get back into the system) - mainly as a way of connecting to the web to research the issue I'm having. I'd feel comfortable using Linux purely, but there are games I own on steam (about 90%) that I can't run on Linux - even through WINE, so I keep Windows just for the games.

Make your decision wisely and know we can help you out with any issues regarding supported versions of Ubuntu. Graphics drivers may be the biggest issue you'll face.

---

### Post by holycow131415 on 2014-03-28
You should dualboot. You paid for windows, so why delete it?

---

### Post by Navneet_Kumar on 2014-03-28
Yup I support @holycow131415....u should dualboot it with windows and grub gives no such problems............i myself have a dualboot system of windows 8.1 wit ubuntu and it works perfectly........no need to worry just do it...........:D

---

### Post by presence1960 on 2014-03-28
> **Mark Phelps said:**
> You really need to try the LiveCD route before making the switch.  

Lots of folks with Toshibas have reported problems on the forums and the HD7xxx series doesn't appear to work very well with AMD drivers.  

One of the main reasons I strongly recommend dual-booting before making the switch is so that folks have a fallback position, should the conversion not go well.

I had a toshiba c655 series. Problematic for Ubuntu and Mint. Installed Arch and no problems. Go figure! In Arch the proprietary AMD drivers were no good for video. 

+1 for dual booting.

---

### Post by sammiev on 2014-03-29
A lot of good info on these pages.
+ 1 for dual boot.

---

### Post by monkeybrain20122 on 2014-03-29
> **pqwoerituytrueiwoq said:**
> hd7610m
basically a amd HD7000 series gpu
you may want to wait a week for the release candidate of 14.04 so you can have the latest kernel with a good driver for that gpu out of the box

If experience is to go by you rarely have good graphic driver out of the box (except for Intel) for each ubuntu new release, let alone a release candidate. Personally I would definitely stay away from 14.04 if this is my only system, I don't need the thrill of breakage for every update. I would install 13.10 and switch to 14.04 in july, there are still almost 4 months of support for 13.10 and by July 14.04 would be solid after a few waves of post install bug fixes.

---

### Post by fantab on 2014-03-29
> **oldfred said:**
> In addition we get several users every day who just erase Windows and then find one game or application or school needs for Windows and want to reinstall Windows in dual boot.
If really wanting Ubuntu best to start with dual booting. Then make full backup of Windows if you do decide to erase it.

       Linux is not Windows:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

   Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

+1.

Dual Booting is an excellent idea. Install Ubuntu and use only that. But keep Windows until such time that you are really comfortable with Linux. Also you've paid for an expensive OS. So keep it around.

---

### Post by monkeybrain20122 on 2014-03-29
> **holycow131415 said:**
> You should dualboot. You paid for windows, so why delete it?

-1 for dual booting.

Well if you have been forced to pay some racketeers does it follow that you should not escape even when there is a chance because you will lose their 'service'? If you pay for life insurance does it follow that you should die to make it worthwhile? :)

If you don't actually need or use Windows keeping it around is like hanging a heavy weight on your neck (because you pay for it??) It isn't just a waste of space, dual booting with Win 8 is the source of a lot of inflexibilities and complications because of secure boot and uefi. It is a lot simpler for installation and maintainence (back up, cloning, trying out other Linux distros etc) to just remove Windows if there is no use for it.

---

### Post by monkeybrain20122 on 2014-03-29
> **pqwoerituytrueiwoq said:**
> if it is a school application you can install windows in a virtualbox, any AMD cpu or intel CPU that is at least a i3 support vitalization
but with resource intensive games, you should keep windows for that

Agreed. Vbox is a much better solution than dual boot if you only have to use a few Win programs (and they don't work in wine)

---

### Post by Kris_Spencer on 2014-03-29
> **monkeybrain20122 said:**
> Agreed. Vbox is a much better solution than dual boot if you only have to use a few Win programs (and they don't work in wine)


I agree with that, other than I wouldn't even try to run games in Virtual Box. However, I did have a VB set up last year when I needed Microsoft Visual Studio and Microsoft SQL Server software. It works wonderfully! And using VB's seamless mode is pretty cool.

When I bought either one of my laptops, first thing I did was wipe the drive (also had to e-cycle the 1 year of antivirus they gave me to install...). I refuse to have Windows on my system directly.

---

