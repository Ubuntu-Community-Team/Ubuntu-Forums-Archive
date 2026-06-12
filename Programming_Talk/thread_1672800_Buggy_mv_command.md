---
title: "Buggy mv command"
date: 2011-01-21
forum: Programming Talk
---

### Post by tonemgub on 2011-01-21
Hello,
I have upgraded to maverick a few days ago and the "mv" command behaves strangely since then. Here is an example:
```
$ mv Name\ With\ Spaces.pdf NewName.pdf
/bin/mv: cannot stat `Name': No such file or directory
/bin/mv: cannot stat `With': No such file or directory
/bin/mv: cannot stat `Spaces.pdf': No such file or directory
```
while the same command with 'cp' works fine
```
$ cp Name\ With\ Spaces.pdf NewName.pdf
```
Has anyone experienced the same problem? Any idea how to solve this or where to report the problem?
Thanks for your time.

---

### Post by gmargo on 2011-01-22
Do you have an alias or shell script for the **mv** command?  This is not a mv problem, it's entirely a shell issue.

```

$ touch "Name With Spaces.pdf"
$ ls -lgG *Name*pdf
-rw-r--r-- 1 0 Jan 22 09:52 Name With Spaces.pdf
$ mv Name\ With\ Spaces.pdf NewName.pdf
$ ls -lgG *Name*pdf
-rw-r--r-- 1 0 Jan 22 09:52 NewName.pdf

```

Here's a quick way to test if it's an alias or script issue:  Repeat the same command but use the full path to the mv command: **/bin/mv**.

---

### Post by geirha on 2011-01-22
My best guess is you have a broken alias or function by that name. This should tell you if you do have that:
```
type -a mv
```

EDIT: Sorry, missed the text of gmargo's post there. We're guessing the same thing. :)

---

### Post by tonemgub on 2011-01-22
Thank you very much, it was a broken alias as you correctly guessed! I would never have thought of that!

---

