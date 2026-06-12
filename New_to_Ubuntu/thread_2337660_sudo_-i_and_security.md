---
title: "sudo -i and security"
date: 2016-09-20
forum: New to Ubuntu
---

### Post by ScorpioTiger on 2016-09-20
This might sound like a real newbie question, but here goes;

I'm looking to harden a number of Ubuntu servers. In doing so, I've disabled root access to SSH and created another user with sudo that can use a private key with passphrase to access via SSH (on a non-default port). This I have done based on numerous posts and articles on security.

Being a newbie, I've only just discovered "sudo -i". My question is, other than the fact that a brute force attack is not going to get anywhere attempting to log in as root, what benefit is there in disabling remote access for root and having a non-root user if they can elevate to root so easily anyway?

---

### Post by ian-weisser on 2016-09-20
> **ScorpioTiger said:**
> other than the fact that a brute force attack is not going to get anywhere attempting to log in as root, what benefit is there in disabling remote access for root and having a non-root user if they can elevate to root so easily anyway?

You are assuming that anyone can escalate to root. Not true - only you (the admin account) can. Nobody else can unless you grant them that power. Everyone else will get a permissions error. 

You are also assuming that using a non-default port will always be effective.
It's not. It's effective merely against attackers who have not discovered the new port (or who compromise one of your clients).  
Attacks and vulnerabilities change over time. The bad guys are clever, too.

We use layers of safeguards to protect from attacks we don't know about yet.
One of those layers is to disallow root login across ssh entirely. There is simply no need to have that kind of power accessible from the dirty, dirty internet...and you never know when some black-hat will figure how to use some zero-day exploit to bypass the key requirement, or perhaps to forge or reconstruct a key...or decrypt a sniffed key.
Another of those layers is to limit account permissions to only what the user (or application) needs...incidentally preventing a 'sudo -i' escalation when (when, not if) an account is penetrated.

---

### Post by mastablasta on 2016-09-21
i also added a whitelist of IP's from which SSH or access to server admin site is allowed. nothing perfect, just another layer.

also fail2ban with banned IP list and long ban times at second or even first attemt at connection. plus every once in a while log checks just in case.

---

