---
title: "[PHP]SQL Injection via comment box."
date: 2012-06-13
forum: Programming Talk
---

### Post by kenweill on 2012-06-13
I always got hacked again and again via comment box.

Comment box (in database) is saved as text. How come a javascript code is used to mess my website via comment box?

Instead of a user writing a comment, a javascript is entered as comment and messes with my website.

How could I block such thing?

I tried the same code, on my competitors (not trying to inject them, just want to know the effect), but the effect is just the javascript code was displayed as comment as text in my competitors website but when entered in mine, displays blank and all other data below them get's messed up.

Is this SQL injection? Where can i find guides or how can I patch this?

I can share my addcomment.php file if needed.

--- Addition ---

I think the displaying part is the problem. If scripts are saved in the database, then they'll only execute when being fetched as is. Is it possible to force all database fetching into displaying it as text and not as values? Even if it's pure text, still convert it to text to make sure that no codes are fetched as codes but instead, displayed as text.

Code to display comment:
[PHP]<p><?php echo $comment["Comments"] ?></p>[/PHP]
If the value of $comment["Comments"] is a code, then it gets executed. How can I force it to display as text, regardless if it's really a text or a code?

---

### Post by wallaroo on 2012-06-13
Hi kenweill,

I get around this by simple substitution of 'code type' characters with their safe HTML and ASCII code equivalents (referred to as 'escaping'), thus rendering any embedded scripting ineffective. You do this on the special characters like ' " $ & < > (for example '<' gets changed to '&lt;'). Web browsers understand these characters and display their character equivalents correctly.

So when the users 'post' their comment, before you do anything with it, run it through the filter to convert special characters.

You can also store the string with the converted characters directly in the database and if you need to retrieve it and display it then it's already safe to do so.

However, if you are presenting the string back to the user in a form for editing then you'll need to 'un-filter' it back into the original form, and re-filter it when they present it back to you. This way you prevent double-filtering the string and screwing it up.

There are probably utilities available but I prefer to control this myself.

Note: I've included code examples here as an image, because this site is doing exactly what I'm talking about here and if I try to embed the code in this message it gets filtered and is changed - good practice.

---

### Post by kenweill on 2012-06-13
Thanks wallaro.

Actually, I tried mysql_real_escape_string () to no avail as "It's" will be displayed as "It\'s", and any other characters.

htmlspecialchars () kind of fixed my problem with

[PHP]<p><?php echo htmlspecialchars($comment["Comments"]) ?></p>[/PHP]

I also used the same functions for all other variables which involves user inputted entry. 

Currently, website is doing fine.

Yes, codes are still accepted on comment box, saved as javascript in database but fetching it with htmlspecialcharacters makes it displayed as text now and not as executable code.

So for now, I'm gonna mark this thread as solved.

Thanks for your suggestion. I'll take a look into those and see if I can do that in my website.

---

