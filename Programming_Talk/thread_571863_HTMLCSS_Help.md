---
title: "HTML/CSS Help"
date: 2007-10-09
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-09
I am currently working on a simple webpage for a college class of mine. I have limited experience designing webpages so these questions may seem pretty simple. Hopefully the answers will be simple also!

Here is my page currently:

[http://www.personal.psu.edu/sjc5002](http://www.personal.psu.edu/sjc5002)

I did it a while ago by following a CSS tutorial but that was a few months ago. Today I started updating it and adding in some new pages. I would like to change a few things about the style.

1) a)Making everything centered. I'd like to have everything moved over to the center of the page instead of being on the left side of the page.
b) If I do center the page I'd like to make the area around what I have now a different color. So where the navigation bar is and wherever I have writing right now I'd like to keep as a white background, but everywhere else I'd like to have a different color.


2) I think I need to add something to the left side of the page because it seems a little boring. I might just add a little block with some quick information about me. How could I do this?

Thanks for the time.

edit--

Oops! I forgot to attach the css code.

```

body {

  	padding-left: 12em;
	padding-right: 18em;

	font-family: courier, "Times New Roman",

          Times, serif;

    color: #000066;

    background-color: #FFFFFF }

ul.navbar {

	 list-style-type: none;

    padding: 0;

    margin: 0;

    position: absolute;

    top: 4em;

    left: 1em;

    width: 10.3em }

ul.navbar li {

    background: #000066;

    margin: 0.5em 0;

    padding: 0.3em;

    border-right: 0.8em solid #CCCCCC}

  ul.navbar a {
	font-family: "verdana";

    text-decoration: none }

  a:link {

    color: #CCCCCC }

  a:visited {

    color: #CCCCCC }

h1 {

    font-family: Helvetica, Geneva, Arial,

          SunSans-Regular, sans-serif }

address {

    margin-top: 1em;

    padding-top: 1em;

    border-top: thin dotted;
	text-decoration: none }

```

---

### Post by dickohead on 2007-10-09
Try searching the web for:
CSS center div
and
CSS three column layout

---

### Post by LaRoza on 2007-10-10
If you are using Firefox, use the Web Developer Toolbar Extension, and look at my site:

[http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

It may have all the CSS you want for you own site, you can adapt the CSS for you own needed.

---

### Post by Samhain13 on 2007-10-10
Everything centred?

Try giving the body margin: 0px and padding: 0px first.
Wrap everything up in a div called, "content" and give it a width say 720px. Then style it with margin: auto.

Snippet:

```

body {
  margin : 0px ;
  padding : 0px ;
}

#content {
  width : 720px ;
  margin : auto ;
}

```

[HTML]
<body>
  <div id="content">
    ...put everything here...
  </div>
</body>
[/HTML]

...or something to that effect. :D

---

### Post by TreeFinger on 2007-10-10
Right now the code displays perfectly in Firefox but in IE 7 it messes up. I am not sure why. What do I need to change?

---

### Post by bigboy_pdb on 2007-10-10
If you don't have a DOCTYPE tag at the top of your document, you should add one. Without it Firefox, Internet Explorer, and other browsers won't know how to interpret your code.

For example, for strict XHTML use:
```

<!DOCTYPE html 
	PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

```

You should also check that your HTML and CSS code are both valid. You can do that at the following URL:
[http://validator.w3.org/](http://validator.w3.org/)

You may still find that your styles don't look the same in both browsers (or in other browsers). If this is the case then try adjusting the margins and padding for the elements. For example, if you have the following HTML and CSS:

HTML:
```

<div id="tag1">
	<div id="tag2">
		CONTENTS
	</div>
</div>

```

CSS:
```

#tag2 {
	margin: 10px;
}

```

then you can also use the following CSS to get the same effect:

CSS:
```

#tag1 {
	padding: 10px;
}

```

**[EDIT]**
You can change background colours by using the attribute "background-color". The colour specified can be the name of a colour (such as "blue" or "white"), the hexadecimal code for the colour (such as "#0000AA" or "#FFFFFF"), or it could be specified using rgb(RED,GREEN,BLUE) where RED, GREEN, and BLUE are numbers between 0 and 255 (such as "rgb(0,0,170)" or "rgb(255,255,255)". Also, temporarily changing the background colours of elements can help you to see what space they're taking up.

Regarding the adding of the biography or some other section, you can create the section and use the "float" attribute on it and the other contents to make it float to the left or right side of the page and so that the other contents are stacked onto it. The only problem with doing this is that you would have trouble adjusting the contents so that they are centred.
**[/EDIT]**

---

### Post by Samhain13 on 2007-10-11
Try this. What I did was:

1. Created a "container" DIV to limit the width of your content and so you can place everything at the middle of the page.
2. Fixed up your logo since you have it inside a UL but not inside an LI.
3. Created a "content" DIV to separate page content from your navigation bar, floated the navbar left and and gave content the appropriate margin so that text will not go under navbar.
4. Fixed mixed-case code in the ADDRESS element.

Take bigboy's advice too, validate your pages because in many cases, CSS rendering anomalies are caused by malformed markup.

I hope that helped. Cheers! :)


[HTML]
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html>

  <head>
    <title>Your Title Here</title>
    
    <style type="text/css">
      <!--
        body {
          color: #000066 ;
          
          margin : 0px ;
          padding : 40px 0px ;
        }
        
        h1 {
          font-family: Helvetica, Geneva, Arial, SunSans-Regular, sans-serif
        }
        
        address {
          border-top : 1px #000066 solid ;
          padding-top : 10px ;
        }
        
        #container {
          width : 720px ;
          
          margin : auto ;
        }
        
        #content {
          margin-left : 200px ;
        }
        
        #navbar {
          width : 175px ;
          
          list-style-type : none ;
          
          float : left ;
          margin : 0px ;
          padding : 0px ;
        }
        
          #navbar li {
            width : 152px ;
            
            background : #000066 ;
            border-right: 15px #CCCCCC solid ;
            margin : .5em 0em ;
            padding : 5px 10px ;
          }
          
          #navbar #logo {
            border : 0px ;
            padding : 5px 0px 5px 20px ;
          }
          
          #navbar a:link, #navbar a:visited {
            color : #fff ;
            text-decoration : none ;
          }
      //-->
    </style>
    
  </head>
  
  <body>
    <div id="container">
    
      <!-- Site navigation menu -->
      <ul id="navbar">
        <li id="logo"><img src="http://www.personal.psu.edu/sjc5002/images/small_psu.gif"></li>
        <li><a href="index.html">Welcome</a></li>
        <li><a href="major.html">Major</a></li>
        <li><a href="classes.html">Classes</a></li>
        <li><a href="links.html">Links</a></li>
      </ul>
      
      <div id="content">
        
        <h1>Sam Chodur's E-Portfolio, Welcome!</h1>
        
        <p>Hello and welcome to my e-portfolio.</p>
        
        <p>I'd first like to tell you what you will find here on my webspace.</p>
        
        <p>Here you will be able to find information about my College Education at Penn State University. Use the navigation bar on the left side of the page to hopefully find what you are looking to learn about me. If you have any suggestions for my page please send me an e-mail. You can do that by clicking my name at the bottom of any page.</p>
        
        <address>
          Last Updated: 9 Oct 2007<br>
          by <a href="mailto:sjc5002@psu.edu">Samuel J. Chodur Jr.</a>
        </address>
      
      </div>
    
    </div>  
  </body>

</html>

[/HTML]

---

