---
title: "help with this javascript"
date: 2009-06-10
forum: Programming Talk
---

### Post by ELD on 2009-06-10
Hi all i am finding a way to make it so ticking one box ticks them all kinda thing and i have this at the moment:
 ```

     function checkUncheckAll(checkAllState, cbGroup)
{
    // Check that the group has more than one element
    if(cbGroup.length > 0)
    {
        // Loop through the array
        for (i = 0; i < cbGroup.length; i++)
        {
            cbGroup[i].checked = checkAllState.checked;
        }
    }
    else
    {
        // Single element so not an array
        cbGroup.checked = checkAllState.checked;
    }
} 

```
Which is fine if the name is say "message" but my checkbox names are like "message[1]" or "message[15]" (a name array so php can sort the messages checked when it does the action, like deleting or saving the ticked ones).

How would i go about doing that? (Note i don't know javascript, this was from a rather small and undetailed tutorial).

---

### Post by Reiger on 2009-06-10
Not there: the function expects an array which contains *all* checkbox elements to be checked/unchecked. Long story short: use a container element to hold all checkboxes that must be checked/unchecked by what I'll name the "bulkXYZ" checkbox. Then have a onclick="checkUncheckAll();" eventhandler. Then use the `container' function of the parent element of the element called "bulkXYZ" and getElementsByTagName() magic.

If you use XHTML served as such (or XML transformed on the client side) you will have the added bonus of interoperability between HTML-only browsers like MSIE and the rather smarter browsers which aren't called MSIE (or hopelessly behind).

All in all:

```

<div><!-- containers -->
<input type="checkbox" name="bulk1" onclick="var myparent=this.parentNode; checkUncheckAll(this, (myparent.getElementsByTagName('INPUT') || myparent.getElementsByTagName('input') )); return false;"><!-- this is the bulkXYZ checkbox --></input>
<!-- some checkboxes here -->
</div>

```

Note: my code will process the "bulk" checkbox as well but there should not be any side effects of this as the "bulk" checkbox will be set to the value it already had.

If you want to understand this code I suggest you read up on manipulating the DOM with JavaScript and the difference between HTML and XML DOM in this respect and the onclick() event handler in JavaScript.

---

