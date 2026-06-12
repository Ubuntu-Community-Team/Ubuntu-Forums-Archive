---
title: "HOWTO: Canon iP3000 Printer"
date: 2005-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by zxc on 2005-05-21
The "Paperweight" can print.

This guide isn't ideal or perfect but it got my Canon iP3000 to work without Turboprint or anything else. So I hope it works for you.

I'm not big on Print Quality either so I wouldn't know what it's printing out as, but it Prints!

Edit: Ripped from here [http://www.linuxprinting.org/pipermail/canon-list/2004q4/001797.html](http://www.linuxprinting.org/pipermail/canon-list/2004q4/001797.html) 
But made Ubuntu Specific
--

Go to System-->Adminstration--> Printing

Then Click "New Printer"

Click "Use Printer by specifying Port"

Select USB Printer #1 (Works if you only have 1 Printer only apparently)

Click Forward

Select Canon from the Dropdown menu.

Select Model: BJC-7000

Install driver BJC 800 (recommended)

Apply

-End-

---

### Post by RastaMahata on 2005-05-21
[QUOTE=zxc]The "Paperweight" can print.

This guide isn't ideal or perfect but it got my Canon iP3000 to work without Turboprint or anything else. So I hope it works for you.

I'm not big on Print Quality either so I wouldn't know what it's printing out as, but it Prints!

Edit: Ripped from here [http://www.linuxprinting.org/pipermail/canon-list/2004q4/001797.html](http://www.linuxprinting.org/pipermail/canon-list/2004q4/001797.html) 
But made Ubuntu Specific
--

Go to System-->Adminstration--> Printing

Then Click "New Printer"

Click "Use Printer by specifying Port"

Select USB Printer #1 (Works if you only have 1 Printer only apparently)

Click Forward

Select Canon from the Dropdown menu.

Select Model: BJC-7000

Install driver BJC 800 (recommended)

Apply

-End-[/QUOTE]
 so the problem was with the drivers? bjc 7000 and bjc 800 dont sound even near to ip3000. Good tip by the way ;)

anyway, What you say about "Select USB Printer #1 (Works if you only have 1 Printer only apparently)" is true. But if you have a second usb printer, you should select USB Printer #2".
At least that what I think...

---

### Post by zxc on 2005-05-21
lol, yeah about the drivers, God Knows how the guy found that out  :roll: 

I have no idea about the USB #2 thing, just thought I'd mention it in case someone else had trouble as that might be it.  :smile:

---

### Post by mandy2tom on 2005-05-22
I have ip4000
im using s630 driver works good

---

### Post by zxc on 2005-05-24
> im using s630 driver works good

Nice to hear! I couldn't face going through all the drivers to find ones which work :P

---

### Post by veelivar on 2005-06-01
Does anybody know if any of the other drivers work for the iP1500?

Cheers,
Dan.

---

### Post by andlinux21 on 2005-06-08
[FONT=Comic Sans MS][SIZE=3][COLOR=DarkSlateGray]I have a Sony picture station any chance for some info on this one too.[/COLOR][/SIZE][/FONT]

---

### Post by rykel on 2005-07-15
I chose the BJC-7000 (with gimp-print) driver instead. It "seems" to work better than the other BJC 7000. Note the hyphen difference.

Anyway, its is disappointing that after numerous emails and letters to Canon, the company still does not have a driver for the PIXMA series... more so since they already have the Japanese versions.

But I think they will eventually come around to it!

---

### Post by Weav on 2005-09-05
Is it possible to get this to work with a network printer that is shared? I'm trying to print from a printer from a room next to mine do i need to select windows network printer?

Thanks

---

### Post by u-blunt-2 on 2005-09-27
[QUOTE=rykel]I chose the BJC-7000 (with gimp-print) driver instead. It "seems" to work better than the other BJC 7000. Note the hyphen difference.
[/QUOTE]

What difference can you notice? Is the color printing better ?

I tried installing the japanese drivers from canon, without success. The instalation seemed flawless, however when I printed something, the file was queued to the printer, then disappeared as if printed. However, nothing came out... :confused:

---

### Post by rykel on 2005-09-28
[QUOTE=u-blunt-2]What difference can you notice? Is the color printing better ?

I tried installing the japanese drivers from canon, without success. The instalation seemed flawless, however when I printed something, the file was queued to the printer, then disappeared as if printed. However, nothing came out... :confused:[/QUOTE]

i have tried printing with both the BJC-7000 and Japanese Canon iP3100 drivers now on ubuntu... but i have totally stopped this practice.

reason? it seems like with these user-self-appointed "alternative" drivers, the printer inks get drained FAST...

i use linux to print only occasionally, but when i need to print a lot, i boot into windows XP... it sucks, but then again, it's all canon's lack of support. thanks to them.

unless a very good reason exists, i now advise linux friends NOT to use canon PIXMA printers... simply coz there are no drivers!!

---

### Post by Ibbelz on 2006-01-09
Works perfect for my IP3000 printer. Thank you very much. :)

