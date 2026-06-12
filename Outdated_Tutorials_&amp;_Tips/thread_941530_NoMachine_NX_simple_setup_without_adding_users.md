---
title: "NoMachine NX: simple setup without adding users"
date: 2008-10-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Steve1961 on 2008-10-08
After struggling with VNC for some years I finally tried out Nomachine's NX server instead.  Overall it's much faster than VNC and very simple to set up. However, searching this forum and google turned up lots of conflicting instructions about how to configure things.  So in the end I just waded through Nomachine's online documentation and help system.  What I wanted was for the connection to a remote machine to be as secure as possible, and more usable than VNC through an ssh tunnel, without having to jump through too many configuration hoops.  I'm posting what I did here in case someone else wants to give NX a try.  I know there are other how tos on the forum, but most seem to include a step about adding users.  This isn't strictly necessary, and so I haven't included it.

Just for information, both the server and client software were installed on Hardy, and I've used the latest version of the Nomachine packages and not the FreeNX packages.  I believe FreeNX is very similar, but having never tried it I don't know if these instructions will work with that as well.  So here goes:  

1. Make sure openssh-server is installed on the server machine/s and that you can ssh into into those machines.  See this [link]("https://help.ubuntu.com/community/AdvancedOpenSSH").  Just one caveat.  You must ensure that password based authentication is enabled in the /etc/ssh/sshd_config file of the server machine.  Initially you should also use the standard port 22 for ssh as well.

2. Download these files from [here]("http://www.nomachine.com/download-package.php?Prod_Id=6") 

nxclient_3.2.0-14_i386.deb
nxnode_3.2.0-13_i386.deb
nxserver_3.2.0-16_i386.deb

3. Put the files in the home directory of the machine you want to use as the server, open a terminal, and install them:

```
sudo dpkg -i *.deb
```

note: make sure that these are the only .deb packages in your home directory when you do this.

4. Repeat the above on the client machine - on the client you only need the nxclient package and not the nxserver and nxnode packages

5. At this stage it's worth testing that everything works 'as is'.  You may have to do a 'killall gnome-panel' before the NX entry appears in the menu, but once it has you'll find it under applications/internet.  Open the NX connection wizard and follow along.  You should be able to log in as a normal user with the user name and password that you normally log into the system with.  If all goes well a session should open on your desktop displaying the server machine's desktop.

6. If all went well you will now want to change the default ssh keys that the NX server uses.  When you first install the nx packages they ship with default keys that are the same for everyone.  Potentially this means that anyone with the nxclient package installed could authenticate against your server.  Not good!  However, changing these keys is simple.  Just log into the server (or ssh to the server) and do the following:

```
sudo su
/usr/NX/scripts/setup/nxserver --keygen
chown nx:root /usr/NX/home/nx/.ssh/authorized_keys2
chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys2
chown nx:root /usr/NX/home/nx/.ssh/default.id_dsa.pub
chmod 0644 /usr/NX/home/nx/.ssh/default.id_dsa.pub
```

Then copy the default.id_dsa.pub file to the client.  I did this using scp from the client machine, e.g.
```

scp user@server:/usr/NX/share/keys/default.id_dsa.key .
```

But you could just as easily copy it to a usb flash drive and transfer it to the client.  Once you've saved it to the client machine's home directory you should rename the key from default (I use my user name) and copy it to the /usr/NX/share/keys/ directory:

```
sudo cp default.id_dsa.key /usr/NX/share/keys/user.id_dsa.key
```

Now test that you can connect to the nx user account on the server with this key:
```

ssh -i /usr/NX/share/keys/user.id_dsa.key nx@server
```

You shouldn't be prompted for a password.  If you can connect as the nx user just type quit to exit.  Then launch the nx client from the menu, hit configure, and then the key button on the general tab.  Delete the exiting key and press the import button.  Import the key that you've just saved in the /usr/NX/share/keys directory.  Save everything and then try connecting with the client.

Optional steps

7. If all went well you can now change the default ssh port to a non-standard one (say 2222 for this example).  Go back to the server machine (or shh to it) and edit three files to make the changes.

