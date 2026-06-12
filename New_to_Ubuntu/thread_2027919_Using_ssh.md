---
title: "Using ssh"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-07-17
I would like to login to my Ubu machine, from my Intel iMac, using ssh **without the need of a password**. This is a home setup I'm talking about, and I'm the only person who will ever be doing any of this, so a password isn't necessary. (I am able to login fine and carry out a small range of tasks already.)

Advice I've been given so far :
*Run: *[FONT="Courier New"]ssh-keygen -t dsa[/FONT]
[I]Make sure to provide a passphrase. Many instructions on the internet suggest using an empty passphrase.
Then, copy the generated public key into the .ssh directory in the home directory of the account on Linux that you wish to login to. You should then be able to log in without a password.[/I]

What are the steps I should carry out to 'copy the generated public key into the .ssh directory in the home directory' on my Ubu machine?

This is all to shortcut, as much as possible, the whole login process.

---

### Post by spjackson on 2012-07-17
> **Penfold1971 said:**
> 
Advice I've been given so far :
*Run: *[FONT=Courier New]ssh-keygen -t dsa[/FONT]
[I]Make sure to provide a passphrase. Many instructions on the internet suggest using an empty passphrase.
Then, copy the generated public key into the .ssh directory in the home directory of the account on Linux that you wish to login to. You should then be able to log in without a password.[/I]

What are the steps I should carry out to 'copy the generated public key into the .ssh directory in the home directory' on my Ubu machine?


If you run the above command on your Mac, then this will create the file ~/.ssh/id_dsa.pub on your Mac. (Well, I don't have a Mac but if you were going from Linux to Linux it would.)

Then on your Ubuntu machine, append those contents to the file ~/.ssh/authorized_keys (If the file does not exist then create it.)

You can do this either by copying and pasting in an editor or by other means.

---

### Post by Cheesemill on 2012-07-17
> What are the steps I should carry out to 'copy the generated public key  into the .ssh directory in the home directory' on my Ubu machine?It's easiest to just use the ssh-copy-id command to copy the keys across. Once you have generated the key just do:
```
ssh-copy-id user@host
```You'll be prompted for your password and your key will automatically be copied to the correct place on the remote host. You should then be able to connect via SSH without being prompted for a password.

For more information:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Transfer_Client_Key_to_Host](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Transfer_Client_Key_to_Host)

---

### Post by d4m1r on 2012-07-17
Pretty sure this is not possible as SSH as a protocol does not allow blank (no) passwords....Only way around this is to use a file/key and specify it in place of a password.

Is it really that big of a hassle to type it in each time to ensure security? :confused:

---

### Post by Cheesemill on 2012-07-17
> **d4m1r said:**
> Pretty sure this is not possible as SSH as a protocol does not allow blank (no) passwords....Only way around this is to use a file/key and specify it in place of a password.
This is exactly what the OP is trying to do, generate a key and copy it to the remote machine.
Therefore no password needed :)

---

### Post by Penfold1971 on 2012-07-17
> **Cheesemill said:**
> This is exactly what the OP is trying to do, generate a key and copy it to the remote machine.
Therefore no password needed :)

That's correct. I know it must seem weird but the only other person around is my wife and she wouldn't touch Terminal with a bargepole, even if she knew where to find it.  So having no password is fine here. There is no potential security problem. I just want to be able to quickly get in to the Ubu machine from my iMac and do very minimal stuff.

I've only got to these replies just now and am catching up.

I've entered [FONT="Courier New"]ssh-keygen -t dsa[/FONT] and the result is :
[FONT="Courier New"]Enter file in which to save the key (/home/rod/.ssh/id_dsa):[/FONT]

Presumably a key has been generated. (There is no mention of a passphrase.)

Is this now where I enter the command :

[FONT="Courier New"]ssh-copy-id penfold1971@host[/FONT]  ?

---

### Post by Cheesemill on 2012-07-17
Yes :)

---

### Post by Penfold1971 on 2012-07-17
Great, thanks. And I apologise for being a bit tentative here. Uber-noob! :redface:

I got a reply, after entering a blank (i.e. space) for the passphrase, like this :

```
Your identification has been saved in ssh-copy-id rod@rod-Z68MA-D2H-B3.local.
Your public key has been saved in ssh-copy-id rod@rod-Z68MA-D2H-B3.local.pub.
The key fingerprint is:
'long alphanumeric thing' penfold@penfold-Z68MA-D2H-B3
```
followed by :
```
The key's randomart image is:
+--[ DSA 1024]----+
```
followed by lines of odd symbols in a rectangular grid.

So I quit terminal on my iMac, reopened it and did the usual ssh etc. Got a password prompt, and thought I had to put in my passphrase which was a space/blank, but got a 'Permission denied' response. I had to enter my old password.

