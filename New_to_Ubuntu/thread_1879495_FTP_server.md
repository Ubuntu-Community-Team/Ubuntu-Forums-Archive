---
title: "FTP server?"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by llakais on 2011-11-11
Hello,

I have a spare laptop running Oneiric at home.  It's mostly used to play movies and stuff on our TV.  What would be really nice is if there would be a way for anybody to upload a file to that computer (and its attached external hard drive) from anywhere.

What we'd really like is an ftp server that we could access from a web browser (since everyone is guaranteed to at least have one of those!).  I've found lots about using systems running Ubuntu as FTP servers, but a lot of the information is over my head.

Is there an easy (or at least not impossibly difficult) way to do what I've described?  Thanks so much for your help!

---

### Post by larrypg on 2011-11-11
Hello,  I think you need to give this a bit more thought.  Since this seems to be your home system are you aware that when you allow &quot;ANYBODY&quot; to upload anything they want to your system it will also allow them to upload any malicious bit of software they want?  It does not seem to me at least that you have enough experience to handle all the problems that this can entail.    Just a bit of a warning before you do this.

---

### Post by llakais on 2011-11-11
Hello,

I believe I've seen implementations where a username and password was required?  I was just hoping that, if such a solution exists someone might know of it and be willing to point me in the right direction.

Also, if the worst case scenario is that someone installs a malicious program and the system is rendered completely useless, then it's not a big deal.  There isn't and won't be anything of value stored on the machine.

---

### Post by JKyleOKC on 2011-11-11
> **llakais said:**
> Also, if the worst case scenario is that someone installs a malicious program and the system is rendered completely useless, then it's not a big deal.  There isn't and won't be anything of value stored on the machine.The worst case scenario is a bit different. The kiddie porn business is quite big and active, and when those folk find an open FTP server they may well take advantage of it to set up a new distribution point. Then the authorities discover that your machine is full of this material, and you're headed for a long time up the river with all your possessions confiscated.

Or the record companies may find that someone is using your server to distribute pirated music, and they sue you for more than a million dollars (no exaggeration, they've already done it at least once).

These are just two of the serious problems you can invite by running a purely open FTP server.

For my database recovery service, which involves files that are sometimes bigger than 2 GB, I have to maintain a private server that's open for any potential customer to upload to, but nobody can download anything from the "incoming" directory, nor can anyone upload anything to the "public" or "private" directories from which downloading is available. I have to manually transfer files from one directory to another before they become available, either to the public or to specific customers via the "private" directory. These are just parts of the detailed structure I must maintain on the server to protect myself from it being used in that fashion. In addition I don't allow listing of the contents of any directory except "public" so that nobody can learn who has sent what to me.

It's relatively easy to set up such a server using the ProFTPd package, but there's a lot you have to consider before doing so. For instance, most cable ISPs prohibit such servers on their networks, so you might find yourself disconnected and banned from getting back on line. Unless you dot all the Is and cross all the Ts ahead of time, you can get into serious trouble with a public server!

This isn't just paranoid fear, either. My firewall logs show an average of three to five attempts **every day** to break into my server. I use "fail2ban" to lock these out and prevent them from filling my logs, but before I did so I often saw single efforts persisting for 6 to 8 hours as the would-be intruder tried every conceivable password to gain access (to an account that did not exist, but about which the server specifically failed to send any error message out). This traffic is just part of the cost of running the server. However as ISPs implement bandwidth limits, it could get quite expensive over the course of a month.

---

