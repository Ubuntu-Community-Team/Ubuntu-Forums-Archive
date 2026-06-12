---
title: "html php problem"
date: 2009-04-19
forum: Programming Talk
---

### Post by Whiteice on 2009-04-19
Hello everyone I have a problem that i can't seem to figure out. What I'm trying to do is make editing a web page easier. I want to create a single page which somebody could enter information into some forms and that information is than saved and called when the user's open my main page.

editing page> storage> page that users see.

---

### Post by Reiger on 2009-04-19
Assuming you have the editing page covered (tried echo'ing back the output of the PHP code yet?) the problem most likely lies with the file permissions.

---

### Post by s.fox on 2009-04-20
Hi,

Sounds simple enough idea.  Could you post your current code so we can have a look and see where the bug might  be?  :)

-Ash R

---

### Post by ufis on 2009-04-20
> **Whiteice said:**
> Hello everyone I have a problem that i can't seem to figure out. What I'm trying to do is make editing a web page easier. I want to create a single page which somebody could enter information into some forms and that information is than saved and called when the user's open my main page.

editing page> storage> page that users see.
As I see it there is 3 things here that you need to know. And I cannot figure exactly which one (or all) is your problem.

1. How to interact between HTML forms and PHP.
[http://www.google.com/search?q=php+forms+tutorial]("http://www.google.com/search?q=php+forms+tutorial") or similar searches should provide you with that solution.

2. Storing the information.
A lot of the pages from 1. will touch on this subject too.
You need to figure how you want to store the info first. Using a DB or using Cookies or whatever. Once you decided that, **ask google again**. "php mysql tutorial" or similar searches, depending on your choice of DB, will be helpful. Or "php cookie tutorial" if you will be using cookies.

3. Retrieving and displaying the saved information.
Most topics covering 2. will also cover what you need for 3.

And remember: Ask Google. Google knows a lot about all kinds of things.
And remember 2: [http://www.php.net/]("http://www.php.net/") is your friend.

---

### Post by tturrisi on 2009-04-20
1. Users will need to login and this is stored in a cookie or the db.
2. pages read the cookie or db to determine if user is currently logged in.
3. pages contain code that displays content if user logged in else displays something else, such as default content for that section of the page.
4. logged in user accesses form to create content.
5. form input stored in db.
6. pages now display user's content in that section of page.

It's very simple.  Just like this section of these forum pages display at the upper right:

Welcome, tturrisi.
You last visited: 19 Hours Ago at 12:50 PM
Private Messages: Unread 0, Total 1.

---

### Post by gregor171 on 2009-04-20
Think of the security when users can actually save content into your page:
[WordPress hacked]("http://www.techcrunch.com/2008/06/11/my-blog-was-hacked-is-yours-next-huge-wordpress-security-issues/")
It looks a simple task, but. 
What content could be saved? PHP and JavaScript definitely not. 
You have to check what users have entered and either use some escaping or you can make some rules and possibly mapping.

---

### Post by Reiger on 2009-04-21
And it's not so straightforward to `manually' enforce (X)HTML-only rules:

Think about the following kind of things...:
```

<div 
onclick="window.location = 'http://www.evil.com';" 
style="z-index:500; position:absolute; left:0px; top:0px; width:100%; height:100%;">
My custom stuff: 
<a href="http://www.good.com" onclick="window.location = 'http://www.bad.com';">my `homepage'</a>.
</div>
```

---

### Post by gregor171 on 2009-04-21
Task as this is good for practice, but for live web it will be short lived. A part of the learning curve are mistakes. They shouldn't be costly.
For intranet use you can afford making more mistakes.

---