First edit the /usr/NX/etc/server.cfg file:
```

sudo gedit /usr/NX/etc/server.cfg
```

Look for these entries:

#SSHDPort = "22"
#SSHDAuthPort = "22"

Uncomment and change 22 to 2222.  Save and close.

Then edit /usr/NX/etc/node.cfg:
```

sudo gedit /usr/NX/etc/node.cfg
```

Look for this entry:

#SSHDPort = "22"

And again uncomment and change the port number.  Save and close.

Finally edit /etc/ssh/sshd_config

```
sudo gedit /etc/ssh/sshd_config
```

Look for this entry:

Port 22

And again change the port, save and close.

Finally, restart ssh:
```

sudo /etc/init.d/ssh restart
```

On the client machine you should then launch the nx client, press the configure button, and enter the new port in the general tab.

That's it.  You should now be able to connect to the nxserver on a non-standard port with a custom ssh key.

8. For added security you might also want to go back to the server machine and edit the /usr/NX/etc/server.cfg file again.  Find this line:

#EnableUnencryptedSession = "1"

Uncomment it and change the "1" to a "0"

This will force nx to use ssl encryption at all times.

That's basically it.  The only problem I have with nx so far is not being able to disable password based authentication in my sshd_config.  There is a work around which involves adding system users to the nx server and then using the nx database rather than ssh to authenticate.  However, I haven't tried this, so I'm not able to comment on how well it works,  What I've done instead is limit the number of users who can ssh into the server machine (nx must be a listed user), and restricted access in my firewall to only allow certain machines through.

Hope this helps someone.

---

### Post by recif on 2008-12-02
Hi,
 Thanks for posting directions on setting up NoMachine NX. Installation on a system running Ubuntu 8.1 seemed to proceed fine:
/usr/bin/NX/nxserver --status gives 

NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.

I imported the default.id_dsa.key into the NX client on the remote machine. When I try to log in, I get:
Public Key authentication failed

and in details:

NX> 502 ERROR: Public key authentication failed
NX> 502 ERROR: NX server was unable to login as user: recif
NX> 502 ERROR: Please check that the account is enabled to login,
NX> 502 ERROR: the user's home directory, the directory ~/.ssh
NX> 502 ERROR: and the file ~/.ssh/authorized_keys2 have correct
NX> 502 ERROR: permissions setting according to the StrictModes
NX> 502 ERROR: of your SSHD configuration.
NX> 999 Bye.
NX> 280 Exiting on signal: 15

I checked that group and other do not have write access the directory ~/.ssh and the file ~/.ssh/authorized_keys2 for recif on the server running NX.


Any help to fix this is appreciated.
Recif

---

### Post by Steve1961 on 2008-12-05
Sorry for the delay in replying.  I'm working away from home all week at the moment so I'm only back at weekends.

For some reason the ssh keys clearly don't match.  Can you log in to the server as the nx user using the key you generated:

ssh -i /usr/NX/share/keys/user.id_dsa.key nx@server

Obviously change the name of your key in the above command to whatever you renamed it to, and make sure it's location is correct.

If that fails try generating a new set of keys and try again.  I've now followed this method on 5 different machines and had no problems, although I'm using Hardy not 8.10

---

### Post by juanoleso on 2008-12-05
I'll probably be giving this a try!  Thank you!

---

### Post by sandbox4us on 2008-12-06
Hi,

The question is how do you run a NX Client Session so that it is the only X11 session on the server?  I'm not sure if I phrased this correctly so bear with me, because I am a Linux newbie.

I've tried to use Nomachine NX server as a solution to running a headless Ubuntu box (Intrepid).  I've gotten the setup to work, but I havent bothered yet to change the keys or ports.  The bottom line is that it is a very nice solution.  The performance is amazing for an RDP application, much faster than VNC... so long as you run it from the client and "spawn" a new X11 session (sorry if my terminology is incorrect here) at the server.  From the General tab of the NX client configuration screen you select Unix + GNOME (or KDE) in the Desktop configuration box.  The alternative is to run it as a Shadow session, but then the performance is about the same as VNC.

