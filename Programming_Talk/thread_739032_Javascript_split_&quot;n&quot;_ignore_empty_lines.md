---
title: "Javascript split &quot;\n&quot; ignore empty lines"
date: 2008-03-29
forum: Programming Talk
---

### Post by likwid on 2008-03-29
Hi

Is it possible to split the contents of a text box into rows while ignoring empty lines, using split? It's possible in php but i can't find anything for js.

Thanks :)

---

### Post by insineratehymn on 2008-03-29
Would it work if you threw all of the data in the text box into an array, for each'd through the array and tested if it was empty?

---

### Post by likwid on 2008-03-29
Hi 

That would work, in fact the split function loads the textarea into an array. I was hoping there would be a delimiter that I could use within split.

---

### Post by insineratehymn on 2008-03-29
Yeah. I just tried a quick array with a line break in it and it at least seems to work...

```

<script>
//alert("Test!");
var testing = new Array("Test", "\n", "Woo!");
alert (testing);
for each ( testing in testing ) {
        if(testing != "\n") alert (testing);
}
</script>

```

Seems kind of a stupid for each compared to perls... but hey. You get what you get with JS. ;)

---

### Post by likwid on 2008-03-29
Thanks very much :)

It's a shame javascript seems pretty limited for inbuilt functions but I'm really enjoying using it nonetheless.

---

### Post by insineratehymn on 2008-03-29
JS is quick and dirty, but most of your java syntax translates pretty seamlessly.

---

### Post by ML-Spinner on 2008-05-14
Whats wrong with

var mySplitResult = myString.split("\n");

:)

---

### Post by likwid on 2008-05-14
It doesn't ignore empty lines :)

---

### Post by ms609 on 2010-11-28
How about the following?

var mySplitResult = myString.split("\n**+**");

---

