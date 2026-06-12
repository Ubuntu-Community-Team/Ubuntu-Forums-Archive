---
title: "HOWTO:  SSH &amp; Public Keys"
date: 2005-04-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Beernut on 2005-04-29
Since SSH (Secure Shell) scans are so common anymore I wanted to add better protection to my server so I configured SSH to only allow logins with public & private keys instead of password authentication.  This is how I set it up on Ubuntu however it should work on any version of Linux.  Don't be afraid of the length of this tutorial it's really pretty simple and only a few commands.  This HowTo ended up longer than I anticipated because I wanted to explain each step as best I could.

**This HowTo assumes that you already have SSH installed properly.**

The first thing we need to do is generate the key pair.  On your host computer go to "Applications">"System Tools">"Terminal" note this is your regular user terminal not a root terminal.  Enter the following command at the terminal.

```
username@ubuntu:~$ ssh-keygen -t dsa

Generating public/private dsa key pair.
Enter file in which to save the key (/home/username/.ssh/id_dsa):
 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again:
 
Your identification has been saved in /home/username/.ssh/id_dsa.
Your public key has been saved in /home/username/.ssh/id_dsa.pub.
The key fingerprint is:
5b:ab:73:32:9e:b8:8c:4b:29:dc:2a:2b:8c:2f:4e:45 username@ubuntu
```

As you see above I chose the default location for the keys which is in the .ssh/ directory in your home directory.  At the "Enter passphrase" prompt enter a strong password.  This password is needed to use the key so this adds some security in case your private key ever gets stolen.  **Your private key needs to be protected.**
 
This will generate a [DSA](http://www.rsasecurity.com/rsalabs/node.asp?id=2239) key pair.  If you notice I say pair it generates a private key *id_dsa* and your public key *id_dsa.pub* which we will copy to the server.

Next we need to copy the public key to the server.

```
username@ubuntu:~$ cd .ssh/
```

This moves you into .ssh directory where the keys were saved.  Now to copy the public key to the server.

```
username@ubuntu:~$ scp id_dsa.pub [email]serverusername@192.168.1.40:./id_dsa.pub[/email]

id_dsa.pub    100% |*****************************************************|  
 614  00:00
```

The "scp" command allows files to be copied to/from a remote server using the SSH protocol to establish a secure connection and to encrypt all data passing between the client and the server.

Now that we copied the public key to the server we have to install the key in the proper directory.  To do this login to the server using ssh and your usual password.  We still aren't using public key authentication yet but we are close.  Once logged into the server issue the following command in the terminal.  Note you don't need to be logged in as root just login with your normal user account.

```
username@server:~$ cd .ssh
serverusername@server:~$ touch authorized_keys2
serverusername@server:~$ chmod 600 authorized_keys2
serverusername@server:~$ cat ../id_dsa.pub >> authorized_keys2
serverusername@server:~$ rm ../id_dsa.pub
```

Ok so here we set the file permissions to 600 which is gives only the owner read and write access.  Then we added the key to the file called authorized_keys2.  Note it's important to use the >> because that adds the key to the file without any line breaks.  Then finally we removed the key id_dsa.pub from the server.  Now if you logout and log back in you should see that you are using the key authentication as shown below.

```
username@ubuntu:~$ ssh -l serverusername 192.168.1.40
Enter passphrase for key '/home/serverusername/.ssh/id_dsa':
Linux everest 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Mon Apr 25 19:43:43 2005 from 192.168.1.15
serverusername@everest:~$
```

There is one more step and that is to disable password authentication on the server.  Once this is set the only way to login will be with private and public keys.  In order to accomplish this we have to change a line in the ssh_conf file on the server.  The ssh_con file is located in the following location on the server /etc/ssh/ssh_config.  Once in the file look for the following line:

```
#   PasswordAuthentication yes

Change to:
  
PasswordAuthentication no
UsePAM no
``` 

Now that wasn't so bad was it?  I am not an expert with this I just put this together from searching around on my own and figured I would put it all together in one place in case I needed to do this again and hopefully it will help someone else out.

---

### Post by airhead on 2005-04-29
[QUOTE=Beernut]
Next we need to copy the public key to the server.

```
username@ubuntu:~$ cd .ssh/
```

This moves you into .ssh directory where the keys were saved.  Now to copy the public key to the server.

```
username@ubuntu:~$ scp id_dsa.pub [email]serverusername@192.168.1.40:./id_dsa.pub[/email]

id_dsa.pub    100% |*****************************************************|  
 614  00:00
```

The "scp" command allows files to be copied to/from a remote server using the SSH protocol to establish a secure connection and to encrypt all data passing between the client and the server.

Now that we copied the public key to the server we have to install the key in the proper directory.  To do this login to the server using ssh and your usual password.  We still aren't using public key authentication yet but we are close.  Once logged into the server issue the following command in the terminal.  Note you don't need to be logged in as root just login with your normal user account.

```
username@server:~$ cd .ssh
serverusername@server:~$ touch authorized_keys2
serverusername@server:~$ chmod 600 authorized_keys2
serverusername@server:~$ cat ../id_dsa.pub >> authorized_keys2
serverusername@server:~$ rm ../id_dsa.pub
```

Ok so here we set the file permissions to 600 which is gives only the owner read and write access.  Then we added the key to the file called authorized_keys2.  Note it's important to use the >> because that adds the key to the file without any line breaks.  Then finally we removed the key id_dsa.pub from the server.  Now if you logout and log back in you should see that you are using the key authentication as shown below.
[/QUOTE]

Nice howto  :) I'm not sure if you're aware if it, but the above can essentially be replaced with the "ssh-copy-id" command. As far as I'm aware, its only a debian thing. The only real difference to the above is that it copies your key to a file called "authorized_keys" instead of "authorized_keys2", but it still works the same.

