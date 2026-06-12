---
title: "Question about OOP PHP5 and proper app structure"
date: 2009-01-26
forum: Programming Talk
---

### Post by thenetduck on 2009-01-26
I am making a PHP app and I am trying to figure out if the best way to store my classes is in one big classes.php file or keep all of them in separate files like dog.php cat.php and mouse.php 

I guess the real question is, if I keep them in one .php file, does it make the server run tons of processes when I include the classes.php file to be used? Or does it not matter because they aren't being executed? 

I know how to OOP but am trying to figure out how to effectively do it with php because it's in a little bit different context than I am used to. 

Also, I am creating a site with this type of structure (Control(controls relaying information), Webpages (front end) Classes(functions and back end). 

Is this the right way to do it? 
Thanks 
The Net Duck

---

### Post by snova on 2009-01-26
> **thenetduck said:**
> I guess the real question is, if I keep them in one .php file, does it make the server run tons of processes when I include the classes.php file to be used? Or does it not matter because they aren't being executed?

I don't know much about PHP, but I think I can safely say; no, it doesn't matter.

> Also, I am creating a site with this type of structure (Control(controls relaying information), Webpages (front end) Classes(functions and back end). 

Is this the right way to do it?

Sounds good to me.

Actually, it sounds like you've recreated MVC, in a way.

---

### Post by slavik on 2009-01-26
separating classes into separate files is nicer for you, so that instead of having 1 10000 line file, you have 10 1000 line files. the choice is yours.

---

### Post by DocForbin on 2009-01-27
I've never benchmarked this in PHP, but it wouldn't surprise me if there are noteable performance benefits to using separate files (depending on size and use).

Regardless, it's much cleaner to separate them IMHO.

---

### Post by Reiger on 2009-01-27
From personal experiences with syntax errors and the like it looks like:
[list="1"]
[*] PHP skims a file for possibly interesting stuff. It does this by analyzing scope: the outer scope contains no  {} which is therefore fully parsed and executed along the way, once a reference is made to something of inner scope (function foo () {} or class bar {} or even if(true) {}) that item is parsed along the way as well.
[*] If PHP cannot find the referenced item it will proceed to analyze included files in the scope it is currently analyzing (which is to say: an include only gets parsed/evaluated if the containing scope has been included evaluated)
[/list]

Assuming my observations are correct, this means that you can squeeze out a tiny bit of performance by grouping classes which reference each other inside a file as it'll mean less seek time. On the other hand, a very big file of which a tiny portion is actually used incurs a lot of read time for no good purpose (because the entire outer scope must be evaluated which amounts to reading the entire file).

EDIT: Of course it makes ton of difference for your editor: many small files incur much less processing load when syntax highlighting is involved. That is resolved for every change for the file which is being modified; meaning a 10000 line file with syntax highlighting is going to make for a slow editor.

---

### Post by skirkpatrick on 2009-01-27
PHP, like all script interpreters, reads and processes the entire file.  For things like classes and functions, it creates objects to be used later when they are referenced but this is why you can have a lot of functions at the top of the file and do nothing other than have an echo or print statement at the bottom and it will still be executed.  Therefore, the larger the file (including all the included or required files), the longer it will take to process.

As far as OOP or any programming goes, you are better to split your functionality up into distinct modules.  For instance, you talked about having a cat and a dog class.  If you have another module that only wants to deal with a dog class, then why should it carry around the baggage of a cat class (or snake, cockroach, horse, etc.)?  It may look like there are more files littered about on your webserver but it will actually be easier to maintain.

---

### Post by thenetduck on 2009-01-27
Thanks for all the helpful answers. I do have a question about my post that I am still trying to figure out.

Can my control script some how be OOP based? As of now when I pass data through a form to my control, it's just a script that has a lot of if statements or case statements in it. Is there a way to use classes to both display information and process information? I am downloading joomla to check out their source code and see if I can find anything interested. 

Here is an example of the "mangled script control" with ifs and else I am talking about. 


The Net Duck

---

