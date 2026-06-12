---
title: "gfx card for old mobo"
date: 2008-02-27
forum: Other OS Talk
---

### Post by themuddaload on 2008-02-27
ok, this has purt near zero to do with linux. (except it would make it run better)

i have a quite old computer (it was not new when my dad got it quite some time ago) it has a celeron 633mhz processor, and 256mb of ram(maxed ram) 
this is what the pdf dad gave me for the mobo user manual said it is.
"Mainboard MS-6178MICROATX WH5           Version 1.0C"

ok, so what i want to do is find an older, but gutsy (very cheap = good) graphics card for this computer, i do not forsee me getting a new computer very soon, so slapping a 128mb (or anything other than the built in for that matter) graphics card on it would make it alot better for the games i like to play on it.

i am not an expert, and so i come to yall, as i know that many of you are.
thanks.

- me

---

### Post by fwojciec on 2008-02-27
If I've managed to find the correct info about the mobo in question -- it looks like it needs a card with a regular PCI slot (not PCI-Express).  Here is what [newegg ](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642&name=PCI) has to offer in terms of video cards with this slot...  I don't know any of these cards well enough to give you a specific recommendation -- avoid ATI (which probably means "go with Nvidia") is the best I can do.  The specific model shouldn't really matter -- it's not like you're going to play Crysis on that system...

---

### Post by themuddaload on 2008-02-27
> **fwojciec said:**
> If I've managed to find the correct info about the mobo in question -- it looks like it needs a card with a regular PCI slot (not PCI-Express).  Here is what [newegg ](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642&name=PCI) has to offer in terms of video cards with this slot...  I don't know any of these cards well enough to give you a specific recommendation -- avoid ATI (which probably means "go with Nvidia") is the best I can do.  The specific model shouldn't really matter -- **_it's not like you're going to play Crysis on that system..._**

party pooper =)

---

### Post by themuddaload on 2008-02-27
why is ATI bad? i dont have any experiance with graphics cards, so it  would be nice to know.

---

### Post by ryanhaigh on 2008-02-27
ATI has poor driver support for linux, they are improving but nvidia is still ahead. I ran compiz with a FX5200 a while back with no issues although mine was an AGP card.

---

### Post by themuddaload on 2008-02-27
oh, i see, he was referring to its inability to work on linux.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289) 

does this one look good? looks like a good one to me for $40 after rebates

---

### Post by ryanhaigh on 2008-02-27
the user reviews look good as long as its compatible with your board. you might be able to find older benchmarks comparing the 5 series with the 6200 as unfortunatley getting a higher model number doesn't always mean you are getting higher performance.

---

### Post by jinx099 on 2008-02-27
Does that motherboard have an AGP slot?  If so, you can find a 6600GT (AGP) on craigslist or something for around $20 if you look hard enough.

---

### Post by ryanhaigh on 2008-02-27
as mentioned by fwojecic and the manual for the board [here]("http://www.google.com/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fwww.fujitsu-siemens.co.uk%2Frl%2Fservicesupport%2Ftechsupport%2FBoards%2FMotherboards%2FMicroStar%2FMS6178%2FManual%2FUser%2520Manual%25206178c-.pdf&ei=HA_GR8DAMpm2pgTu6v0E&usg=AFQjCNGywRn8fuEAMWczvrq5lFk7TDlSzA&sig2=qHRsozIbIfi7kR04D_n8kw") the board doesn't have a dedicated graphics slot. While the PCI options are obviously inferior (particularly for flooding the PCI bus) they are still better than integrated for gaming.

---

### Post by jinx099 on 2008-02-27
> **ryanhaigh said:**
> as mentioned by fwojecic and the manual for the board [here]("http://www.google.com/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fwww.fujitsu-siemens.co.uk%2Frl%2Fservicesupport%2Ftechsupport%2FBoards%2FMotherboards%2FMicroStar%2FMS6178%2FManual%2FUser%2520Manual%25206178c-.pdf&ei=HA_GR8DAMpm2pgTu6v0E&usg=AFQjCNGywRn8fuEAMWczvrq5lFk7TDlSzA&sig2=qHRsozIbIfi7kR04D_n8kw") the board doesn't have a dedicated graphics slot. While the PCI options are obviously inferior (particularly for flooding the PCI bus) they are still better than integrated for gaming.

I dont see where fwojecic said anything about AGP.  :confused:

Decent PCI cards for gaming are going to be very hard to find unfortunately.  The 6200 looks to be your best bet, and the one posted looks like a pretty good deal.  It should be able to run compiz on it too.

---

### Post by themuddaload on 2008-02-28
is this the 6600gp thingy you are talking about? [here]("http://www.nvidia.com/page/geforce_6600.html")

---

### Post by themuddaload on 2008-02-28
oh, my comp is running win 98, incase it needs 2000/ xp like the one i just saw on ebay does.
if that is listed on the requirements, will it not work on 98?

---

### Post by mips on 2008-02-28
> **themuddaload said:**
> is this the 6600gp thingy you are talking about? [here]("http://www.nvidia.com/page/geforce_6600.html")

That will NOT work on your motherboard as it is only available in PCI-E & AGP according to the site.

