---
title: "Looking for help hooking to a T.V."
date: 2008-07-16
forum: Pennsylvania Team - US
---

### Post by Sabar on 2008-07-16
Well I don't know how many of you have ever had this bad idea. Wow a 32" HD Widescreen T.V. would make a GREAT Monitor.

So far I am finding out I was wrong. 

I recently purchased a 32" Go Video (probably my first mistake) Plugged it into my alien with is duel booting XP and Ubuntu 7.10.

I am running a three year old rig with an ATI x550 256mb PCIe Radeon Video Card.

After all that I was shocked to see things worked with Windows but not Fiesty. What will happen on boot it will go to the grub and if I pick fiesty the splash screen will come up but when it is time for the log in screen I get a [COLOR="Red"]NO SIGNAL[/COLOR] from the T.V.

So far I have tried a few things. Below is a quote from the regular Help forums [[COLOR="Blue"]From my original Post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=846774&highlight=Sabar")



>  Failing at plans
Ok. here is what I have done so far.

Under the grub I clicked on "Recovery"

then I typed in
Quote:
Sudo dpkg_reconfigure-phigh xorg-xserver
The response. I got was it did not recognize this

So then I typed in
Quote:
sudo dpkg-reconfigure xserver-xorg
This got me a box with options I followed thruethe options, set my monitor at 1024x768 clicked on the option so say it was bigger than 24" and basically defaulted to everything else.

Didn't work. still just have the no signal screen.
same as I had before just the grub screen then the load screen with the bar on it then .......... nothing ....

I was about to try the third option to see if that does anything. but I wanted to post this to see if there was something under advanced options I should have done.

Thanks by the way, to every one trying to help me out



P.S.

I Ran
Quote:
gksudo displayconfig-gtx
The responce I got was " GTK - WARNING ** cannot open display

I also reran
Quote:
sudo dpkg-reconfigure xserver-xorg
the only diferance was I tried the highest first number that ended with a x768 I think it was 12??x768. then I went under medium and chose 1024x768

same result of "No Signal"

I did find this interesting post though. I just didn't find anything in it that helps yet though. Comprehensive Multimedia & Video How-to

If anybody has any more ideas or sees what I am doing wrong please let me know becouse my wife is getting really mad at me.

Thanks

If any one has any ideas please let me know. The other thing I was thinking about updating my video card any how. But dont know what is most linux friendly  But i have a few ideas I think??
If some one could let me know what you think of these.

[GeForce 8800GTS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130300")

[GeForce 8800 GT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130318")

---

### Post by Rhubarb on 2008-07-22
Any nvidia based video card should be fine.
Just make sure you know what video card slot you've got (AGP / PCIe)
And whether it's an 8 or a 16 lane PCIe slot.

And obviously make sure it's got TV-out support too.  (I'm not sure what inputs your HD TV has).

The nvidia drivers have some very good configurable tv-out settings you can use (some of it may be command-line based).

---

### Post by treepolitik on 2009-03-10
In theory, if you have the right wire, you can use Ubuntu as a cable box for a noncompliant TV, because Linux is based on analog, although it has a digital interface.  What do you think?

---

