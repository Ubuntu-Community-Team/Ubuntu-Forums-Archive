---
title: "Legallity libdvdcss / w32codecs"
date: 2011-03-28
forum: Recurring Discussions
---

### Post by mutrax on 2011-03-28
Well the title says it all. I found some old threads that are a bit vague and inconclusive.

The reason I'm asking is because I'll be rolling out a shop, selling Ubuntu systems that of course should "just work". 

Making things "just work", implies that libdvdcss2 and w32codecs should be installed (among others). 

I'm trying to prevent that somewhere along the road (after lots of sales), someone pops me a lawsuit. 

I contacted a law firm to figure this out by Belgian/European law, but as you might have guessed, they don't come cheap.

So just to be sure, did anyone else figured this out before me? Or can I find some interesting lecture around this topic? This would allso help them figure this one out to.


_Any_ relevant input will be much appreciated!

---

### Post by rgb1701 on 2011-03-28
The EU does not generally recognize software patents, so I don't think you should have an issue.

[http://en.wikipedia.org/wiki/Software_patent](http://en.wikipedia.org/wiki/Software_patent)

In any case, it is trivial for the user to install these by copy/pasting three lines into a terminal-

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

<copy>
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
<paste>

<copy>
sudo apt-get install libdvdcss2
<paste>

<copy>
sudo apt-get install w32codecs
<paste>

or make a single script they can double click that does all three at once when they get home ;)

---

### Post by realzippy on 2011-03-28
If your company's headquarter was in Finland,it would be alright at least
for libdvdcss2...
[URL="http://www.turre.com/2007/05/finnish-court-rules-css-protection-used-in-dvds-ineffective/"]Finnish court rules CSS protection used in DVDs &#8220;ineffective&#8221;
[/URL]
...and there is a lawyer claiming this was EU-wide.
Also you could install a big,fat button on the Desktop linking to Ubuntu restricted extras..should be another legal relevance ..


BTW,not really a support question,should be moved to the cafe...

---

### Post by SeijiSensei on 2011-03-28
You couldn't do this in the US, but it has nothing to do with software patents.  Installing libdvdcss2 violates the "[anti-circumvention]("https://www.eff.org/issues/dmca")" clause in America's Digital Millennium Copyright Act.  It's illegal to distribute any device (including software) that is designed to disable or otherwise defeat a copy-protection method applied to copyrighted software.

You're in Belgium, so this obviously doesn't apply to you, but the [European Union Copyright Directive]("http://www.euro-copyrights.org/index/13/52") might.  Read the page at that site on Belgium, too.  

Software patents matter when it comes to other things like the [MP3]("http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues") and [H.264]("http://en.wikipedia.org/wiki/H.264#Patent_licensing") codecs, both of which are encumbered in the US.  Again, I have no idea what their status is in Belgium.

---

### Post by mutrax on 2011-03-29
Yeah, I was thinking in the trend of a disclamer/one click install/agree button. I might cook up something fancy in Zenity or so...

> **realzippy said:**
> 

BTW,not really a support question,should be moved to the cafe...

Yeah, sorry bout that. Didn't really know where to go with this.

Anyway, thank you for the replies so far!

---

### Post by sydbat on 2011-03-29
Well...unless things have changed and I am really out of the loop...when you buy a pre-built computer with Windows on it, you cannot play DVD's right away either. You have to buy a DVD software package that includes a player and the codecs. These often come with DVD burners...at least here.

So, if you are including the ability to play DVD's OOTB, you have a minor advantage over other store bought Windows boxes. And any other items you configure (like Flash for example) is another minor advantage, because even Windows users have to download and install many things to make the computer more useful.

Also, as stated earlier, software patents only apply in the US. The rest of the universe does not recognize the ability to patent software.

---

### Post by SeijiSensei on 2011-03-29
> **sydbat said:**
> And any other items you configure (like Flash for example) is another minor advantage

