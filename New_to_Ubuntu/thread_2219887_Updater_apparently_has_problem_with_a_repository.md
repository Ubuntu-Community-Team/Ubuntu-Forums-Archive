---
title: "Updater apparently has problem with a repository"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by Peter_Heft on 2014-04-25
Please help again.
Am running Ubuntu 12.04.  Am getting the red triangle indicating a problem with the update manager, 'information is out of date'.  Yesterday said last updated 10 days ago, today 11 days.  Manual updates work.  [http://askubuntu.com/questions/424381/update-information-outdated-conflicting-message](http://askubuntu.com/questions/424381/update-information-outdated-conflicting-message)  seems to address the problem except that I can not find the talked about list of repositories.  The 'other sources' under edit is actually 'other software' and the choices in 'independent' are binary or source.  Where is the list hiding?.

Please help, thanks,
Peter

---

### Post by grahammechanical on 2014-04-25
If we run 
```
sudo apt-get update
sudo apt-get upgrade
```

we usually get an error message about not able to access some repository or other. That will give you a clue. Have you installed any PPAs? After using a PPA to install software we should disable that PPA to avoid errors like this.

Without that error message from apt-get I do not think that we can be more specific.

Regards.

---

### Post by Peter_Heft on 2014-04-25
Thanks for the quick response.  I don't know if I istalled any PPAs, but it seems likely. 
I ran the code and got the following:
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ibjsb4 on 2014-04-25
[COLOR=#000000]GPG error: [/COLOR][COLOR=#000000]BADSIG[/COLOR]

[http://ubuntuforums.org/showthread.php?t=2219569&p=13001327#post13001327](http://ubuntuforums.org/showthread.php?t=2219569&p=13001327#post13001327)

---

### Post by Peter_Heft on 2014-04-25
Thank you both, update manager is working again.

---

