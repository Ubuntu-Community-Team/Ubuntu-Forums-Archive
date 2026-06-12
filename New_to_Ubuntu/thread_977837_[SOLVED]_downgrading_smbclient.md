---
title: "[SOLVED] downgrading smbclient"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by LRT on 2008-11-10
i have ubuntu 8.10 installed which includes smbclient 3.2.3. i installed smbclient using apt-get smbclient.

this naturally installed version 3.2.3. but, i want version 3.0.28a (which came with 8.04).

how can i install the older version in place of the newer version????

---

### Post by quirks on 2008-11-10
1. Open **Synaptics Package Manager**.
2. Go to **Settings -> Repositories**.
3. Switch to the **Third-Party Software** tab.
4. Click the **Add ...** button.
5. Paste the following string into the popup box:
```
deb http://de.archive.ubuntu.com/ubuntu/ hardy main
```
6. Click the **Close** button.
7. Back in Synaptics, click the **Reload** button (upper left corner).
8. Search for **smbclient** and highlight the package.
9. Go to **Package -> Force Version ...**.
10. Choose the desired version from the drop-down box.
11. Click the **Force Version** button.
12. You will probably have to downgrade other packages as well. Make sure there is nothing vital listed and confirm it.
13. Finally, click the **Apply** button in Synaptics.
(14. I recommend disabling the Hardy repository again after this.)

If you have any problems following the above steps, let me know. I could not test it, because I still use Hardy myself, but in principal, it should work.

---

### Post by jimv on 2008-11-10
I'm curious as to why you would want to do such a thing.

---

### Post by LRT on 2008-11-11
> **quirks said:**
> 1. Open **Synaptics Package Manager**.
2. Go to **Settings -> Repositories**.
3. Switch to the **Third-Party Software** tab.
4. Click the **Add ...** button.
5. Paste the following string into the popup box:
```
deb http://de.archive.ubuntu.com/ubuntu/ hardy main
```
6. Click the **Close** button.
7. Back in Synaptics, click the **Reload** button (upper left corner).
8. Search for **smbclient** and highlight the package.
9. Go to **Package -> Force Version ...**.
10. Choose the desired version from the drop-down box.
11. Click the **Force Version** button.
12. You will probably have to downgrade other packages as well. Make sure there is nothing vital listed and confirm it.
13. Finally, click the **Apply** button in Synaptics.
(14. I recommend disabling the Hardy repository again after this.)

If you have any problems following the above steps, let me know. I could not test it, because I still use Hardy myself, but in principal, it should work.

i should have specified, i need to know how to do this from the command line with apt-get, but you were helpful because i didn't know you could do that with synaptic.

---

### Post by LRT on 2008-11-11
> **jimv said:**
> I'm curious as to why you would want to do such a thing.

i running BackupPC which for some reason doesn't work right with the latest version of samba.

---

### Post by LRT on 2008-11-11
this is what i've done so far

added the line ... deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main .... to sources.list

apt-get upgrade

apt-get install smbclient=3.0.28a-1ubuntu4.4

but apt-get tells me version is not found

---

### Post by quirks on 2008-11-11
> apt-get upgrade

apt-get install smbclient=3.0.28a-1ubuntu4.4

but apt-get tells me version is not found 

It should read
```
apt-get **update**
```
This **updates** the package list (with all available versions).

Your command **upgrades** all packages to the latest version.

You can get a list of all the available versions of the smbclient package with this command (to verify that the package list update worked):
```
apt-cache show smbclient | grep Version
```

---

### Post by LRT on 2008-11-11
sorry, "apt-get upgrade" was a typo.

i should also have typed:

 apt-get install smbclient=3.0.28a-1ubuntu**4** (notice no ".4" at the end)

this is solved! thanks for everyone's help.

---

