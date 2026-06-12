---
title: "[MVC/Zend Framework] Partials, View Helpers, Action Helpers - please explain"
date: 2011-02-21
forum: Programming Talk
---

### Post by steve_c on 2011-02-21
I'm a long-time PHP developer who only recently has gotten into MVC patterning and the Zend Framework. I'm loving it so far but I have a few questions because I want to make sure I'm doing things the "right" way. Sorry if a bunch of this is boring or noob-ish questions. I only saw one similar question on a search of the forum but it has no answer yet, and similar questions on StackOverflow still left me confused.

What are the differences between partials, view helpers, and action helpers? I know that view helpers maintain state across the application while partials are stateless but I'm trying to figure out why I would prefer one or the other in practice. At first I thought action helpers was another name for view helpers, but in some of my recent readings I'm getting the impression they are two different things.

Also, do any of these three apply to anything to do with Zend_Tool? I've been using that as per the QuickStart to create my projects but some of the folders suggested in the Zendcasts tutorials I've watched aren't automatically created by it so I don't know if there's a different way of doing things or what.

I'm using Zend_Framework 1.11.2.

Perhaps if it helps as an example, I'm currently building a new website. I now have a Zend_Navigation menu (thanks to the ZendCasts tutorial--those tutorials are great) on every page. I also have on the main page separate sections for "News Items" and "Sponsors" that I feel should probably be abstracted out (the Sponsors div will probably stay solely on the main page, but the "News Items" div might become a persistent feature on the rest of the site, and might perhaps change form (for instance on the main page I have it in a side bar, and I might change it into a ticker-style list on other pages). Is it more right to do one or both of these tasks with partials, view helpers, or action helpers?

If that doesn't work then I'm all ears if someone has other examples that will help me distinguish between when and why I would want to use one of these over the others.

Thanks for any help!

---

