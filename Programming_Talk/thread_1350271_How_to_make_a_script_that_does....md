---
title: "How to make a script that does..."
date: 2009-12-09
forum: Programming Talk
---

### Post by dwally89 on 2009-12-09
Hi,

Sorry about the vague title, couldn't think of a more specific one...

How can I write a script that searches through a given folder, and all its subfolders, and reports all files and folders that contain the characters: ```
* . " / \ [ ] : ; | = , 
```

Thanks

---

### Post by Rany Albeg on 2009-12-09
Hi ,

Just run a loop like 'for i in $(find <dir>)'
and check equality for each i .

---

### Post by dwally89 on 2009-12-09
Sorry, I'm a bit new to all this, please could you be a bit more specific?

---

### Post by Barriehie on 2009-12-09
I'm new to awk so I'll have to work on it a bit but:

```

#!/bin/bash
ls -lR *somedir* > ./*somefilename*
gawk *somegawkfile.awk* -f *somefilename* > ./*outputfilelist*

```

That should work but I'll have to get back with the *somegawkfile.awk* part!

Barrie

Edit: After some searching your list can be narrowed a bit! [Click here!](http://ubuntuforums.org/showthread.php?t=688615)

---

### Post by jimi_hendrix on 2009-12-09
i am no find pro, but i bet this could be a find oneliner

---

### Post by Arndt on 2009-12-09
> **Barriehie said:**
> I'm new to awk so I'll have to work on it a bit but:

```

#!/bin/bash
ls -lR *somedir* > ./*somefilename*
gawk *somegawkfile.awk* -f *somefilename* > ./*outputfilelist*

```

That should work but I'll have to get back with the *somegawkfile.awk* part!

Barrie

Edit: After some searching your list can be narrowed a bit! [Click here!](http://ubuntuforums.org/showthread.php?t=688615)

There is some good stuff in that thread, but for the purpose of narrowing down a search, rather than suggesting what file names to create yourself, the only thing you can exclude is the forward slash '/'.

And it could be just as well that you don't exclude it either. Unix will never create such a file, but a foreign file system daemon might (that is a bug, of course). I remember this happening once, but I don't remember the details.

---

### Post by mo.reina on 2009-12-09
```
ls | grep -F '*'
ls | grep -F '"'
ls | grep -F '['
.......
.......
.......

```

---

### Post by ibuclaw on 2009-12-09
> **mo.reina said:**
> ```
ls | grep -F '*'
ls | grep -F '"'
ls | grep -F '['
.......
.......
.......

```

```
grep -lR '[]*.":;=,|/\[]'
```

---

### Post by stylishpants on 2009-12-09
This one liner does it:
```
ruby -rfind -e 'chars=%q[*."/\\[]:;|=,].split(//); Find.find(".") { |f| puts f if chars.any?{|char| File.basename(f).include?(char)} }'
``` 

Here's the same code formatted and commented for readability:
```
#!/usr/bin/ruby -w
require 'find'

# Make an array of chars to search for
chars=%q[*."/\\[]:;|=,].split(//); 

# Find all files/dirs under the current dir
Find.find(".") { |f| 

	# Print if the basename contains any target chars
	puts f if chars.any?{|char| File.basename(f).include?(char)} 
}

```

---

### Post by mo.reina on 2009-12-09
> **tinivole said:**
> ```
grep -lR '[]*.":;=,|/\[]'
```

gets my vote :D

---

