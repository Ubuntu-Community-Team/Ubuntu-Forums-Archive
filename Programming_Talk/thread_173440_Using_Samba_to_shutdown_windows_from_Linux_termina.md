---
title: "Using Samba to shutdown windows from Linux terminal"
date: 2006-05-10
forum: Programming Talk
---

### Post by krypto_wizard on 2006-05-10
Hi,

I want to shutdown some remote windows PCs using a Linux Box in a small home network. 

Has anybody ideas how to do it using Samba ?

Every help is appreciated.

Thanks

---

### Post by cgjones on 2006-05-10
Check out the man page for the **net** command.
```
man net
```
There is a shutdown option that might work for you.

---

### Post by krypto_wizard on 2006-05-10
I am using the shutdown option and giving right username and password for the windows PC but I am getting rpc error.

I need some help in setting up the smb.conf file correctly.

Any clue if anybody has done like this before.

Thanks

[QUOTE=cgjones]Check out the man page for the **net** command.
```
man net
```
There is a shutdown option that might work for you.[/QUOTE]

---

### Post by cgjones on 2006-05-10
Which versions of Windows are these computers running, and what exact command are you using?

---

### Post by krypto_wizard on 2006-05-10
[QUOTE=cgjones]Which versions of Windows are these computers running, and what exact command are you using?[/QUOTE]

These are windows XP.

I am using the following command

$ net rpc SHUTDOWN -I 192.168.XXX.XXX -U username

And I get an error

utils/net_rpc.c:rpc_shutdown_internals(4108)
Shutdown of Remote machine failed.

Every help is appreciated.

---

### Post by cgjones on 2006-05-10
Have you tried leaving the protocol out?
```
net SHUTDOWN -I 192.168.XXX.XXX -U username
```

---

### Post by krypto_wizard on 2006-05-10
Error message:
No command: Shutdown

It neccesititaes to use rpc or some protocol.

[QUOTE=cgjones]Have you tried leaving the protocol out?
```
net SHUTDOWN -I 192.168.XXX.XXX -U username
```[/QUOTE]

---

### Post by cgjones on 2006-05-10
**net** should automatically try to determine the correct protocol if one isn't specified. Try this command:
```
rpcclient -U *username* -I *IP Address* -c shutdown
```

---

### Post by krypto_wizard on 2006-05-10
no success!!

It gives me the USAGE of rpcclient after doing this.

Any more suugestions ?

Can you do this thing at your home ?

[QUOTE=cgjones]**net** should automatically try to determine the correct protocol if one isn't specified. Try this command:
```
rpcclient -U *username* -I *IP Address* -c shutdown
```[/QUOTE]

---

### Post by cgjones on 2006-05-10
This just isn't my day. I would try it if I had a computer running Windows.

Try this:
```
rpcclient -U username -I IP Address -c REG shutdown
```

---

### Post by krypto_wizard on 2006-05-10
Thanks cgsjones for your efforts. I am off the work now but I will try in couple of hours and keep you posted. 

[QUOTE=cgjones]This just isn't my day. I would try it if I had a computer running Windows.

Try this:
```
rpcclient -U username -I IP Address -c REG shutdown
```[/QUOTE]

---

### Post by cgjones on 2006-05-10
No problem. We'll get this figured out one way or another.

---

### Post by krypto_wizard on 2006-05-12
It gives me an error

failed tcon_X with NT_STATUS_DUPLICATE_NAME
Cannot Connect to Server. Error was NT_STATUS_DUPLICATE_NAME

Any more clues ??

[QUOTE=cgjones]This just isn't my day. I would try it if I had a computer running Windows.

Try this:
```
rpcclient -U username -I IP Address -c REG shutdown
```[/QUOTE]

---

### Post by cgjones on 2006-05-12
Try this:
```
rpcclient -c 'shutdown' -U *username* -I *ip address*
```

I also found information about needing to have the Windows machine set up correctly. See if your local security policy allows shutdowns from a remote system.

---

### Post by cgjones on 2006-05-12
Edit: Double Post

---

### Post by cgjones on 2006-05-12
Edit: Triple Post

---

### Post by krypto_wizard on 2006-05-12
[QUOTE=cgjones]Try this:
```
rpcclient -c 'shutdown' -U *username* -I *ip address*
```

I also found information about needing to have the Windows machine set up correctly. See if your local security policy allows shutdowns from a remote system.[/QUOTE]


