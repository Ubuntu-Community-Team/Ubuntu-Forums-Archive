---
title: "how to parse css with php..."
date: 2009-02-06
forum: Programming Talk
---

### Post by hockey97 on 2009-02-06
Closed!!!!

---

### Post by Tibuda on 2009-02-06
Just rename your CSS file extension to PHP, and in your HTML too:
```
<link rel="stylesheet" type="text/css" href="stylesheet.php" />
```
and add a Content-type header to your CSS/PHP file:
```
<?php header('Content-type: text/css'); ?>
/* CSS code here */

```

---

### Post by hockey97 on 2009-02-06
Closed!!!!

---

### Post by hockey97 on 2009-02-07
the problem is I have the html cs3 vaild button thing suppsoed to be on the footer.

when I used this methdod it seems like the html button thingy dosen't use css at all even though I assigned it properly with css and the html div id.

the button appears top left of the screen. Any ideas how I can fix this or any workaround this?

The reason I need to use php is to make the layout customizable by grabbing data from the database and using those values to set the elements  on the page. 

Thanks for your time... I will still be goggling around to see any type of fix I can do and may play around with the code.

thanks for the replies so far..;):p

---

### Post by Reiger on 2009-02-07
FYI:
Using Dragonfly, Opera informs me that it computed (for the div with the id=bottom):
```

bottom: 863px;
display: block;
font-family: "UnBatang [unknown]";
font-size: 15px;
height: 51px;
left: 95px;
position: absolute;
right: 1275px;
scrollbar-3dlight-color: ;
scrollbar-arrow-color: ;
scrollbar-base-color: ;
scrollbar-darkshadow-color: ;
scrollbar-face-color: ;
scrollbar-highlight-color: ;
scrollbar-shadow-color: ;
top: 812px;
width: 1180px;

```

But for the div with id=htmlcheck it computed:
```

bottom: 35px;
display: block;
font-family: "UnBatang [unknown]";
font-size: 15px;
height: 35px;
left: 0px;
right: 1180px;
scrollbar-3dlight-color: ;
scrollbar-arrow-color: ;
scrollbar-base-color: ;
scrollbar-darkshadow-color: ;
scrollbar-face-color: ;
scrollbar-highlight-color: ;
scrollbar-shadow-color: ;
top: 0px;
width: 1180px;

```

---

### Post by hockey97 on 2009-02-07
why is that???  I put the css code to  put it next to the id csscheck.

I don't know why the htmlcheck is being shown on the top left of the screen.

any ideas?

I am using a php file with the code header content text/css

and this is what I get.

---

### Post by hockey97 on 2009-02-08
Closed!!!!

---

### Post by Reiger on 2009-02-08
PHP doesn't render anything. Software does; PHP is just a language to write software in.

And in your case the software that does the rendering (as with virtually everything accessed by HTTP) is the webbrowser (which very probably isn't written in PHP). Quite simply: there exists a bug with _your_ CSS and/or with _your_ (X)HTML.

---

### Post by hockey97 on 2009-02-08
UPDATE: I found the error It was a extra } somewhere before the checkhtml.

Thanks for the replies. 

This is solved...

---

