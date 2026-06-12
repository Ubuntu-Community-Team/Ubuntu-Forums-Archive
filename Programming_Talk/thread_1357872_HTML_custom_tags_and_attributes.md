---
title: "HTML custom tags and attributes"
date: 2009-12-17
forum: Programming Talk
---

### Post by Yuzem on 2009-12-17
Does anyone know if there is any bad consequence in using custom tags and attributes.
I am coding an application and it makes more sense to use toolbar or icon instead of div, ul etc...

For example, instead of this:
```

<div class=toobar>
  content here
</div>

<ul class="icons s128">
  <li class=icon></li>
  <li class=icon></li>
  <li class=icon></li>
  <li class=icon></li>
</ul>

```

This:
```

<toobar>
  content here
</toolbar>

<icons size=128>
  <icon></icon>
  <icon></icon>
  <icon></icon>
  <icon></icon>
</icons>

```

---

### Post by Can+~ on 2009-12-17
Swap the css for:

```
ul."icons s128"
{

}

ul."icons s128" li
{

}
```

So it applies to every li inside the ul.

I don't know about if it's a good practice what you want to do, but I would think that hiding the class references with custom tags may lead to certain unexpected behaviours. For example, you're updating certain css element, and it changes another thing that was using that reference, but it was hidden because of the custom tag.

---

### Post by Hellkeepa on 2009-12-17
HELLo!

It depends upon the DOCTYPE you use, and what DOCTYPE the application/rendering endinge understands of course. Nothing wrong with creating your own DOCTYPE, if you can control the rendering engine yourself.
If not: Better stick to the standard methods of doing things, lest you end up with some really strange bugs later on.

Happy codin'!

---

### Post by wmcbrine on 2009-12-17
> **Yuzem said:**
> This:
```

<toobar>
  content here
</toolbar>

<icons size=128>
  <icon></icon>
  <icon></icon>
  <icon></icon>
  <icon></icon>
</icons>

```If you do that, then it just isn't HTML. But it is (or could be) XML. Read up on XML.

---

### Post by era86 on 2009-12-17
You could do this or use an existing Javascript library to parse the page?  If you want to, you can write you're own Javascript library to handle this or you're own webserver to parse the page before sending it as a response to the correct format.

Just some overkill solutions for you to think about... Why not look into an existing library like Spry, Dojo, or JQuery.

---

### Post by Yuzem on 2009-12-17
> **Can+~ said:**
> Swap the css for:

```
ul."icons s128"
{

}

ul."icons s128" li
{

}
```

So it applies to every li inside the ul.

Of course, it was just an example.
I should have wrote:
```
<icons size=128>
  <icon></icon>
</icons>
```
and
```
<ul class="icons s128">
  <li></li>
</ul>
```


> **Can+~ said:**
> 
I don't know about if it's a good practice what you want to do, but I would think that hiding the class references with custom tags may lead to certain unexpected behaviours. For example, you're updating certain css element, and it changes another thing that was using that reference, but it was hidden because of the custom tag.
Why was it hidden? I use the tag instead, I think I don't understand...

> **wmcbrine said:**
> If you do that, then it just isn't HTML. But it is (or could be) XML. Read up on XML.
I have just read a little about XML and it seems that it can't handle standard HTML tags. I need them: input, a, from, h1, h2, etc...

So... nobody knows a real problem that could arise by doing this?

---

### Post by Hellkeepa on 2009-12-18
HELLo!

To put it simple: HTML is a standard, using certain names for their tags. If you don't use these names, then it is not HTML. Then we're talking about XML, which is a generic markup language, used to define other markup languages (such as XHTML, Atom, RSS, etc)
As I said previously: If you can defined your own DOCTYPE (flavour of markup language the parser uses), then you can design your own markup language. However, I would not expect any existing web browser to parse this properly.

Thus I recommend sticking with plain HTML.

Happy codin'!

---

### Post by Yuzem on 2009-12-18
Thanks for the answer Hellkeepa.
> **Hellkeepa said:**
> To put it simple: HTML is a standard, using certain names for their tags. If you don't use these names, then it is not HTML.
I use those names, and I want to use some custom names also. If you don't want to call it HTML, that's fine but using XML is not an option since I need the standard HTML tags.

The question remains: Does anyone know of any bad consequence in doing this?

---

### Post by Hellkeepa on 2009-12-18
HELLo!

It's not a matter of what I want to call it, or not, I'm afraid. It's a matter of whether it follows the standard, or not. Same way I can't add a whole lot of random words to my post, and still say it's all in English.

What you might want to do, is to research micro-formats. Either that, or use XML to define your own version of HTML, as this is the only solution to your question as it stands. Though, as previously have mentioned (three times already) browsers are unlikely to be able to parse your custom format. Something which, most likely, will lead to strange bugs.

Since you have given us precious little information on what you're trying to accomplish, other than that you want to use your own custom tags in a HTML-page for whatever reason, we can't give you more specific help than what's already given. For instance, you haven't even answered on the question of whether or not you're using a web browser, embedded rendering engine, or your own custom one. We're just assuming you're talking about a web page in a web browser here. By answering on the "why", instead of "what I want to do", we are in a much better position to give you more accurate help.

PS: What you are stating, in essence, is "I want to use HTML, but I don't want to use HTML." See the paradox?

Happy codin'!

---

