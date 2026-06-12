---
title: "object lesson in a javascript array"
date: 2017-03-11
forum: Programming Talk
---

### Post by maclenin on 2017-03-11
Essentially, while testing the following javascript array in jsbin I've been wondering...

```
var produce = [ { "fruit":"apple, banana, pear", "veg":"pea, carrot, turnip" } ];
```

...whether it is possible to call the fruit and veg values as the commas separate them?

For example, how might I cause...
```
document.body.innerHTML += produce[0].fruit;
```
...to return (only the) apple instead of:
```
apple, banana, pear
```
Thanks for any guidance!

---

### Post by The Cog on 2017-03-11
I don't understand what you are trying to do there. 
Having an array with only one object in it doesn't make a lot of sense to me. Perhaps you want to have one object with lists of names instead, like this:
```
var produce = { "fruit":["apple", "banana", "pear"], "veg":["pea", "carrot", "turnip"] } ;
```
Then you can do:
```
document.body.innerHTML += produce.fruit[0];
```

---

### Post by maclenin on 2017-03-12
Indeed. I think it's an issue of mission and my (evolving) understanding of proper syntax (to accomplish the mission).

Here's, perhaps, a more useful (display & sort) example:
```
var gallery = [];

gallery = [

{
"title":"",
"date":""
},

{
"title":"",
"date":""
},

{
"title":"",
"date":""
}

];
```
Thanks for your comments!

---

### Post by The Cog on 2017-03-12
There's a nice example of sorting a list of objects here: [https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/sort](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) . Search for "sort by name".

---

### Post by maclenin on 2017-03-12
Thanks The Cog!

I have deployed the sorting methods in the link you provided - having found the link, previously, while researching sort options.

I added the comment about (display & sort) to describe the purposes for which I had used the gallery array example.

I think my question is really more about whether the gallery array syntax is a best way / proper syntactically.

Thanks, again, for the follow-up!

---

### Post by The Cog on 2017-03-13
OK back to your first post, splitting that fruits string on ", " will yield a list of fruit names, apple being the first:
```
var produce = [ { "fruit":"apple, banana, pear", "veg":"pea, carrot, turnip" } ];
document.body.innerHTML += produce[0].fruit.split(", ")[0]

```
Your gallery code looks fine except that you assign an empty array to gallery before re-assigning an array with contents. The first assignment is unused and not actually needed.

---

### Post by maclenin on 2017-03-16
Thanks for the split clarification but I think your previously suggested fruit basket is cleaner.

The assignment ( var x = []; ) is something I use when I am creating / displaying dynamically sorted sub-sets.

For example, given two buttons: fruit basket, veg basket - if someone chooses the veg basket, I push the veg into var basket = []; and display the selected basket array.

However, if someone then chooses fruit,  I need to empty the basket, beforehand - so var basket = []; empties the basket (at the top of the sort function) - in prep for the filling of it with fruit (or veg)....

Thanks, again, for the comments!

---

