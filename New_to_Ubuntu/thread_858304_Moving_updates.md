---
title: "Moving updates"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by cairnsww on 2008-07-13
I have an Ubuntu machine running Hardy which I have kept up to date as updates become available, However, I also have another one and a half machines running Hardy that I have not updated at all. (One of teh machines is a virtual machine under Windows). 

Can I transfer the updates (via CD or other medium) to my other two machines without having to go through the whole downlaod process?

(I am sure that this is an easily answered quesion and that it must be answered on the web already. I am just not sure how to ask the question!)

Thanks,
  Bill

---

### Post by ugm6hr on 2008-07-13
Easiest way - backup all the files (except "lock") from /var/cache/apt/archives on the up-to-date machine (on CD or USB etc).

Copy the files (as sudo) to the out-of-date machine in the same location.

Then apply the updates on the machine.  It will update the repo list, and then install them all without downloading again (as long as they are the latest available).

Another option is AptOnCD.

---

### Post by cairnsww on 2008-07-13
Thanks. I knew i would be quite simple!

---

