---
title: "contract a form into a single hyperlink"
date: 2010-11-09
forum: Programming Talk
---

### Post by w0296094 on 2010-11-09
Hey guys this is what i want to do:

I want to have a word that also acts like a hyperlink, or more specifically, acts as a form category that has already been selected. I.e.:

"You can select your non-profit by _TYPE_, _ORGANIZATION_, or _FACULTY_. "

any of the words that have been underlined will be clicked on and each word will execute a command:

[HTML]
<form action="viewdatabaseinformation.php" method="post">
<br /> 
    <select name="searchtype"> 
    <option value="TYPE">Type</option> 
  </select> 
  <br />
 <input type="submit" value="Search">
[/HTML]

In other words, as I click TYPE, it will be as if I selected type from a drop-down form and clicked submit. Is there anyway I can do this with PHP alone. 

(I will be using PHP and mysql, using apache)

---

### Post by SeijiSensei on 2010-11-09
Use an A tag and enter the parameter like this:

```
<a href='viewdatabaseinformation.php?searchtype=TYPE'>TYPE</a>
```

You can retrieve the value in PHP using either $_GET['searchtype'] or $_REQUEST['searchtype'].

---

### Post by w0296094 on 2010-11-23
thanks, i understand the rationale behind it. Now i wanted to do a more complex one.

[HTML]
  <form action="tbn.php" method="post"> 
    View Service-Learning opportunities by selecting the organization below. 
    You may also sort opportunities and view them by faculty, location and type. : <br /> 
    <select name="searchtype"> 
    <option value="course">Department</option> 
  </select> 
  <br /> 
  Enter Search Term: <br /> 
    <input name="searchterm" type="text"> 
    <input type="submit" value="Search">       
  </form>

[/HTML]

Now the first part is the same, but how do i do it when i have to enter an additional filter(or filters) such as searchterm.

---

