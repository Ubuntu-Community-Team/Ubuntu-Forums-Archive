---
title: "how do you search for two names in one label using the search app?"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by s1baker on 2012-07-21
hi,

How do you search for a label that contains two different texts in one label?

I want to use the search app ( I think it was wrote for Gnome, I'm using xfce 12.04, but it works in xfce ), I don't want to use the terminal with grep, the search app is quicker.

Other words, if I want to find a label that contains "a", I can put "a" ( without the quotes ) into the "Name contains" field box, and it works, likewise I can put "b" into the field box and it works, but what do I put into the field box to search for a label that contains both "a" and "b" ?

~Also, how do you clear the list of searched for items? 

Thanks

---

### Post by Vaphell on 2012-07-21
I don't know the answer to your question, but i can elaborate on the terminal way of doing that:
I think you meant *find* not *grep*, *grep* mainly is used with file contents, *find* with the file properties. 

Most likely the search app uses *locate* as its backend. *locate* searches in database that is refreshed daily and thanks to that results are instantaneous.
```
locate 'phrase'
```
locate also supports regexes
```
locate -r 'a.*b'
```
additional -b if only name is to be matched (without path)
*locate --help* for more info.
if the files you are interested in are not indexed yet (are newer than the last database update), you can force update with
```
sudo updatedb
``` and try again

---

### Post by s1baker on 2012-07-27
bump

---

### Post by Bufeu on 2012-07-27
Does this help? [http://forums.linuxmint.com/viewtopic.php?f=110&t=93354](http://forums.linuxmint.com/viewtopic.php?f=110&t=93354)

---

### Post by s1baker on 2012-07-27
There is a "add" option on the gnome-search-tool whereby you can search
for more than one text inside of files, what I am wondering about if there is something like this for file names.

For example a name field might be "a b c d", or "abcd".
It would be neat if one could search for a name that contained "a" and
"d".

---

### Post by JKyleOKC on 2012-07-27
Try "a*d" (without the quotes) as the string to search for. That would also locate "ad" but not "abcd.txt" or "dxyza" but making it "*a*d*" might work for "abcd.txt" or even "abracadabra"...

This is with the "find" method, not "locate" which are the only two methods available on my system...

---

### Post by s1baker on 2012-07-27
```
file name example =  "a b c d"
```


If I wanted to find the file name that contained "a" and "d" I had success by using *a* *d* in the search field box, but *d* *a* did not work.

Apparently it searches until it finds the first hit and then searches the rest of the field for the second argument ( instead of starting over at the beginning of the field )

---

### Post by cmcanulty on 2012-07-27
post # 5 how do you access that add option, I don't see anything in synaptic

---

### Post by s1baker on 2012-07-28
@ cmcanulty



it's not in synaptic. 

The "add" option mentioned was referring to a feature in the search program "gnome-search-tool".

In "gnome-search-tool", there is a "select more options" field.
You can click on this and see more search criteria to add to your search.

---

### Post by cmcanulty on 2012-07-28
OK thanks, I never knew that

---

