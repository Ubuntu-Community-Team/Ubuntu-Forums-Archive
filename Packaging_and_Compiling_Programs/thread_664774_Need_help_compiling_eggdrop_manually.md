---
title: "Need help compiling eggdrop manually"
date: 2008-01-11
forum: Packaging and Compiling Programs
---

### Post by D0T-C0M on 2008-01-11
I need to install eggdrop1.6.13 which is the same as all the other bots that are in the botnet. I've gotten through the ./configure , make config , and when I get to the "make" step it craps out. Below is a paste of what it says,


md5c.c: In function â€˜MD5_Updateâ€™:
md5c.c:208: error: invalid lvalue in assignment
make[2]: *** [md5c.o] Error 1
make[2]: Leaving directory `/home/nascar/eggdrop1.6.13/src/md5'
make[1]: *** [compile_md5] Error 2
make[1]: Leaving directory `/home/nascar/eggdrop1.6.13/src'
make: *** [modegg] Error 2

any ideas?

---

### Post by D0T-C0M on 2008-01-19
anybody have any ideas?

---

### Post by D0T-C0M on 2008-02-09
nobody knows?

---

### Post by dholbach on 2008-02-11
What's in the lines around line 208 in /home/nascar/eggdrop1.6.13/src/md5/md5c.c ? Did you check?

---

### Post by D0T-C0M on 2008-02-13
Hey thanks for your reply. I don't understand source code very much here are the line 187 to 219. Maybe you can see a problem? ( I marked line 208 )

> 
void MD5_Update(MD5_CTX *ctx, void *data, unsigned long size)
{
        MD5_u32plus saved_lo;
        unsigned long used, free;

        saved_lo = ctx->lo;
        if ((ctx->lo = (saved_lo + size) & 0x1fffffff) < saved_lo)
                ctx->hi++;
        ctx->hi += size >> 29;

        used = saved_lo & 0x3f;

        if (used) {
                free = 64 - used;

                if (size < free) {
                        memcpy(&ctx->buffer[used], data, size);
                        return;
                }

                memcpy(&ctx->buffer[used], data, free);
                (unsigned char *)data += free;           <------------line208
                size -= free;
                body(ctx, ctx->buffer, 64);
        }

        if (size >= 64) {    
                data = body(ctx, data, size & ~(unsigned long)0x3f);
                size &= 0x3f;
        }

        memcpy(ctx->buffer, data, size);
}


---

### Post by D0T-C0M on 2008-02-20
can anyone help please?

---

### Post by YourFather on 2008-02-21
Hello D0T-C0M,

I want you to open the file "src/md5/md5c.c" in text
editor and do this:

Change this line:
```

(unsigned char *)data += free; <------------line208

```

To this:
```

data = ((unsigned char *)data) + free;

```

Save and run "make" again.
Should do the trick!

:guitar:

---

### Post by D0T-C0M on 2008-03-01
excellent , just tried it and it worked. Thank you very much

---

