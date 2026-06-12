---
title: "ubuntu is waiting for user to give nameserver"
date: 2018-05-25
forum: New to Ubuntu
---

### Post by amitp2 on 2018-05-25
Hi everyone , 

i am  trying to install ubuntu 16.04 in my VMware using kickstart.
When i am trying to install it don't know why is start waiting for user to give nameserver ip address even though i have added in my kickstart's .cfg file 


following is the content i have added in my kickstart

keyboard us
#System mouse
mouse
#System timezone
timezone America/New_York
#Root password
rootpw --disabled
#Initial user
user nxadmin --fullname "nxadmin" --iscrypted --password $1$cnq7N2Kw$W2au7QDXxQblpUChQLyqC/
#Reboot after installation
reboot
#Use text mode install
text
#Install OS instead of upgrade
install
#Use CDROM installation media
cdrom
#System bootloader configuration
bootloader --location=mbr
#Clear the Master Boot Record
zerombr yes
#Partition clearing information
clearpart --all --initlabel




#Advanced partition
part /boot --fstype=ext4 --size=500 --asprimary
part pv.aQcByA-UM0N-siuB-Y96L-rmd3-n6vz-NMo8Vr --grow --size=1
volgroup vg_mygroup --pesize=4096 pv.aQcByA-UM0N-siuB-Y96L-rmd3-n6vz-NMo8Vr
logvol / --fstype=ext4 --name=lv_root --vgname=vg_mygroup --grow --size=10240 --maxsize=20480
logvol swap --name=lv_swap --vgname=vg_mygroup --grow --size=1024 --maxsize=8192




#System authorization infomation
auth  --useshadow  --enablemd5


#Network information
network --bootproto=static --ip=192.168.81.57 --netmask=255.255.255.0 --gateway=192.168.81.1 --nameserver=192.168.71.20 --device=ens160


#Firewall configuration
firewall --disabled
#Do not configure the X Window System
skipx



after giving dns-nameserver everything is working fine  and it is not asking any further user interfere 



please let me know what should i do in this case.


Thanks All

---

