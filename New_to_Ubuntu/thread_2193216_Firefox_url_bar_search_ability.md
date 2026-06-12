---
title: "Firefox url bar search ability"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by nathanmiller77 on 2013-12-11
I know on windows, the main url bar for firefox can double as a search bar; but it times out for me. I can't see anything in the about:config to toss this capability into firefox.

---

### Post by sammyp90 on 2013-12-11
i had this problem with fresh install and it went once i updated firefox, is your firefox up to date?

---

### Post by nathanmiller77 on 2013-12-11
Yes. 25.0.1

---

### Post by vasa1 on 2013-12-11
> **nathanmiller77 said:**
> ... I can't see anything in the about:config to toss this capability into firefox.
But that capability is there by default (unless you've made some changes in the past). What exactly is your issue? Browser version? Linux OS and version?

---

### Post by asus-user on 2013-12-11
> **nathanmiller77 said:**
> Yes. 25.0.1

The newest version of Firefox is **26.0**. update and see what happens.

---

### Post by nathanmiller77 on 2013-12-11
I went to firefox's website, and the page says congratulations, your firefox is up-to-date. :-( I had assumed I was, sorry.

And what @vasa: what exactly is my issue is what I said. The main URL bar doesn't act like a search bar in the way that the actual search bar (in the top right corner) behaves. I type something to search; and it just shows status as "Connecting..."; and never brings up a google result. I use Ubuntu 13.10. 
Firefox 25.0.1 (this was said above...)

---

### Post by deadflowr on 2013-12-11
Have you tried switching search engines, maybe?

You can switch them with the search bar.
Try yahoo, or bing or maybe, for free software ethics, duckduckgo.
See how that works.

---

### Post by asus-user on 2013-12-11
> **deadflowr said:**
> Have you tried switching search engines, maybe?

This worked for me, whenever I choose a different search engine and write a word in the url bar, it uses the chosen search engine to search for that word.

---

### Post by nisargshah on 2013-12-12
You might find your answer at [URL="http://www.searchenginejournal.com/change-your-default-search-engine-in-firefox-google-chrome-ie/24378/#address"]http://www.searchenginejournal.com/change-your-default-search-engine-in-firefox-google-chrome-ie/24378/#address

[/URL]> 
[LIST=1]
[*]Open *about:config* in Firefox (if you doing it for the first time, you may have to promise you are going to be careful)
[*]Search for* keyword.url* from the filter box.
[*]Double click on this entry. It will open a dialog where you can edit the ‘keyword.url’ string.
[*] Change this string to whatever you want it to be:
[/LIST]

[IMG]http://ho9od35yvs05ejqn.zippykid.netdna-cdn.com/wp-content/uploads/2010/09/default-search-engine-gogle-firefox-01.jpg[/IMG]
[URL="http://www.searchenginejournal.com/change-your-default-search-engine-in-firefox-google-chrome-ie/24378/#address"]
[/URL]

---

### Post by Habitual on 2013-12-12
keyword.url was removed from firefox releases not too long ago.

---

### Post by nathanmiller77 on 2013-12-12
I will try changing the search engine when I get home today. As for the url.keyword; yes, I found that as a listed solution but as was said; could not find that parameter to change. It seems it was removed.

---

### Post by whitesmith on 2013-12-12
> **nathanmiller77 said:**
> I went to firefox's website, and the page says congratulations, your firefox is up-to-date. :-( I had assumed I was, sorry.

And what @vasa: what exactly is my issue is what I said. The main URL bar doesn't act like a search bar in the way that the actual search bar (in the top right corner) behaves. I type something to search; and it just shows status as "Connecting..."; and never brings up a google result. I use Ubuntu 13.10. 
Firefox 25.0.1 (this was said above...)This is highly unlikely, but once I had exactly the same problem with FF in Ubuntu because I had used about:config to disable the referer (and referrer) headers. You didn't do that by any chance, did you?

---

### Post by Habitual on 2013-12-12
firefox "manage search engines" +keyword.url
in your favorite search engine.

---

### Post by vasa1 on 2013-12-12
> **whitesmith said:**
> This is highly unlikely, but once I had exactly the same problem with FF in Ubuntu because I had used about:config to disable the referer (and referrer) headers. You didn't do that by any chance, did you?
Ideally, people should try running in safe mode or with a clean profile when they encounter problems. And if they've done so, they should mention that.

---

### Post by nathanmiller77 on 2013-12-13
> **whitesmith said:**
> This is highly unlikely, but once I had exactly the same problem with FF in Ubuntu because I had used about:config to disable the referer (and referrer) headers. You didn't do that by any chance, did you?

I have not. I checked, in case, and it is the default setting.

Changing the small search engine to duckduckgo did nothing, I still get no search results.

---

### Post by nathanmiller77 on 2013-12-13
FWIW, the only thing I've changed was the 'clickSelectsAll' field; as I'm used to just clicking in the URL bar to highlight all.

---

### Post by nathanmiller77 on 2013-12-14
Not sure what happened. Power went out a day ago, started computer up, firefox works fine now. Weird...

---

### Post by nisargshah on 2013-12-16
> **Habitual said:**
> keyword.url was removed from firefox releases not too long ago.

I'm using *Firefox 26* and I do have **keyword.URL** in my *about:config*.

---

