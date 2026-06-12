---
title: "Medibuntu"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by didiercool on 2008-07-08
I've been trying to make skype work on Ubuntu and found the following directions for the terminal (I'm running Hardy):

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install skype

After the second command I get an error which reads:

gpg: no valid OpenPGP data found

And now when I try to open Synaptic Package Manager I get this error:

E: Type '--22:40:38--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Help?

---

### Post by iaculallad on 2008-07-08
Move the original medibuntu.list file:

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.bak

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Bubba64 on 2008-07-08
9th post on this page has your correct input.
[http://ubuntuforums.org/showthread.php?t=851742&page=2](http://ubuntuforums.org/showthread.php?t=851742&page=2)

---

### Post by didiercool on 2008-07-08
K, everything appeared to work until the last line after which I got:

gpg: no valid OpenPGP data found

Thanks for helping!! :)

---

### Post by didiercool on 2008-07-08
K, I tried the 12th post command (#20) and it all worked until the end and I got the following error:

E: Type '--00:07:47--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

ideas?

---

### Post by iaculallad on 2008-07-08
Re: Medibuntu
K, I tried the 12th post command (#20) and it all worked until the end and I got the following error:

E: Type '--00:07:47--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

ideas?

What about doing:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Bubba64 on 2008-07-08
> **didiercool said:**
> K, I tried the 12th post command (#20) and it all worked until the end and I got the following error:

E: Type '--00:07:47--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

ideas?

The 19th post by forestpixie suggest that the lines from the medibuntu are incorrect and that you have to delete any wrong file.

---

### Post by didiercool on 2008-07-08
I think that's the set of commands I just did but maybe not... I tried it and got the same result:


E: Type '--00:07:47--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

after the last command.

---

### Post by iaculallad on 2008-07-08
Try this:

```
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get update && sudo apt-get upgrade
sudo aptitude install skype

```

---

### Post by didiercool on 2008-07-08
> **Bubba64 said:**
> you have to delete any wrong file.

How do I do that?  I thought, by the context of post #19, that in order to delete the offending file you run the commands he suggests.  I've now run them twice and returned the same error.  I must be missing something...

---

### Post by didiercool on 2008-07-08
> **iaculallad said:**
> Try this:

```
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get update && sudo apt-get upgrade
sudo aptitude install skype

```

After the first command I get:

E: Type '--00:19:48--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by didiercool on 2008-07-08
IT WORKED!!

Sorry, I didn't think to remove it with this command:

sudo rm /etc/apt/sources.list.d/medibuntu.list

before employing iaculallad's code.  When I did, everything worked perfectly and the package manager works just fine again!

Thanks all!!

---

### Post by iaculallad on 2008-07-08
Had you tried doing the 6th post of this thread, Where you are to delete the /etc/apt/sources.list.d/medibuntu.list file?

EDIT: OP had already done it, and, Success..

---

### Post by Bubba64 on 2008-07-08
> **didiercool said:**
> IT WORKED!!

Sorry, I didn't think to remove it with this command:

sudo rm /etc/apt/sources.list.d/medibuntu.list

before employing iaculallad's code.  When I did, everything worked perfectly and the package manager works just fine again!

Thanks all!!

I was going to suggest following this posts, I have seen the help this person provides. Yippee it works :)

---

### Post by didiercool on 2008-07-08
> **iaculallad said:**
> Had you tried doing the 6th post of this thread, Where you are to delete the /etc/apt/sources.list.d/medibuntu.list file?



I did, and I kept getting this:

E: Type '--00:19:48--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

But not until the last line of command.

---

### Post by iaculallad on 2008-07-08
> **didiercool said:**
> I did, and I kept getting this:

E: Type '--00:19:48--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

But not until the last line of command.

OK. Im glad you made it to work. Good luck.

---

### Post by didiercool on 2008-07-08
So, I may have rejoiced in haste.  Medibuntu worked just fine, but I went to open skype under the internet tab and it wasn't there.  I then reviewed what it told me about the skype installation and it said:

Couldn't find any package whose name or description matched "skype"

hmm...

---

### Post by starcannon on 2008-07-08
reinstall skype using synaptic package manager, that should fix it.

---

### Post by didiercool on 2008-07-08
When I search for Skype in the Package Manager it can't find it...

---

### Post by iaculallad on 2008-07-08
Navigate to System->Administration->Software Sources, under the "Ubuntu Software" tab, see to it that Main, Universe, Restricted, and Multiverse are ALL checked. Try to change your "Download From:" to "Main Server". Click on Close, and click on Reload on the next windows that pops.

Drop to your terminal:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install skype
```

---

### Post by didiercool on 2008-07-08
K, after clicking reload (and a lot of downloading), I ran the upgrade code and got this error:

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

I tried ignoring that and just ran the apt-get install and it still couldn't find it.  I also tried the 'sudo aptitude skype' thing but to no avail.  I tried looking for it in the package manager and no luck there either.

Any ideas?

---

### Post by iaculallad on 2008-07-08
Navigate to System->Administration->Software Sources, under the "Ubuntu Software" tab, uncheck the box w/c says "Installable from CD-ROM/DVD" and click on close. Do the reload on the next window and drop back again in your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get install skype
```

---

### Post by didiercool on 2008-07-08
K, you're right, the box was checked, and the first line did a lot of downloading of things, but the second still returned without finding skype.

E: Couldn't find package skype

---

### Post by aktiwers on 2008-07-08
Maybe some of this will help?
[http://ubuntuforums.org/showthread.php?t=852687](http://ubuntuforums.org/showthread.php?t=852687)

---

### Post by iaculallad on 2008-07-08
Ooowww... :confused: What about adding the official Skype repository for Debian and Ubuntu.

On your terminal:

```
gksudo gedit /etc/apt/sources.list
```

And add the line of texts below on the end-part of your sources.list file

> deb [http://download.skype.com/linux/repos/debian/stable](http://download.skype.com/linux/repos/debian/stable) non-free

Save and Close. Using the terminal again:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install skype
```

---

### Post by aktiwers on 2008-07-08
They also have debs on skypes website
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
(note it says 7.04**+**, so it works great on Hardy as well)

---

### Post by iaculallad on 2008-07-08
Or if you opt to perform the post above this post:

Click [here]("http://www.skype.com/go/getskype-linux-ubuntu") to get the .deb file, w/c will save it on your Desktop.

Once you had successfully downloaded the file named skype-debian_2.0.0.72-1_i386.deb, drop to your terminal and issue the command:

```

cd ~/Desktop
sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb
```

That should install it.

---

### Post by didiercool on 2008-07-08
> **iaculallad said:**
> 

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install skype
```

E: Malformed line 50 in source list /etc/apt/sources.list (dist parse)

I'm currently downloading the Ubuntu linked Skype file so that may work.

---

### Post by didiercool on 2008-07-08
> **iaculallad said:**
> Or if you opt to perform the post above this post:

Click [here]("http://www.skype.com/go/getskype-linux-ubuntu") to get the .deb file, w/c will save it on your Desktop.

Once you had successfully downloaded the file named skype-debian_2.0.0.72-1_i386.deb, drop to your terminal and issue the command:

```

cd ~/Desktop
sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb
```

That should install it.

THAT WORKED!!
I had to remove that line I added a few posts ago.  I am now running skype.  Thanks all!

---

