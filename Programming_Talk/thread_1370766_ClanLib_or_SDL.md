---
title: "ClanLib or SDL?"
date: 2010-01-02
forum: Programming Talk
---

### Post by NinjaNumberNine on 2010-01-02
Which is more stable of the two, and which has more features? I am using a development app called "novashell" for a game I'm working on, and it uses ClanLib. Trouble being, I have encountered numerous bugs, and have not been able to compile it (ClanLib) in linux (ubuntu) from source (not without a million errors, anyhow). The version in the ubuntu repos (0.8 I believe) is too old to support my game in full; thus I have to compile the source. However, if this is necessary for the end user to have to do prior to installing the game (by the way it's called BioTux, you can [see more here]("http://biotuxdev.org")) then that will defeat the entire purpose, cause who wants to go through all that trouble to play a simple game?
 

I expect a lot of SDL users to try to convince me over, but make it good, 'cause swapping libraries means entirely starting over, throwing previous results to the wind... :(


Thanks,


NinjaNumberNine

---

### Post by rombust on 2010-01-12
Anything before ClanLib 2.0 I would avoid.
 
ClanLib 2.1.1 is very stable, and as far as I know bug free :)
 
But whether you want to use ClanLib or SDL, that's up to you.
 
Examine ClanLib 2.1.1 API and SDL API, so see what you are most comfortable with.
 
You will find ClanLib has a more extensive API, but it may take longer to learn (because there is so much in it)
 
ClanLib does contain an SDL display target as an external library (using SDL software rendering), but ClanLib "GDI" software renderer is a lot faster.
 
ClanLib requires the SSE2 intruction set, unless someone sends a patch to support older processors.
 
Have a look at [http://www.clanlib.org/examples.html](http://www.clanlib.org/examples.html) and the showcase [http://www.rtsoft.com/forums/forumdisplay.php?f=17](http://www.rtsoft.com/forums/forumdisplay.php?f=17)
 
Spend a couple of weeks with both, and see what you feel is best for you.

---

### Post by caelestis2 on 2010-01-12
[SFML?]("http://www.sfml-dev.org/")

---

### Post by NinjaNumberNine on 2010-01-12
Oh, the power... I'm going into a programmer's heaven... Those screenshots. Can they be done from NovaShell? It's so confusing, there's like four different bridges, Lua, C++, ClanLib and NovaShell, somehow linked together. And yeah, rombust, I'm the guy from the NovaShell forums with all the nooby problems... ;)

@caelestis: the link didn't seem to load, or was being super slow.

---

### Post by caelestis2 on 2010-01-12
Link seems fine to me. Live far?

I don't know about clanlib, but compared to sdl, sfml is much faster and easier to work with, being C++ based.

---

### Post by NinjaNumberNine on 2010-01-14
I'm pretty sure I live pretty close. I try to stay within 10 feet of myself, but sometimes I get carried away... :mrgreen:

Sfml... The link works fine now. It sounds really impressive, but there isn't a app like NovaShell for using it. I'm not nearly the programmer it would take to use that... 

However, I'd like to learn more. The specs sounded really good- I'll be looking into when I get time.


Thanks!


NinjaNumberNine

---

