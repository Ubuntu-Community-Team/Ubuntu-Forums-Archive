---
title: "&quot;yes to all&quot; in bash?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by PGScooter on 2008-08-15
Hi,

when doing some command, for example, cp, or fsck.vfat, I realize that I should have chosen a "yes to all" option instead of interactively. Instead of exiting and reissuing the command with that option, is there anything that will input as "yes to all" when confronted with yes/no?
I assume that this depends on the particular command and not bash, itself?

thank you

---

### Post by RealPSL on 2008-08-15
From what I have seen it is specific to the command
```
cp -f source target
```
will assume the yes
```
fsck -y /some_file_system
```
will also assume yes

---

### Post by dwhitney67 on 2008-08-15
Try the "yes" command when running a script that prompts for yes/no.  For example:
```
$ yes "yes" | script.sh
```
This works too if removing file(s) or whatever:
```
$ yes "yes" | rm -i file1 file2 file3
```

---

### Post by t0p on 2008-08-15
> **dwhitney67 said:**
> Try the "yes" command when running a script that prompts for yes/no.  For example:
```
$ yes "yes" | script.sh
```

All the yes command does for me is print "y" to st out, repeatedly, until I hit Ctrl-C to kill it!

**EDIT:** Silly me!  I can see its utility now.  You could pipe it to fsck, ie
```
yes | fsck /file/system
```
and it would save you from hitting all those y's...

---

### Post by dwhitney67 on 2008-08-15
That's correct.  That is what "yes" does... it repeats the value you supply (if any) indefinitely until the script (or command) terminates.  Bear in mind that "yes" is not appropriate for all situations; there may be scripts that ask questions that require an answer other than the value 'y'.

Anyhow, the usage for "yes" is:
```
$ yes [value] | <cmd or script>
```

---

### Post by PGScooter on 2008-08-15
that's an interesting command.

Is there anyway to do that during a script though? that is, once i have a script running and it keeps prompting for a y, how can I implement that code? Does bash allow you to pipe commands to an already running script?

Thanks

---

### Post by dwhitney67 on 2008-08-15
> **PGScooter said:**
> that's an interesting command.

Is there anyway to do that during a script though? that is, once i have a script running and it keeps prompting for a y, how can I implement that code? Does bash allow you to pipe commands to an already running script?

Thanks
Not that I am aware of.

---

