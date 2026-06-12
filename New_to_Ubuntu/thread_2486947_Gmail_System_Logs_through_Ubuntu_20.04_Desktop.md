---
title: "Gmail System Logs through Ubuntu 20.04 Desktop?"
date: 2023-05-17
forum: New to Ubuntu
---

### Post by bhubunt on 2023-05-17
Hi,
I know some of you don't like gmail, and probably for good reason. However, perhaps one of you knows if it is at all possible to get system logs for gmail on Ubuntu 20.04 desktop?

Due to an administrative error, my personal gmail account got hijacked by Gmail Workspace, when a technician installed chrome on a work computer. The issue has been reported and will hopefully be resolved soon, when a technician returns from vacation.  But as a result, I can't install the gmail system logs app as I have lost administrative privileges to my own gmail account (!). 

Is there any way in which I could generate some kind of gmail system logs through Ubuntu 20.04 desktop?

---

### Post by TheFu on 2023-05-17
Just to clarify, this thread is about a **commercial gmail account service**, not the free accounts that almost everyone in the world (except mainland China where google stuff is blocked) have.  If you don't pay google for gmail, then you don't have access to these logs, if any.

For standard email servers, only the admin of that email server running the MTA (sendmail/postfix/exim) would have access to logs.

---

### Post by bhubunt on 2023-05-18
Hi The Fu,
Thanks as always for your reply. 

Actually, my private gmail account is not a paying email account but a _free_ personal email account. But, for some reason, when Chrome/Google Workspace was installed on my work computer, my free personal email account got hijacked, so that it is now being administered by the Google Workspace administrator. In other words, I can't even check the headers of my personal emails, etc. It is absurd, if not bizarre, because even when I work on my private computer in Firefox, which I prefer, and log into my personal gmail with my personal password, it still opens up on Google Workspace automatically...

I also have a Proton personal email account, which thankfully offers a great system logs feature with the free account. 
Thanks for explaining that Google only offers a systems log feature for paying accounts, not for free accounts. 

However, to get back to my question in post nr 1: I thought that perhaps since you can use gmail via the terminal, there might also be a way to monitor gmail activity via the Ubuntu terminal? 

Are there any extra security features to accessing gmail via the Ubuntu terminal that are not available through the use of the regular gmail app? 

For example, would it be possible to detect suspicious log-ins into one's gmail account via the terminal? The free gmail account only offers the "Details" link in the right-hand bottom of the gmail inbox page, listing IPs, but that's very clunky to get to and not entirely reliable.

P S this is a link I found on using gmail via the terminal: [https://embedjournal.com/how-to-use-gmail-from-terminal-linux/](https://embedjournal.com/how-to-use-gmail-from-terminal-linux/)

---

### Post by TheFu on 2023-05-18
IDK.  I stopped using gmail for anything when they took away IMAP for external clients by demanding oauth2 be used for credentials. I'd always been a lite-gmail user before then.

I think google broken their implementation of IMAP in June 2022. Any guides dated before then will likely not work.

I don't consider "headers" as system logs.  They are part of the message and available in any email.  Whether the mail viewer you use allows that is a different issue.  All my email clients do allow showing the headers for each message.

---

### Post by bhubunt on 2023-05-18
Agreed, the headers are different from system logs. I just mentioned them as an example of the various privileges that I no longer have for my own private free gmail account, because my account was hijacked by Google Workspace and I am no longer in control of my personal gmail. As bizarre as it sounds, I can't check the headers of my gmail!

 I am now transitioning to Proton but still have communications to take care of via gmail.

So you're saying you don't know whether it is possible to monitor gmail log-ins or do security check-ups of the gmail account via the terminal.

If anyone has any suggestions, please post instructions here.

Thanks.

---

