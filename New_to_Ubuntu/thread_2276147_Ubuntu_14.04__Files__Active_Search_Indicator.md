---
title: "Ubuntu 14.04 | Files | Active Search Indicator?"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by anotherman2 on 2015-04-30
Hello Ubuntu Forum Members!  

Does anyone know how I can tell if a search I am performing in Files is still running?  I keep stumbling over this, as I do not know whether there are simply no results or whether the search is still running.  

Any ideas?  

Thanks!  

Anotherman    

EDIT #1: Sometimes a little indicator shows up in the bottom right corner of the Files window.  It does not show up every time I do a search, though.    

EDIT #2: It seems as if this occurs only when searching NTFS volumes.

---

### Post by GrouchyGaijin on 2015-05-01
It sounds like there is a problem (yeah OK I guess that is obvious or you would not have posted in the first place.).
I just tried searching my home in files and was able to find things buried three and four levels deep in just a matter of seconds.  It could take longer if you are searching through your entire system.

---

### Post by anotherman2 on 2015-05-08
GrouchyGaijin,

Thank you for replying!  Sometimes search is really fast for me, too.  But there are times when it takes quite a while, and although the indicator does not show up, I can tell the search is still going on b/c of more results popping up.

I was wondering whether the indicator should be present whenever there is an active search going on, and if perhaps there is a known bug causing it to disappear/not show at times.

I was also wondering if there was any other way to tell when a specific search has finished.

Anotherman

---

### Post by GrouchyGaijin on 2015-05-08
If by indicator you mean the small word "searching" that appears in the bottom right hand corner of the window in which you are conducting the search, then yes it seems to disappear on my system when at least part of the search criteria have been met.  Regardless, as you pointed out the search does continue even though the word searching is no longer visible.  Honestly, this is the first time I've even noticed the word "searching".

---

### Post by anotherman2 on 2015-05-19
Yes, that is the indicator I was referring to.

So basically there is no way to tell whether (a) there is no file meeting the specified search criteria, or (b) the search is simply still in progress w/o any results so far - am I correct?

---

### Post by GrouchyGaijin on 2015-05-19
So it would seem.
Actually when I need to search for something that ```
which
``` or ```
locate
``` can't find I use this alias which I have in my .bash_aliases file

```
alias myfind='read -p "Searching for: " search_string; find / -name "$search_string" 2>/dev/null'
```

I type ```
myfind
``` in the terminal and when it says ```
searching for:
``` I type ```
*<thing I want to find>*
```

---

