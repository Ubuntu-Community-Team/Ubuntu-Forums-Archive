---
title: "[solved!] Mass renaming multiple directories!"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2013-03-31
Can anyone give me some command line renaming help?

I foolishly decided to rename all my media directories with the year the show was made at the end of it.  For instance:

/television/Dallas (2012)
//01) Season One
//02) Season Two
/television/Downton Abbey (2010)
//01) Series One
//02) Series Two

Now XBMC insists on asking me to rename the show every time I do an import.

Can any of you recommend a command line renaming sequence that would simply strip the directory name of the space, parenthesis, date , parenthesis?

Thanks!  I'd really hate to have to manually rename everything all over again.  Also, everything is on my portable HD in case that matters.

---

### Post by monkeybrain2012 on 2013-04-01
There are apps that do that,

[http://gprename.sourceforge.net/](http://gprename.sourceforge.net/)

or if you are on KDE

[http://www.krename.net/](http://www.krename.net/)

Edited: Turns out both are in the repository,

---

### Post by mechdave on 2013-04-01
There should be a script on your system called rename. have a look at this solution using rename --> [http://stackoverflow.com/questions/2709458/bash-script-to-replace-spaces-in-file-names](http://stackoverflow.com/questions/2709458/bash-script-to-replace-spaces-in-file-names)

---

### Post by bornagainpenguin on 2013-04-01
> **monkeybrain2012 said:**
> There are apps that do that,

[http://gprename.sourceforge.net/](http://gprename.sourceforge.net/)

or if you are on KDE

[http://www.krename.net/](http://www.krename.net/)

Edited: Turns out both are in the repository,

I was looking into those last night while I waited for a reply.  Unfortunately I don't know how to properly use wildcards to block out the entire area I want to remove.

[IMG]http://i.imgur.com/fK8Zutf.png[/IMG]

See what I mean?

---

### Post by steeldriver on 2013-04-01
if they're all in the current directory (not different levels of subdirs) you could probably do something like

```
rename -nv 's# \([0-9]+\)/#/#' */
```

[0-9]+ matches any non-zero number of digits between the parentheses - you could be more strict with [0-9][0-9][0-9][0-9] which is exactly 4 digits. The trailing / on the shell glob (wildcard) restricts it to directories. NB the 'n' switch tells rename not to actually take any action - test the expression carefully and only remove it if you're sure it's matching correctly.

If it needs to descend subdirs, you could enable shell globstars:

```
shopt -s globstar
rename -nv 's# \([0-9]+\)/#/#' ****/***/
```

or you could do something with find e.g.

```
while read -r -d $'\0' dir; do echo mv "${dir}" "${dir%(????)}"; done < <(find . -type d -regex '.* ([0-9]+)' -print0)
```

(the 'echo' does the same as the -n for the rename)

---

### Post by bornagainpenguin on 2013-04-02
> **steeldriver said:**
> if they're all in the current directory (not different levels of subdirs)

Everything is on my portable 2TB USB drive.  It's my primary back up of all my media right now.  I'm trying to get it organized and then I want to import everything in it to XBMC, then have it export back out to the individual directories of the XBMC library...  That way once I have everything exported I can copy over my Dad and Mom's television shows to my older 1TB drive for an (hopefully) easy import process at their house, instead of taking hours to download everything on their dinky little DSL connection.

My stuff is organized like so:

/television
//show1
//show2
//show3
//...

/movies
//movie1
//movie2
//...

> **steeldriver said:**
> if they're all in the current directory (not different levels of subdirs) you could probably do something like

```
rename -nv 's# \([0-9]+\)/#/#' */
```

[0-9]+ matches any non-zero number of digits between the parentheses - you could be more strict with [0-9][0-9][0-9][0-9] which is exactly 4 digits. The trailing / on the shell glob (wildcard) restricts it to directories. NB the 'n' switch tells rename not to actually take any action - test the expression carefully and only remove it if you're sure it's matching correctly.

I tried this with a test directory with two directories to test it out in my home directory.  This is what I got:

```
 cd test
~/test$ rename -nv 's# \([0-9]+\)/#/#' */
abc (1987)/ renamed as abc/
xyz (1991)/ renamed as xyz/
```

So far, so good right?  Only, when you look at the directory, everything is still named as it was before!  I'm not sure what I did wrong...

--bornagainpenguin

---

### Post by steeldriver on 2013-04-02
> **bornagainpenguin said:**
> 
So far, so good right?  Only, when you look at the directory, everything  is still named as it was before!  I'm not sure what I did  wrong...

you missed this bit... you need to change 'rename -v**n** ... ' to 'rename -v ...' 

> **steeldriver said:**
> NB the 'n' switch tells rename not to actually take any action - test the expression carefully and only remove it if you're sure it's matching correctly

---

### Post by bornagainpenguin on 2013-04-02
Whoops!  Well that's exactly why I'm so nervous here.  I desperately am afraid of making silly typos like this and trashing my media!

Thanks for the reply!  I just fixed what you pointed out and it worked great.

[s]One last question--is there any reason why the file system on the portable being NTFS would represent a problem?[/s]

Everything worked splendidly!  Thanks for your help!

---

