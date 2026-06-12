---
title: "Connect to localhost:80"
date: 2008-07-12
forum: Programming Talk
---

### Post by LCID Fire on 2008-07-12
Hi.
I'm a little stuck (and so is my app) when trying to connect a socket to port 80.
I have a tcp socket on another port and I'd like to redirect it to port 80 (and read the transmitted data without having to use iptables). So I do:

```

struct sockaddr_in output_address;
output_address.sin_family = AF_INET;
output_address.sin_addr.s_addr = INADDR_LOOPBACK;
output_address.sin_port = 80;
 		
connect(tcp_socket, (struct sockaddr*)&output_address, sizeof(struct sockaddr_in))

```

But the app then locks up on the connect. Am I missing anything:confused:

---

