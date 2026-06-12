---
title: "Futile Hope: MS Visual Studio .NET on Ubuntu?"
date: 2007-03-25
forum: Programming Talk
---

### Post by SwedishHatFaction on 2007-03-25
I have a dual boot of XP Pro and Edgy and back on my Windows partition, I installed Microsoft Visual Studio .NET 2003. Is there any way to run Visual Studio or even just a Visual Basic IDE in Ubuntu? Any help would be greatly appreciated.

---

### Post by Hairy_Palms on 2007-03-25
you could take a look at REALBasic, its free on linux, i find it much better than VS.net. it compiles single executable programs so no need for dlls or external libraries,

[http://www.realbasic.com/](http://www.realbasic.com/)

---

### Post by pmasiar on 2007-03-25
> **SwedishHatFaction said:**
> Is there any way to run Visual Studio or even just a Visual Basic IDE in Ubuntu? 

LOL obviously not. You may try Wine but don't be surprised if things do not work under emulator.

The whole point of maintaining Microsoft monopoly is to make Windows platform indispensable. MS was scared enough when browser-based application became possible - and is working hard now creating incompatible IE features/extensions/implementations to make Windows the best platform - like when webmaster makes website "best viewed in IE". ActiveX controls and such.

MS adds compatibility measures with other platforms only when their biggest customers whine hard and long. From MS profit perspective, porting VS to Linux would counterproductive and makes no sense at all.

GNU/Linux and Microsoft Windows are competitors in market share and mindshare. Like Ubuntu bug #1 is [Microsoft has a majority market share](https://launchpad.net/ubuntu/+bug/1) and we are working to fix it :-) MS developers are working hard to maintain their desktop majority using any measures they have available, including deliberate incompatibility. It is nothing personal against you - it is business. :-)

And I fully understand why MS does what it does - they have responsibility first to their stockholders (including Bill Gates) to deliver best returns on investment, and they do just that. 

And same is in place in free software world: sometimes it makes sense to port a free tool to windows, and sometimes it does not. So far quest for world domination continues as planned. :-)

---

### Post by j_g on 2007-03-25
You know, you really are _terrible_ at advocating Linux. Your entire reply to the OP consists of "I don't know", followed by an unrelated anti-everything-associated-with-MS-and-Window rant that at best, will bore the OP, and at worst, annoy him and make him feel like Linux has nothing to offer him except the "privilege" of hearing how the tools he has willingly chosen to use are allegedly "satan's handiwork".

That sort of thing already helped kill the Amiga and OS/2. If you want to get fanatical about something, try a local sports team or something.

---

### Post by cunawarit on 2007-03-25
MonoDevelop does list a Visual Basic GTK and console project types. I have never tried them as I am not a VB developer, so no idea how good it is with VB, but it is alright with C#. Not as nice as Visual Studio 2005 yet, but it already very useful on version 0.13... 

[http://packages.ubuntu.com/edgy/devel/monodevelop](http://packages.ubuntu.com/edgy/devel/monodevelop)

:)

---

### Post by Wybiral on 2007-03-25
> **j_g said:**
> You know, you really are _terrible_ at advocating Linux. Your entire reply to the OP consists of "I don't know", followed by an unrelated anti-everything-associated-with-MS-and-Window rant that at best, will bore the OP, and at worst, annoy him and make him feel like Linux has nothing to offer him except the "privilege" of hearing how the tools he has willingly chosen to use are allegedly "satan's handiwork".

That sort of thing already helped kill the Amiga and OS/2. If you want to get fanatical about something, try a local sports team or something.

lol, you're so defensive... How did you help the OP? You didn't... All you did was voice your opinion. Right? How is that any different then pmasiars post?

Besides... It _IS_ true, MS is not going to release a non-MS version of MS studios... So pmasiar wasn't too far off.

As cunawarit mentioned, Mono has been working on .NET alternatives that might be worth looking into... But don't expect anything great since they have to be careful about how much their product resembles MS's product.

---

