---
title: "A couple of questions"
date: 2006-07-14
forum: Programming Talk
---

### Post by titititi on 2006-07-14
Hi everyone,

First of all, I'm sorry if this is not the correct forum to post this, however, I didn't find another more apropriate.

I have some questions, noob ones, actually:

1 - How can I run 'Clear Private Data' - feature from Firefox - on Terminal? I wanted to add it to a simple clean up script I'm trying to code.

2 - Is it safe to delete the content of /tmp ? Should I do it? Why?

3 - If you ever did a clean up script and care to share, go ahead :D I could use some examples.

Take care everyone

Edit:

4 - And how to use "Clear Recent Documents" feature, also in a script?

---

### Post by fluffington on 2006-07-14
A better place for this would be [Absolute Beginner Talk](http://ubuntuforums.org/forumdisplay.php?f=73) or [Desktop Support](http://ubuntuforums.org/forumdisplay.php?f=132). Maybe a friendly mod will come by and move this thread.

Also, calling a post "A couple of questions" is uninformative and will lead to people not reading your questions (I see about thirty posts with the same title every day, and it's starting to bug me). Use a title that reflects what you're asking in the future.

> **titititi said:**
> 1 - How can I run 'Clear Private Data' - feature from Firefox - on Terminal? I wanted to add it to a simple clean up script I'm trying to code.

This seems to work:
```

cd ~/.mozilla/firefox/<insert profile name here>
rm history.dat
rm formhistory.dat
rm downloads.rdf
rm cookies.txt
rm Cache/*
rm signons.txt

```

> 2 - Is it safe to delete the content of /tmp ? Should I do it? Why?

Depends on whether or not the stuff in /tmp is currently in use. You might break something if whatever process put stuff there is still using it. I don't see any point in clearing it yourself, anyway, when the system should be automatically removing old stuff already.

> 3 - If you ever did a clean up script and care to share, go ahead :D I could use some examples.

You'll have to define "clean up script".

> 4 - And how to use "Clear Recent Documents" feature, also in a script?

In KDE, you can do the following:
```
rm ~/.kde/share/apps/RecentDocuments/*
```
I don't know how to do it in GNOME.

---

### Post by titititi on 2006-07-15
Hi,

First, thanks for the information. Title edited.

'Clean up' script, is something that will delete unnecessary files from the system.

I'm using GNOME ... Maybe someone will know how to do it.

---

### Post by ifokkema on 2006-07-15
Hi,

> **titititi said:**
> First, thanks for the information. Title edited.
I'm not seeing any change here, sorry.

> **titititi said:**
> I'm using GNOME ... Maybe someone will know how to do it.
The file you're looking for is this:
~/.recently-used
It's an XML file. Check the contents, clear recent documents using the functionality in Gnome, and look at the file's contents again. Then you know what your script needs to do with the file :)

---

### Post by titititi on 2006-07-15
Sorry, I edited the post title, not the thread's :S

As for the file ...

I think the way of cleaning the list is by deleting the file. Correct?

---

### Post by ifokkema on 2006-07-15
> **titititi said:**
> As for the file ...

I think the way of cleaning the list is by deleting the file. Correct?
Not sure - use the functionality in Gnome and see what it does to the file. Maybe it just empties the file or keeps one or two lines in it.

---

