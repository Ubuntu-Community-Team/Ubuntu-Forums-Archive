---
title: "[SOLVED] Problems using LZO compression library"
date: 2008-09-11
forum: Programming Talk
---

### Post by British0zzy on 2008-09-11
I've added these two functions for compressing a dynamic array, and I've modeled them from examples given from the LZO library.
When run I get results like these...
Uncompressed:1048576
Compressed:14001593389084
Incompressible.
Uncompressed:2097152
Compressed:14001593393196
Incompressible.
Uncompressed:3145728
Compressed:14001593397311
Incompressible.
Uncompressed:4194304
Compressed:14001593401428
Incompressible.
Uncompressed:5242880
Compressed:14001593405553
Incompressible.
Uncompressed:6291456
Compressed:14001593409693
Incompressible.
Uncompressed:7340032
Compressed:14001593413868
Incompressible.
Uncompressed:8388608
Compressed:14001593418124
Incompressible.

Can you find any reason this code shouldn't work??
If you need any more information just ask.

```
typedef struct {
    int* data;
    unsigned int size;
} DynArray;

#include "minilzo.h"

int compress(DynArray* da, lzo_uintp len)
{
    if (da->data == NULL)
        return -1;

    lzo_bytep in;
    void* out;
    lzo_voidp wrkmem;
    lzo_uint in_len;

    if (lzo_init() != LZO_E_OK)
        return -1;

    in_len = da->size;
    in = (lzo_bytep) da->data;
    out = malloc(in_len + in_len/64 + 64 + 3);
    wrkmem = malloc(LZO1X_1_MEM_COMPRESS);
    if (out == NULL || wrkmem == NULL)
        return -1;

    if (lzo1x_1_compress(in, in_len, (lzo_bytep) out, (lzo_uintp) len, wrkmem) != LZO_E_OK) {
        free(wrkmem);
        free(out);
        return -1;
    }

    free(wrkmem);

    printf("Uncompressed:%lu\nCompressed:%llu\n", in_len,(unsigned long long) *len);

    if ((lzo_uint)*len >= in_len) {
        free(out);
        printf("Incompressible.");
        return 0;
    }

    free(da->data);
    da->data = (int*) out;
    return 0;
}

int decompress(DynArray* da, lzo_uint in_len)
{
    if (da->data == NULL)
        return -1;
    lzo_bytep in;
    void* out;
    lzo_uint out_len;
    lzo_uint expect_len = da->size;

    if (lzo_init() != LZO_E_OK)
        return -1;

    in = (lzo_bytep) da->data;
    out = malloc(expect_len);
    if (out == NULL)
        return -1;

    if (lzo1x_decompress(in, in_len, (lzo_bytep) out, &out_len, NULL) != LZO_E_OK) {
        free(out);
        return -1;
    }

    if (out_len != expect_len) {
        free(out);
        return -1;
    }
    free(da->data);
    da->data = (int*) out;
    return 0;
}
```

---

### Post by British0zzy on 2008-09-11
For some reason len must be set to zero before sending it to the compressor.

---

