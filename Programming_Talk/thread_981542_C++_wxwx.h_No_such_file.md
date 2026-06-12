---
title: "C++ wx/wx.h No such file"
date: 2008-11-13
forum: Programming Talk
---

### Post by deejross on 2008-11-13
I am JUST learning C++ because I need to write a cross-platform application. I decided to go with the wxWidgets library and am trying to get a very simple program to compile. I come from C#, so #include and all that other C++ stuff scares me. I am very new so I will need some hand-holding :)

This is the application I have so far:
```

#include "wx/wx.h"

int main(int argc, char **argv)
{
    wxPuts(wxT("A console application"));
}

```

I have build-essential, libwxbase2.8-0, libwxbase2.8-dev, wx-common, wx2.8-headers, libwxgtk2.8-0, libwxgtk2.8-dev installed but I'm getting the following error:
```

g++ console.cpp -o console

console.cpp:1:19: error: wx/wx.h: No such file or directory
console.cpp: In function ‘int main(int, char**)’:
console.cpp:5: error: ‘wxT’ was not declared in this scope
console.cpp:5: error: ‘wxPuts’ was not declared in this scope

```

I don't really know how to use g++, I was using Code:Blocks (because I thought it would help me to learn since I'm used to IDE's) and it was having the same issue, so I've been trying a few commands I found after Googling the problem.

I tried this command I found from an earlier post [Here]("http://ubuntuforums.org/showthread.php?t=145417&page=2"):
```

g++ console.cpp 'wx-config --libs' 'wx-config --cxxflags' -o console

```

And no luck. I also tried copying everything from /usr/include/wx-2.8/wx into it's own wx folder in the same folder as the cpp file. I also tried using #include <wx2.8/wx/wx.h> instead, but then all of it's #includes give me "No such file or directory" errors.

Remember, I have no idea what I'm doing when it comes to C++...so if you have any tips for someone trying to learn C++ I would appreciate that as well. Thanks for any help you can give me.

---

### Post by jpkotta on 2008-11-13
You need the -dev package to build programs.  I don't know if this is all you need, by you definately need it.
```
sudo aptitude install wx2.8-headers libwxbase2.8-dev
```

Then, make sure you can run wx-config.  I can't figure out what package it's in.
```
wx-config --help
```

Finally, you need backticks (`) not single quotes (').  An alternative syntax is '$()'.  It takes the quoted expression, tries to run it as a command, and replaces the quoted expression with the output of the command.
```
g++ console.cpp `wx-config --libs` `wx-config --cxxflags` -o console
```

---

### Post by deejross on 2008-11-13
I already had the needed packages installed and I was able to run wx-config. It was the backticks. That's so strange and certainly not mentioned in any tutorial.

This leads me to other questions (hope you don't mind answering):
[LIST]
[*]Is g++ the right thing to be using?
[*]If so, is there a way to make this work without the extra commands?
[/LIST]

---

### Post by snova on 2008-11-13
G++ is the C++ compiler, so yes. You've avoided a lot of confusion by not using gcc.

The backticks are shell syntax. Basically it means, "Run this command and substitute the output here". So wx-config prints out installation information in a format that GCC accepts as compilation flags.

Set up a build system (I like SCons personally) to do it all automatically.

---

### Post by deejross on 2008-11-13
Is there a good way to do this using Code:Blocks? I suppose I could do all this using the CLI, but I'd like to get the IDE working as well.

---

### Post by snova on 2008-11-13
With Code::Blocks, the only way I know of is to get the output of wx-config and insert the values into the appropriate fields manually.

I haven't used it in a while, however this should work.

---

