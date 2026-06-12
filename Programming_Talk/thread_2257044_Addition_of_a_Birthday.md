---
title: "Addition of a Birthday"
date: 2014-12-16
forum: Programming Talk
---

### Post by TheodoreP on 2014-12-16
I'm trying to come up with a way of adding a three drop menus that will insert a users birthdate into the database, and I would like a little advice on a nice professional way of accomplishing this. As well, I want to automate the form so that it will fill in the options automatically, for that I will probably be using a while loop.

---

### Post by ofnuts on 2014-12-17
Three drop menus added to what, a web page? A regular application (what language and windowing framework..)? 

The professional way to do it is to avoid the three dropdowns for day/month/year and use a calendar popup instead....

---

### Post by TheodoreP on 2014-12-17
the drop menus (select menu) will be added a register include file for the website I'm developing, but your calendar popup idea has seriously got me rethinking my options right now. I was mainly going off of what I've seen sites like facebook use for this. my main concern is with storing the date in the database table as a date and not being able to have it displayed like "month day, year." As well as being able to program a way to calculate the users age by taking the users birth year and subtracting from the current/past year, depending on weather or not the month and day have passed, the current year!

---

### Post by ofnuts on 2014-12-17
Ah,storing dates... One could write a book about it (mostly filled with anti-patterns...). Is your site going to be used across several time zones? Then things get really interesting :)

---

### Post by TheodoreP on 2014-12-17
I really don't know yet, it all depends on where people are located when accessing the site. So I must go with the answer of yes, the users will be from all walks of life and across the globe!

---

### Post by ofnuts on 2014-12-19
So you'll have to take their time zone in account (IIRC their navigator sends you a "time offset")

---

