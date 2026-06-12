---
title: "Python Data Type Conversions"
date: 2007-10-09
forum: Programming Talk
---

### Post by russell.h on 2007-10-09
I'm trying to read from /dev/random in a python script, but I want the data as a number, not a string. But because python seems to use implicit data types I can't figure out how.

For example:
```
for count in range(10):
	random_gen=open('/dev/random', 'r')
	random_number = random_gen.read(1)
	print random_number
```returns```
;
?
?
+

?
f
?
?
5
```
How can I convert each byte to an integer?

Thanks,

Russell

---

### Post by Wybiral on 2007-10-09
```

print int(random_number)

```

---

### Post by russell.h on 2007-10-09
I tried that, but as far as I can tell that converts a string which contains an integer to an integer, instead of telling me the actual integer value of the byte. If that makes any sense. I guess I'm used to C where a string is just an array of characters anyway.

---

### Post by Wybiral on 2007-10-09
Oh, sorry. Use "ord" instead of "int". I wasn't thinking.

---

### Post by russell.h on 2007-10-09
Brilliant, thanks.

---

