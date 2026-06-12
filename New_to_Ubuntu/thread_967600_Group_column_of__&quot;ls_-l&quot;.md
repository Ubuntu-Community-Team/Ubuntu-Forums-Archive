---
title: "Group column of  &quot;ls -l&quot;"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by sohaikia1 on 2008-11-02
Hi guys,

I have a question on the group column of the output of ls -l. Which group does that column refers to? Since a user might belong to more than 1 group.

---

### Post by Daveth on 2008-11-02
is the argument not the other way around? What you are looking at is the group relevent to the file, are you not, so that my "tux" folder is owned by me, and in my group. The fact that i might belong to another group is surely not relevent, is it? 
We both might learn something here!

---

### Post by scorp123 on 2008-11-02
> **sohaikia1 said:**
>  I have a question on the group column of the output of ls -l. Which group does that column refers to? Look at that output again. The group it is referring to is clearly listed in the 4th column. That a user might be a member of multiple groups is irrelevant, the columns that "ls -l" shows are the usernames and groups under which the file was created. If you wish to change the group ownership you'd have to use the "chgrp" command against that file in question.

---

### Post by sohaikia1 on 2008-11-02
So it depends on which folder that file is located in right? Ok thanks for clearing that up!

---

### Post by Sand Lee on 2008-11-02
> **sohaikia1 said:**
> So it depends on which folder that file is located in right? Ok thanks for clearing that up!

Actually I think it depends on who created that file and what main group that person was under.

---

