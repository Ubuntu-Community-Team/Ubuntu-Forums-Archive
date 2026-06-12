---
title: "Error while trying to update"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by Hsakiv on 2012-03-10
I am constantly getting this error while trying to update Ubuntu 11.10. 
"W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead."

I really have no clue how to address this.

I read in a post regarding deleting some PPAs.

I am attaching the relevant screenshots.

Can anyone please tell me how to address this.

Thanks!

---

### Post by winh8r on 2012-03-10
try running these commands in this order:

```
sudo apt-get clean
```

```
sudo cd /var/lib/apt
```

```
sudo mv lists lists.old
```

```
sudo mkdir -p lists/partial
```

```
sudo apt-get clean
```

```
sudo apt-get update
```

---

### Post by disabled20191128 on 2012-03-10
Maybe there is a problem with the repo try updating later

---

### Post by Hsakiv on 2012-03-10
Thanks Guys!

@Winh8r: But it seems the issue is not getting resolved..the same error in the terminal as well.(PS Image)

@Dennisgre: Dear...I've posted only after waiting a good 21 days and constantly getting the same error.

Thanks anyways guys..

---

### Post by Hsakiv on 2012-03-16
Hi Guys

The issue got resolved. Looks like it had sth to do with Chromium. 
I uninstalled Chromium and since then it started getting updated.

Thanks everyone!

---