That rite, I need to enable certain settings in windows to accepts remote command. I am googleing it, haven't found something that will work.

Do you have any idea ?

---

### Post by cgjones on 2006-05-12
I think that if you go to Start >>Control Panel >> Administrative Tools >> Local Security Policy you can set the options to allow remote shutdowns. Although if you are logging in through rpcclient as an Administrative user, you should already be allowed to shutdown the computer. Did you try that last command I posted?

---

### Post by krypto_wizard on 2006-05-12
I did, it wont work either.

after this command it gives me how to use the rpcclient option...thats it.

Is there any other OUT OF THE BOX WAY TO do the same thing.

[QUOTE=cgjones]I think that if you go to Start >>Control Panel >> Administrative Tools >> Local Security Policy you can set the options to allow remote shutdowns. Although if you are logging in through rpcclient as an Administrative user, you should already be allowed to shutdown the computer. Did you try that last command I posted?[/QUOTE]

---

### Post by cgjones on 2006-05-12
If these computers are running Windows XP Professional, you could turn on Remote Desktop and then log into them using the Terminal Services Client (I think thats what its called) in Ubuntu. This should give you the Windows desktop, and then you could shut it down. I'm running out of ideas on how to get this working with Samba. We must be missing something, because I think either **net** or **rpcclient** should work.

---

### Post by krypto_wizard on 2006-05-12
I have to write a script and run the script to get the shutdown operation done. 

I installed called WAC server Manager on Windows, it is a SSHD equivalent on Windows. I can login to windows fron linux using

ssh user@IP_ADDRESS


It asks me password. And then I use shutdown command to get it done.

Can we automate this procedure that if these parameters are given in the script, it will execute by itself without asking for password. 

[QUOTE=cgjones]If these computers are running Windows XP Professional, you could turn on Remote Desktop and then log into them using the Terminal Services Client (I think thats what its called) in Ubuntu. This should give you the Windows desktop, and then you could shut it down. I'm running out of ideas on how to get this working with Samba. We must be missing something, because I think either **net** or **rpcclient** should work.[/QUOTE]

---

### Post by cgjones on 2006-05-12
Taking a quick look at WAC's site, it looks like you should be able to set this up so that in can be scripted without needing user intervention. You'll need to set up authorized keys though, so that you won't need to supply a password when the script runs. Check out the documentation for WAC to find out how to set up authorized keys (public keys).

---

### Post by krypto_wizard on 2006-05-12
I wil try this one.....can we also pass shutdown command in the script somehow ?


[QUOTE=cgjones]Taking a quick look at WAC's site, it looks like you should be able to set this up so that in can be scripted without needing user intervention. You'll need to set up authorized keys though, so that you won't need to supply a password when the script runs. Check out the documentation for WAC to find out how to set up authorized keys (public keys).[/QUOTE]

---

### Post by cgjones on 2006-05-12
You should be able to pass the shutdown option through the script. Although I tried something similar once, and never got SSH working quite right. Once the SSH session is opened, the remote machine can't continue executing the script, so it just sits there, waiting for input.

---

### Post by krypto_wizard on 2006-05-12
whats happening with me right now is that once i create a pair of public and private key it asks for a passphrase.

When I logon using ssh user@IP_Address

it always asks for a passphrase


So that way it still didnt get automated. I have to supply passphrase.

Any input ???


[QUOTE=cgjones]You should be able to pass the shutdown option through the script. Although I tried something similar once, and never got SSH working quite right. Once the SSH session is opened, the remote machine can't continue executing the script, so it just sits there, waiting for input.[/QUOTE]

---

### Post by cgjones on 2006-05-12
How did you generate the key pair? Have you set up the public key on the remote machine?

---

### Post by krypto_wizard on 2006-05-12
yes, using the ssh-keygen i generated the key pair

```

ssh-keygen -t dsa

or 

ssh-keygen -t rsa

```
It will ask a passphrase while creating key pairs.

By haing private key in client's $HOME/.sshd/ and by having public key in server $HOME/.sshd, I use ssh but it always asks for a passphrase.

So there I am kinda stuck .....

every help is appreciated


[QUOTE=cgjones]How did you generate the key pair? Have you set up the public key on the remote machine?[/QUOTE]

---

### Post by cgjones on 2006-05-12
Did you specify a passphrase when you generated the key pair, or did you leave it blank? And you need to have the contents of the public key in a file called authorized_keys in $HOME/.ssh/

