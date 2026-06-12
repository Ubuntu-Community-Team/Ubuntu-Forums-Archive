---
title: "[javascript] Error in google chrome"
date: 2009-07-10
forum: Programming Talk
---

### Post by ELD on 2009-07-10
Basically my bbcode insertion javascript works near on perfect in all browsers now apart from chrome. It seems to repeat whatever is before it when you enter text:

```

// add simple text
function addText(Text)
{
    var obj = document.form.message;
    obj.focus();
 
    if (document.selection && document.selection.createRange)  // Internet Explorer
    {
        sel = document.selection.createRange();
        if (sel.parentElement() == obj)  
        {
            sel.text = Text;
        }
    }

    else if(typeof(obj) != 'undefined')  // Firefox
    {
        var longueur = parseInt(obj.textLength);
        var selStart = obj.selectionStart;
        var selEnd = obj.selectionEnd;

        obj.value = obj.value.substring(0,selStart) + Text + obj.value.substring(selEnd,longueur);
    }
 
    else 
    {
        obj.value += Text;
    }

    obj.focus();
}

// wrap code in tags or just simply add them by themselves
function addTags(Tag, fTag)
{
    var obj = document.form.message;
    obj.focus();

    // Internet Explorer
    if (document.selection && document.selection.createRange) 
    {
        sel = document.selection.createRange();
        if (sel.parentElement() == obj)
        {
            sel.text = Tag + sel.text + fTag;
        }
    }

    // Firefox
    else if(typeof(obj) != 'undefined')
    {
        var longueur = parseInt(obj.textLength);
        var selStart = obj.selectionStart;
        var selEnd = obj.selectionEnd;

        obj.value = obj.value.substring(0,selStart) + Tag + obj.value.substring(selStart,selEnd) + fTag + obj.value.substring(selEnd,longueur);
    }
 
    else
    {    
        obj.value += Tag + fTag;
    }

    obj.focus();
} 

```

You can test here:
[Prxa.info Message Board >> Add New Topic](http://forum.prxa.info/newtopic.php?fid=9)

In chrome it will delete whatever was before it when entering the bbcode into the box and repeat stuff, test above to see what i mean :(

---

### Post by smartbei on 2009-07-10
I have to ask - why aren't you using something like tinyMCE or any other WYSIWYG text editor in javascript. There are even ones that work with BBCode instead of HTML.

You could also take a look at their source code as a reference, and see how they are dealing with making the code run well under different browsers.

---

### Post by ELD on 2009-07-10
Because this is a custom script with a custom license. And i would rather use my own code.

---