---

### Post by bradlis7 on 2006-04-03
Hm, didn't work for me. It says there's a print job, but nothing happens. Does it require a restart by chance?

UPDATE: The BJC-7004 drivers seem to work well, and I think I had selected the wrong port to begin with. I had to delete the printer and start over, so now it's working.

---

### Post by ozzymud on 2006-04-30
[QUOTE=Weav]Is it possible to get this to work with a network printer that is shared? I'm trying to print from a printer from a room next to mine do i need to select windows network printer?

Thanks[/QUOTE]
Just installed Ubuntu, went to New Printer in System, Administer, Printer, chose:

Network Printer: Windows Printer (SMB), it asked for a user/pass...

the printer is shared without a password, so i click ok with the password blank, it had my current username filled in already.

After that, i chose 'bedroom' from the Host dropdown, after a slight wait
Printer... canon,
left username and password blank... clicked forward, chose Canon: BJC 7000,

for driver it had only the listing: 

High Quality Image (GIMP-Print) (gimp-print) (Suggested)

so i click apply and there is my printer, i right click and choose properties, and printed a test page...

Worked flawlessly, out popped a very nice looking Ubuntu test page :)

I know this post was way back in 05, but the one that suggested BJC7000 was even older and it helped me a ton! So i figured id post the steps i took and answer your question that YES it will work fine for a shared winblows printer :)

---