The downside of starting a new GNOME session is that it eats up memory in your server box, because you essentially have 2 GNOME sessions operating on your machine at the same time.  I also happen to have VNC server installed on the box, and I can VNC into the "original session" while controlling a 2nd NX Session.  When you pull up system monitor, you have 2 copies of a host of processes running... I guess because you have 2 simultaneous GNOME sessions running at the same time.  There are other downsides as well. I havent figured out how you run firefox in 2 different sessions.  You get the error "Firefox is already running, but is not responding.  To open a new window, you must first close the existing Firefox process...".  The final downside is that you cant shutdown your server from the 2nd session.  If you issue a shutdown command, it shuts down the session, but does not shut down the server.  On the other hand, if you shutdown from the original VNC session, it seems to shutdown the machine.

So, I hope this explains my problem but does anyone know if it is possible to run NX Client as the first (or primary, if there is such a thing) X11 session?

---

### Post by De_JA_Vu on 2009-01-17
> **sandbox4us said:**
> 

So, I hope this explains my problem but does anyone know if it is possible to run NX Client as the first (or primary, if there is such a thing) X11 session?
I am looking for the same solution.
any one "expert" want to have look into this please?

---

### Post by Steve1961 on 2009-01-17
If anyone does know a way to do this please let us know.  However, as far as I'm aware I don't think it is possible.

---

### Post by AlesZib on 2009-02-12
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

### Post by Steve1961 on 2009-02-14
> **AlesZib said:**
> Hello!

I have followed the how to, however am unable to connect. I'm trying to connect to Ubuntu 8.10 - Intrepid Ibex from Windows XP.

The installation seemed to go smoothly on both, but if I try to connect, I get the following error:
"Authentication failed for user (username)".

I can log in to the server via ssh as an nx user.
Also, I ran 
nxserver --usercheck <username>
and the output indicated that everything is ok.

Does anybody have any ideas what could be wrong?

Thanks in advance

If you can log into the nx server as "nx" using the imported key, you should be able to connect via the gui.  Reimport the nx key into the gui and try again.  That said, this was tested using hardy not intrepid so I'm not aware of any gotchas that intrepid may have introduced.

---

### Post by AlesZib on 2009-02-15
Thanks for the reply. I would just like to add that if I use a wrong key-file, I get a different response, namely that NX service is not available.

I have a feeling that users could be set wrongly. Can I somehow that that from the server or using SSH?

Thanks for the reply,
Ales

---

### Post by Steve1961 on 2009-02-18
> **AlesZib said:**
> Thanks for the reply. I would just like to add that if I use a wrong key-file, I get a different response, namely that NX service is not available.

I have a feeling that users could be set wrongly. Can I somehow that that from the server or using SSH?

Thanks for the reply,
Ales

See if you can log in with ssh as nx.

ssh -i /usr/NX/share/keys/<whatever you named the key> nx@<ip address of your server>

---

### Post by sir_blargh on 2009-02-18
> **recif said:**
> Hi,
 Thanks for posting directions on setting up NoMachine NX. Installation on a system running Ubuntu 8.1 seemed to proceed fine:
/usr/bin/NX/nxserver --status gives 

NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.

I imported the default.id_dsa.key into the NX client on the remote machine. When I try to log in, I get:
Public Key authentication failed

and in details:

NX> 502 ERROR: Public key authentication failed
NX> 502 ERROR: NX server was unable to login as user: recif
NX> 502 ERROR: Please check that the account is enabled to login,
NX> 502 ERROR: the user's home directory, the directory ~/.ssh
NX> 502 ERROR: and the file ~/.ssh/authorized_keys2 have correct
NX> 502 ERROR: permissions setting according to the StrictModes
NX> 502 ERROR: of your SSHD configuration.
NX> 999 Bye.
NX> 280 Exiting on signal: 15

I checked that group and other do not have write access the directory ~/.ssh and the file ~/.ssh/authorized_keys2 for recif on the server running NX.


Any help to fix this is appreciated.
Recif

I found that in my setup, which admittedly was a bit different, I needed to copy the .ssh/authorized_keys2 file to .ssh/authorized_keys, to match what was in my /etc/ssh/sshd_config file.  (Make sure that sshd_config has using an Authorized Keys file enabled!)

