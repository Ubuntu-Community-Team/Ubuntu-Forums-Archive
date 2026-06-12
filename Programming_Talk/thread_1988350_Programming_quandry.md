---
title: "Programming quandry"
date: 2012-05-27
forum: Programming Talk
---

### Post by dylbud on 2012-05-27
Just wondering if anyone has any ideas for a solution to this problem:

There is a website that I visit often ([http://www.ralphpatt.com/Song.html](http://www.ralphpatt.com/Song.html)) which contains simple text-only pages of hundreds old jazz standard chord progressions. They are all contained in a list on one page that links to each song in a separate html file.

I want to create a single text file from all those pages that I can print, or put into a word processor and then print. So I can put it on my music stand and/or carry it with me.

I could just click, select all, copy, paste into text file, over and over again for all the songs, but I was thinking that with a little creativity there may be a better way.

I can program well with shell scripts and javascripts, and very basic levels with a few others, but I'm not sure what other languages would be applicable. 

If you know how to do this, please don't do it for me. I'm into learning about programming in addition to jazz :)  Just let me know if you have any ideas or guidance. Thanks!

---

### Post by ian dobson on 2012-05-27
Have a look at wget, then a cat with redirection. Then print.

Or write a scraper/spider in perl.

Regards
Ian Dobson

---

### Post by Tony Flury on 2012-05-27
Personally I would suggest python rather than perl for this - but it does not sound overly complex.

---

### Post by roelforg on 2012-05-27
> **Tony Flury said:**
> Personally I would suggest python rather than perl for this - but it does not sound overly complex.

I'd use php for this.
Retreiving a webpage is as simple as:
```

$content_of_page = file_get_contents($url);

```
and using tidy+simplexml to parse the main page to extract the links is very simple (pun intended :P)
Now just use file_get_contents to retreive the pages and slap them together.

---

### Post by Bodsda on 2012-05-27
Recursive wget with a 1 level depth does the trick. It does grab some needless stuff like the jpg's and css files, but the resulting <site>/VB/ dir contains all of your song sheets

```

wget -r -l 1 http://www.ralphpatt.com/Song.html

```Bodsda

---

