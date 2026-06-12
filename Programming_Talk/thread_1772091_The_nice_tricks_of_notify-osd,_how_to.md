---
title: "The nice tricks of notify-osd, how to?"
date: 2011-05-31
forum: Programming Talk
---

### Post by hakermania on 2011-05-31
We've al seen the tricks of notify-osd, when, for example, I have a message in Pidgin (let's say "Hi")
the notification says
```
Hi
```when the user that's talking to me continue typing, let's say "How are you?" The notification will add the text 'How are you?' below the 'Hi', without actually changing the notification itself.

Another trick i've seen is the one with the banshee, which can change the notification whenever it wants, I mean, when you change the track, you get a notification like
```
"Imagine
John Lennon"
```if, at the moment that this notification is shown you change track again, immediately the notification is closed and another one pop-ups with the next track you choose. Using notify-send you have to w8 for the one notification to close in order to show another one...
Are all these functions of notify-osd possible to be done with notify-send?
I don't think so...
Any ideas :/ ?

---

### Post by slavik on 2011-05-31
use the library

---

### Post by hakermania on 2011-06-02
Ok, could suggestion but since the tool is there....
Anyway, you're right, the easiest way is most of the times the worst way :/

---