I'm glad you said that the user must enter a password. IMO, if you don't passphrase your key, you're asking for trouble ;)

You might also like to add something about ssh-add as it saves you from entering your passphrase everywhere.

---

### Post by Heliode on 2005-04-30
Thanks for the howto! But how do I disable regular password authentication now that this is in place?

---

### Post by Beernut on 2005-05-01
[QUOTE=Heliode]Thanks for the howto! But how do I disable regular password authentication now that this is in place?[/QUOTE]

I forgot about this part I'll add it to the HOWTO above.  You need to edit the following file on the server.  /etc/ssh/ssh_config now there are a few ways to do this like below.

```
sudo vim /etc/ssh/ssh_config

sudo gedit /etc/ssh/ssh_config  (Enter this one only if you are on the server.)
```

If you know how to use the  VI editor you edit the file from terminal on a remote host.  I am not that good with VI so I won't even attempt to tell you how to do it that way.   ;-) 

When you open the file all you have to do is change the following line to no.

```
#   PasswordAuthentication no
```

That should do it for you.

---

### Post by Beernut on 2005-05-01
[QUOTE=airhead]Nice howto  :) I'm not sure if you're aware if it, but the above can essentially be replaced with the "ssh-copy-id" command. As far as I'm aware, its only a debian thing. The only real difference to the above is that it copies your key to a file called "authorized_keys" instead of "authorized_keys2", but it still works the same.

I'm glad you said that the user must enter a password. IMO, if you don't passphrase your key, you're asking for trouble ;)

You might also like to add something about ssh-add as it saves you from entering your passphrase everywhere.[/QUOTE]

Thanks.  I just found the "ssh-copy-id" command but wasn't sure if it would work the same.  The file is named "authorized_key2" so that if you want to have seperate keys for Protocol 1 & Protocol 2 versions of ssh.  I am going to try it on my Suse box to see if it is just a Debian thing or not.

I hate blank passwords or passphrases.  Why go through the trouble of securing you server and then leave that out?

Thanks for the hint on ssh-add command I'll have to look into it.  Does that just remember your password for the current session?

---

### Post by airhead on 2005-05-03
[QUOTE=Beernut]Thanks for the hint on ssh-add command I'll have to look into it.  Does that just remember your password for the current session?[/QUOTE]

Thats correct.

When turning off password auth, I found that my debian testing version of sshd already had "PasswordAuthentication no". To really turn it off, you need to set "UsePAM no" (as sshd uses pam instead of doing the authentication itself).

---

### Post by Heliode on 2005-05-03
Hey, i'm probably doing something wrong here,but i've set password authentication to 'no' on my (Gentoo) server in the /etc/ssh/ssh_config file, but I can still logg in with my regular password if I just hit enter when it asks me for the passphrase for the key. any idea what might be causing this?

