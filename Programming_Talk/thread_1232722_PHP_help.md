---
title: "PHP help??"
date: 2009-08-05
forum: Programming Talk
---

### Post by kuldeepsidhu on 2009-08-05
I am starting with PHP..i know little bit of C,C++....i have read many books from net..but i cannot get the clear idea..i want to  make my own site using html,css,php,mysql....can you tell me book or tutorial,which is easy for the beginner...which explain the each step for making a website..i know html and css..i want to make  a site of many pages..tell me how can i buid that site..

---

### Post by enduser000 on 2009-08-05
Hey,
   php is great.  You should grab the [PHP manual]("http://www.php.net/download-docs.php") and look at that.  Also some good tutorials for css and html can be found [here]("http://www.w3schools.com/css/").  I'll include my generic.php and index.php for you to see how I'm doing things (using the same stuff u are, working on forums/mysql now).  I'm just calling this page with different images and data each time as you can see. Good luck!

enduser

---

### Post by Finalfantasykid on 2009-08-06
Many web pages are divided up using a header.php , body.php , and a footer.php file.  Your index.php file would include("header.php"); and so on.  This way, if you make a layout change, it will reflect it on all pages, instead of you having to change it for every single html file(which as you can imagine for large websites this can be daunting).

Now, when you are linking to another page in your website, I would recommend having the link do something like this...

```
http://www.yourDomain.com/index.php?page=newPage
```In index.php you will have something like...

```
switch ($_GET['page'])
    {
        case 'newPage':
            include("newPage.php");
            break;
        case 'otherNewPage'
            include("otherNewPage.php);
            break;
    }

```You would continue that switch statement for all you webpages.  include() functions are very easy to use, and can save the amount of work you have to do significantly.  And if you can get databases and php working together, you can potentially have your entire website consist of just 1 php file and a bunch of database entries.

I don't know how much php you know, but hopefully this helped :)

---

### Post by kuldeepsidhu on 2009-08-06
thansk for the help...what is the  ide you use for coding...i am downloading quanta plus..is it good..?or some other is good..can we use html,css, and php in the same file..under .php name....???


like in header.php file..we have to code some css to place the header content in center....can we use so..?

prevoius i have used this but i got a problem..

---

### Post by credobyte on 2009-08-06
Yes, PHP file can contain HTML/CSS/JavaScript/PHP. Regarding IDE's .. Eclipse O:)

---

### Post by Mirge on 2009-08-06
> **credobyte said:**
> Yes, PHP file can contain HTML/CSS/JavaScript/PHP. Regarding IDE's .. Eclipse O:)


+1

Get Eclipse PDT all in one from zend... see:
[http://www.zend.com/community/pdt](http://www.zend.com/community/pdt)

---

### Post by enduser000 on 2009-08-06
As they said above you can include HTML/CSS/PHP in one file.  However you might want to put your css in a separate file and include it with

<link rel="stylesheet" type="text/css" href="path/to/mycssfile.css">

As for the php/html it's usually a good idea to separate things that change from those that don't.  It will get more difficult to maintain large files mixed with php and html as they get bigger if you don't keep some stuff separate.

As for the IDE I've always liked [Geany]("http://www.geany.org/").  It's really fast and cross platform and has good syntax highlighting.  Cheers,

enduser

---

### Post by kuldeepsidhu on 2009-08-07
can you give me example..how to add html and css to php file..i have linked the css file...in my file header.php..but it does not work..is their a special syntax for adding css to php...

and is their need to write the <html></html> codes in the header.php file.
while writing the html code..or is it automatically  check it...plz give me the link to some tutorial which has css and html included in php file..

---

