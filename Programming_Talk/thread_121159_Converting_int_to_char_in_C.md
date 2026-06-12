---
title: "Converting int to char in C"
date: 2006-01-24
forum: Programming Talk
---

### Post by ItsMe1989 on 2006-01-24
Hi everyone,

I cant work out how to convert a int into a char using c. Help would be appreciated.

:) 

Cheers,
Andrew

---

### Post by LordHunter317 on 2006-01-24
I'm confused?  You want to represent an integer as a character string?  If so, sprintf would be the most trival way.

---

### Post by ItsMe1989 on 2006-01-24
i have carried out some mathematical operations on a int, and i need to put it into a char variable.

---

### Post by Viro on 2006-01-24
A char can only hold the values between 0 and 255 (or -128 and 127 if it is signed), and an int can hold anything from -2 million to +2 million. You can't convert an int to a char unless you are sure you won't go out of range.

Instead, if you want to convert an int to a character string, you could take a look at sprintf. Here's a simple example that converts the value 45 into a string.

```

int i = 45;
char msg[80];
sprintf(msg, "%d", i);

```

---

### Post by LordHunter317 on 2006-01-24
[QUOTE=Viro]A char can only hold the values between 0 and 255 (or -128 and 127 if it is signed), and an int can hold anything from -2 million to +2 million. You can't convert an int to a char unless you are sure you won't go out of range.[/quote]Nitpick.  Neither of those will necessarily be true, everywhere C will runs.  They will be true on most platforms, however.

I only bring this up because making these assumptions can yield further problems down the road if you aren't careful.

---

### Post by ItsMe1989 on 2006-01-24
many thanks, all i want the char to do is store the number thats in the int, say 4000 so str[1]=4, str[2]=0 etc.

Is this possible?

Cheers.

---

### Post by Lord Illidan on 2006-01-24
> **Viro]A char can only hold the values between 0 and 255 (or -128 and 127 if it is signed), and an int can hold anything from -2 million to +2 million. You can't convert an int to a char unless you are sure you won't go out of range.

Instead, if you want to convert an int to a character string, you could take a look at sprintf. Here's a simple example that converts the value 45 into a string.

```

int i = 45 said:**
> ;
sprintf(msg, "%d", i);

```

I am not a programmer myself, but can't char store strings? or is it only in C++ .. I distinctly remember using strings in C++ with char.

---

### Post by jerome bettis on 2006-01-24
[quote=ItsMe1989]many thanks, all i want the char to do is store the number thats in the int, say 4000 so str[1]=4, str[2]=0 etc.

Is this possible?

Cheers.[/quote]

yes the code that was posted above is exactly how you do it

int i = 45;
char msg[80];
sprintf(msg, "%d", i);
printf("%s\n", msg);

45

---

### Post by Viro on 2006-01-24
[QUOTE=LordHunter317]Nitpick.  Neither of those will necessarily be true, everywhere C will runs.  They will be true on most platforms, however.

I only bring this up because making these assumptions can yield further problems down the road if you aren't careful.[/QUOTE]

Of course, all the size of data types are dependent on the platform it is run on, but given that ItsMe1989 is probably running Ubuntu Linux, on a 32 bit machine, it was a safe assumption to make ;).

---

### Post by ItsMe1989 on 2006-01-25
Cheers guys, i understand now!

---

