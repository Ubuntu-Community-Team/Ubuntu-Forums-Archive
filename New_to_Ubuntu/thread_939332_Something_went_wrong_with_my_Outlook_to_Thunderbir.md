---
title: "Something went wrong with my Outlook to Thunderbird transfer..."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by pariate on 2008-10-05
Hi everyone

I used the info from this article - [http://ubuntuforums.org/showthread.php?t=796094&nojs=1#goto_displaymodes]("http://ubuntuforums.org/showthread.php?t=796094&nojs=1#goto_displaymodes") to try and move all my emails etc. from Outlook to Tbird.  

Everything seemed to be fine, I opened Tbird after copying the necessary files but I can't see a single email!  My contacts are all there, so that's great, but what's gone wrong with my emails?!  

I'm not sure what other information I should give you here, so please let me know if you need anything else.  I'd really appreciate some help with this!

I've searched the forums but haven't been able to find any pointers.  I apologise if I've overlooked something.

I'm using Tbird 2.0.0.17 on Ubuntu 8.04.

Thanks,
pariate

ETA:  I tried sending myself a "test" message to see if it would show in my inbox.  I received an error message - **The messages could not be moved or copied to folder "Sent" because writing to the folder failed.  To gain disc space, from the File menu, first choose Empty Deleted, and then choose Compact Folders, and then try again**.  Tried following those instructions but it made no difference.

---

### Post by pariate on 2008-10-05
Found more info about ImportExportTools download for Tbird but it won't install, it tells me that it's not compatible with Firefox 3.  

Really at my wits' end, would love to hear from anyone who can offer any advice please.

---

### Post by Drezard on 2008-10-05
Is the account created in Thunderbird?

Daniel

---

### Post by pariate on 2008-10-05
> **Drezard said:**
> Is the account created in Thunderbird?

Daniel

Um... yes.  I had installed Thunderbird, set up my mail accounts etc before I even considered attempting transferring all my old data!  So I was copying files to the Thunderbird folder after the account had been created.

---

### Post by Drezard on 2008-10-05
Sounds something has gone wrong :S But, thats what I'm here for.

If you still have the outlook with all the mail on it, try exporting it in a different file format that is supported by Thunderbird. 

Thats my only other idea. Ive never attempted this, but I finish work in 30 minutes, then once I get home Ill give it an attempt and see what I get. So if your still stuck PM me and Ill give you some more help.

Daniel

---

### Post by pariate on 2008-10-05
You star.  I could hug you, really I could.  After seeing a few unresolved threads on this issue I was feeling pretty hopeless!  

I probably should have mentioned this earlier - in Windows I installed Tbird and imported all the settings from MS Outlook.  The emails displayed in TB no problem, so I copied the files as per the instructions in the article linked in my original post here.  I didn't have any problems until I tried to view the copied files in Ubuntu's Thunderbird.  I tried uninstalling and reinstalling TB but it didn't seem to be a clean install - it had retained all my mail account settings etc.  :confused:  

I'll try to stay on for another half an hour.  It's 2.30am here and I am drooping...  If I'm not around please do reply.  I need you!  :) 

Thanks a million.

---

### Post by pariate on 2008-10-05
Posting some more things I've tried just in case anyone else has any ideas.

I tried creating a new profile using the -ProfileManager switch in a terminal.  New profile works fine but still can't view the data I copied to that folder.

---

### Post by pariate on 2008-10-05
Oh my god!  I fixed it :-D  If anyone has the same problem, [http://fosswire.com/2008/03/04/migrate-your-thunderbird-emails-from-windows-to-linux/](http://fosswire.com/2008/03/04/migrate-your-thunderbird-emails-from-windows-to-linux/) is where I found the solution!

Yay!  I was getting far too stressed about this :-)

Thank you again Daniel for your reponse.

---

### Post by oldsoundguy on 2008-10-05
I sent the saved emails by forwarding back to my account.  Closing OE and then opening TB and retrieving. (but the originator becomes YOU and the date is the date YOU send it.  It STILL gets the stuff into TB at least!)

But I was dealing with TWO machines .. OE on a Windows box and TB on a Gutsy box.  (clearing out the Windows machine)

---

### Post by 73ckn797 on 2008-10-07
I am late in this thread but for future reference you can follow this:
[http://ubuntuforums.org/showthread.php?p=5764972#post5764972](http://ubuntuforums.org/showthread.php?p=5764972#post5764972)

---

