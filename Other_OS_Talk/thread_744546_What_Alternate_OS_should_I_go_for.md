---
title: "What Alternate OS should I go for?"
date: 2008-04-03
forum: Other OS Talk
---

### Post by ibuclaw on 2008-04-03
High, currently clearing out a bit of space on my computer, and may have a free partition to spare.
So I thought that I might jump on the opportunity to try out something new (Is that not the Linux Slogan...) and try a completely different OS of an experience.

The question is, which one would you recommend?

[ o Aranym]("http://aranym.org/")

[ o Aros]("http://aros.sourceforge.net/")

[ o FreeBSD]("http://www.freebsd.org/")

[ o FreeDOS]("http://www.freedos.org/")

[ o Haiku]("http://www.haiku-os.org/")

[ o KolibriOS]("http://www.kolibrios.org/")

[ o ReactOS]("http://www.reactos.org/en/index.html")

[ o SyllableOS]("http://web.syllable.org/pages/index.html")

[ o Visopsys]("http://visopsys.org/")

Any others that I haven't found that you would recommend to a moderate computing user.
Please send your info.

Cheers in advanced

Regards
Iain

---

### Post by whitefang5412 on 2008-04-03
React Os looks pretty cool as an open source alternative to windows. I'd give it a try. What are all of these Os's based off of? Are they not linux or unix at all? All written by some other human?

---

### Post by ibuclaw on 2008-04-03
None are Linux,
I think FreeBSD is the only UNIX type.
FreeDOS and ReactOS are Windows.
The others are either unique or clones of ATARI or Amiga Systems.

I'm just curious as to which one I should give a crack at (without wasting all though CDs to burn every ISO, just to throw most of them out).

Regards
Iain

---

### Post by whitefang5412 on 2008-04-03
> **tinivole said:**
> None are Linux,
I think FreeBSD is the only UNIX type.
FreeDOS and ReactOS are Windows.
The others are either unique or clones of ATARI or Amiga Systems.

I'm just curious as to which one I should give a crack at (without wasting all though CDs to burn every ISO, just to throw most of them out).

Regards
Iain

Try reactOS. It looks cool for what it is.

---

### Post by HangukMiguk on 2008-04-03
> **whitefang5412 said:**
> React Os looks pretty cool as an open source alternative to windows. I'd give it a try. What are all of these Os's based off of? Are they not linux or unix at all? All written by some other human?
Haiku is based off BeOS.

That's the only one I could tell you (other than freeDOS, whose name speaks for itself)

---

### Post by Midwest-Linux on 2008-04-03
React OS

 Positives 

It installs real quick

Looks just like a Windows installation

Doesn't take up much space

Will actually install a few windows programs

I was able to install the Juice (podcatcher) for windows and it worked


Negatives

Will not work with all computers (believe me I tried)

I never got the internet to work with it. It would not find the drivers, this is even if you have the driver disc! 
(Maybe try another ethernet card and drivers)

No internet capability is worthless in my opinion.


Summary, If you want to give it a try....Then  give it a go,  if you don't mind experimentation and don't expect much. Its a small install and doesn't take forever to download. Maybe you can install it on your computer and maybe you can get the internet to work. If you do, perhaps start a separate thread and gives us a report. While React OS looks promising, it has a long way to go. Its been in development for a long time.

---

### Post by Lord Illidan on 2008-04-03
I've not tried any of them, but my fav. Linux magazine Linux Format mentions FreeBSD a lot. (If I had the harddrive space, I'd install it!), and it also likes Syllable OS.

---

### Post by init1 on 2008-04-03
FreeDOS- One of my favorite OS's. Boots quickly.  
KolibriOS- Awesome OS, I can't believe the they could so much in there!
SyllableOS- Looks great, but not very stable yet
Visopsys- Has a partition manager, but not much else. Still a cool project though 
Others not on the list:
Minix 3- A small UNIX like OS
SolarOS- Another interesting OS
RXDOS- A DOS clone
BugOS- A very complete OS that is not based on any other

---

