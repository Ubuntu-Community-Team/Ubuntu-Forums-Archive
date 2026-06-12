---
title: "Issue with PHP / input forms with MySQL scripts."
date: 2010-06-15
forum: Programming Talk
---

### Post by Dave_Connor on 2010-06-15
So with my website I am designing I am trying to get where when you search on the sidebar it will store the user submitted search but the problem is when the <form> tag printed out will go to search/search.php and then the script will preload. I have tried to create a process script to echo back the vars to bar.php but this did not work. Any tips ?

Edit: Found the solution with simple passing variables through a few scripts and now prints the user input in text field now. Thanks to everyone who wanted to help. Sometimes it takes simple messing around and end up fixing an annoying issue.

---

### Post by xsandz on 2010-06-15
can u please a little bit more descriptive baout your prob...its not clear to me

---

### Post by DanielWaterworth on 2010-06-15
So, you're trying to send variables from one php page to another?

---

### Post by Dave_Connor on 2010-06-15
Well I know about passing variables to other scripts. Pretty simple stuff within PHP. 

Steps:
1. Take input that the user submits in bar.php 
2. Be able to take this input and allow for the value of <input name='search' value=$search />
3. Then execute search.php that will search MySQL database on my server and return results. 

I am not quite sure what to do here with this. The problem with search.php is the action in the <form action='search/search.php'> tag I have set and yet I would like to when the user submits his input on he is looking for on my site is to have his search stored / retrieve and print in bar.php I also have set up to retrieve the search value and then search the SQL database. 

Any tips on what to do ?

---