### Post by zekopeko on 2007-03-25
install windows in vmware server and then look at this howto:

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by Mirrorball on 2007-03-25
> **Wybiral said:**
> lol, you're so defensive... How did you help the OP? You didn't... All you did was voice your opinion. Right? How is that any different then pmasiars post?
He doesn't know, but he really is _terrible_ at advocating non-fanaticism.

---

### Post by pmasiar on 2007-03-26
> **j_g said:**
> You know, you really are _terrible_ at advocating Linux. ... try a local sports team or something.

Ok J_G, I appreciate you toned down your rhetorics. So before we start explaining how we have different *opinions*, let's agree on *facts*.

1) Microsoft was convicted as being monopoly in US courts.  True or false?
(I know it was overturned on appeal, in 2001 when US administration changed)

2) Microsoft as company, CEO and board, has [fiduciary duty](/http://en.wikipedia.org/wiki/Fiduciary) to protect interest of the stockholders, to earn most profit they legally can, under economic system called  [capitalism](http://en.wikipedia.org/wiki/Capitalism). True or false?

3) Keeping the monopoly increases profit. True or false?

4) MSFT has enough profits to pay for porting VS to Linux if it was in their (and their stockholder's) interest, and if MSFT decides *not* to port, it does so for other reasons, not for lack of funds. True or false?

Do we agree on facts? I answered "yes" on all. 

If we do not agree on facts, on postulates, discussions does not make any sense.

Now my *opinions*: 

Exactly as for MSFT does not make sense to port VS to Linux, *IMHO* for free software does not make sense to do it either. Some people do try port different Windows applications, using wine, Mono and other tricks. It is my *opinion* that this is a sucker game, because all they do is chase changes in Windows API, and when they have almost usable Wine after 10 years of efforts, MSFT changes to Vista and they can start chasing it again. For some people the limited API they managed to get working is good enough, and bless them. Other people are not so lucky. I would not waste my time on such IMHO futile effort, and I would advise anyone interested in my advice against doing so. Of course if someone is strongly interested to chase MSFT's tail, and does it at their own time and money, well - go and do it, it is waste of effort but people have stranger hobbies. :-)

If lot of smart people will go into that project, it is even possible that for short period of time those smart people will get something usable. Then MSFT has problem: their platform is not requirement anymore, so what whey can do to protect their stockholders interests? They can  try changing API a little (by some required security fix or something), or they can sue company developing those solutions (and Novel made smart more to get protected from that threat).

I perfectly understand why MSFT does what is does, and how it makes sense for *them*. I do not own MSFT stock, so I am not interested in supporting that monopoly. I do not *hate* them, I do not say they are *great satan* or something. I just do not agree with them. I believe that given enough time, free software can out-inovate and out-perform any proprietary software. Until then, I try to use free software when I can. I am patient. It is getting better every half-year :-)

And I perfectly understand that for some people free software as it is *right now* is not good enough, and they may go for proprietary software. No problem, it is not like they are spending my money. In free market they can make their own decisions, likevise I can do too.

You can disagree with my opinions but please don't tell me crap like that I am (or my attitude is) responsible for demise of Amiga. Amiga lost in competition between different proprietary platforms, please explain me how Amiga is relevant in competition between free and proprietary software.

Would be world nicer if MSFT played nice with free software and helped interoperability? Sure it would. Do I see it happening anytime soon? Yeah, I'll have sizzling hot pork wings with that.

I am realist. Definition: realist sees world as it is, and not as it should be.

I do not hate MSFT (it behaves as monopolist should), it's developers (I know most are much richer than me, but I am richer than most people in Africa), or users of proprietary software (I use it too when I have too). I want to have right to my preferences and opinions, thats all.

BTW I am not interested at all in any sport teams, I prefer do sports myself instead of wasting my time watching other people doing it. I watch it very rarely, must be *some* competition.

I waste my time posting to forums instead :-)

---

### Post by Tomosaur on 2007-03-26
Come on guys, stop derailing the topic.

@Swedish - you won't be able to get the current version of VS to run properly, even on Wine. You COULD try Cedega (an alternative to wine, but more focused on graphics/games etc. It's free if you use the CVS version (meaning you need to compile it yourself), but it's a long shot.

