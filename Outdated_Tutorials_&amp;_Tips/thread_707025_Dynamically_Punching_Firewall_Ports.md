---
title: "Dynamically Punching Firewall Ports"
date: 2008-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2008-02-25
**UPDATE: 2-25-08: ** punchfw now closes ports the application doesn't hold open.


**Synopsis:**

This guide shows how to define a command to dynamically punch open firewall ports. P2P programs, IM clients, and other networking clients may open a dynamic or random port in order to function, and it can be difficult to write firewall rules for such cases.


This is designed to be used in conjunction **with a blocking firewall**. Again, punchfw **OPENS** ports. Running it on a system without a configured firewall does not add any security benefits. It'll try to open an opened port, which works but is rather useless.

**Usage example:**
```

$ punchfw transmission
punchfw: Process opened new port: ["tcp", "9090"]
punchfw: Process opened new port: ["tcp", "9091"]
punchfw: Process closed port: ["tcp", "9090"]



```

This launches the Transmission torrent client, at the same time telling iptables to open any ports Transmission demands. When Transmission closes, all of these ports would be closed. In this case, Transmission opened port 9090/tcp. Via preferences, I told Transmission to open port 9091 rather than 9090. After a few seconds, punchfw realized this and opened the new port and closed the old one.

** Security Implications **:
As with any security measure, it can actually introduce security vulnerabilities, so think hard before blindly applying a tool like this. I've tried to list the obvious security issues that came to mind:
[LIST=1]
[*]Authorized punchfw users will be able to open any port in the allowed range. This of course is necessary for function but think if it's what you want.
[*]The portfw_helper script needs to run as root. Although it's been designed to only call iptables with authorized input, my poor programming skills could lead to a vulnerability. I've tried to make it short and easy to read/review. It would not be a bad idea to use an apparmor/SELinux profile to make sure the tool can only call iptables.
[*] If you use a SIGKILL on the punchfw (kill -9), it will leave these ports open.
[*] More of a software limitation, if the child process launches another child to open ports, then those ports will not be detected and opened. Sorry.
[/LIST]


** How it works **

Instead of launching application "foo", launch "punchfw foo". Punchfw will launch foo on your behalf, and also monitor it periodically (every 2 secs until it opens a port, every 30s after that in case it opens a new port) for opened ports. It then calls "punchfw_helper" with sudo to open up the port via iptables. Finally, an exit hook makes sure all opened ports are closed.


** Installation Instructions **

Attached tarball contains "punchfw" and "punchfw_helper". Both should be installed to your path in /usr/local/bin.

```

$ sudo tar xzvf punchfw-0.1.tar.gz -C /usr/local/bin

```

Next, we need to set up sudo to allow punchfw_helper to run iptables as root.

Run **sudo visudo** to start an editor, and add this line to the end of the file:

```

%admin ALL=NOPASSWD:/usr/local/bin/punchfw_helper

```
This gives the admin group rights to punchfw_helper without the need to enter a password. I wouldn't suggest giving this kind of power to any less trusted group.


** Using punchfw **

As said, just put "punchfw" in front of any command you'd usually run that needs this functionality. Also, you can adjust launcher icons and such to point to punchfw variants of the original command.

** Additional Customizations **

I added the ability to "ban" ports from being opened. Look at the source code for /usr/local/bin/punchfw_helper. You'll find a line like:
```

banned_ports=[ ["tcp", 50000], #Additional banned pairs here

]

```

In here, you can add comma separated pairs of "protocol", portnumber that will not be allowed to be punchable. By default, all ports under 1024 are banned. These allow you to prevent users/applications from opening sensitive ports on the system via portfw_helper.

---

### Post by say2sky on 2008-03-05
This is good way to have more security server and I will try it by myself as your howto, thank you very much.

I also googled and found some similar application such as fwknop(Firewall Knock Operator) and knockd but I haven't had time to compare them. Would you give some idea about pros and cons of them. Thanks!

---

### Post by jdong on 2008-03-05
fwknop and knockd both operate on the opposite side (unsolicited inbound connection) -- they are advanced and good for their purpose, but not what I wanted. I wanted something more permissive for my bittorrent client -- that it can grab ANY port it wants and I'll let it open.

---

### Post by say2sky on 2008-03-05
> **jdong said:**
> fwknop and knockd both operate on the opposite side (unsolicited inbound connection) -- they are advanced and good for their purpose, but not what I wanted. I wanted something more permissive for my bittorrent client -- that it can grab ANY port it wants and I'll let it open.

Oh, great I see, yours open ports from lan inside let p2p client use. fwknop and knockd for user to open ports on a server from outside.  So they are totally for different purpose.

---

### Post by jdong on 2008-03-05
Indeed, they both open firewall ports, but for entirely different cases.

---