---

### Post by heon2574 on 2005-05-03
[QUOTE=Beernut]
When you open the file all you have to do is change the following line to no.

```
#   PasswordAuthentication no
```

That should do it for you.[/QUOTE]

I think you should remove that comment (#) after chaning it to "no."

EDIT: wait a sec..whay are we setting up "password authentication no" in ssh_config? Isn't it sshd_config we should be changing?

---

### Post by Beernut on 2005-05-04
OOPS Missed the comment that's the bad thing with copy and paste.  As far as changing it in the sshd_config file I don't have one on my system.  At least not in /etc/ssh/ which is where it should be according to the documentaion at [OpenSSH](http://www.openssh.com/manual.html). 

Also I don't see the anything about the "UsePAM no" option in the manual.

```
man ssh_config
```

---

### Post by dmccarney on 2005-05-16
Great howto. Very easy to follow. I have only one question: You explained how to generate the keypair on two Ubuntu boxes, I'm curious. I run the SSHD at home on my ubuntu box but often connect from my workplace using Putty. How does one go about generating another keypair on windows with Putty?

---

### Post by dmccarney on 2005-05-16
Nevermind. I figured it out by RTFM. Putty has a side program that will do this. Anyone who is interested should check out [Public Keys With Putty](http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter8.html#pubkey). Also, the PUTTY docs hint to a possible weakness in the DSA key for use with the SSH-2 protocol and recommends using RSA for SSH-2 instead so I modified your how-to to do that. Its all the same steps except for a different argument when you generate the key-pairs and of course point all of the other steps to the correct RSA keys.

The changed line in the howto at the start is

```
ssh-keygen -t dsa
```

changed to:

```
ssh-keygen -t rsa
```
Make sure you change all the subsequent lines to point to the RSA files and not a DSA file.

Thanks again for a great tutorial. :)

---

### Post by KmL on 2005-05-29
[QUOTE=Beernut]OOPS Missed the comment that's the bad thing with copy and paste.  As far as changing it in the sshd_config file I don't have one on my system.  At least not in /etc/ssh/ which is where it should be according to the documentaion at [OpenSSH](http://www.openssh.com/manual.html). 

Also I don't see the anything about the "UsePAM no" option in the manual.

```
man ssh_config
```[/QUOTE]

Hi, first post,

I recently tried to set public_keys with this how to, and it's work. But the file to edit is indeed sshd_config file in /etc/ssh/.

At the begin of the howto, you wrote that the ssh-keygen has to be done in the _host_, correct me if I'm wrong, but is'nt in the _client_?

great howto, before this, I didn't understand public-keys for ssh.

sonoma

---

### Post by arjay1 on 2005-08-17
Beernut - thanks for a great tutorial.  Really helped me.

However, I now have the same problem that others have had - I did the last bit of the posts re editing the sshd_config file (including usepam no) but I still have to log in when I ssh to the remote computer.

I thought this wouldn't happen any more?

TIA

---

### Post by Jaymoid on 2005-09-23
[noob post]I followed the guide exactly, but it only worked when I renamed the authorized_keys2 file to be authorized_keys on the remote server. Guessing this reverts to version 1 of the protocol.[/noob]

Also something quite handy is that if you enter a blank passphrase then you don't have to enter a passphrase when ssh-ing over to your remote server. Obviously this is not as secure, but its quite fun. Also handy for automating/crontabbing scp of files.

---

### Post by ggnore on 2005-09-23
[QUOTE=Jaymoid][noob post]I followed the guide exactly, but it only worked when I renamed the authorized_keys2 file to be authorized_keys on the remote server. Guessing this reverts to version 1 of the protocol.[/noob]

Also something quite handy is that if you enter a blank passphrase then you don't have to enter a passphrase when ssh-ing over to your remote server. Obviously this is not as secure, but its quite fun. Also handy for automating/crontabbing scp of files.[/QUOTE]

It can be secured : i use this method to backup some files on another computer by using crontab.
I created a user who cant log on at all (login disabled)
When i use scp to copy all my files on the other computer, i just use this account. rsa and dsa keys are only available for this user. It's powerfull and may be secured, if you cant.

---

### Post by Jaymoid on 2005-09-23
[QUOTE=ggnore]It can be secured : i use this method to backup some files on another computer by using crontab.
I created a user who cant log on at all (login disabled)
When i use scp to copy all my files on the other computer, i just use this account. rsa and dsa keys are only available for this user. It's powerfull and may be secured, if you cant.[/QUOTE]

Splendid idea! Thanks for that.

---

### Post by RandomGeek on 2005-10-10
Many thanks for the how to.  I was getting very confused - particularly at why the file needed to be called authorized_keys2 (duh, two protocols)

As others have mentioned, I'm still able to login using regular passwords which I really want to turn off.  The option "UsePAM no" causes a config error for me, it won't start the service when I add that option to ssh_config.

Are you sure it's not sshd_config? What's the difference between the two?

What I want is an ssh config that only allows me to login with one private key. Are the config files locked down as much as possible now?

Also, could somebody explain how to restart the service from the command line? I thought it was "/etc/init.d/ssh restart" but this gives me peculiar message and I can't see sshd which is what I'd expect.  Sorry if this is a dumb question :)

---

### Post by grugnog on 2005-11-19
OK, having played around with this for quite a while I finally figured out the problem I was having.
If you always get asked for a password (even when the keys are found, match and correct passphrase entered) then try this! None of the above advice works for me...
This is for Ubuntu Breezy trying to SSH into Debian Etch, both fresh installs.

On Debian, as root, edit /etc/ssh/sshd_config and edit the line
[INDENT]StrictModes yes[/INDENT]
to read
[INDENT]StrictModes no[/INDENT]

Then, on Ubuntu, as a regular user run:
[INDENT]ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub you@debian[/INDENT]
any then
[INDENT]ssh you@debian[/INDENT]
to check it worked.

Simple really, but to find that StrictModes option took a lot of trial and error :)

---

### Post by msr7x57 on 2005-11-25
For those of you who are thinking that ".ssh/authothized_keys" is ssh1 and ".ssh/authothized_key2" is ssh2, my "man ssh" tells me that when using ssh-keygen under  ssh1, you get keys called "$HOME/.ssh/identity" and a public key in "$HOME/.ssh/identity.pub".

In ssh2, you get "$HOME/.ssh/id_dsa or $HOME/.ssh/id_rsa" and the equivalent *.pub files.

HTH

---

### Post by Felipe_U on 2005-11-25
[QUOTE=RandomGeek]
Also, could somebody explain how to restart the service from the command line? I thought it was "/etc/init.d/ssh restart" but this gives me peculiar message and I can't see sshd which is what I'd expect.  Sorry if this is a dumb question :)[/QUOTE]
 I restart the ssh service with this command: sudo /etc/init.d/./ssh restart

