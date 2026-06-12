---
title: "Problem getting Sylpheed to work"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by Victor_Gilbert on 2015-04-01
I installed Sylpheed from the Software Centre
In the Form:                    
[LIST=1]
[*]I selected IMAP  and clicked     **Forward**. 
[*]Entered my email address     ‘[EMAIL="youruser@riseup.net"]youruser@riseup.net[/EMAIL]’. 
[*]Gave the account a name  and     clicked **Forward**. 
[*]Filled in ‘youruser’ and     ‘yourpassword’ and mail.riseup.net (for both incoming and     outgoing servers). 
[*]Selected **SSL/TLS**     for both. 
[*]Selected **Use SMTP     Authentication**. And clicked **Forward**. 
[/LIST]
 Got the email server – but not able to receive or send??? 
Nor can I find a way to re-access the details above.

Help
Victor

---

### Post by ajgreeny on 2015-04-01
You could simply delete that account and start again.

I have used sylpheed for IMAP with gmail and it always connects very quickly and sends and receives without problem.  Is the authentication set up correctly with SSL/TLS?  I think gmail does alll that part with no user input, if I remember correctly.

---

### Post by Victor_Gilbert on 2015-04-01
Thanks for reply[I]

You could simply delete that account and start again
[/I]There in lies my problem. I can go to the software centre and remove sylpheed, but after rebooting I install Sylpheed only to get the email box appearing again. I tried on their website with the same result.

How can I remove Sylpheed to [I]start again?
[/I]
Victor

---

### Post by howefield on 2015-04-01
> **Victor_Gilbert said:**
> There in lies my problem. I can go to the software centre and remove sylpheed, but after rebooting I install Sylpheed only to get the email box appearing again.

Did you remove the hidden .sylpheed-2.0 folder in your home folder.

---

### Post by ajgreeny on 2015-04-01
Yes, howefield is correct.
I didn't mean you should remove sylpheed itself, just delete the mail account you have just made by using the sylpheed **Configuration ->Edit accounts** menu.  You could then have made sure you have all the configuration correct the next time you tried to configure the account.

Unfortunately I have no way to set up a mail account for any email provider other than gmail, so I don't know what manual configuration you need in order to do that.

---

