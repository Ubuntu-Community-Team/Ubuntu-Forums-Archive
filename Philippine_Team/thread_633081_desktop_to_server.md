---
title: "desktop to server"
date: 2007-12-06
forum: Philippine Team
---

### Post by dexjul on 2007-12-06
Mga Gurus I need your help.

I installed ubunut 7.04 (destop) gusto ko gawing server anong mga kailangan na application para maging server yung desktop ko. I already installed LAMP pero basic lang sinundan ko lang ito [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and pano ba implement yung lamp?

Salamat.

---

### Post by Samhain13 on 2007-12-06
Server, as in web server? Tama na na may LAMP ka.

Ang pagkakaintindi ko kasi sa LAMP ay web server nga siya. Yung files, kung hindi mo na gagalawin yung stock configuration, na sa /var/www. Diyan ka maglalagay ng mga files at scripts na gusto mong makita ng iba through "http". Para masubukan mo, magbukas ka ng browser at ilagay mo sa address bar [http://localhost](http://localhost).
Mapapansin mo na yung laman niya ay kung ano yung laman ng /var/www.

Kung may network of local computers, imbes na localhost, yung local IP address ng computer mo ang ilalagay sa address bar ng browser. Ingat ka nga lang kasi kahit sa labas ng local network, maa-access na yang PC mo through the web server basta alam yung IP address mo na galing sa ISP.

Kung office file server naman, siguro mas mabuti nang iba ang sumagot. :)

---

### Post by jmazaredo on 2007-12-09
ala eh, mamimili ka muna kung anung server na aplikasyon ang iyong nais na mailagay.
gusto mo bang maging web server para makapag host ka na ng website mo?
mail server kung e-mail ang nais mo
samba kung gusto mong gawing file server iyan.
at marami pang iba..

o gusto mo lahat gaya nang sabi ni zakame frankenstine :)

---

### Post by dexjul on 2007-12-10
Gusto ko lahat ng pedeng iinstall na server application. Pwede ba yun? 

Salamat sa mga reply nyo mga gurus.

---

### Post by pinoyskull on 2007-12-10
> **dexjul said:**
> Gusto ko lahat ng pedeng iinstall na server application. Pwede ba yun? 

Salamat sa mga reply nyo mga gurus.
technically pwede, pero ang rule is kung ano lang ang need mo yun lang install mo :)

---

### Post by elite_angel on 2007-12-13
What Server? Kind?

---

### Post by raxso on 2007-12-13
Check this site you can find a lot of how-to's about how to setup a server

[http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-ubuntu-7.10](http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-ubuntu-7.10)

---

### Post by dexjul on 2007-12-19
Mga gurus ok na yung LAMP pati samba. Nag install naman ako ng binds, kaya lang may error eh.

```
dexter@dexter-laptop:/etc/apache2$ dig docjul.com

; <<>> DiG 9.3.4 <<>> docjul.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 59881
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;docjul.com.                    IN      A

;; AUTHORITY SECTION:
com.                    231     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1198054478 1800 900 604800 900

;; Query time: 10 msec
;; SERVER: 58.69.254.106#53(58.69.254.106)
;; WHEN: Wed Dec 19 17:06:11 2007
;; MSG SIZE  rcvd: 101

```


```
dexter@dexter-laptop:/etc/apache2$ nslookup docjul.com
Server:         58.69.254.106
Address:        58.69.254.106#53

** server can't find docjul.com: NXDOMAIN


```

docjul.com.db

```
// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
docjul.com. IN SOA ns1.docjul. admin.docjul.com. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
// ns1 = DNS Server name
// mail = mail server name
// example.com = domain name

docjul.com. IN NS ns1.docjul.com.
docjul.com. IN MX 10 mail.docjul.com.
docjul.com. IN A 124.83.19.155

// Replace the IP address with the right IP addresses.
www IN A 124.83.19.155
mta IN A 124.83.19.155
ns1 IN A 124.83.19.155
```

rev.0.0.124.in-addr.arpa
```
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it’s 1, as my IP address is #192.168.0.1.
@ IN SOA ns1.docjul.com. admin.docjul.com. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS ns1.docjul.com.
1 IN PTR docjul.com


```

Thank you...

---

