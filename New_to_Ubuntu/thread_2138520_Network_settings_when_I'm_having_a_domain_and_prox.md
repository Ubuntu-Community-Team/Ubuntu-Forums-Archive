---
title: "Network settings when I'm having a domain and proxy"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by MrHoek on 2013-04-24
Dear Users,

This is my first post on this forum so Hi to everyone, and my very first day with Linux/Ubuntu.
I have installed Ubuntu 12.10 in an virtual environment (Virtual Machine).
The workstation is not a member of my domain and I don't want to be it, also the Ubuntu workstation is behind a proxy server.

Now I want to install some packages but the *Ubuntu **Software* *Center* won't let me install packages.
I went to the *Network* and then to *Network Proxy* and there filled in the name of our proxy server: *Juno.2work.ltd* with port* 8080*
- Proxy server: Juno
- Domain name: 2work.ltd

And clicked on *Apply system wide*
When this is done I didn't got any packages from the *Ubuntu Software Center*
So I went on the Internet and found the following file to edit: */etc/*apt/apt.conf
When I finally found a way to open it, it showed me the same settings, so this didn't offered me a solution.
Searching further I came a long different topic saying I need to put my username and password @proxy.domain.ltd: 8080
But this didn't worked either for example here is my full line:
- Acquire::http:: proxy "http://martijn: [EMAIL="password@Juno.2work.ltd"]password@Juno.2work.ltd[/EMAIL]:8080/";
- Acquire::https:: proxy "https://martijn: [EMAIL="password@Juno.2work.ltd"]password@Juno.2work.ltd[/EMAIL]:8080/";
- Acquire::ftp:: proxy "ftp://martijn: [EMAIL="password@Juno.2work.ltd"]password@Juno.2work.ltd[/EMAIL]:8080/";
- Acquire::socks:: proxy "socks://martijn: [EMAIL="password@Juno.2work.ltd"]password@Juno.2work.ltd[/EMAIL]:8080/";

Is there anyone knowing what I'm doing wrong?
Since when I go on the Internet with *Firefox* it gives me a possibility to enter my username and password to go on the Internet and then it works.
Username: martijn
Password: password
Proxy server: Juno
Proxy server port: 8080
Domain name: 2work.ltd

I hope there is anyone who can give me a helping hand to provide me a solution so I can use the *U**buntu Software Center* to install software.
Since now I'm stuck in the VM and can not log in with third-party software

Kind regards
Martijn

---

### Post by SeijiSensei on 2013-04-24
I presume the domain name "2work.ltd" is a placeholder?  It's not a valid domain name.

---

### Post by MrHoek on 2013-04-24
Dear SeijiSensei,

Thank you for replying.
That is indeed true these are not valid names I changed them but the idea behind it is the same offcourse.

Kind regards,
Martijn

---

