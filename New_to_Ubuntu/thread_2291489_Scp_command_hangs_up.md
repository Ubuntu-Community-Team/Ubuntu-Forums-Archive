---
title: "Scp command hangs up"
date: 2015-08-20
forum: New to Ubuntu
---

### Post by mostafafci-2008 on 2015-08-20
I used this command to copy a file from my machine over a remote host using a private OpenSSH key over a Shrew VPN connection :
----------------------------------------------------------------------------------------------------------------------------------------------------------
scp -i mostafa home/mostafam/RC_Sprint094_20150820/www/RC_Sprint091.1_06252015.tar.gz mostafam@172.16.50.196:/data/deploy/Test/

and the result after 1 minute is :        

Connection closed by 172.16.50.196lost connection

I have made a little search and didn't find anything useful. The the message returned from :  ssh -vvv mostafam@172.16.50.196 was hanging up from attached "2.png" image: and ends up after almost 2 minutes with:


Connection closed by 172.16.50.196



The default way of SSh connection was working with me before but now I tricked it to work

Previous way:     ssh mostafam@172.16.50.196
Current way:      MACs=hmac-sha1                         ssh -o MACs=hmac-sha1 -vvvl mostafam 172.16.50.196
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Can any developer help me with this?

---

### Post by chopra on 2015-08-25
scp -i mostafa home/mostafam/RC_Sprint094_20150820/www/RC_Sprint091.1_06252015.tar.gz mostafam@172.16.50.196:/data/deploy/Test/

I don't follow this syntax.  So the file you want to copy is home/mostafam/RC_Sprint094_20150820/www/RC_Sprint091.1_06252015.tar.gz
which you want to copy into the  /data/deploy/Test/ directory at 172.16.50.196 on which your username is mostafam.
Are you trying to copy two files? If not, what's the mostafa doing after the scp -i?

Perhaps try getting rid of the -i option, or maybe try compressing the file a second time?

---

