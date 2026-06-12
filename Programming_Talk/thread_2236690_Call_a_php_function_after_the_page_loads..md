---
title: "Call a php function after the page loads."
date: 2014-07-28
forum: Programming Talk
---

### Post by Sasha_Aderolop on 2014-07-28
I'm  making a website wher i have a table where quotes (finance) are loaded  from a csv file. When i visit the page it takes i while to load the page  becauese of the csv files. Is there a way to load that part of the page  after everything else has loaded ?

---

### Post by SeijiSensei on 2014-07-28
You could perhaps use an iframe for the data display and have that call a second PHP script to load the data.

Have you considered uploading the csv data into an SQL database like PostgreSQL or MySQL?  Retrievals would probably be faster.

Another possibility is to load the csv data once and store it in a session so it is immediately available to all other pages after the initial load.  That won't speed up the initial loading, but it might move later pages along.

---

### Post by s.fox on 2014-07-30
As an idea you could call another php script via AJAX once the page loads and have the php script page contents load in a div.

---

### Post by Sasha_Aderolop on 2014-08-12
Thanks all for your help. 
I use javascript onLoad function to bring it in after the rest of the page has loaded.
and then call the data into a php array function and then display it.

---

