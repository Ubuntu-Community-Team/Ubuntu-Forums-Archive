---
title: "javascript indexOf() method"
date: 2014-04-13
forum: Programming Talk
---

### Post by AstroLlama on 2014-04-13
Hi everyone, I'm stumpted on this problem! I spent the last few hours looking for a solution, but to no avail. 

On a site I'm working on users click a button to send the button's ID to a function: selection(id).
A cookie is stored: the IDs of the buttons clicked.
The function checks to see if the newly-clicked ID is already present in the cookie. A new entry is accepted and a repeat entry is rejected.
The cookie is updated and rewritten.

```
function selection(id) {
  var cookie_clone = document.cookie;           //  copy the cookie value. cookie_clone in this case is a string.
  var cookie_value = cookie_clone.slice(8);     //  cut out the key name of the cookie "choices="
  var cookie_pieces = cookie_value.split(',');   //  split the comma-separated values into the array cookie_pieces.

  if (cookie_pieces.length <= 2 && cookie_pieces.indexOf(id) == -1 ) {     // if there are two or fewer entries in the cookie_pieces array, AND if the function parameter is absent from the array... 
    cookie_pieces.splice(0, 0, id);    // add the id into the array
    }
  else if (cookie_pieces.length >= 3 && cookie_pieces.indexOf(id) == -1 ) {     // If there are 3 or more array entries AND if the ID passed from the button isn't found...
    cookie_pieces.pop();        //   remove the last entry
    cookie_pieces.splice(0, 0, id);       // and add the new one at the beginning.
    }
  else {
//    continue;
    }
    document.cookie = "choices=" + cookie_pieces;
    document.getElementById('text').innerHTML=document.cookie;
  }
```

The indexOf() method repeatidly returns true, even if you click several time and populate the cookie with duplicate entries... can anybody see where the hang up is?

---

### Post by pqwoerituytrueiwoq on 2014-04-13
cookie_pieces is a array not a string
indexOf does work with arrays in modern browsers, but it in old stuff

your best best is to use a in array function (below)
```
if(inArray(cookie_pieces,id))
  //found it
else
  //not there
```
```
function inArray(arr,val){
    if((arr.constructor==Array)===false){
        if(arr.toString().indexOf(',')!=-1){
            arr=arr.split(',');
        }
        else{
            if(arr==val){
                return true;
            }
            else{
                return false;
            }
        }
    }
    for(var i=0;i<arr.length;i++){
        if(arr[i]==val){
            return true;
        }
    }
    return false;
}
```

---

### Post by AstroLlama on 2014-04-23
Thanks for the reply! It was very helpful and gave me an insight into what I was trying to do. :)

---

