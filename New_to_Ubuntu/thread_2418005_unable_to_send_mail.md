---
title: "unable to send mail"
date: 2019-04-30
forum: New to Ubuntu
---

### Post by maniish4u on 2019-04-30
Hi All,

I am unable to send my mail from Ubuntu server using sendmail command. Getting following logs continuously on the server. 

Apr 30 16:20:11 mudcotrs sendmail[31500]: STARTTLS=client, relay=owa.paytmbank.com., version=TLSv1.2, verify=FAIL, cipher=AES256-GCM-SHA384, bits=256/256
Apr 30 16:20:16 mudcotrs sendmail[31500]: x3UAoBQv031500: to=root, ctladdr=smmsp (113/120), delay=00:00:05, xdelay=00:00:05, mailer=relay, pri=30532, relay=owa.paytmbank.com. [103.1.112.195], dsn=5.0.0, stat=Service unavailable
Apr 30 16:20:16 mudcotrs sendmail[31500]: x3UAoBQv031500: x3UAoBQw031500: DSN: Service unavailable
Apr 30 16:20:16 mudcotrs sendmail[31500]: x3UAoBQw031500: to=smmsp, delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=31556, relay=owa.paytmbank.com., dsn=4.0.0, stat=Deferred: Connection reset by owa.paytmbank.com.

---

### Post by dino99 on 2019-04-30
Maybe sendmail is simply not supported:

Paytm - India&#8217;s largest mobile e-commerce website is an ultimate destination for prompt Online Recharge, DTH, Data Card & Metro Card Recharge and Mobile Bill Payment for Airtel, Aircel, BSNL, Tata Docomo, Idea, MTNL, Vodafone & other operators for all the circles across India. 

Check their support directly.

---

### Post by SeijiSensei on 2019-04-30
Who is the sender of this message? Who is the recipient?  If either is root, it will almost certainly be rejected.

Then there is the question of the identity of your sending server.  Is it yours? Does it have a fully-qualified domain name? Is reverse DNS resolution correctly configured for the sending server?  Do you have an SPF record for the server? Have you checked your server's IP at mxtoolbox.com?

In a world where >90% of mail traffic is spam, service providers have erected a lot of barriers.

---