---

### Post by krypto_wizard on 2006-05-12
I think I missed on that i will check that again. Is that at the server end or client end ?

[QUOTE=cgjones]Did you specify a passphrase when you generated the key pair, or did you leave it blank? And you need to have the contents of the public key in a file called authorized_keys in $HOME/.ssh/[/QUOTE]

---

### Post by cgjones on 2006-05-12
You create the key pair on the computer you will be logging in from, then copy the public key to the computer you will be logging into. Then **cat** the contents of the public key into the authorized keys file. Take a look at the man pages for **ssh** and **ssh-keygen**.

---

### Post by krypto_wizard on 2006-05-12
Thanks, In the meanwhile I came across

[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

Have you tried that ?

[QUOTE=cgjones]You create the key pair on the computer you will be logging in from, then copy the public key to the computer you will be logging into. Then **cat** the contents of the public key into the authorized keys file. Take a look at the man pages for **ssh** and **ssh-keygen**.[/QUOTE]

---

### Post by cgjones on 2006-05-12
I've looked at it before, but never really had the need to run SSH on Windows.

---

### Post by krypto_wizard on 2006-05-13
I have started using openssh for windows as it is free and WAC was not free.

I have setup everything successfully but for a small problem.

When I ssh from linux box to windows PC, it asks me a password. I tried all possible passwords but it just wont let me login. So I tried from another windows pc to login to Windows PC, and same problems persisted.

Do you have any idea with this ?


[QUOTE=cgjones]I've looked at it before, but never really had the need to run SSH on Windows.[/QUOTE]

---

### Post by cgjones on 2006-05-13
No idea on that. I've never run OpenSSH on Windows. I would make sure that OpenSSH is set up correctly on Windows. Do you need to set up users accounts, or does OpenSSH use the Windows user accounts like it does on Linux?

---

### Post by krypto_wizard on 2006-05-13
I think you need to setup user accounts and I did setup them.But while sshing from linux box it wont accept those passwords and after 3 attempsts it shutd down the daemon.

Any ideas ?

[QUOTE=cgjones]No idea on that. I've never run OpenSSH on Windows. I would make sure that OpenSSH is set up correctly on Windows. Do you need to set up users accounts, or does OpenSSH use the Windows user accounts like it does on Linux?[/QUOTE]

---

### Post by cgjones on 2006-05-13
Are you using passwords for authentication, or public keys?

---

### Post by krypto_wizard on 2006-05-13
I set up passwd file in /etc/passwd.

That didnt work, so I tried using public keys meachnism.

Am I missing on something ???

[QUOTE=cgjones]Are you using passwords for authentication, or public keys?[/QUOTE]

---

### Post by cgjones on 2006-05-14
Detail the exact steps you've taken so far, and we'll see if we can figure something out.

---

### Post by krypto_wizard on 2006-05-15
I am doing the following steps

1. Installed Openssh on windows.

2. I performed 
```

mkgroup -l > .. \etc\group
mkpasswd -l -u username >> .. \etc\passwd

```

3. Generate public and private keys on Ubuntu box
```

ssh-keygen -t dsa

```

4. Copied the id_dsa.pub to windows user directory
```

$HOME\username

```

5. Copied the id_dsa.pub into the autorized_keys in the $home directory.

6. Started the daemon on Windows

net start opensshd

7. From Ubuntubox connected as

```

ssh -v username@IP_ADD

```

Windows box asks a password and after giving password I successfully login.

Inspite of setting public and private keys it still asks me the login password. I want to automate the procedure to run the shutdown.exe as I login.


Am I missing something on here.

Every help is appreciate.

Thanks for all your help,




[QUOTE=cgjones]Detail the exact steps you've taken so far, and we'll see if we can figure something out.[/QUOTE]

---

### Post by cgjones on 2006-05-15
On Linux, the authorized_keys file should go in /$HOME/*username*/.ssh/

Not sure if it would be the same in Windows, but I would think that it should be.

---

### Post by krypto_wizard on 2006-05-15
I tried at both the places...i.e in /$HOME and well as /$HOME/.ssh

Any ideas if I am doing wrong or something ?


[QUOTE=cgjones]On Linux, the authorized_keys file should go in /$HOME/*username*/.ssh/

Not sure if it would be the same in Windows, but I would think that it should be.[/QUOTE]

---

### Post by cgjones on 2006-05-15
No, that should be right. When you created the keys, did you specify a passphrase or did you leave it blank?

---

### Post by krypto_wizard on 2006-05-15
I left it blank because if I make a passphrase I cannot automate.

I had tried with passphrase also and that time it didnt ask me the passphrase either.

So I am assuming that public/private key thing is not working for me.

Every help is greatly appreciated.

Thanks man


[QUOTE=cgjones]No, that should be right. When you created the keys, did you specify a passphrase or did you leave it blank?[/QUOTE]

---

### Post by krypto_wizard on 2006-05-16
Hi,

I finally got it working to work with public keys where you dont need to provide password at the run time.

Now, I came to my ultimate goal which was shutting it down remotely from linux terminals.

So, I wrote a script like 
```

ssh Admin@IP_ADDR  # connects me fine now without problems (LOCAL)
shutdown -s            # This is a windows command (REMOTE)

``` 

Now, when I run this script, it successfully logs me into the windows box but doesn't run the second part of the script which is shut down.


Can you please tell me why ??

Eveyr help is appreciated.

[QUOTE=cgjones]No, that should be right. When you created the keys, did you specify a passphrase or did you leave it blank?[/QUOTE]

---

### Post by krypto_wizard on 2006-05-16
Finally got it working. It has to be done like this to execute a remote script on windows PC.
```

ssh username@IP_ADDR shutdown -s

```

Thanks for all your help cgjones, your responses really kept me trying. Thanks.
I really appreciate it.

---

### Post by cgjones on 2006-05-18
Glad you got it working. I just kept drawing a blank.

---

### Post by tackfurlo on 2008-06-06
I would like to mention some simi-progress I have made on this subject.

I have a remote system I'm SSHed into.  It's an Ubuntu Server 7.10 box and therefore doesn't have any sort of GUI (and hence no capability to access Remote Desktop).  I have a windows box which I use as a wifi AP on the same network linking a desktop without wifi to the internet.  To recap:

Redeemer, laptop with wifi running ICS on Windows Server 2003
Nautilus, laptop using ethernet with Ubuntu Server 7.10 and ssh, SAMBA.  Only system accessable from internet.
Enlightened, desktop running Thunderbird & Windows Server 2003, using Redeemer to get online.
Specter, laptop I'm using now that I want to setup Evolution on, running Ubuntu 8.

My problem is that Thunderbird on Enlightened accesses GMail over POP3 once every minute.  My plan is to setup a sort of POP proxy on Nautilus so that I can get email via POP3 on both Specter and Redeemer.  GMails POP3 system won't go to 2 computers at once.  Using Nautilus, it will be setup so that it will check GMail and then all my other systems can check Nautius.

Here the problem begins.  Before I can do any server setup, I want to setup evolution on Specter first.  However, for that to work, I need to shut down either Enlightened (which is on the other side of Redeemer) or just shut down Redeemer (hence knocking Enlightened offline for now.)  The wifi card on Redeemer randomly dies every couple days anyway so at some point it will go offline anyway but I would prefer to begin working on this now, since configuring the POP proxy may take me a while as I don't even know what I'll use for it just yet.

I can SSH to Nautilus with no problem, but telnet is not open on Redeemer and I have no other method to access it right now.  I am a 2 hour drive away and cannot physically access it to install any kind of SSH until Monday, which also defeats the purpose of doing it at all.  So, because of the circumstance I am in I need to be able to execute a samba shutdown remotely from Nautilus.  I have added smbclient and thus have rpcclient available.  After a couple (hundred) rounds of trial and error, I had zero success with "net shutdown" but have had minor success with rpcclient.  This is what I get:

```
tackfurlo@Nautilus:~$ rpcclient --user='Server2003' -I 192.168.7.104 --command='REG shutdown' Redeemer
Password:
command not found: REG
tackfurlo@Nautilus:~$ rpcclient --user='Server2003' -I 192.168.7.104 --command='REGshutdown' Redeemer
Password:
command not found: REGshutdown
tackfurlo@Nautilus:~$ rpcclient --user='Server2003' -I 192.168.7.104 --command='shutdown' Redeemer
Password:
Invalid command
tackfurlo@Nautilus:~$ 

```

My first breakthrough was when I discovered that you MUST provide a hostname argument, EVEN IF you specify an IP address.  The man page doesn't say this (and even inferrs that the IP argument can be used as a substitute for a hostname, which it can't, and it will give you back usage if you try.)  After that, I have discovered that you don't need the "REG" as part of the command argument, based on the error output.  The command is simply "shutdown".  So, knowing my password and now even the rpcclient command is correct, I next attempted a port scan using NMAP.  Here's what I get from that:

