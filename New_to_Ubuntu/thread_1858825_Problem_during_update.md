---
title: "Problem during update"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-10-13
I tried to do an update using the Update Manager program, and got an error message. It said:

```
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011k-0ubuntu0.10.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011k-0ubuntu0.10.04_all.deb)
   Something wicked happened resolving /us.archive.ubuntu.com:http (-5 - No address associated with hostname)
```

NOTE: The messaging system is refusing to include vital data. (I can't see it, after it's posted!) The data being deleted is part of the address that couldn't be resolved. After ubuntu.com, it should read (delete the spaces): /ubuntu /pool /main /t /tzdata-java_2011k- 0ubuntu0.10.04_all.deb

I'd never seen the term "wicked" used in an error message before. What's going on here?
TIA, for assistance.

---

### Post by sadaruwan12 on 2011-10-13
Bro I also use 10.04 on my home desktop and never had this type of error message for me this smells fishy.

What I would do is do a fresh install normally I use a separate partition for my home so if you have your home on a separate partition do a fresh install to be on the safe side.

---

### Post by lolpenguin on 2011-10-13
This doesn't seem like a genuine error message, but try "sudo apt-get update" (without the inverted commas) and try the update again. I don't use LXDE but this should work (if there is a genuine problem requiring the repos to be reloaded) on all variants

---

### Post by Lisiano on 2011-10-13
apt is agnostic to the DE you use. Try ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
I encountered that error before, it was due to my DNS failing (My router is quite decent but it has a fail DNS implementation, it fails regularly, I just switched to OpenDNS and Google DNS and it works marvelously)
Also it might mean that the server is down for maintenance or something.
You can see if it's on and available by going to that address in a web browser. [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/)
Basically the same URL it tried to resolve minus the package name (The one with .deb at the end)

Btw. If apt works perfectly but the LXDE Update Manager keeps failing, it might be a problem inside Update Manager, you can use Synaptic or apt to update (Not sure if LXDE has Ubuntu Software Center)

---

### Post by scruffyeagle on 2011-10-14
> **Lisiano said:**
> apt is agnostic to the DE you use. Try ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
I encountered that error before, it was due to my DNS failing (My router is quite decent but it has a fail DNS implementation, it fails regularly, I just switched to OpenDNS and Google DNS and it works marvelously)
Also it might mean that the server is down for maintenance or something.
You can see if it's on and available by going to that address in a web browser. [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/)
Basically the same URL it tried to resolve minus the package name (The one with .deb at the end)

Btw. If apt works perfectly but the LXDE Update Manager keeps failing, it might be a problem inside Update Manager, you can use Synaptic or apt to update (Not sure if LXDE has Ubuntu Software Center)

Thanks, Lisiano! It's reassuring to me, to know that someone else has seen this error message; i.e., that it's not an indication that my system was hacked & damaged. I didn't specify this in my original post, but I'm using the Gnome DE. I added more software yesterday, so now I get an Ubuntu Studio intro when powering up, but really the DE is still Gnome.

It's also worth knowing in case I ever see this again, that you'd pegged it as being a DNS failure. I haven't tried the update manager since I posted about the error here, so I'll probably do that after I log off & shut down FF.

And, if the UM still can't do it, I'll try the command line approach using "clean" as the 1st of 3 commands.

Your suggestion about browsing to the pool makes a lot of sense too. I hadn't realized you could do that without being in the process of trying to download. (So, now I know!)

Thanks!

---