I would second REALBasic, although you could have a look at Gambas.

---

### Post by _duncan_ on 2007-03-26
It's not an ideal solution, but it is possible to install Windows XP Pro as a virtual machine in Ubuntu, then install Visual Studio within the virtual machine. So you basically have 2 OS running in the same computer at the same time, with Ubuntu running as host OS and Windows XP running as guest OS.

It worked for me with VS 2005, don't see why it shouldn't for VS 2003.

---

### Post by stijngysemans on 2007-03-26
> **_duncan_ said:**
> It's not an ideal solution, but it is possible to install Windows XP Pro as a virtual machine in Ubuntu, then install Visual Studio within the virtual machine. So you basically have 2 OS running in the same computer at the same time, with Ubuntu running as host OS and Windows XP running as guest OS.

It worked for me with VS 2005, don't see why it shouldn't for VS 2003.
I'm really curious about how this setup performs because my .net development (WPF and .net 3.0) is holding back my switch for my professional computer. Can you share your experiences and hardware configuration with us?

---

### Post by _duncan_ on 2007-03-26
Hardware requirement isn't very high. The slowest computer I tried it on was a Sempron 2400+ with 1 GB RAM. This is considered old by today's standards.

I followed [[COLOR="Red"]_this_[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=183209") link to set up VMWare Server and Windows XP Pro, allocated 512 Mb for the virtual machine, then installed Visual Studio on the XP virtual machine just like I would on a normal XP installation.

My experience is that you need at least 1 GB of RAM, more will be better but not absolutely necessary. Anything less and you will really experience sluggishness when operating both OS. It also helps if you have a very fast processor (dual core would be really nice) since the 2 OS will be sharing the same CPU.

One bonus about this set-up is I can access servers running in the host OS (Ubuntu) from the guest computer (xp virtual machine) . So if you have PostgreSQL, MySQL, Apache, etc. running in Ubuntu, you can just connect to it from the XP virtual machine, as if you have 2 *real* computers connected by LAN. You can even share files between the 2 by setting up Samba.

The added processing load tends to increase processor temperature by about 3-5 degrees celsius. This should not be a problem for most computers, although some laptops operating at high temperatures already with 1 OS may not be able to accommodate the heat increase.

The link I gave you also provides the link to the VMWare website. It will be worth your time to go over there and read up on what virtualization can do for developers.

---

### Post by stijngysemans on 2007-03-26
Thank you for all the information.
I think I need to buy a new computer because with 512 of ram in total and only an amd 1800+

---

### Post by mikalh on 2007-03-29
Mono 1.2.3 has a new Visual Basic 8.0 (2005) compiler, and MonoDevelop from SVN supports this.

---

### Post by mardawi on 2007-04-03
Thanks a lot for sharing the experience.

I was able to run VS.net 2003 on ubuntu 6.10 using windows XP vm and rdesktop 1.5 (previous versions will not give the same results)

Have a look at the attached screenshot, it totally looks like actually running vs on linux (except for the theme which can be changed). I've created a 512 MB ram 6gig hd vm to install windows XP, and the performace of running vs using rdesktop is totally acceptable (i'm running on a 1.6ghz laptop, 1.5gb ram)

i followed this great how-to to install vmware server (which is now for free)
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

and this nice article to get rdesktop to work
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

I had to compile rdesktop 1.5 from source since the latest version wasn't available on app-get

I hope that helps

---

### Post by cprofitt on 2007-04-03
I am not aware of anyway to run in IN Ubuntu, but you could download the free version of VMWare Server - load an instance of Windows in that and then run VStudio.

I am not sure what you are trying to accomplish -- I am trying to switch to Ubuntu as my desktop OS of choice, but I have to run a Windows VM to manage my AD environment and support the old .Net applications I wrote.

---

### Post by mdurham on 2007-04-04
Why not try VirtualBox instead of VMWare? I found it much smaller, easier to use and it's in the repos.

---

### Post by mardawi on 2007-04-04
i've read somewhere that the guest OS in VirtualBox runs a little bit slower than vmware. I haven't tried it though.

---

