---
title: "Secure RSA Key Authorization with FreeNX and NX Client in Precise"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by mcgrete on 2012-12-13
Hello,

I have a recent installation of Ubuntu 12.04LTS.  I have also recently installed FreeNX so that my home PC serves as a host (Precise comes with ssh server already installed).  I have also succesfully installed NX Client (on the same PC as well as a different PC) to connect to my host computer.  I am attempting to use keys.  I am able to connect from my local network (192.168.1.XXX), as well as an external network (by using a DYNDNS service that points to my dynamic ipaddress).  I do not use the standard port 22; I modified configuration files to use another port.

I attempted to setup custom keys; however, without installing/using the new custom key on the actual client(s), I was able to connect to my host; the host PC indicated the RSA key fingerprint, asked if I want to continue the connection, and when I said yes, it warned that it permanently added 'mydyndnsaddress' to the list of knowns hosts.  

I have tried to fix this for days now, without success.  I believe that I am misunderstanding one or several important points, but with all the different (and some dated) posts offering advice, I believe I have confused myself to no end.

What I believe (not sure) is happening is that my ssh server permits connections with my simple login and password, irrespective of the keys that are used.  I have tried to use a new custom key, and modify the configuration, but have had no success; I tried multiple threads found over the internet without success.  I have confused and frustrated myself to the point where I lack confidence and will to continue further without asking for assistance.

What I would like to do is:
1.  Remove all keys from the host as if starting new.  (I am confused as to where / which directories & files contain the keys and AuthorizedKeyFiles (Keys2 or standard Keys), and how to setup the node.conf and sshd_config files to do this...)
2.  Create a new custom key that will be used for authorization, and use a passphrase.  
3.  Setup the ssh server to use RSSAAuthentication, and not permit authorization with a users login and password.  
4.  Understand if/how to setup AllowUsers (nx and myself, or others), and if this pertains to the ssh server, or the nxserver, or both.  Replicate to remove/add users as desired.
5.  Disable the PermitRootLogin and use RSA authentication so that the user will need to know the normal user's RSA passphrase plus the root password to login as root.


Here is what I have done so far...
A. Online instructions indicate issues with Unity, and the need for a simple(r) version of Gnome...so I executed "sudo apt-get install -y openssh-server python-software-properties gnome-session-fallback".  Feedback indicates I already have installed.
B. Make sure ubuntu-desktop is installed (prerequisit, but I confirmed that 1.267 is already installed)
C. Make sure that openssh-server is installed using the command "sudo apt-get install openssh-server"; it was already installed.
D.  Add the Freenx PPA via "sudo add-apt-repository -y ppa:freenx-team"
E.  Install Freenx Server via "sudo apt-get update", and "sudo apt-get install -y freenx freenx-server"
F.  Download the installation script via "wget https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz"
G.  Extract the script and copy it to the NX directory vai "tar -xvf nxsetup.tar.gz", and "sudo cp nxsetup /usr/lib/nx/nxsetup"
H.  Run the installation script "sudo /usr/lib/nx/nxsetup --install", and say Ues to creating a custom KeyPair.
I.  Download NX Client for Linux (Ubuntu version) from [http://www.nomachine.com/download-package.php?Prod_Id=3829;](http://www.nomachine.com/download-package.php?Prod_Id=3829;) saved to ~/Downloads/NXCLIENT
J.  Installed NX Client via "sudo dpkg -i nxclient_3.5.0-7_amd64.deb", followed instructions to enter command to allow printing from from the NX session...i.e. "sudo chmod 755 /usr/lib/cups/backend/ipp"
K.  I modified the sshd_config file to change the ssh server port to XXXXX, and restarted the ssh server
L.  Was able to connect via ssh, i.e. "ssh [email]myusername@myDYNDNSname.dyndns.org[/email] -p XXXXX"
M.  But failed to connect via NX Client, so modified node.conf (if I recall correctly) to use port XXXXX as well.  Restarted ssh server.  I was able to conncect via NX Client on port XXXXX but not 22 (good); connection was established with it asking to continue after it identified the RSA key fingerprint...
N.  Tried to generate a new key with a more secure passphrase, so I tried "sudo ssh-keygen -p", and was asked "Enter file in which the key is (/root/.ssh/id_rsa):", and responded with "/var/lib/nxserver/home/.ssh/client.id_dsa.key".  Restarted server.  I think this generated a dsa key rather than a RSA key.  Would like to remove and use RSA as I understand it is more secure than DSA.
O.  Tried on 2nd computer (client), and was able to conenct/login without the new/modified key; system did ask if it was OK to procede with RSA fingerprint XX.XX.XX.blah.blah.  I said OK.  Seems that I am authorizing with username and password, not RSA Key.

Any help would be greatly appreciated.

---

### Post by mcgrete on 2012-12-17
Answering my own question / update:

I believe I was confusing ssh keys and nxserver keys.  One can generate keys for ssh (and use a passphrase if you so desire) via

```
ssh-keygen -t rsa (for an RSA keyset; conduct on the CLIENT) 
```

and generate a nxserver keyset (no passphrase possible) via

```
sudo /usr/lib/nx/nxkeygen
```
 with the nxserver keyset automatically replacing the/any existing key located at "/var/lib/nxserver/home/.ssh/client.id_dsa.key" (and backing up existing key automatically).  The nxserver keyset appears to have no impact on the RSA keyset.

:?: I have not figured out how to have nxserver generate an RSA key rather than a DSA key, it generates a DSA key by default (and 'man nxkeygen' provided no help); but, it is a custom key, not a default keyset.  

Wishing not to use PasswordAuthentication for ssh authorization, I disabled in /etc/sshd_conf; however, before I can do so, I need to establish/register the key with the server, which will require me to temporarily allow password authentication for ssh authentication.  I also made sure my nonstandard port was being used in /etc/sshd_config:
```
Port XXXXX
```

:?: What I fail to understand is:
where/how the registration takes place; I realize that it modifies certain files such as "authrozied_keys" or "authorized_keys2", but at which location "/var/lib/nxserver/home/.ssh"?  Other files?  In otherwords, if I were to cleanup my files, eliminate all but a given ssh key and ensure that it is being used and is authorized, how to do so?  Any help clearing this up would be appreciated, as understanding this would permit me to manage it better in the future.) 