I do not think you will get anything better than a GForce 6200 in PCI configuration. These are your options:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+1305520548+106790703&name=GeForce+6+series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+1305520548+106790703&name=GeForce+6+series)

WIn98 drivers for the above cards are here:
[http://www.nvidia.com/object/win9x_81.98.html](http://www.nvidia.com/object/win9x_81.98.html)

---

### Post by K.Mandla on 2008-02-28
> **mips said:**
> I do not think you will get anything better than a GForce 6200 in PCI configuration. 
Yup. I used to have one of those 6200s and they work well enough. That might be a little overkill for a 633Mhz Celeron, but if you're willing to buy a new card, you might as well go for it.

I'd suggest an old FX-series card or even a Geforce4 if you want one cheap. I can run Compiz on a 1Ghz Pentium 3 and a 64Mb Geforce4 440 Go at 1600x1200, just to give you an idea of it's ability.

And don't be afraid of an ATI card. You're not buying cutting edge so driver issues will be less frustrating. My XPress Radeon 200M is a lot better than it was two years ago, so something to match that hardware should be fine. ...

---

### Post by rustybronco on 2008-02-29
> **K.Mandla said:**
> 
I'd suggest an old FX-series card... I second the opinion, I use a MSI fx5900xt (128meg-agp, bought used) @ 1440x900 resolution and I am very pleased with it. but stay with a good brand card no matter what you buy.

---

### Post by themuddaload on 2008-03-01
> **mips said:**
> That will NOT work on your motherboard as it is only available in PCI-E & AGP according to the site.

I do not think you will get anything better than a GForce 6200 in PCI configuration. These are your options:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+1305520548+106790703&name=GeForce+6+series](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609642+1305520548+106790703&name=GeForce+6+series)

WIn98 drivers for the above cards are here:
[http://www.nvidia.com/object/win9x_81.98.html](http://www.nvidia.com/object/win9x_81.98.html)

yeah, those are kind a spendy though in comparison to what id be looking to spend

---

### Post by themuddaload on 2008-03-03
question: what are RAMDACs

---

### Post by mips on 2008-03-04
[http://en.wikipedia.org/wiki/RAMDAC](http://en.wikipedia.org/wiki/RAMDAC)

---

### Post by themuddaload on 2008-03-20
ok, question, WHY ARE AGP CARDS LIKE HALF THE PRICE OF PCI'S !?!

looking for cheap PCI ones makes me sad when i see the same thing for like $5 in the agp configuration.

---

### Post by mips on 2008-03-20
It's a matter of supply and demand. PCI gfx cards are old and no longer produced. It's the same as old ram, you are going to pay more for it simply because it is no longer as freely available as the new stuff. It has nothing to do with technology but it has to do what the market has on offer.

---

### Post by themuddaload on 2008-03-21
aah. i kinda figured it was something along those lines. anybody happen to know what the site is that popsci is always getting older computer parts for dirt cheap? my mommy made me throw away my older issues, so i only have like 3, and they don't have the site listed.

=(

---

### Post by themuddaload on 2008-03-21
ah yes, and i'm thinking that these look like good options if i can find one for $25 or so.

EVGA 128-P1-N298-LX GeForce FX 5200 128MB 64-bit DDR PCI Low Profile Video Card - Retail 

XFX PVT64KNTFG GeForce FX 5200 128MB 64-bit DDR PCI Video Card - Retail

from newegg, any known probs with either of these?

---

### Post by BigSilly on 2008-03-22
I've got a new card on the way for my PC, so I'll be getting rid of my old Geforce FX5600XT. It's an AGP card, and may need a new fan, but if you live in the UK I don't mind sending it to you once I set up my new card OK. Shouldn't cost too much to post in the UK, so I'd rather send it to someone who's going to find it useful than throw it away. Let me know what you think.

---

### Post by mips on 2008-03-22
> **BigSilly said:**
> I've got a new card on the way for my PC, so I'll be getting rid of my old Geforce FX5600XT. It's an AGP card, and may need a new fan, but if you live in the UK I don't mind sending it to you once I set up my new card OK. Shouldn't cost too much to post in the UK, so I'd rather send it to someone who's going to find it useful than throw it away. Let me know what you think.

Nice of you to offer but he needs a PCI video card and not AGP, unless he upgrades the MB to one with a AGP slot :)

---

### Post by Extreme Coder on 2008-03-22
Actually, the no ATI rule wouldn't work here, since:
- ATI's latest drivers are actually pretty good
- Most of the ATI cards with PCI are well supported with the OSS driver, which instantly means no hassles :)

---

### Post by tad1073 on 2008-03-22
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133007](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133007)

---

### Post by BigSilly on 2008-03-22
> **mips said:**
> Nice of you to offer but he needs a PCI video card and not AGP, unless he upgrades the MB to one with a AGP slot :)

Oh I see. I didn't read the whole thread, so thanks for that. Still, I've got my new card up and running anyway...

---

### Post by mips on 2008-03-22
> **BigSilly said:**
> Oh I see. I didn't read the whole thread, so thanks for that. Still, I've got my new card up and running anyway...

You never know, there might be someone else out there that needs an AGP car :)

---

