---
title: "Premake + Make Always Rebuilds The Whole Thing"
date: 2008-09-17
forum: Packaging and Compiling Programs
---

### Post by nikki93 on 2008-09-17
Hey!

I'm using premake with the gnu make target, on Linux, with the following premake.lua file:-
```
-- Project ----------------------------------------------------------------------------------

project.name = "TheProject"
project.bindir = "bin"

-- Package ----------------------------------------------------------------------------------

package = newpackage()

package.name = "TheProject"
package.kind = "exe"
package.language = "c++"
package.configs = { "Debug", "Release" }

-- Include and library search paths, system dependent :( ------------------------------------

package.includepaths = {
"/usr/local/include/OgreBullet",
"/usr/local/include/OgreBullet/Collisions",
"/usr/local/include/OgreBullet/Dynamics",
"/usr/local/include/boost-1_36",
"/home/nikki/Development/Libraries/ngf/include",
"/home/nikki/Development/Libraries/squirrel/include",
"/home/nikki/Development/Libraries/squirrel/sqplus",

"include",
}

package.libpaths = {
"/home/nikki/Development/Libraries/squirrel/lib"
}

-- Libraries to link to ---------------------------------------------------------------------

package.links = {
"OgreBulletCol",
"OgreBulletDyn",
"GIMPACT",
"bulletcollision",
"OgreAL",
"openal",
"sqplus",
"sqstdlib",
"squirrel"
}

-- pkg-configable stuff ---------------------------------------------------------------------

package.buildoptions = {
"`pkg-config OGRE --cflags`" ..
"`pkg-config OIS --cflags`" ..
"`pkg-config MyGUI --cflags`" ..
"`pkg-config bullet --cflags`" ..
"`pkg-config openal --cflags`" ..
"`pkg-config OgreAL --cflags`"
}

package.linkoptions = {
"`pkg-config OGRE --libs`" ..
"`pkg-config OIS --libs`" ..
"`pkg-config MyGUI --libs`" ..
"`pkg-config bullet --libs`" ..
"`pkg-config openal --libs`" ..
"`pkg-config OgreAL --libs`"
}

-- Files ------------------------------------------------------------------------------------

package.files = {
matchrecursive("*.h", "*.cpp"),
}

package.pchheader = "include/globals.h" -- Precompile this.

-- Debug configuration ----------------------------------------------------------------------

debug = package.config["Debug"]
debug.defines = { "DEBUG", "_DEBUG" }
debug.objdir = "obj/debug"
debug.target = "debug/" .. package.name .. "_d"

debug.buildoptions = { "-g" }

-- Release configuration --------------------------------------------------------------------

release = package.config["Release"]
release.objdir = "obj/release"
release.target = "release/" .. package.name
```

I do a 'premake --target gnu', and then a 'make'. Then after editing just one cpp file, if I 'make', the whole thing is rebuilt (all files), instead of just one. In fact, if I do a 'make && make', without changing in between, the whole thing is rebuilt twice.

Any ideas what I'm doing wrong?

Thanks! :)

---

### Post by InfinityCircuit on 2008-09-17
Where is the bug?  Packages are supposed to be correctly built twice after make && make to test that the makefile doesn't irreversibly edit the source code.

Please clarify what you expect to happen.  If you are running "make", you are telling it to make everything, since you didn't specify a specific target.

You can consider ccache if you want to speed up multiple successive makes.

---

### Post by nikki93 on 2008-09-18
I expected that only the .cpp files that have been changed will be compiled into .o files, and all of them will be linked together. Lets say I have three files, a.cpp, b.cpp, and c.cpp. I build and link them. I change a.cpp. Isn't make supposed to only rebuild a.cpp and link it with the rest?

If I do 'make NewProject' twice, it builds _all_ the files into .o, twice. I expected it to do it only for the changed once (ie. none).

---

