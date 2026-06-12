---
title: "Help in modifying the query"
date: 2011-07-25
forum: Programming Talk
---

### Post by vjohnny8 on 2011-07-25
Hi everyone,

In the below query, for the user_code column, if the same data is present in mst_user and unlock_user_checker tables, then only the data from the unlock_user_checker table must be displayed in the user code column. 

Kindly help !!!

select a.user_name as usrname,
a.user_code as usrcode,
b.no_of_login_attempt as usrattempt,
a.user_status as usrstatus,
c.unlocked_by as usrunlockedby,
c.unlocked_on as usrunlockedon,
c.approved_by as usrapprovedby,
c.approved_on as usrapprovedon,
c.rem as usrremarks,
c.approve_status as usrapprovestatus
from mst_user a, user_log_info b, unlock_user_checker c
where (b.No_of_login_Attempt >= 2 or a.user_status = '1')
and a.user_code = b.user_code
and a.user_code = c.user_code

---

