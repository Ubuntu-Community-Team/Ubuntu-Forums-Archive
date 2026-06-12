---
title: "Help with CSS and XHTML"
date: 2010-06-30
forum: Programming Talk
---

### Post by MadCookie on 2010-06-30
I am creating a website at the moment, but this is the firs one I make from scratch.
I have made a rough mockup (1st attatchment) of something similar of what I am trying to create. The colours are just showing different parts of the the website.

**My first challange:**
I am having some difficulties with the main menu. I get this space that i don't want, above and on the sides of the menu:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161963&d=1277906397[/IMG]
How do I eliminate those spaces? The menu code is found below:

**in the index.php:**
```

<div id="menu">
	<div id="nav1">
        <ul>
            <li><a href="#">Forum</a></li>
            <li><a href="#">Wallpapers</a></li> 
            <li><a href="#">Home</a></li>
        </ul>
     <div class="clearer">&nbsp;</div>
    </div>
</div>

```

**in the css:**
```
#menu {
	background: #1D1D1D;
	border-bottom: 5px #D01111 solid;
	height: 50px;
	font-family: sans-serif;
	font-size: 15px;
	
}
#menu ul, #menu li {
	display: inline;
	float: right;
	padding-bottom: 5px;
}
#menu a {
	float: left;
	margin-right: 1px;
	text-align: center;
	text-decoration: none;
}

#nav1 a {
	color: #BBB;
	padding: 10px 12px 12px;
}
#nav1 a:hover {color: #EEE;}
```

---

### Post by MadCookie on 2010-06-30
Solved it by adding margin: -10px, to the left, right and top...:lolflag:

---

### Post by Dragonbite on 2010-06-30
Could it also be fixed with the BODY's top and left, and the div's width?  ```

BODY {
	left:0px;
	top:0px;
     }
#menu {
	background: #1D1D1D;
	border-bottom: 5px #D01111 solid;
	height: 50px;
	font-family: sans-serif;
	font-size: 15px;
	**width:100%**;
	
}

```

---

