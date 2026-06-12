---
title: "How to configure SSH so it works on both directions without password?"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Quickiez on 2012-11-01
is there anyone who can tell me how to make ssh work on both directions without a password?

---

### Post by drmrgd on 2012-11-01
Have a look at the community documentation here:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

In short, you need to create a key pair on both computers using:

```
ssh-keygen -r rsa
```

That will generate a public key (something with .pub at the end) and a private key.  You then must create a file called "authorized _keys" on both computers, and add the public key from the computers to that.  

So, let's call them computerA and computerB.  Generate a key pair on both.  The copy the .pub file from computerA to computerB at ~/.ssh/, and import the key into the "authorized_keys" file:

```
cat computerA.pub >> authorized_keys
```

Now computerA can ssh to computerB without a password.  

To get computerB to ssh to computerA without a password copy the .pub file from computerB into ~/.ssh of computerA and import it into the authorized_keys file of computerA in the same way as you did for computerB.

---

### Post by Cheesemill on 2012-11-01
It's easier to just use the ssh-copy-id command to transfer keys between machines. This way you just need to do the following on each machine:
```
ssh-keygen
ssh-copy-id user@host
```
Just hit Enter a few times after the first command to accept the defaults, and replace user and host with the correct user and host name (or IP address) for the remote machine.

---

### Post by Lars Noodén on 2012-11-01
Another way is to use [host-based authentication](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Host-based_Authentication) between the machines.  That way if you are logged into one, the other will automatically assume you are good to go.

---

### Post by drmrgd on 2012-11-01
> **Cheesemill said:**
> It's easier to just use the ssh-copy-id command to transfer keys between machines. This way you just need to do the following on each machine:
```
ssh-keygen
ssh-copy-id user@host
```
Just hit Enter a few times after the first command to accept the defaults, and replace user and host with the correct user and host name (or IP address) for the remote machine.

You mean to tell me that I've been doing this the hard way all this time!!!  LOL!  

Thanks for pointing that out.  That's definitely going to save me some effort later on down the road.  I guess I should read the documentation a little more carefully! :P

---

### Post by Lars Noodén on 2012-11-01
ssh-copy-id is just a shell script to copy the key if nothing goes wrong.  You can rummage through the source easily if you want.  It works pretty well though it is not found on all systems.  The truly portable way is to manually copy or copy-n-paste.

---

### Post by drmrgd on 2012-11-01
> **Lars Noodén said:**
> ssh-copy-id is just a shell script to copy the key if nothing goes wrong.  You can rummage through the source easily if you want.  It works pretty well though it is not found on all systems.  The truly portable way is to manually copy or copy-n-paste.

Also very good to know.  Thanks Lars!

---

