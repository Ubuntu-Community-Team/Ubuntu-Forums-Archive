---
title: "Creating a clone of Wordweb"
date: 2007-10-31
forum: Programming Talk
---

### Post by legends2k on 2007-10-31
There, already is [Wordnet ]("http://en.wikipedia.org/wiki/Wordnet")a free semantic lexicon, for linux, but its browser (Wordnet Browser) is really awful, unlike the cool interface of Wordweb in Windows.

Likewise, the default Dictionary app. in Ubuntu looks-up the net for the definition, which is slow in some countries and for ppl who cannot be always online.

So I thought, it would be handy if there is an application like Wordweb which is not more than 7 MB which does the magic off-line, with all the cool features of Wordweb, since it also uses Wordnet for its database.

I tried searching, and it seems fairly easy to write such an app. using Python & wxGidgets, making the app. stay in the sys. tray to capture a particular keystroke, and popup with the meaning.

So if I can write a decent GUI for Wordnet using Python with similar features of Wordweb, is it possible that we can make it available in the Hardy Heron? If so, how?

And if I use wxWidgets, I think its lib. will also become mandatory to be included for the app to run, is it?

Please, someone try to throw some light on this/guide me!!?

---

### Post by legends2k on 2009-02-01
Well, the above post was 2 years ago by the same person (me!). Now, I am happy to reply for my own question [to *brag* ;)] that I have finally created an replacement for WordWeb in Linux (using Ubuntu, of course!).

[Artha ~ The Open Thesaurus]("http://artha.sourceforge.net/"): (Refer [this thread]("http://ubuntuforums.org/showthread.php?t=1065384") for full details)
Apart from the features that WordWeb gives, Artha has a few additions which it doesn't. When you select some text in a window and press Artha's hot key (say Ctrl + Alt + W). It can either pop-up with the look up of that term OR it can passively show a (balloon tip) notification of the selected term's most important definition. Artha uses WordNet as its backend, hence it works completely off-line!

Artha has two modes, simple & detailed. Simple is what WordWeb gives, which is the default mode, while in detailed mode, you can see relatives of a word with its derivates (Apart from Synonyms & Antonyms, it gives 'Type of', 'Types', 'Similar', etc.with each term further having a relative)

Technically, its written in pure C using GTK+ and libnotify.

---

### Post by sejal on 2009-09-13
Dude, this has been indeed a boon.. just tried your application and it's awesome.. thanks a lot!

---

### Post by soltanis on 2009-09-13
Just to say, you are amazing for actually having gone through and written the application.

+1 to you.

---

### Post by legends2k on 2009-09-14
Thank you guys! I guess it's a small thing, compared to such a big/beautiful project WordNet, which is the actual the back-end, corpus of Artha :)

---

### Post by sunilrjpt on 2013-02-22
Thanks a lot,

Your application is a simply the best. I am using it from last 2 months.
:D

---

### Post by howefield on 2013-02-22
Old thread closed.

---

