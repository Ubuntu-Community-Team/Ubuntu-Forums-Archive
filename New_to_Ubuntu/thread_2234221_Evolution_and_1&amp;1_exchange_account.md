---
title: "Evolution and 1&amp;1 exchange account"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by gaz3 on 2014-07-13
Hi,

I've just installed Ubuntu for the first time. I've got most stuff working so far, but I've got stuck trying to connect to a 1and1 MS Exchange 2013 email account using Evolution.
I've had a look around these forums and google in general, but can't find a solution.

I've installed evolution and evolution-ews plugin ok. The account set up seems to go ok, but the authentication always fails. 
I can connect to the account using Outlook on Windows, and via my android phone ok. Is there something I'm missing?

I could probably connect using IMAP, but I'd prefer the exchange connector so I have full access to calendar and address book.
I'd be interested to know if anyone has managed to do this successfully before?

Thanks

---

### Post by WirezFree on 2014-09-11
Hi,

If you are still around.?

I also use 1&1 for Hosted Exchange account.
Unless something's changed.?, I've been looking for 6 months
It appears it is not possible to use Evolution to connect to 1&1 Hosted Exchange.
From what I've read,
It is something to do with how Exchange is used in a Hosted environment, and how Authentication is not working

It's sad that I can enter 3/4 items on an Android Phone/Tablet, and it all works perfectly... But not on Linux.

So you are either re-signed to:
1. OWA
2. Try to get Outlook running in Wine, but you need Outlook 2010/13 for 1&1
3. Run Windows/Outlook in VBox/VMWare
4. Run Android in VBox... Big Screen

Dave

---

### Post by P_THE_AWESOME on 2014-09-11
**I would strongly recommend [DavMail]("http://davmail.sourceforge.net/").** From personal experience, I can say that it is AWESOME. It acts as a gateway on your local computer that converts Exchange into IMAP (receive messages and all folders), POP (receive messages in a single folders), SMTP (send messages), LDAP (for directory listings) CardDAV (view and modify contacts), and CalDAV (view and modify Calendars).

[LIST=1]
[*]Of course, if you service is already offering any of these protocols (IMAP, POP, SMTP, LDAP, CardDAV, and CalDAV) use the official one and not the DavMail one - it will be much faster and smoother. Be sure to disable services in DavMail that you aren't using to conserve RAM and CPU, however, it runs pretty calmly anyways. 
[*]You will probably have to login with your DOMAIN too; not just your username. 
[*]Lastly, while DavMail may not *server* SSL, it does *receive* SSL from the Exchange server. And since I assume that you will not be enabling remote connections, the DavMail server will never leave your own computer and therefore doesn't need to be encrypted. 
[/LIST]
     I would also recommend [Thunderbird]("https://www.mozilla.org/en-US/thunderbird/") + [Lightning]("https://www.mozilla.org/en-US/projects/calendar/") (for fantastic calendar and tasks support) + [SOGo Connector]("http://www.sogo.nu/downloads/frontends.html") (for CalDAV and CardDAV support) + [MinimizeToTray]("https://addons.mozilla.org/en-US/thunderbird/addon/minimizetotray-revived/").

[LIST]
[*][DavMail Linux setup instructions]("http://davmail.sourceforge.net/linuxsetup.html") 
[*][Thunderbird IMAP/SMTP instructions]("http://davmail.sourceforge.net/thunderbirdimapmailsetup.html") 
[*][Thunderbird Calendar instructions]("http://davmail.sourceforge.net/thunderbirdcalendarsetup.html") 
[*][Thunderbird Directory instructions]("http://davmail.sourceforge.net/thunderbirddirectorysetup.html") 
[*][Thunderbird Contacts instructions]("http://davmail.sourceforge.net/thunderbirdcarddavsetup.html")
[/LIST]
 **I'm pretty sure this can all be done with Evolution too since DavMail uses all standard protocols.** I personally prefer Thunderbird.

---

### Post by WirezFree on 2014-09-12
> **P_THE_AWESOME said:**
> **I would strongly recommend [DavMail]("http://davmail.sourceforge.net/").** From personal experience, ....
>> SNIP <<
 **I'm pretty sure this can all be done with Evolution too since DavMail uses all standard protocols.** I personally prefer Thunderbird.


Hi [SIZE=2][COLOR=#000000]P_THE_AWESOME,[/COLOR][/SIZE]

[SIZE=2][COLOR=#000000]Thanks for all the info, I have been down all these routes, unfortunately none of these get past authentication with Exchange Server.[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]In my limited understanding, because Exchange is hosted in a multi tennancy way, there is an an extra layer of authentication.[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]There is another server(proxy) configured withinin MS Outlook, and it uses NTLM, there are no config options for this in any other Clients.[/COLOR][/SIZE]
[SIZE=2][COLOR=#000000]So none of the existing methods work with **Hosted** Exchange.

Thanks... David[/COLOR][/SIZE]

---

### Post by gaz3 on 2014-09-13
Thanks for the replies

So does this mean that (a) there are no linux mail clients that can handle this configuration, and (b) even if I shifted to another hosted exchange provider, I wouldn't be able to get this to work?

---

### Post by WirezFree on 2014-09-13
> **gaz3 said:**
> Thanks for the replies

So does this mean that (a) there are no linux mail clients that can handle this configuration, and (b) even if I shifted to another hosted exchange provider, I wouldn't be able to get this to work?

From everything I've tried & read, "NO".
it appears this is how Exchange authentication needs to operate in a Hosted environment.

I would love for somebody to come forward and say "it can be done", but I fear not.

At this moment I'm stuck with clunky OWA and a Virtualbox with Windows & Outlook 2010.

Dave
(1&1 Hosted Exchange)

---

### Post by gaz3 on 2014-09-13
That's disappointing.
I suppose the latest webmail for outlook isn't too bad, so that's probably the best solution for now

---

