---
title: "Thunderbird with GUFW  problem"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by asigurnjak on 2014-06-12
After setting up my Ubuntu the way i like it i decide to add firewall . Since i was playing with #crunchbang  i followed this  blog 
[http://debianhelp.wordpress.com/2012/10/02/crunchbang-11-waldorf-debian-wheezy-os/](http://debianhelp.wordpress.com/2012/10/02/crunchbang-11-waldorf-debian-wheezy-os/)  .

Now when i enable GUFW Thunderbird can not reach Gmail . All is well when GUFW disabled .
After tweaking it for a while this is where i am now :
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
5353/udp                   DENY IN     Anywhere
5900/tcp                   DENY IN     Anywhere
22                         DENY IN     Anywhere
25/tcp                     DENY IN     Anywhere
135,139,445/tcp            DENY IN     Anywhere
137,138/udp                DENY IN     Anywhere
110                        DENY IN     Anywhere
2049                       DENY IN     Anywhere
143                        ALLOW IN    Anywhere
21/tcp                     DENY IN     Anywhere
465                        ALLOW IN    Anywhere
993                        ALLOW IN    Anywhere
143,993/tcp                ALLOW IN    Anywhere
25                         ALLOW IN    Anywhere
995                        ALLOW IN    Anywhere
465,995/tcp                ALLOW IN    Anywhere
465,995/udp                ALLOW IN    Anywhere
465,993/tcp                ALLOW IN    Anywhere
465,993/udp                ALLOW IN    Anywhere
5353/udp (v6)              DENY IN     Anywhere (v6)
5900/tcp (v6)              DENY IN     Anywhere (v6)
22 (v6)                    DENY IN     Anywhere (v6)
25/tcp (v6)                DENY IN     Anywhere (v6)
135,139,445/tcp (v6)       DENY IN     Anywhere (v6)
137,138/udp (v6)           DENY IN     Anywhere (v6)
110 (v6)                   DENY IN     Anywhere (v6)
2049 (v6)                  DENY IN     Anywhere (v6)
143 (v6)                   ALLOW IN    Anywhere (v6)
21/tcp (v6)                DENY IN     Anywhere (v6)
465 (v6)                   ALLOW IN    Anywhere (v6)
993 (v6)                   ALLOW IN    Anywhere (v6)
143,993/tcp (v6)           ALLOW IN    Anywhere (v6)
25 (v6)                    ALLOW IN    Anywhere (v6)
995 (v6)                   ALLOW IN    Anywhere (v6)
465,995/tcp (v6)           ALLOW IN    Anywhere (v6)
465,995/udp (v6)           ALLOW IN    Anywhere (v6)
465,993/tcp (v6)           ALLOW IN    Anywhere (v6)
465,993/udp (v6)           ALLOW IN    Anywhere (v6)

1:19/tcp                   DENY OUT    Anywhere
1:19/udp                   DENY OUT    Anywhere
22:52/tcp                  DENY OUT    Anywhere
22:52/udp                  DENY OUT    Anywhere
54:79/tcp                  DENY OUT    Anywhere
54:79/udp                  DENY OUT    Anywhere
81:122/tcp                 DENY OUT    Anywhere
81:122/udp                 DENY OUT    Anywhere
124:442/tcp                DENY OUT    Anywhere
124:442/udp                DENY OUT    Anywhere
444:65535/tcp              DENY OUT    Anywhere
444:65535/udp              DENY OUT    Anywhere
1:19/tcp (v6)              DENY OUT    Anywhere (v6)
1:19/udp (v6)              DENY OUT    Anywhere (v6)
22:52/tcp (v6)             DENY OUT    Anywhere (v6)
22:52/udp (v6)             DENY OUT    Anywhere (v6)
54:79/tcp (v6)             DENY OUT    Anywhere (v6)
54:79/udp (v6)             DENY OUT    Anywhere (v6)
81:122/tcp (v6)            DENY OUT    Anywhere (v6)
81:122/udp (v6)            DENY OUT    Anywhere (v6)
124:442/tcp (v6)           DENY OUT    Anywhere (v6)
124:442/udp (v6)           DENY OUT    Anywhere (v6)
444:65535/tcp (v6)         DENY OUT    Anywhere (v6)
444:65535/udp (v6)         DENY OUT    Anywhere (v6)


and Thunderbird is still not getting to Gmail .
What am i doing wrong ?
All help is appreciated .

---

