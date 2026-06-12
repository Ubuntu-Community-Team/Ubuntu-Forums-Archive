---
title: "Javascript String prototype"
date: 2008-01-10
forum: Programming Talk
---

### Post by Wybiral on 2008-01-10
I'm not sure if this is even possible, but I might as well ask before I redesign my project... I need a way to add a method to the "String" prototype in Javascript that allows me to alter the string instance.

My method should look like this:
```

String.prototype.__setitem__ = function(i, c) {
    this = this.substr(0, i) + c + this.substr(i + 1);
}

```

But Javascript doesn't allow assignment to "this" and there is no other way to alter individual characters in a string (or is there?).

And yes, I know that I could just have it return the concatenated strings and use it as "str = str.__setitem__(i, c);" but that doesn't fit with the rest of my design and is not an option.

I'm rather unsatisfied with Javascript's lack of consistency with regards to objects. I should be able to "duck" on the method to a string, which you can for any other objects, but for some reason strings/ints/floats are exceptions to that behavior.

Any ideas?

---

### Post by LaRoza on 2008-01-10
[php]
function nString(val)
{
    this.value = String(val);
    this.len = this.length;
}

nString.prototype.alterString = function()
{
    this.value = "me";
}
[/php]

Might work...

It allows "this.value" to alter the value. As you can see, it is just a wrapper for the String object.

[php]
window.onload = function()
{
    var name = new nString("name");
    alert(name.value);
    name.alterString();
    alert(name.value)
}
[/php]

Worked as expected.

**<edit>**
[php]
nString.prototype.__setitem__ = function(i, c) {
    this.value = this.value.substr(0, i) + c + this.value.substr(i + 1);
}
[/php]

Works.
**</edit>**

---

### Post by Wybiral on 2008-01-10
That would work, except not for my project. The string objects need to be capable of being passed to functions as-is (without having to access a member each use), but also have a standard interface for getting/setting items. Naturally, this is for [Epy]("http://code.google.com/p/epy/"),

I'm turning the Python code "x[i] = y" into "x.__setitem__(i, y)" (which is required so Epy can work with custom getitem/setitem methods like Python does). But if the string were wrapped in a class, code such as "createTextNode(x)" wouldn't work (and since the type isn't guaranteed at compile-time, I can't append the member name since that label could easily become another type at any point).

I wonder why Javascript strings are immutable? Javascript is in SERIOUS need of a rewrite of the standard.

---

### Post by LaRoza on 2008-01-10
> **Wybiral said:**
> 
I wonder why Javascript strings are immutable? Javascript is in SERIOUS need of a rewrite of the standard.

Aren't strings immutable in many languages? The standard is ECMA-262, in case you want to rewrite it.

I don't have time at the moment, but I am sure this can be done. I just need to look into the more in depth ECMAScript OO and the available string functions.

(I have to go to school. I left the movies I bought yesterday there.)

---

### Post by Wybiral on 2008-01-10
> **LaRoza said:**
> Aren't strings immutable in many languages?

A lot of languages treat strings like character arrays and allow you to easily index/alter the data. Javascript doesn't treat them as an array, but treats them as a single object where the data (as far as I know) is private.

---

### Post by LaRoza on 2008-01-10
> **Wybiral said:**
> A lot of languages treat strings like character arrays and allow you to easily index/alter the data. Javascript doesn't treat them as an array, but treats them as a single object where the data (as far as I know) is private.

Perhaps you can rewrite the class as a character array. You can use split() to create an array out of a string.

---

### Post by pmasiar on 2008-01-10
> **Wybiral said:**
> I wonder why Javascript strings are immutable?

Python's strings are also immutable.

---

### Post by Wybiral on 2008-01-10
> **pmasiar said:**
> Python's strings are also immutable.

Holy crap, I actually never realized that.

** smacks forehead **

I always thought you could use "str[i] = c", but I just tried, and... Well, you're absolutely correct. I guess I should still have __setitem__ throw this error then:
> 
'str' object does not support item assignment


But, I'll leave this unsolved in case anyone actually finds a way to do this in Javascript.

Thanks for the help guys!

---

### Post by CptPicard on 2008-01-10
You know.. Java's strings are immutable just as well. It's common. :)

---

### Post by LaRoza on 2008-01-10
> **CptPicard said:**
> You know.. Java's strings are immutable just as well. It's common. :)

That is what I thought....

---

### Post by Wybiral on 2008-01-10
> **CptPicard said:**
> You know.. Java's strings are immutable just as well. It's common. :)

I know, I know...

I spent several years in C and C++, what do you expect?

---

