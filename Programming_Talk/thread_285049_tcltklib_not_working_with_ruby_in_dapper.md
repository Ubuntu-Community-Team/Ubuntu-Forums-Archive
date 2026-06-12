---
title: "tcltklib not working with ruby in dapper"
date: 2006-10-26
forum: Programming Talk
---

### Post by ajaustin on 2006-10-26
I have ruby 1.8 installed and working and want to have a look at the Tk interface.

I get the following:-

irb(main):001:0> require 'tk'
RuntimeError: tcltklib: fail to Tk_Init(). this isn't a Tk
applicationunknown color name "Black"
        from /usr/lib/ruby/1.8/tk.rb:1102:in `initialize'
        from /usr/lib/ruby/1.8/tk.rb:1102
        from (irb):1
irb(main):002:0>

Any ideas please?

Tony

---

### Post by Jim_Fuqua on 2006-10-28
I have had the same problem. Debian and Ruby GUIs don't seem to get along very well.  Apparently Debian has broken the Ruby package into many packages.  They have made a formal statement against the Ruby Gem scheme of files and directories.

In Windows it just takes one click and I got it all working, but in Ubuntu it has been a struggle.  After not being able to get it to work using the package manager, I tried compiling it from source code with information about the tcl/tk header files and it still did not work because it was looking for a different version of Tk.  From searching the net, it appears that this specific problem is limited to Debian based distributions.

If you find the answer, let me know.  I have seen some other postings here that may have clues as to the solution.  

Jim_Fuqua

---

