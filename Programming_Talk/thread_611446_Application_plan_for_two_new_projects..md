---
title: "Application plan for two new projects."
date: 2007-11-12
forum: Programming Talk
---

### Post by SomeLuser on 2007-11-12
NOTE: I'm not a developer, but I read Wikipedia, so I have some knowledge of... the stuff I'm talking about here. ;-)

I was reading an article in a local newspaper about laptop theft, and it mentioned some commercial software which helped track thieves by reporting to a server every time it logged on to the mighty Internet, which would presumably leave the server with an IP address to be WHOIS'd at will.

Since I'm interested in the public good, I considered possibilities for a Free Software application of a similar nature. My plan is this:
A daemon to be invoked around boot-time or login-time which would send an e-mail to a specified e-mail address (through POP3) every time its host computer obtained a new IP address, since an entirely new IP address could quite possibly mean the host computer has changed location. It would have to include a utility for configuration, such as the target e-mail address, so the number of times it would be allowed to send a e-mail a day could be configured along with that.

Because this is to be a free project, it would raise privacy concerns (in my opinion) if a team of developers or this free project were reviewing reports of stolen laptops and their respective IPs, so I chose private e-mails.

However, if this application is to be cross-platform (due to the relatively small number of GNU/Linux-running laptops compared to other OSes), reliance on one e-mail sending method probably wouldn't work out as efficiently as, say, the SQLite approach (bundling the utility with every copy of the application).

Thus, I also propose building a library for the purpose of sending mail, using the SQLite architecture:
A library to control the database file (in this case a text file with the inbox, outbox, etc...)
The database file
Other applications call on the library, and the library executes the commands (SQL calls) through a link to the database file

So we could take the SQLite codebase (or use it as a reference) to build a control library with some of the following procedures:

Adding the ability to communicate with POP3 servers

Replacing the SQL commands with something like:
sendmail(sender@example.com, password; [email]recipient@example.net[/email]; title; body <br/> of the e-mail <br/> message )

checkmail(mailbox@example.net; password)


We could also modify the database file to reflect its e-mailbox status, so a typical file for one person could look like this:

(beginning)
Mailite 0.0.1

---inbox---<recipient@example.net>
{(1)
SENDER=sender@example.com
TITLE="Hello, World!"
DATE=(1-25-2002; 00:10:01)
BODY:(
Hi, I'm just testing this e-mail service my friend told me about!
)
}
{
{(2)
SENDER=sender@example.com
TITLE="Great"
DATE=(1-26-2009; 00:15:21)
BODY:(
> I got your mail just fine.
I'm happy to see this service works OK!
)
}
---outbox---<recipient@example.net>
{(1)
SENDER=recipient@example.net
TITLE="Yes"
DATE=(1-25-2009; 10:31:47)
BODY:(
> Hi, I'm just testing this e-mail service my friend told me about!
I got your mail just fine.
)
}
(end)


For more than one mail profile, there could be multiple inboxes and outboxes as needed. The password would be stored by the client (or typed in each time mail is sent or recieved, if needed), so I didn't include that in the file.


What do you think of this plan?

---

### Post by LaRoza on 2007-11-12
I don't see how that would be useful. My laptop has a built in chip that can be used to deactivate the hardware, but I highly doubt if someone where to steal my laptop (perish the thought) they would be able to log on. That is what passwords are for. If they can't log on, they would have to either crack it (I doubt it) or just install a new OS, which is what I would do if I stole a computer. Actually, I would take it apart and use the parts so the computer itself wouldn't exist.



The software would have to be independent of the OS, which means a "Linux version" isn't needed any more than a "Windows version".

The intergrated chip is best for that, and having a good defense: [img]http://tbn0.google.com/images?q=tbn:U-rQbNTHujDscM:http://www.the-gadgeteer.com/assets/dreamcheeky-usb-6.jpg[/img] I just received it today, that is why I brought it up.

> 
A daemon to be invoked around boot-time or login-time which would send an e-mail to a specified e-mail address (through POP3) every time its host computer obtained a new IP address, since an entirely new IP address could quite possibly mean the host computer has changed location. It would have to include a utility for configuration, such as the target e-mail address, so the number of times it would be allowed to send a e-mail a day could be configured along with that.
At boot time? That is a security risk, especially if it is communicating to a remote source. IP addresses are easy to change, and often change everytime a laptop connects, through DHCP. Getting the IP address wouldn't help, with IPv6, there are 5^1028 IP addresses for 6.5 million people. Getting one wouldn't help.

-EDIT That IP statistic is the number for *each* of the 6.5 billion people, the total number is much larger, 2^128 which is about 3.4^1038

---

### Post by SomeLuser on 2007-11-13
Those are some excellent points. Any opinions about the e-mail library idea?

---

### Post by CptPicard on 2007-11-13
> **SomeLuser said:**
> Any opinions about the e-mail library idea?

It seems very confused indeed. Why bring so much of SQLite into this? It's an embeddable SQL database engine. It has nothing to do with email.

Sending mail through SMTP (not POP3, that's a mail fetching protocol) is a known quantity and you can implement that cross-platform very simply. No need for anything fancy. In particular there is no need for some local mailbox format unless you're also reading and storing mail, and for that, I don't think you need to start reinventing the wheel, just use what is out there.

The most dangerous idea is the marriage of the two -- if you feel that your stolen laptop needs to call home with some sort of full email stack with mail database files that even probably include mail server usernames and passwords, think again :)

---

### Post by SomeLuser on 2007-11-13
Oh, OK.

I didn't realize what SMTP is for.
I thought the whole mail thing might be useful for embedded devices, and that SQLite already seemed to be doing something similar with SQL. Maybe it wasn't such a good idea ;-)

---