Greetings,
Felipe

---

### Post by Felipe_U on 2005-11-25
[QUOTE=msr7x57]For those of you who are thinking that ".ssh/authothized_keys" is ssh1 and ".ssh/authothized_key2" is ssh2[/QUOTE]
I am actually using the authorized_keys file and not the authorized_keys2. If you want to use authorized_keys2 You'll have to change the following line in the sshd_config file.

AuthorizedKeysFile      %h/.ssh/authorized_keys

change it to:

AuthorizedKeysFile      %h/.ssh/authorized_keys2

Greetings,
Felipe

---

### Post by dashersey on 2005-11-30
Hey, just wanted to post the solution to a problem I was having on both  suse and ubuntu.

After following instructions similar to this HOWTO, I was successful in loggin into my server using public key authentication, using an rsa key (I have read that there are security issues using dsa). 

However, when I set up additional user accounts the server would refuse to use pubkey authentication and would either prompt for a password or give me an error (if I had disabled password auth). 

It was frustrating -- I had identical permissions on my authorized_keys file, and even identical content (I was using the same private key for both).

I tried a lot of things, including cp'ing vs >>'ing to create the file; tried authorized_keys2 vs authorized_keys ... played with group membership; no luck.

Finally after reading this thread I did a man ssh-copy-id and learned that you can't have group write access on either your home, your ~/.ssh directory, or the authorized_keys file. 

chmod g-w on each of these, and it worked! 

This seems strange, since Ubuntu seems to follow the UPG scheme, similar to [redhat]("http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-users-groups-private-groups.html"), where users have private groups. I had changed my umask to 002 to enable my users to access subversion repositories as themselves, and this is why my new user accounts had the wrong permissions for SSH. 

