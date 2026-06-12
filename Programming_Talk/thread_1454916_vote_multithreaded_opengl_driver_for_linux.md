---
title: "vote: multithreaded opengl driver for linux"
date: 2010-04-15
forum: Programming Talk
---

### Post by Geri_lgfx on 2010-04-15
Hi all, i got a fully working opengl 1.3 implementation. Its related to mesa3d, but mesa3d is only single-threaded, this can be scaled up 4 cores currently (later can easilly expand).

-easy install (just a libGL.so.1, only need to be copyed)
-can come with MMX/SSE/SSE2/3dnow! support, or without them too
-driver can run quake3demo (win ver tested) and xmoto (win ver tested) playable on a modern 2 core'd computer. (of course a lot of other games are also tested, like wolfenstein3d, quake2, etc)
-currently its 32 bit version, precompiled binary

The original project called TitaniumGL: [http://TitaniumGL.tk](http://TitaniumGL.tk) 
TitaniumGL is a opengl multiwrapper for game developers. 

**Now i want to create a version that targets end-users, and linux. **With 3d acceleration, a very lot user has problem under linux, so this is why a good multicpu software renderer would help to them persons. I alreday had a previous public pre-alpha test with the code with different name, but since that i rewrited the rasterizer. 

Now i am needing the opinion of the community. Please vote and/or share your opinion about this.

---

### Post by Geri_lgfx on 2010-04-17
oh i post some screenshots too:

[IMG]http://legend.uw.hu/TitaniumGL/gal2/q3.jpg[/IMG]


[IMG]http://legend.uw.hu/TitaniumGL/gal2/wolf.jpg[/IMG]

quake3 demo and wolfenstein demo

---

### Post by slavik on 2010-04-18
how about numbers from a benchmark?

---

### Post by Geri_lgfx on 2010-04-18
On the webpage, it is a result from quake3 demo. Now i dont has any other res. Most quake3 based games and most of the lot of other opensource games should run playable on a modern cpu of todays.

---

### Post by soltanis on 2010-04-18
Just to clarify, is this a software renderer implementation of OpenGL across multi-core CPUs? Because I was under the impression most of OpenGL magic takes place on the GPU, which integrated chipsets aside are massively parallel processors already.

---

### Post by Geri_lgfx on 2010-04-19
This opengl implementation using multiple cpu cores simultanously to produce the 3d graphics. The target is the systems, where for some reason no GPU based opengl available.

---

### Post by cb951303 on 2010-04-19
> **Geri_lgfx said:**
> The target is the systems, where for some reason no GPU based opengl available.

which is maybe %0.0000001 of the todays computers?
seriously though what need will it serve?

btw, gallium3d has a software rasterizer which is superior than mesa's.

---

### Post by Geri_lgfx on 2010-04-19
,,which is maybe %0.0000001 of the todays computers?''

[http://www.google.hu/search?hl=hu&safe=off&client=firefox-a&hs=yl0&rls=org.mozilla%3Ahu%3Aofficial&channel=s&q=linux+opengl+crash&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.hu/search?hl=hu&safe=off&client=firefox-a&hs=yl0&rls=org.mozilla%3Ahu%3Aofficial&channel=s&q=linux+opengl+crash&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=)

according to this, ,,who needs'' means 310 000 user :D

---

### Post by cb951303 on 2010-04-20
> **Geri_lgfx said:**
> ,,which is maybe %0.0000001 of the todays computers?''

[http://www.google.hu/search?hl=hu&safe=off&client=firefox-a&hs=yl0&rls=org.mozilla%3Ahu%3Aofficial&channel=s&q=linux+opengl+crash&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.hu/search?hl=hu&safe=off&client=firefox-a&hs=yl0&rls=org.mozilla%3Ahu%3Aofficial&channel=s&q=linux+opengl+crash&meta=&aq=f&aqi=&aql=&oq=&gs_rfai=)

according to this, ,,who needs'' means 310 000 user :D

which is smaller than I think.
also as I said before we have gallium3d for them we don't need a proprietary driver.

---

### Post by Geri_lgfx on 2010-04-20
,,we don't need''
No. Let me correct. ,,i don't need''.

Gallium3D should be a famous product, once. i have the jitters for them!


,,which is smaller than I think.''
:lolflag:
310.000 user is smaller than %0.0000001? What are you talking about? Did you realized that linux got ~1% market share? 2billion computer users on the world, 1% of 2 billion is 20million, this is the linux users. 

And the 310.000 number, who got problem. Actually, its not all problematic case, google does not find all problematic threads to this keyword (and finds some wrong matches also). So count with minimum. AND: 2/3 of peoples according to world factbook does not use internet. So according to mathematics, the number who had problem with linux's 3d acceleration is **minimum** 1 million person. Wich is 5% of the total users according to mathematical facts. 

So please, dont trololo my thread. Be constructive. I am accepting your opinion, but this, what you do, is a serious **FAIL**.

---

### Post by Npl on 2010-04-20
and your renderer is supposed to fix all 300.000 users problems (even if those questions actually involved driver-problems and not say.. asking for help with programming)? I dont think so, judging from your site you arent implementing alot of features (atleast now), probably just enough for old Quake-Engine games.
Certainly your 1 million potential users is based on assumptions and not mathematical facts.
And how do you want to reach those users without internet access? Probably hard selling them anything.

On topic, well if you want to sell such a product it would`ve to be really cheap as 20€ buys you a Nvidia Card which totally destroys any software renderer, has good drivers and tons of D3D10/OpenGL3.x features your driver is lacking.

---

### Post by Geri_lgfx on 2010-04-20
Thank you for the response!

I did not sayd that it will resolve every person's problem. I sayd, it has reason for existence. And what, if your motherboard just say kernel panic to your nvidia card with the accelerated drivers? You buy a new computer? Do it! :D (3d acceleration-related problems under linux is far too complex to describe them in here). OpenGL 3.0 and above is used by 0 games currently. Most linux games using opengl 1.1 based features, except some commercial ones. Pixel shader, and other features are not even a good idea to be emulated: they would be result like 0,2 fps, wich is uplayable. So 1.3 is far enough now.

Btw, i dont want to become rich from this program, this is why i thinking to give 2-threaded version for free. But who has money for a 4 core'd computer, has money to give some to me also, so this is like a guerilla-donation. ;) :D

---

### Post by Simian Man on 2010-04-20
Sorry but I can't see anybody paying for this.  There *are* a lot of people who don't have full 3D acceleration support, but if Mesa isn't good enough for them, I think they will just buy a new graphics card rather than your drivers, no matter how much faster than Mesa they are.

I know this can't have been easy to implement, so good work though.

---

### Post by Geri_lgfx on 2010-04-20
Thanks, yes, mee too think mostly like this, but i made this poll to made a good decision about the software, how should i do a next step.

(but well it was a fail from me to start the topic in a programing thread instead of some end-user related topic)

---

### Post by Npl on 2010-04-20
> **Geri_lgfx said:**
> Thank you for the response!

I did not sayd that it will resolve every person's problem. I sayd, it has reason for existence. And what, if your motherboard just say kernel panic to your nvidia card with the accelerated drivers? You buy a new computer? Do it! No, Id try to fix it by using different drivers.

> **Geri_lgfx said:**
> :D (3d acceleration-related problems under linux is far too complex to describe them in here). OpenGL 3.0 and above is used by 0 games currently. Most linux games using opengl 1.1 based features, except some commercial ones. Pixel shader, and other features are not even a good idea to be emulated: they would be result like 0,2 fps, wich is uplayable. So 1.3 is far enough now.I think some Emulators of the PS1-PS2 age consoles use GL 2.0, UT 2004 probably uses it too. Its not like there are alot Linux-native games to choose from. You can "fix" pretty much everything if you just plug in a 20&#8364; Nvidia-Card which was my main point.

> **Geri_lgfx said:**
> Btw, i dont want to become rich from this program, this is why i thinking to give 2-threaded version for free. But who has money for a 4 core'd computer, has money to give some to me also, so this is like a guerilla-donation. ;) :DI`d think those kind of people wont be content with software-rendering =)

Your driver surely would be a nice fallback-option (I see why a game-dev would love it), but unless it comes pre-installed (either with the OS or the game) I dont think it will reach many people. Even if you just have to copy over a library its still messing with OS-innards and might lead to trouble if you replace an existing file or the OS`s packet-manager decides to overwrite/remove it.

Oh, and for the record I voted 2. I can`t think of a reason why I could be totally against it

---

### Post by Geri_lgfx on 2010-04-20
Well, trying different drivers of course can help in some situations. Fixing problems with buying a new graphics card is a nice idea, but you may should use a chainsaw to swap it, if you has a notebook (wich is a bigger market now then desktop pc-s). 

But your latest point is good. So you say, i should probably try the software to sell to some big linux distributor to be part of the OS by default? This is a very interesting idea. Maybee some bigger distributor is interested in it.

---

### Post by Reiger on 2010-04-20
I'd have to agree with Simian Man here: facing the choice between:
[list="1"]
[*]Dedicated graphics card
[*]Integrated graphics
[*]Old style mesa 3d or upcoming gallium 3d
[*]Your renderer
[/list] 

Most (really: most people who have shopped for a PC/laptop by themselves before) people will know about (1), (2) and will reply `what?' for the other two. 

Then when it comes to price point the (3) is at least a hassle-free experience on most linux distributions because distributions take care to maintain a coherent graphics stack around those. For free. That is not just money, it is also a lot of time & frustration (dependency hell) you can save yourself right there.

Finally, then, people who know that they need some sort of (3) or (4) will probably also know they get a much better performance deal out of buying and installing (1) or postponing & later upgrading wholesale in case of (2). Remember that even simple integrated graphics of DirectX 10 generation and later will sweep the board with most CPU software solutions if there is a half decent driver stack to back them up on the software layer. If only because it leaves considerably more CPU free to handle the program logic and interrupts.

---

### Post by Geri_lgfx on 2010-04-20
Well, so according to your oppinion, selling licenses to linux distributors would be the best way. Are somebody heard any distributor, who are searching a product like this?

---

