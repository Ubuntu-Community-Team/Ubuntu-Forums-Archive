---
title: "Automatically update navigation buttons?"
date: 2010-07-18
forum: Programming Talk
---

### Post by TyD on 2010-07-18
I'm just getting into the realm of web development and I have started to create a blog from scratch.  I put 4 navigation buttons on the page which link to the first, previous, next, and last posts.  Everything works great, except I realized that every time I create a new post, I'll have to go through each page I've created and update the "last" link to the "new" page (and of course, the "next" link on the penultimate page).  Is there an easy way to do this?  I know CSS and HTML and some PHP, but if there's a better way to do this I'm quite willing to learn something new. =)

---

### Post by Tony Flury on 2010-07-19
instead of your last and next links pointing direct to a html page, they should post to a PHP (or similar file) which can work out what last and next actually mean and serve the right page. 

To make this easier you would either store each of your blog posts in an database (and use a PHP file to fetch and display them), or at least store an index of pages so that your "next" and "last" scripts know how to find the relevant pages.

---

### Post by soltanis on 2010-07-19
So to break that down even further, what you need is a procedural way of storing entries and retrieving them. The easiest way to think of it is a list or array which you can access by numerical indices.

For example, let's say that you programmed your software to add blog entries using a monotonically increasing index number. The last blog entry is then the highest number, and the one that comes before that is the next highest, and et cetera.

If you store your blog entries on the filesystem as HTML snippets then you might have:

```

entry0 entry1 entry2 entry3

```

To find the highest entry, you would list the storage directory contents and find the highest integer after "entry". To display a page, your (really simple) PHP script may look like:

[php]
<?php

$id = $HTTP_GET_VARS['entry'];
if (isset(id)) {
  $entry = fopen('entry' + $id, "r");
  while (!feof($entry)) {
    echo fgets($file);
  }
  fclose($entry);
}
?>
[/php]

This takes a number as the "entry" parameter in a GET request, opens the corresponding blog entry, and writes it out. You can easily modify this script to add the buttons you're talking about.

---

### Post by philippeweb on 2010-07-19
thanks for sharing the code its help me also in creating on  my blog

---

### Post by TyD on 2010-07-19
Much appreciated! :D

So if I understand you right, in order to navigate to the newest page I need to tell my PHP script to search a directory for the page with the highest number appended to it and echo it within an anchor?  Or does the script you wrote open the page itself?

---

