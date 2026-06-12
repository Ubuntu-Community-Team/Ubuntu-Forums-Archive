---
title: "Remembering things"
date: 2007-02-11
forum: Programming Talk
---

### Post by Ubuntuud on 2007-02-11
Hi,
I have a website, fairly simple...
On the website there is a sidebar...
The sidebar contains separate 'parts', hide able with a button.

The problem is, the website forgets that a 'part' was hidden when the page is reloaded, or when the user goes to another page.
Pretty annoying.

So, my question is, what is the smartest way of making the website remember what 'parts' should be hidden.

My first thought were cookies, but those must be set before loading the page.
PHP sessions are possible, with ajax, but seems quite an overkill to me...
Any clues?

Thanks in advance!
pieter.

---

### Post by Tomosaur on 2007-02-11
Cookies would indeed be the 'easiest way' to do this. Alternatively, you may want to rethink your design. Try using i-frames to represent your side bar and your main content area. That way, the user need never reload the side bar, and you can just load content into the main area. This will allow you to use whatever method you're currently using (I assume JS?) to remain.

---

### Post by Ubuntuud on 2007-02-11
Is an option...
But I can't stand frames...

I think I'll use ajax with a php-cookie-setter-file (still need to find out if that is even possible), that would be more handy, since I would like the sidebar to remember along multiple sessions.

When I have time I will also try frames, but the current design isn't very suited for that, since some pages have got a sidebar, and some don't.*

* If that seems silly, note that the links are _not_ on the sidebar. The sidebar contains news and stuff.

---

### Post by LotsOfPhil on 2007-02-12
Couldn't you just have the page refresh when they change the look? Then you could use a cookie.

---

### Post by Ubuntuud on 2007-02-12
That seems so anoying to me...

BTW. Do javascript cookies behave differently from php ones? Meaning that you can set one without refreshing?

Right now I can't test anything because I'm having some trouble with my apache server (and I need to start learning some Latin).

I just put the website online btw.
I know it isn't very good. But it's my first serious website. It's in Dutch, for a 'students-board' of a high school...

llr.hetsoet.nl

Is it possible to put the sidebar in an iframe?
Maybe it is the best option...

---

### Post by Mirrorball on 2007-02-12
You can set cookies with Javascript at any time. Here are some instructions:
[http://www.quirksmode.org/js/cookies.html](http://www.quirksmode.org/js/cookies.html)
Please, no frames! I think cookies would be your best option in this case.

---

### Post by Ubuntuud on 2007-02-13
That's handy :)

Thanks!

---

