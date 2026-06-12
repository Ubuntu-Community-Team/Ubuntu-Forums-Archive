---
title: "Whats the Best Spec For  New Ubuntu Linux PC?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by sharkster2007 on 2008-12-02
Hello again

My PC is getting way out of date now an considering upgrading (Must be Linux compatible)

For best Ubuntu Linux support (near 100%) whats the best type of:

SATA Motherboard
RAM         (I assume any would do)
DVD-R/+R    (Again I assume any would do)
Harddisk    (Would SATA work with Linux)
Blue-ray    (If possible)
Video Card  (Is ATI 3D support in Ubuntu as standard? because Iam very annoyed at the Nvidia "farce" over "open-source" and stupidly difficult to set up for newcomers without relevant .deb files)
Wireless Card
Firewire

I wish to migrate fully from windows and need my PC as a desktop/entertainment pc (thought not for 3D games)

Thanks Again

---

### Post by Paqman on 2008-12-02
> **sharkster2007 said:**
> 
SATA Motherboard


All motherboards have SATA these days. It's support for IDE devices like optical drives and old HDs that can be in fairly short supply. A lot of boards only have one IDE connector.

As for brands, i'd recommend Intel, and some others report good results with Gigabyte. Always check before buying a mobo though, search these forums under the model number to see if people have had issues, as even good brands can put out some dodgy cards.

> 
RAM         (I assume any would do)
DVD-R/+R    (Again I assume any would do)
Harddisk    (Would SATA work with Linux)


Any of these would be fine. Compatibility isn't an issue.

> 
Blue-ray    (If possible)


Good question. I have no idea.

> 
Video Card  (Is ATI 3D support in Ubuntu as standard? because Iam very annoyed at the Nvidia "farce" over "open-source" and stupidly difficult to set up for newcomers without relevant .deb files)


Actually it's Nvidia that support open source much better. Definitely get an Nvidia card (although some ATI cards are usable)

> 
Wireless Card


Again, Intel is a good bet. Stay away from anything with a Broadcom chipset.

> 
Firewire


Firewire is normally built into your mobo these days.

---

### Post by philinux on 2008-12-02
My desktop setup works just fine. The nvidia deb package is in synaptic, no probs at all.

---

### Post by xmango on 2008-12-02
One of the best things about the Ubuntu platform is that it does not take a super computer to be able to run it.  Any 2003 model clunker sitting in the corner can get the job done.  But to give you an answer what are you doing with it?  You said no games so if not, then any machine with 2-3GB of RAM and a decent HDD will work.  A duel core processor is also very nice.  I would however recommend a duel core processor and 4GB of RAM on perhaps an ASUS board like the MS32-SLI Deluxe.  Then you can run the x64 operating system, but as I mostly use command line, I am not sure what the added benefit would be to you in a GUI.

---

### Post by xmango on 2008-12-02
Agreed with the poster two up.  HH or 8.10 should be able to install your card by default.  You will just need to enable the card to work on your system, which is easy because a hardware manager pop-up will come and ask you :)

---

### Post by xikarrousx on 2008-12-02
****... my 1998 model handles it! if you are going cheap though, get lots of ram!

---

### Post by sharkster2007 on 2008-12-02
Thanks for info paqman, with regards to philinux: > My desktop setup works just fine. The nvidia deb package is in synaptic, no probs at all.

I have the Nvidia 177 package installed via .deb files it is faulty and displays the "titlebar glitch" often, the solution is Nvidia 180 that is not yet available as a .deb package (Only as a .run which is virtually impossible to run for new users without getting a "black screen of death" hence the "farce" I was refering to above)

With regards to xmango, I understand some users prefer the "command line", but i myself am a newbie trying to migrate from Windows i am proficient with ms-dos but consider text commands a "step backwards" compared to GUI based applications when a newcomer is considering migration to ubuntu from WindowsXP (the last time I had to use MS-DOS on windows xp must have been over several years ago. though I do understand the advantage performance gain wise).

Desktop wise: Is it worth getting a graphics card other than ATI/NVIDIA like INTEL so that 3D support could be included "out of the box" so to speak?

*Just had a thought something like an eee-pc or aspire one may do for what i want, audo & video playback, wordprocessing, graphics, a little bit of video editing*

Current PC: Pentium 4 2.4ghz, 1gb ram, x2 IDE hardisks, x1 Firewire Hardisk, DVR -R/+R, NVIDIA 6600GT (AGP)

---

### Post by philinux on 2008-12-02
I've heard about this title bar glitch. How does it appear? I've had some odd stuff, occasionally, when opening apps like a mish mash display for half a second before it renders properly.

---

### Post by binbash on 2008-12-02
> **Paqman said:**
> (although some ATI cards are usable)


What do you mean with SOME? Yes nvidia's driver is better at linux, i also suggest getting a nvidia card BUT most(probably all) ati cards are usable and works good with compiz etc.

---

### Post by SamNSane on 2008-12-02
As a user of Ubuntu 8.04.1 on three systems -- one with a high end nVidia graphics workstation card, one with a middling ATi integrated solution, and one with a lower end Intel integrated video subsystem -- I've got to say that your choice in graphics subsystems depends very much on what you plan to use the system for.

