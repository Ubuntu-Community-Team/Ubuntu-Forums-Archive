---
title: "My Php Project"
date: 2011-02-21
forum: Programming Talk
---

### Post by yarnoiser on 2011-02-21
Hi yall. I'm currently working on a web project for a friend, and one aspect has been stumping me.

I'm completely new to php, but my research has indicated that a php script can receive information from an html form using php's get and post variables, but I've found nothing on how to do the opposite.

What I'm trying to do is get an array of file names from a directory scan within the php script, and have the elements converted to options on a selection list type form.

The end result should be you can select a file from a particular server directory using the form.

Can anyone tell me if this is possible, or if there is a better way to implement it? Thank you for taking the time to assist.

---

### Post by LoneWolfJack on 2011-02-21
it appears you're not only new to PHP but (web) programming in general.

but, yes, what you intend to do is possible. you would simply scan a directory for files using PHP's built in functions and then produce the HTML code for a dropdown.

[http://www.thelampblog.com/2010/03/07/get-directory-tree-andor-files/]("http://www.thelampblog.com/2010/03/07/get-directory-tree-andor-files/")

(not my blog, but from a freelance programmer my company is hiring on a regular basis)

---

