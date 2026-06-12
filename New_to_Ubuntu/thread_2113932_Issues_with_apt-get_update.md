---
title: "Issues with apt-get update"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by allynm on 2013-02-08
Hello everyone,

For several days I have received the following message at the end of the feedback from a call to "sudo apt-get update".  I have no idea what is happening or if I even should care. 

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 6A9653F936FD5529 Launchpad PPA for atareao

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/precise/Release](http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.I can't follow whether the update has actually happened or not.  A good deal of the reporting prior to this terminating material seems to indicate that files have actually been updated.  Could someone kindly explain what is going on?

Thank you,
Mark Allyn

---

### Post by schragge on 2013-02-08
Try this
```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

If it doesn't help then look for further solutions in [thread=1657004]this thread[/thread].

---

### Post by allynm on 2013-02-09
Good afternoon, Schragge,

It worked!  Thanks.

Mark

---

