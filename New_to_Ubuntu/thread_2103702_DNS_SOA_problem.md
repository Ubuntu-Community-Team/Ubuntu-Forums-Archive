---
title: "DNS SOA problem"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by livingsky on 2013-01-10
I have setup a name/mail server and am having problems with the DNS part of the setup. I am able to go to the specific address (no website, just a mailman page) and do stuff. I am also able to email a user through gmail, so I know that the mail is working. As I used an online dns lookup tool/checker though, it tells me that I have no SOA record for the domain. I am unable to ping the domain without the www. in front of the domain name, but ping does work when I use www. As far as I can tell, the zone file is correct, but obviously I am missing something. Here is my zone file. 

$TTL 3600
faithwalk.ca.    IN     SOA    server.faithwalk.ca. [email]bob@faithwalk.ca[/email]. (
                                2013011103  ; Serial
                                3H          ; refresh after 3 hours
                                1H          ; retry after 1 hour
                                1W          ; expire after 1 week
                                1D)         ; minimum TTL of 1 day

        ; Name Server
@       IN      NS      server.faithwalk.ca.    ; My server
        IN      NS      ns0.xname.org.          ; xname 1
        IN      NS      ns1.xname.org.          ; xname 2
        IN      NS      ns2.xname.org.          ; xname 3

        ; Mail Exchanger
        IN      MX      10 mail.faithwalk.ca.   ; Your Mail Server


server                  IN A                    24.72.66.135
www                     IN A                    24.72.66.135
;server                 IN CNAME
mail                    IN A                    24.72.66.135

; Resource Record - veryfy the IP where your mails come from(disable if not needed)
; @     IN TXT          "v=spf1 ip4:85.214.123.0/24 -all"

; EOF


Can someone help me figure this out. It's not a huge problem, but I would like to have the domain working properly in all aspects.

---

### Post by vasiliscnisrok on 2013-01-11
$TTL 3600
faithwalk.ca. IN SOA server.faithwalk.ca. [email]bob@faithwalk.ca[/email].

Email must be in the form
bob.faithwalk.ca.

not write @

example SOA [http://www.zytrax.com/books/dns/ch8/soa.html](http://www.zytrax.com/books/dns/ch8/soa.html)

---

### Post by livingsky on 2013-01-11
Thanks, I fixed that, but I still have the same problem. The message I get from my dns record search on faithwalk.ca still states that there it cannot find the domain, and a search on [www.faithwalk.ca](www.faithwalk.ca) finds no SOA record, no MX record (although I am able to get mail) and only comes up with the reverse lookup for the domain. I am not sure what to try next.

---

### Post by Doug S on 2013-01-11
try changing this line:```
faithwalk.ca. IN SOA server.faithwalk.ca. bob@faithwalk.ca. (

```to this:```
@ IN SOA faithwalk.ca. bob.faithwalk.ca. (

```(where I have also included the change suggested in the above post.)

---

