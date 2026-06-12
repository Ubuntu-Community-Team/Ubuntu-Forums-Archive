---
title: "Unable to authenticate in any way after editing the SSH Daemon config file (PuTTY)"
date: 2019-06-09
forum: New to Ubuntu
---

### Post by nicky90 on 2019-06-09
Hi everyone,

I've been searching for 2 days now and trying a lot of manipulations without success. I don't know what to do anymore except to post my issue here.

Some useful informations before I start to explain :

- My OS : Windows 10
- VPS server : Ramnode (Ubuntu 16.04 64-bit)
- Emulator : PuTTY (PuTTYgen for keys generations)
- My first language is French, I apologize if my English is not correct :-#

OK, here is my issue :

I firstly authenticated myself with the user "root" and my password. Then,I created a new user as "ubuntu" and I installed SSH key authentification. All was running good and I could auth. as "ubuntu" with my SSD key instead of the password.
I used these commands one line at a time :

```
adduser ubuntu
usermod -aG sudo ubuntu
su ubuntu
sudo -S true
```

Then, the tutorial asked me to enter this command but it didn't apply :

```
cd && mkdir .ssh && chmod 700 .ssh && cd .ssh && sudo cp /root/.ssh/authorized_keys . && sudo chown ubuntu authorized_keys && chmod 644 authorized_keys
```

I thought it didn't apply because it was reserved to Vultr (as mentioned in the tuto), and since the authentification with SSH key was already running good, I didn't pay much attention. (I precize that I also configured this on Vultr in the same way and I met no issue, everything is running good on this one.)

Then, according to the tutorial, I edited the SSH Daemon config file to lock down the server :

```
sudo nano /etc/ssh/sshd_config
```

Still according to the tutorial, I found the following lines and change them to the following settings (with removing the "#") :

```
PermitEmptyPasswords no
PasswordAuthentication no
ChallengeResponseAuthentication no
PermitRootLogin prohibit-password
UsePAM no
```

After having saved the modifications, I restarted the SSH Daemon in order to apply these new settings :

```
sudo systemctl restart sshd.service
```

And here is where my issue begin. After that, I've never been able to authenticate again. Neither with root, neither with ubuntu, neither with SSH key or password... Nothing works, even when editing the PuTTY configurations, I just can't access to the commands anymore.

Here is the error message I have :

```
Server refused our key
```

PuTTY Fatal Error : No supported authentification methods available (server sent: publickey)

I think my mistake is that I haven't allowed enough permissions to my ubuntu user (because the command for Vultr didn't apply with Ramnode). And since I have locked down the server by editing the SSH Daemon config file, the root user has restricted permissions now...

Is my diagnostic correct ? What solutions do I have ? I can give more precisions on the other commands I used if needed.

Thanks by advance to anyone who will try to help me ;)

---

### Post by kevdog on 2019-06-11
Can you ssh at localhost?
ssh -vvv <user>@localhost  <--- The -vvv option will give a lot of output and it might shed light on the problem.  I'm betting its a permissions issue on either the .ssh directory or the authorized_keys file

---

### Post by nicky90 on 2019-06-11
Hi, thanks for your answer :smile: Yes, I'm now pretty sure it's a permissions issue on the authorized_keys file.

I tried this :
```
login as: ssh -vvv ubuntu@localhost
```
And this :
```
login as: ssh -vvv root@localhost
```
But I still have this message :

[COLOR=#000000]PuTTY Fatal Error : No supported authentification methods available (server sent: publickey)[/COLOR]

---

### Post by kevdog on 2019-06-12
Ok the root login method probably wont work because of your sshd_config file

Focus on the normal user.  Within the ~/.ssh directory you should have an authorized_keys file.  What are the permissions on the authorized_keys files and who holds owner/group privileges? 

(usually in terms of debugging -- I first ensure I can ssh with use of a password first then move onto the use of keys -- passwords will show if there is an underlying problem with the ssh server)

---

### Post by nicky90 on 2019-06-12
Sorry but I don't understand how I could inspect the authorized_keys file if I can't even login in PuTTY ? I can't apply any command...

But what I know is that I didn't add any key in the authorized_keys files and it's the reason why I can't login anymore. And since I have prohibited-password and lock down the server in SSH Daemon, I have no option but to connect with my key...that I didn't give permission ](*,)