---

### Post by jk-menifee on 2009-02-18
Hi,

Great howto, definitely lacking in the nomachine documentation. Much appreciated.

I would like to mention that I use port knocking to open my ssh port. This means I drop all ssh packets by default, and a successful port knock allows access to port 22 from where I am only. It turns out that when you try to connect to nxserver, the interim authorization step (from user "nx" to the username you ultimately will be using) requires ssh access via localhost (i.e. the loopback address of 127.0.0.1). So I needed to add an entry in iptables to allow ssh connections from localhost. Hopefully others (one or two at the most perhaps??) can learn from this experience.

John K.

---

### Post by AlesZib on 2009-02-19
> **Steve1961 said:**
> See if you can log in with ssh as nx.

ssh -i /usr/NX/share/keys/<whatever you named the key> nx@<ip address of your server>

Yes, I can do that. I'm using Putty (as I'm logging form windows), but I have no problems here. I get this output in the terminal:
Authenticating with public key "imported-openssh-key"
HELLO NXSERVER - Version 3.3.0-14 - LFE
NX> 105 

By the way. I tried then in this terminal window the "login" command. Then I was asked for the user and password. When I entered it, the terminal window disappeared. 

Any ideas what does this mean?

---

### Post by sp00n on 2009-02-25
AlesZib: I am experiencing the exact same issue. Have you made any progress? I can connect via ssh as the nx user using key authentication with no password. however, the nxclient fails with the message "Authentication failed for user xxxx".

how can I determine if the user attempting to log in is authorised for nx? what logs do I need to check to determine what is going on?

---

### Post by sp00n on 2009-02-25
syslog of the server shows the following after a failed connection attempt:

Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: ERROR: Failed authentication. NXSsh exit status is:255 'NXNssUserManager::auth'
Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: Failed SSHd authentication for user 'uuuu', to '127.0.0.1', port '22': ' ssh_exchange_identification: Connection closed by remote host^M\n' 'NXNssUserManager::auth'
Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: ERROR: Error while trying to authenticate user:uuuu. NXNssUserManager::auth returned 255 'NXShell::handler_login'
Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: ERROR: failed 'sshd authentication' for user 'uuuu' from 'nn.nnn.nnn.nnn'. NXShell::handler_login NXShell 373

---

### Post by sp00n on 2009-02-25
running sudo /usr/NX/bin/nxserver --usercheck uuuu gives the following:

```
NX> 900 Verifying public key authentication for NX user: uuuu.
NXSERVER - Version 3.3.0-15 - LFE
Wed Feb 25 23:15:55 2009 running as user: 'root' (uid: 0, pid: 8613) on 'xxxx.dddd.local'
Info: selected user 'uuuu' is not authenticated no password available (NXNodeExec)
Info: preferred auth method is 'publickey' (NXNodeExec)
Info: selected NX Node with host name '127.0.0.1', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l uuuu 127.0.0.1 -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 8617 (NXNodeExec)
Info: received data in err channel from NX Node: 'ssh_exchange_identification: Connection closed by remote host
' (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 702FA254. To get detailed information about
NX> 595 ERROR: the error search for the string 702FA254 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
uuuu@xxxx:~$ sudo /usr/NX/bin/nxserver --userlist
NX> 149 Listing NX users:

Username
--------------------------------
uuuu

NX> 999 Bye.
```

This results in the following in syslog:

```


Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) Error: no 'CONNECTED' message from NX Node
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) ssh_exchange_identification: Connection closed by remote host^M
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) NXNodeExec::exec('ping', '', 127.0.0.1, 22, 'uuuu', 'publickey') called at handlers/nxserver.pl line 7419
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) NXShell::handler_user_checklogin('uuuu') called at NXShell.pm line 373
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) NXShell::handle_command('checklogin', 'uuuu') called at handlers/nxserver.pl line 7506
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) NXShell::handler_user_check('username', 'uuuu') called at NXShell.pm line 373
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) NXShell::handle_command('checkuser', 'username', 'uuuu') called at nxserver.pl line 5206
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) main::parse_args called at nxserver.pl line 4429
Feb 25 23:29:37 xxxx NXSERVER-3.3.0-15[11216]: ERROR: (exception id AB97C4E6) eval {...} called at nxserver.pl line 4426
```

