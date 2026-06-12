---
title: "And into Karmic Koala...."
date: 2009-10-07
forum: Philippine Team
---

### Post by Laibcoms on 2009-10-07
Currently backing-up my stuff ^_^  Why?  Upgrading to 9.10 Karmic Koala (beta) !!

I can't wait for RC-1 week :p I'll install it now, should be fine when it comes to the other apps I use since it's been Beta release +1 week already.

Who here are using Karmic Koala already?  Or when are you going to upgrade?

... back to work...  /run Karmic Koala 64-bit alternative fresh install...

---

### Post by guitar_man on 2009-10-07
I have'nt install it...just live cd.....still loooking for my extra Hard disk install and test karmic...

---

### Post by sixrodriguez on 2009-10-07
na-upgrade ko karmic to jaunty ko........

maganda siya.....

themes......

splash......

sa audio, static na-encounter ko......

kaya to balik muna ako jaunty......

wala naman ako cd karmic para sa fresh install.......

wait nalang siguro ako sa official release......

share naman kayo experience nyo sa karmic beta......

More Power Ubuntu Team Philippines!!!!!

---

### Post by Laibcoms on 2009-10-07
My first experience:

Ubuntu 9.10 Karmic Koala Beta Alternate CD fails to detect my SATA Hard Drive.

:p

So now I'm downloading the LiveCD iso T_T  Have to wait between 4-6 hours...

---

### Post by killer_d76 on 2009-10-07
I just installed it on my lappie.. yung OSX partition eh na-recognize agad not unlike nung unang labas may bug sa grub.. themes, splash everything looks very nice and it's FAST!.. with just 2.1GB footprint what more can you ask for?

---

### Post by cloudscream on 2009-10-07
Intel GM965 performance is FAST on Karmic! It's way faster than it was on Hardy (before the disaster in Intrepid and Jaunty).:guitar:

---

### Post by jepong on 2009-10-07
upgraded na ako alpha 5 pa lang... 

encounter ko lang now is nag hhigh and llow brightness so parang nag bblink cya hanggang di pa loaded gnome-power-manager and hindi one click pag connect sa mobile broadband, you have to disconnect and connect several times bago maging successful... 
so far solb na solb na ako... 

astig yung theme at humanity icon plus if you install the community-themes package, you'll get the breathe-icons and few more nice themes.

wwait ko pa final release nung ifuse and libiphone para maka-sync na ako ng music using ubuntu.

:guitar:

---

