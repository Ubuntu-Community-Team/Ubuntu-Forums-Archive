---
title: "Boot then Black screen and monitor turns off, then Log in"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by matt2911 on 2012-01-29
[FONT=Tahoma]Hi Guys and Gals, I have a dual boot of Win XP and Ubuntu 11.10 Oneiric Ocelot and I have some questions.   My main question is why I have a Black screen after booting to Ubuntu and before logon screen(yes monitor turns off during black screen).  I suspect it is because my video card is not fully supported or the drivers are not working properly.

 My next question deals with checking if I have all drivers installed properly.  Its was easy in Win XP due to the various guides around the net and the many years Ive spent using XP.  I am aware there are guides for Ubuntu and even specific user guides too, but I have not found what I am looking for, specifically.   [/FONT]Wish I could just open the Device Mgr and right click on a device or see the red or yellow flags hovering around the device, man I need to learn a lot. :b (whats the difference between using a 'P' or a 'b' with that I will never know?)  

Yes I used the search feature and found others with a similar problem but I did not want to mess up something, applying someone elses patch to my own.   I am a new user to Ubuntu but I have used PCBSD on another system for a few months( I think it was a proprietary Compaq system that was the problem).  

  Here is what I did to install Ubuntu 11.10.  I DL a .iso file and burned to CD.  I booted from CD to install and kept my win XP install.  On a 500 Gig drive XP got 140Gig Ubuntu got 93 Gig Swap got 8.4Gigs and the rest was assigned to the Home drive(350GB)    I used Ext3 to format with the CD, but it was set to use EXT4, I think.  The first time I installed I got hung on the setting a password screen(did not want a password but found that I had to have one)  I re-ran the setup and installed all but the restricted software or drivers IDK (its the last box about restricted stuff i left it unchecked)  I did get installed the second time and booted normally for the next two times then I got a wierd color pattern of lines going across the screen all way down for about 2 seconds.  This happened after I change the resolution to 1024 x 768 from higher res. I think.  

My system is GA-EP45-DS3R mobo with a Core 2 quad Q8200 or Q8400 - EVGA 6600GT - 4 gigs RAM - WD hard drive 640 GB - SATA DVD drive - 600 watt PS - Dual booting Win XP SP3  

By the way when I type the lspci / grep VGA command it does not work maybe cuz I am using the wrong / symbol right?  oops I found it on the key below backspace but I had to use shift to get it and it does not look like | on key but it is | its more like two lines not one sorry.

---

### Post by rgreener25 on 2012-01-29
i dont know why but where you typed in lspci / grep VGA it should be lspci | grep VGA

---

### Post by matt2911 on 2012-01-29
Ok here is the lspci | grep VGA 
VGA compatible controller : nVidia corp NV43 [GeForce6600GT] (rev a2)

---

