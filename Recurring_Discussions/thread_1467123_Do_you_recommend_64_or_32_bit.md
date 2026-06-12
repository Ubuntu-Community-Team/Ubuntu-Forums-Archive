---
title: "Do you recommend 64 or 32 bit?"
date: 2010-04-30
forum: Recurring Discussions
---

### Post by Zappanale on 2010-04-30
Hi, I'm doing a fresh install of 10.04. Do you recommend staying with 32 bit (as I have been using) or installing the 64 bit instead?

Here's my system:
dell studio 1535
Intel dual core, 2 ghz
3 gb ram
Thanks.

---

### Post by ScottinSoCal on 2010-04-30
> **Zappanale said:**
> Hi, I'm doing a fresh install of 10.04. Do you recommend staying with 32 bit (as I have been using) or installing the 64 bit instead?

Here's my system:
dell studio 1535
Intel dual core, 2 ghz
3 gb ram
Thanks.

Depending on your specific hardware and what apps you use, some people have reported problems with finding patches and drivers for the 64 bit version. Whether you ever run into that is totally up in the air.

---

### Post by Zappanale on 2010-04-30
In that case, for the time being, I shall play it safe and go 32 bit.

Thanks.

---

### Post by philinux on 2010-04-30
> **Zappanale said:**
> Hi, I'm doing a fresh install of 10.04. Do you recommend staying with 32 bit (as I have been using) or installing the 64 bit instead?

Here's my system:
dell studio 1535
Intel dual core, 2 ghz
3 gb ram
Thanks.

I've been using 64 bit for 18 months. No problems.

---

### Post by Sector11 on 2010-04-30
Since you have less than 4 GB RAM I see no advantage to using the 64bit OS. I doubt very much that you would see a difference and if you did it might be on the negative side.

Here's and article written a few years back regarding Ubuntu 32 vs 64bit OS:

