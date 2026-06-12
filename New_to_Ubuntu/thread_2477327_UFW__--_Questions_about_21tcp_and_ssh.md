---
title: "UFW  -- Questions about 21/tcp and ssh"
date: 2022-07-21
forum: New to Ubuntu
---

### Post by bhubunt on 2022-07-21
Hi All,
I have two sets of questions relating to  UFW and Ubuntu 20.04:

1/ First, about port 21 tcp: 

I forgot to close port 21 on installation of Ubuntu 20.04, so I changed the rules to deny 21/tcp incoming on my UFW. But when I checked status verbose of the UFW, for some reason I instead got as a result:

21/tcp   LIMIT IN      (from) ANYWHERE

Port 21/tcp is for the File Transfer Protocol, and for making connections to a server (which I do not have, just a regular laptop). 

Why did I get "limit in" instead of "deny in"?

(I since changed the rule to "deny in" for port 21 but I am still curious to know what "limit in" means.)


2/ Second, about ssh:

on the following website ([https://phoenixnap.com/kb/ssh-to-connect-to-remote-server-linux-or-windows](https://phoenixnap.com/kb/ssh-to-connect-to-remote-server-linux-or-windows)), I read that I need to enter the commands listed below to check if an SSH client is installed on my Ubuntu 20.04. 

I never installed an SSH client on my OS, nor do I want to install one. 

Indeed, I read on several Linux websites that by default remote access via ssh is not allowed on Ubuntu 20.04 upon installation of the OS. Rather, the user needs to activate and install SSH themselves.

However, after I followed the instructions and typed ssh in a terminal I got the same result as pictured below (with my own username and the string of digits being different).

My question: how come I have ssh installed on my OS, when I did not do this myself?

Thanks for your help.
 
[LIST=1]
[*]Type in **ssh** and press **Enter** in the terminal.
[*]If the client is installed, you will receive a response that looks like this:
[/LIST]

[COLOR=#404040][FONT=monospace]username@host[/FONT][/COLOR][COLOR=#404040][FONT=monospace]:~$ sshusage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec][-D [bind_address:]port] [-E log_file] [-e escape_char][-F configfile] [-I pkcs11] [-i identity_file][-J [[/FONT][/COLOR][COLOR=#404040][FONT=monospace]user@[/FONT][/COLOR][COLOR=#404040][FONT=monospace]]host[:port]] [-L address] [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]][[/FONT][/COLOR][COLOR=#404040][FONT=monospace]user@[/FONT][/COLOR][COLOR=#404040][FONT=monospace]]hostname [command][/FONT][/COLOR][COLOR=#404040][FONT=monospace]username@host[/FONT][/COLOR][COLOR=#404040][FONT=monospace]:~$[/FONT][/COLOR]

---

### Post by ActionParsnip on 2022-07-21
If you port forward port 22 then you have SFTP. Please don't use FTP. Its unsecure and garbage. You can install the openssh-server package on Ubuntu and you can then connect using the account on the system you are connecting to, in order to authenticate. Just running "ssh" on it's own doesn't do anyting. Its not a GUI application. You need to specify options.

E.g
```

ssh foo@servername

```

This will then ask you for the password for the username "foo" on the server "servername". Obviously yours will be different and you should adjust the command for your username and your password. If this is the first time connecting then you will be given a certificate and you will need to type "yes" and press ENTER to accept it. You won't need to do this again.

---

### Post by Holger_Gehrke on 2022-07-21
Regarding question 2: AFAIK the openssh-client **is** part of the installation. At least on my XUbuntu 22.04 it's listed in /var/log/installer/initial-status.gz (the list of packages put on the system during installation). It's the server which isn't installed by default. The server is what would allow other systems to connect to your system, if it was running. The client is used if you want to connect to another system.

Holger

---

### Post by bhubunt on 2022-07-22
> **Holger_Gehrke said:**
> Regarding question 2: AFAIK the openssh-client **is** part of the installation. At least on my XUbuntu 22.04 it's listed in /var/log/installer/initial-status.gz (the list of packages put on the system during installation). It's the server which isn't installed by default. The server is what would allow other systems to connect to your system, if it was running. The client is used if you want to connect to another system.

Holger

Hi,
Thanks for explaining that to me. Just to follow-up: how do I remove the openssh-client from my Ubuntu 20.04 OS, as I don't need it? If you could provide command lines or a link to command lines that would be great.

Does anyone know the answer to my first question? What is the difference between "limit" and "deny" in? Limit suggests that some traffic is still coming in through some port? Or did I get that wrong?

And I am also confused about another thing: I am no longer sure why I entered a separate rule for port 21, as the main line of UFW says: deny all incoming. If I have deny all incoming, then why did I need to enter a separate rule for deny or even limit port 21?

---

### Post by The Cog on 2022-07-22
I don't see the point of removing the ssh client myself, but if you really want to, the command is:
```
sudo apt remove openssh-client
```
As for closing port 21, there are two reasons why there was no need to explicitly deny port 21 incoming:
1: If there was a deny all incoming anyway, then explicitly denying 21 in is superfluous, and
2: Unless you are running an FTP server, the OS will reject incoming calls to port 21 anyway, even if the firewall lets the request in.

As for why you ended up with limit and not deny, I have no idea. Maybe I'm being unfair, but I think that may have been a user error.

Just a note on open ports:
In the OS, ports are either:
    - Open: There is an application running that opened the port and is listening for incoming calls, or
    - Closed: No running application has asked to receive incoming calls on that port - they will be rejected with Port Unreachable.
If a firewall is inspecting connection requests, it can choose to either:
    - Accept: Allow the connection request to pass through to the OS unimpeded - the OS can accept or reject, depending on whether the port is open.
    - Drop: Discard the connection request so it never reaches the OS - the call attempt will eventually time out
    - Reject: Not often used - the firewall sends a connection refused indication - the OS never sees the connection request, open or closed is irrelevant.

It bugs me personally when people talk about a firewall "closing" or "opening" a port. Firewalls can't do that - OS applications do. Firewalls, in general, just drop/block or accept/permit particular ports.

---

