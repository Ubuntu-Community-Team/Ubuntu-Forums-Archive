---
title: "dlopen and Unicode"
date: 2009-11-12
forum: Programming Talk
---

### Post by WitchCraft on 2009-11-12
Question:

As you may or may not know, the definition of dlopen is:
```

void *dlopen(const **char** *filename, int flag);

```
which works fine for ASCII.

Now what I wanted to know (and google doesn't answer):
Is there anything like a unicode version of dlopen, for example something like
```

void *dlopen(const [COLOR="Red"]**wchar_t**[/COLOR] *filename, int flag);

```
?

---

### Post by Arndt on 2009-11-12
> **WitchCraft said:**
> Question:

As you may or may not know, the definition of dlopen is:
```

void *dlopen(const **char** *filename, int flag);

```
which works fine for ASCII.

Now what I wanted to know (and google doesn't answer):
Is there anything like a unicode version of dlopen, for example something like
```

void *dlopen(const [COLOR="Red"]**wchar_t**[/COLOR] *filename, int flag);

```
?

I don't think one is needed, any more than there are separate versions of 'creat' or 'open'. You give the same string to 'dlopen' as you did when you created the file. Linux as such doesn't interpret the byte sequence in any other way than using '/' as directory delimiter and Nul for ending the string, and neither can occur as part of a multibyte Unicode UTF-8 character (I think).

---

### Post by WitchCraft on 2009-11-12
> **Arndt said:**
> I don't think one is needed, any more than there are separate versions of 'creat' or 'open'. You give the same string to 'dlopen' as you did when you created the file. Linux as such doesn't interpret the byte sequence in any other way than using '/' as directory delimiter and Nul for ending the string, and neither can occur as part of a multibyte Unicode UTF-8 character (I think).

So what you're saying is that I should for example try:

```

dlopen( (char*) L"SöméçLïbråry.so" )

```

I doubt it will work, but I will try with some chinese characters.

---

### Post by Arndt on 2009-11-12
> **WitchCraft said:**
> So what you're saying is that I should for example try:

```

dlopen( (char*) L"SöméçLïbråry.so" )

```

I doubt it will work, but I will try with some chinese characters.

I suppose the (wchar_t *) string should be converted to UTF-8.

---

### Post by WitchCraft on 2009-11-12
> **Arndt said:**
> I suppose the (wchar_t *) string should be converted to UTF-8.

And the conversion algorithm I found at 
[http://www.codeproject.com/KB/string/UtfConverter.aspx](http://www.codeproject.com/KB/string/UtfConverter.aspx)

I'll try tomorrow.

---

