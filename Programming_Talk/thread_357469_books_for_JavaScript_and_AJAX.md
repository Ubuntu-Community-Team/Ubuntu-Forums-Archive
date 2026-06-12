---
title: "books for JavaScript and AJAX?"
date: 2007-02-09
forum: Programming Talk
---

### Post by RedSquirrel on 2007-02-09
Hi all,

I am looking for some good books to learn/master JavaScript and AJAX.

I am familiar with C/C++ and Java, and I have more recently picked up (X)HTML and CSS.


I have read elsewhere that the following books are pretty good:

(1) "JavaScript - The Definitive Guide, Fifth Edition" by David Flanagan (O'Reilly)

(2) "Ajax in Action" by Dave Crane and Eric Pascarello with Darren James (Manning)


Does anyone have an opinion about these books and/or suggestions for other books and resources?

Thanks for any responses. :)

---

### Post by phossal on 2007-02-10
Flanagan's book is pretty good. For anyone who doesn't have a solid grasp of Javascript or the DOM, I can't imagine a better reference. While "In Action" was a best seller for 2006, I can't think of a better way to waste paper. It is, in many ways, a how-to book on general programming geared toward people with *some* web experience and very little other programming experience. For example, how many chapters on *refactoring* does a book need? If you think  the tricks used in late 2005 are still relevant, or you want to make double-combo scripts, then you might read it. Otherwise, get yourself the Rico and Prototype libraries and leave "In Action" low enough on your to-do list that you never get to it.

---

### Post by kvorion on 2007-02-10
Javascript - The Definitive Guide is a pretty good book. For learning ajax, I havent used any book as yet. The best resources are found online. I started off from [here]("http://developer.mozilla.org/en/docs/AJAX")

Even for javascript, you can find loads of tutorials online.

---

### Post by daz4126 on 2007-02-10
DOM Scripting by Jeremy Keith and The Javascript Anthology by Cameron Adams and James Edwards. Both excellent (but not much AJAX).

see:

[http://domscripting.com/]("http://domscripting.com/")

DAZ

---

### Post by yaaarrrgg on 2007-02-10
For Ajax, I was happy with the book  "Fundamentals of Ajax" (Ryan Asleson and Nathaniel T. Schutta.  Apress 2006.)  At the very least it will point you to a couple libraries to research more.   Really, there's not much to Ajax ... it's not even a w3c standard.

---

### Post by RedSquirrel on 2007-02-10
> **daz4126 said:**
> DOM Scripting by Jeremy Keith and The Javascript Anthology by Cameron Adams and James Edwards. Both excellent (but not much AJAX).

see:

[http://domscripting.com/](http://domscripting.com/)

DAZ



It seems Keith has an AJAX book coming out in a couple of days. :)

[http://bulletproofajax.com/](http://bulletproofajax.com/)

---

### Post by RedSquirrel on 2007-02-10
> **yaaarrrgg said:**
> For Ajax, I was happy with the book  "Fundamentals of Ajax" (Ryan Asleson and Nathaniel T. Schutta.  Apress 2006.)  At the very least it will point you to a couple libraries to research more. 


Minor correction: I think you meant "Foundations of Ajax".

> Really, there's not much to Ajax ... it's not even a w3c standard.

Is there really not that much to it? I've heard it's kind of complicated...

---

### Post by RedSquirrel on 2007-02-10
> **phossal said:**
> Flanagan's book is pretty good. For anyone who doesn't have a solid grasp of Javascript or the DOM, I can't imagine a better reference. While "In Action" was a best seller for 2006, I can't think of a better way to waste paper. It is, in many ways, a how-to book on general programming geared toward people with *some* web experience and very little other programming experience. For example, how many chapters on *refactoring* does a book need? If you think  the tricks used in late 2005 are still relevant, or you want to make double-combo scripts, then you might read it. Otherwise, get yourself the Rico and Prototype libraries and leave "In Action" low enough on your to-do list that you never get to it.

Thanks for your opinion. I had wondered if the "In Action" book was a little dated. Of course, that sounds a little odd given that it's not really *that* old yet, but things do change quickly!

---

### Post by RedSquirrel on 2007-02-10
> **kvorion said:**
> Javascript - The Definitive Guide is a pretty good book. For learning ajax, I havent used any book as yet. The best resources are found online. I started off from [here]("http://developer.mozilla.org/en/docs/AJAX")

Even for javascript, you can find loads of tutorials online.

Thanks for the link.

Online tutorials are handy (and cheaper!), but I sort of like to have a book as well. I find it's easier to read a printed page than to always be reading off a screen (of course, I could also print out some tutorials, too!).

---

### Post by yaaarrrgg on 2007-02-10
> **RedSquirrel said:**
> Minor correction: I think you meant "Foundations of Ajax".

Is there really not that much to it? I've heard it's kind of complicated...

Ah good catch! :)  

The core of Ajax is really simple... it's just making use of the (non-standard) XMLHttpRequest javascript object:

```

var xmlHttp; 
 
function createHttpRequest( ) {
    if ( window.AxtiveXObject ){
        xmlHttp = new Microsoft.ActiveXObject( "Microsoft.XMLHTTP" ) ;
    } else { 
        xmlHttp = new XMLHttpRequest()
    } 
} 

```
 
methods of the object:
 
```

    abort() 
    getAllResponseHeaders()
    getResponseHeader( "header" )
    open( "method", "url" [, isRelative] )      //method is GET, POST, ...
    send( content )
    setRequestHeader( "header" , "value" )

```
 
properties of the object
 
```

    onreadystatechange  //callback
    readyState          //1 = loading, 2 = loaded, 3 = interactive, 4 = complete
    responseText        //what the server returns
    responseXML         // " as xml
    status              //HTTP status code, eg, 200 for ok, 404 for not found
    statusText          //the text part of status like "OK"

```
 
It's just a way to pass data back to the browser without reloading the entire page.

---

### Post by RedSquirrel on 2007-02-15
> **yaaarrrgg said:**
> Ah good catch! :)  

