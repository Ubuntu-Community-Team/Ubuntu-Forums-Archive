---
title: "Help me use grep with regex please; i know the JS version but it doesnt seem to work"
date: 2012-02-27
forum: Programming Talk
---

### Post by maxymus on 2012-02-27
Im creating a bash script for a project that will search through my list of backups which are all named in the format: -

dd.mm.yyyy-hh.mm (the last one is hour hour minute minute)

in javascript regular expressions seemed to be pretty easy to do and to find a file in february in JS it would be something like ---


/^([0-9][0-9)\.02\.2011\-([09][09])\.([09][09])$/

but ive tried all different ways to achieve the same result as the one above, ive searched online their doesnt seem to be any good sites for regex in bash, what would be an equivilent in bash

basically i want to plug this regular expression into this line of code here : -

find ~/the/directory -type f -exec basename {} \; | grep '/^([0-9][0-9)\.02\.2011\-([09][09])\.([09][09])$/' > file.list

if i  can get this line of code to work then I will be able to make a loop on it that will turn the files which matched the regular expression into a zipped tarball for archiving purposes. 

P.S. I know this regex doesnt check for date validity its purely intended to find files whose names correspond to feb.2011 for example.

Anyone who could give me anyhelp converting this regex so it will work in bash will be awesome. 

THANKY YOU :D :D :D :D

---

### Post by josephmills on 2012-02-27
> **maxymus said:**
> Im creating a bash script for a project that will search through my list of backups which are all named in the format: -

dd.mm.yyyy-hh.mm (the last one is hour hour minute minute)

in javascript regular expressions seemed to be pretty easy to do and to find a file in february in JS it would be something like ---


/^([0-9][0-9)\.02\.2011\-([09][09])\.([09][09])$/

but ive tried all different ways to achieve the same result as the one above, ive searched online their doesnt seem to be any good sites for regex in bash, what would be an equivilent in bash

basically i want to plug this regular expression into this line of code here : -

find ~/the/directory -type f -exec basename {} \; | grep '/^([0-9][0-9)\.02\.2011\-([09][09])\.([09][09])$/' > file.list

if i  can get this line of code to work then I will be able to make a loop on it that will turn the files which matched the regular expression into a zipped tarball for archiving purposes. 

P.S. I know this regex doesnt check for date validity its purely intended to find files whose names correspond to feb.2011 for example.

Anyone who could give me anyhelp converting this regex so it will work in bash will be awesome. 

THANKY YOU :D :D :D :D

maybe a for loop ? 
for f in [0-9][0-9].[0-9][0-9].[0-9][0-9][0-9][0-9]-[0-9][0-9].[0-9][0-9]; do tar ... "$f"; done

---

### Post by Khayyam on 2012-02-27
maxymus ...

There is no need to grep for the string, find can search based on modification times, and as these are backups their respective modification times will reflect the search string ... so:

```
find /path -type f -newermt 2011-02-01 ! -newermt 2011-02-28 >> file.list
```

This will find all files with modification times for the month of Feb 2011.

HTH ... khay

---

### Post by ofnuts on 2012-02-27
> **maxymus said:**
> Im creating a bash script for a project that will search through my list of backups which are all named in the format: -

dd.mm.yyyy-hh.mm (the last one is hour hour minute minute)

in javascript regular expressions seemed to be pretty easy to do and to find a file in february in JS it would be something like ---


/^([0-9][0-9)\.02\.2011\-([09][09])\.([09][09])$/

but ive tried all different ways to achieve the same result as the one above, ive searched online their doesnt seem to be any good sites for regex in bash, what would be an equivilent in bash

basically i want to plug this regular expression into this line of code here : -

find ~/the/directory -type f -exec basename {} \; | grep '/^([0-9][0-9)\.02\.2011\-([09][09])\.([09][09])$/' > file.list

if i  can get this line of code to work then I will be able to make a loop on it that will turn the files which matched the regular expression into a zipped tarball for archiving purposes. 

P.S. I know this regex doesnt check for date validity its purely intended to find files whose names correspond to feb.2011 for example.

Anyone who could give me anyhelp converting this regex so it will work in bash will be awesome. 

THANKY YOU :D :D :D :D
Maybe you are getting  a bit too stringent here. Something like
```

find -name "??.02.2011-??.??"

```
would be more than enough if your directory structure isn't too polluted ('?' matches a single character). Otherwise, find supports the [] syntax:
```

find -name "[0-9][0-9].02.2011-[0-9][0-9].[0-9][0-9]"

```

---

### Post by maxymus on 2012-02-27
Thank you so much guys, I actually found a way in  the end, i think it was just a slight syntax difference between JS expressions and bash expressions, I think youve given me some really good ideas to simplify my expression, i did think there would be an easier way to do it, im going to try doing it with just find tomorrow and see how that goes and ill let you all know.

I think in my regex i just put a / at the end and a / at the beggining like in JS, when this is not required for bash, after that it worked lol :D

find /media/Backup/Backups/CIS -type d -exec basename {} \; | grep '^[0-9][0-9].1.2012' > /home/max/file.list

and this worked pefectly

then i was able to do a loop on the file that coppied it to another location for acrhiving purposes.

But thank you so much for answering, its really given me some extra ideas and understanding after struggling so long on linux manuals (lol)

---

### Post by Khayyam on 2012-02-28
> **maxymus said:**
> Thank you so much guys, I actually found a way in  the end [...]

Your welcome ... but you may, as ofnut's suggests, be overdoing it.

> **maxymus said:**
> ```
find /media/Backup/Backups/CIS -type d -exec basename {} \; | grep '^[0-9][0-9].1.2012' > /home/max/file.list
```

The question is whether the '|grep' is necessary. Does the following not produce the same output?

```
find /media/Backup/Backups/CIS -type d -newermt 2012-01-01 ! -newermt 2012-01-31 > /home/max/file.list
```

If these are dated backup dirs that were created on the dated suffix then it should produce the same output as the '|grep'.

Doesn't matter I suppose, but there is always an overhead when piping, and so if the task can be achieved without it .. bonus. Anyhow, thought it worth drawing your attention too. 

best ... khay

---