### Post by Twitch6000 on 2008-04-04
Well reactos is only would that would make me change again.
although right now it is in alpha so yeah >.>.
It is a bsd with alot of programs such as wine hoping to make a full windows clone.
That is the goal of that os.I think they had a better chance of doing it with Linux though :(.

---

### Post by heartburnkid on 2008-04-04
ReactOS isn't BSD; it's a custom kernel meant to be compatible with NT.  It borrows a lot of code from WINE, and in turn contributes a lot of code back, but that doesn't make it WINE.

---

### Post by Seti on 2008-04-04
I voted for FreeBSD but OpenBSD is even better. And like maple-syrup, its made in Canada.

---

### Post by Amarsingh0793 on 2008-04-04
I haven't even heard of half of these lol

---

### Post by ibuclaw on 2008-04-04
> **heartburnkid said:**
> ReactOS isn't BSD; it's a custom kernel meant to be compatible with NT.  It borrows a lot of code from WINE, and in turn contributes a lot of code back, but that doesn't make it WINE.

I agree. I've had a small read about, and ReactOS calls itself an "Open Source Replacement" for XP.
Also for ReactOS to run Windows binaries natively, they would also have to use the same function calls at ground level.

ie: Here's a function WINAPI found in winbase.h, from Visual Studio's include files.
[PHP]
BOOL
WINAPI
ReadFile(
IN HANDLE hFile,
OUT LPVOID lpBuffer,
IN DWORD nNumberOfBytesToRead,
OUT LPDWORD lpNumberOfBytesRead,
IN LPOVERLAPPED lpOverlapped
); 
[/PHP]

And ReactOS' version (found in w32api/include)
[PHP] BOOL WINAPI ReadFile (HANDLE, PVOID, DWORD, PDWORD, LPOVERLAPPED); [/PHP]

For Native windows applications calling the WINAPI function, the two have to be exactly the same, else you might as well be building your own OS from scratch.

PS:
Gave ROS a try. It is indeed very alphish. Got it to run on my old Computer (80268 300Mhz Processor, Currently has Win98 Installed).
First thing I tried was copy and paste via the rosexplorer....
Alas, I had to resolve to the terminal (re-learning DOS) and do it that way. :lolflag:

I'll wait till the first beta release on that one, else I would honestly say that it has the potential of being the most important OS of the 21st Century (and that may be an understatement)

I'm just giving FreeBSD a try atm, as a majority (at this point in time) have voted for that.

Thanks for your suggestions.

Regards
Iain

[EDIT]
> **Amarsingh0793 said:**
> I haven't even heard of half of these lol

Anyone can build a unique OS from scratch. But since the market is already well established into a 2-way system (There's UNIX, and then there's Windows).
Though the root reason is purely down to hardware manufacturers favouring one OS, rather than building open hardware for all.
Thus, anything else that is made just gets shoved to the side.

It's a shame, isn't it?...

---

### Post by Amarsingh0793 on 2008-04-04
yup it is a shame

---

### Post by mivo on 2008-04-04
FreeBSD. Lots to learn and it's very usable. :)

---

### Post by liquidfunk on 2008-04-05
Haiku OS looks pretty nifty. I quite fancy trying that when an .iso comes out.

---

### Post by mr.farenheit on 2008-04-05
vixta

---

### Post by Amarsingh0793 on 2008-04-05
I've tried vixta. It's filled with bugs I wouldn't recommend it to anyone.. for now at least.

---

### Post by sajro on 2008-04-05
> **Seti said:**
> I voted for FreeBSD but OpenBSD is even better. And like maple-syrup, its made in Canada.

Like most good things: hockey, Arch Linux, and friendly folks who say 'eh' a lot without noticing it

---

### Post by ibuclaw on 2008-04-06
> **sajro said:**
> Like most good things: hockey, Arch Linux, and friendly folks who say 'eh' a lot without noticing it

And don't forget metal...

Canadian's make [very good metal]("http://zeroscapemusic.com/").

But absolutely suck in the grunge scene, sorry Nickelback...:lolflag:

---

### Post by xaer0knight on 2008-04-07
> **HangukMiguk said:**
> Haiku is based off BeOS.

That's the only one I could tell you (other than freeDOS, whose name speaks for itself)

Haiku is promising. BeOSMax had a name change to Haiku. The only problem is that if BeOS 5 PE didn't pick up my old SMC network card or my Nvidia card, you would think that BeOSMax 5 PE would pickup them. Well BeOSMax 5 PE did pick up my Nvidia card but would not pick up my SMC network card (which bebits.com doesn't even have a download for the driver and the manual install for networking is ungodly)... If Haiku is just a name change I will stick away from it. BeOS even on my old 233Mhz had a problem with my Network cards.

Haiku doesn't even have a stable Live CD release and your stuck with a hard to understand install which are RAW HDD and VMware Images. Too me, until there is a stable LiveCD Haiku will not be an option because its just BeOS Max with a new name. Don't get me wrong I loved BeOS 5 (back in the day with Dialup) but for networking its just so incompatible with NICs, Its a "love/hate relationship" for the last 10 years.

I know Fluxbuntu 7.10 doesn't have a live CD but since its Ubuntu-based(?), i knew everything would work.

---