```
tackfurlo@Nautilus:~$ nmap -v -p 130-140 192.168.7.104

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-06 14:56 CDT
Initiating Ping Scan at 14:56
Scanning 192.168.7.104 [1 port]
Completed Ping Scan at 14:56, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 14:56
Completed Parallel DNS resolution of 1 host. at 14:56, 13.00s elapsed
Initiating Connect Scan at 14:56
Scanning 192.168.7.104 [11 ports]
Discovered open port 139/tcp on 192.168.7.104
Completed Connect Scan at 14:56, 0.01s elapsed (11 total ports)
Host 192.168.7.104 appears to be up ... good.
Interesting ports on 192.168.7.104:
PORT    STATE  SERVICE
130/tcp closed cisco-fna
131/tcp closed cisco-tna
132/tcp closed cisco-sys
133/tcp closed statsrv
134/tcp closed ingres-net
135/tcp closed msrpc
136/tcp closed profile
137/tcp closed netbios-ns
138/tcp closed netbios-dgm
139/tcp open   netbios-ssn
140/tcp closed emfis-data

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 13.099 seconds
tackfurlo@Nautilus:~$ 

```

Notice that port 139 is open and therefore it appears that SMB, and the windows Server service, is running.  I can see most other SMB ports are closed and I am thinking that maybe this is the problem (perhaps it requires 135, 137, or another to be open) but I think with 139 it should take the command - someone please correct me if I'm wrong.  The user account is in the Administrators group so as someone mentioned earlier, it has permission to shutdown regardless of remote shutdown permissions for normal user accounts.

