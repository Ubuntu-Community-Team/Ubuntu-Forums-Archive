---
title: "php question..."
date: 2009-03-27
forum: Programming Talk
---

### Post by hockey97 on 2009-03-27
Hi, I am working on  a table system.

Currently I am making a market part of my website.

So basicly the users are able to upload images and descriptions on what they are selling.

So I have a page where it gives you the map of the U.S. You can click on  a state and it should load all catagories that has stuff posted.

So lets say their is no cars in navada for sale  but their are a bunch of computers for sale on my site.

I want the system to update the drop down menu. This way I don't need to put no results found.

Now that's great and all. 

I just have 2 problems. I want to make this also international.

So I added a drop down menu right above the map of the U.S.

So since I don't have the time to manually add country names.

I decided that when the user is posting a ad for selling an item they will have to input what country  and if U.S then what state.


Now I was told that it's a bad idea cause they can add a country called  canaputa.

a country that dosen't exist. or add  eeeeeeee   etc..

Do you think I am going at this at the right way or is their a better way of doing this?

---

### Post by s.fox on 2009-03-28
You could store a list of all the countries of the world in a database table.    You could then have php create a drop down menu from the database.

Alternatively you could have a drop down menu containing a list of all the countries without using a database.   

Take a look at the source code of [this web page]("http://www.jkwebdev.com/countriesList.html").

-Hope this gives you some ideas.

---

### Post by tturrisi on 2009-03-29
How much international participation do you expect to have?
Simplify it and for non-US, group by continents, i.e. EU, Asia, Africa, SA, Aus.

If want to use individual countries, and allow user to input the country rather than select from a lsit, you will have to implement error checking such as when a user inputs "South Afrblogonia".  You'd have to x-check that name with a list of countries in a database table.

For user input like this it's best to NOT give the user the opportunity to type text, force then to make a selection which you can control.  You could even maintain the country database along with lat & long and use those coordinates for the maps.

Another thing to consider is shipping.  Use only those countries where goods can easily be shipped to.  For example, I'm not certain, but shipping to Cuba may not be easily handled, so don't use Cuba in your selections.

---

