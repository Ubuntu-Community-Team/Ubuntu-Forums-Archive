---
title: "reinstall GCC"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by g34r on 2012-02-24
Because i had a problem with my older GCC which is my stdio.h not found when i compiled my source code, so I decided to remove it from ubuntu software center, and install it again. but when I trying to install it again using Software center
```
This error could be caused by required additional software packages which are missing or not installable.
 Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details:The following packages have unmet dependencies:

```
and when I trying using terminal this is happen
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gcc : Depends: gcc-4.5 (>= 4.5.2-1~) but it is not going to be installed
       Recommends: libc6-dev but it is not going to be installed or
                   libc-dev
E: Unable to correct problems, you have held broken packages.

```
I have installed libc6-dev & libc-dev on my machine
so what's should I do for reinstall my gcc? thanks for your help :D

---

### Post by ohadcn on 2012-02-24
i think you copied only parts of the error message
we need the whole one to help you
try install it from terminal and see what happens
```

sudo apt-get install gcc

```

---

### Post by g34r on 2012-02-24
when using apt-get install this message appear
```

syahdeini@NeXT:~$ sudo apt-get install gcc
[sudo] password for syahdeini: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gcc : Depends: gcc-4.5 (>= 4.5.2-1~) but it is not going to be installed
       Recommends: libc6-dev but it is not going to be installed or
                   libc-dev
E: Unable to correct problems, you have held broken packages.

```
thanks for your reply

---

### Post by raja.genupula on 2012-02-24
open your terminal and type 
```
sudo apt-get install -f

```
and try again . let us know what you got ,all the best 
.

---

### Post by g34r on 2012-02-24
this is what happened
```

syahdeini@NeXT:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libx264-116 python-gnomedesktop libsidplay1 libid3tag0 libopencore-amrnb0
  libgnome-desktop-2-17 libopencore-amrwb0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
