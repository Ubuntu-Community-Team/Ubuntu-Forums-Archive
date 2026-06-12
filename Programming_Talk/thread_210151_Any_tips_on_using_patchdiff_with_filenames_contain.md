---
title: "Any tips on using patch/diff with filenames containing spaces?"
date: 2006-07-06
forum: Programming Talk
---

### Post by munckfish on 2006-07-06
Hi

It seems that patch and diff's inability to handle filenames/paths containing spaces is a well known shortcoming and is mentioned in the diff info manual. Yet it seems nothing has been done to correct it. 

Removing spaces from paths isn't always an option especially if you are patching someone elses source code. This problem must be encountered for many apps packaged for ubuntu so I'm presuming that there must be some decent ways to get around this problem.

Does anyone have any tips and tricks they could share on how to work around this issue?

Any time I've used them before and faced this problem I've just ended up having to exclude problem files and try to write a shell script to deal with files patch/diff barf on. But that sort of reduces the efficiency benefit of working with these tools.

Thanks ahead for any tips which are shared.

---

### Post by taurus on 2006-07-06
Use " " or put a \...
```

"name of the file"
-or-
name\ of\ the\ file

```

---

### Post by asimon on 2006-07-06
In what way do diff and patch have problems with spaces in file names? I couldn't find anything about that in their man pages.

```

$ echo foo >> "Foo 1"
$ echo bar >> "Bar 2"
$ diff Foo\ 1 Bar\ 2
1c1
< foo
---
> bar
$ diff -u Foo\ 1 Bar\ 2 > "Foo Bar Patch.patch"
$ patch < "Foo Bar Patch.patch"
patching file 'Foo 1'
$ cat Foo\ 1
bar

```

---

### Post by munckfish on 2006-07-06
asimon: The problem occurs when using diff -r on trees of changed sources.

Here's the link to the manual page with the note about the issue: [Unusual Filenames]("http://www.gnu.org/software/diffutils/manual/html_node/Unusual-File-Names.html#Unusual%20File%20Names")

Diffing just two files isn't a problem as you can use quotes or escapes on the command line when you specify their names.

However, if you are generating a patch for a tree of code then the diff outputs the patch successfully but when you come to apply it using patch you get a problem. E.g.:

```
srctree/
   my dir with spaces/
      afile.txt
```

If you make a patch for a change to afile.txt and try to apply it, the patch program will start looking for "srctree/my". 

In fact the last time this happened to me my patch was creating a subtree of files which didn't exist in the target tree. The directory contained a theme for a web app. The dir name was the theme title and contained a space in it's name (for e.g. 'Theme Name'). When I applied the  patch, the patch bin went crazy for a bit and created a single file instead of the directory itself (just called 'Theme') and filled it full of all the file data (text and binary) which was supposed to be in the subtree. ](*,).

Taurus: I presume you are indicating that the filepaths can be edited in the patch file? (I'll go try anyway)

---

### Post by asimon on 2006-07-07
> **munckfish said:**
> asimon: The problem occurs when using diff -r on trees of changed sources.

Here's the link to the manual page with the note about the issue: [Unusual Filenames]("http://www.gnu.org/software/diffutils/manual/html_node/Unusual-File-Names.html#Unusual%20File%20Names")

Wow, I didn't knew this, really disappointing.

---

