---
title: "Logging on as ROOT / Needing ROOT to update ClamAV"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by radi0j0hn on 2008-08-07
Just installed ClamAV and it asks me to log on as ROOT before I can update virus signatures.

First, this seems a bit dodgy.  Second, I've never logged on as ROOT and don't know the password.

Third, once logged on, can I change this so I don't have to log on as ROOT?

TIA

John

---

### Post by Atomic Dog on 2008-08-07
Try running the update command with "sudo" (without the quotes) in fron of it.  You will be prompted for your password, but then the command will be executed as root.

---

### Post by Thomazian on 2008-08-16
Hi radi0j0hn,

There may be another way to do it but being a new user, I used the command "sudo clamtk" from the terminal and updated using the GUI.

---

### Post by nicedude on 2008-08-16
He said he isn't the admin as I read it ( he said he doesn't know the password ie not admin ) but in general I would say that clamav is not needed on your Ubuntu system since it wont find any Ubuntu viruses ( because there aren't any available on planet earth ) so the only reason to want clamav is to scan windows partitions for windows viruses nothing else. I would say you can scan for windows viruses in windows and forget the word virus applies to computers in Ubuntu ( untill you hear otherwise here ). I have to admit I had windows itus when I first started using Ubuntu and felt I had to have AV and scan for viruses but soon learned all I was doing is wasting CPU cycles with the clam av process running :-) so rest assured you are quite safe from viruses here and be happy :-)

my 2 cents

---

