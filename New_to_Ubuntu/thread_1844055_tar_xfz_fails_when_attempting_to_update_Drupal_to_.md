---
title: "tar xfz fails when attempting to update Drupal to 6.22"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by willow315 on 2011-09-14
I am running Ubuntu 10.04 in Virtual Box 9 on a MAC. I installed Ubuntu via apt-get and am attempting to update the core of Drupal 6 (CMS). The file is a tar.gz file and my download was successful, but all attempts to extract the file using tar- xfz filename  or tar -zxvpf filename fails with an error of "cannot open file, no such file or directory." And I had done an "ls" to see that, in fact, the file I want to extract is there. The error "no such file or directory" is repeated after a listing of each file in the archive, though. It's totally confusing. If in fact it's listing a file from an archive, how can it not exist? Either the tar.gz file or the individual file in the archive. 

I really appreciate any assistance anyone could give me, because without being able to resolve this issue, I am dead in the water. I MUST be able to update files, and most if not all files for Drupal are in tar.gz format.

I successfully use the "tar -xfz command on CentOS and Debian. Is there some reason that it won't work on Ubuntu? I have found directions for it's use on Ubuntu Server. I am using the Ubuntu Desktop, however. 

I have tried the command with and without "sudo." Don't know what else to try. 

Thanks, WCW

---

### Post by LowSky on 2011-09-14
What happens if you do this?
```

tar -xvzf drupal*
```

But if you are using the desktop version why not point & click the tar, extract it using the GUI to the folder of your choice. That is an option.

---

