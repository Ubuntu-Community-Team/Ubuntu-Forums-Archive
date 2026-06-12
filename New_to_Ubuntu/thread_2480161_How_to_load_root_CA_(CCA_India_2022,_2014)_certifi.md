---
title: "How to load root CA (CCA India 2022, 2014) certificate in Ubuntu"
date: 2022-10-21
forum: New to Ubuntu
---

### Post by dineshraghunath on 2022-10-21
Please let me know how to load root CA (CCA India 2022, 2014) certificate in Ubuntu. The below mentioned is the command which i saw in a document.

[B]certutil -A -n rootca -i /location_of_ca_root_cert/rootcert.pem -t"CT,CT,CT" -d ~/.pki/nssdb

[/B]Please let me know How to get the root cetificate?

Below is the document which Im following. The pupose is to add the digital signature in Ubuntu and use it for signing PDF through Libre Office 

[https://www.hypersecu.com/_files/ugd/5aae8d_952a62b8ee024d94ac1cc290ffd2417f.pdf](https://www.hypersecu.com/_files/ugd/5aae8d_952a62b8ee024d94ac1cc290ffd2417f.pdf)

---

### Post by dineshraghunath on 2022-10-22
Please see this. Im getting an error message like **" certutil: could not decode certificate: SEC_ERROR_BAD_DER: security library: improperly formatted DER-encoded message." **when im trying to add root ca certificate.

tex@TEDesk:~/Downloads$ sudo certutil -A -i CCAIndia2014.cer -n root_ca -t "CT,CT,CT" -d /home/tex/.pki/nssdb/
[sudo] password for tex: 
**certutil: could not decode certificate: SEC_ERROR_BAD_DER: security library: improperly formatted DER-encoded message.**


Please let me know how to solve this

---

