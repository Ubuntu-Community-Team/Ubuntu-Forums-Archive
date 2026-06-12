---
title: "How much has Apple stole from open source?"
date: 2010-03-04
forum: Recurring Discussions
---

### Post by JohneG on 2010-03-04
I love technology and i love open source. I am of the opinion that we need both closed source and open source. If you argue how much closed source can affect development then i'm very much on board (if you're talking about the likes of Microsoft, whom I've just finished a project on and understand how they hold back development). I do however believe that both open and closed source can and have to co exist, at least in this day and age. I don't want any back lash unless it's constructive. I admire what Apple do and i really enjoy working with their software. I am not a developer. I am a user end person but i do however use a LOT of software being in the media field and unless i have to specifically work on certain software, i can get the same result on Linux. My question to everyone is, how much have Apple actually stole from open source??? I know they have used a lot of open source modules but as a user end can you explain what they have used as inspiration? I understand that they used the same rendering engine as Konqueror etc. Just so i can get an idea, what have they took inspiration from/ stole from(if that's your leaning). Thanks, and please keep it informative :D

---

### Post by swoll1980 on 2010-03-04
> **JohneG said:**
> I love technology and i love open source. I am of the opinion that we need both closed source and open source. If you argue how much closed source can affect development then i'm very much on board (if you're talking about the likes of Microsoft, whom I've just finished a project on and understand how they hold back development). I do however believe that both open and closed source can and have to co exist, at least in this day and age. I don't want any back lash unless it's constructive. I admire what Apple do and i really enjoy working with their software. I am not a developer. I am a user end person but i do however use a LOT of software being in the media field and unless i have to specifically work on certain software, i can get the same result on Linux. My question to everyone is, how much have Apple actually stole from open source??? I know they have used a lot of open source modules but as a user end can you explain what they have used as inspiration? I understand that they used the same rendering engine as Konqueror etc. Just so i can get an idea, what have they took inspiration from/ stole from(if that's your leaning). Thanks, and please keep it informative :D

Why do we even need closed source? The only thing holding oss back is adoption. Adobe could open the source code to Photo shop, and still sell it. Sure someone would could release the source for free, but don't pirates to that already? Truth is corporations would still go to Adobe.

---

### Post by blur xc on 2010-03-04
I've always wondered how can you possibly know if a closed source proprietary product had stolen open source code in it?

BM

---

### Post by mickie.kext on 2010-03-04
> **blur xc said:**
> I've always wondered how can you possibly know if a closed source proprietary product had stolen open source code in it?

BM

There is stuff called [decompiler]("http://en.wikipedia.org/wiki/Decompiler"). You can extract sources out of binary with it. Of course, that is illegal and source will usually be buggy and maybe would not compile again without fixing it, but it is enough to see if some GPL'd code is stolen.

---

### Post by JohneG on 2010-03-04
I do understand that adoption is a big issue but most people aren't familiar with open source and the fact that something that is free can be, and is often, better than the proprietary version. I think if open source does take off that it will be awhile off. I understand developers frustrations and putting in a lot of work and feeling, rightly so, that their end products can be, and often are better than commercially availably products. I also understand how hard it is to pin point how much closed source takes off of open source. I used to live with a computer programmer and he claimed that most of the programmes now made start off with base code from open source. I do however know that Apple openly acknowledge that they used open source components. I'm just wondering how much has made up their operating system and programmes?

---

### Post by kk0sse54 on 2010-03-04
The infamous Apple who has never ever contributed to Open Source and has just blatantly ripped off FreeBSD and Open Source in general :roll:

Ever heard of Darwin, CUPS, Webkit (just to name a few)?

