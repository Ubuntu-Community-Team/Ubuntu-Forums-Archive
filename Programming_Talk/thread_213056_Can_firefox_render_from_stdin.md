---
title: "Can firefox render from stdin?"
date: 2006-07-10
forum: Programming Talk
---

### Post by Peepsalot on 2006-07-10
I have an idea for a script which would generate some html based on results of a grep command.  I would like to be able to view these results directly in firefox, preferably without writing a file to disk first.  Is there any way to pipe input to firefox like that?

---

### Post by dabear on 2006-07-10
> **Peepsalot said:**
> I have an idea for a script which would generate some html based on results of a grep command.  I would like to be able to view these results directly in firefox, preferably without writing a file to disk first.  Is there any way to pipe input to firefox like that?

Sorry, I could not find any flag to pass to fx to manage this. However, this will work
```


tmpfilename="/tmp/tmp.html";#should be absolute path
htmlstring="<html><strong>Your html here..</strong></html>"

echo $htmlstring >$tmpfilename;
firefox "file://$tmpfilename";rm $tmpfilename #removes tempfile after use

```

---

### Post by Peepsalot on 2006-07-10
Ok.  I didn't try that because I thought there would be a problem with firefox not finishing loading before the file was deleted.

But it works so I guess that's not really a problem.  Thanks.

---

### Post by fluffington on 2006-07-10
> **Peepsalot said:**
> Ok.  I didn't try that because I thought there would be a problem with firefox not finishing loading before the file was deleted.

Wouldn't you have to start Firefox in the background to do that (firefox "file://$tmpfilename" **&**;rm $tmpfilename)? As it is, it waits 'til Firefox quits before deleting anything.

---

### Post by Peepsalot on 2006-07-10
> **fluffington said:**
> Wouldn't you have to start Firefox in the background to do that (firefox "file://$tmpfilename" **&**;rm $tmpfilename)? As it is, it waits 'til Firefox quits before deleting anything.
Yeah, but if firefox is already open, it will load new tab, and the  sript will continue without waiting for Firefox to close.

It still works...i was just not too sure about it before.

---

### Post by Peepsalot on 2006-07-11
Check this out.  I posted the same question on the mozillazine forums and got an answer pointing me to this: 
[http://en.wikipedia.org/wiki/Data:_URI_scheme](http://en.wikipedia.org/wiki/Data:_URI_scheme)
It's pretty cool.

---

