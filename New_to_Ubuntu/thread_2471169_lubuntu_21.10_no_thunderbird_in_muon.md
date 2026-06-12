---
title: "lubuntu 21.10 no thunderbird in muon"
date: 2022-01-22
forum: New to Ubuntu
---

### Post by nginmu on 2022-01-22
Fresh install of Lubuntu 21.10; I can't find Thunderbird listed in Muon package manager.

Is it in a non standard repo or something?

---

### Post by KBar on 2022-01-22
No. [It's]("https://packages.ubuntu.com/impish-updates/amd64/thunderbird/download") still in the main repository. What's the output of:```
apt-cache policy thunderbird
```

---

### Post by nginmu on 2022-01-22
```

me@skully:~$ apt-cache policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:91.5.0+build1-0ubuntu0.21.10.1
  Version table:
     1:91.5.0+build1-0ubuntu0.21.10.1 500
        500 http://archive.ubuntu.com/ubuntu impish-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu impish-security/main amd64 Packages
     1:91.1.2+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu impish/main amd64 Packages
me@skully:~$ 

```

but wait.. I just found it by selecting the email category on the left, and manually scrolling down on the right, alphabetically down to the "t"'s

t-prot..
tart..
bingo. thunderbird

I don't know why typing 'thu.. ' etc in the search bar, didn't bring it up.. like how you get firefox showing up if you type 'firef...

All I was getting was something called bolt, which had thunder.. in the description

---

### Post by KBar on 2022-01-22
That's because the string you gave it is ambiguous. The very first result that matches the pattern 'thu' in package description is this:```
bolt/focal-updates,now 0.8-4ubuntu1 amd64 [installed,automatic]
  system daemon to manage thunderbolt 3 devices

```

---

### Post by nginmu on 2022-01-22
I'm trying to find gnome-disk-utility as well but having a similar problem

---

### Post by KBar on 2022-01-22
Your search string and the results you're getting?

---

### Post by nginmu on 2022-01-22
gnome-disk-utility
gnome-disks-
 - nothing (blank)

gnome, gnome-, disks, -disks
 - various packages but not gnome disks

---

### Post by KBar on 2022-01-22
That's really strange. Does it at least show up with this:
```
apt search gnome disks
```

---

### Post by nginmu on 2022-01-22
```

me@skully:~$ apt search gnome disks
Sorting... Done
Full Text Search... Done
gnome-disk-utility/impish,now 41.0-1ubuntu1 amd64 [installed]
  manage and configure disk drives and media

policykit-desktop-privileges/impish,impish,now 0.21 all [installed,automatic]
  run common desktop actions without password

sensors-applet/impish 3.0.0+git6-0.5ubuntu1 amd64
  Display readings from hardware sensors in your Gnome panel

me@skully:~$ 


```

but, this was after I'd done the following in terminal

```

sudo apt install gnome-disk-utility

```

(which worked ok)

---

### Post by KBar on 2022-01-22
Right. **apt search** just performs a search in enabled repositories. 

I don't know how Muon works but a glimpse into its code tells that its backend is *apt-xapian-index*, so the issue is most likely somewhere within it. Or maybe it just works in a totally different way.

---

### Post by nginmu on 2022-01-22
I installed Synaptic, no problems with that, all the ones that aren't showing up in Muon, are showing up fine in Synaptic.

Not completely happy with the way I've got my system arranged so I'm going to reinstall again anyway; once done I'll try Muon again and see if anything's different

---

### Post by nginmu on 2022-01-24
Just for completeness a day later, I've not reloaded anything yet, and Muon is now finding everything I ask of it.

---

