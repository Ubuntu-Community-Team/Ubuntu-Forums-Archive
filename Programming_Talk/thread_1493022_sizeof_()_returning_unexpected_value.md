---
title: "sizeof () returning unexpected value"
date: 2010-05-25
forum: Programming Talk
---

### Post by tbastian on 2010-05-25
I have a structure which I need to know the size of. I wrote this test program.

```
#include <stdio.h>
#include <stdint.h>

#pragma pack ( 1 )

typedef struct {
	uint16_t header_word;
	uint16_t size;
	uint8_t major_no;
	uint8_t minor_no;
	uint16_t trailer_word;
} header_t;

#pragma pack ()

int main ( int argc, char ** argv )
{
	header_t header;
	printf ( "header_t %d\n", sizeof ( header ));
	return 0;
}
```

sizeof (header) returns 8, not 64! why?

---

### Post by Compyx on 2010-05-25
The sizeof operator yields a size in bytes, not bits. To get the number of bits, you need to multiply the value with CHAR_BIT, which the C standard guarantees to be at least 8.

By the way, to print a size_t (which is what sizeof 'returns') you should use either (C99):
```

printf("%zu\n", sizeof foo);

```
or (C89):
```

printf("%lu\n", (unsigned long)sizeof foo);

```

---

### Post by tbastian on 2010-05-25
> **Compyx said:**
> The sizeof operator yields a size in bytes, not bits.


ahh, right. I knew that!:oops:

---

