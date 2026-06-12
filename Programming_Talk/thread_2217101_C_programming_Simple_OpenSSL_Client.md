---
title: "C programming Simple OpenSSL Client"
date: 2014-04-15
forum: Programming Talk
---

### Post by fugu2 on 2014-04-15
Okay I've been playing around with openssl a little bit, and I wanted to learn how to make a simple https webpage fetching program, which I did here:
```

//gcc -o test test.c -lssl -lcrypto
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <unistd.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <unistd.h>
#include <signal.h>
#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <errno.h>
#include <sys/time.h>
#include <stdlib.h>
#include <memory.h>
#include <ifaddrs.h>
#include <net/if.h>
#include <stdarg.h>

#include <openssl/crypto.h>
#include <openssl/x509.h>
#include <openssl/pem.h>
#include <openssl/ssl.h>
#include <openssl/err.h>

int main(int argc, char *argv[]){
	int sd;
	struct hostent *host;
	struct sockaddr_in addr;
	BIO *outbio = NULL;
	SSL_METHOD *method;
	SSL_CTX *ctx;
	SSL *ssl;
	char *req;
	int req_len;
	char hostname[] = "www.google.com";
	char certs[] = "/etc/ssl/certs/ca-certificates.crt";
	int port = 443;
	int bytes;
	char buf[128];

	OpenSSL_add_all_algorithms();
	ERR_load_BIO_strings();
	ERR_load_crypto_strings();
	SSL_load_error_strings();

	outbio	= BIO_new(BIO_s_file());
	outbio	= BIO_new_fp(stdout, BIO_NOCLOSE);

	if(SSL_library_init() < 0){
		BIO_printf(outbio, "Could not initialize the OpenSSL library !\n");
	}

	method = SSLv23_client_method();
	ctx = SSL_CTX_new(method);
	SSL_CTX_set_options(ctx, SSL_OP_NO_SSLv2);

	host = gethostbyname(hostname);
	sd = socket(AF_INET, SOCK_STREAM, 0);
	memset(&addr, 0, sizeof(addr));
	addr.sin_family = AF_INET;
	addr.sin_port = htons(port);
	addr.sin_addr.s_addr = *(long*)(host->h_addr);

	if ( connect(sd, (struct sockaddr*)&addr, sizeof(addr)) == -1 ) {
		BIO_printf(outbio, "%s: Cannot connect to host %s [%s] on port %d.\n", argv[0], hostname, inet_ntoa(addr.sin_addr), port);
	}

	ssl = SSL_new(ctx); 
	SSL_set_fd(ssl, sd);
	SSL_connect(ssl);

	req = "GET / HTTP/1.1\r\nHost: www.google.com\r\n\r\n";	
	req_len = strlen(req);
	SSL_write(ssl, req, req_len);

	memset(buf, '\0', sizeof(buf));
	bytes = SSL_read(ssl, buf, sizeof(buf));
	while(bytes > 0){
		write(STDOUT_FILENO, buf, bytes);
		memset(buf, '\0', sizeof(buf));
		bytes = SSL_read(ssl, buf, sizeof(buf));
	}
	SSL_free(ssl);
	close(sd);
	SSL_CTX_free(ctx);
}

```

but i know I'm lacking something because no where do I specify the 'certs' variable with openssl. It kinda already knows which is not a problem in this example, but if I had a different cert file that I wanted to specify, then how could I change this to do that?

Thanks

---

### Post by tux3do on 2014-04-16
I modified your code to this:

