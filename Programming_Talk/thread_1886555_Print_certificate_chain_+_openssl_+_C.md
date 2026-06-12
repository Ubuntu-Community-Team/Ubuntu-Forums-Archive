---
title: "Print certificate chain + openssl + C"
date: 2011-11-25
forum: Programming Talk
---

### Post by ang3lo on 2011-11-25
Hi,

I am doing a program in C that has to connect through SSL to a certain server to validate the server certificate and after that print some information about the all certificate chain.

To do the SSL connection I used the openssl library and I am calling the verify_callback. If I get is right I need to call this function in order to inspect the certificate right?

My callback function is like this:
```
static int verify_callback(int preverify_ok, X509_STORE_CTX *ctx)
 {
    char    buf[256];
    X509   *err_cert;
    int     err, depth;
    SSL    *ssl;

    err_cert = X509_STORE_CTX_get_current_cert(ctx);
    err = X509_STORE_CTX_get_error(ctx);
    depth = X509_STORE_CTX_get_error_depth(ctx);

    ssl = X509_STORE_CTX_get_ex_data(ctx, SSL_get_ex_data_X509_STORE_CTX_idx());
    X509_NAME_oneline(X509_get_subject_name(err_cert), buf, 256);


    if (!preverify_ok) {
        printf("verify error:num=%d:%s:depth=%d:%s\n", err,X509_verify_cert_error_string(err), depth, buf);
    }

    if (!preverify_ok && (err == X509_V_ERR_UNABLE_TO_GET_ISSUER_CERT))
    {
      X509_NAME_oneline(X509_get_issuer_name(ctx->current_cert), buf, 256);
      printf("issuer= %s\n", buf);
    }
      return preverify_ok;
 }
``` 

And I am calling it like this
```
SSL_CTX_set_verify(ctx, SSL_VERIFY_PEER,verify_callback);
```

Know my question is, how can I get the all certificate chain, in order to know how many certificates are in the chain? So I can print information about all certificates in the chain?

Thanks

---

