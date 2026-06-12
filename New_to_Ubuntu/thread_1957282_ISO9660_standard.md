---
title: "ISO9660 standard"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by newport_j on 2012-04-12
I am trying to copy a 2 gigabyte file to a DVD tha can easily hold it. But when I start it I get the message:
 
 
The size of the file is over 2 GB. Files larger thsn two gigabytes are not supported by ISO9660 standard in its first and second versions (the most widespread ones). It is recommended to use the third version of ISO9660 standard which is supported by most operating systems,, including Linux and all versions of Windows. However, MAC OS X cannot read images created with version 3 of the ISO9660 standard. 
 
 
 
Then I get a message to either always add a file of never add a file. I must answer to always add file. If i do not then the copying to DVD process ends. What file am I adding and can I put it all back together if the need arrises?
 
Since this is all a backup, I have taken the option to always add a file and I have got my coping to DVDs done. However, i am worried about what I got. I hope that I will not have any problems putting this tgz file back toger if i have to to,
 
Any help appreciated. Thanks in advance.
 
Newport_j

---

### Post by idoitprone on 2012-04-12
> **newport_j said:**
> I am trying to copy a 2 gigabyte file to a DVD tha can easily hold it. But when I start it I get the message:
 
 
The size of the file is over 2 GB. Files larger thsn two gigabytes are not supported by ISO9660 standard in its first and second versions (the most widespread ones). It is recommended to use the third version of ISO9660 standard which is supported by most operating systems,, including Linux and all versions of Windows. However, MAC OS X cannot read images created with version 3 of the ISO9660 standard. 
 
 
 
Then I get a message to either always add a file of never add a file. I must answer to always add file. If i do not then the copying to DVD process ends. What file am I adding and can I put it all back together if the need arrises?
 
Since this is all a backup, I have taken the option to always add a file and I have got my coping to DVDs done. However, i am worried about what I got. I hope that I will not have any problems putting this tgz file back toger if i have to to,
 
Any help appreciated. Thanks in advance.
 
Newport_j

use a better compression such as 7z or gz2, so you only have to copy less. 
For the MAC OS X not support version 3 ISO standard, just go and yell at apple. It the only way you can get support for 2.0iso or larger.

Please tell me that you are not using apple's file system to store files

[http://arstechnica.com/apple/reviews/2011/07/mac-os-x-10-7.ars/12](http://arstechnica.com/apple/reviews/2011/07/mac-os-x-10-7.ars/12)

this will be a great read because linux filesystems are the best and apple is the worst

---

### Post by newport_j on 2012-04-12
I am not using anything by Apple in file compression. I have completed the backup and I want to begin using this PC again. It uses Ubuntu 11.04. I just want to make sure that this is a good backup and should the need arise, I can restore quickly and easily even with this wrinkle in the backup (the IS9660 third standard).
 
Can be assured this can now be restored?
 
Newport_j

---

### Post by idoitprone on 2012-04-12
> **newport_j said:**
> I am not using anything by Apple in file compression. I have completed the backup and I want to begin using this PC again. It uses Ubuntu 11.04. I just want to make sure that this is a good backup and should the need arise, I can restore quickly and easily even with this wrinkle in the backup (the IS9660 third standard).
 
Can be assured this can now be restored?
 
Newport_j

the problem with apple is not the file compression tool, because they use open source tools as well to save cost, but their filesystem. Devices like ipod and other eletronic that uses htf+ cannot guarantee your files are safe. It gets worse when the files are large and lots of processing such as servers

bz2 can unzip quickly

If you are really scared that the file integrity is altered, then to make sure save the file in two places and make a sha1 hash.

This is how git make sure the file is the same by comparing the file against the generated hash.

I personally do not use it, so i guess maybe another forum member can take a look and tell you how

---

### Post by guilleme on 2012-04-12
Hi! I hope you don`t mind me jumping in :). 
Well, if you are concerned about being able to read you DVD backups in any platform (Mac OSX included), then you could split your compressed files into "volumes" of a small size, and then copy all the volumes into the DVD. 
You can do that using the compressing tool known as "7Zip" by installing the package on the software centre or the terminal, and then right-clicking the original file/directory to compress, selecting "compress...", selecting "7z" from the drop-down menu, and expanding the "more options" option at the bottom of the dialogue box. 7z archives lets you split them into volumes for storing convenience :). 
The only possible problem here, is that the computer you are going to uncompress them in must be able to read .7z files, and I`m not sure weather there is an implementation of 7zip for all the most common platforms.

---

