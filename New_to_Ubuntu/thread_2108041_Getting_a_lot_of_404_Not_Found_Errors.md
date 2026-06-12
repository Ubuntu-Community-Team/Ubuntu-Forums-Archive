---
title: "Getting a lot of 404 Not Found Errors"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by cg40k on 2013-01-23
```
N: Ignoring file 'google-chrome.list]' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/fioan89/slidewall/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/gwibber-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
```

E: Some index files failed to download. They have been ignored, or old ones used instead.

Would like to learn how to get rid of these. Not very good with terminal, but am learning. Any help or direction pointing would be appreciated.

---

### Post by CharlesA on 2013-01-23
Remove the PPAs from Software Sources.

---

### Post by Elfy on 2013-01-23
> **CharlesA said:**
> Remove the PPAs from Software Sources.

You'll find all these PPAs in the Other Software Tab.

The fioan89 appears to be completely dead

The fyrmir and gwibber PPAs don't have quantal versions available. 

This line

> N: Ignoring file 'google-chrome.list]' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

suggests that there is a file in that directory with the wrong name

do a

```
ls /etc/apt/sources.list.d
```

from a terminal 

If there is in fact a file called google-chrome.list] then you can rename it 

```
sudo mv /etc/apt/sources.list.d/google-chrome.list] /etc/apt/sources.list.d/google-chrome.list
```

If you want to delete the others manually for practise then give us the output of the ls command so we aren't guessing.

Once you've done everything then you should be able to update without error

```
sudo apt-get update
```

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deadflowr on 2013-01-23
Sidenote: If you want to know where software sources can be found its in the system settings program.
The ppas are in the other software section.
After removing them, you'll need to reload, so an easy way is to open a terminal and run sudo apt-get update.
If any errors occur after doing so, you can copy and post them here.

---

### Post by cg40k on 2013-01-23
Here is the list from sources:

```
chris@chris-MS-7529:~$ ls /etc/apt/sources.list.d
atareao-atareao-precise.list
atareao-atareao-precise.list.distUpgrade
atareao-atareao-precise.list.save
atareao-lenses-quantal.list
atareao-lenses-quantal.list.save
diodon-team-stable-quantal.list
diodon-team-stable-quantal.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
fioan89-slidewall-quantal.list
fyrmir-compiz-plugins-quantal.list
fyrmir-compiz-plugins-quantal.list.save
fyrmir-livewallpaper-daily-quantal.list
fyrmir-livewallpaper-daily-quantal.list.save
google-chrome.list
google-chrome.list]
google-chrome.list.distUpgrade
google-chrome.list.save
google-musicmanager.list
google-musicmanager.list.save
gwibber-team-ppa-quantal.list
gwibber-team-ppa-quantal.list.save
indicator-multiload-stable-daily-precise.list
indicator-multiload-stable-daily-precise.list.distUpgrade
indicator-multiload-stable-daily-precise.list.save
opera.list
opera.list.distUpgrade
opera.list.save
precise-partner.list
precise-partner.list.distUpgrade
precise-partner.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-65_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-65_ubuntu.list.save
scopes-packagers-ppa-quantal.list
scopes-packagers-ppa-quantal.list.save
steam.list
steam.list.save
ubuntu-mozilla-security-ppa-quantal.list
ubuntu-mozilla-security-ppa-quantal.list.save
xorg-edgers-ppa-quantal.list
xorg-edgers-ppa-quantal.list.save
yorba-ppa-precise.list
yorba-ppa-precise.list.distUpgrade
yorba-ppa-precise.list.save
```

---

### Post by cg40k on 2013-01-23
This is what I am now getting (after sudo apt-get update):



```
N: Ignoring file 'google-chrome.list]' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```


*Updated as I removed the duplicates*

---

### Post by cg40k on 2013-01-23
Thanks for all the help by the way as all but the google-chrome.list has been fixed. Huge thanks.

Update: For the google-chrome.list] im getting this:

```
chris@chris-MS-7529:/etc/apt$ rm /etc/apt/sources.list.d/google-chrome.list]
rm: remove write-protected regular file `/etc/apt/sources.list.d/google-chrome.list]'? y
rm: cannot remove `/etc/apt/sources.list.d/google-chrome.list]': Permission denied 
```

Taking it I need to log into root to remove?

---

### Post by CharlesA on 2013-01-23
Just use sudo:

```
sudo mv /etc/apt/sources.list.d/google-chrome.list] /etc/apt/sources.list.d/google-chrome.list
```

That will fix that PPA. If you want to remove it entirely, just use sudo with rm.

---

### Post by cg40k on 2013-01-23
> **CharlesA said:**
> Just use sudo:

```
sudo mv /etc/apt/sources.list.d/google-chrome.list] /etc/apt/sources.list.d/google-chrome.list
```

That will fix that PPA. If you want to remove it entirely, just use sudo with rm.

Thank you good sir!

---

### Post by arpanaut on 2013-01-23
For reference: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Elfy on 2013-01-23
> **cg40k said:**
> ...

Update: For the google-chrome.list] im getting this:..

Taking it I need to log into root to remove?

> **CharlesA said:**
> Just use sudo:

```
sudo mv /etc/apt/sources.list.d/google-chrome.list] /etc/apt/sources.list.d/google-chrome.list
```

That will fix that PPA. If you want to remove it entirely, just use sudo with rm.
I could have sworn black is white that I'd put that in my post, seems like I had an errant reference to a thread that only 36 people would have been able to read - changed it now :)

---

### Post by CharlesA on 2013-01-23
> **Elfy said:**
> I could have sworn black is white that I'd put that in my post, seems like I had an errant reference to a thread that only 36 people would have been able to read - changed it now :)

That explains why I wondered how that would apply to this. :lol:

---

