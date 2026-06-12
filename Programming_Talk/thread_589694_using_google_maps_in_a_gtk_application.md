---
title: "using google maps in a gtk application?"
date: 2007-10-24
forum: Programming Talk
---

### Post by Choad on 2007-10-24
i am wanting to make an app for my dad. he does piano tunings, and goes to lots of places... the idea is that the app will hold a database of all his customers, and where they are, and will find the most efficient way to visit them all

now i could do it just by getting a image of a map and getting the user to input the locations, but google maps is very good at finding locations based just on postcode so i thought it would be a very neat idea to somehow integrate it with google maps and get that to do route layout etc. etc.

but is it possible to use google maps in this way? can i extract information from google maps such as x/y coords?

i was also hopefully going to integrate it with evolution, so you can have a contact list maintained in evolution, and then my app will take that contact list and look up the postcodes on google maps.

any help appreciated

(also, if it can use google maps, then it can be a generic app that anyone who does house calls can use)

---

### Post by jespdj on 2007-10-24
You can probably find interesting information about using Google Maps in your own application here: [http://www.google.com/apis/maps/](http://www.google.com/apis/maps/)

It looks like this API is meant to be used from JavaScript inside a web page, but probably you can also find a way to use it from a regular desktop application.

But what is your application going to be doing that you can't do with the normal Google Maps already?

---

### Post by Choad on 2007-10-24
organise the hundereds of places he has to visit each year in to groups representing 1 day's work, and organise them so they're close together so he doesn't have to travel ridiculous distances to get from one place to the next.

---

