---
title: "C: string to binary"
date: 2011-02-28
forum: Programming Talk
---

### Post by Psycho.mario on 2011-02-28
Hi, I'm quite new to C so bear with me. I have an address in a string, which takes the form of (for example) "7c802446", Can somebody tell me how I can convert this from the string its in, to a string that is half the length, as the binary equivalent. What I mean is converting 7c802446 to \x7c\x80\x24\x46. I haven't explained this very well, ask extra questions if you need.

Thanks

---

### Post by schauerlich on 2011-02-28
You can use sscanf to read a hex number from a string. It might also be just as simple to do the conversion yourself.

---

### Post by Psycho.mario on 2011-02-28
```
    
    char test[4]; //output
    char *p, *q;
    for (p=adrlen,q=test; *p; p+=2,q++) { //adrlen is input
        sscanf(p, "%2x", q);
        }
    *q = '\0';
```

---

### Post by schauerlich on 2011-02-28
What if you have an odd-length string? You can't be guaranteed that anything but the last byte is 0 for a properly formed C string. The next byte after may be anything.

---

### Post by Psycho.mario on 2011-02-28
True... The actual program is for windows, and it gets its string from getprocaddress. all i need to do is prepend '0' until it gets to a length of 8. I thought it would be okay to post here becuase the actual question wasn't windows related.

---

### Post by foxmuldr on 2011-03-01
> **Psycho.mario said:**
> Hi, I'm quite new to C so bear with me. I have an address in a string, which takes the form of (for example) "7c802446", Can somebody tell me how I can convert this from the string its in, to a string that is half the length, as the binary equivalent. What I mean is converting 7c802446 to \x7c\x80\x24\x46. I haven't explained this very well, ask extra questions if you need.

Thanks

```

int result = foo("7c802446");

int foo(char* src)
{
    int length = strlen(src);
    int value = 0;
    for (i = 0; i < length; i++)
    {
        if (src[i] >= '0' && src[i] <= '9')
            value = (value << 4) + (src[i] - '0');
        else if (src[i] >= 'a' && src[i] <= 'f')
            value = (value << 4) + (src[i] - 'a' + 10);
        else if (src[i] >= 'A' && src[i] <= 'F')
            value = (value << 4) + (src[i] - 'A' + 10);
        else
            break;  // Some other character, we're done
    }
    return(value);
}
```

---

