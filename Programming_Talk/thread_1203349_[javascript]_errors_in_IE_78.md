---
title: "[javascript] errors in IE 7/8"
date: 2009-07-03
forum: Programming Talk
---

### Post by ELD on 2009-07-03
I currently us the below code for javascript insertion which works fine in FF & Opera but gives errors in IE.

(this was from a tutorial i found)
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

    else if (obj != "undefined")  // Firefox
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
    else if (obj != "undefined")
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

Here is a screenshot of the error:
[http://i43.photobucket.com/albums/e397/clericvash/jserror.jpg](http://i43.photobucket.com/albums/e397/clericvash/jserror.jpg)

I am no good at all with JS so i don't know what it means?

---

### Post by Reiger on 2009-07-03
For a start consider your type checking:
```

if(obj != 'undefined')

```

Is wrong for two reasons. First of all you are comparing an object (possibly null) with a string. You do this to check whether or not a variable has been set, but what if it is null. Second problem is already alluded to: this is the wrong way to check if a variable has been set. Use: typeof(obj) = typeString. Like this:
```

if(typeof(obj) != 'undefined')

```

---

### Post by ELD on 2009-07-03
Wow that actually fixed the errors in IE 8. Thanks a lot!

---

