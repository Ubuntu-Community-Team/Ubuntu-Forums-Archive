---
title: "Media Player"
date: 2007-02-28
forum: Programming Talk
---

### Post by moberry on 2007-02-28
HI All. I posted something on this while back, but removed it because I felt it was too forward. The orginal post can be found here [http://ubuntuforums.org/showthread.php?t=184892](http://ubuntuforums.org/showthread.php?t=184892). I have been working on (in my sparse free time) a new media player written in C from the ground up, it is starting to seriously shape up.   I am posting this to get some suggestions; I have implemented a pretty abstract no-limits plugin system and I am torn between how I want core parts of the program to be implemented. Much of the said code has already been written; I would just like some suggestions as to how it would be best implemented. Here are my ideas.

Currently the basic interface is part of the main executable. Playlists, database backends, etc. are all being loaded as plugins. I like this approach as it makes for a very very powerful and extendable interface (about the only thing hard coded into the exutable are playback controls, and  a determined zone for plugins to "request" gui space and display their information). I wonder though if this is over complicating things. The database is a hidden interface the user never messes with. One part of me says, put it all in the main program and let end users develop and customize plugins; the other part says, write damn near everything as a plugin.

I would like some nice suggestions as to what some of you think is the best way to handle it. I am not quite ready to release the source of the software when I finally decide how I want everything to be put together I will get some documentation for the plugin API and try to start finding people to get involved and bump heads with ideas.

Anyway, what do you guys think? thanks for listening and for your comments.

---

### Post by zanglang on 2007-03-01
I'd say, just build it with minimal functionality first (least pluginization, more hardcoded features), and then incrementally work towards properly decentralizing the functions into a real plugin architecture, learning as you go, until you've really got a "feel" of what would work best in terms of configurability versus usability versus efficiency. Leave the ambitious system design alone for now until you can absolutely come up with the fully mapped out architecture with clear ideas on how to make everything work, otherwise it'll more likely end up a terrible product with horribly cobbled together hacks (like Windows ;)).

One more quote:
"Plan to throw one away, you will anyhow." - Fred Brooks

---

