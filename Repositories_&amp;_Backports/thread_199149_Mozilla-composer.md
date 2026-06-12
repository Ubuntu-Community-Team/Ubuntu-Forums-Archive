---
title: "Mozilla-composer"
date: 2006-06-18
forum: Repositories &amp; Backports
---

### Post by DavidFourer on 2006-06-18
I just upgraded to Dapper.  Flawless install and better hardware support than Breezy.  

However, Mozilla Composer, a great web page creation tool, disappeared from my applications menu.  apparently Ubuntu uses it's own builds of firefox and thunderbird, which is confusing.  The Mozilla website is also confusing because composer is listed as part of Mozilla suite, while firefox and thunderbird are separate apps in the newest versions.  

I suspect mozilla-composer is still installed, but not in the applications menu any more.  I don't know how to find the executable and make an icon to launch it.

If not...
I can go to Applications/add-remove and find firefox but not composer.  I can go to sys/admin/synaptic package manager and find firefox and thunderbird but not mozilla composer.  I have multiverse and universe repositories checked.  

There is a sticky called "my recommended Dapper sources.list".  I don't know if I need any of this.  I forget how I installed mozilla-composer in Breezy, whether I downloaded it from the mozilla site or found it in a repository.  

Thanks for your expert help!

---

### Post by plateoffelt on 2006-07-26
firefox and thunderbird are separate from mozilla suite. mozilla suite seems to have dissappeared off the repositories i see listed in synaptic- it does not show up in a search at all for me. what worked for me, though was just running > apt-get install mozilla. that installed the mozilla suite no problem, including composer. a friend (who was the one trying to do this at the time and having trouble) noticed that it did not work if he did not have universe level repositories selected.

i don't know if everyone is having this problem, just something i noticed this morning.

---

### Post by jscheiderer on 2006-09-12
Apt-get is a good way, buty also simply going into synaptic and click into SETTINGS - REPOSITORIES, check everything, close and reload. install mozilla browser and composer will be in menu.

---

