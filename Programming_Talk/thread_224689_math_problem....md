---
title: "math problem..."
date: 2006-07-28
forum: Programming Talk
---

### Post by kintarooe on 2006-07-28
ver= grep -o --quiet -m 1 -E "(\+|-)?([0-9]+\.?[0-9]*|\.[0-9]+)([eE](\+|-)?[0-9]+)?" ~/Desktop/control

nver= echo "scale=10; $ver + .01" | bc

the code above is suppose to capture a version number <ex. 1.24> from the control file, increment by .01, so that it can replace the old version number automatically. the first part works fine with capturing the number but incrementing seems to be a problem. It give me (standard_in) 1: parse error when i attempt to increment. Anybody know what I am doing wrong?

---

### Post by rocketman768 on 2006-07-28
You can't add a value to a string. I.e. the variable "ver" contains a string: '1.21' or something. In this case, a string of 4 characters. You can't add a value to a string. You can only add values to values. So, you must use the appropriate command to convert the string to a value (parse-ing a string), or you must write something to change the individual characters within the string.

---

### Post by LordHunter317 on 2006-07-28
Err no, that's not it at all, since bc only takes textual input.  This is the shell, ***everything*** is a string. 

Anyway, your error is that $ver doesn't contain what you think it does.

But doesn't the devtools have a thing that can automatically increment versions numbers?  And is it a really big deal to do this manually given how much other manual work you have to do anyway?

---

### Post by kintarooe on 2006-07-28
What devtools might you be referring to?? This is not really for my use, im just trying to build a script for the webmaster. I just maintain the servers.

---

### Post by psykotic on 2006-07-29
The other guy is right: $ver doesn't contain what you expect it to contain. It contains the literal text on the right-hand side of the assignment statement, not whatever was written to standard output as a result of executing the text via the shell. Anyway, if you're using bash you should change

ver=stuff

to

ver=$(stuff)

and it should work as expected.

---

### Post by kintarooe on 2006-07-31
thanks guys for the support.

---

