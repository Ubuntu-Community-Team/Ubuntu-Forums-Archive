---
title: "C question: Using field-size in scanf()"
date: 2009-10-23
forum: Programming Talk
---

### Post by rbaleksandar on 2009-10-23
Hi, guys. :)


  Well, I have been pocking around with SCANF() and in particular - field-size and bypass-operator '*' (I call it that way, 'cause it works like that and frankly I don't know the real name of this :D).
  In order to verify if I'm correct, I read in a book (from Herbert Shield). It says that:

> You can specify a maximum size of a field to all specificators except %c, for which the field is always 1 character, and %n, which is not included in the set of input specificators.

  So according to this and to my logic the following code should give an error when compiling or be compiled but do nothing or give an error when executing:

Note:
int first, second

```

scanf("%d%*10c%d", &first, &second);

```

  A character is only one symbol. So you can't specify a max. field-size of one single character right? Well, I thought so too, but apparently my compiler (GCC) doesn't agree with me and if I enter for example 1234aBcDeFg5678, I get:

first = 1234
second = 5678

  Now the question is why it works? If it was
```

%*10s

```
  I would agree since we talk about a string (in C - array of characers). Is it possible that, when the compiler encounters %*10c, it creates an array of characters? :confused:

Thanks in advance.

---

### Post by Arndt on 2009-10-23
> **rbaleksandar said:**
> Hi, guys. :)


  Well, I have been pocking around with SCANF() and in particular - field-size and bypass-operator '*' (I call it that way, 'cause it works like that and frankly I don't know the real name of this :D).
  In order to verify if I'm correct, I read in a book (from Herbert Shield). It says that:



  So according to this and to my logic the following code should give an error when compiling or be compiled but do nothing or give an error when executing:

Note:
int first, second

```

scanf("%d%*10c%d", &first, &second);

```

  A character is only one symbol. So you can't specify a max. field-size of one single character right? Well, I thought so too, but apparently my compiler (GCC) doesn't agree with me and if I enter for example 1234aBcDeFg5678, I get:

first = 1234
second = 5678

  Now the question is why it works? If it was
```

%*10s

```
  I would agree since we talk about a string (in C - array of characers). Is it possible that, when the compiler encounters %*10c, it creates an array of characters? :confused:

Thanks in advance.

I actually get

first = 1234
second = 8

for that input, so it skipped 10 characters, rather than 7.

---

### Post by rbaleksandar on 2009-10-23
Thanks for the reply.

It seems that every time a call it and enter the same string, a different thing appears. :D Another strange thing:

```

scanf("%d%*10**s**%d", &first, &second);

```

  Enter 1234abcdef5678 and see what happens. :confused:

---

### Post by dwhitney67 on 2009-10-23
Some possibilities to consider:  either Herbert Shield is wrong, or his information is outdated/obsolete, or you are taking him too literally.

If you attempt to place a number before the 'c', such as "%4c", then you will get a compiler warning (if -Wall is used).  If using a format such as "%*4c", apparently the asterisk somehow convinces the compiler that your intent to to specify how many characters you want ignored from the input stream.

So if you enter "1234abcd5678", and you use a format specifier such as "%d%*5c%d", your first number will be 1234, and the second will be 678.  Note 5 characters, "abcd5", were skipped because of the "%*5c" portion of the format specifier.

---

### Post by Arndt on 2009-10-23
> **rbaleksandar said:**
> Thanks for the reply.

It seems that every time a call it and enter the same string, a different thing appears. :D Another strange thing:

```

scanf("%d%*10**s**%d", &first, &second);

```

  Enter 1234abcdef5678 and see what happens. :confused:

It seems to skip 10 characters and then want to read a number, which isn't supplied in the input. But if you enter 1234abcdef56789, it makes second=9.

To better see what scanf thinks it is doing, print out the return value. It's the number of fields actually assigned.

---

### Post by rbaleksandar on 2009-10-23
How can I take this sentence too literally? :D As for the outdated-part - maybe, the book's from 1997. :D

  Ok, so I always have to enter as many character as my field-size is in order to avoid the situation where scanf() takes part of my integers as character.


  Thanks a lot, mates. :)


PS: Arndt, it returns **1**. As far as I remember, if there's something wrong it should return EOF (that is -1), right?

  The thing returns 2 if I use %*20s and enter "1234-------------------5678" (there are 19 "-"). As for FIRST and SECOND they're both 1234...Bah...


EDIT: Problem solved.
If I enter exactly the same number of characters that I set to be the field-size, I get a correct answer. Though the problem with %*c with a field-size is still a problem, but obviously it doesn't work, which is good. :D

---

### Post by Arndt on 2009-10-23
> **rbaleksandar said:**
> How can I take this sentence too literally? :D As for the outdated-part - maybe, the book's from 1997. :D

  Ok, so I always have to enter as many character as my field-size is in order to avoid the situation where scanf() takes part of my integers as character.


  Thanks a lot, mates. :)


PS: Arndt, it returns **1**. As far as I remember, if there's something wrong it should return EOF (that is -1), right?

No, if it assigned both 'first' and 'second', it returns 2. 1 means there was not input enough for 'second'.

---

### Post by rbaleksandar on 2009-10-23
Thanks a LOT! :)

---