The core of Ajax is really simple... it's just making use of the (non-standard) XMLHttpRequest javascript object:

```

var xmlHttp; 
 
function createHttpRequest( ) {
    if ( window.AxtiveXObject ){
        xmlHttp = new Microsoft.ActiveXObject( "Microsoft.XMLHTTP" ) ;
    } else { 
        xmlHttp = new XMLHttpRequest()
    } 
} 

```methods of the object:
 
```

    abort() 
    getAllResponseHeaders()
    getResponseHeader( "header" )
    open( "method", "url" [, isRelative] )      //method is GET, POST, ...
    send( content )
    setRequestHeader( "header" , "value" )

```properties of the object
 
```

    onreadystatechange  //callback
    readyState          //1 = loading, 2 = loaded, 3 = interactive, 4 = complete
    responseText        //what the server returns
    responseXML         // " as xml
    status              //HTTP status code, eg, 200 for ok, 404 for not found
    statusText          //the text part of status like "OK"

```It's just a way to pass data back to the browser without reloading the entire page.



Thanks for the summary. Now I am off to read some reviews of "Information Architecture" (Morville and Rosenfeld)....

---

### Post by broy on 2007-02-15
I would say that there is more than enough Ajax/Javascript resources on the internet. Don't waste money on a book, I bought two and I never use them.

---

### Post by yaaarrrgg on 2007-02-15
> **broy said:**
> I would say that there is more than enough Ajax/Javascript resources on the internet. Don't waste money on a book, I bought two and I never use them.

I've been using the public library lately ... I was surprised to find a better tech section that our local Barnes and Nobles. :)

---

### Post by pmasiar on 2007-02-15
> **RedSquirrel said:**
> I am looking for some good books to learn/master JavaScript and AJAX.

I like HeadFirst series [http://www.oreilly.com/store/series/headfirst.csp](http://www.oreilly.com/store/series/headfirst.csp) for learning programming stuff - excellent reading, not boring. After you get your feet wet (or head :-) ) you can continue with some expert book, but you will have better idea how parts fit together. O'Reilly books are above average, and this series is excellent. It would be my first choice to dive into new subject.

---

### Post by Mirrorball on 2007-02-15
I recommend "ppk on Javascript." ppk is the owner of [http://www.quirksmode.org/](http://www.quirksmode.org/)

---

### Post by RedSquirrel on 2007-02-17
Many thanks to everyone for the replies. Your responses were very helpful. :)

---