So I'm all out of things to try.  I need to shut this down soon, otherwise I might as well just wait until after 5 on Monday when I'm there and have finished work for the day, but if I can I'd like this to be working by 8AM Monday so I don't have to deal with not getting email (or using the web based GMail system on one system and POP3 on another) all day Monday.  My day job is as a paralegal and I depend on email literally for a living so if I can't get Enlightened offline before I setup evolution and I start losing emails I will mess something up in a hurry.

Any thoughts?

---

### Post by chronos00 on 2008-08-15
This is quite old, but it's never too late to bring something back to the community.

I had the exact same problem as you. After reading your post and countless more, and many MANY trials and errors, I finaly got it working...

The problem isn't with samba, but with windows local security policies.
More precisely, after changing the following parameter:
"Network access: security model for sharing for local accounts." [1-see below]
to the "classic" setting, the rpc shutdown command finally worked.

[1] My windows is in spanish, and what I posted is my humble (and probably wrong) translation. The original setting was called:
"Acceso de red: modelo de seguridad y para compartir para cuentas locales".
I know this sounds awful in spanish too, but this is also probably translated from english.
Two possible settings:
"Classic: local users authenticated as themselves"
or
"guests only: local users authenticated as guests"

Hope this finally helps someone.
Regards

---

### Post by stimpak on 2008-10-22
i know its old, but i was searching up and down the internet for a solution

anyway make sure to do what chronos001 suggested and run 

net rpc shutdown -s  -I XXX.XXX.XXX.XXX -U "user name"


dont forget the " " after the -U command otherwise samba, if the uname is john doe, will sent only john, and thus get an error that says

The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE

---

### Post by Ubuntolonius on 2008-11-18
The following command works fine for me: 
net rpc shutdown -t 10 -f -C "must not be empty" -U "name" -I xxx.xxx.xxx.xxx

---

### Post by Cracauer on 2008-11-19
I wrote a little TCP server to remote control Windoze.

It does shutdown, reboot or sends a screenshot of the current Windoze screen or of the current foreground Window.

P.m. me if that sounds useful, I'd have to dig out the newest version. You'll need that Win32 perl port, name I've forgotten.

---

### Post by msisamonopoly on 2008-11-24
> **Ubuntolonius said:**
> The following command works fine for me: 
net rpc shutdown -t 10 -f -C "must not be empty" -U "name" -I xxx.xxx.xxx.xxx

Cool. It works, but found adding **-W domainname** helps.

