---
title: "Running ruby scripts"
date: 2008-12-18
forum: Packaging and Compiling Programs
---

### Post by DrPepper836 on 2008-12-18
How exactly do you run a .rb ruby script file outside of a program like geany or netbeans? Is there a way to do it with a launcher or an executable text file?

---

### Post by geraldm on 2008-12-18
Use an executable text file.  Execute it from an xterm terminal.

The script must have as its first line the shebang + path_to_ruby


Gerald

---

### Post by GregTheGerg on 2009-02-19
What would the proper shebang be? Thanks! ^_^

---

### Post by Tek-E on 2009-02-19
I know very little about ruby programming and any programming in ruby that I do is not under ubuntu.  But im going to take a guess at ./ ??
I might be wrong though, so I would check with someone else if this fails.

---

### Post by geraldm on 2009-02-20
The program permission must be executable.  The first line 
(could be #!/usr/local/bin/ruby OR #!/usr/bin/env ruby)  Filename ends in ".rb"

#!/usr/bin/ruby
puts "hello"

---

