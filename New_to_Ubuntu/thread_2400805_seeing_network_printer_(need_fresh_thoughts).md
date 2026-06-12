---
title: "seeing network printer (need fresh thoughts)"
date: 2018-09-10
forum: New to Ubuntu
---

### Post by nigel1952 on 2018-09-10
Yes I know this is an "old chestnut" but since installing Ubuntu (now  18.04) I have spent 4-5 weeks trying to print on our windows 10 home network, I have looked at 100s of so called fixes and tutorials (linux babe techmint etc). on the web yet sill cannot print. The in-passe  appears to be with Samba, it obviously seeing the home workgroup as the PC to which the printer is attached is shown in the Samba browser but when selected the dreaded login window appears Ubuntu logins/user does not work neither does the windows credentials work. Does anyone have any fresh thoughts what I could be doing wrong before I abandon Ubuntu as a leap too far. Thanks

---

### Post by Autodave on 2018-09-11
Since no one else has jumped in....

What kind of printer do you have?  Wired, wireless, or ethernet connection?

---

### Post by him610 on 2018-09-12
We are sort of working in the dark here. Could you provide the printer specifications? Some information on your network configuration might be helpful also.

---

### Post by nigel1952 on 2018-09-16
> **him610 said:**
> We are sort of working in the dark here. Could you provide the printer specifications? Some information on your network configuration might be helpful also.

sorry for the lack of detail, the printer (HP6940 deskjet) is wired to one of 2 win 10 machines, these were previously members of a win homegroup prior to the last major win 10 update. Now it is an ad-hoc workgroup. This is seen by the Ubuntu machine via samba when searching for a network printer but I am asked to login but neither Ubuntu or win  credentials are accepted. Following one of the "web solutions" I ended up creating 2nd user account supposedly for printing this also hits the same in-passe. Ubuntu is 18.04 Samba 4.9, I have modified samba following [https://www.linuxbabe.com/ubuntu/install-samba-server-ubuntu-16-04](https://www.linuxbabe.com/ubuntu/install-samba-server-ubuntu-16-04)

---

