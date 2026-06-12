---
title: "regex to grab &lt;div&gt;*&lt;/div&gt; ?"
date: 2008-08-21
forum: Programming Talk
---

### Post by justleen on 2008-08-21
Hey all..

Im running in cirkels with this silly little problem, I hope some of you can break the spell..

I have a bunch of html from a page, and I want everything from one certain div+class in variable.. 

so far, I only manange to do this with to regex replaces (perl syntax, in php)

```
$x='aevrything before opendiv tag<div id=\"contentmiddenbreed\"> stuff i want   </div> everything after  closediv tag';
		
$x =  preg_replace('/^.*.<div id=\"contentmiddenbreed\">/e', '' ,$x);
$x = preg_replace('/<\/div>.*.$/' , '' , $x );

```
this works, but only if the input is on one line...plus, I know this should be do-able in 1 statement...


Any ideas??

---

### Post by scragar on 2008-08-21
php includes the m modifier which let's you do multiline matching.

[php]$x='evrything before opendiv tag
<div id="contentmiddenbreed">
stuff i want
</div>
everything after  closediv tag
<div>lies :P</div>';

echo preg_replace("/<div class=\"contentmiddenbreed\">(.*?)</div>/im", "$1", $x);
[/php]

---

### Post by LaRoza on 2008-08-21
Why are you using RE's on HTML? It would be much easier using an API for that. Since an ID must be unique, you can use the DOM (among others) to get that in one line. document.getElementById("contentmiddenbreed") and handle it from there?

---

### Post by slavik on 2008-08-21
> **LaRoza said:**
> Why are you using RE's on HTML? It would be much easier using an API for that. Since an ID must be unique, you can use the DOM (among others) to get that in one line. document.getElementById("contentmiddenbreed") and handle it from there?
must not is ... (I've seen cases where they aren't)

---

### Post by LaRoza on 2008-08-21
> **slavik said:**
> must not is ... (I've seen cases where they aren't)

There is that, but then the OP shouldn't call the page "HTML" if it isn't.

---

### Post by howlingmadhowie on 2008-08-21
> **scragar said:**
> php includes the m modifier which let's you do multiline matching.

[php]$x='evrything before opendiv tag
<div id="contentmiddenbreed">
stuff i want
</div>
everything after  closediv tag
<div>lies :P</div>';

echo preg_replace("/<div class=\"contentmiddenbreed\">(.*?)</div>/im", "$1", $x);
[/php]

a word of warning. how greedy is the regexp implementation in php?

---

### Post by scragar on 2008-08-21
> **howlingmadhowie said:**
> a word of warning. how greedy is the regexp implementation in php?

the *? cancels out the greedy mode.

---

### Post by justleen on 2008-08-21
I'm reading a remote generate php file, so the end output is "plain html"
Since I started using fopen to read the page, I ended up using a regex to grab what i wanted...

Thanks a buch for the replies though!
with your help I ended up with:
```
$x =  preg_replace('/^.*.(<div id=contentmiddenbreed>.*.<div>).*.$/im', '\\1' ,$x);
```

---

### Post by slavik on 2008-08-21
> **LaRoza said:**
> There is that, but then the OP shouldn't call the page "HTML" if it isn't.
and the browser shouldn't render it I presume (I am not an HTML standards expert by any stretch of imagination), but we do have IE and Firefox and Opera and Safari ...

---

### Post by scragar on 2008-08-21
> **justleen said:**
> I'm reading a remote generate php file, so the end output is "plain html"
Since I started using fopen to read the page, I ended up using a regex to grab what i wanted...

Thanks a buch for the replies though!
with your help I ended up with:
```
$x =  preg_replace('/^.*.(<div id=contentmiddenbreed>.*.<div>).*.$/im', '\\1' ,$x);
```

```
.*.
``` is the same as ```
.+
```
except .+ is slightly faster and reads easier.

PS:
your not closing the tag right:
```

$x =  preg_replace('/^.+(<div id=contentmiddenbreed>.+<\/div>).+$/im', '\\1' ,$x);

```and again, double check the notes on greedy replacing, you can reduce the overall work of the regExp just by switching greedy off for your match.

---

### Post by justleen on 2008-08-21
cheers...

but.. Im still not able to read multiline, even if I end with /im?

```

<?php
$x='alles voor de opendiv tag<div id=contentmiddenbreed> 
meuk tussen de tags   </div> 
alles achter de sluitdiv tag';
		
$x =  preg_replace('/^.+(<div id=contentmiddenbreed>.+<\/div>).+$/im', '\\1' ,$x);

print_r($x);


?>
```

---

### Post by scragar on 2008-08-21
[http://php.net/manual/en/reference.pcre.pattern.modifiers.php](http://php.net/manual/en/reference.pcre.pattern.modifiers.php)

My mistake, you need the **s** modifier as well so . can be a new line as well.

---

### Post by justleen on 2008-08-21
Yes!  Thank you!

_o_

---

### Post by badperson on 2008-08-21
I would grab it by

s/<div>(.*?)<\/div>/whatever you're replacing/g;

---

### Post by howlingmadhowie on 2008-08-21
> **scragar said:**
> the *? cancels out the greedy mode.

good to know :)

however, consider the following case:

```
<div>
  <div id="contentmiddenbreed">
    <h2>hello world</h2>
    <div>i am a div</div>
  </div>
</div>
```

the two ways i can see of handling this case at the moment are:
counting opening and closing divs (boring)
or
making a tree out of it (which is, as LaRoza pointed out, what you should be doing anyway).

on a different note, wouldn't firefox be cool, if it could read dom trees in straight away, something like:

```

html:
  children: 
    head:
       children:
         title: name: mypage
         script: src: script.js
                 type: text/javascript
    body:
       children
         h2:
           class: myh2
           value: hello world
         div:
           id: mydiv
           children:
             text: i am in a div
             a:
               href: mylink.html
               children:
                 text: click me!

```

maybe i'll write some javascript applet to interpret and parse that :)

---

### Post by scragar on 2008-08-21
The code is PHP, so javascript isn't any good for it's intended use if I am correct, this might work, although I am unsure(and haven't tested it):
[php]
$x='evrything before opendiv tag
<div id="contentmiddenbreed">
stuff i want
</div>
everything after  closediv tag
<div>lies :P</div>';

$doc = new DomDocument;
// needed to grab IDs
$doc->validateOnParse = true;
$doc->loadHTML($x);
$ele = $doc->getElementById('contentmiddenbreed');

$innerHTML=preg_replace('/^<[^>]*>(.*)<[^>]*>$/',"\\1",DOMElement_getOuterHTML($doc,$ele));
[/php]

---

### Post by LaRoza on 2008-08-21
> **slavik said:**
> and the browser shouldn't render it I presume (I am not an HTML standards expert by any stretch of imagination), but we do have IE and Firefox and Opera and Safari ...

That is what bothers me. Browsers are the only apps that allow very faulty code. Their acceptance has caused weird behavior in various browsers and resulted in sloppy coders. They should be jailed.

---

