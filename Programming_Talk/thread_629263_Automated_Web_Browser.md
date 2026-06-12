---
title: "Automated Web Browser"
date: 2007-12-02
forum: Programming Talk
---

### Post by Spektyr on 2007-12-02
I'm not exactly sure what this should be called, but the best name I can think of is an "Automated Web Browser".  Basically, I'm looking for a way to run a particular website more efficiently - like the way the KoLmafia program runs KoL (for those familiar with it.)

Ideally I'd like to be able to view it as raw data rather than all the pretty pictures and such, and have it perform series of tasks without constant supervision.  So it needs to be able to read information from the page and then react to it according to preset rules.


Does an application that can do this already exist?  If not, what would be the best way to make one and how much expertise would it require?

Thanks.

---

### Post by SjoerdC on 2007-12-02
you could try something like [iMacros]("https://addons.mozilla.org/en-US/firefox/addon/3863") but I'm not sure if that is what you mean...

---

### Post by smartbei on 2007-12-02
I am not sure what you mean by 'run a website'. If you mean get the source of the website and perform operations on it/according to it, I think the way to go would be to learn Python and use the module urllib2 to fetch the website, either re for regular expression parsing or something like beautifulsoup for fetching data from a specific part of the website.

Beware that while this may be the fastest way I can think of of doing this, it could easily take you a week or two (or three or four, depending on your time, dedication, previous programming experience, etc.).

---

### Post by Spektyr on 2007-12-02
Yeah, by "run a website" I mean from a user side perspective, not administrate.

I want to be able to load the data from a page, and instead of it being visible graphically (where I need to mouse-over to see certain information) it is shown as alpha-numeric data.  Then I want it to perform certain tasks on its own depending on the data it reads.

For example, if a certain value is within a certain range, it would then follow that link, perform the task I currently do manually to correct that value, and continue to the next task.

From the looks of it, the iMacros thing is close, but not quite what I need.

---

### Post by ssam on 2007-12-02
maybe Selenium is what you need

---