I've mucked it up somehow.

---

### Post by Cheesemill on 2012-07-17
Sorry, I hadn't noticed you had generated a DSA key instead of the default RSA key.
You need to specicy this when using ssh-copy-id:
```
ssh-copy-id -i ~/.ssh/id_dsa user@host
```Also a space isn't a blank passphrase. There is a difference between just hitting ENTER (which would be a blank passphrase) or hitting SPACE (which would be a passphrase of SPACE). Make sure you do the same thing you did when generating your key.

---

### Post by Penfold1971 on 2012-07-17
OK -before I enter that though, would it just be 'user@host' at the end of that command, or 'user@host.local' ?

My hostname for the Umac is 'penfold1971-Z68MA-D2H-B3'  (clumsy, I know)  so either

'penfold1971@penfold1971-Z68MA-D2H-B3' or 'penfold1971@penfold1971-Z68MA-D2H-B3.local' ?

---

### Post by Cheesemill on 2012-07-17
It shouldn't matter, they both resolve to the same IP address.

---

### Post by Penfold1971 on 2012-07-17
Thanks.

Unfortunately, I get this result now :

```
/usr/bin/ssh-copy-id: ERROR: No identities found
```

I can't believe what a mess I'm making of this.

---

### Post by markbl on 2012-07-17
> **Cheesemill said:**
> This is exactly what the OP is trying to do, generate a key and copy it to the remote machine.
Therefore no password needed :)
The terminology is what is confusing people here. A "password" is what is configured on your linux login account. A "passphrase" is what you type to unlock your private ssh key. A password should not be blank but a passphrase can be, although you typically only need enter your passphrase once thereafter it is cached on your client by your keychain while you remain logged in at that client.

---

### Post by Penfold1971 on 2012-07-18
Since I seem to have made a hash of this, is it possible to go through the process again, thus cancelling and overwriting the previous attempt?

I am still able to ssh into the Umac OK, but only by using my original password.

---

### Post by Cheesemill on 2012-07-18
Yes you can start again. First delete the previous keys:
```
 rm ~/.ssh/id*
```
Then create a new key:
```
 ssh-keygen
```
Just hit ENTER a few times to create an RSA key in the default location with a blank passphrase.
Then copy your key to the remote host:
```
 ssh-copy-id user@host
```
You need to enter your login password for the remote host to copy the key accross.
You should then be able to SSH to the remote host without a password:
```
 ssh user@host
```


I've just done this on my machine to test that it works, here's what the process should look like:
```
rob@precise:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/rob/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/rob/.ssh/id_rsa.
Your public key has been saved in /home/rob/.ssh/id_rsa.pub.
The key fingerprint is:
7f:ec:4d:36:99:67:c8:1a:70:87:08:9c:64:30:46:30 rob@precise
The key's randomart image is:
+--[ RSA 2048]----+
|    Eo=.o        |
|     o = .       |
|        +        |
|         . . .   |
|        S o o .  |
|         . + o + |
|          . + O o|
|           o * + |
|            o .  |
+-----------------+
rob@precise:~$ ssh-copy-id rob@192.168.1.100
rob@192.168.1.100's password: 
Now try logging into the machine, with "ssh 'rob@192.168.1.100'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

rob@precise:~$ ssh rob@192.168.1.100
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

 System information disabled due to load higher than 1.0

0 packages can be updated.
0 updates are security updates.

Last login: Wed Jul 18 11:13:38 2012 from 192.168.1.124
rob@virtualmin:~$ 
```

---

### Post by Penfold1971 on 2012-07-18
Hah! Just as I'd started to enter the first command from your post, we had a power cut!! Welcome to the 21st Century ... excuse my cynicism ;)

After we were blessed with a return to power, I tried the first command on my iMac and got this :

```
penfolds-imac:~ penfold$ rm ~/.ssh/id*
rm: /Users/penfold/.ssh/id*: No such file or directory
penfolds-imac:~ penfold$
```

I the ssh-ed into the Umac and got :
```
penfolds-imac:~ penfold$ ssh penfold@penfold-Z68MA-D2H-B3.local
Warning: Permanently added the RSA host key for IP address '10.0.1.4' to the list of known hosts.
penfold@penfold-z68ma-d2h-b3.local's password: 
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

Last login: Wed Jul 18 11:44:21 2012
```

Presumably the reference to 10.0.1.4 is down to having had a power cut (?) .

