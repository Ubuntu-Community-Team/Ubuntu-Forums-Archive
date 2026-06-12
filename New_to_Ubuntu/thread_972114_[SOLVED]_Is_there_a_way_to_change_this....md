---
title: "[SOLVED] Is there a way to change this..."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by scprosser on 2008-11-05
Noob question. Is there any way to change (other than re-installing Ubuntu) the name that was assigned to a machine at install...my wife has decided she doesn't like the name she gave to her system and wants it changed.

(For example: in terminal, your prompt is [name]@[computer name], I need to change the [computer name] part to something different)

Can it be done?

Thanks in advance for any help offered.

---

### Post by Mr_JMM on 2008-11-05
System -> Administration -> Users and Groups

Select Unlock and then properties.

In older versions there were some conflict issues requiring new user groups and copied folders but I think this was resolved.


EDIT: This doesn't allow you to change username. I thnk you will have to create a new user then copy over the files.

---

### Post by cariboo on 2008-11-05
Open a Applications-->Accessories-->Terminal and type the following:

```
sudo hostname new_name
```

Then restart the computer.

---

### Post by scprosser on 2008-11-05
> **cariboo907 said:**
> Open a Applications-->Accessories-->Terminal and type the following:

```
sudo hostname new_name
```

Then restart the computer.

Ok, could you be a little more specific, or provide an example, I've tried various permutations of this with no luck.

For instance, if my user name is sean, and current computername is test1 (in Terminal would show as sean@test1) then what command (exactly) would I use to change the computername to test2 (so that in terminal it would show as sean@test2) (these are all just examples, but it will show me the syntax I need)

---

### Post by Coreigh on 2008-11-05
System >> Administration >> Network, General tab.

Change the _H_ost name line

---

### Post by scprosser on 2008-11-05
> **Coreigh said:**
> System >> Administration >> Network, General tab.

Change the _H_ost name line

I dont have such an entry in my Administration menu, I have Network Tools, but there is no general Tab>

I'm on Intrepid BTW.

---

### Post by bodhi.zazen on 2008-11-05
You need to be careful or you will break sudo.

You need to edit 2 files

/etc/hostname

and 

/etc/hosts

use any editor you like, ```
gksu gedit
```/etc/hostname is a one liner, straight forward

in /etc/hosts change the line :

> 127.0.1.1 computer_nameThen, IMO, always nice to reboot after changing the host name.

---

### Post by The Cog on 2008-11-05
[SIZE="3"]NOOOOooooo!!![/SIZE]

If you do that, sudo stops working.

You must change both /etc/hostname and /etc/hosts at the same time. Use the command:
**sudo gedit /etc/hosts /etc/hostname**
and change the name in both files. Double/triple check before saving both.

If you have already locked yourself out of sudo by only changong one of the two files, go into recovery mode and use these two commands to make them match:
[B]nano /etc/hostname
nano /etc/hosts[/B]

Edit - beaten to it by bodhi.

---

### Post by Yashiro on 2008-11-05
Log onto the machine with the account that installed Ubuntu.

Press Alt+F2
Type network-admin
Press Run.
Press Unlock.
Click the General tab.
Change the hostname.
Close the network admin panel.
Reboot.

If you go the manual route:

Do as above, gksu gedit. Then open both /etc/hosts and /etc/hostname
Put your new name in the /etc/hostname file.
Make sure your /etc/hosts file starts like this:

127.0.0.1 localhost
127.0.1.1 newhostnamehere

Save them both and reboot.

---

### Post by scprosser on 2008-11-05
Thanks Guys, that did the trick!

---

