---
title: "Individual Hard drives per user account?"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by KG4UJD on 2013-05-31
If I build a machine with a ssd for the os to be installed and 2 1t harddrives is their a way to set it up where when user A logs in their home dir will be on hd A and when user B logs in their home dir will be on hd B?

---

### Post by Cheesemill on 2013-06-01
Yes.

You can either mount the 2 HD's under the respective home folders (mount HD1 at /home/user1 and HD2 at /home/user2) or you can change the location of a users home directory to wherever the drives are mounted using the usermod command.

---

