---
title: "JavaScript onclick help"
date: 2008-09-05
forum: Programming Talk
---

### Post by Verminox on 2008-09-05
**[color=red]This issue has been solved. I realised the answer myself. Thanks anyway.[/color]**

Hey, I am writing some simple code in JavaScript which is giving me a bit of trouble. 

I have a bunch of links (<a> elements), but if I click on the link, I want to execute a JS function and not actually redirect the page. The reason I have the links is for degradation when JS is disabled or unavailable.

The simplest way I know is to do this:

```
<a id="foo" href="foo.html" onclick="showImage('foo'); return false;">FOO</a>
```

I know that **return false** will obstruct the redirection of the link, and showImage() will be executed without going to foo.html.

However, my problem arises when I remove this event handler from the HTML and add it to a script.

In this case even though showImage() is executed I am also redirected to foo.html which I want to avoid. I don't know how to stop the event from causing a link redirection when setting the event handler from the script itself. Help is appreciated.

Edit: Got it

```
var foo = document.getElementById('foo');
foo.onclick = function(){ showImage('foo'); return false; }

```

---

