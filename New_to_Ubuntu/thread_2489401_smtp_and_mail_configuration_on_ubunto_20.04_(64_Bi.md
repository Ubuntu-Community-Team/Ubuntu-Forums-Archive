---
title: "smtp and mail configuration on ubunto 20.04 (64 Bit)"
date: 2023-07-28
forum: New to Ubuntu
---

### Post by zehouani on 2023-07-28
hello, 
i recently started working with servers and what not , i eneded up with a vps that i wanted to setup for mailing , nevertheless i ran into my problems , one's which i couldnt connect to my smtp credentiels , i will give where im at right now , what i figured till now is that  that Postfix is indeed listening only on the loopback interface (127.0.0.1), and it's not accessible from external IP addresses , as when i telnet my ip it says "telnet: Unable to connect to remote host: Connection refused"
i will share with you my firewall ports are also well set 
```
root@server:~# sudo ufw statusStatus: active


To                         Action      From
--                         ------      ----
25                         ALLOW       Anywhere
587                        ALLOW       Anywhere
465                        ALLOW       Anywhere
25 (v6)                    ALLOW       Anywhere (v6)
587 (v6)                   ALLOW       Anywhere (v6)
465 (v6)                   ALLOW       Anywhere (v6)


22                         ALLOW OUT   Anywhere
25                         ALLOW OUT   Anywhere
587                        ALLOW OUT   Anywhere
465                        ALLOW OUT   Anywhere
22 (v6)                    ALLOW OUT   Anywhere (v6)
25 (v6)                    ALLOW OUT   Anywhere (v6)
587 (v6)                   ALLOW OUT   Anywhere (v6)
465 (v6)                   ALLOW OUT   Anywhere (v6)


root@server:~#



```

ive been on this issue for quite a while now , to note that i also installed cyberpanel on this server and created a website and an email as where i dont even see them on my server .
to note inet_interfaces is set to all , and please i would be more than happy to share with you my main.cf or master , beside this , the mail log really doesnt share much besite unable to connect ...

---

### Post by TheFu on 2023-07-28
Many VPS providers block email to prevent spammers.  A few months ago, I was setting up a new VPS to be an email gateway for a private network and they refused to enable it until I spent 3 days going back and forth telling them what my email use would be like.  then they enabled it.

So, ask your VPS if they block SMTP and SMTPs on port 25/tcp.  This is probably the issue.

When you setup postfix, there are some options offered.  I usually setup as a "satellite" system for my servers that aren't primarily for email, so they can send emails to my main SMTP server .... like from cron, at, and logwatch alerts.  For email systems, the postfix setup is a little more complex.  LinuxBabe has a how-to guide to get almost everything you probably want setup.  

BTW, you probably don't want ssh on any VPS to listen on 22/tcp.  Move that to a high port or massively filter the IPs that are allowed to use ssh and never allow ssh authentication with just a password.  Force ssh-key/ssh-certs to be used.

BTW, your firewall settings are for SMTP only for server-to-server and client-to-server email transfers.  You don't have any rules for clients to retrieve email via IMAPS or POP3S, which will be needed for any clients to get email.  If you are using webmail, you'll probably use the mbox format or dovecot.  I suppose there are others. I've been using Zimbra since 2008, so I haven't kept up with client stuff.  postfix+dovecot is pretty light.  Zimbra is a hog.  

I need to migrate my Zimbra setup to a new OS and new Zimbra release. The old version uses 4GB of RAM and 2 vCPUs and 30GB of storage, just for the family. Did I mention Zimbra was a hog?  On my zimbra system:

```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           3.9G        3.0G        402M        768K        452M        616M
Swap:          979M        331M        648M

```
I'd never run Zimbra on any VPS.  There, I run a little gateway system inside a linux container to keep it separate from the host VPS. The gateway is very light and uses bog-standard postfix, amavis, clamAV, and the other directly related tools for SMTP to handle spammers. This gateway doesn't hold any data, unless the Zimbra is down. Then it holds inbound emails until Zimbra is back up.

---

### Post by SeijiSensei on 2023-07-29
Look in /etc/postfix/main.cf for this line:
```
#inet_interfaces = all
```

Remove the hash mark at the beginning of the line, then restart postfix. Are you going to be receiving mail from the public Internet? If so, configure the server, then run it through the security checks at mxtoolbox.com.

---

### Post by TheFu on 2023-07-29
Good catch, 

I've had to add 
$ egrep inet   /etc/postfix/main.cf
```
inet_interfaces = all
inet_protocols = ipv4
```
the inet_protocols line for a few years as well.

---

