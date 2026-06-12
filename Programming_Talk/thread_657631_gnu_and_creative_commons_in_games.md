---
title: "gnu and creative commons in games"
date: 2008-01-03
forum: Programming Talk
---

### Post by Nerdcore Steve on 2008-01-03
I've sent the below email to [email]gnu@gnu.org[/email] and haven't gotten a response yet. I was interested what anyone here on the ubuntu forums thought:

I'm not a professional developer but I've been messing around with a point and click javascript text adventure game. The game engine takes an xml file which is the games content. The xml file contains a description of the rooms you encounter and of the choices you can click on when you get in that room. I got to thinking that I'd like to release the javascript game engine on the gnu license. I know people would take the code anyway, but it would be mainly to encourage people to contribute improvements to it. I was also thinking I could put the xml game data out on the creative commons license. Then I wasn't sure if the gnu license would do essentially the same thing and maybe I was making things too complicated. Until I had a thought. 

Wouldn't it be cool if there was a bunch of free game engine software that could be used in conjunction with copyrighted game content, which could include, art, animation, game scripts, scripts governing character behavior, music, etc., but used open source software? That way a bunch of people who didn't know much about programming but were good artists and writers, might make an RPG that they owned, that they could even sell if they wanted to. Or wouldn't be nice if I could take, say, the code from Freedroid, and put my own art, sound effects, and music in it, maybe make some changes to the software, which I would release under the terms of their open source license, but keep the game content as a creative commons non-commercial distribution license and sell it on a web site. 

It think this would encourage a lot of people who wouldn't make games otherwise, into making games. Is this allowed in the terms of the gnu license? Would I have to make another license instead? Are people already doing this? Do you see any potential problems with this idea?

---

### Post by samjh on 2008-01-04
> **Nerdcore Steve said:**
> Are people already doing this?

Yes they are.  ID Software released its Quake 2 and Quake 3 engines under GPL, and there have been a lot of free and open source games using the original engines or modifications to the engines, but with custom art and content.

See [http://en.wikipedia.org/wiki/Id_Tech_2](http://en.wikipedia.org/wiki/Id_Tech_2) and [http://en.wikipedia.org/wiki/Id_Tech_3](http://en.wikipedia.org/wiki/Id_Tech_3)

---

### Post by Nerdcore Steve on 2008-01-08
Could I then, make a game using the id Tech engine with all original art, music, etc even tweak it to be say a first person rpg, and then release the source code under gpl but still sell the game?

Or could I take the super tux engine, again using all original art and music, and tweak the engine so it's a rpg platformer with fighting game moves, release the source code under gnu, but charge for the game?

---

### Post by samjh on 2008-01-09
You cannot use idTech 2 or 3 with original Quake media.  The engine itself is free and open source, but the media is copyrighted by ID Software.

Sorry for not providing a satisfactory answer, but your meaning of "original" is a bit vague.  Are you talking about the original media from the game itself, or original media that you created?

To explain clearly:

[quote=Nerdcore Steve]Wouldn't it be cool if there was a bunch of free game engine software that could be used in conjunction with copyrighted game content, which could include, art, animation, game scripts, scripts governing character behavior, music, etc., but used open source software?[/quote]That is illegal, unless you purchase rights to use that copyrighted content from the publisher.  As long as the game contents are protected by the publisher under copyright laws, you cannot use them without their permission, even if the game engine is free and open source.

[quote=Nerdcore Steve]Or wouldn't be nice if I could take, say, the code from Freedroid, and put my own art, sound effects, and music in it, maybe make some changes to the software, which I would release under the terms of their open source license, but keep the game content as a creative commons non-commercial distribution license and sell it on a web site.[/quote]This is possible, as long as Freedroid's license allows it.  If Freedroid's game engine is free and open source, and you add your own original game content, and release the final product as another open source product, that is legally OK.

[quote=Nerdcore Steve]Could I then, make a game using the id Tech engine with all original art, music, etc even tweak it to be say a first person rpg, and then release the source code under gpl but still sell the game?[/quote]You can make a game using free and open source licensed idTech engines (idTech 2 and idTech 3), but you cannot use the original copyrighted art, music, etc.  The content is still under copyright.  So if you want to tweak any of the game content, the content must be either your own creation, or someone else's creation that has been licensed to allow you to use them.

GPL does not restrict one from selling anything.  You can release a product under terms of the GPL and still sell it.

[quote=Nerdcore Steve]Or could I take the super tux engine, again using all original art and music, and tweak the engine so it's a rpg platformer with fighting game moves, release the source code under gnu, but charge for the game?[/quote]As long as the original art and music are licensed to enable you to use them in such a manner, then yes.  You need to check what the original art and music is licensed under.  If you mean "original" as in your own creation, then do whatever you want with them.

---

