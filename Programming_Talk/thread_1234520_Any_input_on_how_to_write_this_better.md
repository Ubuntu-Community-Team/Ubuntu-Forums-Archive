---
title: "Any input on how to write this better"
date: 2009-08-08
forum: Programming Talk
---

### Post by JimBuntu on 2009-08-08
```
<img src="../images/image1_thumb.jpg" alt="thumb"
onmouseover="window.document.getElementById('full').src='../images/image1.jpg';"
onmouseout="window.document.getElementById('full').src='../images/full.png';"/>
```

I'm looking for a better way to do this, or just write it. Maybe just a single function. Any ideas?

---

### Post by smartbei on 2009-08-08
If you are doing this several times, then you can definately use a function.
This is untested, but:
```

function return_default_image()
{
        window.document.getElementById('full').src='../images/full.png';
}
function set_new_image(image)
{
        window.document.getElementById('full').src='../images/' + image;
}

```
And then you would have:
```

<img src="../images/image1_thumb.jpg" alt="thumb" onmouseover="set_new_image('image1.jpg');" onmouseout="return_default_image();"/>

```

Which looks quite a bit nicer to me :-)

---

### Post by JimBuntu on 2009-08-08
very nice...very nice...

---

### Post by bobince on 2009-08-10
And then unobtrusive JavaScript techniques allow you to move all the onsomething event handlers out completely, potentially into a separate JavaScript file:

```
    <img src="/img/button0.gif" class="hoverable" />

    ...
    function imagemouseover() {
        this.src= this.src.replace('0.gif', '1.gif');
    }
    function imagemouseout() {
        this.src= this.src.replace('1.gif', '0.gif');
    }

    for (var i= document.images.length; i-->0;) {
        var image= document.images[i];
        if (image.className=='hoverable') {
            image.onmouseover= imagemouseover;
            image.onmouseout= imagemouseout;
        }
    }
```But then if all you're doing is a hover effect, you might be better off just using CSS :hover.

---

### Post by hessiess on 2009-08-10
Use CSS insted, and learn how to use JQuery.

---

### Post by JohnFH on 2009-08-10
You don't need to use getElementById.  Just do:

```

<img src="../images/image1_thumb.jpg" alt="thumb"
onmouseover="full.src='../images/image1.jpg'"
onmouseout="full.src='../images/full.png'"/>

```

---

### Post by hessiess on 2009-08-10
Like I said above, Just use CSS:
[http://htmldog.com/articles/rollovers/](http://htmldog.com/articles/rollovers/)

---

### Post by bobince on 2009-08-11
> **JohnFH said:**
> onmouseover="full.src='../images/image1.jpg'"

I'm assuming you've omitted &#8216;id="full"&#8217; on the img (like in smartbei's example), without which this doesn't make much sense.

Even so, this isn't a good idea. Referring to an element with &#8216;id="foo"&#8217; by using a global-scope &#8216;foo&#8217; (or &#8216;window.foo&#8217;, which is the same thing) is a non-standard hack introduced by IE that [doesn't work | works differently | works unreliably] in other browsers. Firefox will spit a &#8220;Element referenced by ID/Name in global scope. Use W3C standard&#8221; warning to the console to let you know you're doing it wrong.

&#8216;document.foo&#8217; is another slightly-less-short shortcut that is often used, but it too has problems with cross-browser compatibility. Both &#8216;document.foo&#8217; and &#8216;window.foo&#8217; also suffer from problems when you use a name which clashes with a method or other property defined on &#8216;document&#8217; or &#8216;window&#8217;. In this case, using the direct property access can leave you with the element, or the original member. And since every new browser/version can introduce new members of &#8216;document&#8217; and &#8216;window&#8217;, you can't be sure that your element ID won't clash with a native member in a future browser.

So, for accessing elements by ID, &#8216;document.getElementById()&#8217; really is what you want. The old-style DOM-HTML form-navigation interfaces like &#8216;document.forms.formname.elements.fieldname&#8217; can sometimes also be useful if you want to access fields by control name without having to use IDs, but otherwise definitely &#8216;getElementById()&#8217;.

A more pleasant alternative in this case is to use &#8216;this.src&#8217;. In an event handler, &#8216;this&#8217; points to the element that received the event.

---