### Post by Victor_Gilbert on 2015-04-02
[                                                      [IMG]http://ubuntuforums.org/customavatars/avatar186490_53.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=186490")                                                                                     [**[COLOR=#990303][B]howefield**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]Thanks Howerfield - I'm the one on the right!
> Did you remove the hidden .sylpheed-2.0 folder in your home folder.                 
No - but I don't find any folder there.
Victor (77)

---

### Post by Victor_Gilbert on 2015-04-02
Thaks Ajgreeny
> I didn't mean you should remove sylpheed itself, just delete the mail account you have just made by using the sylpheed **Configuration ->Edit accounts** menu.  You could then have made sure you have all the configuration correct the next time you tried to configure the account.
That is the peculiar thing I only obtained a partial installation without Accounts, Help, etc.

I have an online account with BT but find something like Outlook Express so much easier to use. I'm still hoping that Sylpheed does it for me.

Victor

---

### Post by Vladlenin5000 on 2015-04-02
Outlook Express just happen to be more _familiar to you_ but it doesn't make the client easier to use. A best, it's as easy to setup and use as most if not all of the basic clients out there.
Regardless of the software you elect, setting up an email account is the same. Where and how those servers (and ports) and user authentication data goes may vary from software to software, but you'd be entering the exact same data.

Here's an example for Thunderbird: [https://we.riseup.net/riseuphelp+en/thunderbird-imap](https://we.riseup.net/riseuphelp+en/thunderbird-imap) 

Do NOT expect any email client to be able to automatically configure Riseup.net accounts. Thunderbird, the standard client in the standard Ubuntu and others, can do it for major service providers like GMail, Yahoo Mail, etc, etc.

---

### Post by Victor_Gilbert on 2015-04-03
Well well well
At last got what you all have been saying!

Edited the account 
User:                  [EMAIL="vic.soap@btinderground.com"]snipped@btinderground.com[/EMAIL]
Password           8 numbers & letters   
Protocol             POP3 
incoming and outgoing servers.   I used mail.btinternet.com 
 BUT after I requested Mail .... I got
> **Authentication failed**:
-ERR [AUTH] invalid user or password[

I must be close?

Victor

---

### Post by Vladlenin5000 on 2015-04-03
The instructions above were for IMAP and Riseup.net (from you original post). Now you show an address from [EMAIL="vic.soap@btinderground.com"]btinderground.com[/EMAIL]????? I couldn't find that domain or anything related to it...

---

### Post by Victor_Gilbert on 2015-04-04
> **Vladlenin5000 said:**
> The instructions above were for IMAP and Riseup.net (from you original post). Now you show an address from [EMAIL="vic.soap@btinderground.com"]btinderground.com[/EMAIL]????? I couldn't find that domain or anything related to it...

Thought I was just disguising my server   ...... btinternet.com ... Have an online account -less than inspiring- with a password. Is that the password I should use with Sylpheed?

Victor

---

### Post by Victor_Gilbert on 2015-04-04
Bingo

Installed Thunderbird

Thanks to everyone for their forbearance and patience.

Victor

---

### Post by Vladlenin5000 on 2015-04-04
You're welcome.

For the future keep a few notions in mind:
- Software email clients - Thunderbird, Sylpheed, ... or Microsoft Outlook (Windows), or ... - don't require special passwords. Usernames and passwords are characteristics of your unique email accounts, not of any particular software; they don't change (unless you or the service provider change them).
- The settings for inbound/outbound servers, IMAP or POP3 (when available), authentication encryption method and anything related with your email settings are also 'client agnostic', i.e., they're all the same regardless of the client you use; where and how - again - you access the addition/configuration of email accounts is what differs from one client to another, and some are more 'user friendly' than others.
Some, like Thunderbird, as you just discovered, only require as little as the email address and password - exactly the same you'd need for a web based access - to setup most of the well known services. However, it's always preferable to know where and how to add/edit email accounts in case you need it.
- For every email account that can't be configured automatically be sure to have all the settings beforehand -> Contact your service provider if you must; usually a simple Google search is enough. You may stumble with an instructions page from the service provider but for a different software, let's say for example Microsoft Outlook or Outlook Express. No problem! At some point they'll have to mention all the fields/data discussed above; you just adapt it to the software you're actually using.

---

### Post by Mike_Walsh on 2015-04-05
> **Vladlenin5000 said:**
> You're welcome.

For every email account that can't be configured automatically be sure to have all the settings beforehand -> Contact your service provider if you must; usually a simple Google search is enough. You may stumble with an instructions page from the service provider but for a different software, let's say for example Microsoft Outlook or Outlook Express. No problem! At some point they'll have to mention all the fields/data discussed above; you just adapt it to the software you're actually using.

Good advice; especially the part about making sure to have the necessary information beforehand. I'm surprised nobody's mentioned this, so I will do so:-

DO be aware that when using Sylpheed, as stated, GMail will set-up automatically (correct). However; ANY OTHER e-mail provider, you will have to enter the information manually.....and the incoming & outgoing servers are almost always different. For instance, on IMAP (remote, cloud-based folders.....as opposed to POP3, where the folders are held locally, on your machine), the outgoing server is almost always 'smtp.xxxxx', as different from the incoming server, which is 'imap.xxxxx'.

Unfortunately, I can't remember what the differences are with POP3; I haven't used it for nearly a year. But with all email clients, if you get things wrong the first time, simply delete the account details, close the client, open it again, and re-enter your a/c details again...

Works for me.

Regards,

Mike. ;)

---

### Post by bapoumba on 2015-04-05
Just a comment regarding the passwords. When using a gmail account where the 2 steps verification has been set-up, each different email client need their own password generated from the google web interface, and not the gmail account password. Not the case here, I know :)

---

