---
title: "id tech 3 (&quot;quake 3 engine&quot;)"
date: 2008-06-07
forum: Programming Talk
---

### Post by LoneWolfJack on 2008-06-07
Hi there,

are there any people around here who have already been working with id tech 3?

I'm running a small software company and we decided to license id tech 3 for a game project (not a shooter, sorry folks :) ) and I would be willing to spend some dollars on someone who can share his experience with id tech 3 so we don't have to work all the way through its internals ourselves.

---

### Post by Mickeysofine1972 on 2008-06-07
> **LoneWolfJack said:**
> Hi there,

are there any people around here who have already been working with id tech 3?

I'm running a small software company and we decided to license id tech 3 for a game project (not a shooter, sorry folks :) ) and I would be willing to spend some dollars on someone who can share his experience with id tech 3 so we don't have to work all the way through its internals ourselves.

Have you already spend the dollars on this tech? there are some very good open source systems available that you could use without having to divulge you sources if thats your concern.

Or is it that the tech 3 stuff has a special feature you need?

Mike

---

### Post by LoneWolfJack on 2008-06-07
we haven't yet spent the dollars on this engine, but no other engine has the three distinctive features we are looking for: it is available for linux/mac/windows in its current version, it is a proven product and there is a non-GPL version. Also, we prefer C over C++ (even though we'd go with C++ if we have to).

We have been looking at many interesting engines (crystal space, irrlicht, ogre, you name 'em), but all had certain weak spots or were not available for either linux or windows.

However, if you think there's a good open source game engine we have not yet had a look at, I'll be happy to check it out.

---

### Post by LoneWolfJack on 2008-06-08
*bump*

still looking...

---

### Post by harry666t on 2008-06-08
I have some experience with mapping & modding for another game based on Id3, namely Jedi Academy. I'm just a hobbyist, I haven't ever done anything professionally with this stuff and although I have some good understanding of Id3's general architecture, I think anyone after a couple of hours/days/weeks of playing with the source would give you more interesting details (I'm assuming that all you want are the details & glitches & such things).

What I'd do if I were you, is to go to one of the developers of OSS Id3-based FPSs, such as OpenArena, Alien Arena, Tremulous... ([http://en.wikipedia.org/wiki/Id_Tech_3#Projects_based_on_the_GPL_source_release](http://en.wikipedia.org/wiki/Id_Tech_3#Projects_based_on_the_GPL_source_release)) and ask them directly for their experience with fighting the zomb^W^W^W rocking the^W^W whatever they do with that code, and offer them these bucks that you have prepared for that occasion. Names and emails of these guys should be right there in the sources.