A lot of people love nVidia because they were very cooperative about putting out decent drivers for Linux early on. However, their adherence to closed source development of their drivers is causing no end of trouble to many users of their products. AMD/ATi and Intel have stepped forward and joined in the spirit of Open Source development. If you're looking for an easy experience out of the box, be very careful of what you choose. But be particularly careful of the model you choose if it's nVidia. Because, if you happen to get one of their cards that isn't working well under Linux, you're likely to wait quite a bit longer to see a resolution (if any) to your problems. And in the meantime you'll be depending pretty much on hearsay at nvnews or another nVidia user hangout for help. That has been my experience, and it is the reported experience of a number of people over at nvnews.

In the meantime, my low-end Intel integrated graphics on a subnotebook, and the standard ATi graphics on my cheap Dell Optiplex both outperform the expensive Quadro graphics subsystem on my workstation. Worth thinking about.

---

### Post by Izek on 2008-12-02
> **binbash said:**
> What do you mean with SOME? Yes nvidia's driver is better at linux, i also suggest getting a nvidia card BUT most(probably all) ati cards are usable and works good with compiz etc.

Yeah, my ATI Radeon HD 3200 (Integrated) doesn't work very well in Intrepid, it works better in Hardy, even Windows has a little trouble with it. :(

---

### Post by celticbhoy on 2008-12-02
I use an Aspire One 120G with 8.10 dual booting with the pre-installed linux and it works fine, a couple of small setups to get everything going as it should but nothing difficult and all well documented.

---

### Post by theozzlives on 2008-12-02
my DVD/CD +/- R/RW on my laptop supports Blue Raye with an adapter, you might see if they have that for a desktop.

---

### Post by forkandles on 2008-12-02
Make sure a good quality psu is at the top of your list (e.g Seasonic, Corsair or Antec) and not just an afterthought (see below).
Do not get carried away by high wattage figures. Look here for what power you actually need.  Doubtful if you need more than 380w or 430w.
[http://www.thermaltake.outervision.com/](http://www.thermaltake.outervision.com/)

I recommend: 
CPU     AMD Athlon 64 5400 x2 (2.8 MHz) or 4600 x2 (2.4MHz) Lots of good reliable, inexpensive umph.

RAM    4GB Corsair 6400DDR2 XMS2 or similar (800MHz) 4-4-4-12 (alternatively, 5-5-5-15) Excellent quality with a lifetime guarantee. High performance RAM needs to run at 2.1v or more (not 1.8 or 1.9v). Consult the mobo manufacturer and increase the default voltage in the BIOS, one stick only for starters.

MOBO  Gigabyte GA-MA770-DS3 AMD 770 Socket AM2+ 8 channel audio ATX
Very good quality and loves Linux.
A lot of Northbridges run hot but do not worry. I use a Noctua NC-U6 chipset cooler and everything runs fine.
[http://www.overclock3d.net/reviews.php?type=3&id=161&page=1&desc=noctua_nc-u6_chipset_cooler](http://www.overclock3d.net/reviews.php?type=3&id=161&page=1&desc=noctua_nc-u6_chipset_cooler)

CASE & PSU combo   Antec NSK6580 or Antec4480 (430w/380w) Well made cases and good psus.
EDIT  Newegg are doing the Antec NSK6580 with 430w PSU for $79.99!! Buy now while stocks last!

HDDs Samsung SATA or whatever else takes your fancy

DVD RW Samsung, LiteOn, LG, Sony SATA

GRAPHICS CARD     Definitely nvidia    (be guided by others on here but I find XFX very good). If possible, get a fanless one for quietness, unless you are a headbanger!

Case Fans   Akasa Ultra Quiet Amber 120/92

Arctic Silver 5 Paste

---

### Post by Paqman on 2008-12-02
> **forkandles said:**
> 
GRAPHICS CARD     Definitely nvidia    (be guided by others on here but I find XFX very good). If possible, get a fanless one for quietness, unless you are a headbanger!

Case Fans   Akasa Ultra Quiet Amber 120/92

Arctic Silver 5 Paste

+1 on all that, noisy graphics cards suck.

I'd also spend a few bucks on a decent cooler for the CPU. It's the hottest and most expensive component in the machine, and it's worth spending money to cool it properly. The aftermarket fans are a lot quieter and better built than the stock ones. The new Zalman 9300ATs are excellent, not too massive, and fit onto pretty much every CPU so you can switch it into your next box.

I wouldn't go too crazy with cooling/quietening though. Some people go beserk, but once you've got a silent graphics card, decent CPU cooler and some quiet case fans I think you've won 90% of the battle IMO.

---

### Post by sharkster2007 on 2008-12-03
In reply to philinux,

Sorry about the delay the "Titlebar Glitch" makes the window titlebar (usually orange) go grey and makes window title unreadable, after moving around a bit it comes back, a minor issue but very annoying (also makes us look bad when comparing with windows)

---

### Post by nhasian on 2008-12-04
i'd like to weigh in.  I dont know what your budget it like, but i prefer to use Intel processors and Nvidia graphics cards.  If its in your budget i highly recommend Intel's new i7 Core chipset.  its quad core with hyperthreading enabled!  you can have 8 threads at once :KS super fast.  ram is sold in sets of three for this chipset so you can do 3 gigs and run a 32bit OS or 6 gigs if you want to run the 64 bit OS instead.

---

### Post by I wanted to leave on 2008-12-04
I got caught out with a Gigabyte m/b (81932) that uses specific proprietary drivers for usb ports. Its a few years old now but I haven't forgotten yet to replace it with an Intel board when the time comes.

---

