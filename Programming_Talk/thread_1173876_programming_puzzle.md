---
title: "programming puzzle"
date: 2009-05-30
forum: Programming Talk
---

### Post by MadCow108 on 2009-05-30
hi, a little puzzle for you, I hope not all know it already:

```
int i, n = 20; 
for (i=0; i<n; i--) 
{ 
	cout << "x" << endl; 
}

```

find three different solutions to get this code to print out 20 times x by only replacing a **single** character with another **single** character.
No adding of characters.

Usually people find two possibilities quite quickly but the third can be tricky :)

---

### Post by Victor Liu on 2009-05-31
```
int i, n = 20; 
for (i=0; i<n; n--) 
{ 
	cout << "x" << endl; 
}
```

```

int i, n = 20; 
for (i=0; i+n; i--) 
{ 
	cout << "x" << endl; 
}
```

```

int i, n = 20; 
for (i=0;-i<n; i--) 
{ 
	cout << "x" << endl; 
}
```

---

### Post by NielsBhor on 2009-05-31
Victor got it. Very good programmer. I didn't know about Slerp until now.

---

