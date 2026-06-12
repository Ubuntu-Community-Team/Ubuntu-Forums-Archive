---
title: "script with curl to search"
date: 2008-12-29
forum: Programming Talk
---

### Post by davidtuti on 2008-12-29
Hi,
I would like to aumatice a script to from command line that cand send a string to the web page ([http://www.blogdecine.com/](http://www.blogdecine.com/)) where is the field "IR>>"  of the web page and get the search resaults. I have the html code with curl of the webpage but I don't know how to follow the link to see the next code.

Many thanks and sorry for my english!!

---

### Post by catchmeifyoutry on 2008-12-29
Hello, if you want to get the search result page, you could use the same URL your browser generates when you enter a search term in the form, and only replace the search term to the one you actually want.
For example when I enter the search term "test me", it generates the following URL:
```

http://www.blogdecine.com/busqueda?q=test+me&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091

```
You can see that my query appears as the 'q' argument in the URL (that is after the 'q=' and before the first '&' part. Also note that the term is appropriately escaped such that spaces are replaced by + signs (other special characters like & would be encoded too). So to get the result for some other query, change the value of the 'q' argument.
Example to search for "nicole kidman":
```

http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091

```

Now i don't now about many of the other arguments such as 'client' or 'channel', but if my suggested methods works, keep them there, otherwise try to remove them from the URL.

---

### Post by davidtuti on 2008-12-29
Many thanks!

But when I do:

curl -L -s [http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091](http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091) -o xxxx

The command doesn't end and doesn't redirect to a file xxxx the html code?

Any help?

Many thanks.

---

### Post by catchmeifyoutry on 2008-12-29
> **davidtuti said:**
> Many thanks!

But when I do:

curl -L -s [http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091](http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091) -o xxxx

The command doesn't end and doesn't redirect to a file xxxx the html code?

Any help?

Many thanks.

That's because in your command line shell the & sign of the URL are interpreted as shell syntax to start a process in the background. The line you gave will try to start several processes (with strange non-existent names) in the background. Put quotes around the URL to explain to the shell that it is one literal string, like so:
```

curl -L -s "http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091" -o xxxx

```

Good luck!

---

### Post by davidtuti on 2008-12-29
> **catchmeifyoutry said:**
> That's because in your command line shell the & sign of the URL are interpreted as shell syntax to start a process in the background. The line you gave will try to start several processes (with strange non-existent names) in the background. Put quotes around the URL to explain to the shell that it is one literal string, like so:
```

curl -L -s "http://www.blogdecine.com/busqueda?q=nicole+kidman&domains=http%3A%2F%2Fwww.blogdecine.com&sitesearch=http%3A%2F%2Fwww.blogdecine.com&client=pub-9977500652563564&forid=1&channel=6370492291&ie=UTF-8&oe=UTF-8&cof=GALT%3A%23008000%3BGL%3A1%3BDIV%3A%23336699%3BVLC%3A663399%3BAH%3Acenter%3BBGC%3AFFFFFF%3BLBGC%3A336699%3BALC%3A0000FF%3BLC%3A0000FF%3BT%3A000000%3BGFNT%3A0000FF%3BGIMP%3A0000FF%3BFORID%3A11&hl=es&x=0&y=0#1091" -o xxxx

```

Good luck!

Oh yea! You have reason 

It gives me the html code but it doesn't gives me all. I would like the urls of the search results but the html code that it gives me doesn't show nothing about that.

Many thanks!

---

