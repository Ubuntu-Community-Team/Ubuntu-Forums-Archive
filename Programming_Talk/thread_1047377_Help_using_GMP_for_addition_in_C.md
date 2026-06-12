---
title: "Help using GMP for addition in C"
date: 2009-01-22
forum: Programming Talk
---

### Post by launchcode on 2009-01-22
Hi,

Can anyone help me use GMP for addition in C?

I'm relatively new to C but have a fair understanding and have written several algorithms. I now need to use GMP, and would be grateful if anyone could show me how to code the following routine:

Declare (initialize) a, b, c as mp floats to 256 bits of precision.

Set a = 1E-20, b = 1E-21.

Calculate c = a + b

printf ("%f", c);


Note, I've already installed GMP successfully and know how to link it into the compilation using gcc.

Thanks!

---

### Post by eye208 on 2009-01-22
```
#include <stdio.h>
#include <gmp.h>

int main() {
	mpf_t a, b, c;
	mpf_set_default_prec(256);
	mpf_init(a);
	mpf_init(b);
	mpf_init(c);
	mpf_set_str(a, "1e-20", 10);
	mpf_set_str(b, "1e-21", 10);
	mpf_add(c, a, b);
	mpf_out_str(NULL, 10, 0, c);
	printf("\n");
	mpf_clear(a);
	mpf_clear(b);
	mpf_clear(c);
	return 0;
}
```

---

### Post by launchcode on 2009-01-22
That's great, many thanks. Much appreciated!

---