[http://developer.apple.com/opensource/index.html](http://developer.apple.com/opensource/index.html)

---

### Post by MaxIBoy on 2010-03-04
Nothing has been "stolen." First of all, if someone uses a non-copyleft license, that means he *doesn't mind* if someone else takes it proprietary, so that wouldn't be "stealing." And second of all, Apple *has not taken anything proprietary*, that I know of. Third of all, CUPS, Webkit, OpenCL, and many more open-source technologies all owe a great deal to Apple.

I do think Apple is guilty of a number of unfair business practices, probably even worse than Microsoft. But credit is owed where credit is due.

---

### Post by earthpigg on 2010-03-04
> how much have Apple actually stole from open source???

how can apple have stolen any BSD-licensed code, when _*the owners of said code gave Apple permission to take it*_? that permission was given when the owners *_chose_* to use the BSD license.

> I'm just wondering how much has made up their operating system and programmes?

a lot of under the hood stuff. nearly all the command line utilities, for example. the ssh in ubuntu is the same as the ssh in OS X -- both come from OpenBSD. and that's ok.

if you type 'man command' on a mac to read the man file, the man file will very often start with:

> BSD General Commands Manual

example: [http://developer.apple.com/mac/library/documentation/Darwin/Reference/ManPages/man1/dd.1.html](http://developer.apple.com/mac/library/documentation/Darwin/Reference/ManPages/man1/dd.1.html)

(the url says 'darwin' and that may be where these where copied from, but the web page is titled "Mac OS X Manual Pages"... has apple bothered to rebrand the man pages to say "OS X" instead of BSD? i don't know, but it doesn't really matter.)

---

### Post by kachaffeous on 2010-03-04
> **MaxIBoy said:**
> Nothing has been "stolen.

^^

If it is open source it can't be stolen....

---

### Post by phrostbyte on 2010-03-04
These is no "stolen" code. But OS X does have a ton of open source code in it. Probably in the tens of millions LoC.

---

### Post by blur xc on 2010-03-04
> **kachaffeous said:**
> ^^

If it is open source it can't be stolen....

As I understand it, that's not entirely true.  AFAIK, the GPL states that once you license software under it, it has to *stay* FOSS.  It cannot be used in a proprietary product.  If it is, the sections of code that they use, and any improvements to that code, must be re-released under the GPL which means the code has to be available to anyone who wants it.

On the other hand, the BSD license, allows code to be taken and use in proprietary products willy nilly with no clause stating anything should be returned the the open source community.  

At least that's how I take it...

BM

---

### Post by earthpigg on 2010-03-04
> **blur xc said:**
> As I understand it, that's not entirely true.  AFAIK, the GPL states that once you license software under it, it has to *stay* _GPL'd_.  It cannot be used in a proprietary _piece of software_, but _it can be used in a proprietary product (such as a search engine, or TiVO)_. _The source code if it is a piece of software _has to be available to anyone _whom the binary was distributed to under the same terms as the binary itself_.

underlined areas indicate corrections that reflect how i understand it. i could be mistaken, or we could both be.

RHEL doesn't have to give the source code to anyone that wants it... only to anyone *_whom they distribute the binary to_*. and they don't distribute the binary for free - they sell it for a 'distribution fee'.

someone can, however, purchase one copy of it, get the source code, and make copies publicly available for free themselves. that's how we have CentOS, as i understand it. CentOS purchases one copy of RHEL, removes the branding, recompiles, and gives it away at no charge (along with giving the source code away at no charge). you may end up with a product super super similar to RHEL, but if it doesn't have the branding than it isn't RHEL.

every aspect of the GPL has an "if you choose to distribute at all" aspect. if you don't distribute, you don't need to provide a single line of source code. this is why we don't have the source code of google's modified version of ubuntu - google doesn't distribute it outside of google.

if you don't distribute to people who don't give you money, then you don't need to give a single line of source code to people who won't give you money.



i can't think of any examples, but this is also how we see GPL'd software that has free linux versions and the windows setup.exe costs $20 to download. after you buy the setup.exe, you get the source code... you can recompile and give it away for free, but you must remove the branding if the trademark owner says so.

edit: [here ya go]("http://en.wikipedia.org/wiki/GCompris"), gcompris is GPL'd software - > GCompris is a suite of free educational software for children aged 2 to 10.[1]

It is available for Linux, Mac OS X and other systems. Binaries compiled for Microsoft Windows version are distributed as crippleware with a restricted number of activities; it is possible to access all the activities in Windows for a fee.

i can pay the fee, get the source code, compile it myself, and give it away at no cost... but i can't call the end result gcompris. it must be a distinct product -- even if it is identical and the only difference is the name i call it. and i also have to make the source code available under the same terms (cost free) as the binary. this is relevant for marketing reasons.

---

### Post by katie-xx on 2010-03-04
[SIZE=2]Licences are a minefield best left to the lawyers.
The real issue here should _open standards_ rather than worrying about open source or proprietary code.
If we could ever get to a situation where standards can be agreed and openly published then, provided solutions adhere to those standards, it doesnt matter a teeny bit if people publish under one licence or another. IMHO of course :)
Imagine how easy and flexible life would be if we could rely on a component produced by one company meeting in every respect a common standard for communicating with a component produced by another.
I would have thought we would have reached that goal by now but its not so. In some cases, even where a standard has been agreed, access to that standard is severely restricted and can cost a lot of money.
Thats even more unfair than restrictive licensing because small companies or individual programmers can find themselves locked out from using a standard.



Kate[/SIZE]

---

### Post by MaxIBoy on 2010-03-04
> **kachaffeous said:**
> ^^

If it is open source it can't be stolen....
Yes, it can be. But only if the license has some form of copyleft (such as the GPL.) "Weak" or "Permissive" licenses (such as the MIT/X11, BSD, Apache, WTFPL, etc.) do not prohibit you from using the code in proprietary products. So for example, Windows NT has a bunch of BSD code in its TCP/IP stack, and this is perfectly fine. The BSD licenses don't prevent this. But, for example, the GPL does state that this kind of thing isn't allowed.

---

### Post by earthpigg on 2010-03-04
> **katie-xx said:**
> [SIZE=2]Imagine how easy and flexible life would be if we could rely on a component produced by one company meeting in every respect a common standard for communicating with a component produced by another.[/SIZE]

you mean Microsoft's [Office Open XML]("http://en.wikipedia.org/wiki/Office_open_xml")?

scroll down to licensing. 

> "Microsoft irrevocably promises not to assert any Microsoft Necessary Claims against you for making, using, selling, offering for sale, importing or distributing any implementation to the extent it conforms to a Covered Specification [...]"

and this only applies to

> to parties that do not "file, maintain or voluntarily participate in a patent infringement lawsuit against a Microsoft implementation of such Covered Specification".

-**only microsoft can change/improve the standard.** if microsoft says you cannot embed flash video in a presentation and you must use silverlight, then you cannot make a presentation creator using those standards that saves presentations with flash video embedded. if you do, then the promise is void and you can be taken to court for patent infringement.

-if you ever file a law suit against microsoft for patent infringement, the promise is void and you can be taken to court for patent infringement.

-all of this also means that if you make an honest mistake or human error in your implementation of the standard, the promise is void and you can be taken to court for patent infringement.

-i suppose that it also means Microsoft could change the standard in the future so that it relies on underlying software only available in Microsoft Approved Operating Systems. include in the standard a public key that opens 'locks' only present on Windows and OS X (MS gives the lock to Apple with an NDA) would not be very hard. reverse engineering the lock would be a DMCA violation, and removing the public key would mean you have changed the standard on implementation, the promise is void and -- you guessed it -- you can be taken to court for patent infringement.

---

### Post by JohneG on 2010-03-04
As much as i appreciate the comments how many of them are answering my question?

If you DO want to help me with one other question though my computer architecture tutor did say that towards the end of the 90's Windows had beaten Apple Mac in performance and that's what they changed over to BSD Unix based systems? Can anyone confirm this or give me any links? Otherwise i would still like a list of what Apple has TAKEN as their own ( i won't use the word stole anymore as i never meant it that way). Thanks for all the replies though :D

---

### Post by earthpigg on 2010-03-04
> towards the end of the 90's Windows had beaten Apple Mac in performance and that's what they changed over to BSD Unix based systems?

extreme oversimplification. skim [this]("http://en.wikipedia.org/wiki/Nextstep"), and take a gander at Steve Jobs' employment history.

> i would still like a list of what Apple has TAKEN as their own 

here: [http://www.opensource.apple.com/release/mac-os-x-1062/](http://www.opensource.apple.com/release/mac-os-x-1062/)

sort by license, in reverse alphabetical order (so A for Apple comes last).

---

### Post by cariboo on 2010-03-04
This topic has been discussed often enough to make it a recurring discussion. Moved

---

### Post by Shpongle on 2010-03-04
> **blur xc said:**
> I've always wondered how can you possibly know if a closed source proprietary product had stolen open source code in it?

BM

you can also reverse engineer it based on the functionality , although thats practically trying to emulate it with your rewrite, rather than extract the source

---

### Post by wojox on 2010-03-04
In 1997 Microsoft gave Mac 150 million to bail them out. I think they felt guilty. Mac invented Windows and took it to Xerox who in turned laughed at them. Next day Bill is over at beating down Apple's door wanting to look at the source. Next thing you know Microsoft Windows is born and protected.

Microsoft didn't even invent Dos. They bought of some twenty something living in his mom's garage.

Apple's true focus has always been hardware. That's what Wotizky was great at. Jobs is a marketer. Their main focus now is to put a web connected iphone in everyone's pocket.

I did paper's on this stuff in college. If you want proof go to the library or book store and read about it.

---

### Post by Bachstelze on 2010-03-04
> **blur xc said:**
> I've always wondered how can you possibly know if a closed source proprietary product had stolen open source code in it?

BM

[http://ubuntuforums.org/showthread.php?t=1252306#6](http://ubuntuforums.org/showthread.php?t=1252306#6)

Doesn't work all the time, but in a vast majority of cases.

---

### Post by murderslastcrow on 2010-03-04
To be honest, I wish Microsoft would do what Apple did- use a new-age kernel, light interface, and create a compatibility layer of some sort.

Heck, just contribute to Wine and make it perfect, and make your own Linux distribution and sell it! :D Just think of the business prospects! XD

But yeah, to be completely fair, and as you mentioned, Apple uses open source software the way it's meant to be used, and the kernel itself is an open source project that you can use right now. The interface elements and libraries are basically the only thing they primarily develop. If we were nice, we would put a lot of work into porting open source Linux drivers over to Darwin, but we have enough work on our hands. But really, OS X is like the perfect example of why, even with beautiful software, anything proprietary can be a serious pain. iTunes probably being the largest example of vendor lock-in in recent history.

As far as I know, virtual desktops originated with Linux, so there's one. Safari is an obvious example, modifying KHTML into Webkit. I like what Google's done with it. ^,~

Recently, Apple has tried to patent an idea similar to the 3d head-tracking plugin in compiz, etc. To be honest, Apple usually only tries things that are truly new, but occasionally they need to play catch up. Their users are basically happy with it staying the same but gaining some polish periodically. Not a bad idea, kinda' like Debian.

To be honest, if Apple were nice and didn't sue people over petty subjects, weren't so anal about who uses their media players and how, and were more like Canonical in its respect for the user's rights, not just their own pocketbook and image, then I wouldn't be so upset with them. They would effectively just be a good distro who provides hardware and a few closed applications so that other distros don't steal them.

Eh, I'm getting carried away, but in all honesty, they've used a few open source concepts, but altogether their largest 'inspiration' is their actual use of open source software in their OS.

---

### Post by schauerlich on 2010-03-04
See the link in my sig.

---

### Post by PC_load_letter on 2010-03-04
Doesn't Apple use GCC as the default compiler?

---

### Post by Twitch6000 on 2010-03-04
Apple stealing from open source? Hah they have helped it more then anything. Now canicoal on the other hand ...

---

### Post by Bachstelze on 2010-03-04
> **PC_load_letter said:**
> Doesn't Apple use GCC as the default compiler?

Yes. So?

---

### Post by Foster Grant on 2010-03-04
> **wojox said:**
> In 1997 Microsoft gave Mac 150 million to bail them out. I think they felt guilty. Mac invented Windows and took it to Xerox who in turned laughed at them. Next day Bill is over at beating down Apple's door wanting to look at the source. Next thing you know Microsoft Windows is born and protected.

Not so much. The GUI that Jobs fell in love with was originally developed at Xerox's Palo Alto Research Center for the experimental Xerox Alto, a GUI which itself was based on the On-Line System developed by Doug Engelbart at the Stanford Research Institute¹. Jobs saw the Alto's interface when he toured Xerox PARC in 1979 and promptly ... ah, let's just say he got things rolling so Apple could *reverse-engineer* it. :D Apple's version was greatly improved over what Xerox had for its Alto and Star desktop computers, however.

Microsoft first started work on something called "Interface Manager" in November 1981. The original Microsoft Word was an attempt to emulate the Xerox Alto's word processor. It has been claimed that Microsoft started developing Interface Manager after being shown the development version of Macintosh System 1 when Jobs was trying to convince Gates to develop software for the early Mac.

¹[SIZE="1"]You should get to know him and that. Most of what we use today -- GUIs, mice, hypertext/hypermedia, collaborative servers AKA wikis, shared-screen teleconferences -- comes directly from Doug Engelbart's research at SRI.[/SIZE]

---

### Post by PC_load_letter on 2010-03-05
> **Bachstelze said:**
> Yes. So?

Well,I'm not saying Apple are doing anything criminal, legally, but they do benefit quite a bit from FOSS. Their latest lawsuit against HPC is immoral in my humble opinion.

---

### Post by handy on 2010-03-05
I doubt that anyone actually knows the true answer to how much OSS code has been stolen by MS, Apple, or any other large closed source company.

It is a question without an answer really.

---

