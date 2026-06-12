---
title: "Need answers on ATI Radeon vid card and Ubuntu"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by mal1958 on 2012-03-16
I am going to be finally upgrading to a better system and need some help here.  I have heard horror stories of Linux and the ATI chips, and need to find an answer.  Here is the first part of the message on my "hopeful" new system.

> Gateway DX4320-02e AMD Phenom II X4 820 2.8GHz, 6GB DDR3, 640GB Hard Drive, DVD±RW, Windows 7 Home Premium 64-bit Desktop PC. Get powerful yet affordable quad core, advanced memory and graphics to fuel your multimedia demands with the Gateway DX4320-02e Desktop bundle. The all-new Genuine Windows 7 Home Premium operating system, providing the latest in responsiveness and reliability, is paired with an AMD Phenom™ II X4 processor. Graphics come care of an integrated ATI Radeon™ HD 4250. With a 640GB hard drive, 6GB DDR3 1333MHz RAM, 300w power supply, Gigabit Ethernet, media card reader, usability touches like the digital device holder and photo frame button, you'll be able to free your creativity as you blaze through your digital media projects.

  I need to know if the ATI Radeon HD 4250 will work with Ubuntu out of the box, or do I have to look forward to some hoop jumping?  If it seems to much a problem, does anybody have any ideas what Nvidia cards can be put into the PCI-e socket that will work?  keeping in mind that at this time I will have a 300 Watt PSU and no PCI-e cable on the PSU.  Thanks a bunch.

[[COLOR="Blue"]Here is a link[/COLOR]]("http://www.ascendtech.us/gateway-dx4320-02e-windows-7-desktop-pc_i_pcgwdx432002ew7.aspx?agent=pricewatch") to the whole page with the system specs.

---

### Post by Bucky Ball on 2012-03-16
People don't seem to be having a problem with it. Have a look through here:

[http://au.search.yahoo.com/yhs/search?p=Radeon+HD+4250+ubuntu&fr=altavista&fr2=sfp&iscqry=](http://au.search.yahoo.com/yhs/search?p=Radeon+HD+4250+ubuntu&fr=altavista&fr2=sfp&iscqry=)

---

### Post by Mark Phelps on 2012-03-17
I have an onboard HD 4290 -- and it works just fine with the default Open-Source Radeon drivers in Ubuntu 11.10.  I would expect that a 4250 would work just the same.

---

### Post by mastablasta on 2012-03-17
problem are with some older cards that do not have good opensoruce driver support yet (usually mobility and some from the X series) and the newest ones which use proprietary drivers but they might not be ready for linux yet. but all in all ATI works just as well i believe. i mean they even got linux support for hybrid graphics now.

---

### Post by mal1958 on 2012-03-17
Thanks for the response here.  I would also like to know if anybody has had any experience with the Sparkle Nvidia 9400gt.  It is said to require a 300 watt power supply and that is the baseline for the system I am looking at.  Main reason I am now asking this is that I discovered that a game I would be playing (maybe) in windoze called Sims 3, dislikes most of the ati cards.  If I get this card [[COLOR="Blue"](Click here)[/COLOR]]("http://3btech.net/spnvge941gbp.html") will Ubuntu work with that one too? I know that most Nvidia cards will work with Ubuntu due to the great support of the Nvidia folks in seeing that drivers are provided, but I still am a bit leary on this one.  It is a newer card, and I don't know if the drivers are out for it yet, or there are any issues.  I will be using 10.04 to start and upgrading once I can figure out workarounds for the sound problems with the higher versions of Ubuntu.  And also find out if I can still use my favored Gnome desktop with the newest of the versions without much problems.



 My brother thinks I am crazy for trying to build a system to work with, in his words, a pathetic attempt at a windoze wannabe.

---

### Post by Bucky Ball on 2012-03-17
Man, try googling some of this stuff before posting. Please read the second line in my signature at bottom of this post. 

[http://au.yhs4.search.yahoo.com/search;_ylt=A7exU8L9SmVPQ1wALXU36At.?p=Sparkle%20Nvidia%209400gt%20ubuntu&fr2=sb-top&fr=altavista&rd=r1]("http://au.yhs4.search.yahoo.com/search;_ylt=A7exU8L9SmVPQ1wALXU36At.?p=Sparkle%20Nvidia%209400gt%20ubuntu&fr2=sb-top&fr=altavista&rd=r1")

... and from nvidia site:

[http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.20-driver.html)

Yes, supported! Took me two seconds to find out. No doubt you will be offered the drivers on the first update if not already in the kernel.  ;)

---

### Post by mal1958 on 2012-03-18
> **mal1958 said:**
> Thanks for the response here.  I would also like to know if anybody has had any experience with the Sparkle Nvidia 9400gt.  _It is said to require a 300 watt power supply and that is the baseline for the system I am looking at._  



> **Bucky Ball said:**
> Man, try googling some of this stuff before posting. Please read the second line in my signature at bottom of this post. 

Yes, supported! Took me two seconds to find out. No doubt you will be offered the drivers on the first update if not already in the kernel.  ;)

