---
title: "cin.get()"
date: 2008-10-23
forum: Programming Talk
---

### Post by Flynn555 on 2008-10-23
ok i am trying to read one character from a file into an array
but when i use the following...
```

const int MAX = 10;

int table[MAX][MAX]
cin.get(table[0][0], 1);


```
i get this ... 
```

invalid conversion from 'int' to 'char*'

```
i also tryed to declare table as a char but that didnt work either...
it has been awhile since i have used cin.get so im confused.

---

### Post by tCarls on 2008-10-23
table[0][0] is a value, not an address. Use &table[0][0].

```

const int MAX = 10;
char table[MAX][MAX];
cin.get(&table[0][0], 1);

```

---

### Post by Flynn555 on 2008-10-23
ok...that did it. but do i have to declare table as a char?

---

### Post by tCarls on 2008-10-23
Well, you could declare it as int and cast it like "cin.get(reinterpret_cast<char *>(&table[0][0], 2);" (note I changed 1 to 2 because you need one space for the '\0' character), but I don't think that's what you want.

What are you trying to do? Are you trying to read numbers one character at a time and store them in an array? How about something like this:

```

int table[MAX][MAX];
char buf[2];
cin.get(buf, 2);
table[0][0] = atoi(buf);

```

---

### Post by dwhitney67 on 2008-10-23
> **tCarls said:**
> Well, you could declare it as int and cast it like "cin.get(reinterpret_cast<char *>(&table[0][0], 2);" (note I changed 1 to 2 because you need one space for the '\0' character), but I don't think that's what you want.

What are you trying to do? Are you trying to read numbers one character at a time and store them in an array? How about something like this:

```

int table[MAX][MAX];
char buf[2];
cin.get(buf, 2);
table[0][0] = atoi(buf);

```

A agree.  It is hard to determine what the OP wants (for instance, what type of data is being read, and what purpose is it for).

But if indeed he wants to read a character at a time into a char array, an alternative would be to use the single-arg version of get().

For instance:
[php]
char table[MAX][MAX];
char nl;
std::cin.get(table[0][0]);   // character is passed by reference
std::cin.get(nl);            // get the newline char
[/php]

If the array is defined as an array of ints, then:
[php]
int table[MAX][MAX];
char c, nl;
std::cin.get(c);         // get the single char
std::cin.get(nl);        // get the newline char
table[0][0] = c - '0';   // convert c to a number (note this will not function properly if c is not a numeric character digit from 0-9!)
[/php]

---

