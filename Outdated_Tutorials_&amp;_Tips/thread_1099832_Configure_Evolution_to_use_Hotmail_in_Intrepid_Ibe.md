---
title: "Configure Evolution to use Hotmail in Intrepid Ibex"
date: 2009-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Marcelo Ruiz on 2009-03-18
Hi,

This is my first post in the forum. I had problems configuring Evolution to use hotmail but finally got it working. Several threads in different sites pointed to solutions that didn't work for my current configuration:
[LIST]
[*]Ubuntu Intrepid Ibex (8.10)
[*]Evolution 2.24
[*]xinetd (eXtended InterNET Daemon) instead of inetd
[/LIST]

Here are the steps I followed:

1- [COLOR="Blue"]Using Synaptic install hotway and hotsmtp (you can find both of them by typing hotmail in the Quick Search Box)[/COLOR].

2- [COLOR="Blue"]Open a terminal and type:[/COLOR]

***sudo gedit /etc/xinetd.d/hotwayd***

[COLOR="Blue"]in the new window that opens type (or copy & paste) this:[/COLOR]

[B][I]
service hotwayd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotwayd
server_args = -r
port = 110
}[/I][/B]

[COLOR="Blue"]save the file and close gedit[/COLOR]

3- [COLOR="Blue"]You should be back to the terminal you opened in step 2. Now type:[/COLOR]

***sudo gedit /etc/xinetd.d/hotsmtpd***

[COLOR="Blue"]in the new window that opens copy this:[/COLOR]

[B][I]service hotsmtpd
{
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = nobody
groups = yes
server = /usr/bin/hotsmtpd
#server_args = -r
port = 25
}[/I][/B]

[COLOR="Blue"]save the file and close gedit[/COLOR].

4 - [COLOR="Blue"]You're back at the same Terminal window. Type:[/COLOR]

***sudo gedit /etc/hosts***

[COLOR="Blue"]this command will open a file which content should be similar to this one:[/COLOR]

[I]127.0.0.1	localhost
127.0.1.1	Lobo

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/I]

[COLOR="Blue"]in this file you need to add the following two lines:[/COLOR]

[B][I]hotwayd: 127.0.0.1
hotsmtpd: 127.0.0.1[/I][/B]
[COLOR="Blue"]
So the new content of the hosts file will be:[/COLOR]

[I]127.0.0.1	localhost
127.0.1.1	Lobo
hotwayd: 127.0.0.1
hotsmtpd: 127.0.0.1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/I]

[COLOR="Blue"]save the file and close gedit.[/COLOR]

5 - [COLOR="Blue"]You're back at the Terminal window. Now we need to restart xinetd, so type:[/COLOR]

***sudo /etc/init.d/xinetd restart***

[COLOR="Blue"]the output you'll get should be:[/COLOR]

[I] * Stopping internet superserver xinetd         [ OK ] 
 * Starting internet superserver xinetd         [ OK ][/I]

6 - [COLOR="Blue"]We're going to try the previous configuration works by typing in the Terminal window:[/COLOR]
[B][I]
sudo telnet localhost 25[/I][/B]

[COLOR="Blue"]the output you'll get should be similar to:[/COLOR]
[I]
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 Lobo SMTP hotsmtpd v0.8.4. ESMTP-HTTPMail Gateway based on hotwayd.[/I]

[COLOR="Blue"]now type:[/COLOR]

***quit***

[COLOR="Blue"]and hit the Enter key.[/COLOR]

[COLOR="Blue"]you'll get the following output:[/COLOR]
[I]
221 Service closing transmission channel
Connection closed by foreign host.[/I]

7 - [COLOR="Blue"]We are going to repeat step 6 for port 110, so type in the Terminal window:[/COLOR]
[B][I]
sudo telnet localhost 110[/I][/B]

[COLOR="Blue"]the output you'll get should be similar to:[/COLOR]
[I]Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
+OK POP3 hotwayd v0.8.4 -> The POP3-HTTPMail Gateway. Server on Lobo active.[/I]

[COLOR="Blue"]now type:[/COLOR]

***quit***

[COLOR="Blue"]and hit the Enter key.[/COLOR]

[COLOR="Blue"]you'll get the following output:[/COLOR]
[I]
+OK see you later!
Connection closed by foreign host.
[/I]

8 - [COLOR="Blue"]It's time to configure Evolution now. Open Evolution and go to Edit -> Preferences. In the Preferences window you will be looking at the Mail Accounts. Click on Add. You'll be in the Identity tab. Fill in the information in that tab.[/COLOR]

[COLOR="Blue"]Now go to Receiving Email. There you need put the following info:[/COLOR]

Server Type: ***POP***
Server: ***127.0.0.1:110***
Username: *(full hotmail address, _including @hotmail.com_)*
Use Secure Connection: ***No Encryption***
Authentication Type: ***Password***
[COLOR="Blue"]
[COLOR="Blue"]Check Remember Password if you want.[/COLOR]

Now go to Sending Email. There you need to put the following info:[/COLOR]

Server Type: SMTP
Server: ***127.0.0.1:25***
[COLOR="Blue"]Check Server Requires authentication[/COLOR]
Use Secure Connection: ***No Encryption***
Authentication Type: ***Plain***
Username: *(full hotmail address, _including @hotmail.com_)*
[COLOR="Blue"]Check Remember Password if you want.[/COLOR]
[COLOR="Blue"]
Click OK[/COLOR]


We are done! You should be able to send and receive e-mail through Hotmail now!
Enjoy!

:)

---

