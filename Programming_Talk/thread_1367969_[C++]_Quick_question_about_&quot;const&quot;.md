---
title: "[C++] Quick question about &quot;const&quot;"
date: 2009-12-30
forum: Programming Talk
---

### Post by kahumba on 2009-12-30
Hi,
Am I assuming correctly the following?
```

int func() {
	static const int y = 15;//initiated only once and can't change
	const int z = 23;//initiated every time and can't change
	return y + z;
}

```

---

### Post by dwhitney67 on 2009-12-30
It seems correct to me.  Someone else may be able to explain it in 500 words or less, but from how you describe it, it is correct.

P.S.  Most people use the word "initialized" versus "initiated".

---

### Post by kahumba on 2009-12-30
Oh thanks!

---

