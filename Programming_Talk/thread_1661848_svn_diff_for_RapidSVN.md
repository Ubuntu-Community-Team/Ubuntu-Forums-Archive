---
title: "svn diff for RapidSVN?"
date: 2011-01-07
forum: Programming Talk
---

### Post by Arthur_D on 2011-01-07
Hi, is there anything like 'svn diff' in terminal for RapidSVN? The diff tool thingie in Preferences does not seem to do the same, as it want to compare two files. What I want is to compare folders to see what changes I've made, like 'svn diff' and 'svn status'. This is to prevent me to commit changes I don't want to commit.

Thanks. :)

---

### Post by MadCow108 on 2011-01-07
I don't know rapidsvn but you can use meld on the working folder to get this information nicely displayed.

---

### Post by Arthur_D on 2011-01-07
That's what I have set in Preferences for "Diff tool", but I still get an error thrown at me when trying to just diff in a folder instead of comparing files.
Dunno what I'm doing wrong. :confused:

---

### Post by beau.raines on 2011-03-08
From within RapidSVN, my experience that the diff will only work on the same working copy, but different revisions. It seems from your description that you are comparing across working copyies (eg. comparing a branch to a trunk).

If I want to do that, I just use meld outside of RapidSVN. meld does nice directory comparisons (which I think you already know, based upon your post).

---

### Post by ve4cib on 2011-03-08
You can set up meld for use as a diff/merge tool with RapidSVN.  Documentation for doing that is here:

[http://www.rapidsvn.org/index.php/OnlineHelp:Contents#Meld_Setup_for_Use_as_Merge_Tool](http://www.rapidsvn.org/index.php/OnlineHelp:Contents#Meld_Setup_for_Use_as_Merge_Tool)

---

