---
title: "cycling through a php array"
date: 2006-03-10
forum: Programming Talk
---

### Post by oldmanstan on 2006-03-10
I want to go through a php array and if it has multiple items (which it might or might not) I want to place some text in between them.  However, I don't want text at the beginning or end.

The only way I can think of to do this is to use a for loop sorta like this:

```
//print text only between items
for ($i=0; $i < count($array); $i++) {
    if($i) {
        //add text
    }
    //print the array value
}
```

is there a more elegant method?  I checked the manual to see if there was a way to check if you were on the first or last iteration of a foreach loop but I couldn't find anything, anybody?

Thanks

---

### Post by dabear on 2006-03-10
Take a look at [implode](http://no.php.net/manual/en/function.implode.php)

---

### Post by oldmanstan on 2006-03-10
Well now, that's interesting, thanks!

---

