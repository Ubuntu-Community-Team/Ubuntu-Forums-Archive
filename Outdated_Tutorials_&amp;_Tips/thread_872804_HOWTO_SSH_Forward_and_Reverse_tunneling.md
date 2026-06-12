---
title: "HOWTO: SSH Forward and Reverse tunneling"
date: 2008-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Endwin on 2008-07-28
I have noticed an increase in the number of people wanting to set up SSH tunneling either for secure VNC (Virtual Network Computing) to/from work, secure web browsing, or just to punch a while through a firewall for a service they need to run. What I am going to do is show how to setup forward, and reverse ssh tunneling, and give some examplesof using it.

**BASIC CONCEPTS**

SSH Tunneling is used to forward a port on your machine and have it go through some ssh connection allowing access to another machine usually behind a firewall. Here is an example:

<HOME COMPUTER> => <INTERNET> =><WORK SSH SERVER> => <WORK DESKTOP>

In this case we would like to control our work desktop so we can accomplish some task. We are at home and would like to VNC to our work desktop securly through the internet. We know we have an ssh account at the work public server, but the work desktop does not have a public IP address what do we do? We set up a SSH tunnel to the work ssh server and forward ports so that we can access our work desktop from home.

What we are doing is setting up a port on our home computer that connects to our work computer and has the traffic go through SSH freom our home computer to the work ssh server.  When we connect to the work SSH server it automatically forwards the trafic to our desitred host machine IE work desktop.

**SETUP A SSH TUNNEL**

I am assuming you have an SSH server to connect to, and you brought up a console to type in commands. The basic setup of aSSH tunnel/port forwarding is thus:

```
ssh -L <local port>:<destination machine>:<destination machine port> <user>@<ssh server>
```

A little confusing, let us break it down.

-L - This flag says I want to setup a local port forwarding/tunnel.

<local port> - This is the port I will connect to on my local machine (the machie you are typing the command on).

<destination machine> - The machine on an internal network I want to connect to. Essentially the machine that does not have a public IP address. I want to connect to this machine

<destination machine port> - The port on the destination machine I want to connect to.

<user>@<ssh server> - user account, and machine I will be connecting to with ssh this machine has a public IP but also has access to the internal network so it can "see" the destination machine I want to connect to.

Here is a real world example:

I need to use VNC to control a desktop at work. My work has an internal network protected by a firewall. One of the machines on the net has a SSH server I have access to. Here are the players: HOME_PC, my home computer, SSH_SERV, with user USER_ME, the work public IP ssh server I have access to, WORK_PC, my work PC I need to access. I know VNC uses the default port 5900 for comunications. Using the above guidelines I would have the command be this:
```

ssh -L 5900:WORK_PC:5900 USER_ME@SSH_SERV
```

I would then point my VNC client to:

localhost:5900

and I am in!

**COMMON QUESTION**: Why are the ports the same in this example? Wouldn't it always be the same?

The answer is they are the same because I have nothing locally that runs a VNC server in this case. The key part is the local port needs to be an unused port. There are cases where this is not always the same port, and you need them to be different. Say for example my home pc has a VNC server as well I would then need a different port say 5800 so the command would be modified thus:

```
ssh -L 5800:WORK_PC:5900 USER_ME@SSH_SERV
```

I would then point my VNC client to localhost:5800

This is mainly used there the destination port is in use by your local port.

**REVERSE SSH TUNNELING**

Reverse SSH tunneling works a lot like described above but everything is in reverse. The port you setup makes it so that port points to YOUR machine. This is useful if someone is behind a double nat, or has no real public IP, some ISPs do this.

The basic command is a lot like before but a little different:

```
ssh -R <local port SSH server>:localhost:<local port on machine running command> <user>@<ssh server>

```
This is a little harder to wrap one's head around

-R - This flag says I want to setup a reverse port forwarding/tunnel.

<local port ssh server> - this will be the port on the SSH server that when connected to will come all the way back to the machine that issued the command

localhost - Setup the listening port on the localhost, IE the ssh server.

<local port on machine running command> - This is the port on the machine that is using the ssh connection that the port on the ssh server will connect to.

<user>@<ssh server> - User account and machine that has an ssh server from here I can later use SSH to loopback to the machine that issued the command.

Real life example:

Say I need to help my friend who is behind multiple firewalls, They cannot access the firewall config since it is run by their ISP. They can get to my computer which is an SSH server and has a VNC client on it. I make a user account for them on my ssh server, say myfriend. I would then have my friend run the command:

```
ssh -R 5900:localhost:5900 myfriend@My_SSH_Server
```

I would point my VNC client on the ssh server to:

localhost:5900

and it would then loop back to their machine so I can have access through an SSH tunnel.

The above is not limited to VNC you can do the same thing for any port. mapping an open port on your end. Some common things to forward are ports 80 and 22 (web and SSH respectively) using higher ports in the event lower port ranges are blocked. 6060, and 2222 are often used. Hope this helps clear the fog for some people.

---