Redistributing Flash for commercial purposes is a clear violation of Adobe's licensing.  It would be considered as infringing in any country that's a [signatory]("http://www.copyrightaid.co.uk/copyright_information/berne_convention_signatories") to the Berne Convention.  Belgium is most definitely on that list.

Once again, software patents rarely have much to do with any of these issues except perhaps for patented algorithms like H.264.

> **mutrax said:**
> Yeah, I was thinking in the trend of a disclamer/one click install/agree button. I might cook up something fancy in Zenity or so...

Sounds a lot like a "circumvention device" to me.  I'd talk to that attorney again if you really want to do this.  My guess is you'll be advised to obtain licenses for everything that's not covered by an open-source license like the GPL or the BSD or MIT licenses.

Oh, and remember that if you distribute [GPL]("http://www.gnu.org/licenses/gpl-2.0.html") software like the Linux kernel, and a very large portion of the rest of Ubuntu, you must make source code available as well.

---

### Post by mutrax on 2011-03-30
> **SeijiSensei said:**
> I'd talk to that attorney again if you really want to do this.  

Well that still is the point. I just want some good homework that I can fully specify the possible pitfalls in distributing these systems.

They will be more or less vanilla ubuntu. But still I believe easy access to multimedia support is a must. I'll be selling these things to people without any *nix experience, really meaning the "just works" filosophy. 

So I'll have them look at dvd support, media support and licencing implications. Worst case I can link the fluendo packages.

---

### Post by SeijiSensei on 2011-03-30
Or [license them from Fluendo]("https://www.fluendo.com/business/oem_business_model/") and charge for them in your retail price.

---

### Post by sydbat on 2011-03-30
> **mutrax said:**
> Well that still is the point. I just want some good homework that I can fully specify the possible pitfalls in distributing these systems.

They will be more or less vanilla ubuntu. But still I believe easy access to multimedia support is a must. I'll be selling these things to people without any *nix experience, really meaning the "just works" filosophy. 

So I'll have them look at dvd support, media support and licencing implications. Worst case I can link the fluendo packages.Another idea - for all the necessary codecs, and Flash, and whatever else does not come with a Vanilla install, make sure you give each customer well written step by step instructions how to install them.

As for the "source code" argument...in your written instructions, include the web address of Canonical and Ubuntu. A** covered.

---

### Post by mutrax on 2011-03-31
> **sydbat said:**
> Another idea - for all the necessary codecs, and Flash, and whatever else does not come with a Vanilla install, make sure you give each customer well written step by step instructions how to install them.

As for the "source code" argument...in your written instructions, include the web address of Canonical and Ubuntu. A** covered.

Meh, the step by step instructions is to hard and technical for Joe Average. 

I'll be writing some install ui's with [zenity]("http://en.wikipedia.org/wiki/Zenity") (wow! great tool!), saving these in /opt/whatever , and linking them on the desktop. You can cram disclaimers, options etc... with a simple case esac script.:KS

---

### Post by sydbat on 2011-03-31
> **mutrax said:**
> Meh, the step by step instructions is to hard and technical for Joe Average.Not if they are well written. 

Think about it...your average "Joe" who buys a pre-built Windows box HAS to install most of these things by going out onto the Internet and finding them, then following installation directions on each site, etc, etc, *by themselves with no personalized direction*.

If you provide clear and concise "Open a Terminal (Applications > Accessories > Terminal) then do this specific thing" type of instructions, people will follow them and be impressed how easy it all is. **Make sure these directions are in a text document on the desktop that they can copy / paste from.**

If my 83 year old dad can do this by following my directions ***over the phone***, anyone can do it following written instructions they can copy / paste from.

---

### Post by jerenept on 2011-03-31
> **SeijiSensei said:**
> Or [license them from Fluendo]("https://www.fluendo.com/business/oem_business_model/") and charge for them in your retail price.

Do this.
You should get rights to distribute Flash too, while you're at it.

---

