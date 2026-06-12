---
title: "Bash Script for Repeated Task"
date: 2009-01-16
forum: Programming Talk
---

### Post by coberg on 2009-01-16
Hello All,

My company just went to Ubuntu from (ugh) Win2000 and I couldn't be happier, with only one exception.  My job requires completing the same intranet web form over and over again with the same information.  I was looking through the programming section and I decided a bash script might be the best way to go about this.  Any thoughts on how I might accomplish this?  I can get firefox to open the page with '/usr/lib/firefox and the web address 'http://intranet/productionforms/18523/' but how would I go about filling in the information and then submitting?

Thanks in advance.

---

### Post by mechanicalturk on 2009-01-16
The [iMacros]("https://addons.mozilla.org/en-US/firefox/addon/3863") Firefox extension sounds like it might help.

---

### Post by slavik on 2009-01-16
curl and libcurl :)

---

### Post by coberg on 2009-01-17
Hey, thanks guys!  I'm checking out both now, I'll post back the results...

---

### Post by brunovecchi on 2009-01-20
If you want to dive into a little of Perl, the module [_**WWW::Mechanize**_]("http://search.cpan.org/dist/WWW-Mechanize/lib/WWW/Mechanize.pm") seems to be a perfect fit for your task.

---

