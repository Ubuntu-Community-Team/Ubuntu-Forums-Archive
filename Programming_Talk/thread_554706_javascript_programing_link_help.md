---
title: "javascript programing link help"
date: 2007-09-19
forum: Programming Talk
---

### Post by zach12 on 2007-09-19
HI
i'm a bit of newby at javascript
and have coded a lil RPG game
but i'm trying code a script that will open a link when you hit the 3 key
> 
function getkeypress(keypress) {



 keyp = (isNS || isNS6) ? keypress.which : window.event.keyCode;

 if (keyp == 56) p1y = -1;  //K8

 if (keyp == 50) p1y = 1;   //K2

 if (keyp == 52) p1x = -1;  //K4

 if (keyp == 54) p1x = 1;   //K6

 if (keyp == 55) {p1x = -1;p1y = -1;} //K7

 if (keyp == 57) {p1x = 1;p1y = -1;}  //K9

 if (keyp == 49) {p1x = -1;p1y = 1;}  //K1

 if (keyp == 51) //k3


  

     
return false;

}
if you could give me a hand with this 
thanks

---

### Post by LaRoza on 2007-09-19
```
window.location = "http://larzoa.pbwiki.com";
```

You can use window.open, for more options.

---

### Post by zach12 on 2007-09-19
i keep geting a error message with window open

---

### Post by zach12 on 2007-09-19
thanks for your help:)

---

### Post by LaRoza on 2007-09-19
> **zach12 said:**
> thanks for your help:)

No problem. window.open() takes several arguments, an it is easy to make an error. Also, it depends on the browser, use the standards. .location is what you want here probably.

---

