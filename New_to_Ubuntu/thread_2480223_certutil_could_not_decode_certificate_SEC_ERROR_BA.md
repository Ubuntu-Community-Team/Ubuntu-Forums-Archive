---
title: "certutil: could not decode certificate: SEC_ERROR_BAD_DER: security library: improper"
date: 2022-10-23
forum: New to Ubuntu
---

### Post by dineshraghunath on 2022-10-23
tex@TEDesk:~/Downloads$ sudo certutil -A -i CCAIndia2014.cer -n root_ca -t "CT,CT,CT" -d /home/tex/.pki/nssdb/
[sudo] password for tex: 
certutil: could not decode certificate: SEC_ERROR_BAD_DER: security library: improperly formatted DER-encoded message.
tex@TEDesk:~/Downloads$ 

Can someone help me to solve this issue

---