I tried the first command agin, this time in the Umac and got :
```
penfold@penfold-Z68MA-D2H-B3:~$ rm ~/.ssh/id*
rm: cannot remove `/home/penfold/.ssh/id*': No such file or directory
penfold@penfold-Z68MA-D2H-B3:~$ 
```

At this point I feel as though I'm haunted!

I'm sorry you're witness to all this. ](*,)

---

### Post by Cheesemill on 2012-07-18
If the rm command fails then don't worry, it just means that there is nothing to delete.

Just carry on with the rest of the commands and you should be OK.

All of the commands should be run from your local machine, you don't have to run them on the remote host.

---

### Post by Penfold1971 on 2012-07-18
Cheesemill, I swear I followed your advice to the letter (unless I'm going completely insane ... )

It didn't work, so I tried it again. This is the result as far as the command for copying the key to the remote host : 

```
penfolds-imac:~ penfold$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/penfold/.ssh/id_rsa): 
/Users/penfold/.ssh/id_rsa already exists.
Overwrite (y/n)? yes
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/penfold/.ssh/id_rsa.
Your public key has been saved in /Users/penfold/.ssh/id_rsa.pub.
The key fingerprint is:
56:91:56:bc:3d:4d:95:1a:69:00:06:5d:e9:ba:9b:36 penfold@penfolds-imac.local
The key's randomart image is:
+--[ RSA 2048]----+
|       .oo+*+ . +|
|        ..oo.+ ..|
|         .o .ooo |
|         . ...o .|
|        S .    . |
|       . .       |
|          .      |
|         E.      |
|        .oo      |
+-----------------+
[COLOR="Red"]penfolds-imac:~ penfold$ ssh-copy-id penfold@penfold-Z68MA-D2H-B3
-bash: ssh-copy-id: command not found
rod-fryers-imac:~ penfold$ ssh-copy-id penfold@penfold-Z68MA-D2H-B3.local
-bash: ssh-copy-id: command not found
penfolds-imac:~ penfold$ [/COLOR]

```

I can't see what I've done wrong.  :confused:
This is a marathon! I can't thank you enough for persevering with me here.

---

### Post by spjackson on 2012-07-18
> **Penfold1971 said:**
> [COLOR=Red]penfolds-imac:~ penfold$ ssh-copy-id penfold@penfold-Z68MA-D2H-B3
-bash: ssh-copy-id: command not found
rod-fryers-imac:~ penfold$ ssh-copy-id [EMAIL="penfold@penfold-Z68MA-D2H-B3.local"]penfold@penfold-Z68MA-D2H-B3.local[/EMAIL]
-bash: ssh-copy-id: command not found
penfolds-imac:~ penfold$ [/COLOR]
[/CODE]I can't see what I've done wrong.  :confused:
This is a marathon! I can't thank you enough for persevering with me here.
Well, what you did wrong was to ask Ubuntu users how to work your imac, and you've got a Ubuntu answer, not an imac one. ;-)

The Mac doesn't have ssh-copy-id.

You can install it. Google for "ssh-copy-id mac" for examples of how to do that.

Or you can edit ~/.ssh/authorized_keys as I said yesterday, but now you have switched to rsa (rather than dsa in your original post) so the file to extract the key from is now ~/.ssh/id_rsa.pub.

Or you can use this command.
```

cat ~/.ssh/id_rsa.pub | ssh user@machine "mkdir ~/.ssh; cat >> ~/.ssh/authorized_keys"

```See [http://www.commandlinefu.com/commands/view/188/copy-your-ssh-public-key-to-a-server-from-a-machine-that-doesnt-have-ssh-copy-id](http://www.commandlinefu.com/commands/view/188/copy-your-ssh-public-key-to-a-server-from-a-machine-that-doesnt-have-ssh-copy-id)

---

### Post by Penfold1971 on 2012-07-18
> **spjackson said:**
> Or you can use this command.
```

cat ~/.ssh/id_rsa.pub | ssh user@machine "mkdir ~/.ssh; cat >> ~/.ssh/authorized_keys"

```See [http://www.commandlinefu.com/commands/view/188/copy-your-ssh-public-key-to-a-server-from-a-machine-that-doesnt-have-ssh-copy-id](http://www.commandlinefu.com/commands/view/188/copy-your-ssh-public-key-to-a-server-from-a-machine-that-doesnt-have-ssh-copy-id)

I think if I'd known how much trouble I was going to cause you guys I wouldn't have started all this :oops:

Just so I *really* know (!) what I'm to do,

(a) the command above - is it in place of creating 'ssh-copy-id' on the iMac?

(b) if I enter that command, above, is the user@machine to do with the Ubuntu machine or my iMac?

After all this is over, I'm not going to change anything for a while ...

---

### Post by Penfold1971 on 2012-07-18
Forget that last despairing post. It seems to have worked, by some miracle, this time.

My God!

Major thanks to you both, spjackson and Cheesemill.

---

