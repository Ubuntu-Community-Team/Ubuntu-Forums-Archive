---
title: "help with mail - dns please"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by irg2 on 2015-03-25
Hi. Not sure what has triggered but since this week, previously functioning Thunderbird mail now comes up with message "An error occured sending mail: SMTP server smtp.office365.com is unkown. The server may be incorrectly configured. Please verify that your SNMP server settings are correct and try again". 

The mail server settings are still working ok on other devices (android) mail client software.   

I loaded wireshark to see if I could see what was going on. The sequence i see is
dns ipv4 query for smtp.office365.com
dns ipv6 query for smtp.office365.com
response to the ipv4 query containing canonical cname recursive lookup with ipv4 addresses of number of mail server (proxy) nodes.
response to the ipv6 query containing canonical cname recursive lookup with ipv6 addresses of number of (same as above) mail server (proxy) nodes.
ubuntu opens up tcp session to port 53 on router-proxy dns IP address. No data sent except the tcp open.
router ack to the tcp session.
2nd tcp session (new tcp source user port) to the router port 53 initiated by ubuntu.
router ack to the 2nd tcp session.
dns ipv4 query for  smtp.office365.com.home
dns ipv6 query for smtp.office365.com.home
response saying no such name to both the queries.

I checked the trace with an alternate temporary mail client (Claws)  on the ubuntu box. Same behaviour in the trace.  I get an error message on Claws "*** smtp.office365.com:587: unknown host." - assume due to the same underlying inability to be able to contact the mail server.

I check a trace of a ping to smtp.office365.com.  That works ok. In the trace for this I see only the ipv4 dns request (giving same result as the request to the mail triggered lookups), and then successful icmp packets / responses.

In the Thunderbird mail if i select "get mail", the trace shows a dns query and lookup ipv4 and ipv6, followed by a tcp session being opened to the ip address of the POP3 resolved mail server address.  No separate session being opened with the local gateway on port 53. Then functions ok to collect mail.

Is it normal behaviour for the mail software to do what appears to be a second lookup to what I assume is expecting the local domain "home" router proxy dns to be able to answer from a local cache (that it should have populated from listening to the response to the first lookup ?). The router appears to send the entire URL with the "home" on it to its configured (I cant alter it) dns forwarder address of a BT DNS, which cant resolve it due to the "home" suffix.

A microsoft pc running a windows native mail client (temporarily configured for test) plugged into the same network is working ok. It is not suitable to run as my main mail client and really need to get normal service back on the ubuntu box if I can.

Any guidance on this would be appreciated:
Thunderbird: 31.5.0 (I have reinstalled from the package manager as a precaution but no change).
Claws: 3.9.3
Ubuntu: 14.04 LTS
Mail outgoing: STARTTLS security, port 587
Router: BT Home Hub firmware [COLOR=#333333][FONT=Verdana]Version 4.7.5.1.83.8.94.1.37 (Type A), last updated 18/3/14
[/FONT][/COLOR]
Thanks Ian

---

### Post by dino99 on 2015-03-25
might be a thunderbird  issue as the host is not down
[https://support.office.com/en-au/article/Settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c](https://support.office.com/en-au/article/Settings-for-POP-and-IMAP-access-for-Office-365-for-business-or-Microsoft-Exchange-accounts-7fc677eb-2491-4cbc-8153-8e7113525f6c)

[https://www.google.nl/search?q=thunderbird+unknown+host&oq=thunderbird+unknown+host&aqs=chrome..69i57.10829j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8](https://www.google.nl/search?q=thunderbird+unknown+host&oq=thunderbird+unknown+host&aqs=chrome..69i57.10829j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8)

---

### Post by irg2 on 2015-03-26
Thanks for ideas on that.

I thought about some more and focussed on the dns angle as for me this appeared to be the root of it, especially as the Claws mail client had the same problem when I did the trace.

There is a bug in the handling of dns CNAME nested responses.  For the smtp address I get 5 recursive layers of response within the dns reply.  Whilst that reply looks ok in that it gives me the dns A records at the bottom of the CNAME nest, and those A records each have an IP address, the mail clients are not using it for some reason.  

The same recursive lookup of the smtp address is used when I ping the smtp.office365.com.  The ping works ok as I can see it then using the dns returned IP address.

So I have changed the smtp mail server to outlook-emeawest.office365.com in the client and hey presto I am now working ok.  From a trace I can see it is not reliant on trying to deal with the dns CNAME responses as it gets a dns A record and associated IP address from its initial dns lookup request.

Given ubuntu code/kernel must be handing the dns correctly for the ICMP Ping to work, this must be a problem in both of the mail clients, and possibly not expecting the large dns response packet resulting from the large amount of information it returns on the number of recursive nests in the dns record CNAME before it hits the A record and associated IP info in the response.

I hope that the post is useful to others that hit the same issue - if on BT mail then I suggest you use the mail server that I have noted above. If it ever changes / stops working, or if you have another ISP mail service provider then try nslookup of its published server address to get to the A record, ie the lowest in the nested response, so that you can then configured that on your mail client.

Ian.

---

