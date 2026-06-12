---
title: "How can I get the Google Speech Recognition that we use on Android OS."
date: 2010-07-11
forum: Programming Talk
---

### Post by gopi on 2010-07-11
Hi all,

Can anyone help me in getting the Android Speech Recognition API working under the normal Java SDK?

I mean, I am looking for an Opensource, reliable SDK for an application launcher using the voice recognition, something like the GNOME DO.

Thank You

---

### Post by soltanis on 2010-07-11
CSAIL seems to have a version of this: [http://wami.csail.mit.edu/](http://wami.csail.mit.edu/)

I was unable to find a direct interface on Google to Google's own speech recognition engine. It is pretty evident though that they upload speech samples to some server which interprets it into text and returns that back. Their API has shown up in quite a few applications including Google Voice, but I don't see a way to use it directly.

You can also use [CMU Sphinx]("http://cmusphinx.sourceforge.net/"), which is a toolkit for speech recognition.

---

### Post by robert shearer on 2010-08-13
also using the sphinx engine is....
[http://vedics.sourceforge.net/](http://vedics.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?t=1525830](http://ubuntuforums.org/showthread.php?t=1525830)
[http://sourceforge.net/projects/vedics/](http://sourceforge.net/projects/vedics/)

---

