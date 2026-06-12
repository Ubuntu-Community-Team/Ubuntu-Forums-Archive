---
title: "Delay with Ruby until keyprompt ?"
date: 2008-10-12
forum: Programming Talk
---

### Post by Dave_Connor on 2008-10-12
I want to get into more interactive programming and want with before ruby to print out something I could set up a key prompt like enter or y or n before ruby prints something. How can this be done ?

---

### Post by meanburrito920 on 2008-10-13
If you are looking for the program to simply wait for user input, use gets. otherwise, look into a multithreading implementation. do a google search for threads in ruby.

---

### Post by loell on 2008-10-13
it's [rawline]("http://rubyforge.org/projects/rawline/")

---

### Post by loell on 2008-10-13
found another snippet. ;)

```

#!/usr/bin/env ruby -w

require "highline/system_extensions"
include HighLine::SystemExtensions

print "Enter one character:  "
char = get_character
puts char.chr

```

---

