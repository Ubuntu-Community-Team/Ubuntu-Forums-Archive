---
title: "Javascript giving different results in IE and Firefox"
date: 2009-08-03
forum: Programming Talk
---

### Post by phenest on 2009-08-03
Ok guys and gals. I got me an html issue whereby a bit of javascript works perfectly in Firefox, but doesn't work in IE.

The web page cane be found [here]("http://www.scobble.me.uk/rand_pw_gen.html"). The problem is with the Custom Character List. It works in Firefox in Ubuntu (and Windows I believe), but not in IE in Vista (not tested other versions of IE).

The javascript can be viewed [here]("http://www.scobble.me.uk/js/rand_pw_gen.js").

Comments please.

---

### Post by phenest on 2009-08-03
I guess this is just me thinking out loud. But in doing so, found the answer, although I don't know why IE had the problem.

It seems that text from a text box can't be treated as an array in IE. You have to treat it as a string. So, instead of:
```
text=f.chars.value
for(i=0;i<text.length;i++)
{
do something with text[i]
}
```
I had to use:
```
text=f.chars.value
for(i=0;i<text.length;i++)
{
do something with **text.charAt(i)**
}
```
Firefox has no problems with either of these methods, but IE returned 'undefined' for text[i] where text is a string.

Could this be IE not supporting javascript as well as it could, or at least, as well as other browsers?

---

### Post by Reiger on 2009-08-03
No. You appear to be requesting a primitive String value then try to rely on implicit type conversions or equalities which simply may not hold true.

---

### Post by phenest on 2009-08-03
What started off as 2 declared arrays in the script, I then added a 3rd option which took a string from a text box. I hadn't even thought about whether I was trying to treat a string as an array because it simply worked in Firefox.

When it didn't work in IE, my thoughts were about whether the text from the text box was the problem. but what I don't understand is why Firefox didn't have a problem with it. Or is it that IE is that much stricter?

I've already had to change the html code for the button, again, because the original code worked in Firefox but not in IE.

Of course, that still hasn't stopped IE from complaining about errors on the page. Once I've made sense of it, I'll try to fix that.

---

### Post by bobince on 2009-08-03
> **phenest said:**
> what I don't understand is why Firefox didn't have a problem with it. Or is it that IE is that much stricter?

charAt() is a standard method documented in ECMA-262 Third Edition, and historically going all the way back to JavaScript 1.0. It's the right thing to use, as the standard sets out what you can expect to work across different implementations include Microsoft's JScript.

The ability to read 'string'[subscript] is a non-standard convenience method introduced by JavaScript 1.5, the extended version of JavaScript introduced by Mozilla. (Current versions of Firefox are now up to JavaScript 1.8.) As with all non-standard methods, you can't rely on it being there&#8201;—&#8201;although it *is* now also supported in IE8.

Other things: you should be using ‘var’ to declare your functions' variables to be local. For example:

```
function generate() {
    var f=document.getElementById("keygen");
    var pw='';
    ...
```

and:

```
for(var i= 0; i<array.length; i++) ...
```

Otherwise, ‘f’ and ‘i’ are global variables, which can cause no end of confusion when one function scribbles over another function's variables. JavaScript is a bit annoying in forcing you to write ‘var’ where other languages would just assume you mean a local variable.

```
if(f.pw[2].checked & custom.length<2)
```

Best to use && for boolean ops. & is a bitwise operator, which may or may not do the same thing depending on what exactly your arguments are.

Finally, you're declaring an XHTML doctype, but then using the non-well-formed shortcut ‘checked’. For XML documents that should be ‘checked="checked"’.

---

### Post by phenest on 2009-08-03
Er, all I want to know is why these browsers react differently to code.

---

### Post by bobince on 2009-08-04
> **phenest said:**
> all I want to know is why these browsers react differently to code.

Because they're completely different browsers, written by different teams at different times with different goals? It's amazing as much is the same cross-browser as it is.

Really IE should have alerted you straight away to 'string'[index] being bogus. But one of the most unfortunate characteristics of JavaScript is its tendency to sweep errors under the rug&#8201;—&#8201;in particular returning ‘undefined’ for things that don't exist instead of an exception, making it hard to spot what's gone wrong in cases like this.

---

### Post by phenest on 2009-08-04
> **bobince said:**
> Because they're completely different browsers, written by different teams at different times with different goals?

This is the bit I don't understand. Shouldn't they all have the same goals? Shouldn't HTML and Javascript be 'handled' in the same way. I know some browsers are a 'bit behind' when it comes to new features, and maybe rendering is slightly different, but the code remains the same. So, shouldn't the results be the same?

Here's another example (it's how my code was before I changed it). The 'Generate' button didn't work in IE.
```
<form action="generate()" id="keygen">
...
<button>Generate</button>
```
This changed to:
```
<form id="keygen">
...
<input type="button" value="Generate" onclick="generate()" />
```
The latter works in both browsers, whereas the first only works in Firefox. :confused:

---

### Post by Mirge on 2009-08-04
> **phenest said:**
> This is the bit I don't understand. Shouldn't they all have the same goals? Shouldn't HTML and Javascript be 'handled' in the same way. I know some browsers are a 'bit behind' when it comes to new features, and maybe rendering is slightly different, but the code remains the same. So, shouldn't the results be the same?