### Post by LeeM on 2006-05-11
Boo hoo!:( 

I just bought an IP3000 (partially because of the relative success folks here have had on interfacing it with Ubuntu. I used the Canon BJC-7000/800 driver approach mentioned earlier.

The printer works fine for black printing. Unfortunately, it doesn't work worth stink as a color printer. When I try to print a photo, for instance from OpenOffice, or any other application I've tried so far, the results are terrible. I don't know how to describe what is happening, except to say it looks like the result if you tried doing a coloring book, when you had only 4 crayons.

The Printer Test Page (from CUPS) looks great - the color wheel is super.

I tried changing the settings (draft, regular, etc.) to no avail. Any suggestions what to try next (short of returning the printer!)

Thanks for any help!

---

### Post by ursa_major on 2006-11-02
Don't be discouraged! I was about to do the same thing, to give up, but I kept on reading an finally it works! 

Just choose BJ7000 High quality image, Gutenprint. I will need to further adjust some parameters in the driver but trust me, it is worth to spend 15min doing this. The result, able to print in 600x600 and 300x300, the color is good, there is only some missing fractions of an inch to the right hand side but it is not so bothering after all. One remark though, the test page looks odd, but I printed a couple of pictures and they look acceptable to me. It is not so good as Windows driver may print, but for regular use, works for me.

Good luck!:)

---

### Post by blackdalek on 2007-01-21
Just thought I'd mention for other pixma users who come across this thread, that none of these driver combinations suggested work properly for me with my Canon Pixma IP3000 USB printer. Colour prints wrong or pages print quarter size.

I suggest the title of this thread be changed to something more appropriate such as "Partially working drivers for Canon iP3000". Unsuspecting thread browsers may be lead to believe there is a working "HOW TO:" in here. There isn't.

---

### Post by beaulanger on 2007-01-27
> **mandy2tom said:**
> I have ip4000
im using s630 driver works good

Thank you so much.:D 
The S630 driver worked for me with my ip3000. After trying quite a few of them your tip worked for me.

---

### Post by dvarsam on 2007-01-29
[QUOTE=blackdalek]Just thought I'd mention for other pixma users who come across this thread, that none of these driver combinations suggested work properly for me with my Canon Pixma IP3000 USB printer. **Color prints wrong or pages print quarter size.**[/quote]

This is another one of those Threads where some people say:

1. Thank you very much, it works great!!!

And others say:

2. What the "heck" are you talking about?
The **Color prints wrong**!!!
(of course, nobody responds to your claim, because it wouldn't look good to do so... unless you ask specifically for a response... only then the truth is revealed... and it is something like: "well I did NOT care for color printing at all... or ... I didn't notice that...)

And this is to be repeated "infinitely"!!!
I sometimes wonder:

**Are people getting paid to give misleading info on how things work, even though in reality they don't?**

[quote=dvarsam]Sorry man, but whenever I propose an improvement, I get the following response:

But things already work great the way they are!!!
The world is fantastic & the earth is looking fit!

And I respond:

Really?
Please tell me what program to use...?

And I get:

Sure, use either this program or that one...

And I response:

Sure, but how do you make it work?
I am getting errors...
I can't do this & can't do that...

Response:

NONE!!![/quote]

_Conclusion_:
* Ubuntu rocks & Everything is looking great!
* There are programs with which you can do everything you want...
* Everybody will suggest to you what programs to use...
* And when you find that you are stuck in configuring your program & ask for help, everybody will be running for the "Emergency Exit"...!!!
* IF you ever attempt to suggest an improvement for a program... it already exists! - don't bother to suggest anything!... use some suggested program, as it will always be much better compared to your suggestion for improvement... Your suggestion is too complicated & requires too much code, not to mention waste of resources, etc etc...
* IF you try to use a suggested program & can't figure out why it is NOT working, and ask for help... don't bother to do so... cause everybody will be running for the "Emergency Exit"...!!!
* You are back on your own again!
* Good Luck!

[quote=blackdalek]I suggest the title of this thread be changed to something more appropriate such as "Partially working drivers for Canon iP3000". Unsuspecting thread browsers may be lead to believe there is a working "HOW TO:" in here. There isn't.[/QUOTE]

You wish!!!
Everything is misleading in Linux...
Its all marketing...
Well, except one thing...
**That Linux is a more safe OS compared to Windows.**
At least we have something...
It is like owning a car, but:

1. You can't play the Radio, cause it requires configuration
2. You can't turn the steering wheel, cause it requires configuration
3. You can't open the trunk, cause it requires configuration
4. etc etc

Thank God:

5. You can put gas,
6. And you are lucky your can _only_ steer forward & backwards!

So, other than security, the rest _still_ sucks...

Thanks.

P.S.> I know that by writing this, I will be thrown eggs/attacked instantly, but lets accept the plain truth, shall we?
i want my Ubuntu to improve too - I hope it does NOT take ages though...
Cause I will be looking at the world from "under-ground" by that time... :)

---

### Post by dachinster on 2007-05-19
this actually worked great for me in feisty fawn. it saw the canon pixma ip3000 with just a simple "add new printer" and i did not have to do any configs or add any miscellaneous drivers!!

---

### Post by ramadhian on 2007-10-16
New Repo for Canon Printer Driver

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

---

### Post by MidSpeck on 2009-07-16
Replying to an old thread... but with a solution that worked for me:

I was having the problem of Ubuntu only printing out on the upper-left quarter of a page (only I was having it on an HP LaserJet 1012).  It would print out the whole page, it would just look like it was 25% of the size it was supposed to be.  Same with the test pages.

My fix was as follows:
System > Administration > Printers
Select the printer > Job Options tab
My "Pages per side" was set to 4, instead of 1.

---

### Post by rykel on 2010-10-08
After almost HALF A DECADE, I believe there is still NO Linux driver for the Canon PIXMA iP3000. This is just like those WinModems... we should call these cursed devices WinPrinters.

Which, of course, will eventually be forgotten in the ashes of printing history and nobody in the world of Linux would cry for them.

Time to support BROTHER and HP printers more!

---

