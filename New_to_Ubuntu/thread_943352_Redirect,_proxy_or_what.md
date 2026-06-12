---
title: "Redirect, proxy or what?"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by erkswede on 2008-10-10
Hi all

I need help with the following situation:

I need to access a web application on port 8010 (HTTP) on my ubuntu-server from a clients office. That office has a firewall and doesnt allow outbound traffic on 8010. Port 80 works ofcourse. 

In my server I have a apache2 installed that supports different services on port 80. The application on port 8010 has it's own web-server, therefore the different port.

Now, it is possible to use some kind of proxy or redirect and setup eg myserver.com/the_application pointing to myserver.com:8010?

Any other ideas are very welcome.

Regards
/Erik

---

### Post by yogensha on 2008-10-10
I'd use an SSH tunnel.  You'll have to find a port to run sshd on on your Ubuntu server that gets through the client firewall.  I'll bet 443 works too.

To set up the tunnel:

ssh -L<lport>:localhost:8010 <host>

Where <lport> is the local port for the tunnel and <host> is your server.  Then point your web browser at http://localhost:<lport>.

What this does is creates a tunnel from your local machine on <lport> to port 8010 on the remote host.  The 'localhost' portion of the -L option specifies where the end of the tunnel is from the _remote's_ perspective.  See the ssh man page for more information.

If you're running windows on the client side, I'd recommend putty.  There are options for building tunnels that look alot like the -L option for the command line ssh.

---

### Post by erkswede on 2008-10-11
Thanks yogensha

I was hoping to find a solution that doesn't affect the client PC, as I'm not the only one who needs to access this application.

If no other solutions are possible a tunnel will do.
/Erik

---

### Post by erkswede on 2010-04-10
Well, I found a solution after a couple of years. I used the mod_proxy for Apache described here: [http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

---

