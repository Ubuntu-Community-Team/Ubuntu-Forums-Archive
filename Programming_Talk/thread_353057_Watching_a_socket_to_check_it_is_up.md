---
title: "Watching a socket to check it is up"
date: 2007-02-04
forum: Programming Talk
---

### Post by doughie on 2007-02-04
I have a socket server which i run on my box.  I would like to run a cron job to check if the socket is open and if it is not then start up the app that provides the socket.

What would the best way be?

I was thinking a small php script that opened the socket and run a system() command starting the server if the connection is down.

//edit

here is my solution 

[php]#! /usr/bin/php
<?php

$sock = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
socket_connect($sock,"localhost", 9999);

switch(socket_select($r = array($sock), $w = array($sock), $f = array($sock), 5))
{
        case 2:
                echo "[-] Connection Refused\n";
                system('/home/socketserver/start.sh &');
                break;

        case 1:
                echo "[+] Connected\n";
                break;

        case 0:
                echo "[-] Timeout\n";
                break;
}

exit(0);
?>
[/php]


the problem is that control is not being returned to the terminal after i run this script

---

### Post by winch on 2007-02-04
If you want the server app running all the time why not start it in an [init]("http://en.wikipedia.org/wiki/Init") script?

Also [inetd]("http://en.wikipedia.org/wiki/Inetd") can be used to listen on a port and lanch the server app when required.

---

### Post by SuperMike on 2007-02-04
You could implement this Bash with 'expect' command a good bit easier and get a result back that lets you know more than just the port being up, but see if it returns the kind of stuff you're looking to know is up. That's how I do it at my office.

For instance, I have one expect script that tests whether SSH is responding with the two typical responses you get back from SSH. If SSH is up and responding within the expect timeout, then I know fairly well that server doesn't have the processor utilization maxed out.

On another server, I test the backup agent. Now the backup agent runs in binary and is not something I can parse back. However, my expect script, instead of using ssh, uses 'telnet <server> <port num>' as its way to connect. If telnet returns an error, then the backup agent is down. If not, then the backup agent is more than likely up.

However, if you want to go the Perl or PHP route, it's perfectly okay too. I'm a big fan of PHP. However, in my office, the admins there won't let me install PHP on every box just so that I can run system scripts. They would prefer I stick with 'expect', 'telnet', 'ssh', perl, and/or bash.

Before I learned about 'expect', I once wrote an FTP checker script in PHP that tested pushing a test file up and pulling it back down again. If you want to see that, let me know. I'll have to VPN into my office and login to a server to get it for you. Otherwise, I would just say try 'expect' and Bash because it's faster.

---

