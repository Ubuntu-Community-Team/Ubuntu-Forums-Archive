---
title: "ACL's"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by davidmcmhn on 2015-05-05
Hi All,

I am messing around with Access Control Lists to get the hang of them. I have created a test set up where I have a group called "Marketing" and a user called "John", I've set up an ACL on a local file located in a users /Documents/ directory which says that any member of the marketing group has execute permission on that file.

So when I added John into that group - I could see he had execute permission on the file which I wanted him to. Then `getfacl` showed that the marketing group has execute permissions on this file as expected.

My problem/question is that when I removed John from the marketing group - he still had execute access to that file. Do I need to do something extra on the ACL side of things? I thought removing him from the group would have been enough as the ACL was set on the group rather than the user.

Any help would be greatly appreciated :)

Dave

---

### Post by Habitual on 2015-05-05
> **davidmcmhn said:**
> Do I need to do something extra on the ACL side of things? I thought removing him from the group would have been enough as the ACL was set on the group rather than the user.
John would have to logout and back in after editing the ACL, I suspect.

---

### Post by davidmcmhn on 2015-05-05
Sounds good to me. Thanks for the reply :)

---

### Post by Habitual on 2015-05-05
You are very welcome.

---

