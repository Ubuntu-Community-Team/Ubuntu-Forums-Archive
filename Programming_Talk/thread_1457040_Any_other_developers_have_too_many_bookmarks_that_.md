---
title: "Any other developers have too many bookmarks that are everexpanding?"
date: 2010-04-18
forum: Programming Talk
---

### Post by 133794m3r on 2010-04-18
I ask, because right now i have i think ~100 or so. Mainly blogs of people who write about Game Design, AI, Web Design, PHP tricks, a few web comics(not related to gaming obviously), and any other site i find interesting and related to making games/sites/AI.

I think i may have a problem, as this list just keeps growing larger and larger and i think it may get to a point where my browser won't even start anymore due to the extremely long load time from the bookmarks. So, i ask of you, does anyone else out there have seemingly too many bookmarks related to their chosen interests?

---

### Post by ad_267 on 2010-04-18
Yeah I bookmark useful stuff for future reference and end up with a huge amount of bookmarks I hardly use, but don't want to get rid of in case I ever need them.

I think maybe there should be a hierarchy of bookmarks. Some that we actually use often that appear in the Bookmarks menu and then others in some kind of archive that we can refer to every now and then if we're looking for something we found ages ago.

---

### Post by PaulM1985 on 2010-04-18
As a suggestion:

Why not create a simple webpage containing links to each of the sites that you are interested in, and bookmark that.  The bookmark then only has to point to one file on your computer.  Instead of adding a bookmark in the browser, add it to your webpage.  (This page doesn't have to be published and accessed by other people on the web, just a simple, local html file).  You could potentially set this page as your home page.

Its a little bit of messing around, but it may keep stuff tidier.

---

### Post by wmcbrine on 2010-04-18
You think 100 bookmarks is a lot? Oh, you're funny. Anyway, don't worry, the browser can hold thousands, and it doesn't affect startup time. It only gets slow once you actually click on "Bookmarks". Unless you have a whole group of them marked as your homepage (to open in tabs) or something...

But it sounds like your real problem is keeping track of everything you want to read. This is why I started using RSS -- in my case, specifically, Google Reader. (Yeah, that gives Google yet more data about me, but it lets me move between machines with ease, and it makes Google do the bandwidth-intensive part, saving bandwidth both for me and for the sites.) But there are lots of other solutions, including Firefox's built-in RSS support.

ad_267, you can create folders in the bookmarks.

---

### Post by 133794m3r on 2010-04-18
my thing is there's a load of sites with information on them that are well like "blogs" and such done by peopel who sound interesting. And i tend to keep them there and it's well how it is for me. And it is starting to get a bit of a pain to backup/restore them. Since i tend to backup up my bookmarks and such once a week along with my data since i've had quite a few complete computer failures, i worry about losing my bookmarks.

And most sites don't have RSS versions of themselves or else i'd just put it into some random reader. I would use google's reader but well i already dislike how much information they have on me at this exact time.

If there was another engine that'd let me do a keyword search with auto-redirecting i'd be on it right away sadly no one else seems to be able to do that so i tend to use google. And well gmail can't be beat for it's cleanness.

---

### Post by new_tolinux on 2010-04-18
For this I temporarily set up a forum. Every article (and useful comments) are copied there.
Gives me full-text search-functions, a history in case the article is deleted, etc.

Although it's just temporarily...... As I'm building my own homepage with PHP/MySQL, I planned to build something more specific to do this.

---

### Post by wmcbrine on 2010-04-18
> **133794m3r said:**
> And most sites don't have RSS versions of themselvesMaybe not, but most blogs do. Most webcomics, too (although I'm missing a couple there). The main area where I find RSS isn't helpful is forums like this one, so I just have to visit them manually.

---

### Post by bruce89 on 2010-04-18
*cough* Epiphany *cough*

---

### Post by ju2wheels on 2010-04-18
If you are using FF, compress/reindex the sqlite databases instead to get a better startup time from the browser (make sure to close FF and Thunderbird before doing this):

```

find ~ -name "*sqlite" | xargs -I xxx sqlite3 xxx vacuum
find ~ -name "*sqlite" | xargs -I xxx sqlite3 xxx reindex

```

---

### Post by 133794m3r on 2010-04-19
> **bruce89 said:**
> *cough* Epiphany *cough*

FIREFOX FOR LIFE!

on a side note, i'll try those commands in a second.

---

### Post by bruce89 on 2010-04-19
> **133794m3r said:**
> FIREFOX FOR LIFE!

That sounds suspiciously like brainwashing.

---

### Post by phrostbyte on 2010-04-19
I have all the websites worth visiting memorised in my head. :) No use for bookmarks.

---

### Post by 133794m3r on 2010-04-19
> **bruce89 said:**
> That sounds suspiciously like brainwashing.

no not really... if you find me another browser that has the extensions that firefox has, has everything where it is in my firefox, doesn't try to do weird things with hiding panels and such(looking at chrome here), AND has those extensions all working properly and without any worries.

They are Firebug, Noscript, GreaseMonkey, Adblock+, PageSpeed, Y!Slow, Nuke Anything Enhanced, Stumble Upon, Personas(no integrated into firefox so i guess it's not an extension anymore), DownThemAll!, the Auto-redirect thing from firefox+google(if another search engine would do that i'd quit google right away), Ghostery,and all of the specialized extensions built upon and out of firebug. 

So if you have a web browser that's not part of the Mozilla company nor Gecko based that can do all of that, i'd be glad to take a look at it. Also, about:config or similar with full control over all settings is a must.

edit: at phros... i'm sorry i don't have the mind of some super genius. I can't seem to remember that many urls... not all of us are super computers.

---

