---
title: "color coded documentation"
date: 2010-11-18
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-18
In these forums we can use php tags to cite listings that we want to display color coded. Also elsewhere on the web I have been learning from software documentation like [http://www.antigrain.com/doc/basic_renderers/basic_renderers.agdoc.html](http://www.antigrain.com/doc/basic_renderers/basic_renderers.agdoc.html) where the color coding really does help to make it easier to follow :)

Alas, when I use "view source" I see it is done with countless "span" tags of many css classes. Yet it seems to me this should be doable client side, especially since my browser evidently knows how to color code the viewed html source :shock:

So I was wondering if there is any kind of browser plug-in available to view color coded source listings in web pages.

---

### Post by nvteighen on 2010-11-18
I have a problem with that idea... but well, it's probably just me...

Any webpage that's shown by your browser is interpreted by the browser's layout engine, which takes the (X)HTML code and outputs what the (X)HTML specification defines for each markup element. The same for the CSS styles.

Now, asking a browser to alter what the (X)HTML and CSS of the webpage you've downloaded in order to get a better layout means you want your browser behave non-standard-wise, even if that non-standard behaivor is strictly restricted to code snippets.

Whether you implement this right at the engine or via a plugin, it sounds like trying to make the browser prettify the webpage for the bad web designer that doesn't take any account on the readibility of his/her own webpage.

I'm not saying all of this is bad or good; I'm just stating those are the implications of your idea. It can be useful... and I think there are some accesibility plugins that do this sort of stuff, but ugh... I think the issue is that some web designers should start doing their jobs better and that's something a computer can't solve.

---

### Post by Arndt on 2010-11-18
> **worksofcraft said:**
> In these forums we can use php tags to cite listings that we want to display color coded. Also elsewhere on the web I have been learning from software documentation like [http://www.antigrain.com/doc/basic_renderers/basic_renderers.agdoc.html](http://www.antigrain.com/doc/basic_renderers/basic_renderers.agdoc.html) where the color coding really does help to make it easier to follow :)

Alas, when I use "view source" I see it is done with countless "span" tags of many css classes. Yet it seems to me this should be doable client side, especially since my browser evidently knows how to color code the viewed html source :shock:

So I was wondering if there is any kind of browser plug-in available to view color coded source listings in web pages.

Personally, I find it grotesque. Colour coding irritates me more than it helps me.

---

### Post by worksofcraft on 2010-11-18
> **nvteighen said:**
> I have a problem with that idea... but well, it's probably just me...

Any webpage that's shown by your browser is interpreted by the browser's layout engine, which takes the (X)HTML code and outputs what the (X)HTML specification defines for each markup element. The same for the CSS styles.

Now, asking a browser to alter what the (X)HTML and CSS of the webpage you've downloaded in order to get a better layout means you want your browser behave non-standard-wise, even if that non-standard behaivor is strictly restricted to code snippets.

Whether you implement this right at the engine or via a plugin, it sounds like trying to make the browser prettify the webpage for the bad web designer that doesn't take any account on the readibility of his/her own webpage.

I'm not saying all of this is bad or good; I'm just stating those are the implications of your idea. It can be useful... and I think there are some accesibility plugins that do this sort of stuff, but ugh... I think the issue is that some web designers should start doing their jobs better and that's something a computer can't solve.

Hum... have you seen the kind of HTML it produces to colorify it? There is no way **any** web designer is coding that. It's being generated either before uploading the html or may be server side with some PhP. Either way, probably making the web page far more difficult to update and maintain!

Now we all know we can use tags like <pre></pre> to display pre-formatted text such as computer source code but clearly there is a big demand for color coded text in software related documents:

Thus I was thinking even that source code text itself could be taken from a separate file, a bit like one displays an image without the HTML trying to define the picture all with HTML tags.

---

### Post by worksofcraft on 2010-11-18
> **Arndt said:**
> Personally, I find it grotesque. Colour coding irritates me more than it helps me.

All the more reason to have it rendered by a plug-in that can give you the option to turn color coding off... I presume you worked out how to disable it with gedit and chrome source viewer already.

Personally I think it makes it much easier to follow and to spot simple bugs.

---

### Post by trent.josephsen on 2010-11-18
Personally, the first thing I do upon encountering a code listing online is highlight it, open a terminal, type 'cat >something.c', middle-click, and hit Ctrl-D.  Then I can open it in vim, which is much more comfortable than bothering with it in a browser.

---

### Post by worseisworser on 2010-11-18
> **worksofcraft said:**
> In these forums we can use php tags to cite listings that we want to display color coded. Also elsewhere on the web I have been learning from software documentation like [http://www.antigrain.com/doc/basic_renderers/basic_renderers.agdoc.html](http://www.antigrain.com/doc/basic_renderers/basic_renderers.agdoc.html) where the color coding really does help to make it easier to follow :)

Alas, when I use "view source" I see it is done with countless "span" tags of many css classes. Yet it seems to me this should be doable client side, especially since my browser evidently knows how to color code the viewed html source :shock:

So I was wondering if there is any kind of browser plug-in available to view color coded source listings in web pages.

If you're using Firefox, install Firebug; it can show color coded and nicely formatted HTML.

If you're using Chrome/Chromium, it has this built in; just hit Ctrl-Shift-i.

---

### Post by worseisworser on 2010-11-18
> **worksofcraft said:**
> Hum... have you seen the kind of HTML it produces to colorify it? There is no way **any** web designer is coding that. It's being generated either before uploading the html or may be server side with some PhP. Either way, probably making the web page far more difficult to update and maintain!

Unformatted HTML might be generated by a DSL; it's easier to maintain and deal with actually.

Web designers usually have the tools needed to re-format the HTML to their liking at the touch of a key -- or the original author in question can make his DSL-engine output already formatted HTML:

[php]
SW> (who ()
      (:html
       (:head (:title "Test"))
       (:body
        (:h1 "This is a test")
        (:p "Hello World; what's up?")
        (:p :style "background-color: red;"
            "Here is some red text."))))
==>
"<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\">
<html><head><title>Test</title></head><body><h1>This is a test</h1><p>Hello World; what's up?</p><p style='background-color: red;'>Here is some red text.</p></body></html>"



SW> (who (:indent t)
      (:html
       (:head (:title "Test"))
       (:body
        (:h1 "This is a test")
        (:p "Hello World; what's up?")
        (:p :style "background-color: red;"
            "Here is some red text."))))
==>
"<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Strict//EN\" \"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd\">

<html>
  <head>
    <title>Test
    </title>
  </head>
  <body>
    <h1>This is a test
    </h1>
    <p>Hello World; what's up?
    </p>
    <p style='background-color: red;'>Here is some red text.
    </p>
  </body>
</html>"

SW> 
[/php]

---

### Post by worksofcraft on 2010-11-18
It's not the HTML I want to color code. It is for writing documentation **in** HTML for my own software. This documentation needs to be accessible on the local machine without setting up PhP servers to view it.

At the AGG website I liked their use of colored code fragments which they then went on to explain and also contain hyper links, but for instance the following simple C++ 
[php]
#include <string.h>
#include "agg_rendering_buffer.h"

enum
{
    frame_width = 320,
    frame_height = 200
};

// Writing the buffer to a .PPM file, assuming it has 
[/php]
(colors here are not as per original) has this as it's html:
[php]
<span class="kw2">#include</span> <span class="op">&lt;</span>string<span class="op">.</span>h<span class="op">&gt;</span> 
<span class="kw2">#include</span> <span class="str">"<a href="http://www.antigrain.com/__code/include/agg_rendering_buffer.h.html">agg_rendering_buffer.h</a>"</span> 
 
<span class="kw1">enum</span> 
<span class="op">{</span> 
    frame_width <span class="op">=</span> <span class="num">320</span><span class="op">,</span> 
    frame_height <span class="op">=</span> <span class="num">200</span> 
<span class="op">}</span><span class="op">;</span> 
 
<span class="rem">// Writing the buffer to a .PPM file, assuming it has </span> 
[/php]
In that form it would not be maintainable, so I was wondering what solutions programmers use to document their software.

---

### Post by Reiger on 2010-11-18
There's a simple enough way, use JavaScript: [http://alexgorbatchev.com/SyntaxHighlighter/](http://alexgorbatchev.com/SyntaxHighlighter/)

So you adapt your documentation system to bundle a copy of the JavaScript `library' + plugins (language specific stuff) as well as wrap the necessary code in an appropriate <pre> tag.

---

### Post by worksofcraft on 2010-11-18
> **Reiger said:**
> There's a simple enough way, use JavaScript: [http://alexgorbatchev.com/SyntaxHighlighter/](http://alexgorbatchev.com/SyntaxHighlighter/)

So you adapt your documentation system to bundle a copy of the JavaScript `library' + plugins (language specific stuff) as well as wrap the necessary code in an appropriate <pre> tag.

Perfect!
Works a treat, just what I wanted, TYVM :)

I think good hyper text documentation for code is often worth more than the code itself. I also see that Alex Gorbatchev is hosting the scripts on the web so that everyone can use them online. I shall use the <pre> tags as opposed to the <script> tags so my documents will still be readable even when said javascript is inaccessible.

---

### Post by worksofcraft on 2010-11-18
Just wondering if there is a way in HTML to identify locally installed java scripts, but if it doesn't find them there to use the ones on the web instead?

Note: This is obviously to cut down unnecessary costs for the script hosting as well as my own broadband usage, yet allow 3rd parties to get it's functionality without having to install teh scripts themselves.

---

### Post by worksofcraft on 2010-11-18
also I notice that in Google Chrome it always puts a scroll bar on my source code divs... like you can scroll down by one extra pixel :shock: however on FireFox it does not.

So my question is... should I report it as a bug to Google, or to sourcehighlighter... or try to fudge it myself, or ignore it, or go test what it does on I.E. and Opera? Does it do that for you and what would you do? :confused:

---

