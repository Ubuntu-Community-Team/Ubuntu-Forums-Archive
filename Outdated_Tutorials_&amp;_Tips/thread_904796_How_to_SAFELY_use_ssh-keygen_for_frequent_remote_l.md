---
title: "How to SAFELY use ssh-keygen for frequent remote logins"
date: 2008-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by jamesrl on 2008-08-29
Recently it has appeared in the news a safety threat by using unsecured ssh keys to do password-less logins.  E.g. see: [http://blogs.zdnet.com/security/?p=1803]("http://blogs.zdnet.com/security/?p=1803")

**Problem:** During one login session, you want to use your local machine (which i will call LOCAL) to frequently login into remote machine(s) multiple times (which i will call REMOTE), without supplying a password for each login.  If you are the not the only user on the LOCAL machine that has root access on that machine (or at least trust every root user with having ssh access to every local machine that you use this method to access), you should not follow this method.  See note at bottom.

**Solution:** Use ssh-keygen with a strong passphrase, and you only need to type your passphrase the first time you use ssh from any specific machine (as it then unlocks your private key within ssh-agent).

**Step 0).** Determine a strong passphrase.  The security of this method is negated if you use a really weak passphrase (like the typical password).   See for example: [http://www.iusmentis.com/security/passphrasefaq/]("http://www.iusmentis.com/security/passphrasefaq/").  Some good techniques are using [diceware]("http://world.std.com/~reinhold/diceware.html") (to create a string of random words), which is better than a sensical sentence.  If you don't have real dice you can use random.org to generate [dice]("http://random.org/dice/?num=5").

**Step 1).**  If you had previously been using ssh-keygen without a passphrase, go to all machines you use ssh on and delete the authorized_keys file, to prevent the security threat discussed above.  
```

rm ~/.ssh/authorized_keys

```

**Step 2).** On LOCAL, go to the terminal (not as root/sudo) and type in:
```

ssh-keygen -t rsa -b 4096

```
This creates a 4096 byte (-b) rsa type(-t) private public key pair.  You can save to default location (/home/your_user_id/.ssh/id_rsa) and overwrite any previous id_rsa that had been used.  Type in your strong passphrase to the passphrase part.

**Step 3).** Append your id_rsa.pub ssh key into the authorized_keys file of REMOTE.  You can do this by
```
scp .ssh/id_rsa.pub username@REMOTE.domain.com:./id_rsa_LOCAL.pub

```
then connecting to the REMOTE machine and
```
ssh username@REMOTE.domain.com
cat id_rsa_LOCAL.pub >> authorized_keys

```
Note:  If you didn't perform step 1 you possibly might need to type in your newly create passphrase (and still type in the normal login password), while trying to ssh to the remote machine.

If you want to have more machines to ssh into from your machine LOCAL, just repeat step 3 for the new remote machine.

If you want to have more machine that you can use ssh on to connect to other remote machines, repeat step 2 & 3 (but start by already having ssh'd into the new LOCAL machine)

Reference: [http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-5.html]("http://www.sshkeychain.org/mirrors/SSH-with-Keys-HOWTO/SSH-with-Keys-HOWTO-5.html")

**Note on other root accounts.**  If other people besides yourself have root privileges on your LOCAL machine, a potential security hole opens up with using ssh-agent.  A root user has privileges to impersonate any user on any machine by simply typing:
```
sudo su user_name
```
Therefore, if you are logged in to your account, start up ssh at some time (which starts up ssh-agent and has you unlock your private-key within ssh-agent), your private-key remains unlocked within ssh-agent until you log out of the computer, so you can easily ssh into any other hosts.  Therefore after you unlocked your private-key and prior to logout, any root user logged in at the same time, can then impersonate you (sudo su user_name), and then ssh into any remote machine you have access to (that you put your public key within the authorized_keys file).  
Moral of the story: only create private-key/public-key pairs on computers where you 100% trust all root users (that is run ssh-keygen only on machines you trust all root users on).  However, if it is your personal machine (laptop / home machine) you can definitely use this method, and can use this method to connect to remote machines where there are potentially untrustworthy root users.
Reference: [http://en.wikipedia.org/wiki/Ssh-agent#Security_issues]("http://en.wikipedia.org/wiki/Ssh-agent#Security_issues")

---

### Post by yotam on 2008-12-22
> **jamesrl said:**
> 
then connecting to the REMOTE machine and
```
ssh username@REMOTE.domain.com
cat id_rsa_LOCAL.pub >> authorized_keys

```


More accurate:
```
ssh username@REMOTE.domain.com
mkdir -p ~/.ssh
cat id_rsa_LOCAL.pub >> ~/.ssh/authorized_keys

```

---