I ended up with the following in my /etc/sshd_conf file:
```
PermitRootLogin no
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile %h/.ssh/authorized_keys2 (although removing %h works too)
PasswordAuthentication no
AllowUsers nx myusername
UsePAM yes
```

I wanted additional security for the nxserver; I am not sure how secure this is, but I finally decided to use PassDB authentication as I could not get it work otherwise, and becuse when I tried to addusers to nxserver, I obtained the following: "Most probably your FreeNX setup will work out of the box without this functionality and you've been misleaded by an old tutorial or old documentation to do this step. If however you really need this functionality, just set ENABLE_PASSDB_AUTHENTICATION="1" in node.conf."

:?:I am wondering:
if I had chosen SSH rather than PassDB for nxserver authentication, would I be required to have both the nxkey and the sshkey, and if/how the sshkey would request the passphrase?!  This would be preferred for security, but would be a little bit of pain to install keys on a Client if I wish to connect to the host, but what is the issue with installing 2nd key rather than a single key, ~ same effort for much higher security - assuming I don' misplace my keys and secure them properly on the Client machine(s)). THIS IS A BIG QUESTION FOR ME - any input would be appreciated! 

As my nxserver keyset is custom, then any user will need to have the private key "client.id_dsa.key' and import it into NX Client's configuration (as the content of 'client.id._dsa.key' hold the text "-----BEGIN DSA PRIVATE KEY-----" and end with "-----END DSA PRIVATE KEY-----".  Furthermore, using the PassDB, I established myself as a user with a password.  So, not only will someone need to obtain my private key, they will also need to obtain my password and username.  

:?: Am I understanding this properly, I read some posts that say this is the public key, but clearly when it is imported into the NX Client it indicates that it is a private key...


I made sure that ENABLE_PASSDB_AUTHENTICATION="1" in node.conf as well as setting the nonstandard port Port=XXXXX.

I also ran the following script to ensure that the configuration of freenx was consistent with my approach:
```
sudo dpkg-reconfigure freenx-server
```
selecting 'Custom Keys' on the first screen, and 'PassDB' on the second.  Of course, restart both ssh and nxservers via:
```
sudo restart ssh
sudo nxserver --restart
```

:confused: I am nearly there, but would appreciate any assistance on the "?"s above.  

Thanks!

---

