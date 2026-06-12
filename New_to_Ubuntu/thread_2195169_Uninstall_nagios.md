---
title: "Uninstall nagios"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by AE14318791841955 on 2013-12-22
Hello

I have installed nagios in terminal 


[PHP]sudo apt-get install -y nagios3[/PHP]

how do i uninstall it?

i tried

[PHP]apt-get --purge remove nagios3[/PHP]

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I have then typed

[PHP]su[/PHP]

I filled in password

but its says  authentication failure

i am into root using this command
[PHP]sudo -i[/PHP]

it did work howhever it didn't uninstall completely any suggestions?

I also tried
[PHP]sudo apt-get remove nagios3[/PHP]

it also succeeded but i see still leftovers ... :(


Help me please i don't wanna reinstall ubuntu T_T

---

### Post by squakie on 2013-12-22
I'm not sure if it will help at this point or not, but you could also try:

sudo apt-get purge nagios3

---

### Post by claracc on 2013-12-23
This link: [http://askubuntu.com/questions/187888/what-is-the-correct-way-to-completely-remove-an-application](http://askubuntu.com/questions/187888/what-is-the-correct-way-to-completely-remove-an-application) can help you

---