### Post by wmcbrine on 2009-12-18
> **Yuzem said:**
> I have just read a little about XML and it seems that it can't handle standard HTML tags.You should probably read more, then.

> *So... nobody knows a real problem that could arise by doing this?*"Not working at all" isn't a real prolem?

---

### Post by era86 on 2009-12-18
If you want to use your own tags, you must convert it to standard HTML before sending it to the browser.  You can also write Javascript to do this for you on the browser side.

Again, check out Spry, Dojo, or any other framework that allows you to specify something like a toolbar on your page using their existing functions.

---

### Post by Yuzem on 2009-12-18
Thanks all for the answers. As you may have realized I am no expert. :(

> **Hellkeepa said:**
> It's not a matter of what I want to call it, or not, I'm afraid. It's a matter of whether it follows the standard, or not. Same way I can't add a whole lot of random words to my post, and still say it's all in English.
But you can say that it is in English plus a whole lot of random words...
That's exactly what I want to do, HTML plus some custom tags.

> **Hellkeepa said:**
> What you might want to do, is to research micro-formats. Either that, or use XML to define your own version of HTML, as this is the only solution to your question as it stands. Though, as previously have mentioned (three times already) browsers are unlikely to be able to parse your custom format. Something which, most likely, will lead to strange bugs.
Any example on those strange bugs?

> **Hellkeepa said:**
> Since you have given us precious little information on what you're trying to accomplish, other than that you want to use your own custom tags in a HTML-page for whatever reason, we can't give you more specific help than what's already given. For instance, you haven't even answered on the question of whether or not you're using a web browser, embedded rendering engine, or your own custom one. We're just assuming you're talking about a web page in a web browser here.
Yes, I am using a web browser: firefox.

> **Hellkeepa said:**
> By answering on the "why", instead of "what I want to do", we are in a much better position to give you more accurate help.
Well... the answer to the "why" question is just: To have a more clear, understandable code.

> **wmcbrine said:**
> "Not working at all" isn't a real prolem?
I tried replacing <div class=toolbar> by <toolbar>
Then I changed the css to match the tag instead of the class and I only had to add display:block; and it worked...

> **era86 said:**
> If you want to use your own tags, you must convert it to standard HTML before sending it to the browser.
Why? I really don't know... If that were the case it would make it more complicated instead of simplifying things... 

> **era86 said:**
> Again, check out Spry, Dojo, or any other framework that allows you to specify something like a toolbar on your page using their existing functions.
I'm using jQuery.

---

### Post by forgetclosure on 2009-12-19
why is everyone else being such a prick in their responses to you?

well here's my two cents:

unfortunately, that would be not too good of an idea, because of how different browsers interpret different things (especially internet explorer!). technically, yes, it would work, but only in your browser of choice, in another browser, it will most-likely not work. also, the w3c's standards which browsers nowadays adhere to and follow the rules of, say that it is inconsistent to do that because of how browsers interpret the html/css.

you can check your html with the [w3 xhtml validator]("http://validator.w3.org/"), and your css with the [w3 css validator]("http://jigsaw.w3.org/css-validator/") to keep the web clean.

the reason these standards were invented, was because web designers would actually do this, and since browsers don't always know how to interpret that information -- as opposed to a div, ul, or etc, which the browser already understands -- websites would look good in netscape, and bad in IE, or vice versa.

hope that helps!

Edit:
just a side-note, it will work, but it's just that it will not be as reliable as if you just stuck to the w3c's specifications - you can do it, and it will most likely work now that browsers are becoming more standards-compliant, but it's really just a better idea, if not for yourself, then for the internet and its websites as a whole to try and keep it clean :)

---

### Post by Yuzem on 2009-12-19
That was the answer I was looking for.
Thank you very much forgetclosure! :)
And thank you all, I have learned some new stuff.

---

### Post by v8YKxgHe on 2009-12-19
HTML5 actually adds quite a few new tags with English descriptive names, which is sort of what you want - and something you can start using right now. For example, there is the new 'header', 'nav', 'article' tag etc.

So, either use HTML4.01 strict with the current tags - or start using HTML5 strict with the new tags (which of course, wont be supported in all browsers since HTML5 is still a drafting spec).

---

### Post by forgetclosure on 2009-12-21
> **AlexC_ said:**
> HTML5 actually adds quite a few new tags with English descriptive names, which is sort of what you want - and something you can start using right now. For example, there is the new 'header', 'nav', 'article' tag etc.

So, either use HTML4.01 strict with the current tags - or start using HTML5 strict with the new tags (which of course, wont be supported in all browsers since HTML5 is still a drafting spec).

unfortunately, there are plenty of browsers that don't support html5: internet explorer 6, internet explorer 7, internet explorer 8, opera 10; firefox 3.5 and google chrome are partly supported, but not everything.

---

### Post by forgetclosure on 2009-12-21
> **Yuzem said:**
> That was the answer I was looking for.
Thank you very much forgetclosure! :)
And thank you all, I have learned some new stuff.

no problem :)

---

### Post by v8YKxgHe on 2009-12-21
> **forgetclosure said:**
> unfortunately, there are plenty of browsers that don't support html5: internet explorer 6, internet explorer 7, internet explorer 8, opera 10; firefox 3.5 and google chrome are partly supported, but not everything.

I know: *"(which of course, wont be supported in all browsers since HTML5 is still a drafting spec)."*

---

