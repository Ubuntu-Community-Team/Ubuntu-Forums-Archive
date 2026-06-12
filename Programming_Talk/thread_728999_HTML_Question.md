---
title: "HTML Question"
date: 2008-03-19
forum: Programming Talk
---

### Post by tony5429 on 2008-03-19
I am using the following format for links on a web site I am working on...

[HTML]
<a href=http://google.com onFocus="if(this.blur)this.blur()">Google</a>
[/HTML]

Rather than type that onFocus part into every link, is there a way I can put something in the header at the top that applies that to all links in the page? The command removes that little annoying selection rectangle on clicked links.

---

### Post by LaRoza on 2008-03-19
> **tony5429 said:**
> I am using the following format for links on a web site I am working on...

[HTML]
<a href=http://google.com onFocus="if(this.blur)this.blur()">Google</a>
[/HTML]

Rather than type that onFocus part into every link, is there a way I can put something in the header at the top that applies that to all links in the page? The command removes that little annoying selection rectangle on clicked links.

Yes, such declarations are messy. (See my homepage for use of scripting in a clean way. ALL script is in a separate file.)

You can do the same, link to this script as is, and it will apply that to every link in the page:

[php]
window.onload = function()
{
    var linds = document.getElementsByTagName("a");
    //This loop should be executed IF linds exists, so it should be encapsulated in "if (linds && document.getElementsByTagName) {....}"
    for (var i = 0; i < linds.length; i++)
    {
        linds[i].onfocus = function()
        {
            if (this.blur)
            {
                this.blur();
            }
        } 
    }
}
[/php]

---

### Post by lnostdal on 2008-03-19
you might like jQuery .. it's small and simple

```

$("a").focus(function(){
  if(this.blur){ 
    this.blur() 
  }
}

```

---

### Post by Zugzwang on 2008-03-19
Just a question: Doesn't this make a page unusable for keyboard-only navigation? If yes, you shouldn't bother with the selection boxes due to accessibility issues.

(EDIT: This question refers to the original posting)

---

### Post by leg on 2008-03-19
> **Zugzwang said:**
> Just a question: Doesn't this make a page unusable for keyboard-only navigation? If yes, you shouldn't bother with the selection boxes due to accessibility issues.

(EDIT: This question refers to the original posting)
Yes it does and the op should have a very good reason to do this. If not then he should not do it.

---

