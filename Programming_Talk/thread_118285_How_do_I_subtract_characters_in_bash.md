---
title: "How do I subtract characters in bash?"
date: 2006-01-16
forum: Programming Talk
---

### Post by tux101 on 2006-01-16
I need help making a calculating script for bash.  Would someone please help me out?

What I am trying to do is enter an entry, the script will do a modifcation of the entry.  Then use the sum to carry out another task.

Lets say I ran the script, and the script asked me for the entry with
```
echo -n "entry: "
read entry

```

And I put in there "tux101@fakemail.com"

The script then carries out a simple calculation of subtracting the "101@fakemail.com"  And then converts the "tux" into $I.

Then the script can use the $I to carry out other commands.  Lets say it uses $I for a confirmation that will echo "Hi, Tux!  Is [email]tux101@fakemail.com[/email] spelled correctly?"

Don't worry about the confirmation part.  I just want to know how I can get the script to modify an entry and then use the sum of it as a $I.

---

### Post by cwaldbieser on 2006-01-17
[QUOTE=tux101]I need help making a calculating script for bash.  Would someone please help me out?

What I am trying to do is enter an entry, the script will do a modifcation of the entry.  Then use the sum to carry out another task.

Lets say I ran the script, and the script asked me for the entry with
```
echo -n "entry: "
read entry

```

And I put in there "tux101@fakemail.com"

The script then carries out a simple calculation of subtracting the "101@fakemail.com"  And then converts the "tux" into $I.

Then the script can use the $I to carry out other commands.  Lets say it uses $I for a confirmation that will echo "Hi, Tux!  Is [email]tux101@fakemail.com[/email] spelled correctly?"

Don't worry about the confirmation part.  I just want to know how I can get the script to modify an entry and then use the sum of it as a $I.[/QUOTE]

The following bash syntax may help:
```
${var:N}
${var#pattern}
${var##pattern}
${var%pattern}
${var%%pattern}
${var/pattern/string}
```

They are all ways to manipulate string variables.  You could use tools like sed or awk, too.

For your example:
```

$ x="tux101@fakemail.com"
$ echo ${x%@*}
tux101

```

---