Thank you, Bucky.  The links were informative concerning the support part, which in spite of the "main thing" notice was but a secondary bit of rambling.  For that I apologize.  Despite the secondary ramblings I did concerning the drivers and such, I was more interested in finding if the power requirements would be enough.  I have dealt with google and techy forums before and come away more confused then when I went there.  I figured that somebody here, on this forum, might have had a similar setup and could help me figure out if I would Need to upgrade the PSU or could get away with the 300 watt one for a bit.  

   I noticed a while back that all the folks here use a wide variety of system configs and figured that I stood a better chance of finding the info here.  When I did google for "that information"  I got a ton of sales notices but not much in the easy to read knowledge category.  While I know a bit about computer hardware, I still have much to learn.  And at 53 I learn slowly :p    The blurb on the Nvidia specs site for the 9400GT 1 gig card, it did say that a min power requirement was 300 watts.  However I do know that sometimes things may be a bit different.  I was hoping that somebody here had a similar situation and could have advised me as to whether I would be required to upgrade the PSU.  Money is a bit tight now.

---

### Post by Bucky Ball on 2012-03-18
Here's one opinion:

> ... the 300-watt power supply will have to be upgraded  if you plan to add more components, particularly if you upgrade to a  discrete graphics solution. ... from [HERE.]("http://www.pcmag.com/article2/0,2817,2365877,00.aspHERE")

The PSU is probably a generic silver box (can't seem to find what brand it is) so I would immediately upgrade that to start with. 500Watt would be ample, look for 85+ efficiency rating and 600, 000 hours life cycle at least. There are better. A good PSU will also have safety switches built in. What good's the box if the generic PSU takes out the components in it?

You could build better for the price if you're game ... ;)

---

### Post by mal1958 on 2012-03-18
> **Bucky Ball said:**
> Here's one opinion:

... from [HERE.]("http://www.pcmag.com/article2/0,2817,2365877,00.aspHERE")

The PSU is probably a generic silver box (can't seem to find what brand it is) so I would immediately upgrade that to start with. 500Watt would be ample, look for 85+ efficiency rating and 600, 000 hours life cycle at least. There are better. A good PSU will also have safety switches built in. What good's the box if the generic PSU takes out the components in it?

You could build better for the price if you're game ... ;)

The price of 359.00 For what is offered seems to be a good deal (BTW the price there includes shipping)  I tried to build a slightly better and came up well over the price.  I Need some of the stuff the system offers and think that I can hold off for 3 - 4 months to upgrade the power supply.  I noted on the Nvidia site it said that the minimum Power supply needed was 300 watts for the 9400 gt.  I simply wanted to know if I could get away with using the card, or would one of the GeForce 7 or 8 series do a good enough job till I could get the new power supply. I have been saving money doing things around the neighborhood, since I do not have a job at this time.  In a few weeks I will have the needed funds to get the system.  I have also been looking at PSU's on [[COLOR="RoyalBlue"]pricewatch.com[/COLOR]]("http://www.pricewatch.com/")as well as vid cards and the like.  I wish to thank you for your help.  You, like so many folks here, show that the Ubuntu community is the friendliest there is, as well as the most helpful.

---

### Post by Autodave on 2012-03-18
> **mal1958 said:**
> I am going to be finally upgrading to a better system and need some help here.  I have heard horror stories of Linux and the ATI chips, and need to find an answer.  Here is the first part of the message on my "hopeful" new system.



  I need to know if the ATI Radeon HD 4250 will work with Ubuntu out of the box, or do I have to look forward to some hoop jumping?  If it seems to much a problem, does anybody have any ideas what Nvidia cards can be put into the PCI-e socket that will work?  keeping in mind that at this time I will have a 300 Watt PSU and no PCI-e cable on the PSU.  Thanks a bunch.

[[COLOR=Blue]Here is a link[/COLOR]]("http://www.ascendtech.us/gateway-dx4320-02e-windows-7-desktop-pc_i_pcgwdx432002ew7.aspx?agent=pricewatch") to the whole page with the system specs.

Having assembled / built / repaired many systems, I can say that the ATI cards will work "out of the box."  However, if you are looking for a high-performance card, go with the Nvidia.  With the drivers available from Nvidia, you can get the most from your Nvidia card.  With an ATI card, it will work, but you will NOT get the most from a higher performance ATI card.

---

### Post by Holdolin on 2012-03-18
You're 4250 should work just fine.  My 5870 works great out of the box, as does my 42xx onboard GUP on my test box.

---

