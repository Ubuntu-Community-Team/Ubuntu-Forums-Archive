---
title: "pcaps rules"
date: 2018-09-23
forum: Programming Talk
---

### Post by luca31 on 2018-09-23
Following the article about posix capabilities: [http://friedhoff.org/posixfilecaps.html](http://friedhoff.org/posixfilecaps.html)
the rules to calculate the pcaps state of a called process are:
> 
POSIX Capabilities - Capability Rules
The POSIX Capability State is calculated upon an exec(). A forc() or clone() doesn't change the PCaps State.
As defined in 1003.1e p. 17
Definition:

p{I,P,E}' = post-exec() POSIX Capability Sets aka the PCaps State of the new process
X = was not specified by 1003.1e and has subsequently become cap_bset - /proc/sys/kernel/cap-bound for Linux
fP = File Permitted Set of the called executable, also Minimal Forced Set called
fE = File Effective Set of the called executable
fI = File Inheritance Set of the called executables
pP = Process Permitted Set (here of the calling process)
pE = Process Effective Set (here of the calling process)
pI = Process Inheritable Set (here of the calling process)
& --> Intersection
| --> Union

Rules:

1) pI' = pI
2) pP' = (X & fP) | (pI & fI)
3) pE' = fE & pP'


but the rules seems not to be applied to the ping utility:

$ getpcaps $$
Capabilities for `1265': = 
$ getcap /bin/ping
/bin/ping = cap_net_admin,cap_net_raw+p

pI and fI are empty, the ping process won't exploit the inheritability
I  thought that the ping binary should have the posix capabilities   cap_net_admin,cap_net_raw flagged effective in addition to permitted,  that is fE should be cap_net_admin,cap_net_raw+pe.
Especially  I expected the capabilities to grant the access on socket should be in  the effective set pE' of the new ping process , not only in the  permitted set pP', in order to grant the privilege but obviously I  misunderstood:

$ /bin/ping [www.google.it]("https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.google.it%2F&h=AT0FoPYwWBLXvqp5DozU3tM825MnbibDs4CMiveddVY_sK0EU6xQkdLSyczqe5DMQBQu1Iids3ON6h2eO3NWBffZuxnojN6tVWtUQObb6ZoRtUh7CTcdR5bxZ6vL") &>/dev/null &
[1] 1430
$ getpcaps 1430
Capabilities for `1430': = cap_net_admin,cap_net_raw+p

---

### Post by luca31 on 2018-09-23
the new rules from the capabilities man page are:

  **Transformation of capabilities during execve()**
       During an [execve(2)]("http://man7.org/linux/man-pages/man2/execve.2.html"), the kernel calculates the new capabilities of
       the process using the following algorithm:

           P'(ambient)     = (file is privileged) ? 0 : P(ambient)

           P'(permitted)   = (P(inheritable) & F(inheritable)) |
                             (F(permitted) & cap_bset) | P'(ambient)

           P'(effective)   = F(effective) ? P'(permitted) : P'(ambient)

           P'(inheritable) = P(inheritable)    [i.e., unchanged]

       where:

           P         denotes the value of a thread capability set before the
                     [execve(2)]("http://man7.org/linux/man-pages/man2/execve.2.html")

           P'        denotes the value of a thread capability set after the
                     [execve(2)]("http://man7.org/linux/man-pages/man2/execve.2.html")

           F         denotes a file capability set

           cap_bset  is the value of the capability bounding set (described
                     below).

I expected F(effective) bit to be set but I've no capabilities in effective set of the ping binary 

# getcap /bin/ping
/bin/ping = cap_net_admin,cap_net_raw+p

how can I check if F(effective) bit is set on a file? Using getcap or other utilities?

---

### Post by luca31 on 2018-09-23
Using strace the permission to open the socket is denied as expected:

