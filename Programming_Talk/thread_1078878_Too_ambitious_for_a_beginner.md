---
title: "Too ambitious for a beginner?"
date: 2009-02-23
forum: Programming Talk
---

### Post by blairm on 2009-02-23
Hi,

Been toying with the idea of learning Python for a while, and had an idea for a macro to help me learn a bit.
Our newspaper publishes a list of shipping movements every day; at the moment, someone goes to the port website, prints off the shipping movements, then types them up in the newspaper style.Takes them about 15 minutes each day.
Wondering how feasible it would be to write a macro using python to work through the site's html to extract the desired information and format it in newspaper style.
If it's feasible, would I be best to use something like Beautiful Soup? 
In no rush to complete the job - IT isn't my work, just have an interest in computers etc.
Any thought would be gratefully recived!

Blair

---

### Post by slavik on 2009-02-23
using libcurl, someone comfortable and familiar with Python would need a day or two to do this. You will probably need 2 weeks to hack this together, but you will not really understand what is going on. But defintely go for it.

---

### Post by Wybiral on 2009-02-23
> **slavik said:**
> using libcurl, someone comfortable and familiar with Python would need a day or two to do this. You will probably need 2 weeks to hack this together, but you will not really understand what is going on. But defintely go for it.

Why use libcurl in Python? I'd use urllib, and if you need to parse out some data from the HTML easily, BeautifulSoup is awesome at handling HTML. Then you just need to write some function to transform the data into the format you need.

---

### Post by protodog on 2009-02-23
Yeah I think it's easy enough to do. I did something similar when I was learning Python and I also happened to be using urllib.

My recommendations would be:
[LIST=1]
[*]Learn the basic language constructs
[*]Now forget about programming for a moment and write down each step of what is done in those 15 minutes spent copying.
[*]For each step that you've written down, think about how you would tell the computer to do it. If you don't know how, find out.
[*]You may discover that you have to further divide those steps to make your tasks easier as you go along. This is okay.
[*]Another good thing to do is to study similar Python scripts on the web. This will also boost your programming muscles.
[/LIST]

By the way, I highly recommend picking up a copy of Learning Python if you are serious about learning programming. It's a good way to start.

---

### Post by DocForbin on 2009-02-24
If you've got some basic programming chops, not too ambitious at all.

---

### Post by wmcbrine on 2009-02-24
It definitely sounds like a task that needs to be automated. Entirely feasible. You might even want to get paid for it. :)

---

### Post by Scubdup on 2009-02-24
Slightly out of my depth, but for a easier solution (or part thereof) you could experiment with the [iMacros]("https://addons.mozilla.org/en-US/firefox/addon/3863") addon for Firefox...

---

### Post by ajackson on 2009-02-24
One thing to check is whether the data is available via another format (i.e. RSS feed or something similar), that would save parsing through the unneeded HTML tags but this type of project is doable for a beginner and a good way of learning a language.

---

### Post by blairm on 2009-03-01
Thanks for your advice everyone,

Have pretty much no programming experience (just a few macros) but I've been amazed so far how easy Python is to pick up.
Given my other commitments think this will take me a good month, but there's no rush - we've been doing this manually for the past 140 years, so doing it manually for another few weeks won't hurt anyone.

Cheers,

Blair

---

### Post by Can+~ on 2009-03-01
One of my first things I did with python, was a html parser that connected to my University's site, downloaded new material I didn't have and stored it in respective folders according to date and class.

It wasn't pretty code, but it did what I wanted and I learned a lot from it. I say, go for it.

---

### Post by days_of_ruin on 2009-03-01
> **blairm said:**
> Thanks for your advice everyone,

Have pretty much no programming experience (just a few macros) but I've been amazed so far how easy Python is to pick up.
Given my other commitments think this will take me a good month, but there's no rush - we've been doing this manually for the past 140 years, so doing it manually for another few weeks won't hurt anyone.

Cheers,

Blair

Now thats an old website lol.

---