[http://ubuntu-tutorials.com/2007/11/26/32bit-vs-64bit-ubuntu-that-is-the-question/](http://ubuntu-tutorials.com/2007/11/26/32bit-vs-64bit-ubuntu-that-is-the-question/)

or the Wikipedia entry concerning 64bit, read the 32 vs 64 bit section.

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

That said I run a 64bit OS now and my next upgrade will be going back to a 32bit OS as I only have 2GB RAM. I do no heavy duty CPU intensive stuff, video editing, number crunching or database manipulation, and I have some 32bit programs that I use so I need to install the libraries that allow 32bit programs to run under a 64bit OS.

I saw NO different in speed when I changed to the 64bit OS.

s11

---

### Post by kanikilu on 2010-04-30
> **Sector11 said:**
> Since you have less than 4 GB RAM I see no advantage to using the 64bit OS. Agreed. There may be certain use-cases where you have <4GB of RAM, but you want 64-bit because an application you are using can take advantage of it (e.g. Handbrake), but if not, the downsides still outweigh the benefits, but only slightly...it's getting better.

For me, really the only hiccup I've hit with 64 is the Amazon MP3 Downloader. I was able to use the GETLIBS script under previous versions of Ubuntu, but that didn't work when I switched to 10.04 at beta 2. Although FWIW, so far I've had pretty good success with the "Pymazon" alternative downloader...

---

### Post by phrostbyte on 2010-04-30
If you add any RAM you might want to upgrade to 64-bit. Although unlike some other OSes, Linux does have the ability to address more then 4GB of RAM in 32-bit mode. It uses rarely known feature of x86 processors called PAE.

---

### Post by pricetech on 2010-04-30
I recommend 64 bit as long as your hardware can handle it.  Unlike other posters, I saw a noticeable improvement when I switched from 32 to 64.  I do have an issue with flash, but everything else I use gives me no trouble at all.

---

### Post by oldos2er on 2010-04-30
> **Sector11 said:**
> Since you have less than 4 GB RAM I see no advantage to using the 64bit OS. 

I disagree. When I ran 64-bit Ubuntu with 2GB RAM, video encoding and other CPU-intensive tasks were noticeably faster. Tasks e.g. email and web browsing, not much noticeable difference.

---

### Post by NightwishFan on 2010-04-30
I never use up all my RAM, but I like to address it faster, so I go with 64-bit.

---

### Post by necromonger on 2010-04-30
3 gigs or less 32 bit 4 gigs or more 64 bit thats the way i do it.both  are pretty stable.

---

### Post by philinux on 2010-04-30
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by kaivalagi on 2010-05-16
> **philinux said:**
> [http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

mmm, 64 bit all the way then with 2gb memory or more...

---

### Post by Paqman on 2010-05-16
Always 64-bit for any CPU that can handle it.

---

### Post by alphacrucis2 on 2010-05-16
> **pricetech said:**
> I recommend 64 bit as long as your hardware can handle it.  Unlike other posters, I saw a noticeable improvement when I switched from 32 to 64.  I do have an issue with flash, but everything else I use gives me no trouble at all.

I had the same experience. I sorted the flash plugin issue by getting rid of the OSS packages and installing the proprietary Adobe 64 bit version for Linux

---

### Post by stanca on 2010-05-16
Always 64bit on 64bit cpu's too.:)

---

### Post by Daniel Jorge on 2010-05-16
I was reading the replies and i think some people are missing the point. Using 64 bits instead of 32 bits is usefull only if you need to process huge amounts of information. (i.e. servers, databases, etc). If you just use your pc/laptop for multimedia/intenet you'll not gain much by using 64 bits.

And you cannot forget that the huge majority of the programs are made for 32 bits.

---

### Post by gillmt on 2010-05-16
I have found that there are still a few problems with 64 bit - 32 bit works great nearly all the time now. Wine seems to work better in 32 bit for me and I cannot see any performance improvement with 64 bit - probably because I only have 2 Gb RAM

---

### Post by Paqman on 2010-05-16
> **Daniel Jorge said:**
> Using 64 bits instead of 32 bits is usefull only if you need to process huge amounts of information. (i.e. servers, databases, etc).

A lot of normal everyday desktop tasks, such as re-encoding music and video, will benefit heavily from a 64-bit architecture.

---

### Post by conmat on 2010-05-16
Another consideration:

If you ever want to compile programs from source it will probably be easier with 32-bit.

I'm running 64-bit and I have many problems with this.  I don't know enough to fix the code to run on 64-bit.

It kind of makes sense because there are a lot more programs written on 32-bit systems.

I wish there was a 64-bit version of Seamonkey.

---

### Post by KdotJ on 2010-05-16
I've been running 64 bit since 9.10 and no problems what so ever, apart from sorting out flash. I'd say go for 64...

---

### Post by oldos2er on 2010-05-16
> **Daniel Jorge said:**
> And you cannot forget that the huge majority of the programs are made for 32 bits.

The majority of programs are available for both 32- and 64-bits. I've only encountered one, Adobe Acrobat, that's 32-bit only.

---

### Post by cascade9 on 2010-05-16
> **Paqman said:**
> A lot of normal everyday desktop tasks, such as re-encoding music and video, will benefit heavily from a 64-bit architecture.

+1. Even boring tasks, like starting, etc tend to get a 5-15% increase from using 64bit. 

> **conmat said:**
> I wish there was a 64-bit version of Seamonkey.

There is. Its 'unoffical' but its there- 

> **Contributed builds (other platforms)**

  These are unofficial builds and may be configured differently   than the official SeaMonkey builds. Please read their "readme" files for   further information.
  Linux/x86_64     [Linux/x86_64 .tar.bz2]("http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/2.0.4/contrib/seamonkey-2.0.4.en-US.linux-x86_64.tar.bz2")     [(readme)]("http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/2.0.4/contrib/seamonkey-2.0.4.en-US.linux-x86_64.README")     [(MD5 sum)]("http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/2.0.4/contrib/seamonkey-2.0.4.en-US.linux-x86_64.MD5SUM")     [(SHA1 sum)]("http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/2.0.4/contrib/seamonkey-2.0.4.en-US.linux-x86_64.SHA1SUM")   

[http://www.seamonkey-project.org/releases/#official](http://www.seamonkey-project.org/releases/#official)

---

### Post by Total AI on 2010-05-16
I installed my 32 bit ubuntu on a 64 bit computer which I built,the 32 bit system runs better on the new machine,to my way of thinking,an added note,the 32 bit single core celeron processor will not handle ubuntu you will experience stale locks,crashes. I have the quad core intel in mine

---

### Post by philinux on 2010-05-16
> **Daniel Jorge said:**
> 

And you cannot forget that the huge majority of the programs are made for 32 bits.

My 64 bit synaptic is full of 64 bit apps. The only ones I want that are 32 bit are acroread and google earth and they both run fine anyway.

Thread move to recurring discussions.

---

### Post by OooBuntuRox on 2010-05-17
[SIZE=2]I am on the fence about 64 bit too. I have 3 gig of ram. I also installed the 32 bit libraries for compatibility.
I think there might be a slight performance increase but not much.

Honestly, I think the performance increase may be due to upgrading from  9.04 to 10.04. The wifi seems to connect faster. Overall, I love 10.04.[/SIZE] [SIZE=2]

What I have noticed is that the system panel is a little flaky. First the system was freezing just before the panel loaded.[/SIZE] [SIZE=2]
I would have to do a hard reset to recover. I did some updates that seem to have stopped the panel lock ups.
However, may application Icons keep moving around and changing order/ location.

Does anyone know why this happens? Is this 10.04 version specific or is it 64 bit specific? Any thoughts or feedback?[/SIZE] [SIZE=2]


Thanks, OooBuntuRox[/SIZE]   :guitar:

---

### Post by NightwishFan on 2010-05-17
That is probably something like a xorg or kernel modesetting issue, as that happens to me in virtualbox.

---

### Post by WinterRain on 2010-05-18
> **Daniel Jorge said:**
> 
And you cannot forget that the **huge majority **of the programs are made for 32 bits.

As a 64bit user, I can attest that 99.9% of the 32bit apps are available in 64bit. And the odd thing that isn't native will run anyway. Your statement is far from the truth.

> **OooBuntuRox said:**
> [SIZE=2]Is this 10.04 version specific or is it 64 bit specific? Any thoughts or feedback?[/SIZE] [SIZE=2]


Thanks, OooBuntuRox[/SIZE]   :guitar:

I highly doubt it has anything to do with it being a 64 issue. I've been using 64bit for almost 2 years, and if anything, I think it's more stable than 32. But that's just my observation. I read somewhere that by it's very nature, that 64 bit is a tiny bit more stable. I don't have a link, but feel free to google it.

If I had a lesser computer, I would be tempted to stay with 32, but when I've got tons of horsepower, I want to take full advantage of it. I do heavy multitasking with some graphical stuff here and there, and using 64bit is the only way to go for a user like me. If you're just a joe six pack type of user, then yeah, stay with 32bit for all it matters.

---

### Post by OooBuntuRox on 2010-05-18
[SIZE=2]**Quote: **That is probably something like a xorg or kernel modesetting issue, as  that happens to me in virtualbox.     

Thanks. It sounds harmless. So I won't worry about it anymore. It just struck me as odd... being how the icons are ***locked*** to the panel. :rolleyes:

**Quote:** If you're just a joe six pack type of user, then yeah, stay with 32bit  for all it matters.

I hear you but no, far from it. I'm not a knuckle dragger either. ...at least I hope not. While 64 bit probably isn't a must have for me, it just seems like it would offer better performance and security than 32 bit. While I'm not sure, I would suppose that a 64 bit OS would make better use of a 64 bit cpu. It also seemed to me that it would make better use of ram, be more capable of long file names, passwords, and directory structures if needed.

But mostly, I am the curious type. I am ok with fiddling with 64 bit until I am certain I don't need it than to run a 32 bit that I am certain is stable. Thats just an example. I'm not certain that the 32 bit version is more stable.

Thanks for that 10.04 manual link. Does anyone know of a fantastic publication that explains the nuts and bolts of ubuntu [minus the fluff]? I would suppose it would be a ***really good*** admin reference book... or perhaps a begginer programmers guide for Ubuntu [Debian Linux]. Or maybe both.

Heck, I'm not even comfortable with compiling tar files. BUT I WANT TO LEARN! I'm an MS convert who has stumbled upon the Ubuntu worshiping alter. \\:D/I like Ubuntu better than Suse, Solaris and Fedora/ RedHat.

BTW: Yes I've googled for books. I see titles like hackers secrets, guru's book, ...Bible, etc. Then you read the reviews and they get like 2-3 stars or were published in 2003-2008... I'm not impressed. I'm looking for like 4.5 to 5 star out of 5 star books... look on the back and it says something like: This book rated for experts.

While I'm not an expert, I don't like to waste my time/ money reading junk publications. Know what I mean?

Thanks,
OooBuntuRox:guitar:

PS: The installing 64 bit flash was a helpful start. Thanks.
[/SIZE]

---

### Post by NMFTM on 2010-05-18
I recommend [URL="http://ubuntuforums.org/showthread.php?t=1479629"]16-bit.
[/URL]

---

### Post by Paqman on 2010-05-19
> **philinux said:**
> My 64 bit synaptic is full of 64 bit apps. The only ones I want that are 32 bit are acroread and google earth and they both run fine anyway.

Thread move to recurring discussions.

I suspect his point was that they were written with 32-bit in mind, in the same way that most software is still written for a single core. You can compile the code for 64-bit, just like you can run a single-threaded app on a multi-core machine, but you won't see the real benefit of your architecture.

---

### Post by OooBuntuRox on 2010-05-19
[SIZE=2]> **Paqman said:**
> I suspect his point was that they were written with 32-bit in mind, in the same way that most software is still written for a single core. You can compile the code for 64-bit, just like you can run a single-threaded app on a multi-core machine, but you won't see the real benefit of your architecture.

excuse me if I am using incorrect terminology, what you say is a good point. As, why would you include 64-bit specific processor calls in an app written for 32 bit architecture. Kind of like putting a 4 cylinder (32 bit apps) in a Ferrari (64 bit kernal) because it still ***looks*** fast.... hey?

So if I am running a 64 bit Ubuntu kernal, can I assume and trust that all the repository and synaptic apps are 64 bit apps? Though I wouldn't think so, might there be a mix of 32 and 64 bit apps? Or are the repositories kept fully segregated?

**Winterrain:** Thanks for the new manual link. It seems better than the 9.04 manual. I didn't even think to search for an updated version.

OooBuntuRox[/SIZE]  :guitar:

---

### Post by del_diablo on 2010-05-19
> excuse me if I am using incorrect terminology, what you say is a good point. As, why would you include 64-bit specific processor calls in an app written for 32 bit architecture. Kind of like putting a 4 cylinder (32 bit apps) in a Ferrari (64 bit kernal) because it still looks fast.... hey?

Its x86, it hardly matters. Intel tried a pure x64 version, it failed because nobody wanted to lose the backward compability over nothing good. Basically their x64 version is the exact same as AMD's x86-64 BUT it can't run 32-bit code, it did not toss over board all the useless **** that was still on x86.

---

### Post by 3Miro on 2010-05-19
The only issues that exists with 64-bit Ubuntu are:

1. Flash can be tricky. I have been using it and it is fine, but it often requires a bit of extra work.

2. Some WMA codecs will not work (you can fix that with recompiling your own version of 32-bit mplayer).

3. There might be some proprietary drivers (such as Canon printers) that don't work for 64-bit.

Overall, 64-bit is 10 - 30% faster for regular apps and it can get twice as fast for some heavy video conversions and such. You can also use more RAM.

The FOSS apps in the Ubuntu repos have been compiled for 64-bit machines. The only 32-bit apps in the 64-bit repos are proprietary ones.

BTW I have been using 64-bit Linux and mixed 32 and 64-bit apps on both Intel and AMD CPUs with no trouble. That is AMD Athlon X2, Intel Core 2 Duo and Intel Pentium Dual Core.

---

### Post by ubuntu27 on 2010-05-19
My 2 laptops run Fedora Linux 12 64-bit with KDE, and Ubuntu Lucid 64-bit.

Both of my laptops has 3 GB of RAM, and they are doing fine..


And in fact, not just fine, but they work very well. I never had trouble with installing software.


And in a side note, Ubuntu 64-bit is faster than my Fedora 64-bit.

As for Flash.. just look for Flash Install Script in this forum for Flash 64.

**GO FOR 64**

---

### Post by formaldehyde_spoon on 2010-05-20
> **Paqman said:**
> I suspect his point was that they were written with 32-bit in mind, in the same way that most software is still written for a single core. You can compile the code for 64-bit, just like you can run a single-threaded app on a multi-core machine, but you won't see the real benefit of your architecture.
Whether the code makes use of 64 bit capabilities depends on your compiler, but the single/multi thread problem can't be solved by your compiler.

---

### Post by OooBuntuRox on 2010-05-20
[SIZE=2]> **3Miro said:**
> The only issues that exists with 64-bit Ubuntu are:

1. Flash can be tricky. I have been using it and it is fine, but it often requires a bit of extra work.[/SIZE]> **3Miro said:**
>  [SIZE=2]

2. Some WMA codecs will not work (you can fix that with recompiling your own version of 32-bit mplayer).[/SIZE] [SIZE=2]

3. There might be some proprietary drivers (such as Canon printers) that don't work for 64-bit.[/SIZE] [SIZE=2]

Overall, 64-bit is 10 - 30% faster for regular apps and it can get twice as fast for some heavy video conversions and such. You can also use more RAM.[/SIZE] [SIZE=2]

The FOSS apps in the Ubuntu repos have been compiled for 64-bit machines. The only 32-bit apps in the 64-bit repos are proprietary ones.[/SIZE] [SIZE=2]

BTW I have been using 64-bit Linux and mixed 32 and 64-bit apps on both Intel and AMD CPUs with no trouble. That is AMD Athlon X2, Intel Core 2 Duo and Intel Pentium Dual Core.[/SIZE] [SIZE=2]

I stopped installing flash anyway. Less ads and now I don't have to fiddle with "flash block" so much.

I suppose I should look closer at my cpu/ motherboard as well. Back at the turn of the century... when they had sx and dx chips there was a little trick intel played with internal verses external bus size. Like you may have a 32 bit internal but a 16 bit external bus... I guess I should figure out what I have. It's probably a true 64 bit external bus... but honestly, I never checked.

Some good comments/ thinkers in this thread. Thanks everyone.[/SIZE] 

[SIZE=2]Oh, Here it is:

Data bus width 64 bits
DRAM bus  width dual channel (2) 64-bit buses
Processor address 36 bits bus  width

Well, if the dram is 64 bits, doesn't that imply that the  external data bus is 64 bits wide?
What does the 36 bits bus width  for the processor imply?

Or is it two 64 bit internal data busses  and then two 32 bit external address busses?

Anyone up on the  hardware side of it?[/SIZE]

OooBuntuRox, :guitar:

---

### Post by cascade9 on 2010-05-20
> **del_diablo said:**
> Its x86, it hardly matters. Intel tried a pure x64 version, it failed because nobody wanted to lose the backward compability over nothing good. Basically their x64 version is the exact same as AMD's x86-64 BUT it can't run 32-bit code, it did not toss over board all the useless **** that was still on x86.

Now, where are you getting your information?

Itanium failed because it was late, very late, very expensive, slower than the x86 CPUs around at the time, and was aimed at the server market/'high end', not desktop use.   

It was NOT 'the exact same version as AMDs x86_64'. 

Itanium 1 had hardware x86 instruction translation (also very slow, but it worked) Itanium 2 dropped the hardware, moved to software x86 emulation.

---

### Post by OooBuntuRox on 2010-05-20
[SIZE=2]Hey cascade9,

I see you still have 9.04 listed on your  name tag. Is that just in need of update or are you hanging back for the 10.04 wrinkles to go away? I liked 9.04 a lot. I upgraded to 9.10 then went back to 9.04 until 10.04 came along. I've decided I might only upgrade each time the next LTS comes along...

OooBuntuRox[/SIZE] :guitar:

---

### Post by cascade9 on 2010-05-20
> **OooBuntuRox said:**
> [SIZE=2]Hey cascade9,

I see you still have 9.04 listed on your  name tag. Is that just in need of update or are you hanging back for the 10.04 wrinkles to go away? I liked 9.04 a lot. I upgraded to 9.10 then went back to 9.04 until 10.04 came along. I've decided I might only upgrade each time the next LTS comes along...

OooBuntuRox[/SIZE] :guitar:

Its still there because that is the last ubuntu release I played with for more than an hour or 3. I have installed 9.10 for afew people, but that wasnt really enough time to get a 'feel' for it as an OS.I will have to give 10.04 a bit a of a try, probably in a week or two. I'm not that worried by wrinkes, as I really cant see myself changing from my current 'main use' distro, but it would be nice if there werent any. ;)

---

### Post by philinux on 2010-05-20
> **3Miro said:**
> The only issues that exists with 64-bit Ubuntu are:

1. Flash can be tricky. I have been using it and it is fine, but it often requires a bit of extra work.

Not had a problem since I uninstalled the 32 bit version and got the 64 bit libflashplayer.so from adobe and stuck it in ~/.mozilla/plugins. One file in one folder for single user anyway. Couldn't be simpler.

---

### Post by McRat on 2010-05-20
New user.  64-bit would not allow wireless networking for me, but 32-bit did.  It also reported HDD size wrong (2TB for a 320gb drive) for me.

IIRC, you will have to use 64bit to address HDD's larger than 2TB, and the new 3TB drives are coming.

---

### Post by WinterRain on 2010-05-20
> **OooBuntuRox said:**
> As, why would you include 64-bit specific processor calls in an app written for 32 bit architecture. Kind of like putting a 4 cylinder (32 bit apps) in a Ferrari (64 bit kernal) because it still ***looks*** fast.... hey?



Bad analogy. With 64bit, I can use 32bit apps when needed, but get the benefits of using a 64bit OS, (address more memory, faster) but if I use 32bit OS, I'm stuck with 32bit apps and get no extra benefits.  See?

---

### Post by OooBuntuRox on 2010-05-20
> **cascade9 said:**
> Its still there because that is the last ubuntu release I played with for more than an hour or 3. I have installed 9.10 for afew people, but that wasnt really enough time to get a 'feel' for it as an OS.I will have to give 10.04 a bit a of a try, probably in a week or two. I'm not that worried by wrinkes, as I really cant see myself changing from my current 'main use' distro, but it would be nice if there werent any. ;)

[SIZE=2]Gotch-ya. Is it possible the wrinkles are intentional for those converts who miss using windows? Just kidding. I still use both but prefer Ubuntu Linux. Almost got a MAC as well a few years back just to see what the fuss was all about. Ubuntu will do. I really enjoy all the repository apps.


[/SIZE]> **WinterRain said:**
> Bad analogy. With 64bit, I can use 32bit apps  when needed, but get the benefits of using a 64bit OS, (address more  memory, faster) but if I use 32bit OS, I'm stuck with 32bit apps and get  no extra benefits.  See?

Acknowledged. Someone else make a joke of it but also a good point by comparing 8-16 and 32 bit CPU's. When I thought back... the rest started to fall into place. I figure I'll stick with 64bit not 32 bit. 
[SIZE=2] 
regards y'all, OooBuntuRox[/SIZE] :guitar:

---

### Post by pluto4ps on 2010-05-21
Go for 64 bit....its future and its fast....you have the right hardware to match with 64 bit fastness....
Think if you have 500cc bike and 1000cc bike which one do you prefer??? 
1000cc...Right????
People who don't know and are afraid of riding 1000cc bikes will stay to 500cc....

So if you want to learn and Advance then go for 64 bit....

---

### Post by kaivalagi on 2010-05-21
I've been using 64 bit linux since I first had hardware to support it (amd64 ages back, now dual/quad core intel) and all I can say is it's great, there were the early problems with flash, but now I have zero issues ever...

---

### Post by OooBuntuRox on 2010-05-21
[SIZE=2]> **kaivalagi said:**
> I've been using 64 bit linux since I first had hardware to support it (amd64 ages back, now dual/quad core intel) and all I can say is it's great, there were the early problems with flash, but now I have zero issues ever...
[B]
Thanks for the Links! I'll poke around and have a look see! [/B]

Also, the coordinates you listed could come in handy if anyone gets a wrinkle in their crumpet or insists on more answers from you. I was testing Google Earth...
Was that you swimming in the pool out back? :lolflag:
 [I hope you have a good sense of humor].

**In all honesty, many thanks for your kindness/ generosity in sharing your efforts!**[/SIZE] 
Regards, OooBuntuRox :guitar:
 [SIZE=3]**Hey kaivalagi, can't thank you enough.** The conky hardcore site seems to be just what I had in mind/ needed. Many thanks. I'll be poking around there for a while. 8-)

[/SIZE]

---

### Post by kaivalagi on 2010-05-22
No probs, must be next doors pool, we don't have one...now if I'd have done more "for sale" development with Windows I might :)

Glad the links help and just note the conky hardcore stuff is really the effort of others, I've just setup the ubuntu repo for related stuff I've done

Cheers

---

