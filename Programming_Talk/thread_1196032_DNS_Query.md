---
title: "DNS Query"
date: 2009-06-24
forum: Programming Talk
---

### Post by Rij on 2009-06-24
Hi,

I am trying to write a program that will do automatic DNS query. I use two approaches. When I ask the system to build the query for me using "res_query", it works fine. But when I try to build the query by making the library call "res_mkquery", it doesn't. Specifically, the program hangs waiting for a response from the DNS server. Any help will be greatly appreciated. Here is the code.
```

int main() {
        struct sockaddr_in to_addr;
        char udp_query[200], udp_response[200], domain_name[] = "www.google.com";
        int s_sock, tx_id, s_tx_id, flags, byte_count;
        ushort s_flag = 0x0100, r_flag = 0x8180;
        socklen_t sin_len;

        to_addr.sin_family      = AF_INET;
        to_addr.sin_port        = 53;
        if (inet_aton("10.10.10.10", &(to_addr.sin_addr)) <=0) {
                printf("Invalid address.\n");
                return 0;
        }

        s_sock = socket(AF_INET, SOCK_DGRAM, 0);
        if (s_sock < 0) {
                printf("udp socket: %s", strerror(errno));
                return 0;
        }

        byte_count = res_mkquery(QUERY, domain_name, C_IN, T_ANY, NULL, 0,
                                         NULL, udp_query, 190);
        if (byte_count == -1) {
                printf("Couldn't make DNS query: %s", strerror(errno));
        }
        printf("Query size = %d\n", byte_count);

        s_tx_id = get_uint16(udp_query);
        flags = get_uint16(udp_query+2);

        if (flags != s_flag) {
                printf("Malformed DNS query\n");
                return 0;
        }

        printf("Sending ...\n");

        byte_count = sendto(s_sock, udp_query, byte_count, MSG_DONTWAIT,
                                    (struct sockaddr *)&to_addr, sizeof(to_addr));

        if (byte_count < strlen(udp_query)) {
                printf("UDP packet send error: %s", strerror(errno));
                return 0;
        }

        printf("Bytes sent = %d, destination = %s\n", byte_count, inet_ntoa(to_addr.sin_addr.s_addr));

        printf("Waiting ...\n");

        byte_count = recvfrom(s_sock, udp_response, 190, 0,
                                                        (struct sockaddr *)&to_addr, &sin_len);
        if (byte_count <= 0) {
                printf("udp recvfrom on socket = %d: %s", s_sock, strerror(errno));
                return 0;
        }

        /*if (res_query(domain_name, C_IN, T_ANY, udp_response, sizeof(udp_response)) < 0) {
                printf("Error: %s\n", strerror(errno));
                return 0;
        }*/

        printf("Will check ...\n");

        s_tx_id = tx_id = get_uint16(udp_response);
        flags = get_uint16(udp_response+2);

        if ((tx_id == s_tx_id) && (flags == r_flag)) {
                printf("Matched.\n");
        }
}


```

---

### Post by stroyan on 2009-06-24
strace of the system calls shows that the port is wrong.

Change
to_addr.sin_port        = 53;
to
to_addr.sin_port        = htons(53);

---

### Post by Rij on 2009-06-24
Ah! Thanks!

---

### Post by kuttya on 2011-01-23
If you need DNS query means try this site [http://www.whoisxy.com/](http://www.whoisxy.com/) and also get the ip to domain,domain to ip,ping test,etc......

---

### Post by Phoenixie on 2011-01-23
> **kuttya said:**
> If you need DNS query means try this site [http://www.whoisxy.com/](http://www.whoisxy.com/) and also get the ip to domain,domain to ip,ping test,etc......

Nice, bumping one year old thread to promote your crappy website.

---

### Post by Ravenshade on 2011-01-23
...guess this also counts as a bump. 

He probably did the same thing as me and searched for it but didn't notice the last time the topic had been replied to. Now....MOD! Shouldn't this thread be locked?

---

