---
title: "[GNUTLS] can't handshake with client"
date: 2011-01-18
forum: Programming Talk
---

### Post by soltanis on 2011-01-18
Background: I'm trying to add SSL functionality to an inetd daemon. These daemons are started by inetd, which in turn starts tcpd, which starts this program. The stdin, stdout, and stderr are all redirected to the socket on which the client program connects.

Relevant code:

```

int init_ssl(int fd)
{
        int error, c;

        gnutls_global_init();
        gnutls_certificate_allocate_credentials(&credentials);
        if (TRUSTFILE) gnutls_certificate_set_x509_trust_file(credentials, TRUSTFILE, GNUTLS_X509_FMT_PEM);
        if (CRLFILE) gnutls_certificate_set_x509_crl_file(credentials, CRLFILE, GNUTLS_X509_FMT_PEM);
        gnutls_certificate_set_x509_key_file(credentials, CERTFILE, KEYFILE, GNUTLS_X509_FMT_PEM);

        generate_dh_params(&dh_params, 1024);
        //generate_rsa_params(&rsa_params, 512);

        /* set key negotiation parameters */
        gnutls_certificate_set_dh_params(credentials, dh_params);

        session = init_tls_session(credentials);
        /* set transport pointer for this session */
        gnutls_transport_set_ptr(session, (gnutls_transport_ptr_t) &fd);

        return gnutls_handshake(session); // <- fails here
}

```

The set up seems to work out, but on trying gnutls_handshake I get a return code of -9, "A TLS packet with unexpected length was received."

I thought initially the problem was being caused by the fact that this program tries to set non-blocking on stdin, so I moved the TLS initialization to come before non-blocking is set. This didn't help, though, as I still get the same error. This error also seems to be completely independent of the input I give the program, and from what I see in the debugger happens basically immediately.

For completeness, this is what happens when I try to connect with gnutls-cli-debug:

```

Resolving '127.0.0.1'...
Connecting to '127.0.0.1:5223'...
Checking for TLS 1.1 support... no
Checking fallback from TLS 1.1 to... failed
Checking for TLS 1.0 support... no
Checking for SSL 3.0 support... no

Server does not support any of SSL 3.0, TLS 1.0 and TLS 1.1

```

Any ideas on why this occurs? The example code works well with sockets, but I have no idea on whether perhaps using the standard input is why the library decides to do this.

---

### Post by soltanis on 2011-01-18
Bumping back to the top of the list. The next thing I'm going to try is removing the non-blocking behavior of the daemon (which is bad form anyway) and using select instead. If anyone has any help, please reply.

---

### Post by soltanis on 2011-01-19
I still haven't figured out what's wrong with my code, but evidently wrapping an inetd daemon into an SSL tunnel is possible using [stunnel]("http://stunnel.mirt.net/").

---