Here's another example (it's how my code was before I changed it). The 'Generate' button didn't work in IE.
```
<form action="generate()" id="keygen">
...
<button>Generate</button>
```This changed to:
```
<form id="keygen">
...
<input type="button" value="Generate" onclick="generate()" />
```The latter works in both browsers, where the first only works in Firefox. :confused:

For that example, I would have used the "onsubmit" event instead.

But, yes, browsers are different and their implementations are different unfortunately. It's one of the big reasons why I love [jQuery]("http://www.jquery.com/"), which hides those differences, among other things.

---

### Post by bobince on 2009-08-05
> **phenest said:**
> Shouldn't they all have the same goals? Shouldn't HTML and Javascript be 'handled' in the same way.

Being able to index strings is an improvement. Most likely it will be specified in a future draft of the ECMAScript standard and all browsers will behave that way in the future. If Mozilla hadn't introduced the capability for fear of incompatibility, programmers in the future would be worse off.

If we'd always followed the strategy of ‘behaving the same way’, there'd be no stylesheets, no AJAX, no DOM scripting; we'd be stuck with the feature set of Netscape 2.0 forever and many of the features of web sites you use every day would be completely impossible to create.

Even when browsers are attempting to hit exactly the same standards, they will always fail, because that's what programming is like. The only way for all browsers to behave the same is if everyone used exactly the same browser code. And then we'd have no Firefox, no IE, no Netscape even... we'd be using Mosaic. And the web as we know it today, which thrives on innovation and development, would not exist.

> Here's another example (it's how my code was before I changed it). The 'Generate' button didn't work in IE.

That code doesn't work in Firefox either. ‘action="generate()"’ means, when you click a submission button, navigate to a relative URL. So you'd end up going to somewhere like ‘[http://www.example.com/something/generate()’](http://www.example.com/something/generate()’). There is no connection to JavaScript there at all, on any browser.

Maybe you meant ‘action="javascript:generate()"’? That would work on both browsers, but it's a hideously nasty hack; it doesn't make sense to say ‘submit this form to a javascript: URL’ and there is no specification that says what should happen if you try. javascript: URLs in general are a dreadful mistake and should never be used in a web page.

If that's what you meant, what would actually stop the code working in IE would be the ‘button’. If you want a submit button, the original and best thing to use is ‘input type="submit"’. If you do use a ‘button’ you need to specify the type: ‘button type="submit"’ if you want it to submit the form, or ‘button type="button"’ for one that just sits there. If you omit ‘type’, the browser guesses; it is a long-standing HTML bug in IE that it guesses wrong (according to spec, it should guess ‘submit’). This is fixed in IE8.

---

### Post by phenest on 2009-08-08
> **bobince said:**
> Maybe you meant ‘action="javascript:generate()"’? That would work on both browsers, but it's a hideously nasty hack; it doesn't make sense to say ‘submit this form to a javascript: URL’ and there is no specification that says what should happen if you try. javascript: URLs in general are a dreadful mistake and should never be used in a web page.

That is what I meant, sorry. But according to validator.w3.org:
```
Line 38, Column 21: required attribute "action" not specified
<form id="keygen">
The attribute given above is required for an element that you've used, but you have omitted it. For instance, in most HTML and XHTML document types the "type" attribute is required on the "script" element and the "alt" attribute is required for the "img" element.
```
...so I'm confused about the right way to do it.

> **bobince said:**
> If that's what you meant, what would actually stop the code working in IE would be the ‘button’. If you want a submit button, the original and best thing to use is ‘input type="submit"’. If you do use a ‘button’ you need to specify the type: ‘button type="submit"’ if you want it to submit the form, or ‘button type="button"’ for one that just sits there.

Thanks. I'll look into that.

> **bobince said:**
> If you omit ‘type’, the browser guesses; it is a long-standing HTML bug in IE that it guesses wrong (according to spec, it should guess ‘submit’). This is fixed in IE8.

Ah, so that's what was happening. Didn't realise that.

---

### Post by gjoellee on 2009-08-08
> **phenest said:**
> Er, all I want to know is why these browsers react differently to code.

IE has always been "reading" code differently, and that causes a lot of problems for website developers. Why they act differently is because they are written differently.

---

### Post by bobince on 2009-08-08
> **phenest said:**
> so I'm confused about the right way to do it.

Use a form with ‘method’ and ‘action’ if you want the results to get submitted to a server-side script.

For just some standalone fields on a web page, on the other hand, you can do without the form element completely. The script would have to be changed to retrieve the input elements using document.getElementById() directly instead of going through the HTMLFormElement object's collections (since there is now no form element to script on), but then this is probably the best approach anyway.

(In the bad old days of Netscape 4.0, the form-based scripting interface was the only one available, and indeed fields outside a form didn't work at all. But that era is, thankfully, long gone.)

---

### Post by phenest on 2009-08-10
> **bobince said:**
> For just some standalone fields on a web page, on the other hand, you can do without the form element completely. The script would have to be changed to retrieve the input elements using document.getElementById() directly instead of going through the HTMLFormElement object's collections (since there is now no form element to script on), but then this is probably the best approach anyway.

I didn't even think of that. Thanks

---

### Post by hessiess on 2009-08-10
Just use server side scripting, its much less problematic, And if you must use JavaScript, use JQuery.

This password generator will not generate truly sccure paswords as Math.random() may not be verry random depending on how the browser implements it, and also there is nothing to prevent it generating the same password twice.

If you want to know how truly random passwords can be generated, check [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm).

---

