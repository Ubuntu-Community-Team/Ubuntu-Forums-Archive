---
title: "[PHP] Adding new lines to an rss feed"
date: 2010-07-04
forum: Programming Talk
---

### Post by ELD on 2010-07-04
Hi all i run the website [GamingOnLinux]("http://www.gamingonlinux.info") and am having a little trouble with my rss feed.

It is a custom design -> [http://www.gamingonlinux.info/news_rss.php](http://www.gamingonlinux.info/news_rss.php) currently i remove the br tags and replace them with \n but it doesn't seem to give it a new line...so currently all the text is squished together :(

Can anyone give me a few tips?

Cheers :KS

---

### Post by ju2wheels on 2010-07-05
Well, you had it correctly before to be honest. A newline (\n) in HTML/XHTML code is always ignored. If you want to add a line break it has to be <br /> .

If you are reading the XML into something else and parsing it, then you should be replacing <br /> with a space or newline so that the words at the end and beginning of a sentence dont turn into one word.

I would also run the output of each section through htmlentities().

---

### Post by ELD on 2010-07-11
Trouble is when i leave them in the text disappears on the firefox rss reader.

---

