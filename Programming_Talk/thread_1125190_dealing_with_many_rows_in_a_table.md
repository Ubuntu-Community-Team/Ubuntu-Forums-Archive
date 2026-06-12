---
title: "dealing with many rows in a table"
date: 2009-04-14
forum: Programming Talk
---

### Post by Xenobug on 2009-04-14
ok, here's something that's been bothering me for months: assume you have a huge mysql table, say 7,5 million rows with firstname, name and all that and you now have to display it on a website where the user is able to sort the list via a dropdown, browse through all pages and so forth - how would you go about it?

the simplest solution wold be to just use an oracle database. but the cost is prohibitive for the client, so I need to use mysql. sorting the table by more than one index takes ages as mysql resorts to filesort in this case. doing something like "limit 6999980,10" makes it even worse.

so my solution was to cache the results and prepare finished pages for all sort variants. now I have nearly 2 million text files on the server that hold the prepared list in all variants. the problem with that is that it takes almost two hours to generate these files so the data is always a bit outdated.

is there any smart solution for that short of omitting results?

---

### Post by dwhitney67 on 2009-04-14
There is no practical reason to display 7.5 million, or even 10,000, names at any particular time on a web page.  Break apart the data space, and display only a subset.  Provide the user for a search box and also the ability to navigate to the next "page" of names.  It is possible that there are multiple pages for the names that begin with "A", and similarly for those with a "B", "C", and so forth.

The choice if MySQL is appropriate if cost is a factor; PostGres (or however it is spelt) is another alternative.  Personally I like MySQL.

---

### Post by Xenobug on 2009-04-14
Nothing wrong with mysql, I tend to prefer it as well, being open source and all. Postgre is definitely slower than mysql.

There are many things you can complain about in oracle's implementation of the sql standard, but it sure is a damn fast database. if not for their insane license fees, I'd probably switch to oracle as my primary db.

That being said, omitting results is not an option. I know most websites (even google) will let you specify a search term and then only display 30 pages or so of results.

That's not possible here, we definitely need the entire list. The rows from the table are divided into several categories, with each categories containing several 100k results. The results returned make out the content of the site and the site lives of people browsing through endless pages of results, so we can't just leave some out. 

Adding further categories doesn't work because there are just no other subcategories we could come up with that would make any sense.

Like I said, my current solution are cached lists, but obviously, this is by far not as elegant as if the results would be read directly from the database because of the delay until changes become visible. Not to mention the "ugliness" of having millions of files sitting on the server just for displaying the website.

I guess I could come up with a very in-depth solution that would somehow cache the cache (eek!) so that additions and updates become visible at once, but I am wondering whether there is a better solution. Perhaps something so obvious that I missed it.

---

### Post by simeon87 on 2009-04-14
> **Xenobug said:**
> That's not possible here, we definitely need the entire list. The rows from the table are divided into several categories, with each categories containing several 100k results. The results returned make out the content of the site and the site lives of people browsing through endless pages of results, so we can't just leave some out.

But nobody said you should ignore rows, you should only serve the content that the users will actually use. It's very well possible to give the user the ability to browse millions of rows, as long as you only serve a portion of them at a time. If you use millions of rows to calculate certain values, perhaps you should consider creating another table that holds these values (that are also updated when the data changes).

---

### Post by Arndt on 2009-04-14
> **Xenobug said:**
> ok, here's something that's been bothering me for months: assume you have a huge mysql table, say 7,5 million rows with firstname, name and all that and you now have to display it on a website where the user is able to sort the list via a dropdown, browse through all pages and so forth - how would you go about it?

the simplest solution wold be to just use an oracle database. but the cost is prohibitive for the client, so I need to use mysql. sorting the table by more than one index takes ages as mysql resorts to filesort in this case. doing something like "limit 6999980,10" makes it even worse.

so my solution was to cache the results and prepare finished pages for all sort variants. now I have nearly 2 million text files on the server that hold the prepared list in all variants. the problem with that is that it takes almost two hours to generate these files so the data is always a bit outdated.

is there any smart solution for that short of omitting results?

How about using the OFFSET and LIMIT constructs in SQL? First ask for 100 rows, then for the next 100 if the user wants to, etc.

If the user wants to sort, either get just the column being sorted, or include the ORDER BY in the request to SQL.

Some of this may not make sense, this is not something I have actually done.

---

### Post by Xenobug on 2009-04-14
> But nobody said you should ignore rows, you should only serve the content that the users will actually use. It's very well possible to give the user the ability to browse millions of rows, as long as you only serve a portion of them at a time. If you use millions of rows to calculate certain values, perhaps you should consider creating another table that holds these values (that are also updated when the data changes).

apparently I was a bit unclear. of course I am NOT generating files that have html tables with 7 million entries. I have like 400k files per sort option, each containing a html table with 20 results.

> How about using the OFFSET and LIMIT constructs in SQL? First ask for 100 rows, then for the next 100 if the user wants to, etc.

If the user wants to sort, either get just the column being sorted, or include the ORDER BY in the request to SQL.

Some of this may not make sense, this is not something I have actually done.

limit is the obvious choice when intending to return certain rows, however, limit has massive performance issues when you do something like "limit 1200000,20" (a flaw that oracle doesn't have) - so limit is of no use if you deal with many rows.

just selecting a single column (i.e. the user_id) and then getting the rest of this user's data by the ids returned is something I tried, but it's useless because in order to retrieve the ids, mysql nevertheless needs to do a complete table sort.

so, basically, thanks, but been there, done that. :)

---

### Post by Arndt on 2009-04-14
> **Xenobug said:**
> 

limit is the obvious choice when intending to return certain rows, however, limit has massive performance issues when you do something like "limit 1200000,20" (a flaw that oracle doesn't have) - so limit is of no use if you deal with many rows.



So that's a flaw in mysql specifically, but not in Oracle, or perhaps other SQL databases? That's useful to know.

---

### Post by pmasiar on 2009-04-17
> **Xenobug said:**
> is there any smart solution for that short of omitting results?

Using index and filter the results by some criteria? User cannot possibly be interested in seeing all 7M orf rows at once?

---

### Post by s.fox on 2009-04-17
Hi,

I also think that nobody is going to want to see that sheer amount of data on screen.  As others have said have the information displayed over several pages of results, in a similar fashion to how the threads in this forum are listed.

-Ash R

---

### Post by ajackson on 2009-04-17
I think you need to go back and have another look at your design (both database and "application").

No one would need to look at all 7M in one go, I don't know how long it takes a person to check/read a line but if they needed to check/read every line they would be there years I would imagine.

---

### Post by lisati on 2009-04-17
7M? Too much to view all in one go, and potentially uses a LOT of bandwidth. As has been suggested, it'll probably be a good idea to find some way of filtering or otherwise limiting the content before sending it out via a web page.

---

