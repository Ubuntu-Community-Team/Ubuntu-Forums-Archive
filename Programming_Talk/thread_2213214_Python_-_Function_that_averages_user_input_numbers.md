---
title: "Python - Function that averages user input numbers."
date: 2014-03-25
forum: Programming Talk
---

### Post by Yozuru on 2014-03-25
Hello good people,

I am working on a function that prompts a user for a numerical character and ends when a non-numerical character is inputted. 

In my code, I managed to get it to prompt for a number, but afterwards it does not work. 

Here is a pastebin of my code: [HTML]http://pastebin.com/SVrRmugs[/HTML]

Many thanks in advance for any help.

Edit: Solved. Many thanks for the input everyone!

---

### Post by Vaphell on 2014-03-25
how can you calculate anything from L if you don't save anything in it?

---

### Post by kostkon on 2014-03-25
Put your call to input inside the while loop and as Yozuru already said, don't forget to save the values you are getting from the user in L.

---

### Post by EddyDreizehn on 2014-03-30
You have: 
```
List = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

Try this: 
```
List = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
```

A value like 0 is not the self like ascii character "0" 

value 0 is in binary 0000h
character "0" is in binary 0030h

:guitar:

Tell me, when it works!

---

### Post by Yozuru on 2014-04-06
Ahh that makes a lot of sense! Many thanks for your help. (:

---

