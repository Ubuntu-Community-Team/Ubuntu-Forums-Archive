---
title: "Connecting to Ubuntu using UltraVNC"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by iversa on 2013-06-05
[FONT=Droid Serif]I'm a beginner to Linux/Ubuntu (I know windows servers very well) and new to Amazon Web Services as well. [/FONT][FONT=Droid Serif]I have deployed an instance of Ubuntu 12.04 on AWS.[/FONT]

[FONT=Droid Serif]I successfully ran this command to install the desktop GUI [/FONT][B][FONT=Droid Serif]sudo apt-get install ubuntu-desktop
[/FONT][/B][FONT=Droid Serif]
Now I'm trying to use UltraVNC viewer to connect to the instance but can't get it to work. I have opened port 5900 in AWS security groups but not sure if I have to open the port on Ubuntu server as well. I tried but not sure if it worked. 

What do I need to do in order to connect to the using UltraVNC? Keep in mind that I'm a beginner.

When I run [/FONT][COLOR=#324354][FONT=Courier New]netstat -a[/FONT][/COLOR][FONT=Droid Serif] there are the results I get

[/FONT]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:ssh                   *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0    224 ip-10-159-46-181.ec:ssh BMTNON37-30967769:29341 ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN     
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:45024                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp6       0      0 [::]:mdns               [::]:*                             
udp6       0      0 [::]:51923              [::]:*

---

### Post by bswilson on 2013-06-05
I don't see your system listening on port 5900. Is the VNC server running? Try the command "[FONT=Courier New]vnc4server[/FONT]" from the command line. Once you've done that and believe it is running, try the command "[FONT=Courier New]netstat -atpn[/FONT]" to ensure you see something in the neighborhood of port 5900 that looks like VNC. 

Next, have you tried checking on the Firewall running on your Ubuntu image? You may want to try updating your rules as well, with these commands:

[FONT=Courier New]sudo iptables -A INPUT -p tcp --dport 5900 -j ACCEPT
sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT[/FONT]

---

### Post by iversa on 2013-06-05
[COLOR=#000000]@[/COLOR][COLOR=#000000]bswilson
[/COLOR][COLOR=#000000]
Thanks for helping but it is not working yet...[/COLOR]

[COLOR=#000000]**vnc4server** was not installed. After installing and starting **vncserver** it prompted me to enter a password which all worked fine[/COLOR]

[COLOR=#000000]Then I ran[/COLOR]
[B][COLOR=#000000]sudo iptables -A INPUT -p tcp --dport 5900 -j ACCEPT[/COLOR]
[/B][COLOR=#000000]**sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT**

Then with this command **netstat -atpn****[COLOR=#000000] [/COLOR]**I get:**[COLOR=#000000][/COLOR]**[FONT=Courier New]

[/FONT][/COLOR]Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      2182/Xvnc4      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0    464 10.159.46.181:22        184.149.17.4:36664      ESTABLISHED -               
tcp6       0      0 :::5901                 :::*                    LISTEN      2182/Xvnc4      
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
ubuntu@ip-10-159-46-181:~$ 

From what I can tell vncserver is running now. Is there anything I'm missing? How can I find out if the port 5900 is open both on the server and on AWS?

---

### Post by steeldriver on 2013-06-05
It looks like the vncserver is listening on 5901 not 5900 - basically unless you ask for a specific port / display number it chooses the next free one

What I typically do is ssh in and then start vncserver on a specific display e.g.

```
vncserver -geometry 1440x900 :5
```

(it will complain if display :5 / port 5905 is already in use) then you *know* which port to open (5900 + display #)

In fact I'd recommend tunneling VNC over SSH - you still need to know which port/display you started the server on in order to set the tunnel end(s) - but you *don't* need to mess with your actual firewall / open ports because regardless of the VNC port, everything goes externally via your (fixed) SSH port.

---

### Post by iversa on 2013-06-06
I installed [COLOR=#323232][FONT=Monaco]sudo apt-get install nmap[/FONT][/COLOR]

Ran this command nmap -v -PN <host>

These are the results and it appears that port 5900 is there but state is closed. How can I open the port?

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-06-06 10:08 UTC
Initiating Parallel DNS resolution of 1 host. at 10:08
Completed Parallel DNS resolution of 1 host. at 10:08, 0.00s elapsed
Initiating Connect Scan at 10:08
Scanning <host> [1000 ports]
Discovered open port 22/tcp on <host>
Completed Connect Scan at 10:08, 4.41s elapsed (1000 total ports)
Nmap scan report for<host>
Host is up (0.00089s latency).
Not shown: 998 filtered ports
**PORT     STATE  SERVICE**
**22/tcp   open   ssh**
**5900/tcp closed vnc**

---

### Post by SlugSlug on 2013-06-06
As suggested you should run VNC over ssh

I find x11vnc works best for me


I use putty at work with ssh tunnels setup to connect to home 
run 
x11vnc &

then in works windows vnc to localhost

---

### Post by iversa on 2013-06-06
Also I can telnet to port 22 but not 5900

---

### Post by iversa on 2013-06-06
Thanks for the suggestion SlugSlug. Like I said I'm a beginner at Ubuntu/Linux

What are the steps to setup [COLOR=#000000]VNC over ssh[/COLOR]

---

### Post by iversa on 2013-06-06
Ok I finally got it to work connecting directly with VNC Viewer. I'm still working on using SSH tunneling.

But now when I connected with the VNC Viewer for the first time I got the terminal screen. I closed it and now I can't open it again and the desktop GIU does not start either.

How can I get to the desktop GUI?

---

### Post by steeldriver on 2013-06-06
Have you created an appropriate ~/.vnc/xstartup file on the server? That's what tells vncserver what kind of session you wan to run

You probably *don't* want to run a regular (3d) ubuntu session over VNC - at least last time I tried it, handling of compiz was pretty flaky

---

### Post by majorkuso on 2013-06-06
I too am looking in to this, perhaps someone can post a link to a tutorial or something that could help us beginners out

---

### Post by iversa on 2013-06-06
I got it to work. Check this out [http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/](http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/)

---

