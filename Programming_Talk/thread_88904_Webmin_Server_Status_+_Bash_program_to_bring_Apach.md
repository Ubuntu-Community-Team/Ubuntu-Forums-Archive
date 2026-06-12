---
title: "Webmin Server Status + Bash program to bring Apache up"
date: 2005-11-11
forum: Programming Talk
---

### Post by xbaez on 2005-11-11
Ok I go to:
[https://mysite.com:10000/status/index.cgi](https://mysite.com:10000/status/index.cgi) (Webmin, Server  Status)
Then I click on "Add Monitor of Type" -> "Apache webserver"
There is an option that sais "If monitor goes down, run command"

I want to creat a bash program
apache_bring_up.sh

in which I will first run a netstat command to see if any other program is listening on port 80 or port 443, so that I can avoid the *(98) Address already in use* error:

This is the program and the out put of it
# netstat --numeric-ports -lp | grep :80
tcp     0   0 srv.site.com:80   *:*         LISTEN      23508/httpd

Ok, so in this example PID 23508 is listening on port 80, the process name is httpd, but some time it happened that qmail was disturbing in those ports.

My main question is, how can I convert this command:
# netstat --numeric-ports -lp | grep :80
in another one that passes the output (in this case: tcp  0  0  srv.site.com:80   *:*   LISTEN   23508/httpd) and gives me only the PID?

I want to kill -9 xxxx that process, and then run start apache again

Thanks in advance

---

### Post by bignate on 2005-11-16
well this isn't pretty but it works...

netstat --numeric-ports -lp | grep :80 | awk -F" " '{print $7}' | awk -F\/ '{print $2}' | sudo xargs killall -9 && sudo /etc/init.d/apache2 start

I am sure there are cleaner ways to do what you want.  But this would do in a pinch

---

### Post by xbaez on 2005-11-22
Thanks for the info I'll try it now

---

### Post by xbaez on 2005-11-22
Thanks, it works perfectly!

Only thing I did was remove the sudo since I'm using RedHat and I'm already root

---

