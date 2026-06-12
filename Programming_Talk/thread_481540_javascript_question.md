---
title: "javascript question"
date: 2007-06-22
forum: Programming Talk
---

### Post by Swab on 2007-06-22
Is there a way to name a variable by using the value of another variable?

For example if var1 = "hello"  I want to be able to create another variable named hello.

It might seem like a strange thing to want to do, but is it possible?  I don't want to use an associative array.

---

### Post by robgr85 on 2007-06-22
> **Swab said:**
> Is there a way to name a variable by using the value of another variable?

For example if var1 = "hello"  I want to be able to create another variable named hello.

It might seem like a strange thing to want to do, but is it possible?  I don't want to use an associative array.

never heard about this... but it doesn't mean that this method doesn't exist...

do not have time to stumble but you can try to find it:
[http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Reference](http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Reference)

Robert

---

### Post by init1 on 2007-06-22
> **Swab said:**
> Is there a way to name a variable by using the value of another variable?

For example if var1 = "hello"  I want to be able to create another variable named hello.

It might seem like a strange thing to want to do, but is it possible?  I don't want to use an associative array.
And if var1 = "Hi" you want to be able to create another variable named Hi? I don't think it is possible. What do you want it for? Maybe if I know the context, I can suggest an alternative.

---

### Post by WW on 2007-06-22
You can use var1 to build a string that defines the new variable, and then **eval** the string.  For example:
```

<html>
<body>

<script type="text/javascript">

var var1="hello"
var makenewvar = "var " + var1 + "=100"
eval(makenewvar)
document.write("Evaluated this string: " + makenewvar)
document.write("<br />")
document.write("The value of " + var1 + " is ")
document.write(hello)
document.write("<br />")

</script>

</body>
</html>

```
Here is the output:
> 
Evaluated this string: var hello=100
The value of hello is 100

You can experiment with it here: [http://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_eval](http://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_eval)
Replace the default example with the above code.

---

### Post by FuturePast on 2007-06-23
> **Swab said:**
> I don't want to use an associative array.
Javascript is essentially one big associative array, and is almost designed to do exactly what you're asking.

---

### Post by Swab on 2007-06-23
Thanks for all the replies.

OK,  here is the situation.   I have an ajax application that is essentially just a page with  a couple of hundred checkboxes.  At the moment every time you check or uncheck a box it used the same request object.  This causes a problem if network conditions are bad or if the user checks the boxes too fast.   So what I thought I could do was create a new object each time the state of a box is changed.  The name of the object would  be based on the id of the checkbox.

There is probably a simple solution here, I've searched around but the examples I find are pretty much beyond my level of understanding.  Any help appreciated.

---

### Post by FuturePast on 2007-06-23
I haven't done any ajax programming, but if you post up a sample it would be easier to grasp the problem.

---

