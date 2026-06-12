---
title: "User input as a variable"
date: 2013-09-28
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-09-28
Hi Guys,

I understand that I can use 

```


read -p "Enter a name for a DVD you want to make: " name

```

This works for a single word or words separated by underscore, but how can I allow multiple words separated by spaces to be used as the variable name?

That is Come Home Snoopy instead of Come_Home_Snoopy?

---

### Post by Lars Noodén on 2013-09-28
You might be able to try playing with the Internal Field Separator (IFS) at the beginning of your script.  But usually if you have to change that, you are probably going about things the wrong way.  You may be stuck with underscores.  I would.

---

### Post by steeldriver on 2013-09-28
isn't it just a matter of quoting your variables properly when you come to use them?

```

$ read -p "Enter some stuff: " myvar
Enter some stuff: here is some stuff
$ echo "$myvar"
here is some stuff

```

EDIT: you question asks about using spaces in the variable NAME but your example appears to be about using spaces in the variable VALUE

---

### Post by GrouchyGaijin on 2013-09-28
> **steeldriver said:**
> isn't it just a matter of quoting your variables properly when you come to use them?

```

$ read -p "Enter some stuff: " myvar
Enter some stuff: here is some stuff
$ echo "$myvar"
here is some stuff

```

EDIT: you question asks about using spaces in the variable NAME but your example appears to be about using spaces in the variable VALUE

Hmmm I thought I had tried that and was stil getting the error that each word was being read as an individual file.
Actually what this is for, is I'm asking what the user wants to call the DVD.  I was storing their input in a variable I called name.

I'll try again, perhaps I didn't quote correctly.

---

### Post by steeldriver on 2013-09-28
Well normally 'read' should read everything up to the newline - it will assign whitespace-separated words to a single variable if that's all you give it, but will split into individual tokens if you either

1. give it multiple variables to assign to e.g.
```

$ read -p "Enter some stuff: " **myvar1 myvar2 myvar3**
Enter some stuff: here is some stuff
$ echo "$myvar1"
here
$ echo "$myvar2"
is
$ echo "$myvar3"
some stuff

```

(notice that since I didn't give it enough vars for all the individual words, the last 2 get assigned to 1 variable); or

2. you use the array form e.g.
```

$ read -p "Enter some stuff: " **-a myarray**
Enter some stuff: here is some more stuff
$ echo "${myarray[0]}"
here
$ echo "${myarray[1]}"
is
$ echo "${myarray[2]}"
some
$ echo "${myarray[3]}"
more

```

---

### Post by GrouchyGaijin on 2013-09-28
Thank you!
The "$myvariable" was the key.

---