---

### Post by AlesZib on 2009-02-26
> **sp00n said:**
> syslog of the server shows the following after a failed connection attempt:

Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: ERROR: Failed authentication. NXSsh exit status is:255 'NXNssUserManager::auth'
Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: Failed SSHd authentication for user 'uuuu', to '127.0.0.1', port '22': ' ssh_exchange_identification: Connection closed by remote host^M\n' 'NXNssUserManager::auth'
Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: ERROR: Error while trying to authenticate user:uuuu. NXNssUserManager::auth returned 255 'NXShell::handler_login'
Feb 25 23:00:44 xxxx NXSERVER-3.3.0-15[5505]: ERROR: failed 'sshd authentication' for user 'uuuu' from 'nn.nnn.nnn.nnn'. NXShell::handler_login NXShell 373

Btw, where can I find this log.

However, it seams that our probles are not the same, as for me, the 
sudo /usr/NX/bin/nxserver --usercheck xxxx

returns no errors:
NX> 900 Verifying public key authentication for NX user: xxxx.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.

---

### Post by sp00n on 2009-02-26
Morning AlesZib.

You can view the last few entries of the syslog  by executing ```
tail /var/syslog.0
```

This log gets written to very frequently, so run the command above immediately after the usercheck.

---

### Post by sp00n on 2009-02-26
I have just tried the following:

completely removed nx packages```
sudo apt-get remove nx-client nx-node nx-server --purge
```

archived existing /usr/NX and /etc/nx* directories and delete originals ```
cd /usr/
sudo tar -czf NX.tar.gz /usr/NX/
sudo rm -rf /usr/NX
cd /etc/
sudo tar -czf nxagent.tar.gz nxagent/
sudo tar -czf nxserver.tar.gz nxserver/
sudo rm -rf nxagent/
sudo rm -rf nxserver/
```

removed any nx related users or groups.

archived existing sshd config, remove --purge sshd.

re-installed openssh-server via synaptic.

tested sshd functionality by ssh-ing in from another machine (you may get a warning about the key not matching the cached key on the client)

changed to the directory where my downloaded most recent nx .debs are

sudo dpkg -i nxclient* - no messages.

sudo dpkg -i nxnode* - no warnings / errors.

```
uuuu@xxxx:~/Desktop$ sudo dpkg -i nxserver_3.3.0-15_i386.deb 
Selecting previously deselected package nxserver.
(Reading database ... 237108 files and directories currently installed.)
Unpacking nxserver (from nxserver_3.3.0-15_i386.deb) ...
Setting up nxserver (3.3.0-15) ...
NX> 700 Installing: server at: Thu Feb 26 10:00:55 2009.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 Creating configuration file: /usr/NX/etc/server.cfg.
NX> 723 Cannot start NX statistics:
NX> 709 NX statistics are disabled for this server.
NX> 700 WARNING: Error when trying to connect to NX server, error is:
.X> 700 WARNING: ssh_exchange_identification: Connection closed by remote host
NX> 700 WARNING: nxsetup cannot validate the sanity of the current installation:
NX> 700 WARNING: the current system or NX configuration could be broken.
NX> 700 WARNING: If difficulties arise (for example sessions cannot be started),
NX> 700 WARNING: it is advisable that you try to uninstall the NX server and the
NX> 700 WARNING: NX client packages then install them again.
NX> 700 WARNING: Search also the NoMachine Knowledge Base at the URL below:
NX> 700 WARNING: http://www.nomachine.com/kb
NX> 700 WARNING: for common errors encountered when performing a software update
NX> 700 WARNING: and the related hints on how to solve them..
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices
```

I then followed the instructions at [http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126) to create some private keys

I also had to rename the old known_hosts file on the nx client machine (C:\Users\uuuu\.ssh\known_clients , it is a Vista machine) so that the nx client does not complain about the key having changed.

And.. after all that....

Still the same! grrr.

syslog now shows:

```
Feb 26 10:34:01 xxxx NXSERVER-3.3.0-15[17877]: ERROR: Failed authentication. NXSsh exit status is:255 'NXNssUserManager::auth'
Feb 26 10:34:01 xxxx NXSERVER-3.3.0-15[17877]: Failed SSHd authentication for user 'uuuu', to '127.0.0.1', port '22': ' ssh_exchange_identification: Connection closed by remote host^M\n' 'NXNssUserManager::auth'
Feb 26 10:34:01 xxxx NXSERVER-3.3.0-15[17877]: ERROR: Error while trying to authenticate user:uuuu. NXNssUserManager::auth returned 255 'NXShell::handler_login'
Feb 26 10:34:01 xxxx NXSERVER-3.3.0-15[17877]: ERROR: failed 'sshd authentication' for user 'uuuu' from '10.101.101.1'. NXShell::handler_login NXShell 373
```

executing nxserver --usercheck uuuu now gives:

```
uuuu@xxxx:/usr/NX/etc/keys$ sudo /usr/NX/bin/nxserver --usercheck uuuu
^[[ANX> 900 Verifying public key authentication for NX user: uuuu.
^[[ANXSERVER - Version 3.3.0-15 - LFE
Thu Feb 26 10:37:08 2009 running as user: 'root' (uid: 0, pid: 18495) on 'xxxx.dddd.local'
Info: selected user 'uuuu' is not authenticated no password available (NXNodeExec)
Info: preferred auth method is 'publickey' (NXNodeExec)
Info: selected NX Node with host name '127.0.0.1', port '22' (NXNodeExec)
Info: selected publickey method to login NX Node (NXNodeExec)
Info: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l uuuu 127.0.0.1 -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec)
Info: nxssh child pid is: 18499 (NXNodeExec)
Info: received data in err channel from NX Node: 'ssh_exchange_identification: Connection closed by remote host
' (NXNodeExec)
Info: NX Node out channel was closed (NXNodeExec)
Info: NX Node err channel was closed (NXNodeExec)
Info: closing nxssh's in, out, err FDs (flagfinished is: 0) (NXNodeExec)
Error: no 'CONNECTED' message from NX Node (NXNodeExec)
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: 1E7F32BE. To get detailed information about
NX> 595 ERROR: the error search for the string 1E7F32BE in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
```

Syslog shows:

```
uuuu@xxxx:/usr/NX/etc/keys$ sudo tail /var/log/syslog
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: nxssh process exited with '255' 'NXNodeExec::exec'
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) Error: no 'CONNECTED' message from NX Node
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) ssh_exchange_identification: Connection closed by remote host^M
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) NXNodeExec::exec('ping', '', 127.0.0.1, 22, 'uuuu', 'publickey') called at handlers/nxserver.pl line 7419
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) NXShell::handler_user_checklogin('uuuu') called at NXShell.pm line 373
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) NXShell::handle_command('checklogin', 'uuuu') called at handlers/nxserver.pl line 7506
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) NXShell::handler_user_check('username', 'uuuu') called at NXShell.pm line 373
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) NXShell::handle_command('checkuser', 'username', 'uuuu') called at nxserver.pl line 5206
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) main::parse_args called at nxserver.pl line 4429
Feb 26 10:37:08 xxxx NXSERVER-3.3.0-15[18495]: ERROR: (exception id 1E7F32BE) eval {...} called at nxserver.pl line 4426

```


Does anybody have any suggestions? I'm tearing my hair out.

---

### Post by AlesZib on 2009-02-27
> **sp00n said:**
> Morning AlesZib.

You can view the last few entries of the syslog  by executing ```
tail /var/syslog.0
```

This log gets written to very frequently, so run the command above immediately after the usercheck.

