---
title: "acces bidimensional array data form from JavaScript"
date: 2012-11-08
forum: Programming Talk
---

### Post by chuchi on 2012-11-08
Hi there!!! I want to access a bidimensional array in a form from javaScript, but I do not know how to do that. this is the form

```


<td><input   type="text" name="tn['.$elem['id'].'][]" value="'.$elem['name'].'" />  </td>


```
As you can see, it is PHP code that generates several input form. What I want to get is the array "tn" in JavaScript, because I need to check that the text is not empty

thanks a lot!

---

### Post by atkrad on 2012-11-08
Hello
Why do not checking in PHP?

---

### Post by chuchi on 2012-11-08
Because what I want to do is to check the values before loading a new page, so I must do that using JavaScript.

---

### Post by Dimarchi on 2012-11-10
An arbitrary amount of generated input fields, depending on the size of of an array? Input field name does not matter, but value does? Not quite sure about the question, but here goes...

How about wrapping those generated inputs in an element and using Javascript to parse the values of the input fields within that element and checking their value? Or, if the case is what it looks like, give those td cells some class name and using Javascript, look for those td cells with that class name and parse the values of input fields within those cells.

Did I understand what you're going after correctly?

---

### Post by chuchi on 2012-11-12
Hi there!! thank you very much for your response. that would be a good solution. But actually, all the data came from the server, so I will form an array in Javascript using the data from PHP.

thank you very much!

---

