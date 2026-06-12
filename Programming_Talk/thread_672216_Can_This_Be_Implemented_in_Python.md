---
title: "Can This Be Implemented in Python?"
date: 2008-01-19
forum: Programming Talk
---

### Post by Xanderfoxx on 2008-01-19
InfiniPy: a World of Chaos

Somewhat of a blend of Java's "RoboCode" and "M.U.G.E.N: Everything vs. Everything," I was thinking to myself that I would love to see *this* as a 2d fighting game in Python.

I admit it would be more or less a clone of Mugen, but it will be somewhat different, as the implementation would be different, it would have different features, and would be fresh.

The point of this post is whether or not it *can* be implemented.

The character files would be *.tar.bz2 files in a special folder, containing a *.py script (defining an object inherited from a so-called "InfiniteBaseCharacter" class or other built-in sub-classes) with the same name, and additional scripts needed by the main script, a directory called "/img", a directory called "/aud"

To protect the running of the game, and to try to prevent the game from crashing from corrupted character files, all scripts would be run from within a battery of exceptions when imported, including divide by zero and similar basic stuff, and when evoked, would graphically remove the character, and replace it with a substitute, as set in the "settings.conf" file.

I was thinking that it would have these features:
[LIST=1]
[*]Simple yet full-featured API for user-contributed characters
[*]Plenty of built-in environment variables and functions for special moves, like "ambientLight",  "freeze()", and "quake()"
[*]An organization to back it all up with paid services such as: 3d modeling and character generation; a huge FLAC audio sample library;
[*]Built-in support for Tekken-style, Mortal Kombat-style, and those Dragon Ball fighter games-style environment APIs so you can do the Fatality, have it say "Finish Him!" if the opponent is almost dead, and you can alter the environment when you power up.
[*]A cast of pre-built characters with a related storyline mode
[*]A feature where you put your freshly-designed character through a predefined storyline[/LIST]I think this would be fun!    :lolflag:

Is it possible to and/or reasonable to go through the effort of creating this game?

---

### Post by LaRoza on 2008-01-19
It can be done with the various libraries available.

It really depends on your abilities. If you are really want this, you will have to start it and make it worth developing.

---

### Post by luisromangz on 2008-01-19
Yeah it is possible, it could be implemented,  you can do it for learning or just for fun, or whatever reason you want...

---

### Post by pmasiar on 2008-01-19
I im sure it **can** be implemented - one of the reasons is that I recall such a project mentioned at planetPython.

But it is a lot of work, you will be much better of to join existing project than starting your own. At least untill your skills will be up to formidable task.

---

### Post by Xanderfoxx on 2008-01-22
You imply that I have the capability to become able. For that I thank you.

I also thank you for the prompt reply.

If you would be so kind, could you tell me what the project was called? A URL would be nice. If not I can look. I'm not that lazy. :)


Thanks.

---

### Post by pmasiar on 2008-01-23
One of the projects working in this area is WorldForge - and they are pretty advanced :-) There are  many many others. sourceforge knows.

BTW Re your sig: First line is temporary status, no worry. Second line is no good: drink() and smoke() hurts your health, and last 3 activities hurt your karma. :-) Middle part is OK.

Try joining some martial arts studio, in YMCA/JCC they are not that expensive, and it is **a lot** of fun. Also, if some bully tries "jokingly" to hit you and you make perfect block, totally reflex, bully realizes that there are other easier targets, and let you alone. :-) Tried in real life.

---

### Post by Xanderfoxx on 2008-01-25
Oh, I was not referring to myself in the sig, but you managed to make me laugh regardless.

I'm have that there until I think up a better one.

OH! And while we are on the subject of sigs,
    How do you register yourself as a Linux or Ubuntu user, in order to get those cool-looking serial numbers, like those others sport on theirs?

---

### Post by pmasiar on 2008-01-25
[http://counter.li.org/](http://counter.li.org/) (google: linux counter)
[http://ubuntucounter.geekosophical.net/](http://ubuntucounter.geekosophical.net/) (google: ubuntu counter) :-)

Funny, ubuntucounter shows 14 registered gNewSense users only.

---

### Post by Xanderfoxx on 2008-03-11
Thank you.

---

