---
title: "Cross-compile Pluto (a Lua library)"
date: 2009-09-11
forum: Programming Talk
---

### Post by kumoshk on 2009-09-11
I'm wanting to create a cross-platform program written in Lua, using Pluto for persistence.

I can compile Pluto fine for Linux (using Ubuntu, Jaunty, 32-bit), but I seem to be having difficulty getting the make file to work properly with the cross-compiler for Windows. I only tried replacing cc with i586-mingw32msvc-cc, but I guess more was needed.

Is there a way I can fix this make file so that it'll compile pluto.dll instead of pluto.so? Compiling for Linux only takes a couple seconds.

Is anyone out there with Windows willing to compile this and send me the resulting pluto.dll file? Of course, the make file doesn't mention dll in the make clean section, so maybe it's not meant for Windows at all. 32 and 64 bit versions would be nice, but either is better than neither.

Will the pluto.so file compiled on Ubuntu work on Macintosh? I heard a rumor that Macs can use .so files (in addition to dylib). However, I don't know if that only means .so files compiled on Macintosh.

Here's where you can get the Pluto source code:
[http://luaforge.net/frs/download.php/3309/pluto-2.4.tar.gz](http://luaforge.net/frs/download.php/3309/pluto-2.4.tar.gz)

---

### Post by kknd on 2009-09-11
There you are (attached)

---

### Post by kumoshk on 2009-09-12
> **kknd said:**
> There you are (attached)

Thank you very much for the file!

However, I can't get it to work through wine for some reason. Is it 32-bit or 64-bit? If it's 64-bit that *might* explain it. It gives me an error saying pluto.dll doesn't contain a module called pluto.

Here's the error I get:
```
error loading module 'pluto' from file '.\pluto.dll':
	Module not found
```

Does it work for you with the following code, if pluto.dll is in the same directory as the lua file containing the following code?

```
--Demonstrates how to save and load persistent data to and from a file
require 'pluto'

myTable={}

testFunc=function()
    --Read from file and unpickle.
    io.input(io.open("my.txt","r"))
        myString=io.read("*all")
    io.close()
    myTable=pluto.unpersist({}, myString)
end
if not pcall(testFunc) then
    --[[exception handling
        This is like the except statement in Python (only it always covers all errors, except SyntaxError).
    --]]
    print "A proper my.txt does not exist yet! This is a first run."
else
    print "File exists. Continuing."
end

print(myTable[1])

myTable[#myTable+1]=#myTable+1

for k,v in ipairs(myTable) do
    print("Key: " .. k, "Value: " .. v)
end

--Pickle and write to file
saveString=pluto.persist({}, myTable)
io.output(io.open("my.txt","w"))
io.write(saveString)
io.close()
```

This code works with my pluto.so file in the same directory.

---

### Post by kumoshk on 2009-09-12
Hmm, actually, nevermind. It seems to work afterall. I think I just had a faulty installation of Lua for Windows.

However, on the first run of my sample code, it hangs from the normal command-line (it doesn't matter whether I use wine or normal Linux). It doesn't hang from the Linux SciTE command-line (but it does from the Windows SciTE that comes with Lua). Any idea how to stop it from hanging?

---

### Post by kumoshk on 2009-09-12
I found the problem. Just switch that function (and the exception handling stuff with an if statement):
```

--Read from file and unpickle.
if io.open("my.txt","r") then
    print "File exists. Continuing."
    io.input(io.open("my.txt","r"))
        myString=io.read("*all")
    io.close()
    myTable=pluto.unpersist({}, myString)
else
    print "A proper my.txt does not exist yet! This is a first run."
end

```

Apparently, io.read("*all") causes the program to hang instead of producing an error if "my.txt" doesn't exist (unless you're using the Linux SciTE command-line). io.open returns a boolean (true if there's a file, and nil if not) so it works out well here instead of trying to do exception handling in Lua. Seems like Lua rarely produces errors when I would think it would.

Anyway, thanks for all the help again!

---

### Post by kumoshk on 2009-09-12
I'm still curious if my Linux pluto.so file will work on a Macintosh, though, or if I need a Mac-compiled .so file (I've heard Macs will do .so files in addition to dylib or whatever they use). If not, can the source be compiled for Macintosh? If anyone can contribute that, if it's needed, that would be great.

---

