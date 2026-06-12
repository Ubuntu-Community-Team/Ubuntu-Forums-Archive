---
title: "Compiling and using OpenSSL"
date: 2008-11-17
forum: Programming Talk
---

### Post by ZDemon on 2008-11-17
Hi guys, I am trying to compile the OpenSSL libraries by myself. Here are the steps that I take :

```
./config --prefix=/home/zero/test --openssldir=/home/zero/test/openssl no-shared
make
make test
make install
```

It compiles properly and all. However, when I try to link my program with the openssl libraries, I get this error with the linker :

```
Invoking: GCC C Linker
gcc -L/home/zero/test/lib -o"SSLclient"  ./client.o   -lcrypto -ldl -lpthread -lssl
/home/zero/test/lib/libssl.a(t1_lib.o): In function `tls1_process_ticket':
t1_lib.c:(.text+0x64e): undefined reference to `EVP_aes_128_cbc'
/home/zero/test/lib/libssl.a(t1_enc.o): In function `tls1_change_cipher_state':
t1_enc.c:(.text+0x1271): undefined reference to `COMP_CTX_free'
t1_enc.c:(.text+0x128a): undefined reference to `COMP_CTX_new'
t1_enc.c:(.text+0x1348): undefined reference to `COMP_CTX_free'
t1_enc.c:(.text+0x1361): undefined reference to `COMP_CTX_new'
/home/zero/test/lib/libssl.a(ssl_lib.o): In function `ssl_clear_cipher_ctx':
ssl_lib.c:(.text+0xfaa): undefined reference to `COMP_CTX_free'
ssl_lib.c:(.text+0xfc6): undefined reference to `COMP_CTX_free'
```

This is just the begining of a whole lot of undefined references. If I use the OpenSSL libraries provided by Ubuntu, it works fine. So I am thinking this is a issue with the compilation.

I am sure my paths/headers are correct, because it wont give these errors otherwise.

Please help.

---

### Post by ZDemon on 2008-11-18
Hi guys, I have solved the problem.

The solution is simple, for some reason, when linking the library, -lssl must be in front of -lcrypto.

This does not happen with the libraries provided by Ubuntu. I wonder why....

If anyone can shed some light on this, I would greatly appreciate it. But anyway, I solved the main issue. Hope this helps others like me.

---

