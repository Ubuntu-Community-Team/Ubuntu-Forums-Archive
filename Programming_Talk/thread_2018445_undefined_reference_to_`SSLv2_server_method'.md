---
title: "undefined reference to `SSLv2_server_method'"
date: 2012-07-06
forum: Programming Talk
---

### Post by sacridex on 2012-07-06
Hello,

my problem is in the topic, i get the error* undefined reference to `SSLv2_server_method'*.
I have installed libssl-dev, so the other functions are defined. Only this particular function throws an error to me.

Here is my code:
```
#include <errno.h>
#include <unistd.h>
#include <malloc.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <arpa/inet.h>
#include <resolv.h>
#include <openssl/ssl.h>
#include <openssl/err.h>

SSL_CTX * InitServerCTX (void)
{
    SSL_METHOD *method;
    SSL_CTX *ctx;
    
    OpenSSL_add_all_algorithms ();
    SSL_load_error_strings ();
    method = SSLv2_server_method ();
    ctx = SSL_CTX_new (method);
    if (ctx == NULL)
    {
        ERR_print_errors_fp (stderr);
        abort ();
    }
    return ctx;
}

int main (int argc, char **argv)
{
    SSL_CTX *ctx;
    int server;
    char *portnum = "1337";
    
    SSL_library_init ();
    
    ctx = InitServerCTX ();
    
    return 0;
}
```How i compile: *gcc server.c -o server -lssl -lcrypto*

Ideas anyone?
thx

---

### Post by MadCow108 on 2012-07-06
I think the long deprecated sslv2 is completely disabled in newer distributions, use sslv3

---

