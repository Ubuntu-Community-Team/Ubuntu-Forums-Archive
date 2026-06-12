---
title: "c++ convert from char[] to hex"
date: 2010-02-20
forum: Programming Talk
---

### Post by Woody1987 on 2010-02-20
I want to convert an array of chars comprising of numbers, no letters into an array of hexadecimal numbers which i assume will have to be of type string.

My arrays are:
char buffer[10]
string bufHex[10]


so if buffer[0] = '101', then bufHex[0] = "65"

How do i do this?

---

### Post by H4F on 2010-02-20
char temp[16];
tempValue[0] = 0;
// put below in a loop for each character
sprintf(temp,"0x%04X, ", Buffer[i]);
strcat(tempValue, temp);

not sure if that will work

---

### Post by geirha on 2010-02-20
```

stringstream ss;
ss << hex << (int)buffer[0];
bufHex[0] = ss.str();

```

---

### Post by djbushido on 2010-02-20
I'm not sure if you are working with numbers that you need to go about converting - the array indexes/values can be accessed the same way - just add "0x" to the beginning - saying "somearray[0xA]" is the same as "somearray[10]".
I could be wrong/misunderstanding the question, but I'm pretty sure that's how it works.

---

### Post by Woody1987 on 2010-02-20
Got it working.

```
char buffer[10];
char bufHex[10];

for(j = 0; j < 10; j++)
    sprintf(bufHex, "%X", buffer[j]);
```

---

### Post by dwhitney67 on 2010-02-20
> **Woody1987 said:**
> Got it working.

```
char buffer[10];
char bufHex[10];

for(j = 0; j < 10; j++)
    sprintf(bufHex, "%X", buffer[j]);
```

Nice C code!

---

### Post by Woody1987 on 2010-02-20
> **dwhitney67 said:**
> Nice C code!

If it works, it works.

---

### Post by geirha on 2010-02-20
> **Woody1987 said:**
> If it works, it works.

But does it? You are overwriting bufHex over and over. In the end it'll just contain the hex string of buffer[9] ...

---

### Post by Woody1987 on 2010-02-20
> **geirha said:**
> But does it? You are overwriting bufHex over and over. In the end it'll just contain the hex string of buffer[9] ...

every iteration i do something with bufhex, so it doesnt matter if it gets overwritten.

---

