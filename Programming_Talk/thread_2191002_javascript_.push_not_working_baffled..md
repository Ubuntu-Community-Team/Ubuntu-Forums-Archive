---
title: "javascript .push not working? baffled."
date: 2013-11-30
forum: Programming Talk
---

### Post by maclenin on 2013-11-30
I am using this [.push "method"]("http://stackoverflow.com/questions/16227197/compute-intersection-of-two-arrays-in-javascript") to try and find the **common** "intersection" between **subArray1** and **subArray2**.

**subArray1** and **subArray2** are created, "dynamically", as subsets of **mainArray**.

Here's the script, which when run...
```
var i, j;
var **mainArray** = [1, 2, 3, 4, 5, 1, 2, 3, 4, 5];
var one, two; // arguments through which I pass the value(s) of subArray to the findCommon function
var **common** = [];

function createsubArrays() {
    var **subArray1** = [];
    var **subArray2** = [];
    **subArray1**.push**(mainArray**.slice(0, 3)); // [1, 2, 3]
    **subArray2**.push(**mainArray**.slice(4, 7)); // [5, 1, 2]
    findCommon(**subArray1**, **subArray2**);
}

function findCommon(one, two) {
  for (i = 0; i < one.length; i += 1) {
    for (j = 0; j < two.length; j += 1) {
      if (one[i] === two[j]) { **// it seems this "if" statement is being evalutated as FALSE, where it "should" be evaluating TRUE for the values 1 and 2**
        **common**.push(one[i]);
}}}
document.body.innerHTML += "one = " + one + "<br>" + "two = " + two + "<br>" + "common = " + **common** + "<br>";
}

createsubArrays();
```
...yields:
```
one = 1,2,3
two = 5,1,2
common = 

```
HOWEVER, I am looking for:
```
one = 1,2,3
two = 5,1,2
common = **1,2**
```
Why does the script NOT evaluate / show values for **common**?

Thanks for any insight.

---

### Post by The Cog on 2013-11-30
Slice returns an array. You are pushing the 3-element slice into an empty array, producing an array that contains one element - the slice, like this: [[1,2,3]]

Try this:
```
function createsubArrays() {
    var subArray1 = mainArray.slice(0, 3); // [1, 2, 3]
    var subArray2 = mainArray.slice(4, 7); // [5, 1, 2]
    findCommon(subArray1, subArray2);
}
```

---

### Post by maclenin on 2013-12-01
**The Cog!**

Thanks very much for the clarification + suggestion.

Your rewrite works perfectly with the code posted in my OP and is, fundamentally, the answer I was looking for....

HOWEVER, my "live" version of the process adds a wee "twist"...
```
if (**x** !== 0) {
    for (i = 0; i < **mainArray**.length; i += 1) {
        if(**mainArray**[i].indexOf(**x**) !== -1) {
        **subArray1** = **mainArray**[i].slice(0,1);
        }
    } 
}
```
...where **x** is a value to be searched for in **mainArray**.

**mainArray** can be made up of 1 or more arrays.

**x** can appear 1 or more times in **mainArray**.

For example, given...
```
**mainArray** = [[**"dogA"**, "gray", **"herding"**, "large"], [**"dogB"**, "black", **"herding"**, "medium"], ["dogC", "gray", "terrier", "small"]];
```
...if the (selected) value of **x** is **"herding"**, the value of **subArray1** will be **"dogA"** AND **"dogB"**.

The issue is, though I am able to iterate / slice the values **"dogA"** and **"dogB"** into **subArray1**, the values are being replaced rather than appended. So, the yeild is...
```
[**"dogB"**]
```
...rather than (**the result I seek**):
```
**["dogA"**, **"dogB"**]
```
I am thinking some form of closure is the solution...but not quite certain how to execute!

Thanks, again, for your guidance!

---

### Post by maclenin on 2013-12-03
I think I have rustled up a "solution" to address the iterative twist of my "live" version.
```
if (x !== 0) {**var xx = -1;**
    for (i = 0; i < mainArray.length; i += 1) {
        if(mainArray[i].indexOf(x) !== -1) {**xx += 1;**
        subArray1**[xx]** = mainArray[i].slice(0,1).**toString();**
        }
    } 
}

```
1. I use the **.toString()** method to convert / return each sliced value of x from mainArray to / as a like-kind / comparable "plain text" object / type / string.
2. I then iterate / append the "vanilla" string (in)to subArray1 using a **counter** initialized near the top of the function.

The resultant subArray1 then takes the form I seek:
```
**["dogA", "dogB"]** // and NOT ["dogB"] or [["dogA"], ["dogB"]]
```
**Woof!**

Thanks to **The Cog**, for redirecting....

---

