---
title: "STFP Server - access denied"
date: 2018-05-29
forum: New to Ubuntu
---

### Post by srjohny on 2018-05-29
[IMG]https://imgur.com/a/cXASKIC[/IMG]Hello Everyone, 

I'm newbie with Ubuntu / linux . 

I've configured a new SFTP server with Ubuntu. I installed openssh-server, I can access SFTP and SSH but for some reason after a few time I cannot access anymore and I get a message Access Deny. The first time I thought could be  an attack, so I configured AllowUsers on sshd_config , as happened the same I create Rules UFW allow Rules to the specific IP which access that server.  what is causing Access deny

My ssh_config 
```

AllowUsers Billy
MaxAuthTries 10
MaxSessions 20
PermitEmptyPasswords no
ChallengeResponseAuthentication no
UsePAM yes
X11Forwarding yes
PrintMotd no
AcceptEnv LANG LC_*
Subsystem       sftp    internal-sftp
#Billy FOLDER
Match User billy
ForceCommand internal-sftp
PasswordAuthentication yes
ChrootDirectory /var/sftp/billy
PermitTunnel no
AllowAgentForwarding no
AllowTcpForwarding no
X11Forwarding no
```

---

### Post by TheFu on 2018-05-29
Welcome to the forums.

Troubleshooting client-server protocols follows the same basic steps.
* Check for ping - both directions.
* Check for name resolution - both directions. Or use  IP addresses.   ssh/sftp/scp and other "servers" should have static IPs.
* Disable the system firewall if there is any issue and test again. 
* Double check the router, port forwarding rules, times allowed for forwarding and IPs for in/out access.
* Clients usually have a way to increase "verbosity" and servers usually have a "debug" option that writes more details to the logs.  If you are not seeing anything in the server log file for every connection attempt, then something else is blocking it.
* if you modify any config files, be certain to remember to manually restart or -HUP the service to force the config files to be re-read.

Those steps work, in general, for web servers, mail servers, ssh servers, REST servers, whatever.  It isn't sexy, but looking at the log files are really the best practice.  Most of the time, config files that haven't been touched are fine for a default, unsecured, situation for a little bit. Before you put a service on the public internet, having a locked down service config is very important.

For sftp, the first step is to verify that ssh is working.  ssh and sftp use the same port/protocol, so if ssh is working and sftp is not, it is purely an sftp config error and nothing else.

Some more ssh troubleshooting steps: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

And there is 1 more thing that I was hit by a few months ago on 1 of my servers, but not all. I had to add a line to the server-side sshd_config due to some ssh project internal changes that prefer IPv6 on systems that aren't running IPv6 at all. The line is:
```
AddressFamily inet
```
This system had been working correctly for years before. It was an ssh-server package update that changed previously default behaviors.  The same updates were made to 10 other systems and none of them needed that option added.   

Clear as mud?

If you are looking for ways to secure ssh, that link above has a few articles about that as well. It is my non-commercial blog.

---

