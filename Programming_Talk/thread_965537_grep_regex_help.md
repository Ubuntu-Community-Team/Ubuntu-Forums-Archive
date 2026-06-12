---
title: "grep regex help"
date: 2008-10-31
forum: Programming Talk
---

### Post by tmetzcc325 on 2008-10-31
Hey guys, I have a quick question that I am sure someone will be able to help me with.  I am pretty new to using regular expressions.  I know the basics, but am not very good with expression matching yet.  So here is what I am trying to do:

I have a directory of CDs that I have ripped, and each CD has its own folder, names like this: Artist - Year - Album (ex. ACDC - 1980 - Back in Black).  In that same directory, I have other folders that contain other random songs from that artist (so I also have a folder just named ACDC with a few files in it).  What I want is to generate a list of only those folders that are full albums (they have a year in the directory name).

This is what I was trying to do:

ls /home/tom/Music/rock | egrep '[-]\s[0-9]{4}\s[-]'

This seems to work pretty well, but for some reason, it is missing some entries (311 - 1995 - 311, Avenged Sevenfold - 2005 - City of Evil, for example)

There has to be a simple way of doing this, right?  How come some of these entries would be missed?

---

### Post by stylishpants on 2008-10-31
You're using the special '\s' character class in the regexp you provided, but this feature is not supported by egrep.  That's a feature of perl-compatible regexps, egrep uses POSIX regexps.

You can use pcregrep to get that feature.  I tried out the example dir names in your email with pcregrep using your regexp unmodified, and it worked.  You can use bare perl as well.

Your regex looks OK.  It's a little unusual that you're putting the - character in a character class all by itself (ie. [-] ) instead of escaping it (ie. \-), but it's allowed.

```

bob@machine:/tmp/test$ mkdir "311 - 1995 - 311"
bob@machine:/tmp/test$ mkdir "Avenged Sevenfold - 2005 - City of Evil"
bob@machine:/tmp/test$ mkdir "ACDC - 1980 - Back in Black"
bob@machine:/tmp/test$ mkdir ACDC


bob@machine:/tmp/test$ ls -1
311 - 1995 - 311
ACDC - 1980 - Back in Black
Avenged Sevenfold - 2005 - City of Evil
ACDC

bob@machine:/tmp/test$ ls  | perl -ne 'print if /[-]\s[0-9]{4}\s[-]/'
311 - 1995 - 311
ACDC - 1980 - Back in Black
Avenged Sevenfold - 2005 - City of Evil

bob@machine:/tmp/test$ ls  | pcregrep '[-]\s[0-9]{4}\s[-]'
311 - 1995 - 311
ACDC - 1980 - Back in Black
Avenged Sevenfold - 2005 - City of Evil

bob@machine:/tmp/test$ ls  | pcregrep '\-\s[0-9]{4}\s\-'
311 - 1995 - 311
ACDC - 1980 - Back in Black
Avenged Sevenfold - 2005 - City of Evil


```

---

### Post by ghostdog74 on 2008-10-31
no need to use regular expression. If you only want to check if  there is a year digits and your directory structure is: something - year - something

```

# ls -1
ACDC - 1980 - Back in Black
Avenged Sevenfold - 2005 - City of Evil
testfile
sdf - sfs323 - dsfsdf

# ls -1 | awk -F"-" '$2+0==$2'
ACDC - 1980 - Back in Black
Avenged Sevenfold - 2005 - City of Evil

```

---

### Post by tmetzcc325 on 2008-11-14
Thanks guys, I will have to take a look at these.  My installation was hosed when I tried to upgrade to Ibex (couldn't get past login page...think it has something to do with Compiz and my old computer's intergrated graphics chip not being supported for some reason), so I haven't had time to look at this yet.

I don't know any awk, so I will have to have a look at that.  The thing that confused me most was that for most of my directories, the original regex I was using worked fine...it just missed on some of them, even though they had the same naming structure.  I'll play with it a bit more later on.

Again, thanks for the input.

Tom

---

### Post by geirha on 2008-11-14
You could simply use pathname expansion too
```
ls -d *-*-*/
```

---

### Post by tmetzcc325 on 2008-11-14
That is a useful trick, thanks.  The only problem is that it is not only showing directories....it is also showing files that match the pattern as well.  I can expand upon it to only get directories, though.

---

### Post by geirha on 2008-11-14
No, that's what the ending / is for, to only match directories ...

---

### Post by tmetzcc325 on 2008-11-14
Ahh, I see I missed that trailing slash.  Worked like a champ, thanks!

Do you have an online reference for this sort of thing?  I read through the ls man pages when first starting at this, and didn't see anything regarding these tricks.  Or should I be reading up on bash instead?

---

### Post by geirha on 2008-11-14
Bash is the one doing the pathname expansion (try echo *-*-*/ and you'll get the same list). Run ```
man bash
``` and search for "Pathname Expansion" by hitting:
```
/Pathname Expansion
```

The nice thing about pathname expansion as opposed to grepping the output of ls, is that you don't need to think about escaping spaces or odd characters in filenames. If you wanted to move these directories to some other place, you could just do:
```
mv *-*-*/ ~/albums/
```

The Beginner and advanced bash scripting guides at [http://tldp.org](http://tldp.org) are good reads btw. Contains a lot of examples.

---

### Post by tmetzcc325 on 2008-11-14
Thanks a lot...this is a big help.  The hardest part is knowing that these options exist, otherwise I wouldn't even know what to look up.

---