dpkg: warning: ignoring option --foreign-architecture=i386: this architecture cannot be foreign
Setting up ca-certificates-java (20100412) ...
creating /etc/ssl/certs/java/cacerts...
  error adding brasil.gov.br/brasil.gov.br.crt
  error adding cacert.org/cacert.org.crt
  error adding debconf.org/ca.crt
  error adding gouv.fr/cert_igca_dsa.crt
  error adding gouv.fr/cert_igca_rsa.crt
  error adding mozilla/ACEDICOM_Root.crt
  error adding mozilla/AC_Raíz_Certicámara_S.A..crt
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_1.crt
  error adding mozilla/AOL_Time_Warner_Root_Certification_Authority_2.crt
  error adding mozilla/AddTrust_External_Root.crt
  error adding mozilla/AddTrust_Low-Value_Services_Root.crt
  error adding mozilla/AddTrust_Public_Services_Root.crt
  error adding mozilla/AddTrust_Qualified_Certificates_Root.crt
  error adding mozilla/America_Online_Root_Certification_Authority_1.crt
  error adding mozilla/America_Online_Root_Certification_Authority_2.crt
  error adding mozilla/ApplicationCA_-_Japanese_Government.crt
  error adding mozilla/Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068.crt
  error adding mozilla/Baltimore_CyberTrust_Root.crt
  error adding mozilla/Buypass_Class_2_CA_1.crt
  error adding mozilla/Buypass_Class_3_CA_1.crt
  error adding mozilla/CA_Disig.crt
  error adding mozilla/CNNIC_ROOT.crt
  error adding mozilla/COMODO_Certification_Authority.crt
  error adding mozilla/COMODO_ECC_Certification_Authority.crt
  error adding mozilla/Camerfirma_Chambers_of_Commerce_Root.crt
  error adding mozilla/Camerfirma_Global_Chambersign_Root.crt
  error adding mozilla/Certigna.crt
  error adding mozilla/Certplus_Class_2_Primary_CA.crt
  error adding mozilla/Certum_Root_CA.crt
  error adding mozilla/Chambers_of_Commerce_Root_-_2008.crt
  error adding mozilla/ComSign_CA.crt
  error adding mozilla/ComSign_Secured_CA.crt
  error adding mozilla/Comodo_AAA_Services_root.crt
  error adding mozilla/Comodo_Secure_Services_root.crt
  error adding mozilla/Comodo_Trusted_Services_root.crt
  error adding mozilla/Cybertrust_Global_Root.crt
  error adding mozilla/DST_ACES_CA_X6.crt
  error adding mozilla/DST_Root_CA_X3.crt
  error adding mozilla/Deutsche_Telekom_Root_CA_2.crt
  error adding mozilla/DigiCert_Assured_ID_Root_CA.crt
  error adding mozilla/DigiCert_Global_Root_CA.crt
  error adding mozilla/DigiCert_High_Assurance_EV_Root_CA.crt
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_1.crt
  error adding mozilla/Digital_Signature_Trust_Co._Global_CA_3.crt
  error adding mozilla/E-Guven_Kok_Elektronik_Sertifika_Hizmet_Saglayicisi.crt
  error adding mozilla/EBG_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;.crt
  error adding mozilla/Entrust.net_Premium_2048_Secure_Server_CA.crt
  error adding mozilla/Entrust.net_Secure_Server_CA.crt
  error adding mozilla/Entrust_Root_Certification_Authority.crt
  error adding mozilla/Equifax_Secure_CA.crt
  error adding mozilla/Equifax_Secure_Global_eBusiness_CA.crt
  error adding mozilla/Equifax_Secure_eBusiness_CA_1.crt
  error adding mozilla/Equifax_Secure_eBusiness_CA_2.crt
  error adding mozilla/Firmaprofesional_Root_CA.crt
  error adding mozilla/GTE_CyberTrust_Global_Root.crt
  error adding mozilla/GeoTrust_Global_CA.crt
  error adding mozilla/GeoTrust_Global_CA_2.crt
  error adding mozilla/GeoTrust_Primary_Certification_Authority.crt
  error adding mozilla/GeoTrust_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/GeoTrust_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/GeoTrust_Universal_CA.crt
  error adding mozilla/GeoTrust_Universal_CA_2.crt
  error adding mozilla/GlobalSign_Root_CA.crt
  error adding mozilla/GlobalSign_Root_CA_-_R2.crt
  error adding mozilla/GlobalSign_Root_CA_-_R3.crt
  error adding mozilla/Global_Chambersign_Root_-_2008.crt
  error adding mozilla/Go_Daddy_Class_2_CA.crt
  error adding mozilla/Hongkong_Post_Root_CA_1.crt
  error adding mozilla/IGC_A.crt
  error adding mozilla/Izenpe.com.crt
  error adding mozilla/Juur-SK.crt
  error adding mozilla/Microsec_e-Szigno_Root_CA.crt
  error adding mozilla/Microsec_e-Szigno_Root_CA_2009.crt
  error adding mozilla/NetLock_Arany_=Class_Gold=_F&#337;tanúsítvány.crt
  error adding mozilla/NetLock_Business_=Class_B=_Root.crt
  error adding mozilla/NetLock_Express_=Class_C=_Root.crt
  error adding mozilla/NetLock_Notary_=Class_A=_Root.crt
  error adding mozilla/NetLock_Qualified_=Class_QA=_Root.crt
  error adding mozilla/Network_Solutions_Certificate_Authority.crt
  error adding mozilla/OISTE_WISeKey_Global_Root_GA_CA.crt
  error adding mozilla/QuoVadis_Root_CA.crt
  error adding mozilla/QuoVadis_Root_CA_2.crt
  error adding mozilla/QuoVadis_Root_CA_3.crt
  error adding mozilla/RSA_Root_Certificate_1.crt
  error adding mozilla/RSA_Security_2048_v3.crt
  error adding mozilla/S-TRUST_Authentication_and_Encryption_Root_CA_2005_PN.crt
  error adding mozilla/SecureSign_RootCA11.crt
  error adding mozilla/SecureTrust_CA.crt
  error adding mozilla/Secure_Global_CA.crt
  error adding mozilla/Security_Communication_EV_RootCA1.crt
  error adding mozilla/Security_Communication_Root_CA.crt
  error adding mozilla/Sonera_Class_1_Root_CA.crt
  error adding mozilla/Sonera_Class_2_Root_CA.crt
  error adding mozilla/Staat_der_Nederlanden_Root_CA.crt
  error adding mozilla/Staat_der_Nederlanden_Root_CA_-_G2.crt
  error adding mozilla/Starfield_Class_2_CA.crt
  error adding mozilla/StartCom_Certification_Authority.crt
  error adding mozilla/SwissSign_Gold_CA_-_G2.crt
  error adding mozilla/SwissSign_Platinum_CA_-_G2.crt
  error adding mozilla/SwissSign_Silver_CA_-_G2.crt
  error adding mozilla/Swisscom_Root_CA_1.crt
  error adding mozilla/TC_TrustCenter_Class_2_CA_II.crt
  error adding mozilla/TC_TrustCenter_Class_3_CA_II.crt
  error adding mozilla/TC_TrustCenter_Universal_CA_I.crt
  error adding mozilla/TC_TrustCenter_Universal_CA_III.crt
  error adding mozilla/TC_TrustCenter__Germany__Class_2_CA.crt
  error adding mozilla/TC_TrustCenter__Germany__Class_3_CA.crt
  error adding mozilla/TDC_Internet_Root_CA.crt
  error adding mozilla/TDC_OCES_Root_CA.crt
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_1.crt
  error adding mozilla/TURKTRUST_Certificate_Services_Provider_Root_2.crt
  error adding mozilla/Taiwan_GRCA.crt
  error adding mozilla/Thawte_Personal_Freemail_CA.crt
  error adding mozilla/Thawte_Premium_Server_CA.crt
  error adding mozilla/Thawte_Server_CA.crt
  error adding mozilla/Thawte_Time_Stamping_CA.crt
  error adding mozilla/TÜB&#304;TAK_UEKAE_Kök_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_-_Sürüm_3.crt
  error adding mozilla/UTN_DATACorp_SGC_Root_CA.crt
  error adding mozilla/UTN_USERFirst_Email_Root_CA.crt
  error adding mozilla/UTN_USERFirst_Hardware_Root_CA.crt
  error adding mozilla/ValiCert_Class_1_VA.crt
  error adding mozilla/ValiCert_Class_2_VA.crt
  error adding mozilla/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G4.crt
  error adding mozilla/VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.crt
  error adding mozilla/VeriSign_Universal_Root_Certification_Authority.crt
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority.crt
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority.crt
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority.crt
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.crt
  error adding mozilla/Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.crt
  error adding mozilla/Visa_eCommerce_Root.crt
  error adding mozilla/WellsSecure_Public_Root_Certificate_Authority.crt
  error adding mozilla/Wells_Fargo_Root_CA.crt
  error adding mozilla/XRamp_Global_CA_Root.crt
  error adding mozilla/certSIGN_ROOT_CA.crt
  error adding mozilla/ePKI_Root_Certification_Authority.crt
  error adding mozilla/thawte_Primary_Root_CA.crt
  error adding mozilla/thawte_Primary_Root_CA_-_G2.crt
  error adding mozilla/thawte_Primary_Root_CA_-_G3.crt
  error adding signet.pl/signet_ca1_pem.crt
  error adding signet.pl/signet_ca2_pem.crt
  error adding signet.pl/signet_ca3_pem.crt
  error adding signet.pl/signet_ocspklasa2_pem.crt
  error adding signet.pl/signet_ocspklasa3_pem.crt
  error adding signet.pl/signet_pca2_pem.crt
  error adding signet.pl/signet_pca3_pem.crt
  error adding signet.pl/signet_rootca_pem.crt
  error adding signet.pl/signet_tsa1_pem.crt
  error adding spi-inc.org/spi-ca-2003.crt
  error adding spi-inc.org/spi-cacert-2008.crt
failed (VM used: java-6-openjdk).
dpkg: error processing ca-certificates-java (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by g34r on 2012-02-25
Can anyone help me, please. I very need gcc for my collage study :(

---

### Post by raja.genupula on 2012-02-25
hi remove everything in apt cache 

```
sudo rm -rf /var/cache/apt/archives/*
```

open your synaptic and remove ca-certificates-java pkg . 

type ```
sudo apt-get update
``` 

now try again . 

all the best,:)

---

### Post by g34r on 2012-02-25
Thanks for your reply raja, but I still get a error like my post above.

---

### Post by g34r on 2012-02-27
No one can help me with this problem? :(
please help.

---

### Post by haqking on 2012-02-27
> **g34r said:**
> Thanks for your reply raja, but I still get a error like my post above.

you have removed them but still get the same error about the certificates ?

---

### Post by g34r on 2012-02-29
Yes of course,any solution for this?
or should I reinstall my ubuntu again.

---

