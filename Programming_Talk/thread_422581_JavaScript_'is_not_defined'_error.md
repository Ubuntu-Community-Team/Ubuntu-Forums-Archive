---
title: "JavaScript 'is not defined' error"
date: 2007-04-25
forum: Programming Talk
---

### Post by Ferio on 2007-04-25
Hi, I'm just learning some JavaScript, and FireBug tells me there's an error that appears to be quite simple, but that I can't seem to fix. It's a script to learn the *for...in* loop by looping through the properties of the *document* object. The JavaScript code is this:
```

document.write('<h1>document properties</h1>');
for(var property in document) {
    document.write('<p>');
    // There was some error here about some unknown property, so I try-catched it
    try {
        document.write('document.' + property + ' = ' + document[property] + '<br />');
    }
    catch(e) {
        document.write('Unknown');
    }
    document.write('</p>');
}

```And the XHTML code is this (it's just my XHTML 1.1 template with an *onload* attribute in the *body* element):
```

<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/css" href=""?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
    <head>
        <title>Objects</title>
        <base href="" />
        <link href="" rev="made" />
        <link rel="stylesheet" href="" type="text/css" media="screen" />
        <link rel="home" title="" href="" />
        <meta http-equiv="content-script-type" content="text/javascript" />
        <meta http-equiv="content-type" content="application/xhtml+xml; charset=utf-8" />
        <meta http-equiv="expires" content="-1" />
        <meta http-equiv="pics-label" content='(pics-1.1 "http://www.icra.org/ratingsv02.html" labels generic true for "" ratings (nz 1 vz 1 lz 1 oz 1 cz 1) "http://www.rsac.org/ratingsv01.html" labels generic true for "" ratings (n 0 v 0 l 0 s 0)' />
        <meta name="Author" content="" />
        <meta name="Description" content="" />
        <meta name="Keywords" content="" />
        <meta name="Robots" content="all" />
        <script src="objects.js" type="text/javascript"></script>
    </head>
    <body onload="objects.js">
    </body>
</html>

```The error that FireBug launches is this:
> 
objects is not defined (objects.htm) line 1
onload(load )
It seems it's an error in the XML declaration at the top of the XHTML file, but I don't know how to fix it, although I've googled it.

Any help will be appreciated,

---

### Post by LaRoza on 2007-04-25
It has nothing to do with the XML declaration.

---

### Post by LaRoza on 2007-04-25
I do not know if you can use the write method in an external ECMAScript file. I use the DOM, so I don't use that method.

[http://www.domscripting.com/book/](http://www.domscripting.com/book/)

This book is very good, especially if you want to use XML or XML compliant web code, like  XHTML.

---

### Post by LaRoza on 2007-04-25
Your JS file will be loaded once the parser gets to the &lt;script src=...tag&gt; tag. You are further onloading it in the body, which doesn't make sense, with the onload event handler, you can call functions, but not external documents.

---

### Post by Ferio on 2007-04-25
LaRoza, I think there's no need to be so rude as to asking me if I have programmed before as if I were some kind of dork; I just had a simple doubt that you've barely answered, but I'll answer yours:
[LIST=1]
[*]I came here asking about a tiny JavaScript doubt and you've redirected me to some tutorials that don't answer my doubt. I've got 3 books yet on JavaScript, and I wanted only to know where I have gone wrong. Maybe it was just FireBug getting picky on my code, but I'd like to know about it.
[*]I know how to reference a stylesheet, both using XML and XHTML. I'm not specifying where it is because there's no CSS involved in this case, and I'm using both ways of referencing it because of the issues some browsers have with the XHTML 1.1 DOCTYPE. In fact, I work as a front-end accessibility consultor, and that's why I need to learn JavaScript, not XHTML or CSS, which I master yet. And as I've said before, I don't need another book, just an answer I couldn't find looking in these forums or using Google.
[*]I didn't know that you can only call functions when using events, so thank you very much, since I've never used events before; as you said, the error was just that I was calling the script in the onload event, if I don't do this, it works perfectly. And to answer your question: yes, I have programmed before, my previous job was doing web services using J5EE and PHP 5, and before that I had one doing .NET, so I think it wasn't a programming skills problem, just an I-don't-master-events-yet one.[/LIST]Well, thank you anyway, now our doubts are solved.

PS: I'm sorry if your intention was not being so rude, but that's what I've understood from your answers.

---

### Post by LaRoza on 2007-04-25
Sorry, I am in school and in class and answering between distractions. 

I was not trying to be rude and apologize giving such an impression. I should have asked what your experience was, so I could further answer your question (that was my intention). 

I had trouble viewing the page because the schools monitor has low resolution, it is difficult to read anything all at once, that is why I had brief and numerous responses.

I shall try to better my responses, to me, it is easier to talk to computers than it is to talk to humans. (Humans don't usually throw exceptions, or strictly enforce syntax:( )

---

### Post by Blacktalon on 2007-04-27
Do you not have a function for you JavaScript?


I have a few Ideas on what might be causing this problem.

1.  No JS function is called.  
2.  You seem to be trying to call the whole JS file, instead of an function within the file,  I don't think this is needed.

Since you have 
>  <script src="objects.js" type="text/javascript"></script>

I don't see any reason why you should have 
> onload="objects.js"

When you call your onload you should be calling a function not the entire file.

Reason I say this is cause when you ```
<script src="objects.js" type="text/javascript"></script> 
```
that is calling all the functions of the file into the head, that is equvient to doing the JS code inside the HTM file.  Then when you do the onload call it will call the function you set it to.

Like I said now you are just trying to call the entire file, not a function. 

Give it a try, I could be incorrect of course.  But I think this can help solve your problem.

I hope you could understand what I have writen, I am kinda tired, and having a hard time putting into typed words on what I am thinking.

Good Luck,
~BT

---

### Post by bluevoodoo1 on 2007-04-29
> **Blacktalon said:**
> 

When you call your onload you should be calling a function not the entire file.


Agreed. When you use onload you are usually calling a function rather than the file name:



contents of alert.js:

```

function alertFunction() {
alert('Hello');
}

```

your page:

```

<head>
<script src="alert.js" type="text/javascript"></script>
</head>

<body onload="alertFunction()">
```

---

### Post by Ferio on 2007-05-12
LaRoza, I want to apologize for my behaviour, I wasn't having my best day and I think I overreacted. I'm very sorry, and I thank you very much for your interest in answering me. I'm mastering JS slowly, but I'll win in the end ;)

---

### Post by Ferio on 2007-05-12
Thanks, Blacktalon and BlueVoodo, I figured it out in the end. I find scripting languages quite hard yet, but I'm improving myself.

---

