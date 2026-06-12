---
title: "silly little html question"
date: 2011-06-02
forum: Programming Talk
---

### Post by dazman19 on 2011-06-02
WHY oh why wont this div display. Gawd

index.php

[PHP]

<html>
    <head>
        <link type="text/css" src="main.css" />
    </head>
    <title>
        test
    </title>
    <body>
        <div class="headersection"></div>
    </body>
    
</html>
[/PHP]

main.css

[PHP]
root { 
    display: block;
}
body {
    background-color: #321321;
}
div.headersection {
    height: 100px;
    width: 100%;
    background-color: #321332;
}
.clear {
    float: none;
    clear:both;
}
[/PHP]

this is like the simpliest thing and for some dumb reason it has take me 20 mins and i still cant figure out why it wont show up!!!

---

### Post by m_duck on 2011-06-02
I'm fairly sure that div elements (and most stuff in CSS) will ignore height properties given in percent without bodgery. The reason it doesn't show up then is that the div is empty, so as far as your browser is concerned, there is nothing to display. If you add a space or something to the div as some content, it should probably display as a character-height box.

Note that I'm far from an expert on the matter so this 'information' may not be technically correct.

---

### Post by PaulM1985 on 2011-06-02
I tried your code.  I think the issue is with loading the css from a different file.  I am not too sure about css myself, but I found if I pasted it into the html it worked.

```

<html>
    <head>
        <style type="text/css">
root { 
    display: block;
}
body {
    background-color: #321321;
}
div.headersection {
    height: 100px;
    width: 100%;
    background-color: #321332;
}
.clear {
    float: none;
    clear:both;
}  
</style>
   </head>
    <title>
        test
    </title>
    <body>
        <div class="headersection"></div>
    </body>
    
</html>  

```

Have a look to see if you are doing the right thing to load your css file.  Note I am using <style> rather than <link>.

Paul

---

### Post by benson444 on 2011-06-02
Like PaulM said, it's not loading the css file. The link tag doesn't have an *src* attribute, it should be *href*. Also, the *rel* attribute is required.

It needs to be something like:

```
<link type="text/css" rel="stylesheet" href="main.css" />
```

---

### Post by ThatCoolGuy220 on 2011-06-02
add:

position:absolute.

to that then you can move it around

---