BUT! - anyway to include the password so that it can be automated?? Am trying to script it and couldn't see anything in the MAN file to indicate how to include the password.

---

### Post by msisamonopoly on 2008-11-24
Actually. I stumbled upon it.

You need to put **%password** immediately after the username without a space. I had tried with a space that didn't work.

So command line that can be scripted >>

net rpc shutdown -t 10 -f -C "must not be empty" -W domainname -U "name"%password -I xxx.xxx.xxx.xxx

Thanks to Ubuntolonius for the key clue.

---

### Post by stimpak on 2008-11-25
works

---

### Post by mohdshakir on 2009-02-17
Someone blogged about it here;
[http://www.techrecipes.net/operatingsystem/linux/shutdown-windows-machine-remotely](http://www.techrecipes.net/operatingsystem/linux/shutdown-windows-machine-remotely)

---

### Post by Dssnz on 2009-03-14
RPC, Remote procedure call - Service needs to be running on the windows machines.
Computer managment - Services
find Remote procedure call tell it to start automatically and to start
and see if it makes any difference.

---

### Post by televisi on 2009-11-22
Yes, the following works as expected.

To reboot Windows from Linux, just add **-r**:
```
[FONT=&quot][FONT=&quot] [/FONT][/FONT]net rpc shutdown **–r** -C "Message from Server: Your computer will be restarted in 15 minute for major system update" -t *900* -f -I *IP_ADDRESS* -U *USER*%*PASSWORD*  
```

Now how about **giving an options to user who logged in to abort the shutdown/reboot process?** can we do that?
let's say, the user click NO, and the shutdown/reboot process aborted

> **Ubuntolonius said:**
> The following command works fine for me: 
net rpc shutdown -t 10 -f -C "must not be empty" -U "name" -I xxx.xxx.xxx.xxx

---

### Post by zazuge on 2009-12-23
just a quick tip
if you want to change the local security policy about remote shutdown
write it on a netlogon script on your samba server 
for example to disable autorun on the client xp

REG ADD HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer /v NoDriveTypeAutoRun /t REG_DWORD /d 0xFF /f

the same can be done about other security strategy rules by manipulating the registry from netlogon scripts

---

### Post by chronos00 on 2009-12-23
> **zazuge said:**
> just a quick tip
if you want to change the local security policy about remote shutdown
write it on a netlogon script on your samba server 
for example to disable autorun on the client xp

REG ADD HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer /v NoDriveTypeAutoRun /t REG_DWORD /d 0xFF /f

the same can be done about other security strategy rules by manipulating the registry from netlogon scripts

grate idea!!
Thanks!

---

### Post by jobsonandrew on 2010-04-21
I didnt read the whole thread, but I noticed that the syntax of commands has been quite wrong throughout..

```
net rpc -S 192.168.0.21 shutdown -t 1 -f
```

That worked great for me

Cheers!

---

### Post by Akim on 2010-06-02
The net rpc commands for shutdown windows machines works fine... but with a vista client throws this error:
[I]utils/net_rpc.c:run_rpc_command(186)
 Could not initialise pipe \winreg. Error was NT_STATUS_OBJECT_NAME_NOT_FOUND[/I]

I think this isn´t a authentication problem...

Could anyone help me?

With the service "Remote registry" started on the Vista machine, samba throws
[I]Shutdown of remote machine failed

result was: DOS code 0x00000078[/I]

---

### Post by Akim on 2010-06-02
I found the solution (I HATE VISTA):

[http://www.howtogeek.com/howto/windows-vista/enable-mapping-to-hostnamec-share-on-windows-vista/](http://www.howtogeek.com/howto/windows-vista/enable-mapping-to-hostnamec-share-on-windows-vista/)

With adding this key remote shutdown of Vista machines works fine :P

---

### Post by orionshock on 2010-11-09
--Sorry to bump after so long

I went looking for this to control my WinXP computer that acts as a media center.

Lots of sugestions & ideas in this thread. However there was one thing that made it work, and it was actually linked from this thread as a side idea.

On Windows: 
Control Panels > Admin Tools > Local Security Settings
 Then in:
Local Policies > Security Options > "Network Access: Sharing and security model for local accounts"

Setting this to Classic mode finally did the trick with the following command from Ubuntu:


net rpc shutdown -t TIME_SECONDS -U UID%PW -I IP_Address

---

