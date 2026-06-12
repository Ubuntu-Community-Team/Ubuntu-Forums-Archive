---
title: "Disable file sharing"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by 2_of_8 on 2008-09-05
I would like to turn off file sharing - right now, all the networked computers see shared files on each other's drives. Now, I do need to keep these shared files shared, so it's not an option to disable sharing on them. (They are on Windows) but I need to disable these Ubuntu machines from seeing those files. I do have a networked printer, however, which I do want access to.

Sorry if I made that complicated. Thanks for your help :)

Ubuntu 8.04

---

### Post by iaculallad on 2008-09-05
If those windoze shared folders are password-protected, No need to disable the file sharing service in Ubuntu (as long as you did not install samba, smbfs on it).

---

### Post by jemate18 on 2008-09-05
> **2_of_8 said:**
> I've set up Ubuntu on students' computers at school as a test project, to see how they react to it and if it's worth keeping. Seems fine for now, but I would like to turn off file sharing - right now, all the networked computers see shared files on each other's drives. Now, I do need to keep these shared files shared, so it's not an option to disable sharing on them. (They are on Windows) but I need to disable these Ubuntu machines from seeing those files. I do have a networked printer, however, which I do want access to.

Sorry if I made that complicated. Thanks for your help :)

Ubuntu 8.04
Do you have samba installed

---

### Post by 2_of_8 on 2008-09-05
I'd rather not password-protect the folders, since this Ubuntu is just a test and the shared folders have been there for a while and people would get mad if they changed :P

I did a clean Ubuntu install and then updated all the recommended updates. Does that mean I have Samba?

---

### Post by 2_of_8 on 2008-09-07
Bump please.

Perhaps you can tell me how to uninstall Samba, if that would solve the issue?

---

### Post by iaculallad on 2008-09-07
> **2_of_8 said:**
> Bump please.

Perhaps you can tell me how to uninstall Samba, if that would solve the issue?

On your terminal, stop the samba process first if it's running:

```
sudo /etc/init.d/samba stop
```

Then, run Synaptic, right click on samba and select 'mark for complete removal' and apply.

---

### Post by scrypt on 2009-06-18
> **iaculallad said:**
> On your terminal, stop the samba process first if it's running:

```
sudo /etc/init.d/samba stop
```

Then, run Synaptic, right click on samba and select 'mark for complete removal' and apply.

Can I just add the correct command to disable samba is

sudo /etc/init.d/networking samba stop

I understand you probably did post this but [code] wont post 'networking'

---

