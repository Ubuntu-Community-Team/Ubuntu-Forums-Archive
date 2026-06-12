---
title: "bzr merge issue"
date: 2010-09-01
forum: Programming Talk
---

### Post by homeslice on 2010-09-01
Howdy, I've been using bzr recently handle version control for some small to medium sized projects, but I recently ran into a merge issue I can't figure out. I've been adding and removing a few files here and there, and on the most recent merge I ran into a few conflicts - nothing out of the ordinary :

```
Brendans-Mac-Pro-2:ACG brendan$ bzr conflicts
Conflict adding files to bin/testing.  Created directory.
Contents conflict in bin/testing/infile.OTHER
Contents conflict in bin/testing/intree.OTHER
Contents conflict in bin/testing/outfile.OTHER
Contents conflict in bin/testing/outtree.OTHER
```

Curiously, the contents of bin/testing/ does not include infile, intree, or outtree, just infile.OTHER and infile.OTHER.BASE, and similarly for the other files.
But worse, the conflicts can't be resolved :

```
Brendans-Mac-Pro-2:ACG brendan$ bzr resolve infile.OTHER
testing/infile.OTHER is not conflicted 
```

OK, that's depressing. But there's nothing important in the files, so I tried to remove them, and ended up engaging in a losing battle of wills with bzr, as follows

```
 Brendans-Mac-Pro-2:ACG brendan$  bzr remove bin/testing/
bzr: ERROR: Can't safely remove modified or unknown files:
unknown:
  testing/
  testing/outtree.OTHER.OTHER
  testing/infile.OTHER.OTHER
  testing/infile.OTHER
  testing/outfile.OTHER.OTHER
  testing/intree.OTHER.OTHER
  testing/infile.OTHER.BASE
  testing/outfile.OTHER.BASE
  testing/outtree.OTHER.BASE
  testing/intree.OTHER.BASE
Use --keep to not delete them, or --force to delete them regardless.
Brendans-Mac-Pro-2:ACG brendan$ bzr remove --force bin/testing/
testing is not versioned.
Brendans-Mac-Pro-2:ACG brendan$ bzr remove --force bin 
Brendans-Mac-Pro-2:ACG brendan$ bzr resolve
0 conflict(s) auto-resolved.
Remaining conflicts:
Conflict adding files to bin/testing.  Created directory.
Contents conflict in bin/testing/infile.OTHER
Contents conflict in bin/testing/intree.OTHER
Contents conflict in bin/testing/outfile.OTHER
Contents conflict in bin/testing/outtree.OTHER
 
Brendans-Mac-Pro-2:ACG brendan$ bzr remove --force bin/testing/intree*
testing/intree* does not exist.
Brendans-Mac-Pro-2:ACG brendan$ bzr resolve
0 conflict(s) auto-resolved.
Remaining conflicts:
Conflict adding files to bin/testing.  Created directory.
Contents conflict in bin/testing/infile.OTHER
Contents conflict in bin/testing/intree.OTHER
Contents conflict in bin/testing/outfile.OTHER
Contents conflict in bin/testing/outtree.OTHER


```

 Long story short, all I want to be able to do is delete those files, have bzr forget about them, and commit some new changes. But bzr won't allow commits until the conflicts are resolved, and I have no idea how to resolve the conflicts.
 Total noob here, any advice would be great. Thanks in advance...

---

### Post by nvteighen on 2010-09-02
Hm... first, do this:

```

bzr revert

```

That will revert the branch to its state before the merging (unless you forced a merge with uncommited changes).

---

### Post by SevenMachines on 2010-09-02
> $ bzr help resolve
Purpose: Mark a conflict as resolved.
Usage:   bzr resolve [FILE...]
.....
Description:
  Merge will do its best to combine the changes in two branches, but there
  are some kinds of problems only a human can fix.  When it encounters those,
  it will mark a conflict.  A conflict means that you need to fix something,
  before you should commit.
  
  Once you have fixed a problem, use "bzr resolve" to automatically mark
  text conflicts as fixed, "bzr resolve FILE" to mark a specific conflict as
  resolved, or "bzr resolve --all" to mark all conflicts as resolved.In essence, using bzr resolve says "i've taken care of these conflicts, ignore them from now on"

[EDIT] Sorry, i missed that you've already tried this!

---

