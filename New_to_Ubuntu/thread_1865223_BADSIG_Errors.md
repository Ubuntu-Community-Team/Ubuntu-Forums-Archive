---
title: "BADSIG Errors"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by axiomprime on 2011-10-19
Don't know if this is the place for this but I haven't been able to download anything from the software center or update manager since upgrading to 11.10.

Tried typing [sudo apt-get update] in terminal but got

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I don't know if this is a bug or just me doing something wrong. I'm not asking for help but I'd be grateful to anyone with an answer.

---

### Post by drs305 on 2011-10-19
> **axiomprime said:**
> Don't know if this is the place for this but I haven't been able to download anything from the software center or update manager since upgrading to 11.10.

Tried typing [sudo apt-get update] in terminal but got

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I don't know if this is a bug or just me doing something wrong. I'm not asking for help but I'd be grateful to anyone with an answer.
axiomprime,

Welcome to the Ubuntu Forums !

I've moved your post to its own thread.

The signatures aren't valid. You can import the correct ones with these commands:
```

sudo apt-get clean
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192 437D05B5
sudo apt-get update

```

If you can now get things working, please mark this thread SOLVED via the 'Thread Tools' link near the top right of the first post. That way I'll know you found this post and that it worked. If it doesn't work, we may need to run several more commands to clean things up.

Happy Ubuntu-ing !

---

### Post by axiomprime on 2011-10-19
Thanks for the help. Everything seemed to be going well until...

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192 437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring 
/tmp/tmp.jMCBw6oDh2 --trustdb-name /etc/apt/trustdb.gpg --keyring 
/etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver 
keyserver.ubuntu.com --recv-keys 3E5C1192 437D05B5
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
```

And then I was back to...

```
W: GPG error: http://extras.ubuntu.com oneiric Release: 
The following signatures were invalid: BADSIG 16126D3A3E5C1192 
Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://gb.archive.ubuntu.com oneiric Release: 
The following signatures were invalid: BADSIG 40976EAF437D05B5 U
buntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

Also, I'm not sure about the etiquette of copying and pasting code into boxes on forums.

---

### Post by drs305 on 2011-10-19
Copying errors and terminal output makes troubleshooting easier.

Looks like we need to clear out some records. Pop over to the following link and use Method 1. Don't include the $ or # symbols - they just represent the prompt.
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")

---

### Post by axiomprime on 2011-10-19
Tried both the methods on that page and I'm still hitting the same BADSIG errors. I'll try again tomorrow with some rested eyes. I don't actually need any new software so it's not urgent. Thanks for the help anyway as I've learnt a lot.

What I meant about pasting code is I'm not sure what bits are relevant and I was putting my own line-breaks in to make it easier to read. I don't know the done thing in these circles.

---

### Post by drs305 on 2011-10-20
For now, you should be able to clear the messages by opening Software Sources and disabling the 'Independent' (Extras) repository and changing the main repository server.
```

gksu software-properties-gtk
```
Go to the "Other Software" tab and untick the "Independent" listing(s). Then change the server, at least temporarily, [noparse](Download from:)[/noparse] in the "Ubuntu Software" tab to something other than what you currently have selected. When I try selecting the first entry under United Kingdom it won't take it, so there could be a problem with that server at present.

As far as displaying error messages, don't worry about trying to tidy things up. Just copy them. As long as you enclose them in 'code' tags it will be fine.

---

### Post by axiomprime on 2011-10-20
That seems to have unblocked most of the pipes and I've managed to update from the update manager and download some software from the software center but there are still things it won't let me download.

Thank you very much for your help.

---

### Post by drs305 on 2011-10-20
> **axiomprime said:**
> That seems to have unblocked most of the pipes and I've managed to update from the update manager and download some software from the software center but there are still things it won't let me download.

Thank you very much for your help.

There are no quotas for requests for help here on the Ubuntu Forums!  :-)

If you are still having issues that you would like us to assist with just keep asking. If you aren't getting the BADSIG errors, you should be able to re-enable the repositories you deselected earlier - especially if you changed servers as well. 

When all related issues are resolved or you don't plan on posting further in the thread you can mark the thread SOLVED via the 'Thread Tools' link near the top right of the original post.

---

