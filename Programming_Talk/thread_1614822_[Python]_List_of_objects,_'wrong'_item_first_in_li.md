---
title: "[Python] List of objects, 'wrong' item first in list"
date: 2010-11-06
forum: Programming Talk
---

### Post by SpinningAround on 2010-11-06
The following code add a 'Profile' to 'profiles' where 'name' and 'path' is "tmp". Question is why?
[PHP]
#!/usr/bin/python
# -*- coding: utf-8 -*-
import os
class Profile:
	name = "tmp"
	path = "tmp"

f_profiles = open(os.path.expanduser("~/.mozilla/firefox/profiles.ini"))
profiles = []
for line in f_profiles:
	s_line = line.strip()
	if s_line.count("Profile")>0:
		profiles.append(Profile())
	if s_line.count("Name")>0:
		profiles[len(profiles)-1].name = s_line[line.find("=")+1:len(s_line)]
	if s_line.count("Path"):
		profiles[len(profiles)-1].path = s_line[line.find("=")+1:len(s_line)]
for i in range(len(profiles)):
	print profiles[i].name
	print profiles[i].path
	print i
[/PHP]

Output:
```

tmp
tmp
0
default
abcdefgh.default
1

```

---

### Post by ssam on 2010-11-06
judging by my profiles.ini it is because of the line
```

StartWithLastProfile=1

```
near the top. that will cause the creation of a profile object, but it's name and path wont be set.

there are a lot of over complicated lines in your program.

instead of
```

if s_line.count("Profile")>0:

```
just use
```

if "Profile" in line:

```

instead of
```

profiles[len(profiles)-1].name = s_line[line.find("=")+1:len(s_line)]

```
just use
```

profiles[-1].name = s_line[line.find("=")+1:]

```
or
```

profiles[-1].name = s_line.partition("=")[2]

```

also as you are reading a ini style file you could use the ConfigParser module from the standard library.

---

### Post by Tony Flury on 2010-11-06
My profiles.ini file contains other data at the beginning which does not contain Name or Path, but does contain the word Profile : 

```

[General]
StartWithLastProfile=1

[Profile0]
Name=Default User
IsRelative=1
Path=5o48dsw4.Default User
Default=1

```

From what i can see your code when run on my ".ini" file will add a new entry when it sees "StartWithLastProfile", but since it does not find a Name or Path field will never set them - therefore leaving a tmp/tmp object in your list.

maybe changing your code to :

```

if s_line.count("[Profile")>0:

```
Will make it work - it did on mine.

---

### Post by SpinningAround on 2010-11-06
Thanks :)
ssam, thanks for the advices will go through the code.

---

