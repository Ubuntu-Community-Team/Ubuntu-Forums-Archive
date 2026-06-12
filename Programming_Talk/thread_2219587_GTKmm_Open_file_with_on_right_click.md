---
title: "GTKmm: Open file with on right click?"
date: 2014-04-24
forum: Programming Talk
---

### Post by fallenshadow on 2014-04-24
Hi all,

So I am here pondering how on earth this kinda functionality works. I am using GTKmm but this is a broad question. If anyone knows how this feature is implemented in general I would like some information.

Searching the web gives random results and I have tried many variations on the search terms.

I guess first step is register filetypes to open with your app? and then what?

When I click on "Open with myapp" what happens in terms of code?

---

### Post by ofnuts on 2014-04-25
You app is just called with the filename as a parameter. It even works for mere scripts.

---

### Post by fallenshadow on 2014-04-27
I see, then your app must check for a param at startup and if exists run open function.

I thought it would be something like this for sure.

---

