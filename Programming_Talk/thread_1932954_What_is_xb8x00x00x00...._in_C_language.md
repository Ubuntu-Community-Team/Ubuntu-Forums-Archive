---
title: "What is \xb8\x00\x00\x00.... in C language"
date: 2012-02-28
forum: Programming Talk
---

### Post by c2tarun on 2012-02-28
Hi friends,

I was reading an article and I found this line of code for a C program.

```

static char abc[7]="\xb8\x00\x00\x00"
                           "\xff\xe0"

```

What is meaning of the code in double quotes?

---

### Post by r-senior on 2012-02-28
It's a series of hexadecimal escape sequences. Each '\xNN' represents the character with value NN in hexadecimal.

---

### Post by Bachstelze on 2012-02-28
Whoever wrote this code has no idea what they are doing. There is no guarantee that 0xb8, 0xff and 0xe0 will fit in a char.

---

### Post by alegomaster on 2012-02-28
> **Bachstelze said:**
> Whoever wrote this code has no idea what they are doing. There is no guarantee that 0xb8, 0xff and 0xe0 will fit in a char.

If it is declared unsigned, shouldn't it work. Also does C declare a char as signed when there is no unsigned or signed prefix in the declaration.

---

### Post by Bachstelze on 2012-02-28
> **alegomaster said:**
> If it is declared unsigned, shouldn't it work. Also does C declare a char as signed when there is no unsigned or signed prefix in the declaration.

It is implementation-defined whether char actually means signed char or unsigned char.

*EDIT:* It will work if it is declared unsigned, yes. Here it is not.

---

### Post by MG&amp;TL on 2012-02-28
> **Bachstelze said:**
> It is implementation-defined whether char actually means signed char or unsigned char.

Would I be right in thinking that passing compiler options would set the default char signed-ness? So...the article could suggest passing the -funsigned-char argument to gcc...but maybe I'm wrong.

---

### Post by Bachstelze on 2012-02-28
> **MG&TL said:**
> Would I be right in thinking that passing compiler options would set the default char signed-ness? So...the article could suggest passing the -funsigned-char argument to gcc...but maybe I'm wrong.

Yes, you're right. So... maybe, but I think that's quite unlikely.

---

