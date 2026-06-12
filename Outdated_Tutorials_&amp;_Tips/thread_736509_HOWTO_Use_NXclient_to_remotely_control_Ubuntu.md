---
title: "HOWTO: Use NXclient to remotely control Ubuntu"
date: 2008-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by A$h X on 2008-03-26
**[SIZE="3"]What does remote desktop mean?[/SIZE]**

Well all it means is that you could have a machine at home/work/wherever which you want to access from another machine at a different location. Remote Desktop (or virtualization as it's now called) allows you to do this.

**[SIZE="3"]What do server, host, and client mean?[/SIZE]**

The server is the machine you want to control. It may be your home PC or a work machine you want to access whilst you are on the move or from another companies' machine. 
Host is just another way to refer to the server.
The client is the machine from which you want to access the remote machine AKA  the machine from which you will control the server. Another way to look at it is if you want to control your home PC from work then your work PC is the client and the home PC is the server.

Got that? Server= Far away computer, Client = Computer your sitting at now.

**[SIZE="3"]What you need:[/SIZE]**

Okay firstly there are loads of remote desktop (RDP) programs out there, I'll be using NXclient/server. With NXclient you require a minimum of effort to get things up and running, and it is popular as it is very fast compared to rival products. It is also free for linux and windows users, so that's an advantage.

Right now here's the files you need:
For an Ubuntu Gutsy (or any debian based distro) SERVER:

NXclient: [http://64.34.161.181/download/3.1.0/Linux/nxclient_3.1.0-6_i386.deb](http://64.34.161.181/download/3.1.0/Linux/nxclient_3.1.0-6_i386.deb)

NXnode: [http://64.34.161.181/download/3.1.0/Linux/nxnode_3.1.0-6_i386.deb](http://64.34.161.181/download/3.1.0/Linux/nxnode_3.1.0-6_i386.deb)

NXserver:[http://64.34.161.181/download/3.1.0/Linux/FE/nxserver_3.1.0-5_i386.deb](http://64.34.161.181/download/3.1.0/Linux/FE/nxserver_3.1.0-5_i386.deb)

You need ALL of these files to able to control your ubuntu machine remotely.
Download and install them IN EXACTLY THE ORDER STATED. So that's client, node and finally server.

Next you need openSSH-server. Get it from the repo by searching for "openssh" or type:
> sudo apt-get install openssh-server

Now for your CLIENT you only need the NXclient software as posted above. For windows users get the Windows XP Professional NXclient here:

[http://64.34.161.181/download/3.1.0/Windows/nxclient-3.1.0-6.exe](http://64.34.161.181/download/3.1.0/Windows/nxclient-3.1.0-6.exe)

So now you have installed the client, node and server and openSSH-server software on the ubuntu machine you want to control, and the NXclient software on the ubuntu/windows machine from which you'll be doing the controlling.

**[SIZE="3"]STEP 1: Testing SSH[/SIZE]**

We just want to see if SSH is behaving as it should be, so in terminal type:
>  ssh localhost
Type yes when prompted. Now type:
> ssh [email]username@your.ipaddress.here[/email]
where "username "  is your ubuntu username, and "your.ipaddress.here" is your IP address.
If you do not know your IP address then visit [http://whatismyipaddress.com/](http://whatismyipaddress.com/) 

The final command for SSH is:
> sudo /etc/init.d/ssh restart

Okay SSH server is configured, next is...

**[SIZE="3"]STEP 2: Configuring NXserver[/SIZE]**
We want to check if NXserver is running, so type (press return after each line):

> cd /
cd /usr/NX/bin
sudo ./nxserver --status

That should say NX server is running. Next type: 
> 
sudo ./nxserver --useradd username  --administrator

where "username" is your ubuntu username. This will add a NXserver user who has admin rights, I think this is necessary as normal users must be added by the admin, so the admin must be setup first. Anyway you will then be prompted for the system password (your login password) so go ahead and type it. After all that a new admin user should have been added, and a key generated. 
To check if the user was added correctly type:
> sudo ./nxserver --userlist

The username you just entered should be there. Now see if everything is okay authenication wise. Type:
> sudo ./nxserver --usercheck username
where username is your system username. If everything is fine and dandy then I believe we are done with configuring NXserver.

**[SIZE="3"]STEP 3: Opening a listening port[/SIZE]**

You need to open port 22 on the server so NXclient can login. I use firestarter GUI to do this, which simply provides a front-end to ubuntu's built-in firewall IPtables. Go to synaptic and search for "firestarter" or type 
> sudo apt-get install firestarter

Start firestarter (from applications > internet) and then goto the policy tab and right click in the "allow service" window and add rule. Choose SSH from the drop-down menu and port 22 is automatically selected. Leave the "apply for" value as anyone, click OK and click apply policy. 

If you have a router, then you will need to open port 22 in your router setup as well as in firestarter. More info about opening ports on your particular brand of router can be found at [www.portforward.com](www.portforward.com)


We are now finished configuring your ubuntu server. Now we just need to login from the client. 

**[SIZE="3"]STEP 4: Connecting using NXclient[/SIZE]**
Once the server is all set then you need to configure the client. Start the NXclient connection wizard and enter a name for the session, then you have to enter the host. Here you enter the IP address of the server and the port is already set to 22. Click Next and you have enter what kind of machine you are connecting to. In the case of ubuntu it will be unix gnome, in the case of kubuntu it will be unix KDE. You can also specify how much screen space will taken up by the remote desktop window (I usually pick 800*600). Click next and finally you will be presented with a small NXclient box. Enter your username in the login field, your system password in the password field, and leave the session as it is. 

If everything went according to plan then you should have a window pop up with a red !M logo, and then it should change into your remote desktop. Enjoy! :)

**[SIZE="3"]Wait! I'm worried about security![/SIZE]**
I don't blame you, and there are a few steps we can take to ensure your remote desktop connection is more secure. Firstly because port 22 is a common target, we'll change it to something else. Firstly type:

> sudo gedit /etc/ssh/sshd_config
Where it says:
> # What ports, IPs and protocols we listen for
Port 22

change 22 for whatever port you wish. I suggest a higher number like 55555 as the lower numbers are used by other applications. SSH also requires another file to be modified to change your port. Type:
> sudo gedit /etc/ssh/ssh_config

and on the line reading:
> #   Port 22

delete the # symbol and change 22 to the value you chose for your port.

Now we must change the config file for NXserver to listen on our new port. Type
> sudo gedit /usr/NX/etc/server.cfg
Change the value 22 in the following two lines:
> # Specify the TCP port where the NX server SSHD daemon is running.
#
# SSHDPort = "22"
(make sure to delete the # from in front of SSHD)

> 
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
SSHDAuthPort = "22"
to the value you chose for your port (55555 in my example). Finally you need to open your chosen port in firestarter and your router if you have one as shown above. Don't forget to delete the entry for port 22.

Now on NXclient you simply change the port to the value you chose and everything should work as before.

A fairly serious security hole is that when you logon to your remote desktop, you use the system password so you have full read/write/delete access which may not be good thing if the computer NXclient is on is an untrusted machine. 
I recommend creating a separate user account on ubuntu which can only read/write to certain areas so as to minimize any chances of malicious action. Then create a NXserver account with that limited access user. You could also specify exactly what actions the NX user can take eg only use installed programs, no terminal access, no desktop only terminal etc.
I would recommend creating a separate NX account for each session at untrusted clients, and then deleting that user after your work is done. Ideally you should be not be remote connecting from insecure machines at all.

Another security risk is that your encryption key for NXclient may be copied, you can generate new keys from the server and then copy them over to the client (physically obviously, or by other means apart from NXclient).

You can find how to create restricted users, create and distribute new encryption keys and more from the NXserver manual, which can be found here:

[http://www.nomachine.com/documents/admin-guide.php](http://www.nomachine.com/documents/admin-guide.php)

**[SIZE="3"]Hey, I want to control XP from Ubuntu![/SIZE]**

Unfortunately, there is no NXserver for windows (yet), so NXclient cannot control a XP machine. 
BUT there is a better solution in that all the programs you need are already installed by default in gutsy and XP professional. Two simple steps are all it takes:

**[SIZE="3"]Step 1: Configuring remote desktop on XP[/SIZE]**

In XP goto control panel > system.
Click the remote tab of the system window.
Tick the "allow users to connect remotely to this computer" check box.
Click apply and OK.

Now open a port to allow us to connect in your firewall and router if you have one. By default remote desktop uses port 3389, but for security reasons you are advised to change it. Make sure the protocol is set to UDP. 
**I have been informed that ubuntu can only communicate with remote desktop if it uses the default port of 3389 so ignore the changing port advice until the bug is resolved. **

**[SIZE="3"]Step 2: Configuring Terminal Server client[/SIZE]**
Now on your ubuntu system goto applications > internet > terminal server client.

In the computer box type the IP address of the XP machine you want to connect to, in the form of the IP address followed by a colon followed by the port number you opened. eg if the XP machines' IP address was 123.456.0.1 and the port we had opened was 55555, then this is what you would type:
> 123.456.0.1:55555

The default listening port for remote desktop is 3389 so if you didn't change it then you would use 3389, in that case you don't need to enter a colon followed by the port number, just the IP address 123.456.0.1 would be enough.

Leave protocol as RDP.
In user type the windows username that you use to login into XP.
In password type the windows password that you use to login into XP.
In client hostname type the name of the ubuntu machine. This step is optional IIRC.

Hit connect and that's it! You should get a window appear with your remote XP desktop inside it. :)

**Note: Due to the publicly known port number amongst other reasons, remote desktop is very insecure, I recommend using SSH tunneling on the XP machine see here:**

[http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html](http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html)

**This will allow you to make a secure connection using port 3389.**

---

### Post by Inxsible on 2008-04-02
I believe there is a small typo in your very useful guide.

If someone wants to change the SSH port then they would find the server.cfg file under /usr/NX/etc and NOT /usr/NX as mentioned in your guide. Apart from that, everything worked for me.


Having said that, I used a 1024x768 screen resolution from my XP machine, but I cannot see the entire desktop. i.e. I cannot see the AWN bar at the bottom and the gnome-panel that I have at the top. So I have to keep pressing Alt+F2 to do anything. Is there a way I can see the entire desktop including the two bars ?

My Ubuntu machine's resolution is 1440x900, if that matters.

---

### Post by A$h X on 2008-04-02
Glad you found the guide useful and thanks for catching the typo.
As far as not being able to see the entire remote desktop, because your ubuntu desktop is larger than your XP desktop, you won't be able fit the entire remote desktop into a window unfortunately. 
Try lowering the resolution of your ubuntu desktop (system> preferences > screen resolution)  to 1024x768 or less so you can have it in fullscreen in XP.

---

### Post by Inxsible on 2008-04-03
Thanks, I will try to change the resolution on the Ubuntu box.

But I tried to login right now and this is what I am getting:
Authentication failed for user: 

I have attached a screenshot. And I have tried it multiple times and it still does not work. I even tried it with a couple other usernames that I have on the ubuntu box

---

### Post by A$h X on 2008-04-03
Is SSHserver and NXserver running on the ubuntu machine? Make sure you are logging in with a NX user; that is a user you have created in NXserver as specified in the guide?

---

### Post by Inxsible on 2008-04-03
> **A$h X said:**
> Is SSHserver and NXserver running on the ubuntu machine? Make sure you are logging in with a NX user; that is a user you have created in NXserver as specified in the guide?
Yes to all the questions :(.

I'll try it again tonight.

---

### Post by hansonlee on 2008-04-04
I tried to add myself to the admin userlist in nxserver, but I kept getting error message that the system is unable to generate the SSH key. 

I have the openSSH installed and running, and can even login from other computer through SSH telnet. 

Ubuntu version: 7.10

Anyone has an idea? Thanks!

```

hanson@lsa-271c-004:/usr/NX/bin$ sudo ./nxserver --usercheck hanson
NX> 900 Verifying public key authentication for NX user: hanson.
NX> 900 Adding public key for user: hanson to the authorized keys file.
NX> 596 ERROR: NXNODE Ver. 3.1.0-6  (Error id e705430)
NX> 596 ERROR: Cannot add NX server public DSA key for user: hanson
NX> 596 to the authorized keys file.
NX> 596 ERROR: Cannot create file: /home/hanson/.ssh/authorized_keys2: Permission denied.
NX> 900 ERROR: Failed to add public key.
NX> 999 Bye.

```

---

### Post by Inxsible on 2008-04-04
Ok I think my problem is with the fact that I changed my port. Because if I change my port back to 22 it works.

if its anything but 22, I keep getting the "Authentication failed for user :  _____" error.

---

### Post by Inxsible on 2008-04-05
Any ideas anyone?

everything works when I use the default SSH port of 22, but if I change it to anything else, i keep getting Authentication errors. :(

---

### Post by A$h X on 2008-04-06
> **Inxsible said:**
> Any ideas anyone?

everything works when I use the default SSH port of 22, but if I change it to anything else, i keep getting Authentication errors. :(

Changing the port works on mine, are you sure you have created a rule in firestarter and changed the port in NXclient? Make sure the port value is the same in all four (SSHD_config, server.cfg, and firestarter on the server, and NXclient's target port on the remote computer).

hansonlee: I'm trying to find more info on your problem, googling your error ID draws a blank, in the mean time trying deleting your user and re-adding them to see if it helps. Or create another system user, then add them as a SSH and NXserver user.

---

### Post by Princey on 2008-04-06
Thanks for the guide. It worked perfectly using the settings suggested. However, when I changed my port as I wanted to move away from port 22, I keep getting an error message from my laptop saying authentification failed. Of course, I'm trying this from home before I leave for work. The machine I want to control is my desktop server/workstation. 

My problem is with ssh however, as everything has been changed even I follow your steps to the letter. Say I changed to 55555 as you stated, I connect but get an authentification error. Testing on the machine where nxserver is installed, I get this error:
> ssh localhost
ssh: connect to host localhost port 22: Connection refused

My port has been changed in /etc/ssh/sshd_config

---

### Post by A$h X on 2008-04-06
Try this:
> sudo gedit /etc/ssh/ssh_config

and change

> #   Port 22

to 

> Port 55555

where 55555 is whatever port you chose. Hopefully sorts out your problems.

---

### Post by Inxsible on 2008-04-06
> **A$h X said:**
> Changing the port works on mine, are you sure you have created a rule in firestarter and changed the port in NXclient? Make sure the port value is the same in all four (SSHD_config, server.cfg, and firestarter on the server, and NXclient's target port on the remote computer).

hansonlee: I'm trying to find more info on your problem, googling your error ID draws a blank, in the mean time trying deleting your user and re-adding them to see if it helps. Or create another system user, then add them as a SSH and NXserver user.Hi Ash,
Yeah I did change the ports everywhere that it was required viz sshd_config, server.cfg, firestarter, my router(i.e.port forwarding) and finally in the nx client on my other PC.

Gotta get this thing working. Now its pissing me off !!!!

---

### Post by Inxsible on 2008-04-06
the server.cfg file has two places ```

# Specify the TCP port where the NX server SSHD daemon is running.
#
SSHDPort = "22"
``` and ```
#
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
SSHDAuthPort = "22"
``` So my question is do we have to change both to a different port?

I was only changing the SSHDAuthPort until now. Maybe that's the problem. Also we do have to KEEP the quotes right ? Just checking...

---

### Post by A$h X on 2008-04-06
Yeah, change both instances of the port and keep the quotes. Try that and if it's STILL not working then try changing ssh_config as mentioned two posts earlier. But only change one file at a time so we can isolate the problem.

---

### Post by Inxsible on 2008-04-06
SUCCESS !!!!

I was finally able to connect after changing the port. But I did have to change the port in the server.cfg at both the places that I mentioned before.

Thanks A$h X for all your help !!!

---

### Post by A$h X on 2008-04-06
Good to hear. Now anyone having the same problem will know what to do. I'll update the guide to show the port number in server.cfg needs to be changed in two different places. 
Also Princey, I suspect this will also solve your problem.

---

### Post by Princey on 2008-04-06
A$h X, my problem is identical to Inxsible. I've now changed the two instances in the server.cfg file. A question though, I see for both instances that the "#" sign appears in front of them. To my limited knowledge, normally that symbol comments out the line. Do I leave it or remove it? In other words, should it read 1. > #SSHDAuthPort = 55555 still using your port example or 2. > SSHDAuthPort =55555

---

### Post by Inxsible on 2008-04-06
No, you have to  remove the # sign. As you said, Ubuntu ignores everything on the line after a #

---

### Post by A$h X on 2008-04-06
If a line has a # in front then as you say, ubuntu ignores it. You must delete the # to apply the changes. 
The # is present as port 22 is default, so SSH knows where to look already. If you uncomment it, then a value must be defined. Get rid of it and put your port number and it should be working fine.

---

### Post by Princey on 2008-04-06
Couple things. I can now connect from my laptop, however, after the desktop appears, it disconnects saying "connection lost, please check your network connection". I'm still getting the error message "ssh: connect to host localhost port 22: Connection refused" when I type in ssh localhost in konsole. Could those two be related? If anything, the laptop runs Kubuntu 7.10 while the workstation/server runs Hardy Heron beta.

Edit:

Went doing some googling for the error message and found a debug command. Based on the output, am I correct to assume that localhost which was first setup for ssh during the beginning steps is what's messing around? Here's the output:

> emmjay@speedy2:~$ ssh -v emmjay@localhost
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused


Note: I have already changed the port to a number above 55555 in sshd_config, nhserver config and in firestarter. The port is already forwarded in my router.

---

### Post by A$h X on 2008-04-07
You have the line:

> debug1: Reading configuration data /etc/ssh/ssh_config

It appears ssh_config maybe responsible, so try changing the port value in /etc/ssh/ssh_config so 
> #   Port 22
should read
>    Port 55555

---

### Post by Princey on 2008-04-07
Thanks A$h X. I did not realise that there was another entry. All the time I was focussing on sshd_config only not realising that ssh_config existed as well. In addition, I had to do the following as I was still getting disconnected.

1. Change the value in /etc/ssh/ssh_config as previously stated

2. Remove the comment out symbol (#) in front of it as nothing changed when I first changed the port number. Saved the file and restarted ssh server.

3. Log into localhost then log in with my username and ip address to generate new keys.

Only then did it work perfectly. I'll have to wait until I get to work to see if it works from outside of the router. I'm just curious though since I'm using port forwarding through my router, do I need to add my external IP or is the internal ip of the machine it's running on sufficient?

---

### Post by A$h X on 2008-04-07
> **Princey said:**
> I'm just curious though since I'm using port forwarding through my router, do I need to add my external IP or is the internal ip of the machine it's running on sufficient?

Good question, as long as you have forwarded the port in your router, then if you want to login over the internet then you will use your REAL IP address as host, ie the one shown in [www.whatismyip.com](www.whatismyip.com) along with the port you are using for SSH.

The IP's you use on your home network are internal only, outside of machines connected to your router, they have no meaning.

And in case you are wondering "well if I only have one real IP address, but I have lots of machines on my network, then how can i connect to a particular machine over the internet?" Port forwarding allows data coming over a specified port to be sent to a specified computer.

So if you had a machine which had an internal (set by you via the router/ubuntu) IP of192.168.0.10, and your real (external) IP was 12.345.678.90 and you had opened port 55555 and forwarded it to 192.168.0.10, then from the internet ALL traffic (including SSH) directed to port 55555 would automatically goto internal IP 192.168.0.10. 

Hope that clarifies the difference between internal and external IP addresses for you.

---

### Post by Princey on 2008-04-07
Thanks, I do understand the differences. I connect to my other machine running Windows XP over the internet from work so I'm not new to computers or routers. It's just my first attempt using a Linux box since my Linux machine is now my main production machine. I'm still familiarising myself with Linux. However, putting all that aside, my question was whether I should add the external IP as part of the key setup with ssh like how we did in the command > ssh username@ipaddress

My other problem now that I'm at work is that I can connect to my computer. However, one of the messages I keep getting (got it at home when I used the laptop and thought maybe it was because I was behind the router. Doesn't appear to be) reads:

> The connection with the remote server was shut down. Please check the state of your network connection.

I am certain that the port is forwarded (wouldn't connect in fact if it wasn't forwarded), all ports correspond to 55555 (using that as an example) in Firestarter, nhserver.config, ssh_config, sshd_config. What am I missing? I can't do a verbose debug right now as I'm at work and would need a live connection which I can't keep at the moment as I get kicked off with that message once the desktop is loaded and 3 seconds passes there after. I already disabled desktop effects as I read earlier it may cause problems.

If anything, my computer at work runs WinXP SP2 and the port is correctly set in the client.

---

### Post by A$h X on 2008-04-07
If you are 100% sure that openSSH server and NXserver are running on your ubuntu host then we'll have to delve deeper. I want you to install PuTTY on your XP machine (if allowed) and then from PuTTY type:
> ssh [email]username@your.IP.address.here[/email] -p XXXX

where username = ubuntu username, your.IP.address.here = your router's external IP, and XXXX = your chosen SSH port. Let me know what the result is, then we'll go from there.

---

### Post by Princey on 2008-04-07
> **A$h X said:**
> If you are 100% sure that openSSH server and NXserver are running on your ubuntu host then we'll have to delve deeper. I want you to install PuTTY on your XP machine (if allowed) and then from PuTTY type:


where username = ubuntu username, your.IP.address.here = your router's external IP, and XXXX = your chosen SSH port. Let me know what the result is, then we'll go from there.

I installed putty on my U3 enabled USB thumb drive. I'm currently connected to my machine at the command prompt. Connection holds so far.

---

### Post by MemoryDump on 2008-04-07
is there a way to make NX resume an already active desktop session? (similiar to what VNC does) I leave my computer logged on at home.. and like to connect to it from work on occassion. What NX does is create a new remote session.

great tutorial btw ;)

---

### Post by Inxsible on 2008-04-07
Guys,

I don't know if anyone of you has experienced this, but sometimes when I connect, I simply get a black screen. Restarting my Ubuntu machine and then trying again seems to resolve the problem sometimes.

Also, now I need to try it with a dydns or a no-ip domain name and see if it works outside of my internal network.

---

### Post by Inxsible on 2008-04-07
Princey,

I am not sure if you need to change 2 files for ssh. I only made changes in the sshd_config file.

Although, I am not sure if this is KDE specific as I use Gnome.

---

### Post by Princey on 2008-04-08
Here's the new output from the command > ssh -v emmjay@localhost

> 
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port xxxxx.
debug1: Connection established.
debug1: identity file /home/emmjay/.ssh/identity type -1
debug1: identity file /home/emmjay/.ssh/id_rsa type -1
debug1: identity file /home/emmjay/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: checking without port identifier
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/emmjay/.ssh/known_hosts:1
debug1: found matching key w/out port
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/emmjay/.ssh/identity
debug1: Trying private key: /home/emmjay/.ssh/id_rsa
debug1: Trying private key: /home/emmjay/.ssh/id_dsa
debug1: Next authentication method: password
emmjay@localhost's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux speedy2 2.6.24-15-generic #1 SMP Fri Apr 4 03:10:59 UTC 2008 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Apr  7 14:10:44 2008 from 10.110.15.82
emmjay@speedy2:~$


From the debug information, it appears that ssh is working properly now however, nomachine still closes with the error message stated in my previous post that the session has been closed, please check my network connection which I find is weird. I use a 2MB ADSL at home and work. I'm starting to get grey hair over this.


---------------------------
Update: I purged all settings and started all over again making sure to install the client first, then the node, then the server. I still keep getting the same error message. Is there a way to get a dubug report like I can get with ssh? I've read the administrator guide but found nothing.

---

### Post by A$h X on 2008-04-09
I've been trying to find out some more info on your problem Princey, and the error you are experiencing could be caused by three of the follwoing:

1) Incompatible server and client versions.
2) Nxserver (free edition) only supports two connections at a time, so if you are logged in from  another tow machines, your third connection will fail. (Make sure you aren't logged in from any other machine to be sure).
3) SSH + NXclient will only work if "Disable encryption of all traffic" in unchecked on NXclient (Settings > advanced tab).

Now seeing as you have the latest versions of NXserver/client/node, it can't be symptom 1. 
With symptom 3, the  "Disable encryption of all traffic" option is unchecked by default, but make sure it hasn't been selected by mistake.
Which leads me to believe that it's symptom 2, just make sure that all the necessary processes are running, and there are no sessions active before you goto work. You can use the NX session administrator to be sure.

And unfortunately there are no logs AFAIK which could pinpoint the problem, unless someone knows otherwise.

MemoryDump: One of the advantages of VNC over NX is that it allows to to login into an existing session, but NX creates a new session. I don't think NX will allow you to "pick up where you left off" when you were using your server machine locally. But still, try the "shadow" option from NXclient, it maybe what you are looking for.

---

### Post by Princey on 2008-04-09
Couple things to note, I didn't use your downloads as they're 32bit only while I run 64 bit. Therefore, I downloaded the 64bit versions of client, server (free edition) and node from the NOMachine website. Could that be the problem. And as far as I know, there are no other processes running utilising nxserver. I even used putty to shut down the nxserver daemon and start it afresh. The only machine left running at home is my Kubuntu workstation/server. I'm at work now, but I'll check the versions that I'm running to see if there's any incompatibilities. Thanks for the info.

---

### Post by Inxsible on 2008-04-09
I don't think 64 bit is your problem. I use 64 bit and it works for me.

---

### Post by Princey on 2008-04-09
Thanks for the assurance. I'll have a bit more time to go at it tomorrow after work. At least, I have another machine to test it from. I'll try making some changes with NX admin itself and see what happens.

---

### Post by smartboyathome on 2008-04-10
I get an error when trying to install nxserver from the website. Here it is:
```
NX> 701 ERROR: Output: chown: invalid user: `nx:root'.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc' to 'nx:root'.
dpkg: error processing nxserver (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Please help, I would like this to work so I can get NXclient working.

---

### Post by Princey on 2008-04-10
If you're using the debs from the website, you should type in "sudo dpkg -i nxse..." normally I press the tab key where the ... appears and that auto completes the entry. If that's what you did, then dpkg was previously interrupted and > sudo dpkg --configure -a should resolve the issue for you.

---

### Post by hansonlee on 2008-04-10
> **A$h X said:**
>  hansonlee: I'm trying to find more info on your problem, googling your error ID draws a blank, in the mean time trying deleting your user and re-adding them to see if it helps. Or create another system user, then add them as a SSH and NXserver user.

I use this command to generate a NX and system user at the same time and it works!

```

nxserver --useradd NEWUSER --system --administrator

```

Still don't understand why adding an existing user to NX server doesn't work, though.:confused:

---

### Post by Princey on 2008-04-10
> **Inxsible said:**
> I don't think 64 bit is your problem. I use 64 bit and it works for me.

Where did you get your package from? Did you use those from the nomachine website? Or was it from the repos? Just curious as you said yours happen to work.

---

### Post by Inxsible on 2008-04-11
> **Princey said:**
> Where did you get your package from? Did you use those from the nomachine website? Or was it from the repos? Just curious as you said yours happen to work. I got the latest debs from the nomachine website.

I would suggest that you purge everything and then redo it. uninstall ssh, nxserver/nxnode/nxclient etc along with the config files

---

### Post by Princey on 2008-04-11
Thanks. That's where I got mine as well. But I'll take your advice when I get home. I can uninstall the nx packages but seeing it's ssh I use to log in for now via putty, I'd have to be at my machine to uninstall it. I'll purge everything when I get home and start from scratch. I'll post back with my results.

---

### Post by Princey on 2008-04-13
> **Inxsible said:**
> I got the latest debs from the nomachine website.

I would suggest that you purge everything and then redo it. uninstall ssh, nxserver/nxnode/nxclient etc along with the config files

I've since done that, followed every step and still can't get the connection to work on port 22 far less for 55555. I have made no sure that there are no running sessions. Every attempt fails after the screen is loaded with the same error message that the session has been shut down and to check my connection. I've run verbose mode on both my local IP behind NAT and localhost and all say ssh is running as expected. I'm really lost here and might start losing some hair too. This is really a feature I NEED working as of last week. Here's the error message from NX session Administrator on the last login.

> 
NXAGENT - Version 3.1.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '28654'.
Session: Starting session at 'Sun Apr 13 12:40:28 2008'.
Info: Proxy running in server mode with pid '28654'.
Info: Waiting for connection from '127.0.0.1' on port '5006'.
Info: Accepted connection from '127.0.0.1'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using agent parameters 5000/0/50/0/0.
Info: Using pack method 'adaptive-9' with session 'kde'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Listening to X11 connections on display ':1006'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/1/2048K.
Info: Using alpha channel in render extension.
Info: Not using local device configuration changes.
Session: Session started at 'Sun Apr 13 12:40:30 2008'.
Info: Screen [0] resized to geometry [1280x951].


---

### Post by wampirek on 2008-04-14
Hello, 

I have Vista installed on my laptop and Gutsy on desktop. 
When I log from Vista, everything seems to look fine, but I don't see programs in backgroung with their icons in tray. For example:  I often leave Gutsy with Deluge running for whole day and when I logg in I cannot control Deluge - I simply don't see its icon :( 

Is there any way to make icons in try visible? 

Regards, 
Wampirek

---

### Post by atomkarinca on 2008-04-14
> **wampirek said:**
> Hello, 

I have Vista installed on my laptop and Gutsy on desktop. 
When I log from Vista, everything seems to look fine, but I don't see programs in backgroung with their icons in tray. For example:  I often leave Gutsy with Deluge running for whole day and when I logg in I cannot control Deluge - I simply don't see its icon :( 

Is there any way to make icons in try visible? 

Regards, 
Wampirek

This is because NX cannot connect to an existing session. You should use VNC for that.

---

### Post by alphacrux on 2008-04-16
I have a question, is it possible to do this with a dynamic ip address, and does anything have to be done differently if so? Also my computer is on a lan behind a router, i.e. no direct connection if that makes any difference.

---

### Post by A$h X on 2008-04-16
> **alphacrux said:**
> I have a question, is it possible to do this with a dynamic ip address, and does anything have to be done differently if so? Also my computer is on a lan behind a router, i.e. no direct connection if that makes any difference.
If you have a dynamic IP which is assigned by your ISP, then you will need to use something like dyndns.com then enter that info into your router (or install a program if you don't have one) which will give you a "pretend" static IP which automatically points to your changing dynamic IP. 

And yes, it will work behind a router, all the examples have been constructed to assume you have a network setup. Of course, you don't need a router, and it makes life slightly easier as you only have to open ports on firestarter. But the advantage of having a router + home network is that you can try out NXclient/server on your network to make sure it's running correctly before using it from a remote computer.

---

### Post by Princey on 2008-04-16
Okay guys, I think I need some bit of clarification here. I've seen mention made of NX not being able to resume a session and I thought it meant resuming another nxsession. However, in trying to diagnose my dilemna, I tried one of the free sessions from the NoMachine website. I got connected!!! But something struck me hence my reason for seeking clarification.

1. If I have already logged into my computer and leave it running at home, does that equate to a "session"? 

2. If that's the case, does it mean that I would simply need to turn my computer on but NOT log in if I have to control it from outside?

3. How then, if the answer to point #2 is correct, do I resume a session either started remotely or one that I started locally and left running while at home? 

I'd be grateful for any clarification on the said questions.

---

### Post by A$h X on 2008-04-16
> **Princey said:**
> 
1. If I have already logged into my computer and leave it running at home, does that equate to a "session"? 

2. If that's the case, does it mean that I would simply need to turn my computer on but NOT log in if I have to control it from outside?

3. How then, if the answer to point #2 is correct, do I resume a session either started remotely or one that I started locally and left running while at home?

1. Yes that's correct. A session is one instance of a user logging in. So as soon you login into ubuntu a session has begun.

2. No, you must login into the ubuntu OS on the host, but that's it. After having your desktop appear after login, leave your server machine as it is. No need to run any SSH or NX processes, they all should be running from startup.

3. You can't use NXclient to login into a existing session. What happens is that  on your client machine you get a window containing your server desktop WITHOUT any programs that might have been running. So say I had firefox and rhythmbox music player running on my server. When I login using NXclient from my remote machine I will see my desktop and everything on it APART from firefox and rhythmbox. As far as my client is concerned those programs aren't running. 

But if I physically went back to my server machine then firefox and rhythmbox would still be running, and I could run whatever programs I want without disturbing the remote session. And vice versa so the client could do what it wants and the server machine would be unaware.
The two sessions exist simultaneously and never interfere with each other, aside from drastic measures like turning the server machine off.

Pretty cool if you ask me. :-D

---

### Post by Princey on 2008-04-16
Thanks, A$h X for clearing that up. However, it still brings me back to square one. I thought maybe that was what I was doing wrong but even getting home for lunch and testing by doing a clean reboot, I still keep getting thrown back out after logging in with the error message "The connection with the remote server was shut down. Please check the state of your network connection." 

I've done everything from configuring the node, server on the home server and client on the machine at work. I know it's not ssh as I can connect and stay connected to my home machine using putty, so that bit I know is out of the way. I double-checked to see if maybe the client was out of date but I used the latest packages from the nomachine website. I am beginning to think that Hardy could be the reason, but I'm not so sure. Any other ideas?

______________
Update: I went to configure, and under desktop, I chose shadow. Amazingly, I got connected to the session that was already in. I'm not sure if it's my connection here at work that has been spotty for the past few days or I could be wrong. I could only view not able to get response from anything. I'll toy around with the settings and report back should I get anything working. Just that when I chose unix and kde (which is what I have running at home) I get the error mentioned above that keeps making me lose hair.

---

### Post by A$h X on 2008-04-16
Well, you seem to be halfway there, but there's still some funny things going on. With a shadow session, the server displays your actions on-screen, so a user on the server machine can watch (but not interfere with) what's going on.
Weird that you can only watch what's happening and not perform actions (almost like you were the server and they were the client).

As an aside it seems the problems maybe on the client side so try unix-gnome as the session type.

---

### Post by Princey on 2008-04-17
Here's an update. For one, using gnome throws me an error saying gdm isn't installed and the window stays open until I close it. I found out with the shadow session that I can perform actions, start programmes, close applications, anything as if I'm sitting on my machine at home. The only thing is  I just don't get to see it in "real time". If I close the window, log back in, all the changes are there. Say I opened firefox. I won't see it open instantly or even if I wait for 4 hours. However, if I close the window, re-log in using shadow session, I see firefox is opened. None of the other methods yield any result. 

I'm tempted to think it's the Windows client, but using the Windows client I do get connected to NoMachines test servers and secondly, the two linux computers at home besides the server are having the same hiccups connecting. I'll try purging nx packages, delete all settings and try yet again when I get home this evening.

---

### Post by alphacrux on 2008-04-19
First off thanks goes to ashx for writing and maintaining this HOW-TO, it sure as hell made things a lot easier for me :)

Now I'm not trying to step on any toes here but there are a couple things I noticed that I think will improve your HOW-TO. First in step 2: > cd /
cd /usr/NX/bin
sudo ./nxserver --status The "cd /" is superfluous. The second line will change to the /usr/NX/bin directory regardless of which directory you are already in (kind of pointless I know but for some reason this just really irked me). 

Secondly don't you think Step 3 should be first. In Step one you link to a site that gives the ip address of the network NOT an individual computer. Therefore to check if ssh is working properly you will have had to already set up your router to forward port 22 to your computer. 

Finally in step 3 you have > sudo apt-get install firestarter  You describe it as a simple gui to your ip-tables but actually firestarter is a firewall for linux. Setting up a firewall can cause conflicts with other apps that use the network. For instance firestarter is known to not be friendly with samba (at least not without further configuration) which is needed for sharing files with windows computers. Even though firestarter is pretty easy to use, I think setting up a firewall is beyond the scope of this HOW-TO and there is probably a better alternative. Personally after I set up the port-forwarding in my router, I was able to ssh in with my network's ip address successfully without having to open up any ports with linux.

Again not trying to step on any toes, these are just the few grievances I had while reading through the HOW-TO that I thought I ought to tell you. Hopefully this helps out, thanks again for the otherwise awesome how-to and help!

---

### Post by atomkarinca on 2008-04-20
> **alphacrux said:**
> Finally in step 3 you have  You describe it as a simple gui to your ip-tables but actually firestarter is a firewall for linux. 

It IS a simple gui to your iptables. You can check your iptables with:

```
sudo iptables -L
```

Firestarter just adds or removes rules to your iptables.

---

### Post by alphacrux on 2008-04-20
This may be true but even on its own website [[COLOR="Blue"]here[/COLOR]]("http://www.fs-security.com/") firestarter describes its own project as a *firewall*.

Also here are a few threads to corroborate my claim that it causes issues with samba a few of which actually solve the problem [[COLOR="Blue"]thread1[/COLOR]]("http://ubuntuforums.org/showthread.php?t=528592"), [[COLOR="Blue"]thread2[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=190542&highlight=firestarter+samba"), [[COLOR="Blue"]thread3[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=134384&highlight=firestarter+samba"), [[COLOR="Blue"]thread4[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=152905&highlight=firestarter+samba")

Maybe all firestarter does is add iptable rules, but somehow when it is setup initially something is changed or configured so that samba is no longer working. This may be the only problem that exists with firestarter, but even so this is a pretty big deal for me. I recommend giving thread2 a read, it is beyond me being a total iptable noob, but the guy really seems like he knows what he is talking about, and just why firestarter and samba are interacting badly.

---

### Post by alphacrux on 2008-04-20
So I have read through [[COLOR="Blue"]thread2[/COLOR]]("http://ph.ubuntuforums.com/showthread.php?t=190542&highlight=firestarter+samba") and the problem with samba is that even though "firestarter is just a front-end for iptables" it also blocks all ports unless otherwise specified to open them. In this case firestarter was preventing a response being issued to a netbios broadcast from another computer on the network trying to receive your ip address. In other words ubuntu receives the broadcast and tries to respond with its ip address but is blocked. Its somewhat complicated and lengthy so I'll let you guys read the thread on your own for details. It seems however that without firestarter there is nothing hindering use of any of your ports (correct me if I'm wrong) which does leave your computer vulnerable, but if you're behind a router anyways then who cares. Once firestarter is activated it seems you have to be specific about which ports you use. Also the samba issue is even an instance where opening up a port STILL won't solve the issue, meaning again firestarter is interfering, although to be fair if you read the thread this is a pretty specific problem that shouldn't affect most other applications. This issue and the fact that you now have to unblock ports however, is what I mean by that setting up a firewall is probably out of the scope of this how-to. Again by all means correct me if I'm wrong but I believe this is how this all works.

---

### Post by Princey on 2008-04-28
Okay, I did a FRESH install of Hardy Heron and started from scratch with the tutorial being careful to follow word by word. Installed nxclient, then nxnode, then nxserver; installed openssh-server and went through the configuration settings. I STILL can't connect to my machine from the computer in the room which is behind a router. If I can't connect, then there's no way I will connect from work. I'm still being thrown with the very same symptoms I mentioned. I get logged in then seconds after I'm kicked out saying, "The connection with the remote server was shut down. Please check the state of your network connection." Of course, that's done with the default port #22. I must get it running on the said port before I change it to something more secure.

I've searched via Google for hours, and nothing concrete comes up as all articles are more than 2yrs old and points to issues that have already been addressed in subsequent versions. Any ideas before I throw in the towel?

---

### Post by gozotto on 2008-04-29
It works fine but I see some problems with hardy.
See link:
[http://ubuntuforums.org/showthread.php?t=773824]("http://ubuntuforums.org/showthread.php?t=773824")

---

### Post by A$h X on 2008-04-29
Can you post up up your etc/hosts and etc/hostname files please? There was a similar issue of not being able to connect even though everything was in place and it turned out to be these files.

---

### Post by Princey on 2008-04-29
I'm currently at work and I did not change the ssh port to the normal one I use and have allowed passthrough in my router so I'll have to wait until I get home to do so, but I will once I'm home. Thanks for the help so far.

---

### Post by mulpuru on 2008-04-29
I followed the instructions ...
```
wget http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-9_i386.deb
wget http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-5_i386.deb
wget http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-7_i386.deb
apt-get install libstdc++2.10-glibc2.2
dpkg -i nxclient_3.2.0-9_i386.deb
dpkg -i nxnode_3.2.0-5_i386.deb
dpkg -i nxserver_3.2.0-7_i386.deb
/usr/NX/scripts/setup/nxserver --server-keygen
copied /usr/NX/share/keys/default.id_dsa.key to the nxclient machine and used it


```

But when i try to connect it gives me host not found error (it was able to authenticate though)

Error log From Nxclient (using winxp and NX win client 1.50-13)
```
NX> 203 NXSSH running with pid: 2948
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 131.183.16.47 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: siva
NX> 102 Password: ******
NX> 103 Welcome to: laptop user: siva
NX> 105 Listsession --user="siva" --status="suspended\054running" --geometry="1600x1200x32+render" --type="unix-kde" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: siva
NX> 105 Start session with: --session="laptop" --type="unix-kde" --cache="8M" --images="32M" --link="lan" --kbtype="pc102\057en_US" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="1600x1170" --media="0" --agent_server="" --agent_user="" --agent_password="" --agent_domain="" --screeninfo="1600x1170x32+render" 
NXSERVER - Version 3.2.0-7 - LFE
Tue Apr 29 14:56:37 2008 running as user: 'nx' (uid: 110, pid: 5685) on 'laptop'
Info: user login is siva (NXShell)
Info: user password is '******' (NXShell)
Info: using 'sshd authentication' (NXShell)
Info: selected user 'siva' is authenticated (NXNodeExec)
Info: password for selected user is in 'text' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l siva localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 5695 (NXNodeExec)
[B]Info: received data in err channel from NX Node: 'nxssh: localhost: Name or service not known
' (NXNodeExec)
[/B]Info: NX Node out channel was closed (NXNodeExec)
Info: Removing not recognized buffer from stdout:[] (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
Killed by signal 15.

```

**/Var/log/messages**
```
Apr 29 14:56:36 laptop NXSERVER-3.2.0-7[5685]: User 'siva' logged in from '131.183.21.137'. 'NXLogin::set'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: Selected node host:localhost with port:22 'main::selectNode'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: Current selected node: localhost is in status: running  'main::selectNode'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: Selected session type: unix-kde allowed in the profile of user: siva 'NXShell::Static'
Apr 29 14:56:37 laptop NXSERVER-3.2.0-7[5685]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) Error: no 'CONNECTED' message from NX Node
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) nxssh: localhost: Name or service not known^M
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXNodeExec::exec('startsession', 'user=siva&userip=131%2e183%2e21%2e137&uniqueid=84AF740D79C212559...', 'localhost', 22) called at handlers/nxserver.pl line 3275
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXShell::handler_session_start('--session="laptop" --type="unix-kde" --cache="8M" --images="32M"...') called at NXShell.pm line 373
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXShell::handle_command('startsession', '--session="laptop" --type="unix-kde" --cache="8M" --images="32M"...') called at NXShell.pm line 145
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) NXShell::run() called at nxserver.pl line 4430
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: ERROR: (exception id 30DB3597) eval {...} called at nxserver.pl line 4389
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'
Apr 29 14:56:38 laptop NXSERVER-3.2.0-7[5685]: Received 'PIPE' signal: this signal is ignored by NX Server 'main::Static'


```

```
root@laptop:~# cat /etc/hostname
laptop
root@laptop:~# cat /etc/hosts
127.0.0.1 laptop
127.0.1.1 laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

could some please help me...? :KS

---

### Post by Princey on 2008-04-29
Here are the results of the commands you asked, a$hx

```
cat /etc/hostname
```
> speedytux

```
cat /etc/hosts
```
> 127.0.0.1	localhost
127.0.1.1	speedytux

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Princey on 2008-04-29
SUCCESS! SUCCESS! SUCCESS!

I finally got it up and running, thanks to something I came across from the RedHat/Fedora forums while doing yet another search. Nothing was wrong with the NX settings per se. The problem was elsewhere. Somehow, the default settings in kontrol center under sessions is set to "resume" on log in. That was what that kept throwing me back out. What I did was to change it as suggested by the poster in the above mentioned forums from "resume" to "start with an empty session". Saved my changes, went back to the other computer and logged in, and lo and behold my desktop loaded and STAYED loaded. :guitar:. I was elated. I left it run a good 5 minutes to see if it would crap out, nothing. Stayed true and faithful.

For those who've had a similar issue, here are the steps to follow:


[LIST=1]
[*]Hold down the Alt + F2 keys or click on the Kmenu and chose "run command". 
[*]Type in kcontrol in the box and press the enter key.
[*]Click on kde components that the sub menu can expand. 
[*]Click on session Manager and chose "start with an empty session" under the section "on login". Click ok and you're done. See below image for clarification.
[IMG]http://i307.photobucket.com/albums/nn285/emmjey/OtherForums/kcontrol-1.png[/IMG]
[/LIST]

@mulpuru, try the packages from nomachine's website. Uninstall those you downloaded first though.[http://www.nomachine.com/download-package.php?Prod_Id=6]("http://www.nomachine.com/download-package.php?Prod_Id=6")

@alphacrux, thanks so much for the information you provided about firestarter. My network went down completely once I got everything running and the 2nd post you linked to did help me solve that problem. Now everything is working perfect!!!

---

### Post by mulpuru on 2008-04-30
thank you guys, but i had solved the problem
had to add 
```
127.0.0.1 localhost
``` 
to /etc/hosts

---

### Post by Princey on 2008-04-30
Something I noticed, while I was able to connect successfully at home, I changed the ports to something about 50000 and still couldn't connect. I kept getting a message that node.cfg was trying to connect to port 22 of ssh. I had to ssh into my machine using putty, change the line in /usr/NX/etc/node.cfg using nano. Tried again, nothing, 5 minutes after, same error. Fired up putty again, restarted the nxserver and all worked fine there after. Just something to note in case someone runs into that problem.

---

### Post by hlovdal on 2008-05-06
> **smartboyathome said:**
> I get an error when trying to install nxserver from the website. Here it is:
```
NX> 701 ERROR: Output: chown: invalid user: `nx:root'.
NX> 701 ERROR: Cannot set ownership attributes for '/usr/NX/etc' to 'nx:root'.
dpkg: error processing nxserver (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I also got the error message
```
NX> 701 ERROR: Output: chown: `nx:root': invalid user.
``` when I tried to install nxserver-3.2.0-7.i386.rpm on my Fedora release 7 system. After some trial and error it turned out to probably be that I had copied /usr/NX/etc/server-fedora.cfg.sample to server.cfg before installing nxserver that made the difference.

When renaming /usr/NX/etc before installing nxserver so that this directory then was recreated from scratch, undoing any modifiactions I had made, the nx user was created properly and the nxserver installation finished successfully.

---

### Post by txmail on 2008-06-12
> **Inxsible said:**
> the server.cfg file has two places ```

# Specify the TCP port where the NX server SSHD daemon is running.
#
SSHDPort = "22"
``` and ```
#
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
SSHDAuthPort = "22"
``` So my question is do we have to change both to a different port?

I was only changing the SSHDAuthPort until now. Maybe that's the problem. Also we do have to KEEP the quotes right ? Just checking...

W00t! Worked for me also, missed that second place in server.cfg.

---

### Post by hiptahop on 2008-07-03
> **Princey said:**
> The problem was elsewhere. Somehow, the default settings in kontrol center under sessions is set to "resume" on log in. That was what that kept throwing me back out. What I did was to change it as suggested by the poster in the above mentioned forums from "resume" to "start with an empty session".

I have the same error as Princey, but I'm operating Gnome.  I am hoping the solution will translate.  What would be the equivalent steps?  Is there a reasonably simple way to do this remotely (SSH) at terminal?

---

### Post by Endolith on 2008-09-08
> **hlovdal said:**
> When renaming /usr/NX/etc before installing nxserver so that this directory then was recreated from scratch, undoing any modifiactions I had made, the nx user was created properly and the nxserver installation finished successfully.

I also got the "`nx:root': invalid user" error, and solved it by removing /usr/NX completely before re-installing.  Then I have to follow [these directions]("http://ubuntuforums.org/showthread.php?t=784880#3") to get it to work.

---

### Post by webik on 2008-09-23
The newest veriosn of packages:
```

[http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-14_i386.deb](http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-14_i386.deb)
[http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-13_i386.deb](http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-13_i386.deb)
[http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-16_i386.deb](http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-16_i386.deb)

```
--

webik

---

### Post by Endolith on 2008-09-23
> **webik said:**
> The newest veriosn of packages:
```

[http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-14_i386.deb](http://64.34.161.181/download/3.2.0/Linux/nxclient_3.2.0-14_i386.deb)
[http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-13_i386.deb](http://64.34.161.181/download/3.2.0/Linux/nxnode_3.2.0-13_i386.deb)
[http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-16_i386.deb](http://64.34.161.181/download/3.2.0/Linux/FE/nxserver_3.2.0-16_i386.deb)

```

I wrote a little script to get the latest versions of these packages and install them automatically, since [Ubuntu won't package them]("https://bugs.launchpad.net/ubuntu/+bug/102025") and I was sick of going to the website and doing it all by hand:

```
#!/usr/bin/env python

# Simple script to upgrade NX Free Edition for Linux to latest version on 
# website using .deb installers
# 
# 2008-09-23

# NoMachine download page
url = "[http://www.nomachine.com/download-package.php?Prod_Id=6](http://www.nomachine.com/download-package.php?Prod_Id=6)"

import urllib
import sys
import os

from HTMLParser import HTMLParser

# Only root can install packages
if os.getuid() != 0:
    sys.exit("Script needs to be run as root (with sudo)")

# Scrape a web page and make a list of .deb links
class ScrapeDebs(HTMLParser):
    def __init__(self):
        HTMLParser.__init__(self)
        self.links = []
    
    def handle_starttag(self, tag, attrs):
        if tag == 'a' and attrs[0][0] == 'href':
            if attrs[0][1][-4:] == '.deb':
                self.links.append(attrs[0][1])

# Read NoMachine web site
print "\nDownloading latest .deb files from" 
print url + "\n"

f = urllib.urlopen(url)
b = ScrapeDebs();
b.feed(f.read())
f.close()
b.close()

for link in b.links:
    if "nxclient" in link:
        nxclient = link
    if "nxnode" in link:
        nxnode = link
    if "nxserver" in link:
        nxserver = link

# Download packages
os.system("wget -nc " + nxclient + ' ' + nxnode + ' ' + nxserver)

# Chop off beginning of URL to get local filenames

nxclient = nxclient.rsplit('/',1)[1]
nxnode   = nxnode.rsplit('/',1)[1]
nxserver = nxserver.rsplit('/',1)[1]

# Install packages

os.system("sudo dpkg -i " + nxclient + ' ' + nxnode + ' ' + nxserver)
```

---

### Post by Maheriano on 2008-09-23
Marked to try later.

---

### Post by Steve1961 on 2008-10-07
Thought I'd just add a few thoughts as I've just installed the latest nx packages from nomachine.  Firstly, you don't need to create a system user, just install the packages and log in with your standard user name and password.  You only need to create system users if you want nx to authenticate using its own database rather than pam/sshd.  Unfortunately, though, this only works if you haven't disabled password logins in /etc/ssh/sshd_config.

Changing the ssh port is a good idea, but according to nomachine this needs to be changed in three places:

> How should I configure NX 3.x to contact the remote SSHD daemon on a port different from default 22?
If you have configured the SSHD daemon to use a port different from the default 22, you need to configure both server and node accordingly.

How to configure NX Server

You should modify the /usr/NX/etc/server.cfg file by setting the proper value for the following configuration keys:

#
# Specify the TCP port where the NX server SSHD daemon is running.
#
#SSHDPort = "22"

#
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
#SSHDAuthPort = "22"


Please note that you could also specify a remote SSHD daemon to be contacted by setting the following key:

#
# Specify hostname of the server used for NX SSH authentication.
#
#SSHDAuthServer = "127.0.0.1"

How to configure NX Node

You should modify the /usr/NX/etc/node.cfg file by setting the proper value for the following configuration key:

#
# Specify the TCP port where the NX node SSHD daemon is running.
#
#SSHDPort = "22"


Nomachine has also posted some clear instructions on changging default keys:

> Replacing the Default SSH Key-Pair with Keys Generated for Your Server

The initial login between client and server happens through a DSA key-pair. The public part is provided during the installation of the server, while the private part is distributed together with the NX Client. In order to replace the default keys used by clients, you need to generate a new DSA key-pair and distribute the private part to those clients you want to get connected to the server.

Generating a new DSA key-pair

    * Login as root on on the NX server host machine and run:

      /usr/NX/scripts/setup/nxserver --keygen 

Distributing the new SSH private key to the clients

    * Change the ownership and permissions on the authorized_keys file. Depending on which O.S. your NX is running on, you may need to execute:

       chown nx:root /usr/NX/home/nx/.ssh/authorized_keys2
       chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys2
       
       Or:
       
       chown nx:root /usr/NX/home/nx/.ssh/authorized_keys
       chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys

    * Change the ownership and permissions on the following file.

       chown nx:root /usr/NX/home/nx/.ssh/default.id_dsa.pub
       chmod 0644 /usr/NX/home/nx/.ssh/default.id_dsa.pub 

    * Distribute the private key from the newly generated key pair located in the file: /usr/NX/share/keys/default.id_dsa.key
    * Once the new key has been distributed to clients, place it under the subdirectory 'share/keys' of the NX Client installation tree reserved for this purpose.

When the key has been placed in the above location, use the key management facilities provided by the NX Client GUI in the 'General' tab of the session configuration window, click on the 'Key' button and choose Import to import the new key by navigating to the appropriate directory above. Click Save to save your changes.

I followed both of these sets of instructions and everything seems to be working fine.

---

### Post by Maheriano on 2008-10-09
Worked perfect for me, I didn't even have to open any ports. I only have 2 problems though...

1. When I play music on my Ubuntu desktop with Audatious (that the name?) it works fine. But when I remote into it with my Vista laptop and play music using the same program, it overlaps the 2 songs through my desktop speakers. I want to be able to control it as if I was sitting at it, not a different instance of it. So I want to be able to open a program using the desktop and close it using the laptop. Possible?

2. When I play music remotely, it plays through the Ubuntu sound card, is there any way to get it to come through the speakers of the client machine?

---

### Post by Inxsible on 2008-10-13
> **Maheriano said:**
> Worked perfect for me, I didn't even have to open any ports. I only have 2 problems though...

1. When I play music on my Ubuntu desktop with Audatious (that the name?) it works fine. But when I remote into it with my Vista laptop and play music using the same program, it overlaps the 2 songs through my desktop speakers. I want to be able to control it as if I was sitting at it, not a different instance of it. So I want to be able to open a program using the desktop and close it using the laptop. Possible?

2. When I play music remotely, it plays through the Ubuntu sound card, is there any way to get it to come through the speakers of the client machine?
1) NX does not connect to an existing session. What you need is VNC for that.

2) Transmitting sound via NX is also an issue I havent been able to figure out :(

---

### Post by kakemann on 2008-10-13
I did some googling regarding the sound. It works, but you have to use ESD, either as a plugin in the music application of your choice or in general preferences.

---

### Post by anselm on 2008-10-15
Everything worked great, Thanks 8)

Also what I found out is if you connect with your client machine(windows xp for me) and log off on your ubuntu machine your session stays running on the client machine. I can even log on and log off with out having to physically log in to ubuntu.

Firestarter did mess up my samba shares not a big problem will work on that later.

Also for me I didn't need to change my port number, all my computers are connected to a hub then to a router and they all have software firewalls installed. Security web sites say my port 22 doesn't exist.

Well enough rambling, thanks again.

---

### Post by khager on 2008-10-27
Problem with AWN.

If I connect from XP w/ a username that uses the "regular" gnome desktop, it works great.

If I connect from XP w/ a username that runs Avant Window Negotiator (AWN) then I get this error in a dialog box:

   Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

Everything still works, but I don't get the AWN tray at the bottom where my launchers are.

Is there a way to get NX and AWN to work together?

Thanks

---

### Post by smartboyathome on 2008-10-27
> **khager said:**
> Problem with AWN.

If I connect from XP w/ a username that uses the "regular" gnome desktop, it works great.

If I connect from XP w/ a username that runs Avant Window Negotiator (AWN) then I get this error in a dialog box:

   Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

Everything still works, but I don't get the AWN tray at the bottom where my launchers are.

Is there a way to get NX and AWN to work together?

Thanks

I don't think that NX can handle compositing. If it can't, then you can't use AWN with it.

---

### Post by khager on 2008-10-29
Thanks for the reply. I suspected a conflict.

Without derailing this thread, can anyone suggest another remote access tool?
[LIST]
[*]I need encryption & speed like NX.
[*]I don't want to have to have an active session on the console.
[*]I like being able to create multiple sessions like with NX
[*]I want to be able to use AWN
[/LIST]

Thanks

---

### Post by smartboyathome on 2008-10-29
> **khager said:**
> Thanks for the reply. I suspected a conflict.

Without derailing this thread, can anyone suggest another remote access tool?
[LIST]
[*]I need encryption & speed like NX.
[*]I don't want to have to have an active session on the console.
[*]I like being able to create multiple sessions like with NX
[*]I want to be able to use AWN
[/LIST]

Thanks

I don't think one exists that would fit all those. My best suggestion is to switch from AWN to a dock which doesn't require compositing (simdock comes to mind).

---

### Post by 080801jk on 2008-10-30
[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#24066;&#22330;&#31350;&#31455;&#26377;&#22810;&#22823; &#24433;&#21709;&#24066;&#22330;&#23481;&#37327;&#30340;&#20027;&#35201;&#22240;&#32032;&#21462;&#20915;&#20110;&#32769;&#24314;&#31569;&#30340;&#32763;&#26032;&#29575;&#21644;&#26032;&#24314;&#31569;&#30340;&#31459;&#24037;&#37327;&#12290;&#20174;2002&#24180;&#24320;&#22987;&#65292;&#24314;&#35774;&#37096;&#22312;&#22269;&#20869;&#25512;&#34892;&#8220;&#24179;&#25913;&#22369;&#8221;&#33410;&#33021;&#25514;&#26045;&#65292;&#35768;&#22810;&#22823;&#12289;&#20013;&#22411;&#22478;&#24066;&#22343;&#20986;&#21488;&#20102;&#30456;&#24212;&#30340;&#8220;&#24179;&#25913;&#22369;&#8221;&#21046;&#24230;&#65292;&#32769;&#24314;&#31569;&#32763;&#26032;&#33410;&#33021;&#25104;&#20026;&#21508;&#22320;&#25919;&#24220;&#30340;&#19968;&#39033;&#37325;&#35201;&#32771;&#26680;&#25351;&#26631;&#12290;&#19982;&#8220;&#24179;&#25913;&#22369;&#8221;&#30456;&#21305;&#37197;&#65292;[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#20063;&#25104;&#20102;&#32769;&#24314;&#31569;&#33410;&#33021;&#25913;&#36896;&#30340;&#19968;&#39033;&#37325;&#35201;&#20030;&#25514;&#12290;&#21516;&#26102;&#65292;&#30001;&#20110;[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#38500;&#20102;&#33410;&#33021;&#22806;&#65292;&#36824;&#20855;&#26377;&#32654;&#35266;&#35013;&#39280;&#12289;&#38450;&#29190;&#38548;&#38899;&#31561;&#29305;&#28857;&#65292;&#21271;&#20140;&#12289;&#19978;&#28023;&#12289;&#26477;&#24030;&#12289;&#24191;&#24030;&#12289;&#27494;&#27721;&#12289;&#37325;&#24198;&#12289;&#22825;&#27941;&#12289;&#23425;&#27874;&#12289;&#19996;&#33694;&#12289;&#28145;&#22323;&#12289;&#38738;&#23707;&#12289;&#22823;&#36830;&#31561;&#20247;&#22810;&#22478;&#24066;&#37117;&#23558;&#29627;&#29827;&#36148;&#33180;&#20316;&#20026;&#22478;&#24066;&#24418;&#35937;&#24037;&#31243;&#30340;&#19968;&#20010;&#37325;&#35201;&#36873;&#39033;&#12290;&#32780;&#19988;&#22269;&#23478;&#24050;&#20986;&#21488;&#30456;&#20851;&#25919;&#31574;&#65292;&#23545;&#23486;&#39302;&#12289;&#37202;&#24215;&#30340;&#39564;&#25910;&#21644;&#35780;&#32423;&#65292;&#23545;&#20889;&#23383;&#27004;&#12289;&#21830;&#22330;&#12289;&#36141;&#29289;&#20013;&#24515;&#12289;&#38134;&#34892;&#12289;&#26426;&#22330;&#12289;&#36710;&#31449;&#12289;&#23637;&#35272;&#39302;&#31561;&#30340;&#21830;&#29992;&#24314;&#31569;&#35768;&#21487;&#33829;&#19994;&#65292;&#37117;&#25226;&#24314;&#31569;&#33410;&#33021;&#26159;&#21542;&#36798;&#26631;&#20316;&#20026;&#37325;&#35201;&#25351;&#26631;&#36827;&#34892;&#32771;&#26680;&#12290;&#19987;&#23478;&#21628;&#21505;&#65292;&#25919;&#24220;&#21495;&#21484;&#65292;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#26159;&#24314;&#31569;&#33410;&#33021;&#30340;&#39318;&#36873; 2007&#24180;&#20013;&#22269;&#31185;&#25216;&#25104;&#23601;&#23637;&#19978;&#65292;&#20013;&#22269;&#24037;&#31243;&#38498;&#19987;&#23478;&#34920;&#31034;&#65292;&#29627;&#29827;&#36148;&#33180;&#22312;&#27431;&#32654;&#22269;&#23478;&#24314;&#31569;&#33410;&#33021;&#39046;&#22495;&#24050;&#32463;&#38750;&#24120;&#25104;&#29087;&#65292;&#32769;&#24314;&#31569;&#20351;&#29992;&#29627;&#29827;&#36148;&#33180;&#19981;&#29992;&#22823;&#33539;&#22260;&#25913;&#36896;&#65292;&#26032;&#24314;&#31569;&#20351;&#29992;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#32654;&#35266;&#22823;&#26041;&#65292;&#26159;&#24314;&#31569;&#33410;&#33021;&#30340;&#39318;&#36873;&#12290;2007&#24180;5&#26376;15&#26085;&#65292;&#22269;&#23478;&#24314;&#35774;&#37096;&#21644;&#36136;&#26816;&#24635;&#23616;&#32852;&#21512;&#21457;&#24067;&#12298;&#24314;&#31569;&#33410;&#33021;&#24037;&#31243;&#26045;&#24037;&#36136;&#37327;&#39564;&#25910;&#26631;&#20934;&#12299;&#65292;&#33258;2007&#24180;10&#26376;1&#26085;&#36215;&#65292;&#24314;&#31569;&#24037;&#31243;&#33410;&#33021;&#19981;&#31526;&#21512;&#35268;&#33539;&#19981;&#33021;&#36890;&#36807;&#39564;&#25910;&#12290;2007&#24180;6&#26376;1&#26085;&#65292;&#22269;&#21153;&#38498;&#21150;&#20844;&#21381;&#19979;&#36798;&#12298;&#20851;&#20110;&#20005;&#26684;&#25191;&#34892;&#20844;&#20849;&#24314;&#31569;&#31354;&#35843;&#28201;&#24230;&#25511;&#21046;&#26631;&#20934;&#30340;&#36890;&#30693;&#12299;&#65307;6&#26376;12&#26085;&#65292;&#22269;&#21153;&#38498;&#25104;&#31435;&#20197;&#28201;&#23478;&#23453;&#24635;&#29702;&#20026;&#32452;&#38271;&#30340;&#22269;&#23478;&#24212;&#23545;&#27668;&#20505;&#21464;&#21270;&#21450;&#33410;&#33021;&#20943;&#25490;&#24037;&#20316;&#39046;&#23548;&#23567;&#32452;&#65307;7&#26376;30&#26085;&#65292;&#22269;&#21153;&#38498;&#21150;&#20844;&#21381;&#19979;&#36798;&#12298;&#20851;&#20110;&#24314;&#31435;&#25919;&#24220;&#24378;&#21046;&#37319;&#36141;&#33410;&#33021;&#20135;&#21697;&#21046;&#24230;&#30340;&#36890;&#30693;&#12299;&#12290;

---

### Post by khager on 2008-10-30
Thanks for the tip. 

I'll give simdock a try.

---

### Post by jbeck22 on 2009-01-14
my problem is that I get connected and authenticated, but then it closes my connection out.  I get the big !M screen and then it closes out.
See attachment for error.

[IMG]http://atlbecks.com/images/nxclient.jpg[/IMG] 

Any ideas?

---

### Post by tebbens on 2009-01-30
When adding a user, what exactly does adding admin rights give ?
How can I check/change admin rights for a current user ?

Thanks !

---

### Post by AlesZib on 2009-02-13
Hello!

I have followed the how to, however am unable to connect. I'm trying to connect to Ubuntu 8.10 - Intrepid Ibex from Windows XP.

The installation seemed to go smoothly on both, but if I try to connect, I get the following error:
"Authentication failed for user (username)".

I can log in to the server via ssh as an nx user.
Also, I ran
nxserver --usercheck <username>
and the output indicated that everything is ok.

Does anybody have any ideas what could be wrong?

Thanks in advance

---

### Post by Sanix on 2009-02-20
Hi, thanks for your tutorial!
I've got another question. Is it possible to login into an existing session not started by NX? I started a java program locally. Now I want to connect remotely and access the GUI. It's not possible, because I starts a new session. I don't want to start the application again, since it could cause troubles.

---

### Post by tjantunen on 2009-04-17
Hi,

I have a problem with user rights. When I am using Ubuntu through NXClient I do not have sudo rights. I can not "unlock items" in GUI. I am logged in as a root. If I log in locally with same username, I have all access rights available.

Edit:I have exactly the same problem as in here:
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/221363](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/221363)

There seems to be some kind of solution also. But I have not yet tested it.

---

### Post by Halvliter on 2009-04-20
I keep getting "Connection timeout" when I try to connect my Ubuntu PC from my Vista laptop, and I followed this guide.

NX> 203 NXSSH running with pid: 704
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options

---

### Post by Halvliter on 2009-04-23
I removed all packages using sudo apt-get remove (combining it with purge) and deleted the /usr/NX folder and install a fresh install. Did the same on my laptop, uninstalled and deleted the .nx and .ssh folders.

It's working again :)

---

### Post by Loan_Refi on 2009-05-23
I'm trying to make the NX Client Connection work but I keep getting the error;

Host not found

I have read the entire thread, made changes according to the instructions with no success.

On host;
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

NX Server
Using Port 3022 instead of 22
I have made changes to node & server.cfg to reflect 3022 port
my node.cfg is set
# Specify the TCP port where the NX node SSHD daemon is running.
#
SSHDPort = "3022"
#SSHDPort = "54322"

# Specify hostname for the NX node.
#
#NodeName = "localhost.localdomain"

my server.cfg is set
# Specify hostname for the NX server.
#
#ServerName = "localhost.localdomain"
# Specify the TCP port where the NX server SSHD daemon is running.
#
SSHDPort = "3022"
# Specify hostname of the server used for NX SSH authentication.
#
#SSHDAuthServer = "127.0.0.1"
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
SSHDAuthPort = "3022"

I'm able to make a connection to my NX Server

$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	300m

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Here is the errors I get from NX Client;

NX> 203 NXSSH running with pid: 8194
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XX.XX.XX.XX on port: 3022
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0-22 - LFE
NX> 105 Hello NXCLIENT - Version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: ME
NX> 102 Password: *********
NX> 103 Welcome to: B1 user: ME
NX> 105 Listsession --user="ME" --status="suspended\054running" --geometry="1680x1050x24+render+fullscreen" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: ME
NX> 105 Start session with: --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --samba="1" --media="1" --mediahelper="esd" --session="TEST1" --type="unix-gnome" --geometry="1680x1030" --fullscreen="1" --client="linux" --keyboard="pc105\057us" --screeninfo="1680x1050x24+render+fullscreen" 
NXSERVER - Version 3.3.0-22 - LFE
Fri May 22 22:37:23 2009 running as user: 'nx' (uid: 112, pid: 18552) on 'B1'
Info: user login is ME (NXShell)
Info: user password is '******' (NXShell)
Info: using 'sshd authentication' (NXShell)
Info: selected user 'ME' is authenticated (NXNodeExec)
Info: password for selected user is in 'text' mode (NXNodeExec)
Info: preferred auth method is '' (NXNodeExec)
Info: selected NX Node with host name 'localhost', port '3022' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l ME localhost -p 3022 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 18565 (NXNodeExec)
Info: received data in err channel from NX Node: 'nxssh: localhost: Name or service not known
' (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 280 Exiting on signal: 15

I replaced my actual username with "ME" 
when I try to connect I use [www.mydomain.com](www.mydomain.com) or my local IP 192.168.1.XX

Does anyone know what I need modify to make this work? Based on the error I can see that the localhost: Name or service not know is causing the problem but I don't know what setting to modify.

---

### Post by Loan_Refi on 2009-05-23
I followed all the steps again from beginning and I encounter 1 error when I enter;

ssh localhost

ssh: localhost: Name or service not known

I'm running this command remotely on the machine I want to control via SSH.

I'm guessing this is my main problem.

any help is appreaciated

---

### Post by Loan_Refi on 2009-05-28
I solved the error.  The problem was caused by not having enough permission rights to file /etc/nsswitch.conf

644 is the proper permission for that file.  

sudo chmod 644 nsswitch.conf

I found the solution at: [http://ubuntuforums.org/showthread.php?t=766628](http://ubuntuforums.org/showthread.php?t=766628)

I was not able to ping localhost but after the correction everything works as it should!!

---

### Post by jngrim on 2009-06-02
Can someone tell me how I can remotely login to my ubuntu server at home and keep programs that I started running after I have closed the NXclient? Is is just suspending the NXclient and not terminating?  I am new to running a server and using a client to access the server to control it...thanks alot.

---

### Post by Loan_Refi on 2009-06-02
jngrim

It sound to me like you already have the server up and running and you probably already installed NX Server, Node & client on the server. You probably already have the right ports forwarded on your firewall to your server so to answer your question;

To leave your programs running chose Disconnect instead of Terminate.

Is this all you're looking for or do you need help setting up your firewall, ports etc.?

---

### Post by blacksunseven on 2009-08-08
I've been using NXclient to remotely control Ubuntu for a while now and I love it. It works great under WinXP and OS X without any problems. I recently needed to reformat my desktop and decided to try Windows 7 instead of going with WinXP. I didn't think this would create any complications regarding NX but apparently I was **wrong**.

My problem is simple but absolutely critical to continuing to use NX from my desktop: **Win7 randomly sends a home key press to my Ubuntu machine.** I don't know what causes it but it can happen anywhere in Ubuntu and it's obviously impossible to do something in Terminal when you're *constantly put back at the beginning of the line* :(

I tried NX on some other computers to check if the issue was with my server but _they all functioned flawlessly_. Disabling the home key seems like a solution but I do use it quite a bit (on my schedule) and hoped others here could provide an alternate solution.

Thanks for any replies!

---

### Post by Loan_Refi on 2009-08-09
Well for starters, you have isolated the problem to Windows 7 by connecting to your server from other different machines and not getting the same problem.

Have you tried uninstalling, installing NXClient on Windows 7?

It looks to me the latest NXClient Version is: Release:	3.3.0-6. I did not see Windows 7 listed as supported at nomachine.com.

I'm afraid I can't provide much help to you.  I haven't tried Windows 7.  I'm in the process of moving away from MS 03 Server, Exchange, XP, Vista. I prefer using VNC over NXClient.

You probably use the entire desktop features when you use NX Client to connect to your server but if you don't give "Krusader" a try.  This application allows you to access you entire  machine via sftp. You can open your documents, files etc. and print them locally.

to install krusader;
sudo apt-get install krusader

---

### Post by blacksunseven on 2009-08-09
This is a fresh install of the latest version (3.3.0-6) from nomachine's site and you're correct about no mention there of support for Windows 7. I assumed that if they supported Vista, it wouldn't be much different for Win7. Leave it to M$ to always find a way to break pre-existing software...

Anyways, I attempted to gather some more information and found this out: **if I just let the Terminal sit and the cursor blink, the home key press never happens**. This leads me to believe that incorrect data is being transmitted to the Ubuntu machine. I then **thought to see if it was isolated to a particular repeated key press, but the sample of keyboard keys I tried all demonstrated the home key issue in the same manner**.

As for switching from NX, no thank you. I used to use VNC but it's just so awful and slow compared to NX and I've never had any luck with encrypting VNC connections. I might still check out krusader to satisfy personal curiosity though. Thanks for the reply!

---

### Post by Maheriano on 2009-08-10
> **jngrim said:**
> Can someone tell me how I can remotely login to my ubuntu server at home and keep programs that I started running after I have closed the NXclient? Is is just suspending the NXclient and not terminating?  I am new to running a server and using a client to access the server to control it...thanks alot.

Ya, just click the X on the NXClient window to close it, it'll keep your session going in the background and allow you to log into it again later.

But if you're trying to close your session on a remote computer and continue it on the server then that's not possible. NXClient doesn't do sessions like VNC.

---

### Post by Loan_Refi on 2009-08-10
Maheriano,

Sorry but, can you explain a little bit more what you just said?

This is why I ask.

I use NXClient to connect to Remote NXServer Miles away. I can disconnect my session instead of terminate and leave it running in the background.  Hours or days later I can login into the same session (I mean if I was working on a Spreadsheet, email or any program) and continue working.

I'm just wondering what other way are you using NXClient? Am I miss understanding you?

Thanks!

---

### Post by Maheriano on 2009-08-10
> **Loan_Refi said:**
> Maheriano,

Sorry but, can you explain a little bit more what you just said?

This is why I ask.

I use NXClient to connect to Remote NXServer Miles away. I can disconnect my session instead of terminate and leave it running in the background.  Hours or days later I can login into the same session (I mean if I was working on a Spreadsheet, email or any program) and continue working.

I'm just wondering what other way are you using NXClient? Am I miss understanding you?

Thanks!

No, that's how I use it too. I'm just saying you can't open a spreadsheet in your session and then go to your server machine and work on the same open spreadsheet. It's 2 different sessions.

---

