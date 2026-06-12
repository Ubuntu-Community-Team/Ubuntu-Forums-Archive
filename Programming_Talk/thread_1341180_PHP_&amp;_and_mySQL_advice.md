---
title: "PHP &amp; and mySQL advice"
date: 2009-11-29
forum: Programming Talk
---

### Post by jingleheimer76 on 2009-11-29
I'm new to PHP and would like some advice on a website on which I am working.

I have a mySQL database of recipes (though subject shouldn't really matter). I want to display hyper links that execute SQL code when clicked on by the user.

I can add and display individual recipes no problem from web pages using PHP.

What I can do now is:

[LIST=1]
[*]User searches on a keyword (ingredient, whatever)
[*]Pages displays table or list of recipes names that match
[/LIST]
What I need help with is:

[LIST=1]
[*]I want the user to be able to click on the names (hopefully they will display like links)
[*]The complete recipe displays.
[/LIST]
Any suggestions? Or a good tutorial that I could use?

---

### Post by qalimas on 2009-11-29
You said you have it where they can view a complete recipe?

I'm not sure how you've done that, but I'll assume it is something like view.php?id=XX.

If not, then research $_GET and also research how to sanitize $_GET to protect against SQL injection.

Once view.php?id=2 displays the recipe in the SQL database with an ID of 2, then on the list of recipes simply make the title link to view.php?id=($recipe['id'] -- assuming you are using a while fetch_array and your variable name is recipe).

---

### Post by jingleheimer76 on 2009-11-29
Thanks, I think I am on the right track now.

---

