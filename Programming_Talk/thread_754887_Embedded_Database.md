---
title: "Embedded Database"
date: 2008-04-14
forum: Programming Talk
---

### Post by rkulp on 2008-04-14
I am a newbie in the Linux world but have experience in programming, most recently VB 2005. I want to use MonoDevelop to write an open source program which has an embedded database for release on both Linux and Windows platforms. What is the best database to choose for this? Are there any "How To" references available? My database experience is limited, mostly MS Access and SQLServer Express. I was planning to write the code in C#.

---

### Post by LaRoza on 2008-04-14
SQLite is good for a single user database.

It is very light and portable.

It works with many languages, although I never used C# so I can't give specific advice there.

If it doesn't work well with C# in Linux (it does in Windows), you can use another language. See: [http://en.wikipedia.org/wiki/SQLite](http://en.wikipedia.org/wiki/SQLite) There is a list of the languages there that can use it, C# is one.

---

### Post by themusicwave on 2008-04-14
Another good one for embedding is Apache Derby or JavaDB as Sun calls it.  

I don't know if it supports C# embedding, but it definitely works great in Java and Java works great on Linux and Windows.

Just another thought.

---

### Post by rkulp on 2008-04-14
> **LaRoza said:**
> SQLite is good for a single user database.

It is very light and portable.

It works with many languages, although I never used C# so I can't give specific advice there.

If it doesn't work well with C# in Linux (it does in Windows), you can use another language. See: [http://en.wikipedia.org/wiki/SQLite](http://en.wikipedia.org/wiki/SQLite) There is a list of the languages there that can use it, C# is one.

Thanks. Initially, this looks like the best choice.  I have looked at the Synaptic Loader and see a myriad of choices for SQLite. Is there a preferred one for the GNOME /MonoDevelop configuration?

---

### Post by rkulp on 2008-04-14
> **themusicwave said:**
> Another good one for embedding is Apache Derby or JavaDB as Sun calls it.  

I don't know if it supports C# embedding, but it definitely works great in Java and Java works great on Linux and Windows.

Just another thought.

Thanks. I will consider it if SQLite does not work out well. I know that SQLite works fine with C# in Windows so that will probably be the best choice.

---

