---
title: "Command &quot;sudo apt-get update&quot; do not work and return error message"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by iyasin on 2013-05-11
hi all, 
i am using ubuntu 13.04(i have upgraded it from u12.10), now i have a problem with it. when i enter the command "sudo apt-get update" in terminal, it get below error
```
E: GPG error: http://extras.ubuntu.com raring Release: The following signatures were invalid: NODATA 1 NODATA 2
```

i followed below instructions but that error occupied for me too:
```

sudo apt-get clean
sudo mv /var/lib/apt/lists /tmp
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
```

how can i solve this problem?
tnx.

---

### Post by ranger1021994 on 2013-05-11
Try this way : 
Install Y-PPA Manager
Go to Advanced tab
Select fix GPG BADSIG error
The above commands do the same i guess but give this method a shot

---

### Post by iyasin on 2013-05-11
> **ranger1021994 said:**
> Try this way : 
Install Y-PPA Manager
Go to Advanced tab
Select fix GPG BADSIG error
The above commands do the same i guess but give this method a shot

i have installed it, and do fix GPG BADSIG error option but this error returned to me
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com raring Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by oldos2er on 2013-05-11
iyasin, see post #6 in [this thread ]("http://ubuntuforums.org/showthread.php?t=1661773"). I'm not sure why suggestions are for BADSIG errors when you're seeing a NODATA error.

---

### Post by iyasin on 2013-05-11
> **oldos2er said:**
> iyasin, see post #6 in [this thread ]("http://ubuntuforums.org/showthread.php?t=1661773"). I'm not sure why suggestions are for BADSIG errors when you're seeing a NODATA error.
 
tnx, i try it

---

