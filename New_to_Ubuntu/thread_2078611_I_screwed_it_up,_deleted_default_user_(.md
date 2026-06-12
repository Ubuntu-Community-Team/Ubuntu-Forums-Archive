---
title: "I screwed it up, deleted default user :("
date: 2012-10-31
forum: New to Ubuntu
---

### Post by arifalisyed on 2012-10-31
Hey there,
          I have Xubuntu 12.10 installed on my machine.
While installing i had created a user 'lalu' , 
later on after few setting changes i screwd up something and now after login 
1) mouse cusrsor was not coming  
2) any app that i open was not visible in task bar

to avoid these problm , i created a new user 'arif' , made him admin.

once that's done. I logged in a arif and everything was fine with 
this new user.

Since 'lalu' was default user ( and automatic login was enabled) 
by default when i boot my mahchie, i used to get logged in as 'lalu', which was a screwed up user.

so i logged in as 'arif' and deleted 'lalu'


After this my life is screwed even more.
Now i can't install/uninstall any software or take updates.

Please help

---

### Post by arochester on 2012-10-31
1) To reset Root look somewhere like here: [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

2) To get apps in the panel, go RIGHT click panel>Panel>Add new items>(ADD) Windows Buttons

3) When my cursor disappeared I *think* I had to restart the windows manager with something like: 
> sudo xfwm4 --replace

---

### Post by Lars Noodén on 2012-10-31
You can boot in to rescue mode with the live CD and then add the new user to the groups adm, cdrom, sudo, dip, plugdev, lpadmin, and sambashare.  The group sudo is the most important as far as admin tasks go.

---

### Post by arifalisyed on 2012-10-31
> **arochester said:**
> 1) To reset Root look somewhere like here: [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

2) To get apps in the panel, go RIGHT click panel>Panel>Add new items>(ADD) Windows Buttons

3) When my cursor disappeared I *think* I had to restart the windows manager with something like:



Wow this worked for me quite smoothly.
changed the root user's password. 
Thanks a ton.


Even though i specified user type as admin ( not as desktop user) it still keeps asking me root password for everything ..
how do i add this user 'arif' to various admin groups ?

---

### Post by pandacookie on 2012-10-31
This happened to me before. The information at this link is what helped me: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

EDIT: Ah, I see you fixed your issue. I was too late with my advice, lol.

---

### Post by arifalisyed on 2012-10-31
> **pandacookie said:**
> This happened to me before. The information at this link is what helped me: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

EDIT: Ah, I see you fixed your issue. I was too late with my advice, lol.

thats perfectly fine :)

do you know how do i avoid annoying dialog that keeps asking root password for everything i do.

even though my new user is an administrative user still it keeps asking password now and then

---

### Post by dannyboy79 on 2012-10-31
> **arifalisyed said:**
> thats perfectly fine :)

do you know how do i avoid annoying dialog that keeps asking root password for everything i do.

even though my new user is an administrative user still it keeps asking password now and thenit's done on purpose, IF you're doing a lot of work which requires root then you can change to root with 
```
sudo -i
```
and enter your user password. Once done with all your root work, I would exit out of the root user though.
You can read all about sudo here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by arifalisyed on 2012-10-31
> **dannyboy79 said:**
> it's done on purpose, IF you're doing a lot of work which requires root then you can change to root with 
```
sudo -i
```
and enter your user password. Once done with all your root work, I would exit out of the root user though.
You can read all about sudo here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for responding. I get an error arif is not in sudoers file

by the way will this work only for terminal or 
normal UI usage of Xubuntu session as well ?

---