```

$ strace /bin/ping -c 1 www.google.it
execve("/bin/ping", ["/bin/ping", "-c", "1", "www.google.it"], [/* 17 vars */]) = 0
...
capget({_LINUX_CAPABILITY_VERSION_3, 0}, NULL) = 0
capget({_LINUX_CAPABILITY_VERSION_3, 0}, {0, 0, 0}) = 0
capget({_LINUX_CAPABILITY_VERSION_3, 0}, NULL) = 0
capset({_LINUX_CAPABILITY_VERSION_3, 0}, {0, 0, 0}) = 0
prctl(PR_SET_KEEPCAPS, 1)               = 0
getuid()                                = 1001
setuid(1001)                            = 0
prctl(PR_SET_KEEPCAPS, 0)               = 0
getuid()                                = 1001
geteuid()                               = 1001
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=106070960, ...}) = 0
mmap(NULL, 106070960, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f7ea87cb000
close(3)                                = 0
capget({_LINUX_CAPABILITY_VERSION_3, 0}, NULL) = 0
capget({_LINUX_CAPABILITY_VERSION_3, 0}, {0, 0, 0}) = 0
socket(AF_INET, SOCK_DGRAM, IPPROTO_ICMP) = -1 EACCES (Permission denied)
socket(AF_INET, SOCK_RAW, IPPROTO_ICMP) = -1 EPERM (Operation not permitted)
...
write(2, "ping: socket: Operation not perm"..., 38ping: socket: Operation not permitted
) = 38

```
but without tracing the system call the ping process gets the required privileges anyway
```

$ /bin/ping -c 1 www.google.it
PING www.google.it (172.217.18.35) 56(84) bytes of data.
64 bytes from mrs08s01-in-f3.1e100.net (172.217.18.35): icmp_seq=1 ttl=48 time=10.5 ms

--- www.google.it ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 10.553/10.553/10.553/0.000 ms
$ ls -l /bin/ping
-rwxr-xr-x. 1 root root 66176 Aug  4  2017 /bin/ping

```

I don't get why..

the executable isn't a suid/sgid binary
$ ls -l /bin/ping 
-rwxr-xr-x. 1 root root 66176 Aug  4  2017 /bin/ping
and the user isn't in the wheel group
$ id
uid=1001(barney) gid=1001(barney) groups=1001(barney) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
wtf..

---

### Post by luca31 on 2018-09-23
they set the effective capability inside the code:

from iputils-s20160308/ping.c

```

/* Create sockets */
         enable_capability_raw();
        if (hints.ai_family != AF_INET6)
                create_socket(&sock4, AF_INET, hints.ai_socktype, IPPROTO_ICMP, hints.ai_family == AF_INET);
        if (hints.ai_family != AF_INET)
                create_socket(&sock6, AF_INET6, hints.ai_socktype, IPPROTO_ICMPV6, sock4.fd == -1);
        disable_capability_raw();

```

from iputils-s20160308/ping_common.c

```

static inline int enable_capability_raw(void) { return modify_capability(CAP_NET_RAW,   CAP_SET);   };

[#ifdef]("https://www.facebook.com/hashtag/ifdef?hc_location=ufi") CAPABILITIES
int modify_capability(cap_value_t cap, cap_flag_value_t on)
{
        cap_t cap_p = cap_get_proc();
        cap_flag_value_t cap_ok;
        int rc = -1;

        if (!cap_p) {
                perror("ping: cap_get_proc");
                goto out;
        }

        cap_ok = CAP_CLEAR;
        cap_get_flag(cap_p, cap, CAP_PERMITTED, &cap_ok);
        if (cap_ok == CAP_CLEAR) {
                rc = on ? -1 : 0;
                goto out;
        }

        cap_set_flag(cap_p, CAP_EFFECTIVE, 1, &cap, on);

        if (cap_set_proc(cap_p) < 0) {
                perror("ping: cap_set_proc");
                goto out;
        }

        cap_free(cap_p);

        rc = 0;
out:
        if (cap_p)
                cap_free(cap_p);
        return rc;
}
[#else]("https://www.facebook.com/hashtag/else?hc_location=ufi")

```

it all makes sense now, the rules are right :D
cheers

---

