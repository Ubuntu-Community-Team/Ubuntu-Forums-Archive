---
title: "SSL_connect() takes eternally"
date: 2012-07-10
forum: Programming Talk
---

### Post by sacridex on 2012-07-10
Hello,

I'm trying to get a Server/Client application with SSL running.
But the client just won't connect to the server... :(
SSL_connect is the problem. It just takes forever and does not return a value.
The official OpenSSL documentation is very... lets call it... thin...

Anyone knows help?
Thx

client.c
```
#include <stdio.h>
#include <errno.h>
#include <unistd.h>
#include <malloc.h>
#include <string.h>
#include <sys/socket.h>
#include <resolv.h>
#include <netdb.h>
#include <openssl/ssl.h>
#include <openssl/err.h>

#define FAIL -1

int OpenConnection (const char *hostname, int port)
{
    int sd;
    struct hostent *host;
    struct sockaddr_in addr;
    
    if ((host = gethostbyname (hostname))  == NULL)
    {
        perror (hostname);
        abort ();
    }
    
    sd = socket (PF_INET, SOCK_STREAM, 0);
    bzero (&addr, sizeof (addr));
    addr.sin_family = AF_INET;
    addr.sin_port = htons (port);
    addr.sin_addr.s_addr = *(long *) (host->h_addr);
    
    if (connect (sd, (struct sockaddr *) &addr, sizeof (addr)) != 0)
    {
        close (sd);
        perror (hostname);
        abort ();
    }
    return sd;
}

SSL_CTX * InitCTX ()
{
    SSL_METHOD *method;
    SSL_CTX *ctx;

    OpenSSL_add_all_algorithms ();
    SSL_load_error_strings ();
    method = SSLv3_client_method ();
    ctx = SSL_CTX_new (method);

    if (ctx == NULL)
    {
        ERR_print_errors_fp (stderr);
        abort ();
    }
    return ctx;
}

void ShowCerts (SSL *ssl)
{
    X509 *cert;
    char *line;
    
    cert = SSL_get_peer_certificate (ssl);
    if (cert != NULL)
    {
        printf ("Server Certificates:\n");
        line = X509_NAME_oneline (X509_get_subject_name (cert), 0, 0);
        printf ("Subject %s\n", line);
        free (line);
        line = X509_NAME_oneline (X509_get_issuer_name (cert), 0, 0);
        printf ("Issuer %s\n", line);
        free (line);
        X509_free (cert);
    }
    else
        printf ("No certificates\n");
}

int main (int argc, char **argv)
{
    SSL_CTX *ctx;
    int server;
    SSL *ssl;
    char buf[1024];
    int bytes;
    char *hostname = "localhost", *portnum = "1337";

    SSL_library_init ();
    
    ctx = InitCTX ();
    server = OpenConnection (hostname, atoi (portnum));
    ssl = SSL_new (ctx);
    SSL_set_fd (ssl, server);
    printf ("This output is shown\n");
    if (SSL_connect (ssl) == FAIL)
    {
        printf ("SSL_connect() failed but its not shown anyways\n");
        ERR_print_errors_fp (stderr);
    }
    else
    {
        printf ("SSL_connect() succeeded but its not shown anyways\n");
        char *msg = "Hello!";
        
        printf ("Connected with %s encryption\n", SSL_get_cipher (ssl));
        ShowCerts (ssl);
        SSL_write (ssl, msg, strlen (msg));
        bytes = SSL_read (ssl, buf, sizeof (buf));
        buf[bytes] = 0;
        printf ("Received: \"%s\"\n", buf);
        SSL_free (ssl);
    }
    close (server);
    SSL_CTX_free (ctx);
    return 0;
}
```server.c
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

#define FAIL -1

