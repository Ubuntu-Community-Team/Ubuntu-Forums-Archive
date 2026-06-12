---
title: "Reboot and select proper boot device .."
date: 2024-03-13
forum: New to Ubuntu
---

### Post by mobinx on 2024-03-13
I recently added a second user but then deleted it. However, the deleted user keeps showing up in the system logs. and my laptop now refuses to reboot properly. When I try to restart, I see an error message: "Reboot and select proper boot device .."
I was previously able to fix this issue by using a maintenance tool to correct the partitions. 
Any suggestions on how to fix the "Reboot and select proper boot device .." error so my laptop boots normally?

laptop Asus 


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293489&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2024-03-13
Once the user has been removed using userdel, you need to delete the user's home directory yourself.
```

sudo rm -r /home/user-name
```

replacing "user-name"" with the username you want to remove.

BTW I'm not sure what was done to your normal boot though, can you think of anything else you did before this happened?

---

### Post by Rubi1200 on 2024-03-14
I am not sure one thing is connected to the other.

Have you checked all your cables?

Please run the boot info script in my signature. Choose to create a summary report and then post the pastebin link that is created back here for us to analyze.

It would be helpful if you can also do the same with the system info script (also in signature).

Thanks.

---

### Post by yancek on 2024-03-14
I would agree that these events do not seem related.  Crating and deleting a user should have no effect on the boot process.  What does 'correct partitions' mean as creating and/or deleting a user should not have any effect on partitions.  Did you create separate partitions also for the new user?

---

### Post by #&amp;thj^% on 2024-03-14
To be accurate, Never did I mention the two was related.

my suggestion was to help eliminate the old user from appearing in the OP's logs
> However, the deleted user keeps showing up in the system logs

Then I said no clues on why the OP's boot was non functional.
JFTR :)

---