Hi sp00n. I do not have this file. I get:
```
tail /var/syslog.0
tail: cannot open `/var/syslog.0' for reading: No such file or directory
```

Any ideas?

---

### Post by sp00n on 2009-02-27
Try without the .0 on the end.

---

### Post by AlesZib on 2009-02-28
sp00n, now I found the syslog.0 in /var/log/.

However, even after runing usercheck (perhaps because it does not  return any errors for me) or a failed atempt it does not contain anyting NX related.

---

### Post by alenis on 2009-03-16
AlesZib and SpOOn, did you make any progress? I have exactly the same problems: I can login as NX user but when I try to access through the GUI I get authorization failed. Even the syslog.0 looks the same...Please let me know

---

### Post by AlesZib on 2009-03-17
Unofortunatelly no. Still hoping that some expert will post some solution here. I'm relatively new to linux and have no idea what else I could do.

---

### Post by alenis on 2009-03-18
reading these posts:

[http://lists.kde.org/?l=freenx-knx&m=121754212328392&w=2](http://lists.kde.org/?l=freenx-knx&m=121754212328392&w=2)

and 

[http://ubuntuforums.org/archive/index.php/t-449382.html](http://ubuntuforums.org/archive/index.php/t-449382.html)

I got the impression that the problem may be related to the sshd_config file on the server. They suggest to put a line relating to the .ssh/authorized_keys2 file.
However, I cannot play right now with the sshd_config file because I am far away from my server. I'll keep you informed...

---

### Post by AlesZib on 2009-03-18
I think I tried this and it did not work. The difference between at least my problem and their is that I can log in as a nx user (that is, as user names "nx") and aslo --usercheck reports that everything is ok, but I ctill can not connect.

---

### Post by sp00n on 2009-03-20
Hi alenis / AlesZib,


No, not fixed it, I have given up. could not get freenx to work either, same problem.

I am experiencing the same issue as AlesZib, the ssh authentication is fine for user nx, I can ssh in as that user no problem. the issue seems to be the authentication of the user that nx does after the ssh session has been initiated.

---

### Post by gotmonkey on 2009-03-20
Initially, I found out about freenx from ubuntuguide and followed the install from the freenx homepage. Everything is working for remoting into the machine remotely. The weird thing that I am experiencing is that I have a monitor, keyboard, mouse connected to that system. I have the machine to autologin my account. When the system boots, I have display through the bios and the Ubuntu splash screen, but after that, the screen goes blank. I can remote in (NoMachine) from another system, I just find it weird that machine went headless on me. 

Anyone know why this happening? It is not a huge issue. I plan to use the system headless, but while I am still setting up my fileserver and shares, it would be nice to do it at the local console.

---

### Post by jelevin on 2009-06-07
This thread has been very helpful to me.  One additional point that I discovered after a long afternoon of frustration is as follows.

In attempting to secure ssh and NX access I modified my working server sshd_config and hosts files as follows:

```

#In sshd_config
Port 55555
Protocol 2
LoginGraceTime 2m
MaxAuthTries 3

PermitRootLogin no
StrictModes yes
PermitEmptyPasswords no

# /etc/hosts.allow
sshd: 192.168.0.0/255.255.255.0
sshd: a trusted external ip address

# /etc/hosts.deny
sshd: ALL

```

This resulted in a an inability to connect and a variety of unhelpful error messages.  I was able to get things working again after adding:

```
# /etc/hosts.allow
sshd: LOCAL

```

I *think* I now have moved ssh to a different port, and restricted access to selected IP addresses.

Maybe adding sshd: LOCAL will help someone else.

---

### Post by badious on 2010-06-23
Thats exactly what happened to me, for some reason it was working fine and not using lo and then all of sudden it switched to using the loopback and I had to add 127.0.0.1 to my hosts.allow for sshd in order for it to start functioning again.

---

### Post by lespedeza on 2010-09-06
jelevin, thanks a bunch for the hosts.allow suggestion.  It solved my problem.  The weird thing is I already had a line in hosts.allow supposedly allowing everything for specific IPs.

I'm no expert, but for some reason, sshd is not included when you put 
```

ALL: xxx.xxx.xxx.xxx

```
I had to specifically put, as you mentioned,
```

sshd: LOCAL

```
Thanks again for the help,

lespedeza

> **jelevin said:**
> 
This resulted in a an inability to connect and a variety of unhelpful error messages.  I was able to get things working again after adding:

```
# /etc/hosts.allow
sshd: LOCAL

```

I *think* I now have moved ssh to a different port, and restricted access to selected IP addresses.

Maybe adding sshd: LOCAL will help someone else.

---

