---
title: "Forcing AESGCM negotiation in openssl based (C++) program."
date: 2014-10-27
forum: Programming Talk
---

### Post by pibara on 2014-10-27
[COLOR=#404040][FONT=Roboto]Really could use some help with forcing AESGCM with OpenSSL.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]Trying to upgrade a little server program into only using GCM based cipher suites. I'm rather confused about openssl (1.0.1.f) on my Ubuntu  (14.04) system right now.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]When I run:  openssl ciphers 'AESGCM'[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]I get a very nice list from openssl : ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-DSS-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384:ADH-AES256-GCM-SHA384:ECDH-RSA-AES256-GCM-SHA384:ECDH-ECDSA-AES256-GCM-SHA384:AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:DHE-RSA-AES128-GCM-SHA256:ADH-AES128-GCM-SHA256:ECDH-RSA-AES128-GCM-SHA256:ECDH-ECDSA-AES128-GCM-SHA256:AES128-GCM-SHA256[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]But now when in my C++ server application I do:[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]SSL_CTX_set_cipher_list(context_.native_handle(),"AESGCM")[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]The server ends up only negotiating a real short list of only two:[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]AES256-GCM-SHA384:AES128-GCM-SHA256[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]Both the openssl tool and my server use the same version of the openssl library, so I'm rather confused. Anyone have a clue how the openssl tool seems to support many more 'AESGCM' cipher suites than my litle server program.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]At this moment my little server only seems to work with Chrome (IE and FF won't work with just these two listed), and I really would like to get things working in such a way that I can support all major browsers AND can force AESGCM cipher negotiation for these browsers.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]Anyone have any clue as to what I'm missing here? Clearly the openssl library on my system supports many AESGCM ciphers (given that the openssl tool lists them, and given that I can use the openssl tool to connect to other servers using some of these ciphers, yet asking the library for AESGCM from my server code does not include most of the ciphers.[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]I'm probably doing something really stupid here, but I'm truly at a loss to what it might be.&#65279;[/FONT][/COLOR]

---

