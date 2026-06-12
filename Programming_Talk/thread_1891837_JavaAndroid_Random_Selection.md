---
title: "Java/Android: Random Selection?"
date: 2011-12-06
forum: Programming Talk
---

### Post by fallenshadow on 2011-12-06
Hi guys/gals,

I am trying to come up with a way to select a random word from an array of Strings and select a random letter of this word to be blank. For some reason my code is showing up an error

[PHP]
XML_ERROR_INCORRECT_ENCODING
[/PHP]

> String setWord = myString.get(new Random().nextInt(myLength));

Anyone know why this line won't be accepted?

---

### Post by PaulM1985 on 2011-12-06
It looks like you are using the get() function on myString, which is an array of Strings rather than a List of strings.  When using arrays, you have to use [] to get an element at an index.

Paul

---

### Post by fallenshadow on 2011-12-07
I changed it around to use an arrayList:

[PHP]
XML_ERROR_INCORRECT_ENCODING
[/PHP]

Although this solved the problem I was having Android crashes because it says the array size is too large and it runs out of memory.

---

