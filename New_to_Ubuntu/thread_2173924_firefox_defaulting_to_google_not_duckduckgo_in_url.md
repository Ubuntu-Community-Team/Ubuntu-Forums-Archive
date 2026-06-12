---
title: "firefox defaulting to google not duckduckgo in url bar"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-09-11
When I type something in the url bar I want it to default to a duckduckgo.com search.

Despite trying, I have had no luck with these instructions, and it keeps defaulting to a google search:

Change the default search engine of FireFox address bar:
With FireFox you can search simply by typing your search terms in the address bar (that’s where you see your current URL). In this case, the default search engine will be used to search.
    Open about:config in Firefox (if you doing it for the first time, you may have to promise you are going to be careful)
    Search for keyword.url from the filter box.
    Double click on this entry. It will open a dialog where you can edit the ‘keyword.url’ string.
    Change this string to whatever you want it to be, ie:
[https://duckduckgo.com/?q=](https://duckduckgo.com/?q=)


Please help

---

### Post by Vaphell on 2013-09-12
i think that since FF23 keyword.url doesn't work anymore. The rationale is it was too easy to use it in hijacking exploits, modify that key and suddenly nublet user doesn't know what's happening. Now the urlbar defaults to the search engine selected from the dropdown to the right.

[http://duck.co/topic/keyword-url-parameter-removed-from-firefox-23-fix-inside](http://duck.co/topic/keyword-url-parameter-removed-from-firefox-23-fix-inside)

---

