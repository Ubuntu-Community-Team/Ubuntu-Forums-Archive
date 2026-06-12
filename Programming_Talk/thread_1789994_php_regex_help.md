---
title: "php regex help"
date: 2011-06-24
forum: Programming Talk
---

### Post by lykwydchykyn on 2011-06-24
I'm trying to add a feature to one of my PHP applications, but I'm not sure how to approach it.

I have a chunk of text like this:

```

response to some message that someone wrote

so and so wrote on 1/1/1900 at 12:00
>This is the original message
>Which you will probably respond to
>blah blah blah


```

What I'd like to do is get all the lines that begin with ">", remove the ">", and wrap the lot of them in html tags so that it looks like this:
```

response to some message that someone wrote

so and so wrote on 1/1/1900 at 12:00
<div id=quoted>
This is the original message
Which you will probably respond to
blah blah blah
</div>

```

I suppose I could brute-force this, but is there some snazzy regex way of doing it?

---

