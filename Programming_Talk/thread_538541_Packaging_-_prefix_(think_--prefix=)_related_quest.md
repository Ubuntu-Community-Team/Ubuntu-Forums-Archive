---
title: "Packaging - prefix (think --prefix=) related question"
date: 2007-08-30
forum: Programming Talk
---

### Post by damava on 2007-08-30
I'm currently creating a package for a game called "sfz" with the following directory layout in mind:

- /usr/bin for the executable
- /usr/share/sfz for the data files

Is it a good idea to define a prefix-macro in the source code and use that whereever the game tries to access some of its data?

Something like
```
#define DATA_PREFIX "/usr/share/sfz/"
open_file(DATA_PREFIX, "subdir/button.png");
```

Or is there a better way for doing these things?

Another problem that just occured to me - the game needs to create/write files in its data directory. This is a problem, since the permissions in /usr/share are 755 root:root and therefore the user is not able to create files.

How do other packages handle those issues? I'd really appreciate some hints on this!

---

### Post by nanotube on 2007-08-30
> **damava said:**
> I'm currently creating a package for a game called "sfz" with the following directory layout in mind:

- /usr/bin for the executable
- /usr/share/sfz for the data files

Is it a good idea to define a prefix-macro in the source code and use that whereever the game tries to access some of its data?

Something like
```
#define DATA_PREFIX "/usr/share/sfz/"
open_file(DATA_PREFIX, "subdir/button.png");
```

Or is there a better way for doing these things?

Another problem that just occured to me - the game needs to create/write files in its data directory. This is a problem, since the permissions in /usr/share are 755 root:root and therefore the user is not able to create files.

How do other packages handle those issues? I'd really appreciate some hints on this!

the data_prefix way seems as good as any to me.
though you might want to define it as "../share/sfz", just so that a person can still play the game even without running the install - just unzip to wherever, and run the executable.

about writing to data files - that's why we have the dot directories in the user's home dir. so your game would also create user-specific files that it can write to in say, ~/.sfz, and that's where it would write stuff.

---