Alternatively, you can already grab the vanilla GPL source from Id's home page, start the development without making any releases, find out if this junk suits your needs and fulfills your expectations, maybe hire someone with previous Id3 experience, and so on until you think that it's time to either make a release (then you hand out $10.000 to Id and remove the GPL boilerplate from the source) or abandon the Id3 (then, you haven't lost 10k bucks and have learned from your own experience).

If you are out looking for potential Id3 replacements, take a look at these lists:

[http://en.wikipedia.org/wiki/List_of_game_engines](http://en.wikipedia.org/wiki/List_of_game_engines)
[http://en.wikipedia.org/wiki/First-person_shooter_engine](http://en.wikipedia.org/wiki/First-person_shooter_engine)

I can't say much about any of the engines, but it shouldn't take that much time to visit each interesting project's website and find out if it meets your criteria.

BTW, is having a GPL engine really such a problem? The engine isn't much worth without the content, and the content is what you can make money out of. Not to mention the hassle with making the binary work on all flavors of Linux (trying to make GtkRadiant work under Debian was so painful that I've finally grabbed the source and compiled it myself).

---

### Post by LoneWolfJack on 2008-06-09
Ah, Jedi Academy... great game. Loved the mutated rancor level.

I may contact a couple of the guys behind those OS games.

As for GPL, the problem is that all changes to the engine would have to be published. Also, engine and game content are usually tied together so closely that it will be very difficult to decide what to publish and what not.

---

### Post by harry666t on 2008-06-09
You're right, sometimes it's questionable what would count as the "full, human readable source code" that the GPL is mentioning. IANAL, but we might use the original source release as a hint...

*goes to Id's site, DLs, unzips, looks around*

The readme is stating that not all code is covered by the GPL (some libs are using BSD-like permissive licenses). So the rest is GPL. Hm. Most of the stuff here seems to be just source code:

```
$ find -type f |egrep -vi '\.[ch](pp)?$'|wc
    497     500   13606
$ find -type f|wc
   1409    1412   35647
```

So, c, cpp and h files are definitely what'd need to be released. What about the rest... I've looked over that list and it's mostly readmes, makefiles, project files, assembly source code, etc. That'd be the engine.

Now the "content", something that you must provide by yourself and what is not covered by the GPL. Taken from JK3's assets[0-3].pk3:

botfiles, botroutes, eagle, effects, ext_data, fffx, fonts, forcecfg, gfx, levelshots, maps, menu, models, music, scripts, shaders, sound, strings, textures, ui, video.

The original Q3 source doesn't have a slightest sign of presence of all these things. Now, even if Id would come and tell you that the source you've released doesn't work without files X, Y, Z, it will still work perfectly without (at least): maps, models, textures, music, sound, shaders, effects. And that's a load of stuff for you to sell, or for someone else to try to eventually recreate.

Also... Suppose that your game will become a bigger commercial success. I can certainly tell you, if I could go and mod a game that I like, I'll like it even more. People in the JK3 community are still making maps, skins, saber hilts, 5 years after the release. Thanks to the release of MP DLL sources, many very enjoyable mods were created (for example JA+, also I've been an active member of the (sadly, now defunct) Lugormod community). My first battle with a bigger C project was also trying to make something funny with JK3's serverside DLL.

Of course all of this also depends on how much value you're going to bring with the content, and how much with a better engine. Since it's going to be a huge spinoff from the Q3 gameplay, I clearly see that there's much to be coded... But again, JK3 didn't suffer from releasing the SDK (yes, it wasn't the full source, but the Raven guys themselves told that they'd love to release code for jamp.exe if the licensing terms for ghoul2 weren't holding them back).

---

### Post by altonbr on 2008-06-09
The game [OpenArena]("http://en.wikipedia.org/wiki/OpenArena") uses [ioquake3]("http://ioquake3.org/"), you may want to contact them.

---

### Post by Frak on 2008-06-09
I've worked on the Tremulous project (FPS/RTS hybrid), and I must say that the ioquake3 engine is superb. I wouldn't blame you for licensing a proprietary version in the least.

---

### Post by altonbr on 2008-06-09
> **Frak said:**
> I've worked on the Tremulous project (FPS/RTS hybrid), and I must say that the ioquake3 engine is superb. I wouldn't blame you for licensing a proprietary version in the least.

Don't those two sentences contradict? Isn't ioquake3 open-source?

---

### Post by Frak on 2008-06-09
> **altonbr said:**
> Don't those two sentences contradict? Isn't ioquake3 open-source?
ioquake3 is open source, true. But in using it, I would use a proprietary version.

The experience should be the same or better.

---

### Post by LoneWolfJack on 2008-06-10
Like I said, the game is not going to be a FPS. I know several engines that would be more suited for our task, but none of them is available for licensing or within reach money-wise. After all, we're just a small software company that is not backed by investors.

Also, the stuff we need the engine for is only a part of the game, so releasing the source would be economic suicide. We have been considering building a special purpose engine ourself but this would certainly cost more than spending those 10k bucks on idt3 and modify it to the extend required. Not to mention the hassle with debugging the beast...

The most urgent task at hand is to find someone who can
- provide his thoughts upon embedding the engine in a GTK+ widget
- tell us about known issues and shortcomings

harry666t, I'm not up to date... did they release the source of JA or was it all about reverse engeneering DLLs again? Damn, I spent so much time squeezing information out of Microsoft's .mw4 format.

---

### Post by harry666t on 2008-06-11
Well... The SDK for JK3 was released shortly after the game (Autumn? Winter? of 2003) and it included:

Full, probably unmodified and very buggy source code for "basejka" 1.01 DLLs: jampgamex86.dll, cgamex86.dll, uix86.dll, compilable under Windows, or in case of jampgame, also under Linux; Various minor tools, including behaved, shadered, md3view, etc (for stuff like viewing / editing / compiling / whatever: effects, icarus scritps, models, shaders...); Sources for all Icarus scripts used in the game; source for behaved (the icarus compiler, IIRC, never toyed with scripts too much).

Also with GtkRadiant 1.4 came sources for a few MP and SP maps (including, but not limited to: mp/ffa5 (Taspir), t1_rail (the mission with train on Corellia), t2_rancor (the "smaller" rancor :P)). I do not know much about the licenses of the maps, but many people were releasing their custom modifications of them (and I too made a great mod of mp/ffa5, although it was before I fully realized the role of hints, portals and detail vs structural brushes in improving the efficiency of rendering, thus the framerate was a FAIL and I never made a release).

It is also a public secret that almost every mapper who feared not the commandline has decompiled many of the maps for his own studies, but I'm digressing here (:


As of embedding the Q3 renderer in a GTK widget. I have almost no experience with hacking GTK, but there's a widget that provides OpenGL view, right? Hmm... Doing "find -type f -print0|xargs -0 grep -E '#include.*GL'" tells me that there are totally 21 includes of GL headers in subdirectories: bspc/, unix/, renderer/, macosx/. My knowledge of Win32 API is like... Uh, there's no such knowledge :P but I fear that there might be no easy *and* cross-platform way to do this stuff... But I really might be wrong, it's just my intuition.

---

### Post by altonbr on 2008-06-11
By the way, because of your problem trying to find a Ubuntu Game developer LoneWolfJack, along with many others trying to find work around or with Ubuntu, I suggested on brainstorm the creation of [http://jobs.ubuntu.com](http://jobs.ubuntu.com) as a marketplace for jobs surrounding Ubuntu (ie: server administration, game development, etc.)

See it here: [http://brainstorm.ubuntu.com/idea/9704/](http://brainstorm.ubuntu.com/idea/9704/)

---

### Post by Mickeysofine1972 on 2008-06-12
Thats one REALLY great idea!

I have looked high and low for the bounties pages and can't seem to find them!

I for one would welcome so freelance project where I could make some pocket money.

Mike

---

### Post by altonbr on 2008-06-13
> **Mickeysofine1972 said:**
> Thats one REALLY great idea!

I have looked high and low for the bounties pages and can't seem to find them!

I for one would welcome so freelance project where I could make some pocket money.

Mike

:) Would you mind posting that on the Brainstorm site? :P

---

