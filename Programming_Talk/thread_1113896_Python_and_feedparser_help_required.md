---
title: "Python and feedparser help required"
date: 2009-04-02
forum: Programming Talk
---

### Post by twistadias on 2009-04-02
Im using [feedparser]("http://www.feedparser.org/docs/index.html") from  to get this [feed]("http://www.aucklanddailyphoto.com/feed/")

So I get the title, description and everything. So far so good. But how do I request more posts. There are only 5 posts when I get the feed.

I dont really know what to search for basically. I tried google, but im still kinda lost.

If someone could guide me in the right direction, I'd be thankful

---

### Post by twistadias on 2009-04-02
bump

---

### Post by G|N| on 2009-04-03
The feed only contains 5 items....so you should use another feed or parse the actual webpage for newsitems.

---

### Post by twistadias on 2009-04-03
This is for a university project.

How do rss readers get the older posts?
I imagine that there would be a request function that would get the previous five posts.

---

### Post by G|N| on 2009-04-03
> **twistadias said:**
> This is for a university project.

How do rss readers get the older posts?
I imagine that there would be a request function that would get the previous five posts.

There is no request to get older posts...
If the rss only provides 5 items, you can only get those 5 items.

A different (more difficult) approuch would be to parse [http://www.aucklanddailyphoto.com/](http://www.aucklanddailyphoto.com/) and after [http://www.aucklanddailyphoto.com/page/2/](http://www.aucklanddailyphoto.com/page/2/) and so on, to get older posts...

You could use BeautifulSoup to parse the webpage, but there is no garantue that it will always work (maybe the site changes it layout and your parsing structure will be broken)

---

### Post by twistadias on 2009-04-03
> **G|N| said:**
> There is no request to get older posts...
If the rss only provides 5 items, you can only get those 5 items.

A different (more difficult) approuch would be to parse [http://www.aucklanddailyphoto.com/](http://www.aucklanddailyphoto.com/) and after [http://www.aucklanddailyphoto.com/page/2/](http://www.aucklanddailyphoto.com/page/2/) and so on, to get older posts...

You could use BeautifulSoup to parse the webpage, but there is no garantue that it will always work (maybe the site changes it layout and your parsing structure will be broken)

Thanks, thats a really good idea. Pretty small chance that the website would change their design on the day of the submission lol.

I guess I could use feedparser for the first five posts, but then my database would be pretty small. And use beautiful soup for atleast 10 more posts.

or I could try finding another rss feed with more posts :)

---

### Post by G|N| on 2009-04-03
> **twistadias said:**
> And use beautiful soup for atleast 10 more posts.

Why not get as much posts as possible? the page address is very simple and with a counter you can set the page automatically...
```

i = 2

while i < 20:
   get_page("http://www.aucklanddailyphoto.com/page/" + str(i))
   i += 1


```

Of course this code does not work, but you get the idea :)

---

### Post by twistadias on 2009-04-04
> **G|N| said:**
> Why not get as much posts as possible? the page address is very simple and with a counter you can set the page automatically...
```

i = 2

while i < 20:
   get_page("http://www.aucklanddailyphoto.com/page/" + str(i))
   i += 1


```

Of course this code does not work, but you get the idea :)

So ive now setup the whole thing using BeautifulSoup. 
I did a for loop to get a few pages, but the whole thing crashes even for getting 2 or more pages.
The loop works for getting 1 page.

However if they are written like this:

get_page("http://www.aucklanddailyphoto.com/page/1")
get_page("http://www.aucklanddailyphoto.com/page/2")
get_page("http://www.aucklanddailyphoto.com/page/3")

It gets all the pages and takes around 10seconds

Any ides why the for loop doesnt work. Is it because of too many get requests at the same time?

---

### Post by G|N| on 2009-04-06
Could you post the actual code, or at least the error message you receive?

without using threads, it will only do one request per time so this can not be the problem...

---

