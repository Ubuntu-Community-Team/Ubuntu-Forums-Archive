---
title: "How do I concatenate a defines and a string in the C Programming Language"
date: 2009-08-23
forum: Programming Talk
---

### Post by sefs on 2009-08-23
```

#define CONFIG_PATH "/etc/openvpn/conf"

glob_t gl;

glob("/etc/openvpn/conf/*.conf"), 0, NULL, &gl);

```

Consider the above.  I want to utilize the CONFIG_PATH defines in the glob statement.
How can I do this economically and without reducing performance?

Thanks.

---

### Post by skirkpatrick on 2009-08-23
```
glob(CONFIG_PATH, 0, NULL, &gl);
```

The C preprocessor will replace all instances of CONFIG_PATH with it's definition during compilation.  As far as the compiler is concerned, there is no difference.

---

### Post by sefs on 2009-08-23
you've lopped off the "/*.conf" part. 

How do I get that part in the concatenation.

Thanks.

---

### Post by Habbit on 2009-08-23
In C, a sequence of string literals separated only by whitespace is resolved into a single string literal. For example, "A" "B" resolves to "AB". Thus, you just need to write [FONT="monospace"]CONFIG_PATH "/*.conf"[/FONT].

---

### Post by stroyan on 2009-08-23
You can just put two string constants next to eachother to concatenate them.

```
#define CONFIG_PATH "/etc/openvpn/conf"

glob_t gl;

/* These three lines are equivalent. */
glob("/etc/openvpn/conf/*.conf"), 0, NULL, &gl);
glob("/etc/openvpn/conf" "/*.conf"), 0, NULL, &gl);
glob(CONFIG_PATH "/*.conf"), 0, NULL, &gl);

```

---

### Post by lensman3 on 2009-08-23
Look at the -E option for gcc.  The -E option will only invoke the pre-processor so you can then look at the output of #define catenation. 

This also shows all the includes and how they are modified and added.  Your code will be at the very end.

---

### Post by sefs on 2009-08-23
good show all.  Thanks for that!

---

