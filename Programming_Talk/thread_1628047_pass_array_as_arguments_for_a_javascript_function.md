---
title: "pass array as arguments for a javascript function"
date: 2010-11-22
forum: Programming Talk
---

### Post by pradeepthundiyil on 2010-11-22
Hi,

I want to write a javascript function which takes an array as its arguments. The size of the array is not known. Here is the code snippet.

For example:
The function is supposed to receive 'n' student's name and use it inside the function. 

function attendanceList(name){ /*name is an array*/

var i;
var count = name.length;
stud = new Array();

for (i =0; i <count;i++) {
stud[i] = name[i];
console.log(stud[i]);
}

class: [' ', ' ', ' ', ' ', ' ', ' '] ;

} //func end


The problem is i need to fill the names of the students between the quotes in class: [' ', ' ', ' ', ' ', ' ', ' '] ;

Please provide a way to do this.

---

