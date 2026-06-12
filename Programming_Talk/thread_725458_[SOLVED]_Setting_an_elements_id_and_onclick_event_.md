---
title: "[SOLVED] Setting an elements id and onclick event from javascript?"
date: 2008-03-15
forum: Programming Talk
---

### Post by lucas4ce on 2008-03-15
I have a table which I am populating with rows, cells and information using javascript as below:

var c = document.getElementById('tableid');
var t = somearray.name.length;
var s = t+3;  // the top three rows remain unchanged
var v;
for(v=3;v<s;v++)
{	
  w = c.insertRow(v);	
  u=v-3;
  w.insertCell(0).innerHTML=somearray.name[u];	
  w.insertCell(1).innerHTML=somearray.data1[u];	
  w.insertCell(2).innerHTML=somearray.data2[u];
  w.insertCell(3).innerHTML=somearray.data3[u];
  w.insertCell(4).innerHTML=somearray.data4[u];
  w.insertCell(5).innerHTML=somearray.data5[u];
  w.insertCell(6).innerHTML=somearray.data6[u];
  w.insertCell(7).innerHTML=somearray.data7[u];
}

This works fine and creates the table correctly.

Now to the first question.....how do I assign an id to each row?

The id's will be something like tablerow0, tablerow1, tablerow2 etc.. so I could do this to create the id:

var str = "tablerow";
var rowid;

then in side the for loop...

rowid = str + u;  // this will use the variable u from above to create the id string "tablerow0" etc...

I'm just not sure how to assign the id correctly.  I've tried a couple of ways with no success.

And the second question....how do I assign an onclick event to each row?

The onclick event for each row will be the same, something like onclick = "tablerowpress(id)".  The tablerowpress(id) function is already written somewhere else to format the clicked rows.

Any help much appreciated.

---

### Post by mssever on 2008-03-15
```
the_row.id = 'some-id';
the_row.onclick = function () {
  // do stuff
};
```
If you don't have the row, but have the cell, somecell.parentNode shold get you the row (if my memory serves me right).

---

### Post by lucas4ce on 2008-03-15
thanks got it working now :)

---

