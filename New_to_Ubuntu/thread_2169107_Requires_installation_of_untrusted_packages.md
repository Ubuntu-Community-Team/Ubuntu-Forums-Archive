---
title: "Requires installation of untrusted packages"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by Kanefa on 2013-08-20
I got the message "Requires installation of untrusted packages" the last few times I tried to download from Lubuntu Software Center.  I ended up using Synaptic each time and not thinking much of it.  Today I tried to add a new language and I got the message.  

Now I now something got messed.  Searching around I found a number of topics with things to try.  I'm just wondering what the heck happened and is there a way to see what the original source list was for 13.04 and correct it?  Thanks.

---

### Post by ibjsb4 on 2013-08-20
Run an update and upgrade in [terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and post any errors.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Kanefa on 2013-08-21
Here is what I got.

> E: Could not open lock file /var/lib/dpkg/lock - open (permission denied)
E: Unable to lock the administration directory (/var/libdpkg/), are you root?

---

### Post by alphacrucis2 on 2013-08-21
> **Kanefa said:**
> Here is what I got.

You probably had the update manager open so it owns the lock and the apt-get command cant run. You need to make sure the software centre, update manager or any other such program is closed before running the apt-get command.

---

### Post by Kanefa on 2013-08-21
I rebooted the machine and ran it again with the same results.

---

### Post by monkeybrain20122 on 2013-08-21
I think the update manager is running at startup so you would encounter that after reboot. Wait 5  minutes and try again, don't reboot. You can disable the update manager at start up from startup applications (search for it in the menu)

The warning "untrusted packages" is probably due to a gpg error in some repositories, probably a ppa. it is no big deal, just ignore it. If you use synaptic it would show you which one it is and you can fix it.

---

### Post by Kanefa on 2013-08-21
I ran the command that ibjsb4 gave me incorrectly.  I forgot the 2nd sudo.

Now when I run the command I receive a lot of 

> W: Failed to fetch [http://mg.archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages]("http://mg.archive.ubuntu.com/dists/raring-backports/multiverse/binary-i386/Packages")  Something wicked happened resolving 'mg.archive.ubuntu.com:http' (-11 - System error)

---

### Post by monkeybrain20122 on 2013-08-21
What archive is that? If you click the link you get 404 not found.

---

### Post by vasa1 on 2013-08-21
Can you go into Menu, Preferences, Software Sources and Updates? If you can, click on the Other Software tab and disable (untick) the entry that's causing the issue. Then do the sudo apt-get update, sudo apt-get upgrade thing and let us know what happens.

Also go into Updates and untick raring-proposed and raring-backports if they're ticked.

---

### Post by Kanefa on 2013-08-21
I also receive a 404.

Here are some additional lines.

> [http://mg.archive.ubuntu.com/ubuntu/dists/raring-backports/mulitverse/]("http://mg.archive.ubuntu.com/dists/raring-backports/multiverse/binary-i386/Packages")[URL="http://mg.archive.ubuntu.com/dists/raring-backports/multiverse/binary-i386/Packages"]source/Sources
http://mg.archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages[/URL]
[http://mg.archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages]("http://mg.archive.ubuntu.com/dists/raring-backports/multiverse/binary-i386/Packages")
[http://mg.archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages]("http://mg.archive.ubuntu.com/dists/raring-backports/multiverse/binary-i386/Packages")

---

### Post by vasa1 on 2013-08-21
One more thing is that you could try a new server in the first tab. Click on the dropdown next to "Download from" and choose Main Server.

---

### Post by Kanefa on 2013-08-21
The tab "Other Software" under "Software & Updates" only has Independent and Independent (Source Code) checked.  If I uncheck them nothing would be checked.  Both Canonical Partners and Canonical Partners (Source Code) are unchecked.

---

### Post by monkeybrain20122 on 2013-08-21
So maybe the server at your location is down. Try a different one. Open synaptic, go to Settings > Repositories > Ubuntu Software and choose a different server from the drop down box (say "Main") and then reload synaptic (click "reload")

---

### Post by monkeybrain20122 on 2013-08-21
> **Kanefa said:**
> The tab "Other Software" under "Software & Updates" only has Independent and Independent (Source Code) checked.  If I uncheck them nothing would be checked.  Both Canonical Partners and Canonical Partners (Source Code) are unchecked.

Your issue is not with the Partners' repo though.

---

### Post by Kanefa on 2013-08-21
Changing "download from:" to the "Main server" fixed my issues.  Thanks.

---

