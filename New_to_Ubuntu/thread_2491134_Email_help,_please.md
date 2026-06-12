---
title: "Email help, please"
date: 2023-09-27
forum: New to Ubuntu
---

### Post by artisanpens on 2023-09-27
Hi,

I am setting up a new Ubuntu 23.04 x64 server and have got stuck on emails.

I have install Postfix and can receive emails into /var/mail/{user} mailboxes.

I have also installed Courier IMAP and Courier POP3, both of which test OK.

My problem is how to read messages with a mail client, Thunderbird (102.15.1) preferably.

Is there a simple guide on how to achieve this anywhere?  

Thanks in advance

---

### Post by Rex Bouwense on 2023-09-27
Here is a place for you to start.  [https://support.mozilla.org/en-US/products/thunderbird/emails-thunderbird/set-up-email-thunderbird](https://support.mozilla.org/en-US/products/thunderbird/emails-thunderbird/set-up-email-thunderbird)
It has become a relatively simple process.

---

### Post by artisanpens on 2023-09-27
> **Rex Bouwense said:**
> Here is a place for you to start.  [https://support.mozilla.org/en-US/products/thunderbird/emails-thunderbird/set-up-email-thunderbird](https://support.mozilla.org/en-US/products/thunderbird/emails-thunderbird/set-up-email-thunderbird)
It has become a relatively simple process.

Thanks, I know how to set up Thunderbird, what I don't know is how to set-up the server in a way that Thunderbird can access it.

---

### Post by SeijiSensei on 2023-09-27
If it's running an IMAP server, it should be available immediately. Create an account in Thunderbird using your email address, then use the "manuial" configuration to point it to your server's IMAP and SMTP ports.

One quick test if you support unencrypted IMAP on port 143 is this:
```

$ telnet your.server.name.or.ip 143

```
You should get back the server's IMAP banner. I use dovecot rather than Courier, so this is what I get:
```

telnet name_of_server 143
Trying 192.168.100.100...
Connected to name_of serrver.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot ready.

```

---

### Post by TheFu on 2023-09-27
I've always used dovecot for IMAP/S connections and haven't used POP3 since the dialup days in the mid-90s.

Thunderbird supports the standards.  In general, those are, 

For getting email:
IMAP on port 143
IMAPS on port 993
POP3 port 110
POP3S 995
Those are all TCP.

I ujse SSL/TCP with a normal password under the thunderbird "Security Settings" for my imap server.

For sending email, your MTA/SMTP server needs to be setup for 465/tcp or 587/tcp for clients.  Typical MTAs are postfix, sendmail, exim4.  You'll need to ensure that your ISP/VPS provider allows sendin and receiving email if you host your own email server.  Most residential ISPs block server-to-server MTAs from working and a quality VPS will require a special request and perhaps some govt ID and 3 messages for "why" before they will enable it to your VPS IP.  I had to go through that last June after years of having a business connection that assumed we'd all be hosting our own email.

For outgoing email, my mail server uses the full email address, plus the FQDN for the server and listens on port 587/tcp. Again, a normal password is used, but with STARTTLS for the connection.

Without an MTA, IMAP and POP3 are extremely limited, since they won't get any inbound messages and your clients won't have anywhere to send email.

My email stack is a Zimbra Server, but that's overkill (and a hog) for most people. I'm just addicted to the enterprise calendaring it provides and the advanced, per email, email filters, tagging, and folder management. Zimbra uses postfix for the MTA, which is what I've been using since around 1995 for all my email servers. Because Zimbra is so complex and mostly a turn-key solution, I run an email gateway through which all inbound and outbound SMTP traffic traverses. It only handles SMTP. No imap/pop3 and no direct client emails. This is a bog standard Debian 12 system. It doesn't usually hold any data. It is just a security enforcement system and if Zimbra is down, it is a store and forward later system.

Anyway, Thunderbird honors standards, so as long as your servers also are configured for those standards, there shouldn't be any issues.

If this isn't sufficient information, I suspect there are things about running servers that we have assumed, but you haven't done.  Things like having DNS setup and static IPs.  Sometimes you may need to have split DNS - so internal systems get 1 answer, but externally, a completely different answer is provided.  I solve that by not allowing any external access by client systems.  To gain access to their email accounts, users have to use our VPN to get onto a known subnet first, then they get client access to all sorts of systems, including email.

---

### Post by artisanpens on 2023-09-28
> **SeijiSensei said:**
> If it's running an IMAP server, it should be available immediately. Create an account in Thunderbird using your email address, then use the "manuial" configuration to point it to your server's IMAP and SMTP ports.

One quick test if you support unencrypted IMAP on port 143 is this:
```

$ telnet your.server.name.or.ip 143

```
You should get back the server's IMAP banner. I use dovecot rather than Courier, so this is what I get:
```

telnet name_of_server 143
Trying 192.168.100.100...
Connected to name_of serrver.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE STARTTLS AUTH=PLAIN] Dovecot ready.

```

Thanks, I get the correct response from telnet {domain} 143, 25, 2525, 143, 110, 993, 995.

So don't think the problem lies there

---

### Post by artisanpens on 2023-09-28
Thanks for that detailed reply.

I think I have narrowed it down to the ssl certificate

Sep 28 17:09:09 {domain} dovecot[23339]: imap-login: Disconnected: Connection closed (no auth attempts in 0 secs): user=<>, rip={myIP}, lip={server IP}, session=<h9CbsGwGxdhaTiX2>
Sep 28 17:10:09 {domain} dovecot[23339]: pop3-login: Error: Failed to initialize SSL server context: Can't load SSL certificate (ssl_cert setting): The certificate is empty: user=<>, rip={myIP}, lip={server IP}, session=<FJU2tGwG2NhaTiX2>


Sep 28 17:10:09 {domain} dovecot[23339]: pop3-login: Disconnected: TLS initialization failed. (no auth attempts in 0 secs): user=<>, rip={myIP} lip={server IP} session=<FJU2tGwG2NhaTiX2>

Those 2 log-in attempts were from an old email client running on another machine with settings to my old server.

When I attempt to configure Thunderbird with a new account and re-test I get
Thunderbird failed to find your email account.

---

### Post by TheFu on 2023-09-28
A few weeks ago, libssl/TLS had a big update.  I haven't noticed issues, but there could certainly be some.

There are TLS/SSL testers on the internet.  [https://mxtoolbox.com/diagnostic.aspxl](https://mxtoolbox.com/diagnostic.aspxl) is one.   [https://ssl-tools.net/mailservers](https://ssl-tools.net/mailservers) also.  I've used both to ensure my email servers weren't relay hosts.  Being one of those is a quick way to be banned.

---

### Post by Impavidus on 2023-09-28
As you've posted this in New to Ubuntu, maybe I should mention this. Ubuntu 23.04 is an interim release and has only 4 months of support left. 10 months from now, its successor (to be released next month) will be dead too. For people new to Ubuntu and for servers, we usually recommend the LTS releases.

---

### Post by artisanpens on 2023-09-28
> **TheFu said:**
> A few weeks ago, libssl/TLS had a big update.  I haven't noticed issues, but there could certainly be some.

There are TLS/SSL testers on the internet.  [https://mxtoolbox.com/diagnostic.aspxl](https://mxtoolbox.com/diagnostic.aspxl) is one.   [https://ssl-tools.net/mailservers](https://ssl-tools.net/mailservers) also.  I've used both to ensure my email servers weren't relay hosts.  Being one of those is a quick way to be banned.

Thanks, everything checks out OK on mxtoolbox but ssl-tools shows SSL certificate errors

[COLOR=#333333][FONT=&quot](Certificate is self-signed.)[/FONT][/COLOR]
[LIST]
[*]3636 days remaining 
[*]2048 bit 
[*]sha256WithRSAEncryption
[/LIST]

[LIST]
[*][FONT=FontAwesome][/FONT] Hostname Mismatch 
[*][FONT=FontAwesome][/FONT] Unknown Authority
[/LIST]

Time to start reading up on ssl certificates.

---

### Post by artisanpens on 2023-09-29
Thanks everyone for the help, I've now got it (partially) working, I can collect mail from the server with Thunderbird but not send via the server.

I can live with that by using my ISP's smtp server for outgoing mail.

The solution was a Dovecot setting '**Index files location'**

---

### Post by TheFu on 2023-09-29
If this is solved, please use the Thread Tools button to mark it. Saves everyone on the community time.

If your ISP blocks server-to-server SMTP/email, you have 2 choices.
[LIST]
[*]Setup (or pay some) for a VPN to a VPS that doesn't and ensure all your email goes through that VPN to a public-facing, MX server
[*]Use their SMTP Relay.
[/LIST]

I paid $50/yr to an email relay service in the late 1990s when the ISP started blocking outbound SMTP.  Compared to the cost of a VPS ($60/yr) and letting them deal with the hassles, it seemed like a bargain.  I only do it myself now because I need more than just email relayed.

---

### Post by artisanpens on 2023-09-29
> **TheFu said:**
> If this is solved, please use the Thread Tools button to mark it. Saves everyone on the community time.

Will do.
Is there a button for partually solved? :-)

> 
If your ISP blocks server-to-server SMTP/email, you have 2 choices.
[LIST]
[*]Setup (or pay some) for a VPN to a VPS that doesn't and ensure all your email goes through that VPN to a public-facing, MX server
[*]Use their SMTP Relay.
[/LIST]

I paid $50/yr to an email relay service in the late 1990s when the ISP started blocking outbound SMTP.  Compared to the cost of a VPS ($60/yr) and letting them deal with the hassles, it seemed like a bargain.  I only do it myself now because I need more than just email relayed.

My ISP does block port 25 but the host allows other ports to be opened for SMTP traffic, which I've done on port 2525.

---

### Post by TheFu on 2023-09-29
> **artisanpens said:**
>  My ISP does block port 25 but the host allows other ports to be opened for SMTP traffic, which I've done on port 2525.

And if they block SMTP, they could just look at the traffic and block it, regardless of the port. When I worked for an ISP, we implemented this "DPI" for ourselves and smaller ISPs who road on our network. The port didn't matter. It was about the traffic.  Perhaps your ISP doesn't do that. IDK.

---

### Post by artisanpens on 2023-09-29
> **TheFu said:**
> And if they block SMTP, they could just look at the traffic and block it, regardless of the port. When I worked for an ISP, we implemented this "DPI" for ourselves and smaller ISPs who road on our network. The port didn't matter. It was about the traffic.  Perhaps your ISP doesn't do that. IDK.

I've been using port 2525 on my old server for 20 years with the same ISP, so guess they don't look at traffic.

---

### Post by TheFu on 2023-09-29
> **artisanpens said:**
> I've been using port 2525 on my old server for 20 years with the same ISP, so guess they don't look at traffic.

Could be.
Or they implemented DPI last weekend if it doesn't work anymore.   Hard to know.

---

### Post by artisanpens on 2023-09-29
> **TheFu said:**
> Could be.
Or they implemented DPI last weekend if it doesn't work anymore.   Hard to know.

Possibly, the problem I asked about was on a new server at a new host.

Our old host had pre-configured the email, whereas the new server was just a bare Ububtu box, which is why I knew nothing about configuring an email server.

---

