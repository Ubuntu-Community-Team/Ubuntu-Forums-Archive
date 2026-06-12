---
title: "Python dictionary"
date: 2009-06-23
forum: Programming Talk
---

### Post by JordyD on 2009-06-23
This is NOT about the Python built-in data type.

I'm looking for a dictionary that I can use with python. I need to be able to query a dictionary for words and what part of speech they're in (verb, preposition, etc.) I originally though of aspell, but I think that only does spell checking. I'd prefer cross-platform, but it's definitely not required, only that it work in Linux.

Does anybody know of something like this? I'm not sure if I'm being too clear about this, so feel free to query me about it.

Thanks,
Jordy

---

### Post by Can+~ on 2009-06-23
Ubuntu comes with a built-in dictionary (gnome-dictionary), I remember this because Randall hacked the game ghost with it:

[http://blag.xkcd.com/2007/12/31/ghost/](http://blag.xkcd.com/2007/12/31/ghost/)

---

### Post by JordyD on 2009-06-23
Can I interact with it in Python (or C, C++, whatever)?

---

### Post by ricegf on 2009-06-24
You might try the thesauri (e.g., th_en_US_v2.dat) in /usr/share/myspell/dicts. They are plain text, with parts of speech on the line(s) following each word. Should be just the ticket.

---

### Post by JordyD on 2009-06-24
> **ricegf said:**
> You might try the thesauri (e.g., th_en_US_v2.dat) in /usr/share/myspell/dicts. They are plain text, with parts of speech on the line(s) following each word. Should be just the ticket.

Yes, this is perfect. Thank you very much.

What is this from, by the way? Is it Ubuntu-specific?

---

### Post by Viva on 2009-06-25
You can use wordnet

---

### Post by ricegf on 2009-06-26
> **JordyD said:**
> Yes, this is perfect. Thank you very much.

What is this from, by the way? Is it Ubuntu-specific?

I believe it comes with OpenOffice.org, so it should be available on Linux distros that aren't space-sensitive. 

It will be in a different path on Windows (see [http://www.openoffice.org/servlets/ReadMsg?list=users&msgNo=108520](http://www.openoffice.org/servlets/ReadMsg?list=users&msgNo=108520)), so if you're seeking some portability, make its path part of your configuration file. 

If you plan to distribute your program, you could also include a link to the download file - it's open source as well, I believe.

---

### Post by smartbei on 2009-06-26
I have used wordnet - install through the repos, and then the interesting files can be found at /usr/share/wordnet/index.*

---

