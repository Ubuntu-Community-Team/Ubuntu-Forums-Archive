---
title: "C, getting fgets() to carry on after \n"
date: 2012-08-03
forum: Programming Talk
---

### Post by scorpious on 2012-08-03
Is there a quick/easy way to get fgets() to carry on reading stdin after getting to a \n? 

I *could* write some code for it but the only way I can think of would be long, ugly and involve lots of embedded loops.

cheers

---

### Post by Odexios on 2012-08-03
Wouldn't just a while loop like this do the trick?

[php]
int i;
char c;
char *string = malloc(sizeof(char) * (dim + 1));

for (i = 0; i < dim && (c = getc(stream)) != EOF; i++) {
  string[i] = (char)c;
}

string[i] = '\0';

[/php]

There's no error checking and so on, of course.

---

### Post by scorpious on 2012-08-03
thanks for your reply Odexios. 

There's a few commands in there I'm unfamiliar with such as malloc and getc (only been programming for a few weeks now).  I will play around with your code a bit and see what I can do.

cheers

---

### Post by spjackson on 2012-08-04
If you simply want to read up to a fixed number of characters from a stream, it sounds like fread() might be what you want. e.g.
```

    bytes_read = fread(buffer, 1, buffer_size - 1, input_stream);
    if (bytes_read >= 0) {
        buffer[bytes_read] = '\0';
    }

```See "man fread".

---

### Post by Bachstelze on 2012-08-04
> **scorpious said:**
> Is there a quick/easy way to get fgets() to carry on reading stdin after getting to a \n? 


And when would you want it to stop, then? If you want to read a fixed number of characters, use fread as spjackson said (but be careful about the terminating NULL if you are working with strings). If you want to read a fixed number of lines, call fgets() repeatedly with a for loop.

---

