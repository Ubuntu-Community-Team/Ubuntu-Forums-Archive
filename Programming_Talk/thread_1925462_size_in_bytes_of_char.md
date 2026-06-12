---
title: "size in bytes of char *"
date: 2012-02-14
forum: Programming Talk
---

### Post by Xender1 on 2012-02-14
So I am trying to figure out the size of a char * array I have in bytes. I am just confusing myself by trying to figure this out because of:
```

sizeof(char) = 1
sizeof(char *) = 4

```
So I am going through my char * array like so
```

int i;
for (i=0;i<MAX_LEN;i++) {
  if (name[i] == '\0') break;
}
int byte_size = (i-1) * sizeof(char *);

```
I am just wondering if this byte_size would be correct. For example, name = "bob". so i would get 3 (b,o,b,\0), and then i-1 would be 2 for b,o,b. now is where i am confused, I assumed each char (b,o,b) took up size 1, but since I used a pointer for declaring name and made it type char *, does each b,o,b now have size 4? Thanks for the help and sorry if I am making this more confusing than it needs to be, just trying to find the size of a char * array for the valid data.

---

### Post by lisati on 2012-02-14
After a quick browse of your post:

**sizeof(char) = 1** refers to the size of a character

**sizeof(char *) = 4** refers to the size of a pointer to a character

---

### Post by muteXe on 2012-02-14
Because a pointer of any kind is an integer. It just holds a number - a memory address.

---

### Post by Xender1 on 2012-02-14
Oh okay, so the size of the pointer name is 4, which is size of int so that makes sense. so after I find the length of valid chars in my name pointer (etc. b,o,b,\0), I take my i counter and that is the number of bytes that the chars are taking up and multiply by sizeof(char) which since its just 1, the byte size will just be i.

---

### Post by gateway67 on 2012-02-14
> **Xender1 said:**
> Oh okay, so the size of the pointer name is 4, which is size of int ...

This is a bad comparison.  I pointer on a 32-bit system does take up 4 bytes, but on a 64-bit system it takes up 8 bytes.  Thus comparing it to the size of an int is wrong.

> **Xender1 said:**
> 
... I find the length of valid chars in my name pointer (etc. b,o,b,\0), I take my i counter and that is the number of bytes that the chars are taking up and multiply by sizeof(char) which since its just 1, the byte size will just be i.
Use strlen() to find the length of a string.  Or perhaps something that's equivalent.  You were on the right track in your opening post, however confusing the size of a pointer with the size of a char (byte) is the issue.

Consider this:
```

size_t myStringLength(const char* str)
{
    size_t size = 0;

    if (str != NULL)
    {
        while (*str++ != '\0') ++size;
    }

    return size;
}

```

---

### Post by Bachstelze on 2012-02-14
Also do not confuse the *size* of an array and the *length* of a string. The size of an array is the amount of memory you allocate to it. If you store a string in an array of size n, the length of the string can be anything between 0 and n-1.

*EDIT:* So if you want to know how much memory your string takes (e.g. if you want to know how much memory you must allocate if you want to store a copy of it), it is important that you do count the terminating null. Something like this is wrong:

```
int n = strlen(mystring);
char *mynewstring = malloc(n);
strncpy(mynewstring, mystring, n);
```

It should be

```
int n = strlen(mystring);
char *mynewstring = malloc(n+1);
strncpy(mynewstring, mystring, n);
```

---

