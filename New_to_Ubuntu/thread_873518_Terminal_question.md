---
title: "Terminal question"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mdmytryk on 2008-07-29
Im pretty new to linux and was trying to play around with the terminal to familiarize myself with some of the basic commands, when i ran into a (probably very simple) problem. I was attempting to delete a file named cimg3225 (copy).jpg.  When i type rm cimg3225 (copy).jpg to delete the file, i get this error: bash: syntax error near unexpected token `(' .  I

Now i if i were to delete the original, cimg3225.jpg, i have no problems. What am i doing wrong here, how do i delete a file containing parentheses in the filename?

Also, i know hitting tab will auto-complete the file name, but it doesnt seem to do this with files containing parentheses. Any help would be great.

I hope my question made sense, its 4am and im not thinking clearly.

---

### Post by iaculallad on 2008-07-29
> **mdmytryk said:**
> Im pretty new to linux and was trying to play around with the terminal to familiarize myself with some of the basic commands, when i ran into a (probably very simple) problem. I was attempting to delete a file named cimg3225 (copy).jpg.  When i type rm cimg3225 (copy).jpg to delete the file, i get this error: bash: syntax error near unexpected token `(' .  I

Now i if i were to delete the original, cimg3225.jpg, i have no problems. What am i doing wrong here, how do i delete a file containing parentheses in the filename?

Also, i know hitting tab will auto-complete the file name, but it doesnt seem to do this with files containing parentheses. Any help would be great.

I hope my question made sense, its 4am and im not thinking clearly.

Try:

```
rm cimg3225\ (copy).jpg
```

---

### Post by Bachstelze on 2008-07-29
> **mdmytryk said:**
> 
Also, i know hitting tab will auto-complete the file name, but it doesnt seem to do this with files containing parentheses.

It should. Otherwise, you can either use backslashes to escape the spaces and perentheses:

```
rm cimg3225\ \(copy\).jpg
```

or put the filename between quotes, like:

```
rm "cimg3225 (copy).jpg"
```

---

### Post by hyper_ch on 2008-07-29
or the most elegant way is to use TAB completion:

start with
```

rm cimg

```

and then press TAB --> if it doesn't autocomplete, press TAB again to see a list of possible file/directory names ;)

---

### Post by mdmytryk on 2008-07-29
Appreciate the help!

---

