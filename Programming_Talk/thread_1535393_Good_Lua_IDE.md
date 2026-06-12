---
title: "Good Lua IDE?"
date: 2010-07-20
forum: Programming Talk
---

### Post by HOLOGRAPHICpizza on 2010-07-20
I absolutely love Lua, its just such a sexy language, but I have been spoiled coding Java for so long in a nice IDE like Eclipse or NetBeans, and I would love something like it for Lua. I'm even willing to pay for a commercial solution.

Does anyone know of a Lua IDE that supports:
[LIST]
[*]Code Completion
[*]Refactoring
[*]Debugging
[*]Linux
[*]Basicaly everything NetBeans or Eclipse can do for Java
[/LIST]

Any suggestions?

---

### Post by Simian Man on 2010-07-20
[LuaEclipse ]("http://luaeclipse.luaforge.net/")looks promising.  I haven't used it, but from my experience, if a less common programming language has a good IDE, it tends to be in the form of an Eclipse plugin.

I'd be surprised if there is anything as complete as Eclipse and NetBeans Java support however.

---

### Post by phrostbyte on 2010-07-20
Code Completion and Refactoring is insanely hard things to do, so only really mainstream languages tend to have IDEs with robust support for it.

---

### Post by kartben on 2011-11-17
Lua Development Tools is an Eclipse plug-in which provides syntax-coloring, error markers, outline, code folding... and a real **debugger**!
It aims at being a successor for LuaEclipse. It is leveraging Metalua to perform source code analysis, and uses heuristics to try to suggest the best autocompletion possible, even though the language is dynamic...

It is an Eclipse Technology project. It is Open Source (EPL license).

[LIST]
[*]Project web page - [http://www.eclipse.org/koneki/ldt](http://www.eclipse.org/koneki/ldt)
[*]Installation via Eclipse Marketplace - [http://marketplace.eclipse.org/content/lua-development-tools-koneki](http://marketplace.eclipse.org/content/lua-development-tools-koneki)
[*]Screencast showcasing the features of LDT - [http://vimeo.com/31590599](http://vimeo.com/31590599)
[/LIST]

---

### Post by HOLOGRAPHICpizza on 2011-11-17
Epic necro-post! I wish I would have had this a year and a half ago when I needed it! >_< Ah.. Makes me want to write some lua, but since this summer I've been doing nothing but C++ for my new job.

Looks like an awesome IDE that I will have to take a look at next time I use lua though!

---

### Post by kartben on 2011-11-17
Hey, at least I learnt the "epic necro-post" expression which literally makes me laugh out loud :)
Sorry 'bout the shameless plug, but I really thought it was worth it! ;)

---

