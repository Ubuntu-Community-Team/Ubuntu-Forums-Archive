---
title: "Find old emails removed from Thunderbird inbox"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by kiwipenguin on 2013-02-07
Hi.
I would like to know if there is a way to find old emails that have disappeared out of my Thunderbird inbox?
I haven't deleted them but maybe they were moved out of my inbox automatically as a result of compacting?
Unfortunately they are no longer on my Yahoo email server either.
I'm using 11.10
Thanks!

---

### Post by Sealbhach on 2013-02-07
There's a good chance they may be gone.

You need to check your Thunderbird Account Settings. You have to tick a box to make sure that your messages on Yahoo are not deleted once you download them into Thunderbird.

Go to Edit/Account Settings and click on Server Settings. Make sure that "Leave Messages on Server" is ticked.

Check your local folder deletion policy. Look at Local Folders and the subsection Disk Space. Check if you have messages set to be deleted after a number of days. 

I lost a few messages by not knowing about this before. :???:

.

---

### Post by SeijiSensei on 2013-02-07
A much better choice if it is available is to use IMAP rather than POP3 with "leave mail on server".

---

### Post by CK000 on 2013-02-08
Thank you very much for this information, I too had the same problem.

---

### Post by kiwipenguin on 2013-02-09
Thanks for the info.

Unfortunately I had ticked the "leave messages on server for at most 14 days" box. So I guess they have gone from the server...

But that doesn't explain why they disappeared out of my inbox without me moving or deleting them.

Where do the compacted messages get stored?

---

### Post by Sealbhach on 2013-02-09
Compacting is an annoying misleading term for deletion. If they are compacted they are deleted. See [here]("http://kb.mozillazine.org/Compacting_folders#Undoing_compacting"). 

You need to check your Disk Space settings in your Account Settings in Thunderbird too. It's likely all the emails in your Thunderbird inbox are set to autodelete after a certain number of days. Unless you fix that you will keep losing emails.

I really think Thunderbird's default settings for this are ******. :mad:  Thunderbird should NOT be deleting emails from internet email accounts by default.
.

---

### Post by SeijiSensei on 2013-02-09
> **Sealbhach said:**
> I really think Thunderbird's default settings for this are ******. :mad:  Thunderbird should NOT be deleting emails from internet email accounts by default.

I have never had that experience using IMAP.

---

### Post by kiwipenguin on 2013-02-18
Thanks for all your help.
Now I'm a little bit wiser.
I've decided I didn't need all those old emails anyway :)

---