```

//gcc -o test test.c -lssl -lcrypto
//http://talkera.org.cp-in-1.webhostbox.net/ascii/ascii.php
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <unistd.h>
#include <arpa/inet.h>
#include <netdb.h>
#include <unistd.h>
#include <signal.h>
#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <errno.h>
#include <sys/time.h>
#include <stdlib.h>
#include <memory.h>
#include <ifaddrs.h>
#include <net/if.h>
#include <stdarg.h>

#include <openssl/crypto.h>
#include <openssl/x509.h>
#include <openssl/pem.h>
#include <openssl/ssl.h>
#include <openssl/err.h>

int main(int argc, char *argv[]){
    int sd;
    struct hostent *host;
    struct sockaddr_in addr;
    BIO *outbio = NULL;
    SSL_METHOD *method;
    SSL_CTX *ctx;
    SSL *ssl;
    char *req;
    int req_len;
    char hostname[] = "www.google.com";
    char certs[] = "/etc/ssl/certs/ca-certificates.crt";
    int port = 443;
    int bytes;
    char buf[128];

    // added this to test
       char           dest_url[] = "https://www.google.com";
       BIO              *certbio = NULL;
       X509                *cert = NULL;
       X509_NAME       *certname = NULL;
    BIO *outbio2 = NULL;



    OpenSSL_add_all_algorithms();
    ERR_load_BIO_strings();
    ERR_load_crypto_strings();
    SSL_load_error_strings();

    outbio    = BIO_new(BIO_s_file());
    outbio    = BIO_new_fp(stdout, BIO_NOCLOSE);
      
    if(SSL_library_init() < 0){
        BIO_printf(outbio, "Could not initialize the OpenSSL library !\n");
    }

    method = SSLv23_client_method();
    ctx = SSL_CTX_new(method);
    SSL_CTX_set_options(ctx, SSL_OP_NO_SSLv2);

    host = gethostbyname(hostname);
    sd = socket(AF_INET, SOCK_STREAM, 0);
    memset(&addr, 0, sizeof(addr));
    addr.sin_family = AF_INET;
    addr.sin_port = htons(port);
    addr.sin_addr.s_addr = *(long*)(host->h_addr);

    if ( connect(sd, (struct sockaddr*)&addr, sizeof(addr)) == -1 ) {
        BIO_printf(outbio, "%s: Cannot connect to host %s [%s] on port %d.\n", argv[0], hostname, inet_ntoa(addr.sin_addr), port);
    }

    ssl = SSL_new(ctx); 
    SSL_set_fd(ssl, sd);
    

    SSL_connect(ssl);

    // try something here
       /* Get the remote certificate into the X509 structure */
       printf("SSL_get_peer_certificate(ssl) \n");
       cert = SSL_get_peer_certificate(ssl);
       if (cert == NULL)
         printf("Error: Could not get a certificate from: %s.\n", dest_url);
       else
         printf("Retrieved the server's certificate from: %s.\n", dest_url);

       printf("\n");
    
       /* extract various certificate information */
       certname = X509_NAME_new();
       certname = X509_get_subject_name(cert);

      /*  display the cert subject here */
      BIO_printf(outbio, "Displaying the certificate subject data:\n");
      X509_NAME_print_ex(outbio, certname, 0, 0);
      BIO_printf(outbio, "\n\n");


    req = "GET / HTTP/1.1\r\nHost: www.google.com\r\n\r\n";    
    req_len = strlen(req);
    SSL_write(ssl, req, req_len);

    memset(buf, '\0', sizeof(buf));
    bytes = SSL_read(ssl, buf, sizeof(buf));
    while(bytes > 0){
        write(STDOUT_FILENO, buf, bytes);
        memset(buf, '\0', sizeof(buf));
        bytes = SSL_read(ssl, buf, sizeof(buf));
    }
    SSL_free(ssl);
    close(sd);
    SSL_CTX_free(ctx);
}

```

It grabs the certificate from google. If you want to use one on your box, I think you could use your own host in dest_url.
Right now it outputs:
```

Displaying the certificate subject data:
C=US, ST=California, L=Mountain View, O=Google Inc, CN=www.google.com

```

Hope this answers your question :popcorn:

---

### Post by fugu2 on 2014-04-22
First of all thank you for your help with this. I'm really trying to learn the openssl library a little better, and I've had a hard time finding information and examples for using it, and your example it very helpful.

 I want to also learn how I can verify a server's certs to tell if it is 'good' or 'bad', from a certs list that a web browser might use. Any ideas on how that might be done?

---

