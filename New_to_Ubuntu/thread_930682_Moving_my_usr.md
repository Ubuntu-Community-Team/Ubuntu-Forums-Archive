---
title: "Moving my /usr"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by rvabdn on 2008-09-26
Hi and firstly apologies I'm sure this has been answere before but I'm having trouble finding a clear tutorial.

I would like to move my /usr folder from my / partition onto a new partition.  

I have copied the contents of /usr onto a new ext3 partition but I'm not sure how to replace/mount it.

I know that I needto rename the existing /usr folder, create a new /usr folder and mount the new partition to that folder.  I also need to alter /etc/fstab  

is that all?  what order should I do these things in?  I've tried a couple of times but I'm not having much success.

Thanks

---

### Post by Nepherte on 2008-09-26
I'd say you copy the /usr to the new partition first, then edit /etc/fstab to reflect the new changes. Then restart and see if that works. If it does, you can delete the old /usr. If it doesn't, change /etc/fstab again. I'm not 100% sure if that's all you have to do, but I can't think of anything else right now.

---

### Post by digitalvectorz on 2008-09-26
[http://outhereinthefield.wordpress.com/2008/02/02/moving-usr-var-to-another-partition/](http://outhereinthefield.wordpress.com/2008/02/02/moving-usr-var-to-another-partition/)

is this what you're looking for?

---

