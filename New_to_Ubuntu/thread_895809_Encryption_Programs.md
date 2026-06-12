---
title: "Encryption Programs"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Generic Bond on 2008-08-20
I'd like to encrypt my hard drive so it is unaccessible from ANY hackers possible. 

Any encryption programs you guys have in mind?

---

### Post by Cypher on 2008-08-20
There are other ways of preventing unwanted access to your machine. First and foremost, you should be using a firewall (preferably hardware).

Unlike other OS' it's not easy for people to take control of your Linux machine with virus', trojans and other things. So unless you have a specific worry, you wouldn't need to bother with any sort of encryption..

---

### Post by markjensen on 2008-08-20
If you are talking drive enryption, that means you are specifically seeking protection against local attacks.   Someone is getting access to your computer hardware?

If you are trying to prevent remote attacks, an encrypted hard drive must still be 'decrypted' to boot and run, meaning your current OS sees it anyhow, so any remote holes you left in your system (SSH access to root with no password) would be able to see it all - even though you think you are safely encrypted.

I recommend you ensure you aren't having SSH/telnet/web/ftp/mail/etc services on, if you aren't needing them.  Also set up a good sensible firewall.

---

### Post by HermanAB on 2008-08-20
Run Firestarter to configure your firewall, then relax and enjoy your secure system.

---

### Post by mike2357 on 2008-08-20
Even with a firewall, I still wanted to be able to encrypt some information, such as financial records.  So I put all of my sensitive stuff in an encrypted directory.  I figure that way if someone steals my computer along with the hard drive, they can't see any of the files in the encrypted directory unless they can guess the encryption password.

There's an excellent "How To" guide here:
[http://ubuntuforums.org/showthread.php?t=148600]("http://ubuntuforums.org/showthread.php?t=148600")

Once you set up your encrypted directory, please take a look at post #12 in the above thread.  You can make the encryption and decryption as simple as pushing a button.

---