Hope this helps someone else!

---

### Post by rjewelll on 2006-02-17
I've spent a lot of time trying to get ssh keys to work and this thread was real helpful. The post by grugnog and the advice that StrictModes should be 'no' worked for me. Overall, there is a lot of great advice here. I'm new to the Ubuntu community. Will all of this helpful information get funnelled into the incomplete howto/wiki? I imagine that wasn't incomplete at one point (or on a certain system maybe)... but there are a lot of settings that should be mentioned to insure a successful setup and increase security. 

Thanks everyone! 

[http://ubuntuforums.org/images/smilies/icon_wink.gif](http://ubuntuforums.org/images/smilies/icon_wink.gif)
;);)

---

### Post by Hakimio on 2007-05-09
> **dashersey said:**
> This seems strange, since Ubuntu seems to follow the UPG scheme, similar to [redhat]("http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/s1-users-groups-private-groups.html"), where users have private groups. I had changed my umask to 002 to enable my users to access subversion repositories as themselves, and this is why my new user accounts had the wrong permissions for SSH. 

Hope this helps someone else!

Wooohoooooo. Just helped to me. Thank you! :)

---

### Post by helmingstay on 2007-08-15
> **dmccarney said:**
>  Also, the PUTTY docs hint to a possible weakness in the DSA key for use with the SSH-2 protocol and recommends using RSA for SSH-2 instead so I modified your how-to to do that. Its all the same steps except for a different argument when you generate the key-pairs and of course point all of the other steps to the correct RSA keys.

The changed line in the howto at the start is

```
ssh-keygen -t dsa
```

changed to:

```
ssh-keygen -t rsa
```
Make sure you change all the subsequent lines to point to the RSA files and not a DSA file.


