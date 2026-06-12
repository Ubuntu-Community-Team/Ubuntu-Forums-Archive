---
title: "[SOLVED] Batch conversion end-of-line Windows - Linux"
date: 2008-02-22
forum: Programming Talk
---

### Post by Average Joe on 2008-02-22
I am not sure if this is the right place to ask, but I'll just give it a try.

I have quite a few perl scripts that I copied from an NTFS disk. These perl scripts now won't run on my Ubuntu box because of the Windows end-of-line characters (^M) on every script line.

[I know ways]("http://en.wikipedia.org/wiki/Newline#Conversion_utilities") to convert every file individually, but this is quite a lengthy process. Is there is smart way to convert all my scripts to the Unix/Linux end-of-line characters in one go?

Changing the names of the scripts is not really an option, in other words, I'd like to keep the input and output filename the same.

---

### Post by jfinkels on 2008-02-22
Take a look at the "tofrodos" package, it's in the repos. [http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)

---

### Post by Average Joe on 2008-02-22
> **jfinkels said:**
> Take a look at the "tofrodos" package, it's in the repos. [http://www.thefreecountry.com/tofrodos/index.shtml](http://www.thefreecountry.com/tofrodos/index.shtml)

Thanks! I just found it myself. It is actually quite simple. It is just:
```
sudo aptitude install tofrodos
find . -name "*.pl" -exec dos2unix {} \;
```
And all my scripts work again. :)

---

