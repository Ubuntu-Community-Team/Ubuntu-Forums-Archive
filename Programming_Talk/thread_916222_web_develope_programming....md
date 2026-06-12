---
title: "web develope programming..."
date: 2008-09-10
forum: Programming Talk
---

### Post by hockey97 on 2008-09-10
HI ok been working on my website and I am trying to make a listing.

I have a image map of the U.S.A and want when a client clicks the state to open a new page that would show the listings of the state.


Now I know how to do the above but I now also need a make a way to display all listings of that state by letting clients input date to create one item of the list. This would cause the list to be able to be long and I want to have a point that if the list is longer than a certain number of items I want to make a auto generator that would create a new page or create a link where it would seem like it's a new page but when clicked on the link it would take out what was displayed and show whatever that overflowed the limit.

It's kinda hard to explain but examples can be found on ebay, and board forms like this.

If you notice here on this board forum at the top or bottom you see numbers like 1,2,3,4,5 ect they are links when clicked it takes you to another page which shows more posts.

I am making a table with listings of items so as the list grows at a certain point I want to autogenerate a new link that would display the other stuff.


so for example lets say I have 100 posts and I can fit on one page 20 posts this would mean that I need 5 pages to fully display all the info.

I was thinking to do this with php but also have thoughts about if I can use javascript.

I would like to figure out what most do for coding such a thing,

---

### Post by mssever on 2008-09-10
AFAIK, most frameworks include some way to do this automatically. If yours doesn't, then check whether you have more than $limit rows. If so, add an appropriate LIMIT clause to your SQL query.

Unless you used an AJAX-style query (and unless that made sense for your situation), then I don't recommend trying to use Javascript as it will unnecessarily increase your page's size.

---

### Post by henchman on 2008-09-11
framework, boo! :)

well, just define a variable like $start with default value of 0. if $_GET['start'] exists, then set $start to $_GET['start']. now do your query like ```
SELECT foo FROM bar LIMIT $start, 10;
```([LIMIT manual]("http://dev.mysql.com/doc/refman/5.0/en/select.html#id4797680"))

This will give you ten elements. Now you just have to create your links.... with a 

```
SELECT Count(*) FROM bar
```

you can find out how many records you have, now you can find out the number of pages with

```
$noOfPages = ceil( $noOfRecords / 10 );
```

just print your links to the pages in a for loop now! job done :>

it may make sense to have an extra variable like $entriesPerPage, so when you want to change it, you don't have to change your whole code... You may also want to sanitize the $_GET['start'] value to make sure it's an integer and its not 93382872323 when you have 3 pages *g* :popcorn:

hf

---

### Post by hockey97 on 2008-09-11
ok thanks for the help but can you clarify $_GET['start'].

I assume it's the data from the form. 

Also about this LIMIT $start, 10;... I know that the $_GET stuff will be in $start but I don't get the limit start ,10  would that just mean LIMIT the var of start and also 10 

I don't get why we need the $_GET['start'] part. Also would 10 be the limit??

I just want to but a limit on what's displayed on one page and if there is more then allowed on one page then either generate another html file or make links that when clicked it would take what's been displayed and show the ones that couldn't be on page one because it displayed to the max so for example if I  have 30 posts and want only the max 10 on each page then when the posts go over 10 it would generate a link saying page 2 or somthing in that order where the user can just click that link or button and it would display the 11nth post.

I am going to work on it but would like you to clearifiy about the $_GET['start'] and the LIMIT PART.

I understood the rest. I also assume that the $_GET var will be  a integer.

thanks for the help.

---