I just looked into RSA vs. DSA key strength and security.  Lots of googling yielded two good technical references in
[http://en.wikipedia.org/wiki/Rsa](http://en.wikipedia.org/wiki/Rsa)
and 
[http://en.wikipedia.org/wiki/Digital_Signature_Algorithm](http://en.wikipedia.org/wiki/Digital_Signature_Algorithm)

It was finally "man ssh-keygen" that cinched it for me:

> 
      -b bits
              Specifies the number of bits in the key to create.  For RSA keys,
*             the minimum size is 768 bits and the default is 2048 bits.  Genâ
*             erally, 2048 bits is considered sufficient.  DSA keys must be
              exactly 1024 bits as specified by FIPS 186-2.


As a federal standard, DSA is somewhat hamstrung in its evolution.  On the other hand keystrength of RSA is adjustable, and defaults to "twice" the keystrength of DSA.  

Now that the U.S. RSA patent is expired, I see ssh-keygen's default key choice of RSA,2048bit as a perfectly reasonable choice.

---

### Post by tobyarnett on 2007-08-16
OK I need some help, you listed in here to upload the keys to the server ie::

```
username@ubuntu:~$ scp id_dsa.pub serverusername@192.168.1.40:./id_dsa.pub

id_dsa.pub    100% |*****************************************************|  
 614  00:00
```

What server are you talking about? The only computer in my house on linux is the one I am working with. I want to log into it from my other windows boxes through putty or secureCRT or something. 

Does my windows need the public key and if so where do i put it? What would be the file format and how would a program such as putty read it?

---

### Post by boob11 on 2007-08-19
Thanks man:lolflag:

---

### Post by phoch_00 on 2007-10-18
I have a question on this - I have set up my Ubuntu PC as  "server1" to be accessed remotely.  This works fine. I have another machine that I've also set up as  "serve2r" and generated a key. How do I add my key from server2 to server1 so that server1 can be a client to server2? I can't just copy the key over as it would overwrite my existing key. Does this make any sense???

---

### Post by Thyrth on 2007-10-18
ok thanks very helpfull post:guitar:

---

### Post by mattigras on 2007-11-16
> **Beernut said:**
> At the "Enter passphrase" prompt enter a strong password.  This password is needed to use the key so this adds some security in case your private key ever gets stolen.  **Your private key needs to be protected.**

 I pretty much only use SSH for one program (Amarok), so I want to be able to just put a launcher on my desktop with a command like "ssh -X user@192.168.2.10 amarok" and not have to open a terminal and type in a password.My 2 *buntu boxes are on a WEP protected wireless network and my router only forwards a couple hi-end ports for Ktorrent. Is there really a need for me to passphrase-protect my key if i'm only planning on SSHing from my local network?

---

### Post by jaem on 2008-01-07
> **mattigras said:**
> I pretty much only use SSH for one program (Amarok), so I want to be able to just put a launcher on my desktop with a command like "ssh -X user@192.168.2.10 amarok" and not have to open a terminal and type in a password.My 2 *buntu boxes are on a WEP protected wireless network and my router only forwards a couple hi-end ports for Ktorrent. Is there really a need for me to passphrase-protect my key if i'm only planning on SSHing from my local network?

I'm no expert, but I would say... yes.  The only reason I don't is because it's for my Palm (running Angstrom Linux) over a USB connection, and I don't care about it too much.  Oh, and if you want to know how secure WEP is, search the Ubuntu repositories for "aircrack".  Heck - if I didn't have any moral sense, I'd be messing with my neighbors' computers all the time, encrypted or not!

---

### Post by splendid on 2008-02-13
Any good links to a How To to setup ssh?

---

### Post by excbuntu on 2009-02-19
how can we have bash's ssh client point to a different *private* key? for example, say i have a private key to use on another computer and i want to use

```
ssh -L 5900:localhost:5900 pcusingadifferentkey@192.168.1.111 
```

---

### Post by elitenoobboy on 2009-03-17
ssh works properly and all for me, but whatever I do, I can't seem to be able to get the server to use passphrases. It always wants to use passwords instead, even after following the guide.

---

### Post by C4rlos on 2010-06-15
Just a little side note for us newbies  to log in to another port:

```
scp -P 34561 id_dsa.pub serverusername@192.168.1.40:./id_dsa.pub
```P < -- Uppercase as opposed to ssh it's lowercase.

---

### Post by FiVAL on 2010-07-28
This is a very good and nice thread about SSH!

Between Ubuntu and Ubuntu it's very easy...
But between my Ubuntu client and my OS X Servers I
can't get SSH with Public (RSA) Keys to work!

Does one of U, here, have an idea?

(see also: [http://ubuntuforums.org/showthread.php?t=1540611](http://ubuntuforums.org/showthread.php?t=1540611))

Thx!

---

### Post by LeFou on 2010-08-04
So I've been banging my head against this for awhile. I have an ubuntu server and need passwordless ssh from it to another machine, which runs CentOS. Have tried many times, with two users. Synopsis.

as user1 
-I did ssh-keygen, accepted defaults (rsa auth) and gave it a passphrase.
-SCP'd this to a file on machine2
-appended this to authorized_keys2 in .ssh
-logged out of machine2 and did ssh machine2

Result: It prompts me to enter the passphrase for the key.

adding -v shows:

> debug1: Unspecified GSS failure.  Minor code may provide more information
Unknown code krb5 195

debug1: Unspecified GSS failure.  Minor code may provide more information
Unknown code krb5 195

debug1: Unspecified GSS failure.  Minor code may provide more information
Unknown code krb5 195

debug1: Next authentication method: publickey
debug1: Trying private key: /home/user1/.ssh/identity
debug1: Offering public key: /home/user1/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>

If I enter the key's passphrase, it *does ssh without prompting for the remote machine password, but this is not an improvement for me. I want not to be prompted for anything. Someone said "ssh-add" would help but it just says "Could not open a connection to your authentication agent."

as user2
-same ssh-keygen, but without passphrase
-SCP'd this to machine 2 and appended it to authorized_keys2 as above
-logged out and did ssh machine2

Result: It prompts me to enter the password for this user on machine2.

with -v shows:

> 
debug1: Unspecified GSS failure.  Minor code may provide more information
Unknown code krb5 195

debug1: Unspecified GSS failure.  Minor code may provide more information
Unknown code krb5 195

debug1: Unspecified GSS failure.  Minor code may provide more information
Unknown code krb5 195

debug1: Next authentication method: publickey
debug1: Trying private key: /home/user2/.ssh/identity
debug1: Offering public key: /home/inuser2nerecho/.ssh/id_rsa
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /home/user2/.ssh/id_dsa
debug1: Next authentication method: password


Since both the half-working and not-working ones have the same "Unspecified GSS failure" I don't think that's the problem.

---

