---
title: "LUA Editor"
date: 2007-05-25
forum: Programming Talk
---

### Post by ART_Adventures on 2007-05-25
Hello People,

What apps would you recommend for editing Lua scripts on Ubuntu?

Thanks.

---

### Post by treak007 on 2007-05-25
vi supports syntax highlighting for Lau, so I would recommend that. Gvim if you prefer a gui.

---

### Post by WW on 2007-05-25
**gedit** has a highlight mode for Lua.  This is not necessarily a recommendation, just an observation.

---

### Post by jyba on 2007-05-25
In the universe repository there's a lua-mode for emacs. It does syntax highlighting, automatic indentation and lets you try stuff out by sending lines/regions/files to a lua interpreter.

---

### Post by Vadi on 2008-07-28
Automatic indentation as in it's indented while you're typing, or you can just run it on a non-indented block of code and it'll indent?

I'm looking for the latter for lua.

---

### Post by Kadrus on 2008-07-28
I use Gedit for it and don't have any complains to be honest.wxLua provides it's own IDE if I am not mistaken written in wxLua.
I suggest having a look at this page.
[Lua Addons]("http://lua-users.org/wiki/LuaAddons")

---

### Post by kknd on 2008-07-28
I use Geany! It supports pre-generated tags for code completion, and I used it for witting C code that interacts with Lua.

---

### Post by kumoshk on 2009-09-05
I use SciTE. It has a built-in command-line (so you can run a script by pressing F5). It has syntax highlighting, auto-indent, etc. Configuring it takes a little learning, but it's doable.

For console-based scripts, I recommend editing the Lua properties file so that it opens a native command-line for running the programs, though, since things like user-input and such aren't always usable from SciTE's command-line.

Change the line that says this:
command.go.*.lua=lua5.1 "$(FileNameExt)"

to this:
command.go.*.lua=gnome-terminal -e 'bash -c "lua5.1 "$(FileNameExt)"; sleep 999999999d"'
(just press ctrl c to exit that command-line or change the sleep parameter so it closes in a few seconds if you like, rather than almost a billion days)

Then when you press F5 it'll open the gnome-terminal instead.

---

### Post by kumoshk on 2009-09-05
Also, in SciTE, since you probably don't need to worry about 'building' in Lua, you can define F7 to open a Lua interpreter.

To do that, open the lua properties file and add this line in there by the compile line I mentioned in my last post:
command.build.*.lua=gnome-terminal -e 'bash -c "cd "$(FileDir)"; lua5.1"'

You probably don't need the cd "$(FileDir)" portion since I think it's there by default. So, you could probably just do this instead:
command.build.*.lua=gnome-terminal -e 'bash -c "lua5.1"'
and still be able to import stuff in the folder of your file and all.

---

