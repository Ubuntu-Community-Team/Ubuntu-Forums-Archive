---
title: "[SOLVED] what does this mean:protected int file_printf(struct magic_set *, const char"
date: 2007-12-31
forum: Programming Talk
---

### Post by fyplinux on 2007-12-31
The code originally from the "file" utility, which is used to determine the file type
```

protected int file_printf(struct magic_set *, const char *, ...);

```

what does these dots(...) in the arguments mean? this is the first time I saw such a notation.

And I found this function is called in more than one ways:
```

file_printf(ms, m->desc, m->value.s);
file_printf(ms, code);

```

---

### Post by public_void on 2007-12-31
It has a variable length argument list and therefore can be called with more arguments than defined. Examples are scanf and printf.

---

### Post by revanthedarth on 2007-12-31
```

void myFunc(const char* fmt, ...)
{
	char text[256];
	va_list ap;
	if(fmt == NULL)
		return;
	va_start(ap, fmt);
	vsprintf(text, fmt, ap);
	va_end(ap);
	printf("%s\n", text);
}

```
Think of that function:
myFunc("%d -> %d -> %d", 1, 3, 5);
prints "1 -> 3 -> 5".

---

### Post by fyplinux on 2008-01-01
thanks

---

