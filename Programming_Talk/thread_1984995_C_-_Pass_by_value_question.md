---
title: "C - Pass by value question"
date: 2012-05-22
forum: Programming Talk
---

### Post by stamatiou on 2012-05-22
I have read in a c book this function
```

int count_spaces(const char *s)
{
  int count = 0;

  while (*s)
    if (*s++ == ' ')
      count++;
  return count;
}

```
But if I call it won't the string be passed by reference?

---

### Post by Bachstelze on 2012-05-22
C does not have pass-by-reference. Everything is passed by value. Here you pass the value of the pointer.

---

### Post by Majorix on 2012-05-22
Here you are not modifying the s string, however you could have perfectly well done so. As Bachstelze has pointed out there is no "pass-by-reference" in C but you can still act like there is and modify the variables/types directly if you have pointers to the said objects in your functions.

---

### Post by stamatiou on 2012-05-22
> **Majorix said:**
> Here you are not modifying the s string, however you could have perfectly well done so. As Bachstelze has pointed out there is no "pass-by-reference" in C but you can still act like there is and modify the variables/types directly if you have pointers to the said objects in your functions.
After the function call, the pointer will point to the end of the string?

---

### Post by trent.josephsen on 2012-05-22
> **stamatiou said:**
> After the function call, the pointer will point to the end of the string?

Yes. The **local copy** of the pointer will point to the end of the string. But the **pointer** was passed by value; you can't change the "original thing" that was passed because you don't have the "original" copy. (Clarification: the pointer local to the function is changed, which goes out of scope when the function returns, so in your calling code, the function call has no side effects; thus "No" is probably a better answer, but I'm trying to make a point here.)

You can change the **string** that the pointer points to, because the **value** that was passed to the function **is a pointer** to the actual string object.

Again, C doesn't have pass-by-reference. C has **values** that can **be** references, but they're *still passed by value*.

---

### Post by Majorix on 2012-05-22
> **stamatiou said:**
> After the function call, the pointer will point to the end of the string?

No, it never does. The name of the string is actually a pointer to the first character in the string. If your string was named "myStr" then "myStr == &myStr[0]".

---

### Post by pellyhawk on 2012-05-22
```

void main()
{
   ...
   char *ptr;
   ...
   count_spaces(ptr);
   ...
}

```

After calling count_spaces(), ptr is still pointer to the original address.

> **stamatiou said:**
> I have read in a c book this function
```

int count_spaces(const char *s)
{
  int count = 0;

  while (*s)
    if (*s++ == ' ')
      count++;
  return count;
}

```
But if I call it won't the string be passed by reference?

---

### Post by trent.josephsen on 2012-05-22
It's **int main(void)**

---

### Post by stamatiou on 2012-05-23
Thank you all for the quick replies!

---

