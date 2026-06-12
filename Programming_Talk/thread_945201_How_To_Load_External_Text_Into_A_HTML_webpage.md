---
title: "How To Load External Text Into A HTML webpage"
date: 2008-10-12
forum: Programming Talk
---

### Post by Bradosia on 2008-10-12
Hello,
I am sure this has been posted somewhere else but I haven't found that "perfect" post that explains it all to me so I have decided to start a topic about this.

First off, when creating your own website from scratch, the thing that always get on my nerves is having to create a navigation bar for your page. And it isn't creating the navigation bar yourself, its having to update it on EVERY SINGLE WEBPAGE of my website whenever I decide to add someting new to my navigation bar. 

This brings me to what I am attempting to do. I figured that maybe i can store the HTML code for my navigation bar in a file called "Nav.txt". Whenever anyone views any webpage from my website the navigation bar will look the same because the HTML is from the same text document. How I will do this is by creating a blank box on every webpage, then adding the unique information on my webpage in a separate box. My webpage will then take the HTML code from "Nav.txt" and insert it into the blank box. The HTML from "Nav.txt" will function just like it was from that webpage except that it was loaded externally. If every webpage loads its navigation bar information from "Nav.txt", then next time I want to change my Navigation bar to add a new menu I would only need to modify one place to affect every one of my webpages.

Now the question I have for you is to help me achieve this magical act. Here is my navigation bar information[http://asodar.com/nav.txt]("http://asodar.com/nav.txt") . This block of HTML would be loaded into this webpage [http://asodar.com/webpage.html]("http://asodar.com/webpage.html")
like it was it's own. The Location of where the "nav.txt" HTML will be placed Is shown when you view the webpage. You can also download my webpage and the text document in the link that follows [http://asodar.com/webpagehelp.zip]("http://asodar.com/webpagehelp.zip") .

I learn everything from looking at other peoples work and attempting to copy it. What I would really find helpful is creating a webpage yourself that implements this, then to link the download to me with your final product. (no viruses please) You can E-mail me at (email removed) ,though if you would like to discuss this more use this forum, so others can learn from this as well.

---

### Post by slavik on 2008-10-12
you need to look into a web programming language such as PHP (it is the most popular).

---

### Post by sinclair86 on 2008-10-12
CSS [cascading style sheets] will allow you to modify multiple elements across pages by how you define it in there as long as you link to the css file ```
<LINK REL=StyleSheet HREF="./name.css" TYPE="text/css" />
```

---

### Post by Bradosia on 2008-10-12
I do use a .css. Do you know what line to add to it?  [http://asodar.com/images/styler.css]("http://asodar.com/images/styler.css")

---

### Post by GavinZac on 2008-10-12
This requires the very basic functions of a programming language. Here it is in one that will mostly likely run on your server, no matter who hosts it: PHP.

```

<html>
<head>
...
</head>
<body>
...

<!-- your navigation bar bit -->
<?php
include_once("nav.txt");
?>
<!-- /end of your nav bar bit -->

...
</body>
</html>
```

---

### Post by drubin on 2008-10-12
> **GavinZac said:**
> 
<?php
include_once("nav.txt");
?>

/me wget servername.com/nav.txt  (Among other txt files that are in plain text.
/me tries servername.com/config.txt as well :) 

Files that should have the extension .php or you will need to also configure your server to not allow plain txt files being view (that would not be a great idea)

---

### Post by Bradosia on 2008-10-12
Special thanks to GavinZac!
It works perfectly in the way I had expected it to work.
I knew it was a simple thing like that, just that it was too simple for anyone to explain :P
And thank you everyone else for leading me to the answer.

---

### Post by Reiger on 2008-10-12
If you are 'just' making static web pages, it is possible to do that -- and probably even maintainable to yourself. But it's bad coding practice to inject PHP blocks in your HTML code or vice versa, especially if you can avoid it. The reason being that if you are modifying 'global' things, this practice coupled to the verbosity (and monstrosity) of HTML will likely make it impossible to find back that PHP needle on which you depend elsewhere in the HTML heystack.

So when practicing this coding style: Keep it really very simple.

---

