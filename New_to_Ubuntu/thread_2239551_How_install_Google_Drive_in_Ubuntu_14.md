---
title: "How install Google Drive in Ubuntu 14"
date: 2014-08-14
forum: New to Ubuntu
---

### Post by deme2 on 2014-08-14
I tried sudo add-apt-repository ppa:nemh/gambas3 && sudo apt-get update && sudo apt-get dist-upgrade but I got a message of deprecated method. Anyway, how can I install Google Drive in Ubuntu 14? I tried grive from software center and however I got the message that it is installed I didn't find how to start it and how to point to a folder for automatically updating.

---

### Post by Sanctimonious_Ape on 2014-08-14
Been looking into this myself.   Grive is command-line only, so try starting a terminal session and issuing the command "man grive" to learn how to use it.  If you don't [get grive working]("http://www.noobslab.com/2014/02/unofficial-google-drive-grive-tools.html"), the best option I've found so far (without [paying for it]("https://www.insynchq.com/")) appears to be [this one]("https://github.com/astrada/google-drive-ocamlfuse") (scroll down for the description).  However I've not had a chance to try it yet due to another problem I'm having at the moment, so I can't say for sure if it works -- it just looks like the best alternative since SyncDrive died thanks to the developer needlessly tying it to his domain and apparently never releasing the source code.

---

### Post by sotiris2 on 2014-08-14
Check [this](http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)out. Appears to be a front-end for grive.

---

### Post by Sanctimonious_Ape on 2014-08-14
Yeah, the first link I gave essentially links to that one, but you get the context of all the comments people have left about this method.  Basically it comes down to the fact that grive hasn't been updated for over a year, so doesn't appear to be actively maintained.  That would make me reluctant to invest too much time into it.  The alternative I gave was not only updated more recently (albeit by only half a year), but actually seems more capable to boot.  Its setup does appear to be more complex, however - I guess Spiderman's slogan applies to this web, too ("With great power comes great responsibility").

---

### Post by deme2 on 2014-08-14
What does it mean? What is the directory which I can paste some files and automaticaly it will be uploaded? What is the cloud drive default of Ubuntu?
deme@PC:~$ grive
grive: Symbol `json_tokener_errors' has different size in shared object, consider re-linking
Reading local directories

---

### Post by newb85 on 2014-08-15
> **deme2 said:**
> What does it mean? What is the directory which I can paste some files and automaticaly it will be uploaded? What is the cloud drive default of Ubuntu?

There isn't one.  Ubuntu used to have their own cloud drive (Ubuntu One), but when they discontinued it, I switched to Dropbox.  I've had no problems with it.

---

### Post by Paulgirardin on 2014-08-15
Copy is a better option.More free space and they don't appoint dodgy people to their board like Drop Box does.

---

### Post by deme2 on 2014-08-15
Thanks to everyone. For further seacher, in my case I installed Grive Tools 1.1 Beta and it is working for me exactlly as I want. I pointed to some folder and the syncronizing is automatic.

---

