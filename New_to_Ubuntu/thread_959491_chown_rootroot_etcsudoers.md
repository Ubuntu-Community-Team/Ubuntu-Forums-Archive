---
title: "chown root:root /etc/sudoers"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by sc3sc3 on 2008-10-26
hi,

i messed up a couple of things
and then found a forum thread where is was suggested
to boot into 'safe mode' and do:

chown root:root /etc/sudoers
chmod 440 /etc/sudoers
reboot

but now a couple of things are broken,
seems i lost the rights to do administrative things
even with sudo,
i can't connect to the internet anymore, ..

could you please help me fix this ?

thanks and good night
sc3*2

---

### Post by Xiong Chiamiov on 2008-10-26
> **sc3sc3 said:**
> hi,

i messed up a couple of things

> **sc3sc3 said:**
> 
but now a couple of things are broken,

Which things?

> **sc3sc3 said:**
> 
seems i lost the rights to do administrative things
even with sudo,

What happens when you try to sudo?

> **sc3sc3 said:**
> 
i can't connect to the internet anymore, ..

Separate problem that we'll need more information on.  You'll need to have root permissions first, though.

---

### Post by sc3sc3 on 2008-10-26
i can use sudo for certain things

but for example when i try to go to 
system > administration > network
( i want to repair my internet connection )
then i get the message 
" the configuration cannot be loaded
  you are not allowed to access the system administration"

same thing when i try to access 
system > administration > users and groups

thanks for your help !!
sc3*2

---

### Post by billgoldberg on 2008-10-26
Seriously, back up your data and do a clean reinstall.

You'll be up and running good again within the hour. 

Trying to fix the problem could take a lot longer.

---

### Post by Xiong Chiamiov on 2008-10-26
I believe that there is some sort of authenticate button in the prefs, that will allow you to enter your password and become root?

It seems that your wireless connection is actually your main problem, for which I'd recommend posting another thread.

---

### Post by sc3sc3 on 2008-10-26
the fact that my internet connection doesn't work
is also linked to a rights issue:

i found in the system logs:

"dhclient execve(/lib/dhcp3-client/call-dhclient-script,..): permission denied"

thanks
sc3*2

---

### Post by sc3sc3 on 2008-10-26
> **Xiong Chiamiov said:**
> I believe that there is some sort of authenticate button in the prefs, that will allow you to enter your password and become root?

It seems that your wireless connection is actually your main problem, for which I'd recommend posting another thread.

where is that button exactly ?

thanks
sc3*2

---

### Post by newton93 on 2008-10-26
> **sc3sc3 said:**
> the fact that my internet connection doesn't work
is also linked to a rights issue:

i found in the system logs:

"dhclient execve(/lib/dhcp3-client/call-dhclient-script,..): permission denied"

thanks
sc3*2

chown root:root /lib/dhcp3-client/call-dhclient-script

i guess.

---