### Post by killer_d76 on 2009-10-07
waaahhhhh... my CD/DVD Rom drive is not recognized!.. pag-salpak ko ng CD sa drive eh parang walang nangyari! :(

---

### Post by guitar_man on 2009-10-07
makapag-install na nga para makita ko kung ano mga problems......

---

### Post by Laibcoms on 2009-10-07
Go go! The more the merrier :p hehe...  Para sa launch party natin prepared (since I read we'll have media guests).

I agree, GRUB2 auto-setups dual-booting.  I always forget to setup GRUB and put back XP, now I don't have to worry about it.  That's the very first thing I noticed.

The new "Software Store", which is named under Applications as "Ubuntu Software Center" (ano ba talaga kuya ang opisyal na pangalan...) lacks a way to know if the updating of the software list hanged or what.  I ended up using Synaptic :p

Upon first login, the system immediately notified me of my Video Card driver, unlike previously I have to click here and there.  After my first reboot, I have the official nVidia driver running already.  But as usual, when opening nVidia's manager, it doesn't open via gksudo, so I have to go to the terminal and open it there.  Without going admin, the settings doesn't get saved.  I do not know if this is nVidia's part or Ubuntu's.

And of course the latest Firefox to day - 3.5.3.

So far, that's my initial report.  And as I mentioned earlier, the Alternate CD failed to detect my SATA, I have to download the LiveCD to successfully install Karmic Koala.  I was trying to find any bug report or updates to this but the last report I found was alpha6(??) and it says there "fixed for next release" - and that would mean beta.  But it isn't.  :p

I will upgrade my fresh system first, then I will start reporting bugs.  ^_^

Karmic Beta Experience since installation (that's an hour as of this writing) - **Excellent**.

Edit:
I noticed the flickering after clicking "restart" after the Installation.  I have to hard boot the system because the LiveCD just keeps on flickering, and won't accept any command (like 'Enter', since this is the part wherein the LiveCD asks for the CD to be removed).

Then I have yet to confirm the flickering I noticed during my first reboot...

---

### Post by zilu54 on 2009-10-07
Sweet! can't wait for official release ng Karmic...
curious lang aku, ok lang kung mag try pa aku ng isa pang OS sa lappy ku? (windows and ubuntu then other linux distro?)

---

### Post by guitar_man on 2009-10-07
ok lang yan...back lang ng file sir kasi minsan hindi maiwasang aksidente mong masadyang ma-delete mga partition ng HD mo...
test lang nang test..:lolflag:

---

### Post by upbeatfury@yahoo.com on 2009-10-07
Im downloading the beta ISO right now. cant wait to test this. !^^, gonna check it for more hardware compatibility and bugs.

---

### Post by gdonwallace on 2009-10-07
I've been using Karmic since alpha 6.  Can't wait for the RC to come out.  Counting it down myself.  I like it so far, and have had no problems with any of my installed apps.

---

### Post by Laibcoms on 2009-10-07
Yep, test first for hardware.  I noticed how it differs per machine configuration.

My box is:
Intel Core2Duo (which is a native 64-bit processor)
2gb RAM
nVIDIA 7300LE

Using 64-bit Ubuntu 9.10 Karmic Koala.

So far no problems on my end, re: hardware compatibility.  Most problems (and there are only a few, and mostly tolerable and rarely happens) are on the software side - being a "beta".  (Compared to other betas I am testing, Ubuntu betas break-down more often :p  Jaunty was the 'almost perfect beta' so far.)

If you are going to install it permanently, as of today, do not upgrade your Nautilus :p  There's a bug that's killing your MIME setup, everything becomes detected as a text file ;)  Follow #[Karmic](http://identi.ca/tag/karmic) on [identi.ca](http://identi.ca), that's where I found out about this Nautilus bug, so I was able to avoid upgrading to the bugged version.  (That one is annoying, so I heard :p hehe )

Karmic Beta is soo exciting LOL.  My list of stuff to report is growing!  I like that actually haha :p

---

### Post by Laibcoms on 2009-10-10
Update to my experience.

Right now, I am having problems with GRUB2 booting my Windows XP.

I logged-in to Ubuntu and typed **sudo fdisk -l**

It showed me that my PATA **secondary slave** is being detected as /dev/sda while my SATA which is my **primary & boot harddrive** as setup via CMOS is being detected as /dev/sdb

I read the GRUB2 wikipage here in Ubuntu, and it says there that /dev/sda is = hd0; /dev/sdb is = hd1; and so on.  That will mean that my SATA where my WinXP, GRUB2, and Ubuntu Karmic are installed is being detected as a **secondary** harddrive!!  And any Microsoft Windows OS doesn't like this at all.

So it fails to boot.  I get this:
error: invalid signature

Trying to search and figure out stuff still....

---

### Post by JunRamoneda on 2009-10-10
Installed Karmic into a VirtualBox VM. Tried intalling Sun java jdk. Version under Karmic is 1.6.0_15 pero sa Jaunty it's 1.6.0_16.  Sa RC kaya?

---

### Post by m3wt on 2009-10-16
been using karmic since alpha stage. I love the new look. Yung splash and login screen kick ***!! better performance in terms of boot time. I love ext4. yung ibang gamit kong linux distro na naka ext3, na upgrade ko na rin sa ext4. Karmic is the best ubuntu version so far.. 

Dont go messing around with grub2 though, especially if you're a noob. :)

---

### Post by Script Warlock on 2009-10-20
paano ba magset ng static ip address sa karmic palagi kc auto lahat kahit binago ko na setting sa network manager ganun pa rin pagboot balik uli sa dhcp at binago ko na network interface ganun pa rin....working lahat hardware ko sa jaunty.....

finally figure out during installation gusto lang pala nya dhcp tapos pagkainstall na at updated na lahat ay pwede na pala set to static ang ip. humahanap lang ako ngayon paano to e-crash ang OS para may mareport sa kanila..:P

---

### Post by ysNoi on 2009-11-09
Can't connect my Karmic on wireless..! How do I connect it pls someone help po..!

---

### Post by junex on 2009-11-09
Testing Ubuntu 9.10 Karmic Koala..! Except for some minor problems like can't play videos in youtube, which was immediately solved, so far so good!

---

### Post by perbiu on 2009-11-10
Buggy, there where issues that was solve in previous versions, and the problems are back again.

I thinks its because they are laying the foundation for the LTS version.
Having problems with network, wireless/plugin, software center, and the hdd encryption that will lock up your boot.

I think i just broke my system, i already have a perfect system on 9.04.

---

### Post by pinoyskull on 2009-12-08
Got my 30pcs Karmic CDs yesterday :)

---

### Post by Ravskie on 2009-12-08
me too i got my request CD delivered here in Kuala Lumpur :D

---

