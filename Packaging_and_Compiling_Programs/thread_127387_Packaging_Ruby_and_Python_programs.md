---
title: "Packaging Ruby and Python programs"
date: 2006-02-08
forum: Packaging and Compiling Programs
---

### Post by mr_ed on 2006-02-08
Say I created RubyProgram or PythonProgram 0.1, and I'd like to make a .deb package out of it.  How exactly would I go about doing that?

With C/C++ I can use autotools and checkinstall.  Is there an equivalent for interpreted languages?

I could manually create a /usr/bin/RubyProgram (which would be a script that executes #!/usr/bin/env ruby RubyProgramMain) or something like that and stuff those two files into a .deb repo...
Any other ideas?

---

### Post by Jimmey on 2006-02-10
There's some useful options in Boa-Constructor for Python - That's available in the repositories...

I'm not too sure about Ruby.

---

