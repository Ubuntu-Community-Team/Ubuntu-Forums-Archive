---
title: "My apt-get is really messed up. :("
date: 2006-03-30
forum: Repositories &amp; Backports
---

### Post by aduckie on 2006-03-30
This all occured a few days ago. I heard of Kino, so I went to Automatix. It worked previously, and it installed many codecs I love. But, it said it's auto-added... Doesn't seem like it. I went to Add New Applications. It freezes at:

```
Initializing:
/var/lib/dpkg/status
```

Stays like that forever. Okay. Let's try Synaptic. It tells me:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

I tried sudo apt-get clean followed by sudo apt-get update. It gave me:

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

I can't apt-get anything. Can someone please help me? I'm generally a Linux newbie, sorry.

---

### Post by aduckie on 2006-04-14
Bump.

...

---

### Post by Linoman on 2006-04-15
Sounds like your Ubuntu sources.list is messed up. What I would do is the following: First of all uninstall the program that Automatix installed. If I understand your post then its Kino that you installed. Use the following command in a terminal to uninstall Kino. 

sudo apt-get remove kino

If you still have a problem after that then I recommend uninstalling Automatix use the following command.

sudo apt-get remove automatix

Then in a terminal do the following:

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

Then in the sources list replace everything with the following lines (Please note I presume you are using Ubuntu 5.10 breezy badger and a 32 bit computer) 

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

Save the file and exit it. Then back in a terminal type the following

sudo apt-get update

hopefully that should solve your problem. Then after all that you can always reinstall Automatix etc.

---

### Post by fdoving on 2006-04-20
[QUOTE=aduckie]This all occured a few days ago. I heard of Kino, so I went to Automatix. It worked previously, and it installed many codecs I love. But, it said it's auto-added... Doesn't seem like it. I went to Add New Applications. It freezes at:

```
Initializing:
/var/lib/dpkg/status
```

Stays like that forever. Okay. Let's try Synaptic. It tells me:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

I tried sudo apt-get clean followed by sudo apt-get update. It gave me:

```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

I can't apt-get anything. Can someone please help me? I'm generally a Linux newbie, sorry.[/QUOTE]


Hi, take a look in /var/lib/dpkg/ look for a file named status-old.
If it's there make a copy of it replacing the existing 'status' file.

List files in /var/lib/dpkg:
```

ls -l /var/lib/dpkg/

```

Replace status with status-old:
```

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```


- Frode

---