### Post by rgreener25 on 2012-01-29
try downloading this [http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run") then open terminal and cd into it and type ```
chmod 777 NVIDIA-Linux-x86-180.51-pkg1.run
``` then ```
./NVIDIA-Linux-x86-180.51-pkg1.run
```

---

### Post by matt2911 on 2012-01-29
> **rgreener25 said:**
> try downloading this [http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run) then open terminal and cd into it and type ```
chmod 777 NVIDIA-Linux-x86-180.51-pkg1.run
``` then ```
./NVIDIA-Linux-x86-180.51-pkg1.run
```
Not to be Anal or anything but I found another technique that I am not sure about its this -->
[COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current      [COLOR=Black]
I found it here at Noobslab --> [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)

Also want to stress I did not do the restricted updates at install.  Maybe thats the problem and I found another way to do that too.
[/COLOR][/COLOR]```
sudo apt-get install ubuntu-restricted-extras  

```I am trying the restricted extras now 
Here is a list of things it found to install.....```
The following extra packages will be installed:
  ca-certificates-java cabextract freepats gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  icedtea6-plugin java-common liba52-0.7.4 libaccess-bridge-java
  libaccess-bridge-java-jni libass4 libavcodec-extra-53 libavformat53
  libavutil-extra-51 libcdaudio1 libcelt0-0 libdc1394-22 libdca0
  libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaac0
  libfaad2 libfftw3-3 libflite1 libgme0 libgsm1 libid3tag0 libkate1 libmad0
  libmimic0 libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0 libmpcdec6
  libmpeg2-4 libmusicbrainz4c2a libofa0 liboil0.3 libopencore-amrnb0
  libopencore-amrwb0 libopenjpeg2 libopenspc0 libpostproc52 libquicktime2
  libschroedinger-1.0-0 libsidplay1 libslv2-9 libsoundtouch0 libswscale2
  libts-0.0-0 libtwolame0 libva1 libvo-aacenc0 libvo-amrwbenc0 libvpx0
  libwildmidi1 libx264-116 libxvidcore4 libzbar0 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib tsconf ttf-dejavu-extra
  ttf-mscorefonts-installer tzdata-java ubuntu-restricted-addons unrar
Suggested packages:
  default-jre equivs libfaad0 libdvdcss2 debhelper fakeroot build-essential
  libfftw3-dev sidplay-base xsidplay slv2-jack sun-java6-fonts
  ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
Recommended packages:
  w32codecs
The following NEW packages will be installed:
  ca-certificates-java cabextract freepats gstreamer0.10-ffmpeg
  gstreamer0.10-fluendo-mp3 gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-plugin
  icedtea6-plugin java-common liba52-0.7.4 libaccess-bridge-java
  libaccess-bridge-java-jni libass4 libavcodec-extra-53 libavformat53
  libavutil-extra-51 libcdaudio1 libcelt0-0 libdc1394-22 libdca0
  libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaac0
  libfaad2 libfftw3-3 libflite1 libgme0 libgsm1 libid3tag0 libkate1 libmad0
  libmimic0 libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0 libmpcdec6
  libmpeg2-4 libmusicbrainz4c2a libofa0 liboil0.3 libopencore-amrnb0
  libopencore-amrwb0 libopenjpeg2 libopenspc0 libpostproc52 libquicktime2
  libschroedinger-1.0-0 libsidplay1 libslv2-9 libsoundtouch0 libswscale2
  libts-0.0-0 libtwolame0 libva1 libvo-aacenc0 libvo-amrwbenc0 libvpx0
  libwildmidi1 libx264-116 libxvidcore4 libzbar0 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib tsconf ttf-dejavu-extra
  ttf-mscorefonts-installer tzdata-java ubuntu-restricted-addons
  ubuntu-restricted-extras unrar
0 upgraded, 81 newly installed, 0 to remove and 0 not upgraded.
Need to get 99.2 MB of archives.
After this operation, 205 MB of additional disk space will be used.
Do you want to continue [Y/n]
```? 
Just want to add I have a new screen that appears to be working or stuck I will tell you in a bit....
TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                   
Edit to the EULA:  I believe it is stuck now and not responding??????
OK I cannot agree to the EULA and continue to use the SW so I guess I just close the window??

Closed the window and re-ran the update only to see this-->  E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
Here are some results....
```
Setting up tzdata-java (2011n-0ubuntu0.11.10) ...
Setting up libdirac-encoder0 (1.0.2-4) ...
Setting up libgsm1 (1.0.13-3) ...
Setting up libva1 (1.0.12-2) ...
Processing triggers for doc-base ...
Processing 3 added doc-base files...
Registering documents with scrollkeeper...
Setting up liboil0.3 (0.3.17-2ubuntu1) ...
Setting up libvpx0 (0.9.6-1) ...
Setting up libmms0 (0.6.2-2) ...
Setting up libzbar0 (0.10+doc-7) ...
Setting up libx264-116 (2:0.116.2042+git178455c-1ubuntu1) ...
Setting up libopencore-amrwb0 (0.1.2-1) ...
Setting up libmodplug1 (1:0.8.8.2-3ubuntu1.1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libmpcdec6 (2:0.1~r459-1ubuntu1) ...
Processing triggers for gnome-menus ...
Setting up libopenjpeg2 (1.3+dfsg-4) ...
Setting up libtwolame0 (0.3.13-1) ...
Setting up libdca0 (0.0.5-4) ...
Setting up libass4 (0.9.13-1) ...
Setting up libsoundtouch0 (1.6.0-2) ...
Setting up gstreamer0.10-fluendo-mp3 (0.10.15.debian-1) ...
Setting up libswscale2 (4:0.7.3-0ubuntu0.11.10.1) ...
Setting up libgme0 (0.5.5-2) ...
Setting up libopencore-amrnb0 (0.1.2-1) ...
Setting up libschroedinger-1.0-0 (1.0.10-2.1) ...
Setting up libofa0 (0.9.3-3.1) ...
Setting up libvo-amrwbenc0 (0.1.1-1) ...
Setting up libkate1 (0.3.8-1) ...
Setting up libdc1394-22 (2.1.3-4) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu2) ...
Setting up cabextract (1.4-1) ...
Setting up libsidplay1 (1.36.59-5) ...
Setting up ttf-dejavu-extra (2.33-1ubuntu1) ...
Setting up libvo-aacenc0 (0.1.1-1) ...
Setting up libxvidcore4 (2:1.3.2-3) ...
Setting up libmimic0 (1.0.4-2.1) ...
Setting up tsconf (1.0-9) ...
Setting up libmp3lame0 (3.98.4-0ubuntu1) ...
Setting up libdvdnav4 (4.1.3-7) ...
Setting up libpostproc52 (4:0.7.3-0ubuntu0.11.10.1) ...
Setting up libfaac0 (1.28-0ubuntu1) ...
Setting up freepats (20060219-1) ...
Setting up libmpeg2-4 (0.4.1-3) ...
Setting up libmusicbrainz4c2a (2.1.5-6) ...
Setting up libmad0 (0.15.1b-5ubuntu1) ...
Setting up libfaad2 (2.7-6ubuntu1) ...
Processing triggers for libglib2.0-0 ...
Setting up libid3tag0 (0.15.1b-10build2) ...
Setting up libslv2-9 (0.6.6-9) ...
Setting up libavcodec-extra-53 (4:0.7.3ubuntu0.11.10.1) ...
Setting up libquicktime2 (2:1.2.3-4) ...
Setting up libts-0.0-0 (1.0-9) ...
Setting up libdirectfb-1.2-9 (1.2.10.0-4ubuntu3) ...
Setting up gstreamer0.10-plugins-ugly (0.10.18-3ubuntu1) ...
Setting up libavformat53 (4:0.7.3-0ubuntu0.11.10.1) ...
Setting up libmjpegtools-1.9 (1:1.9.0-0.5ubuntu5) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.21-1) ...
Setting up gstreamer0.10-plugins-bad (0.10.22-2ubuntu4) ...
Setting up gstreamer0.10-ffmpeg (0.10.12-1ubuntu1) ...
Setting up openjdk-6-jre-headless (6b23~pre11-0ubuntu1.11.10.1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/java to provide /usr/bin/java (java) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode.
Setting up openjdk-6-jre-lib (6b23~pre11-0ubuntu1.11.10.1) ...
Setting up libaccess-bridge-java (1.26.2-6) ...
Setting up ca-certificates-java (20110912ubuntu3) ...
Adding debian:SecureSign_RootCA11.pem
Adding debian:signet_pca2_pem.pem
Adding debian:spi-cacert-2008.pem
Adding debian:signet_tsa1_pem.pem
Adding debian:TÜB&#304;TAK_UEKAE_Kök_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;_-_Sürüm_3.pem
Adding debian:GlobalSign_Root_CA_-_R3.pem
Adding debian:Network_Solutions_Certificate_Authority.pem
Adding debian:GlobalSign_Root_CA_-_R2.pem
Adding debian:Microsec_e-Szigno_Root_CA_2009.pem
Adding debian:GeoTrust_Global_CA_2.pem
Adding debian:EBG_Elektronik_Sertifika_Hizmet_Sa&#287;lay&#305;c&#305;s&#305;.pem
Adding debian:Comodo_Secure_Services_root.pem
Adding debian:SwissSign_Silver_CA_-_G2.pem
Adding debian:COMODO_Certification_Authority.pem
Adding debian:Equifax_Secure_Global_eBusiness_CA.pem
Adding debian:NetLock_Express_=Class_C=_Root.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority.pem
Adding debian:TURKTRUST_Certificate_Services_Provider_Root_2.pem
Adding debian:ApplicationCA_-_Japanese_Government.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:TC_TrustCenter_Universal_CA_III.pem
Adding debian:Entrust.net_Secure_Server_CA.pem
Adding debian:Starfield_Class_2_CA.pem
Adding debian:Verisign_Class_4_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:cert_igca_dsa.pem
Adding debian:Equifax_Secure_CA.pem
Adding debian:AC_Raíz_Certicámara_S.A..pem
Adding debian:GTE_CyberTrust_Global_Root.pem
Adding debian:ACEDICOM_Root.pem
Adding debian:ca.pem
Adding debian:Wells_Fargo_Root_CA.pem
Adding debian:TC_TrustCenter_Class_3_CA_II.pem
Adding debian:UTN_USERFirst_Hardware_Root_CA.pem
Adding debian:QuoVadis_Root_CA.pem
Adding debian:ssl-cert-snakeoil.pem
Adding debian:OISTE_WISeKey_Global_Root_GA_CA.pem
Adding debian:ValiCert_Class_1_VA.pem
Adding debian:AddTrust_Qualified_Certificates_Root.pem
Adding debian:Autoridad_de_Certificacion_Firmaprofesional_CIF_A62634068.pem
Adding debian:Staat_der_Nederlanden_Root_CA.pem
Adding debian:GeoTrust_Primary_Certification_Authority_-_G3.pem
Adding debian:AddTrust_External_Root.pem
Adding debian:GeoTrust_Universal_CA.pem
Adding debian:Sonera_Class_2_Root_CA.pem
Adding debian:brasil.gov.br.pem
Adding debian:GeoTrust_Primary_Certification_Authority_-_G2.pem
Adding debian:GeoTrust_Global_CA.pem
Adding debian:signet_ca2_pem.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:RSA_Root_Certificate_1.pem
Adding debian:Microsec_e-Szigno_Root_CA.pem
Adding debian:AOL_Time_Warner_Root_Certification_Authority_1.pem
Adding debian:NetLock_Notary_=Class_A=_Root.pem
Adding debian:SecureTrust_CA.pem
Adding debian:GlobalSign_Root_CA.pem
Adding debian:Digital_Signature_Trust_Co._Global_CA_3.pem
Adding debian:thawte_Primary_Root_CA_-_G3.pem
Adding debian:Security_Communication_EV_RootCA1.pem
Adding debian:signet_ocspklasa3_pem.pem
Adding debian:Taiwan_GRCA.pem
Adding debian:VeriSign_Class_3_Public_Primary_Certification_Authority_-_G5.pem
Adding debian:UbuntuOne-Go_Daddy_Class_2_CA.pem
Adding debian:TC_TrustCenter_Universal_CA_I.pem
Adding debian:AddTrust_Low-Value_Services_Root.pem
Adding debian:Digital_Signature_Trust_Co._Global_CA_1.pem
Adding debian:ePKI_Root_Certification_Authority.pem
Adding debian:AddTrust_Public_Services_Root.pem
Adding debian:DST_ACES_CA_X6.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:UbuntuOne-Go_Daddy_CA.pem
Adding debian:SwissSign_Platinum_CA_-_G2.pem
Adding debian:signet_pca3_pem.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:IGC_A.pem
Adding debian:Comodo_AAA_Services_root.pem
Adding debian:CA_Disig.pem
Adding debian:TC_TrustCenter__Germany__Class_2_CA.pem
Adding debian:AOL_Time_Warner_Root_Certification_Authority_2.pem
Adding debian:VeriSign_Class_3_Public_Primary_Certification_Authority_-_G4.pem
Adding debian:thawte_Primary_Root_CA.pem
Adding debian:SwissSign_Gold_CA_-_G2.pem
Adding debian:QuoVadis_Root_CA_2.pem
Adding debian:Buypass_Class_2_CA_1.pem
Adding debian:signet_ocspklasa2_pem.pem
Adding debian:spi-ca-2003.pem
Adding debian:Thawte_Server_CA.pem
Adding debian:StartCom_Certification_Authority.pem
Adding debian:signet_ca1_pem.pem
Adding debian:DigiCert_Assured_ID_Root_CA.pem
Adding debian:TDC_Internet_Root_CA.pem
Adding debian:NetLock_Business_=Class_B=_Root.pem
Adding debian:COMODO_ECC_Certification_Authority.pem
Adding debian:ComSign_Secured_CA.pem
Adding debian:Global_Chambersign_Root_-_2008.pem
Adding debian:TDC_OCES_Root_CA.pem
Adding debian:Entrust.net_Premium_2048_Secure_Server_CA.pem
Adding debian:America_Online_Root_Certification_Authority_2.pem
Adding debian:Certigna.pem
Adding debian:Juur-SK.pem
Adding debian:Camerfirma_Global_Chambersign_Root.pem
Adding debian:DigiCert_Global_Root_CA.pem
Adding debian:UTN_DATACorp_SGC_Root_CA.pem
Adding debian:TURKTRUST_Certificate_Services_Provider_Root_1.pem
Adding debian:cacert.org.pem
Adding debian:signet_rootca_pem.pem
Adding debian:Verisign_Class_3_Public_Primary_Certification_Authority_-_G3.pem
Adding debian:America_Online_Root_Certification_Authority_1.pem
Adding debian:NetLock_Arany_=Class_Gold=_F&#337;tanúsítvány.pem
Adding debian:S-TRUST_Authentication_and_Encryption_Root_CA_2005_PN.pem
Adding debian:Comodo_Trusted_Services_root.pem
Adding debian:XRamp_Global_CA_Root.pem
Adding debian:UTN_USERFirst_Email_Root_CA.pem
Adding debian:Verisign_Class_4_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:GeoTrust_Universal_CA_2.pem
Adding debian:GeoTrust_Primary_Certification_Authority.pem
Adding debian:Entrust_Root_Certification_Authority.pem
Adding debian:DigiCert_High_Assurance_EV_Root_CA.pem
Adding debian:VeriSign_Universal_Root_Certification_Authority.pem
Adding debian:E-Guven_Kok_Elektronik_Sertifika_Hizmet_Saglayicisi.pem
Adding debian:Visa_eCommerce_Root.pem
Adding debian:Certplus_Class_2_Primary_CA.pem
Adding debian:DST_Root_CA_X3.pem
Adding debian:Chambers_of_Commerce_Root_-_2008.pem
Adding debian:Verisign_Class_1_Public_Primary_Certification_Authority_-_G2.pem
Adding debian:Thawte_Time_Stamping_CA.pem
Adding debian:signet_ca3_pem.pem
Adding debian:Baltimore_CyberTrust_Root.pem
Adding debian:Secure_Global_CA.pem
Adding debian:Go_Daddy_Class_2_CA.pem
Adding debian:Hongkong_Post_Root_CA_1.pem
Adding debian:NetLock_Qualified_=Class_QA=_Root.pem
Adding debian:ValiCert_Class_2_VA.pem
Adding debian:Thawte_Personal_Freemail_CA.pem
Adding debian:Cybertrust_Global_Root.pem
Adding debian:RSA_Security_2048_v3.pem
Adding debian:CNNIC_ROOT.pem
Adding debian:certSIGN_ROOT_CA.pem
Adding debian:Buypass_Class_3_CA_1.pem
Adding debian:Swisscom_Root_CA_1.pem
Adding debian:cert_igca_rsa.pem
Adding debian:Certum_Root_CA.pem
Adding debian:Equifax_Secure_eBusiness_CA_1.pem
Adding debian:ComSign_CA.pem
Adding debian:Equifax_Secure_eBusiness_CA_2.pem
Adding debian:WellsSecure_Public_Root_Certificate_Authority.pem
Adding debian:TC_TrustCenter__Germany__Class_3_CA.pem
Adding debian:Sonera_Class_1_Root_CA.pem
Adding debian:Firmaprofesional_Root_CA.pem
Adding debian:thawte_Primary_Root_CA_-_G2.pem
Adding debian:Camerfirma_Chambers_of_Commerce_Root.pem
Adding debian:Staat_der_Nederlanden_Root_CA_-_G2.pem
Adding debian:Deutsche_Telekom_Root_CA_2.pem
Adding debian:Izenpe.com.pem
Adding debian:Security_Communication_Root_CA.pem
Adding debian:QuoVadis_Root_CA_3.pem
Adding debian:Verisign_Class_2_Public_Primary_Certification_Authority.pem
Adding debian:TC_TrustCenter_Class_2_CA_II.pem
Adding debian:Thawte_Premium_Server_CA.pem
done.
Setting up libaccess-bridge-java-jni (1.26.2-6) ...
Setting up openjdk-6-jre (6b23~pre11-0ubuntu1.11.10.1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```




Matt2911

---

### Post by matt2911 on 2012-02-04
Bump?

---

### Post by oldos2er on 2012-02-04
Run ```
sudo dpkg --configure -a
``` when the EULA comes up use the Tab key to highlight Ok then press Enter.

---

### Post by sleepingdragon on 2012-02-07
Going back to your black screen issue, it may be that your monitor does not support lower resolutions that the graphics card is switching to temporarily before your login screen. I had a similar issue on an Nvidia 6200 card. Some monitors just don't like 640x480.

My way around it was to install startupmanager and change the resolutions there to 1024x768 with 24-bit colour. Try it, and do a reboot - see what happens (or not).

As oldos2er pointed out, hit TAB, then ENTER to highlight the OK on the EULA, it should carry on as normal from there.

---

### Post by matt2911 on 2012-02-13
Thanks I tried but as they say "no joy"
maXXXXXX@mXXXXXX-EP45-DS3R:~$ sudo dpkg --configure  -a
[sudo] password for maXXXXX1: 
mXXXXX1@mXXXX1-EP45-DS3R:~$ 

It just does nothing? maybe it did finish with the most recent command I don't know.  I still have the black screen at every boot.   One user reccomended installing video drivers see above.    just x ing out the user name just in case there are any hackers out there...
Matt

---

### Post by HiImTye on 2012-02-13
did you attempt to install the proprietary drivers from 'additional drivers' ?

---

### Post by matt2911 on 2012-02-13
I do not recall doing that specfically no, but I did some research and someone recomended installing synaptic package installer.  I forget which user that was but I can check my book marks after work today.  Also I have a updater that pops up from time to time telling me to update (did this twice in last two weeks) Last update was today and i skipped some of the foreign language packs as they were uneeded.

Matt

---

### Post by philinux on 2012-02-13
> **matt2911 said:**
> I do not recall doing that specfically no, but I did some research and someone recomended installing synaptic package installer.  I forget which user that was but I can check my book marks after work today.  Also I have a updater that pops up from time to time telling me to update (did this twice in last two weeks) Last update was today and i skipped some of the foreign language packs as they were uneeded.

Matt

I have nvidia 8600gt and this is what happens.

Plymouth + nVidia on my 8600GT has always produced this.

Stage 1 = Blank aubergine screen for most of the boot time.

Stage 2 = Logo with animated dots appears for a couple seconds.

Stage 3 = Black screen flicker flash

Stage 4 = Login window appears.

I've just got used to it now.

---

### Post by matt2911 on 2012-02-24
Well I tried to install a video driver like another member suggested but no joy again!  After install things did not work like system monitor and system testing.  These programs worked before I know.   So, I ended up uninstalling the driver(Nvidia from additional drivers).

---

### Post by cryptotheslow on 2012-02-25
> **philinux said:**
> I have nvidia 8600gt and this is what happens.

Plymouth + nVidia on my 8600GT has always produced this.

Stage 1 = Blank aubergine screen for most of the boot time.

Stage 2 = Logo with animated dots appears for a couple seconds.

Stage 3 = Black screen flicker flash

Stage 4 = Login window appears.

I've just got used to it now.

Exactly the same experience here with nvidia GTS-250 on Lucid. I did spend a little time originally trying to improve it, but the boot time is so quick anyway I figured it really doesn't matter as long as ends up with the login prompt.

---

### Post by roelforg on 2012-02-25
> **cryptotheslow said:**
> Exactly the same experience here with nvidia GTS-250 on Lucid. I did spend a little time originally trying to improve it, but the boot time is so quick anyway I figured it really doesn't matter as long as ends up with the login prompt.
The flickering is because when X takes over, first the kernel will turn it back into a console (flicker 1) then X will request a pixelbased screen (framebuffer) (flicker 2) and the kernel (again) tells the gfx-card to switch modes, the modeswitch causes the flicker while the card reinitializes. That's what my experience in OS-DEV tells me.

---

### Post by matt2911 on 2012-02-26
> **philinux said:**
> I have nvidia 8600gt and this is what happens.

Plymouth + nVidia on my 8600GT has always produced this.

Stage 1 = Blank aubergine screen for most of the boot time.

Stage 2 = Logo with animated dots appears for a couple seconds.

Stage 3 = Black screen flicker flash

Stage 4 = Login window appears.

I've just got used to it now.
This 8600GT seems similar to my 6600GT with similar problem.  So maybe if others have same issue then it may not be fixable.   Like I said I did install a video driver and got some improvement on colors at boot but had other problems.  The other problems made some programs not work like there was a driver conflict or something.  I think Linux has a default driver much like windows.  Now if I could just find a good health forum I will be all set:)

---

