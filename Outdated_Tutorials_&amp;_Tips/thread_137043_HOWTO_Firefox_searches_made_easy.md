---
title: "HOWTO: Firefox searches made easy"
date: 2006-02-27
forum: Outdated Tutorials &amp; Tips
---

### Post by zi99y on 2006-02-27
(MOD - I already sent this a couple of days ago and it must have slipped thru the cracks - please please publish it or let me know why not? thanks)

A mate of mine just turned me on to some useful ways to use firefox to search sites. Basically you can search anything just by typing a command into the address bar - there are some preset ones that you can try:

type:

```
imdb shaun of the dead
```

lo and behold, IMDB will open on the page for Shaun of the Dead (my favourite film btw)

```
google ubuntu
```

this will produce a google search on ubuntu.

Now, if you want to make google search a site of your choice, you can do something clever using the bookmarks. Lets take the [www.torrentz.com](www.torrentz.com) search engine. Go to the site and enter a search, then bookmark the result, like so:

```
http://www.torrentz.com/search_ubuntu
```

Now edit the bookmark and replace the search term (ubuntu in this case) with %s and add a keyword, we will use torrentz to demonstrate. The Bookmark should look something like this:

[B]
Name: torrentz
Location: [http://www.torrentz.com/search_%s](http://www.torrentz.com/search_%s)
Keyword: torrentz
[/B]

Ok, that's it - now go to the address bar and type torrentz followed by a search term, as so:

```
torrentz debian
```

Bob's your uncle, Fanny's your Aunt - a search is bought up for debian! 

Using this method for searches with multiple terms can be a little fiddly, in the torrentz example you must use - to join the search words, and other sites may work differently, to find out the symbol to use (or none at all) do a search the normal way and examine the url to find the symbol separating your entered words.

This method doesn't always work as some sites hide the actual search parameters in the url, I can't show you how to do it here, but by looking through the html source you might be able to build a url to use in this way.

To search the ubuntu forums, add the following url

```
http://ubuntuforums.org/search.php?query=%s&s=&do=process
```

And even better, to add another one to only search on title, use:

```
http://ubuntuforums.org/search.php?query=%s&s=&do=process&titleonly=1
```

And that concludes Firefox searching made easy, hope you enjoyed it.

Thanks go to [Jamie Kitson]("http://www.kitten-x.com") as the originator of this info. \\:D/

---

### Post by orangedoor on 2006-02-28
Or...

1) Right click in the input box for a search and select "Add a keyword for this Search..."
2) Give the bookmark a name and a "Keyword" (what will you type in the address bar before the search terms.
3) Pat yourself on back.

---

