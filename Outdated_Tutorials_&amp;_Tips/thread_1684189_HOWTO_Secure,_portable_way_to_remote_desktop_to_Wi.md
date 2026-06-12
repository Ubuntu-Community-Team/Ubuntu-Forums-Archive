---
title: "HOWTO: Secure, portable way to remote desktop to Windows"
date: 2011-02-08
forum: Outdated Tutorials &amp; Tips
---

### Post by billdotson on 2011-02-08
Alright folks, so I figured out how to do this about three years ago, and thankfully I wrote down how to do it for future reference.

What I am going to tell you how to do is:
Establish a remote desktop connection with a Windows machine using TightVNC.
Encrypt the communication channel by tunneling it through SSH.
Use RSA encryption technology for added security.
Using a portable version of TightVNC, you can also remote desktop into your target machine from any Windows machine where you are authorized to run the program with "admin" permissions.

So here we go:

type commands are followed by what to type in quotes.  do NOT actually type the quotes.

also, make sure to save your putty sessions so that you will not have to type in the information all over again

each time you want to use it.

 

 

 

how to

1)install openssh in cygwin in Windows and get sshd server running

2)tunnel TightVNC through putty

3) use RSA authentication to login

 

1) Run cygwin.exe

go through the standard procedure until you get to the packages screen

choose openssh, tcp-wrappers, and zlib.  nano and vim are optional but recommended.

open the cygwin terminal and type "ssh-host-config -y" and then when it says CYGWIN= type

"ntsec tty" (without quotes).  Then type "net start sshd" or "cygrunsrv --start sshd"

To stop sshd type "net stop sshd" or "cygrunsrv --stop sshd"

 

2)  Type the domain of the target computer (or the IP address) set the port to 22 and the type to ssh,

then go to SSH > X11 > enable X11 forwarding and then in the box below (X display location) type localhost:0

Then go to tunnels.  Put port 5900 and then for destination put localhost:5900.  Make sure the port is set to local.

Then connect with putty like normal.  Then open tightvnc viewer and connect to localhost:0 (because the port is 5900 and with tightvnc port

5900 is screen :0, 5901 is screen :1 and so on)  Make sure to forward port 22 on your Windows firewall and the router.

3)  Stop the sshd service if it is running.If you do not already have puttygen.exe download it. 

Click on generate and then make sure that the key you

are generated is SSH-2 RSA (1024 bits).  Then move the mouse around to create the key.  Save the private key

Now copy and paste the public key in the dialog box at the top into a text file.  Now open cmd.exe, then open that file and save as, but leave

the new file (result of save as) without an extension.  Now open the cygwin terminal and create a folder .ssh

in /home/Bill.  Now copy that new file (made with cmd.exe with the public key in it) to /home/Bill/.ssh/authorized_keys.

Now type "chmod 711 /home/Bill/.ssh/authorized_keys" to change the permissions so that only root can edit it.

Now change the permissions of sshd_config in /etc so that it can be written to.  Go in and uncomment the lines

that refer to LoginGraceTime, allow root to login (set to no), strict modes (no), MaxAuthTries (6),

RSA Authentication (yes), PubKey authentication (yes), Authorized_keys file (.ssh/authorized_keys),

PasswordAuthentication (no), PermitEmptyPasswords (no), and Allow X11 Forwarding (yes).  Then that private key

you made with putty earlier, then go to ssh > auth and put the file's path in the box in putty that says

"private key file for authentication"

 

Now start the sshd server.

If all of the previous instructions were followed, and everything goes according to plan:

Open PuTTY, and open your session that have all the correct information (the 5900 port number, the domain or IP,

the auth key file path for the public key, etc. [all mentioned above]) then hit connect.  You should then have to

enter the username.  If the username is correct putty will say the key has been paired, and then it will ask

for the passphrase for the key.  Now you are logged in.  However, this is not the end.  Now, open up TightVNC

viewer and type localhost:0 in the dialog box next to the connect button.  Now hit connect and you should be

prompted for the vnc password.  Enter the password and you've done it. The only way a user can connect to your machine is to know your username, have the RSA authetication key and know the passphrase for the key.

 

Great Job!   


Note: I did this a few years ago, so some things may be different. However, I'm assuming that cygwin still works in Windows and that TightVNC still works about the same.
If you notice any potential security issues (or any other issues) with my method please suggest improvements.

---

