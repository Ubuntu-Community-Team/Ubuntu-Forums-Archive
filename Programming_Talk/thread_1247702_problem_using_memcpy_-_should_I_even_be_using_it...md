---
title: "problem using memcpy - should I even be using it...?"
date: 2009-08-23
forum: Programming Talk
---

### Post by mcweaver1 on 2009-08-23
I have a structure defined by
```

struct str {
    void  *base;
    size_t len;
};

```

str is passed to a function as an argument.  It contains len bytes of data, which is stored in base.  Within that function I use this ssl function to encrypt the data:
```

EVP_CipherUpdate(&psk_info->ctx, outbuf, &outlen, &str[i].base[offset*1024], inlen)

```

This works by taking a block of inlen bytes from str[i].base starting at the index offset*1024, encrypting it, and then the encrypted data is put into outbuf.

I run this function within a for loop, offset starting at 0 and increasing by 1 each iteration, so that all the data in str[i].base is eventually encrypted, in blocks of 1024 bytes.

In each iteration this line is run:
```

memcpy(&new_buffer[1024*offset],outbuf,outlen);

```

so that each time a block is encrypted and put into outbuf, the contents of outbuf are put into new_buffer at the right place.  Therefore when all the data has been encrypted, new_buffer contains all of the encrypted data in the order it was encrypted.

I then have to copy all of the data in new_buffer into new_str, which is of exactly the same type as str (where the data is stored).  I use memcpy to do this:

```

memcpy(new_str[i].base,new_buffer,templen);

```

where templen is the total number of bytes of encrypted data.  However this keeps seg faulting.  I've been playing around with it for quite a while but can't see a way of achieving what I want to do.

So basically what I want to end up with is all the encrypted data stored in new_str[i].base....

Any help is much appreciated :)

---

### Post by PmDematagoda on 2009-08-23
Could you provide the complete source code?

---

### Post by mcweaver1 on 2009-08-23
```

write(
    void *                              user_arg,
    const structure *                   str)
{
    structuretemp *                     psk_info;
    int                                 inlen, remlen;
    int                                 outlen;
    const structure *                   new_iovec;
    int                                 new_buffer_len = 0;
    unsigned char *                     new_buffer;
    int                                 i, offset = 0, templen = 0;
    unsigned char                       outbuf[1024 + EVP_MAX_BLOCK_LENGTH];

    psk_info = (structuretemp *) user_arg;

    new_iovec = my_calloc(iovec_count, sizeof(structure));

    for(i=0; i<iovec_count; i++)
    {
        new_buffer_len = iovec[i].iov_len * 1024;
        new_buffer = globus_malloc(new_buffer_len);
        remlen = str[i].len;

        EVP_CipherInit_ex(&psk_info->ctx, EVP_rc2_cbc(), NULL, NULL, NULL, 1);
        EVP_CIPHER_CTX_set_key_length(&psk_info->ctx, 10);
        EVP_CipherInit_ex(&psk_info->ctx, NULL, NULL, psk_info->key, psk_info->iv, 1);

        while(remlen > 0)
        {
            inlen = remlen;
            if (inlen > 1024)
                inlen = 1024;
            if(!EVP_CipherUpdate(&psk_info->ctx, outbuf, &outlen, &str[i].base[offset*1024], inlen))
            {
                /* Error */
                EVP_CIPHER_CTX_cleanup(&psk_info->ctx);
                return 0;
            }
            templen += outlen;
            memcpy(&new_buffer[1024*offset],outbuf,outlen);
            offset += 1;
            remlen -= inlen;
        }
        if(!EVP_CipherFinal_ex(&psk_info->ctx, outbuf, &outlen))
        {
            /* Error */
            printf("error encrypting final block\n");
            EVP_CIPHER_CTX_cleanup(&psk_info->ctx);
            return 0;
        }
        memcpy(&new_buffer[1024*offset],outbuf,outlen);
        templen += outlen;
        EVP_CIPHER_CTX_cleanup(&psk_info->ctx);
        //memcpy(new_str[i].base,new_buffer,templen); - [COLOR="Red"]it is this line im having trouble with[/COLOR]
    }

```

---

### Post by PmDematagoda on 2009-08-23
Could you please post the complete source code of the program? There are some variables I have no idea about like iovec_count and a few others.

---

### Post by mcweaver1 on 2009-08-23
I think I found the problem - I defined new_str as being constant so I couldnt change the data within it, but now I have removed the const it seems to be working.

Thanks

---

### Post by MadCow108 on 2009-08-23
thats strange as the const should have given you a compilation warning/error but not a segmentation fault.
do you compile with -Wall?

---

### Post by grayrainbow on 2009-08-23
What's the sugnature of  EVP_CipherUpdate. You make pointer aritmetic with void* which is not the best thing in the world. I could imagin if it's implicitly converted to int what coud happen.

---

