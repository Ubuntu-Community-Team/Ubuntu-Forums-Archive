---
title: "3G usb key E352 on ubuntu 12.04 LTS"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by wallian on 2012-12-03
hello,

If you don't success in making a E352 USB 3G key orange work on a labtop Dell E5510, you can try this :

--- download info page : ---
wget -U mozilla -k -np -O cle3g_bam_huawei.htm [http://namakutux.blogspot.fr/2012/07/bam-huawei-mobile-partner-for-linux.html](http://namakutux.blogspot.fr/2012/07/bam-huawei-mobile-partner-for-linux.html)

--- download package ---
wget -U mozilla -k -np [http://dl.dropbox.com/u/72782740/linux/bam-huawei-mobile-partner-linux.tar.gz](http://dl.dropbox.com/u/72782740/linux/bam-huawei-mobile-partner-linux.tar.gz)

--- installation as root on /usr/local/BAM_HUAWEI ---
apt-get install usb-modeswitch usb-modeswitch-data linux-headers-generic build-essential dkms 

tar xvfz bam-huawei-mobile-partner-linux.tar.gz
cd bam-huawei-mobile-partner-linux/mobile-partner-linux/
chmod +x install; ./install
cd bam-huawei-mobile-partner-linux
dpkg -i bam-huawei-desktop-integration_21.0.0_all.deb
chmod a+rX -R /usr/local/BAM_HUAWEI

--- application launched from Applications/Internet/BAM... or  /usr/local/BAM_HUAWEI/mobilPartner ---

-> menu tools/options -> new (=cle e352... forfait Let's GO)
       Access number :*99#
        User name : orange.fr
        Password : orange.fr
        APN : orange.fr
        
note1 : if installation in /usr/local/bam_huawei instead of /usr/local/BAM_HUAWEI, do ln -s  /usr/local/BAM_HUAWEI /usr/local/bam_huawei

Note2 : before installation, make sure packages are installed and update : 
usb-modeswitch usb-modeswitch-data linux-headers-generic build-essential dkms 


I hope it can help someone !

---

