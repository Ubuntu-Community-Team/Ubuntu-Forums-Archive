---
title: "Edit .conf file from /bin/sh?"
date: 2011-05-12
forum: Programming Talk
---

### Post by jsbiff on 2011-05-12
Hi,

   I'm working on writing a shell script. One of the things I need to do from the script is to modify a config file. The config file has a pretty basic and common format. It's a plain text file. It's basically a collection of variable name:value pairs. One variable per line. So, a typical line would look like:

DataDir:/var/lib/programname/ServerDb
ListenPort:9876

I think this is a fairly standard/typical format for config files on Unix-like systems.

So, the question is, what program would you recommend I use to be able to easily change/add values? Would something general purpose like awk or sed be easy to put to this purpose? Is there any program which is generally already available on pretty much all Linux (and other Unix-like systems, e.g. Mac OS X), which is more purpose built for manipulating such files (I would think that this is a fairly common need for people writing shell scripts)?

I think that, ideally, if such a thing exists, I'd like a program which operates similar to the following examples (assume editconf is the name of the program which queries/modifies the conf files):

```

#[forum post edit: I forgot that the path-filename would have to be an argument,
# so updated the post to include that so the examples make sense] 

# if a particular variable/key is found, update it, else add it to
# end of file; set return value to 0 on success, not zero to indicate #failure

 editconf $conffilepath --updatekey keyname newvalue

# query the current value of a key; print current value to stdout;
# set return value to 0 if the key was found, not zero if key
# does not exist in the file.

 editconf $conffilepath --querykey keyname

```

If such a purpose-specific program doesn't exist, can anyone suggest the easiest way to accomplish the same things using a more general-purpose command line utility?

Thanks.

**UPDATE 2011-05-12 20:40UTC :** I thought sed might be useful in this situation, so I checked a sed tutorial, and found it's pretty easy to do this with sed. Some example code, for anyone else who is looking for something similar (you might want to add additional code to backup the file before editting, and perhaps check return values to see if there were any errors to roll back to the backup if error; this is a minimal example):

```

 sed 's/\(^keyname:\).*/\1newvalue/' <$conffilepath >$conffilepath.tmp
 cp $conffilepath.tmp $conffilepath
 rm $conffilepath.tmp

```

---

### Post by stylishpants on 2011-05-12
Perl can do this in-line (without the tmp file.)
It also includes the backup functionality you describe, and uses the more featureful perl-compatible regular expressions.

```

# modify conf file in-line
# note the addition of \s* to handle whitespace before/after the key name
perl -pi -e 's/^\s*(keyname)\s*:.*/\1:newvalue/' $conffilepath

# modify conf file in-line and make a backup first
perl -pi.bak -e 's/^\s*(keyname)\s*:.*/\1:newvalue/' $conffilepath
ls $conffile.bak


```

For more information, see the 'perlrun' man page, and read up on the -i and -p flags.

---

### Post by jsbiff on 2011-05-12
Thanks for the suggestion about perl. I had given some consideration to using perl, but not being too familiar with perl (I took a college course on web development that briefly covered perl, like 8 years ago, and barely remember any of it, but I could relearn it if I need to; just haven't used it much in my career which I would have preferred to be more Linux/Unix oriented, but as such things tend to go, has been focused more on Windows).

That looks like a very elegant solution. I may end up using that, although I've already written my shell script using sed (including extra logic to backup the file, check return values from pretty much every command, etc - which it sounds like PERL would have done all that for me; oh well) so as long as that works as expected, I'll probably just stick with what I've already wrote (but if I had to do it again, I'd use the one line of perl).

If you know what you're doing with Perl, it's obvious you can accomplish a lot with very little code. Unfortunately, I don't really know what I'm doing with it. :P

---

### Post by Barrucadu on 2011-05-13
> **jsbiff said:**
> **UPDATE 2011-05-12 20:40UTC :** I thought sed might be useful in this situation, so I checked a sed tutorial, and found it's pretty easy to do this with sed. Some example code, for anyone else who is looking for something similar (you might want to add additional code to backup the file before editting, and perhaps check return values to see if there were any errors to roll back to the backup if error; this is a minimal example):

```

 sed 's/\(^keyname:\).*/\1newvalue/' <$conffilepath >$conffilepath.tmp
 cp $conffilepath.tmp $conffilepath
 rm $conffilepath.tmp

```

You don't need to make a temporary file.

```
sed -i 's/\(^keyname:\).*/\1newvalue/' $conffilepath
```

---

