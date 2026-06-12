---
title: "Sourcing a File in A Different Directory"
date: 2010-03-23
forum: Programming Talk
---

### Post by sharpdust on 2010-03-23
In my .cshrc I do the following:

```

source someDirectory/someFile

```

In someDirectory/someFile, I have

```

source ./anotherFile

```

anotherFile is contained in someDirectory

So the structure looks like this:

/home/me/.cshrc
/home/me/someDirectory/someFile
/home/me/someDirectory/anotherFile

When it tries to source anotherFile it complains it can't find it. I completely understand the reasoning since it's not in the same directory as the initial .cshrc, but is there a way to get around this?

---

### Post by Compyx on 2010-03-23
One way would be to do a 'cd someDirectory' and then source the file, that way the next source also works:```

cd someDirectory
source someFile
cd ..

```

Still looks like a ugly hack to me. Another way would be to source both files in the first file, but that'll only work if the source command of the second file isn't part of some conditional construct.

Using absolute pathnames is another way to get the source commands to work, but would make the whole script rather unflexible.

Perhaps the Advanced Bash Scripting Guide ([http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")) has something useful to add. Although I've only been able to find a script that sources itself.

---

