---
title: "javascript concat() method to join arrays"
date: 2009-09-21
forum: Programming Talk
---

### Post by tc101 on 2009-09-21
I am confused about using the concat() method to join two arrays.  In the example below, why does the first write show all 6 values in the array, but the second only shows 3?  How do I permanently join 2 arrays into 1?

<html>
<body>
<script type="text/javascript">

var arr = new Array(3);
arr[0] = "Jani";
arr[1] = "Tove";
arr[2] = "Hege";

var arr2 = new Array(3);
arr2[0] = "John";
arr2[1] = "Andy";
arr2[2] = "Wendy";

document.write(arr.concat(arr2));  // why does this show all 6 values 

document.write("<br>" + arr); // but this only shows 3

</script>
</body>
</html>

---

### Post by tc101 on 2009-09-21
I figured this out.  

The concat() method is used to join two or more arrays.

This method does not change the existing arrays, it only returns a
copy of the joined arrays.

Tom combine arr1 and arr2 into arr3 this works:


var arr3 = arr1.concat(arr2);
document.write("<br> arr3 = " + arr3);

---

### Post by The Cog on 2009-09-21
[http://www.w3schools.com/jsref/jsref_concat_array.asp](http://www.w3schools.com/jsref/jsref_concat_array.asp)

concat() creates a new third array without modifying the original two.

---

### Post by tc101 on 2009-09-21
Is there some way I can close or delete this thread since I have answered it?

---

