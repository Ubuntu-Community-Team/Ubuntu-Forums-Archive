---
title: "[html/js] Adding an onresize event to the body with js"
date: 2009-07-12
forum: Programming Talk
---

### Post by durand on 2009-07-12
Hi!

I need to run a function whenever the window is resized but I can't access the body tag directly. Is the a way to do it without manually adding it to the body tag? I tried ```
document.body.onresize = "MyFunction()"
``` but it didn't do anything and I didn't get any errors in opera's error console.
Does anyone have any ideas?

Thanks!

---

### Post by Reiger on 2009-07-12
JavaScript is case sensitive, HTML is not.
```

<script type="text/javascript">
/*Using an anonymous function */
document.body.onresize=function() { 
  alert('bingo?'); 
  document.body.onresize= MyFunction; // so after the first resize we will have a new event handler.
};
function MyFunction() {
  alert('bingo!');
}
</script>

```

That will work. I'd suggest you stick to the proper method names, that is to the all-lowercase ones -- even if it is HTML code. Imagine one day migrating to an XML DOM instead and finding out that it too is case sensitive. Plus there can be no confusion if you call the same things by exactly the same name.

The second problem you have here, is that with your assignment you turned an object method into an object property with the value "MyFunction()". You may want to read some JavaScript tutorials because it is a fairly elemental mistake (and one you'll probably never make again). The correct syntax to use is: object.method = functionName; See the example code above for, well, an example.

EDIT: Just in case you were wondering. Of course you can simply set the event listener to MyFunction straight away. ;)

---

### Post by durand on 2009-07-12
It's still not working :(
This is the actual line I'm now using:
```
<script type="text/javascript">document.body.onresize = set_size('iframe')</script>
```
set_size is in the body. Could that be the problem?

About the quotes, I figured that the function name would be in quotes if they were in the body tag so thats what I did. I assumed that if I didn't use quotes, onresize would use the output of the set_size function which returns nothing so I would end up with a blank onresize.

---

### Post by durand on 2009-07-12
Aha, I actually tried using using your example code and it worked when I replaced the alert function with my own. Thanks! However, I'm not sure why the line I posted above won't work.

---

### Post by durand on 2009-07-12
Just saw your edit. How would I pass arguments to the function without using parentheses?

---

### Post by Reiger on 2009-07-12
The key is: what does set_size() return? If it is a function you are good to go, if it is -as I am guessing- a value or void then you are back to your old mistake of turning something that must be a function for it to work into a property...!

But why should that stop you from taking my anonymous function as an example and make it a wrapper to set_size() if you want to? document.body.onresize = function() { set_size('iframe'); }; ?
Alternatively you can make set_size return a function:
```

function set_size(param) {
  return function() {
   /* do your original set_size() stuff here, for example: */
   alert(param);
  };
}

```

Also: For the sake of the fact that it exists and actually works that way: note that my anonymous document.body.onresize function is in fact a simplified version of one that takes a single parameter -- the no-parameter version is taking advantage of the fact that JavaScript allows you to ignore parameters inside function definitions. This extra parameter is the event object itself, which you can use to query for the thing that caused the event to be fired in the first place. Using a no-parameter version means that you can't do the aforementioned things because you don't have the reference to the event object. (It is there but you don't have a name for it, so you can't call upon it.) On the other hand if you aren't going to do those things... why type. :)

You may want to read a few tutorials about JavaScript events that explain this further, and go beyond this kind of event work.

---

### Post by durand on 2009-07-12
Ahhh! My mistake was that set_size didn't return anything. So next time, I'll use the code you wrote in the above post. (I really need to read up on JS more..)

Thank you very much!

---

### Post by Can+~ on 2009-07-12
I recommend using Firefox and Firebug for Javascript. Or maybe firebug is available for opera too.

---

### Post by durand on 2009-07-12
I've tried firebug but I think I prefer opera dragonfly.

---

### Post by Reiger on 2009-07-12
> **Can+~ said:**
> I recommend using Firefox and Firebug for Javascript. Or maybe firebug is available for opera too.

Opera has Dragonfly, and a generally more helpful error console than Firefox has (IMO).

---

