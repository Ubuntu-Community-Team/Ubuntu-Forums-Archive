---
title: "ajax/php/javascript problem with populated forms passing values."
date: 2009-11-01
forum: Programming Talk
---

### Post by hockey97 on 2009-11-01
Hi, I have a problem. 

I posted the problem here: [http://pastie.org/679037](http://pastie.org/679037)

I know it's messy so I will sum it up here give you a short version.


I have 3 drop down menus that consist of country,state/region,city. 

these 3 drop down menu uses javascript,ajax,php to populate their drop down list.  So the list comes from a database and is only shown in the drop down list based on the conditions meaning what the user select.. what country is selected  would populate the state list and what state is selected would populate the city list.

The problem occurs when the user selects all what they need and submits it. 

The other php file that grabs these inputs by using the post method. I checked them and they contain nothing. This is where I get query and mysql_num_rows errors. 

What can prevent the values from passing when submitted?

---

### Post by januzi on 2009-11-01
What does the firebug show when You examine one of the select fields ?

Edit:
Why all those select have got the same name - id ?

---

### Post by NoaHall on 2009-11-01
Oh, btw you need session_start right at the TOP. Before anything else(except the <?php)

---

### Post by hockey97 on 2009-11-01
I now just tested the post values. I changed the name of each select from id to straight forward City,State etc.

I now tested by using echo and now I can see the values. 

the firebug shows no errors or anything. I still do have the query errors and mysql_num_rows errors.

I still don't know why I am getting those errors.

---

### Post by korvirlol on 2009-11-01
>  		Oh, btw you need session_start right at the TOP. Before anything else(except the <?php) 	

he has it at the top, and all of the session variables he is using in the script are commented out.



As far as the SQL errors: After a brief look, it looks like you used the $find resource multiple times for mysql_fetch_assoc. You can only use a resource once per query. You should try printing the SQL error to see if it is a problem with your query, or something else. I'd deal with the SQL errors before you worry about ajax.

Also, just a suggestion. I used to do ajax in the method you chose above before i discovered the wonderful world of jquery. It makes doing ajax requests (almost absurdly) simple, and it is very simple to plug in to your web application.

Just to demonstrate this, a simple ajax jquery request:

```
                $.ajax({
                        type: "GET",
                        url: yourscript.php
                        dataType: "text",
                        cache: false,
                        success: function(msg, e){
                              //do work with what your script returns
                        }
                });

```

---

### Post by NoaHall on 2009-11-01
> **korvirlol said:**
> he has it at the top, and all of the session variables he is using in the script are commented out.



As far as the SQL errors: After a brief look, it looks like you used the $find resource multiple times for mysql_fetch_assoc. You can only use a resource once per query. You should try printing the SQL error to see if it is a problem with your query, or something else. I'd deal with the SQL errors before you worry about ajax.

Also, just a suggestion. I used to do ajax in the method you chose above before i discovered the wonderful world of jquery. It makes doing ajax requests (almost absurdly) simple, and it is very simple to plug in to your web application.

Just to demonstrate this, a simple ajax jquery request:

```
                $.ajax({
                        type: "GET",
                        url: yourscript.php
                        dataType: "text",
                        cache: false,
                        success: function(msg, e){
                              //do work with what your script returns
                        }
                });

```

It needs to be before the includes, too. For good practise, if nothing else.

---

### Post by hockey97 on 2009-11-01
ok, I got rid of the error of mysql

---

