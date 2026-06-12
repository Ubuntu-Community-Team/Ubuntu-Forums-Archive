---
title: "Watching youtube vids without flash player"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by aef54 on 2012-09-06
I use the live Ubuntu disc a lot. Doing that, I'd like to have YouTube play me some background music.

When I go to YouTube, I can't watch any vids because it says it's missing plugins. (and I can't install those on the live disc). However, when I see a youtube video embedded on another website, it actually is possible for me to watch it! It's kinda weird and really interesting. 

Do you maybe know a way that I can also watch youtube vids on youtube itself without the plugin?

---

### Post by aef54 on 2012-09-06
Ok I think I fixed it.

This only works with youtube videos that you can embed:

you change the URL from:

```
http://www.youtube.com/watch?v=*videoID*
```to
```
http://www.youtube.com/embed/*videoID*?html5=1

```and then you can watch the vid without flash player using the Ubuntu live disk. :guitar:

---

### Post by aef54 on 2012-09-06
*please delete*

---

### Post by FOSSteror on 2013-05-09
> **aef54 said:**
> Ok I think I fixed it.

This only works with youtube videos that you can embed:

you change the URL from:

```
http://www.youtube.com/watch?v=*videoID*
```to
```
http://www.youtube.com/embed/*videoID*?html5=1

```and then you can watch the vid without flash player using the Ubuntu live disk. :guitar:

Thanks, that worked -- even without '?html5=1'

---

