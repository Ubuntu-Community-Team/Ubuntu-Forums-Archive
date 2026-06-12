---
title: "wifi and ethernet default name, dhcp lease, bluetooth, search command in grub"
date: 2017-05-06
forum: New to Ubuntu
---

### Post by sb2017 on 2017-05-06
Hello Everyone,

I am new to Linux and I have a series of questions about my HP Laptop. I will be really grateful for your valuable feedback.

First question: 

I cannot change the name of my interfaces permanently. The default name of my interfaces are:
wlp13s0 for with,
enp7s0 for ethernet.

I am using the commands below to change the names :

ip link set wlp13s0 name wlan0
ip link set enp7s0 name eth0

However the change is not persistant and when I reboot the names are changed back to wlp13s0 (for with) and enp7s0 (for ethernet). 
I formatted the whole disk and tried installing Windows 10 and Fedora Linux, however the interfaces names are the same wlp13s0 and enp7s0. How to change these default names? Will bios update can be of any help? How can I check?

Second question:

With all three OS I tried, by default my laptop ip address is : 192.168.43.70.

I am using my mobile as wifi hotspot to connect to my laptop. My mobile gets dynamic ip. I am assuming I should get a dynamic ip in my laptop as well. However the ip address is static. 

After grep I found a file in /var/lib/NetworkManager/dhclient-6612cfce-15e9-4112-8970-19fcb40d1d48-wlp13s0.lease.

Here this ip address is mentioned, I tried commenting all the lines of this file, however the comments got removed.

How do I make my Laptop ip dynamic?

Third question:

Before boot if I edit the grub menu "ubuntu", I get a line :

search --no-floppy --fs-uuid --set=root --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2 e6211905-a1ec-4bc4-aa09-c87f3e08cdf9

I am yet to understand most part of this code , however I didnot understand the syntex "baremetal=ahci0,gpt2".

With the command 
rfkill list , I get in these options:

1. phy0: Wireless LAN
Soft blocked : yes
Hard blocked : no
2. hci0 : Bluetooth
Soft blocked : yes
Hard blocked : no

Is hci0 and ahci0 related ? Is grub searching for a file through bluetooth device?

Finall even if I edit and remove everything except > linux and initramfs in grub it is not persistant. Is there anything to do with grub.cfg?

I understand I have asked a lot of question in one post , however I wanted to give adequate information about my laptop and if it has anything to do with misuse of data and privacy. I will be thankful for your valuable feedback and if this is of any help to anyone.

Yours sincerely,
sb

---

### Post by QIII on 2017-05-06
Hello!

It is best to start one thread for each question.  A "laundry list" thread becomes confusing very quickly -- both for you and those who are trying to answer.  Some people who might otherwise be able to help with one question on another will often move on without comment because of that.

Would you please edit your post so that it contains one of your questions.  Take the other two and start a new thread for each of the questions.

Thanks!

---

### Post by howefield on 2017-05-06
Duplicate thread closed.

---

