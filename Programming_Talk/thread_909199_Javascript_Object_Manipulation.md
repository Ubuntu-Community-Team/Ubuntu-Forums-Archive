---
title: "Javascript Object Manipulation"
date: 2008-09-03
forum: Programming Talk
---

### Post by likwid on 2008-09-03
Hi.

I'm having a lot of problems figuring out the best way to do this. 

Basically I want to iteratively update an object of varying depth, that is objects of objects of object etc which in fact are categories and sub-categories. 

The user selects categories and ajax downloads the data which is stored within its relevant categories. Ideally I would be able to store a pointer location, that is a reference to a location within the object but js doesn't support pointer semantics. 


For example, it would be convenient if I could do this:
```

function objBuild (someIds, newData){
  var st = '';
  for (var i in someIds){
     st = st + "[" + someIds[i] + "]";
  }
  obj+someIds = newData;
}  

```
But of course this obj+someIds results in a string, rather than a reference to an object within an object, or object of object of object etc. 

Alternately I considered:

```

function iter(obj, selCats, data){
  for (var x = 0; x < obj.length; x++){
    if (obj[x].id==selCats[x]){
      iter(obj[x], selCats, data);
      break;
    } 
  }
  obj[selCats[x]] = data;
}

```

But this would leave the original object untouched and only manipulate the copy.

If this isn't clear please let me know and i'll try explain better.

---

