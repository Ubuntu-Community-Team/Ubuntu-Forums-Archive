---
title: "uuid_generate bug?"
date: 2010-11-16
forum: Packaging and Compiling Programs
---

### Post by Mers2009 on 2010-11-16
Hi there,

I'm tring to running the following code:

```

int main(int argc, char** argv) {

uuid_t uuid_id;
char *name_file;
uuid_generate(uuid_id);
uuid_unparse(uuid_id, name_file);

}

```When executes the function uuid_unparse I get a buffer overflow:

```
*** buffer overflow detected ***: ./main terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0xb778f390]
/lib/tls/i686/cmov/libc.so.6(+0xe12ca)[0xb778e2ca]
/lib/tls/i686/cmov/libc.so.6(+0xe0a08)[0xb778da08]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0xb7716afe]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0xe24)[0xb76eaa34]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0xb778dabd]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb778d9fd]
/lib/libuuid.so.1(+0x264c)[0xb780a64c]
./main[0x804923f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb76c3bd6]
./main[0x8048a41]

```I'm runing Ubuntu 10.04. All packages where installed from Ubuntu repositories, including the uuid-dev package.

---

### Post by SevenMachines on 2010-11-17
You need to allocate an array of sufficient size to hold the unparsed uuid. for example,
> char name_file[128];
would work, but i'm imagining there will be something in libuuid that defines the maximum size somewhere that you should use

---

### Post by Mers2009 on 2010-11-17
> **SevenMachines said:**
> You need to allocate an array of sufficient size to hold the unparsed uuid. for example,

would work, but i'm imagining there will be something in libuuid that defines the maximum size somewhere that you should use

Oh, my mind...

Thanks Seven!

---