int OpenListener (int port)
{
    int sd;
    struct sockaddr_in addr;
    
    sd = socket (PF_INET, SOCK_STREAM, 0);
    bzero (&addr, sizeof (addr));
    addr.sin_family = AF_INET;
    addr.sin_port = htons (port);
    addr.sin_addr.s_addr = INADDR_ANY;
    
    if (bind (sd, (struct sockaddr*) &addr, sizeof (addr)) != 0)
    {
        perror ("cannot bind port");
        abort ();
    }
    
    if (listen (sd, 10) != 0)
    {
        perror ("cannot configure listening port");
        abort ();
    }
}

SSL_CTX * InitServerCTX (void)
{
    SSL_METHOD *method;
    SSL_CTX *ctx;
    
    OpenSSL_add_all_algorithms ();
    SSL_load_error_strings ();
    method = SSLv3_server_method ();
    ctx = SSL_CTX_new (method);
    if (ctx == NULL)
    {
        ERR_print_errors_fp (stderr);
        abort ();
    }
    return ctx;
}

void loadCertificates (SSL_CTX *ctx, char *CertFile, char *KeyFile)
{
    if (SSL_CTX_use_certificate_file (ctx, CertFile, SSL_FILETYPE_PEM) <= 0)
    {
        ERR_print_errors_fp (stderr);
        abort ();
    }
    
    if (SSL_CTX_use_PrivateKey_file (ctx, KeyFile, SSL_FILETYPE_PEM) <= 0)
    {
        ERR_print_errors_fp (stderr);
        abort ();
    }
    
    if (!SSL_CTX_check_private_key (ctx))
    {
        fprintf (stderr, "Private key does not match the public certificate\n");
        abort ();
    }
}

void ShowCerts (SSL *ssl)
{
    X509 *cert;
    char *line;
    
    cert = SSL_get_peer_certificate (ssl);
    if (cert != NULL)
    {
        printf ("Server certificates:\n");
        line = X509_NAME_oneline (X509_get_subject_name (cert), 0, 0);
        printf ("Subject: %s\n", line);
        free (line);
        line = X509_NAME_oneline (X509_get_issuer_name (cert), 0, 0);
        printf ("Issuer: %s\n", line);
        free (line);
        X509_free (cert);
    }
    else
        printf ("no certificates\n");
}

void Servlet (SSL *ssl)
{
    char buf[1024];
    char reply[1024];
    int sd, bytes;
    const char *HTMLecho = "<html><body><pre>%s</pre></body></html>\n\n";
    
    if (SSL_accept (ssl) == FAIL)
        ERR_print_errors_fp (stderr);
    else
    {
        ShowCerts (ssl);
        bytes = SSL_read (ssl, buf, sizeof (buf));
        if (bytes > 0)
        {
            buf[bytes] = 0;
            printf ("ClientMSG: \"%s\"\n", buf);
            sprintf (reply, HTMLecho, buf);
            SSL_write (ssl, reply, strlen (reply));
        }
        else
            ERR_print_errors_fp (stderr);
    }
    sd = SSL_get_fd (ssl);
    SSL_free (ssl);
    close (sd);
}

int main (int argc, char **argv)
{
    SSL_CTX *ctx;
    int server;
    char *portnum = "1337";
    
    SSL_library_init ();
    ctx = InitServerCTX ();
    loadCertificates (ctx, "mycert.pem", "mycert.pem");
    server = OpenListener (atoi (portnum));
    
    while (1)
    {
        struct sockaddr_in addr;
        socklen_t len = sizeof (addr);
        SSL *ssl;
        
        int client = accept (server, (struct sockaddr*) &addr, &len);
        if (client > 0)
            printf ("Connection: %d:%d\n", inet_ntoa (addr.sin_addr), ntohs (addr.sin_port));
        
        ssl = SSL_new (ctx);
        SSL_set_fd (ssl, client);
        Servlet (ssl);
    }
    
    close (server);
    SSL_CTX_free (ctx);
    
    return 0;
}
```

---

### Post by sacridex on 2012-07-11
Embarrassing, I forgot to return the socket descriptor in OpenConnection/sever.c. :(

---

