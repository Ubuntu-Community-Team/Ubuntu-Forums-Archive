---
title: "Inoperable &quot;action buttons&quot; &amp; anti virus advice wanted"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by faron45 on 2008-08-18
I asked this question a couple of days or so ago & got [some] answers.At this point,I was just wondering if anybody else had any more ideas as to why when I add the "action button"-"lock screen" to my panel,it is inoperable ? I am trying to make my pc more secure & this is just one of the ways I would like to do so.

 Also,I'd like some feedback on anti virus programs for Xubuntu .Currently,I am running nothing ! I'm not so sure that that was even a good thing to mention but,the person who's installed this on my pc has pretty much asssured me of Xubuntu's security.

 One last issue for today-I've made a folder in my bookmarks so I can put related pages together.But,when I tried to begin the drag & drop of all the related pages into that folder the pc just completely froze up on me & I had to do a hard reboot.Has anyone else had this issue ? Is drag & drop not possible with xubuntu ?

               Thanks again everybody for any & all help
                      Yer pal,faron45
                            rock on :guitar:

---

### Post by halitech on 2008-08-18
I'm not sure on the lock PC button so I'll leave that for someone who might know :)

far as antivirus, not really needed as there are very few viruses that attack linux in general. If you share files with windows users or email attachments to them, you can install clamav (in the repos) to scan those files to protech windows users.

If your bookmarks are in firefox, why just use the Organize bookmarks option in forefox? (if not, I'm not sure why it would lock up)

---

### Post by billgoldberg on 2008-08-18
> **halitech said:**
> I'm not sure on the lock PC button so I'll leave that for someone who might know :)

far as antivirus, not really needed as there are very few viruses that attack linux in general. If you share files with windows users or email attachments to them, you can install clamav (in the repos) to scan those files to protech windows users.

If your bookmarks are in firefox, why just use the Organize bookmarks option in forefox? (if not, I'm not sure why it would lock up)

There are NO viruses for linux on the internet.

The virus scanner for linux only search for win viruses.

If there ever were a virus for Ubuntu, it will be fixed by the update manager.

-

Instead of rebooting the system, use "ctrl + alt +backspace".

---

### Post by halitech on 2008-08-18
not to dispute what you are saying bill but

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

and it wouldn't be fixed by the update manager, it would be resolved by the programmers catching the security flaw and writing the code to patch it and then being submitted for approval and then it would be loaded into the queue for sending out to users.

---

### Post by fadumpt on 2008-08-31
if you are on any networK where WindoWS Pc's Co-exist or if youhave ContactS in your e-mail that use windows..then antiviruS is Kinda needed.

---

### Post by mali2297 on 2008-08-31
Regarding the problem with locking the screen, what happens if you type *xflock4* in a terminal? Any error message?

---

### Post by lisati on 2008-08-31
I don't know about the "lock" button. 
However, for antivurus with Linux: it's one of those "not very likely but not impossible either" things, having antivirus software on your Ubuntu machine is usually more of a courtesy to Windows users with whom you might connect, combined with using good sense when trying stuff.

---

### Post by billgoldberg on 2008-08-31
> **halitech said:**
> not to dispute what you are saying bill but

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

and it wouldn't be fixed by the update manager, it would be resolved by the programmers catching the security flaw and writing the code to patch it and then being submitted for approval and then it would be loaded into the queue for sending out to users.

As far as I am aware, those viruses and other malware have been patched out of existence or are created in labs and aren't on the internet.

A better way to put my previous statement

"there aren't currently any known viruses in the wild that can affect an up to date linux OS"

Sure you can run malicious apps/scripts once you gain control of an machine, but that's another thing all together.
--

The update manager will apply those patches, so I'm not sure why you wrote that second comment.

Do you think I believe the update manager magically writes patches itself?

---

### Post by Yannick Le Saint kyncani on 2008-08-31
> **billgoldberg said:**
> A better way to put my previous statement

"there aren't currently any known viruses in the wild that can affect an up to date linux OS"

+1

Just make sure :

- You have security repositories enabled in your software sources.
- Update once a day.
- Do not add external repositories, use only the official ones. Do not install anything that's not available from the repositories either.
- Avoid proprietary applications, like flash macromedia for example.

---

### Post by halitech on 2008-08-31
> **billgoldberg said:**
> As far as I am aware, those viruses and other malware have been patched out of existence or are created in labs and aren't on the internet.

A better way to put my previous statement

"there aren't currently any viruses in the wild that can affect an up to date linux OS"

Sure you can run malicious apps/scripts once you gain control of an machine, but that's another thing all together.
--

the reason I called it into question was because of the way you worded it
> There are NO viruses for linux on the internet. with the emphasis on no which is technically incorrect and could lead some people into believing Linux is completely safe.


> The update manager will apply those patches, so I'm not sure why you wrote that second comment.

Do you think I believe the update manager magically writes patches itself?

I'm not sure what you thought about patches being applied but if we were looking at a system that doesn't have an update manager, how would the patches be applied in those cases?

---

### Post by Yannick Le Saint kyncani on 2008-08-31
Oh, almost forgotten (how could I),

!!! AND MAKE BACKUP !!!

You're by far the first threat to the safety of your data.

---