---

### Post by kpatz on 2019-06-12
Does your VPS allow console login, or some other way in via a control panel?  You may need to get into it that way so you can fix your SSH setup.

Next time, test your keys before disabling passwords.

And stay logged in to a session while opening another to test.

---

### Post by TheFu on 2019-06-12
Not that it helps Windows users, but on Unix, there's a tool to push the public key to the correct location, **ssh-copy-id**.  Makes setting up key-based ssh access 2 commands.  ssh-keygen and ssh-copy-id.

ssh is a core security tool, so it is picky about file security. Permissions for the files:
```
~/.ssh$ ll
total 100
drwx------  ./
drwx--x---  ../
-rw-------  authorized_keys
-rw-------  config
-rw-------  id_ed25519
-rw-r--r--  id_ed25519.pub
-rw-------  id_rsa
-rw-r--r--  id_rsa.pub
-rw-------  known_hosts

```
That is a mix of client and server files, so don't worry if your server doesn't have them all. Also note that the ~/.ssh/ directory permissions must be 700.  The easy way to think of this is that only the .pub files should be read by group and others. Everything else is locked for owner access only.

If you don't have ssh-copy-id, then moving the public key file over needs to be done in binary mode.  If you copy/paste it, newlines are often added, which must be removed.  Each host signature is a single line.

Unix-to-Unix ssh is so much easier and many things "just work."

---

### Post by kevdog on 2019-06-13
@nicky90

You don't have anymore access to the ssh server?
I was under the impression you controlled both the client and server machine.

---

### Post by nicky90 on 2019-06-15
Hi all ! Thanks for your help, I finally manage to connect in my VPS console and to unable the password authorisations =d>[-o<

So I can now loggin again normally with my username or root and my password. However, the server still refuse my authentification key when I try to connect with. I used these commands to authorise my key :

```
mkdir ~/.ssh
chmod 0700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 0644 ~/.ssh/authorized_keys

sudo vi ~/.ssh/authorized_keys

COPY/PASTE THE KEY

ESC

:w

:q

```

And it works when I set up this with another server, but not with the servers I had to manage with the console. I tried with my previous key and I tried by deleting my previous key and create/authorise a new key but neither of the two ways work...
:lolflag:

---

### Post by TheFu on 2019-06-15
> **TheFu said:**
>  If you copy/paste it, newlines are often added, which must be removed.  Each host signature is a single line. 

Did you see this and handle it?
Also, please see the required permissions above, post #7, for all the files in the directory.

---

### Post by kpatz on 2019-06-15
You don't need sudo to edit ~/.ssh/authorized_keys.

It's probably a permissions or ownership issue.  What's the output of **ls -la ~/.ssh**?

Also when you vi authorized_keys, there should be no ^M (carriage return) at the end of the line.  And when you create the key with puttygen, you're copying the public key right?  The one that looks something like:```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIExTT2OLJ3t8Y3UrNONCwwqO3xLfxaAOXtAm2nWqJ4F1 ed25519-key-20190615
```You'll find it at the top of the Puttygen window, where it says "Public key for pasting into OpenSSH authorized_keys file".

(Note that I created an ed25519 key here for this example... if you used RSA the key would start with ssh-rsa and be a lot longer.  ed25519 keys are more secure).

Are you using the most recent version of PuTTY?  0.71 is the current version.

---

### Post by nicky90 on 2019-06-15
OK, I found it out. Sometimes when I copy/paste the key, the first letter of the key ("s" for SSH) isn't pasted for a reason that I don't understand. It's tricky but at least very simple to solve, just have to pay attention to it.

Thank you very much to all for your help !

---

### Post by kpatz on 2019-06-15
Cool beans.  Don't forget to mark the thread "solved" by clicking Thread Tools at the top of the thread.

---

