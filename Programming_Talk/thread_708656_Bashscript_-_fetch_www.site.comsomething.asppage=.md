---
title: "Bashscript - fetch www.site.com/something.asp?page=?"
date: 2008-02-26
forum: Programming Talk
---

### Post by daller on 2008-02-26
Hi there,

I have to fetch a lot of products for a website.

Basically I have to fetch these pages (and pictures on these pages!):

[www.site.com/something.asp?page=?](www.site.com/something.asp?page=?)

...where the last "?" is all numbers between 1 and 100000.

How do I accomplish this?

---

### Post by yabbadabbadont on 2008-02-26
[http://www.httrack.com/](http://www.httrack.com/)

---

### Post by Martin Witte on 2008-02-26
I don't know if this is possible in a shell script, in Python you can open url's with urllib (see [http://docs.python.org/lib/node577.html](http://docs.python.org/lib/node577.html) for some examples).

---

### Post by ghostdog74 on 2008-02-26
> **daller said:**
> Hi there,

I have to fetch a lot of products for a website.

Basically I have to fetch these pages (and pictures on these pages!):

[www.site.com/something.asp?page=?](www.site.com/something.asp?page=?)

...where the last "?" is all numbers between 1 and 100000.

How do I accomplish this?
first, use wget to get one page. if it works, you can just use a for loop 
```

for number in `seq 100000`
do
 wget http:........$number
done 

```

---

### Post by nhandler on 2008-02-26
One thing to keep in mind is that if you are trying to set up an offline version of a site, the wget method will still be linking to the online version. httrack has options to modify the links and images to reference the offline copy instead.

---

### Post by daller on 2008-02-27
> **ghostdog74 said:**
> first, use wget to get one page. if it works, you can just use a for loop 
```

for number in `seq 100000`
do
 wget http:........$number
done 

```

I only need the content, and no external links...

...I also need the images, though! - How do i setup wget to download the images on the pages, without following other links (wget -r, works, but it crawls the whole site :))

...and can I slow it down a little? - It seems to kill the server after some 1000 wget's!

There's also a lot of numbers that are not valid (displays almost empty template) - How do I insert an IF-statement, that deletes the downloaded file if it doesn't have the string "DKK" in it. (I know this string is in the valid ones, and not in the invalid!) 

Thank you for your help!

---

### Post by Mr. C. on 2008-02-27
Use either --wait *seconds* to wait between retrievals, or --random-wait

```
--wait *seconds*
--random-wait
```

if you are doing a single wget.  If you are looping over multiple wgets, place a sleep 1 call after your wget.

The --page-requisites option will pick up images required for pages to render (along with other stuff).  Use it without recursion set.  Since you know the name of all the pages, this is likely what you want.

You can also specify the types of files you want to accept:

```
--accept *acclist*
```

where *acclist* is a comma-separated list of file suffixes (eg: .jpg,.gif)

There are plenty of options available to wget - the man page takes some time to review, but worth it:

```
man wget
```

MrC

---

### Post by Mr. C. on 2008-02-27
> **daller said:**
> There's also a lot of numbers that are not valid (displays almost empty template) - How do I insert an IF-statement, that deletes the downloaded file if it doesn't have the string "DKK" in it. (I know this string is in the valid ones, and not in the invalid!) 

Do this part at the end, outside the loop:

```
$ find . -type f | xargs grep -v -l DKK | xargs rm
```

which finds all files from the current directory (be sure you're in the top of the download directory first), send that list to grep which prints out only the name of the files that do not contain DKK, and passes that list to rm.

MrC

---

### Post by tg3793 on 2010-12-08
> **nhandler said:**
> One thing to keep in mind is that if you are trying to set up an offline version of a site, the wget method will still be linking to the online version. httrack has options to modify the links and images to reference the offline copy instead.

This is an old thread I know. But since I'm looking at it perhaps another newbie that would not know better might be looking at it as well. So for the edification of all I submit the following reply.

You can use the **--convert-links** option for wget which enables wget to, after downloading all of the pages, to rename the links within the downloaded pages to point at your new local copy.

Here is a [[COLOR="Blue"]**great tutorial**[/COLOR]]("http://dalelane.co.uk/blog/?p=233") on it. Even though the tutorial applies to a wiki, the same principles apply for any offline copy of a website.

---

### Post by ssam on 2010-12-08
also curl (similar to wget) can do this.

---

