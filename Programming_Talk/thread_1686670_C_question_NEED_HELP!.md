---
title: "C question NEED HELP!"
date: 2011-02-12
forum: Programming Talk
---

### Post by meet_123 on 2011-02-12
Suppose we have a const without any spaces null terminated  char string that is 9070002043

I have a Question How would u divide into certain desire and store into 3 arrays with there sizes like
in
char a[5]
char b[8]
char c[7]
 I am really stucked in this part

My idea is to find out the length of the string via stlen and use
char str[20] = "9070002043"
for(i = 0; i <  strlen(str); i++){
if(strlen(str) < 5){
    a[5] = str[i] + "" ;
}
something like that I need suggestion if u guys have plz reply

---

### Post by Some Penguin on 2011-02-12
Why don't you execute your proposed solution, by hand, and work out what would happen.

---

