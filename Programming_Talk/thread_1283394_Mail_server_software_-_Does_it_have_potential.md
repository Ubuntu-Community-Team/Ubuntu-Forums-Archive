---
title: "Mail server software - Does it have potential?"
date: 2009-10-05
forum: Programming Talk
---

### Post by BluShift on 2009-10-05
Hi all. I figured I'd post this here because frankly I don't know where else it would go.

I started off by developing an all-around mail client/server/transfer agent system; not standards based or anything; just a simple system for the sake of coding. I'm relatively new to Python, so what I have isn't spectacular, but I think I may have hit on something interesting. This is what I have developed; the basic code for the sending of these e-mails, and most importantly a server/MTA to accept and spool them into various mail folders based on certain parameters. I use SCP to move the emails, and the emails are formatted as regular text files; I just use a different file extension for the hell of it.

Now, originally this was set up to be a running on all machines who planned to use the service; only thing is for SCP to work, the person sending the mail has to know the password and UN of the other computer. But obviously that compromises security on the machines in question. So what I've thought is that I could tweak the MTA/server app to run on one machine and just spool mail into seperate email folders for different people (accesible through an Apache server (http) or just through SCP again) and such, thereby having the only compromised password being the servers, and that can be a user account (on the server) that only has read/write permission for the softwares' folder (so it doesn't compromise much) /rant

So this is my question: Is something like this that is based on SCP and text-files worth developing? Does it have potential? The thing I noticed is that it is very open, and very, very customizable with little work because it's so simple.

Second, does anyone know of a better way than SCP? Because needing to enter the UN and PW everytime is A: tedious and B: kind of hacked together (understatement). I was thinking SFTP, but even then it's difficult.

Thanks much for reading my whole rant, and I thank you for any help you can offer or any words of advice :)

--Alex

---

### Post by wmcbrine on 2009-10-05
No, IMHO, a system not based on standards is not worth developing.

---

### Post by CptPicard on 2009-10-05
What does it do better than email? Besides considering how hard email servers are to secure (and the have been under development for ages), this sounds like a security hole and/or just begging for abuse...

---

