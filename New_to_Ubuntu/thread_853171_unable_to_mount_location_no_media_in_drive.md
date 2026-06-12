---
title: "unable to mount location no media in drive"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by eXwin on 2008-07-08
can someone help me! after trying to copy a vista burned dvd disc (picture files from an engagement party) my cd dvd drive is not working unable to mount location no media in drive? 
here is my etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                             0  0  
# /dev/sda1
UUID=f9f3d89d-ce35-4ba8-8ecf-ac220cc26a0e  /               ext3         relatime,errors=remount-ro                           0  1  
# /dev/sda5
UUID=19746ccf-1058-44ba-a7c8-6e24a9875deb  none            swap         sw                                                   0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                                0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                             0  0  
/dev/scd1 /media/cdrom0 auto user,noauto 0 0
/dev/sda5                                  /media/sda5     swap         users,sw,user,owner                                  0  0    

been looking thru various posts for three days but no luck
cant even boot from cd 
any help much appreciatedhttp://ubuntuforums.org/images/smilies/icon_smile.gif

---

### Post by billgoldberg on 2008-07-08
> **eXwin said:**
> can someone help me! after trying to copy a vista burned dvd disc (picture files from an engagement party) my cd dvd drive is not working unable to mount location no media in drive? 
here is my etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                             0  0  
# /dev/sda1
UUID=f9f3d89d-ce35-4ba8-8ecf-ac220cc26a0e  /               ext3         relatime,errors=remount-ro                           0  1  
# /dev/sda5
UUID=19746ccf-1058-44ba-a7c8-6e24a9875deb  none            swap         sw                                                   0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                                0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                             0  0  
/dev/scd1 /media/cdrom0 auto user,noauto 0 0
/dev/sda5                                  /media/sda5     swap         users,sw,user,owner                                  0  0    

been looking thru various posts for three days but no luck
cant even boot from cd 
any help much appreciatedhttp://ubuntuforums.org/images/smilies/icon_smile.gif

If your pc is unable to boot from cd, the problem is most likely your drive itself.

---

### Post by eXwin on 2008-07-08
drive was working before i loaded dvd

---

### Post by konungursvia on 2008-07-08
If other discs work, it looks like you haven't enabled DVD playback (an issue on fresh installs of some older releases). Try doing a google search for the document "13 Things to do after a fresh ubuntu install" and go to the part about enabling codecs, good, bad, ugly, and make sure you have installed all linux things needed for DVD playback.

---

### Post by eXwin on 2008-07-08
been using ubuntu for 3 months have installed all good bad and ugly codecs burner was working fine until recently but i did upgrade from 7.04 to 8.10 1 week ago first time i tried to use burner since install and had this problem spent days searching for answer and im stuck

---

