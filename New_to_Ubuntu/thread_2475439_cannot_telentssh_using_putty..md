---
title: "cannot telent/ssh using putty."
date: 2022-05-27
forum: New to Ubuntu
---

### Post by explorerhead on 2022-05-27
[FONT=-apple-system, BlinkMacSystemFont, Segoe UI Adjusted, Segoe UI, Liberation Sans, sans-serif][COLOR=#232629] putty was working fine until i recently upgraded the system to 22.04 LTS. now i can see the putty is working only if its invoked with #sudo putty from terminal. or else its just starting the interface but not able to ssh/telnet to any devices. my final requirement is to launch putty from firefox page using telnetL//x.x.x.x:1234. using the firefox application handler /usr/bin/putty[/COLOR][/FONT]

---

### Post by TheFu on 2022-05-27
Is putty being used on a Windows system?  I've never seen anyone use it on a Linux box.  I use an xterm for my ssh windows into other systems. It is extremely efficient with select/paste and use of ssh-key and the config file to make access to different systems crazy easy.

There's little need to use putty on any Linux, since almost any terminal program is a superior interface for ssh.  Or just use screen or tmux.

In 22.04, some ssh ciphers were modified - removing weak ones and reordering the defaults used to prefer stronger ciphers.  The 22.04 release notes spell this out. They should be backwards compatible for almost all systems. I've not had issues, but I switched to using ed25519 keys about 4 yrs ago.

In 22.04, firefox runs as a snap, inside a constrained environment which prevents running unexpected external programs. Putty would be one of those and I doubt anyone on the firefox snap package team will change it.  99.999% of users shouldn't be using telnet in 2022 ... or since 2002-ish. There are times when telnet is handy, but most people switched to using netcat for those uses about 10 yrs ago. 

You could open a bug with the firefox snap package team to allow ssh:// URLs to be handled by external tools, but I have to say that I've never seen anyone, anywhere, use a URL like that from any browser.  It would seem odd to me.  I suppose we all have different experiences.

sudo abuse is a real issue with people new to Linux. 

Of course, you can look up how to load firefox from a non-snap package, which should let you use it as in prior releases, just with less security.

---

### Post by explorerhead on 2022-05-29
Thanks, i shall check that

---

### Post by ActionParsnip on 2022-05-29
Why do you need PuTTY? You can SSH from the terminal
```

ssh user@server

```

---

### Post by explorerhead on 2022-05-31
@[COLOR=#000000]ActionParsnip .[/COLOR]i have a simulator running in VMware. it uses a http interface  to connect to this vm and administering. it has only web interface for starting the nodes and launching. the hyperlinks on the page are on the format [telnet://"ip_addr" : "portnumber]("telnet://ip_addr:portnumber")."

---

### Post by TheFu on 2022-05-31
All I can say is that is a very poor design for security.
If it were me, I'd grab a copy of the page and setup ssh connections in my ~/.ssh/config file for the systems I will access.  Far too many webapp devs are ignorant of standard utilities like ssh and the easy of use features built-in.

Also, x2go can setup a pretty GUI for access into lots of systems.

---

### Post by mIk3_08 on 2022-06-01
I strongly agree with TheFu and ActionParsnip xtern or terminal is one way to communicate to server. Fast and very secure with your own key to the tunnel for data communication. I used this method for a quite a while now and it helps me a lot for fast and efficient secure service to my client. It seems it gives light weight to my job specially to parallels plesk servers. Regards and cheers.

---

