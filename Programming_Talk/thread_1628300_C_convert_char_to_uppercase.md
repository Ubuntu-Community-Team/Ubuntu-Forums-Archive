---
title: "C convert char* to uppercase"
date: 2010-11-22
forum: Programming Talk
---

### Post by Woody1987 on 2010-11-22
I am asking the user to input some text into a gtk_entry. What I want to do is take that input and convert the entire input to uppercase.

I have tried using toupper(), but I cant figure out how to get it to work. Having looked at some examples I came up with:
```
char *ptr = (char *)gtk_entry_get_text(GTK_ENTRY(pNameEntry));
while(*ptr)
{
    *ptr = toupper(*ptr);
    ptr++;
}
printf("%s", ptr);
```

But the printf at the end does not display anything.

---

### Post by Simian Man on 2010-11-22
That's because the pointer is incremented to the end of the string and left there.  You need to pass a pointer to the beginning of the string to printf.  Change the call to:

printf("%s", (char *)gtk_entry_get_text(GTK_ENTRY(pNameEntry)));

And it should work.

---

### Post by Woody1987 on 2010-11-22
hazaa! Thankyou.

---

