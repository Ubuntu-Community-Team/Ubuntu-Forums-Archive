---
title: "AJAX tutorials hard to find (can you recommend)"
date: 2009-01-18
forum: Programming Talk
---

### Post by dracule on 2009-01-18
Hey guys,

I have been looking around for some nice AJAX tutorials.

Basically the kind of stuff I need (preferably out of the same library):

User Registration:
check to see if username is taken
check to see if passwords match

basic stite viewing
retrieve data from my server and replace what is already is in the div
(like right now i have it set up for viewing along list. the user sees the first 20, clicks "next" the first 20 dissapears w/ some nice effect and the next 20 come along)

add user as friend:
start typing their name, a list drops down of all user's that match what you type so far


-------
I know how to do all the serverside stuff (using django). I am just having a hard time following the tutorials since they are scattered about and all use different libraries

---

### Post by jflaker on 2009-01-18
AJAX is rather simple....pulling data dynamic from a DB

I attached a simple autocomplete....it may help you understand

Once you do one AJAX, it will come to you.

---

### Post by dracule on 2009-01-18
> **jflaker said:**
> AJAX is rather simple....pulling data dynamic from a DB

I attached a simple autocomplete....it may help you understand

Once you do one AJAX, it will come to you.

your example has some errors, when i type a country it comes up w/ some weird stuff

---

### Post by myrtle1908 on 2009-01-18
Maybe this one ... [http://www.w3schools.com/Ajax/Default.Asp](http://www.w3schools.com/Ajax/Default.Asp)

Once you have grasped the concepts you should use a toolkit like ExtJS or JQuery or YUI ... there are many to choose from. Personally I use ExtJS due to its slick UI widgets, excellent docco and active community.

---

### Post by jflaker on 2009-01-18
> **dracule said:**
> your example has some errors, when i type a country it comes up w/ some weird stuff


Yep, you cant run it as 
file:///ajax/index.htm

It won't work.  Make sure it is in your www directory and you have apache2, php and MySql....
You need to access it as [http://localhost/ajax](http://localhost/ajax)

---

