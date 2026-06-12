---
title: "Brasero ate my Mail folder"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2014-05-27
I'm an old codger that for the last 10 years has been extensively using e-mails in SeaMonkey mail folders as a substitute for progressive loss of memory between the ears :frown: 

Well,  effectively regularly backing up these e-mail folders has always been time-consuming,  and I've failed to keep up with the job properly in recent months.   I do have some old backups,  some of them burned on CDs,  some saved on a USB HD, and  some auto-saved by Ubuntu One (soon to be discontinued),  but all this isn't properly organised,  nor is it complete. 

So yesterday, I decided I'd try and catch up by burning a copy of my /home/.mozilla/seamonkey/xxxxx.default/Mail  folder on to a CD using Brasero.  There was about 600Mb of Mail folder content there,  representing about 30 months' of mail archives along with current and pending stuff.  

Having inserted my blank CD, I had a Brasero Data Disc Project window showing,  and a /home/.mozilla/seamonkey/xxxxx.default  window showing,  and I dragged my Mail folder in the latter to the former.     I assumed this would copy the whole of my Mail folder to Brasero ready for burning.    I didn't notice at the time but I discovered later that instead of copy-pasting it had cut-pasted my Mail folder leaving no Mail folder in /home/.mozilla/seamonkey/xxxxx.default. I don't understand how this happened.    Anyway,  I proceded to burn the CD.    Later when I discovered  there was no longer any Mail folder in /xxxxx.default I decided to try to copy it back there from the CD,  but unfortunately the CD burning hadn't gone well,  and my copy back attempt brought up numerous i/o errors.  Some sub-folders copied back OK,  but many didn't.  

So since I've now lost my Mail folder I'm in distress because I can't receive or send e-mail in Seamonkey any more.   I could probably slowly reconstitute some of my lost Seamonkey (it was supporting 6 different accounts)  from my various old archives but I can imagine it could take me months to fully recobble all this together.

Sorry about this long story.  My question now is  "Is it possible that there's a good copy of my lost Mail folder still temporarily lurking in the depths of my Ubuntu file system somewhere as a result of the cut-paste into Brasero that occurred yesterday?".   I've been careful not to shut my system down since then in the hope of possibly finding a clean copy somewhere there.

---

### Post by Elfy on 2014-05-30
Possibly check in /tmp

Double check that there are no backups in the seamonkey folder.

You might have managed to grab stuff with testdisk - but if the machine has been on and used since then, I doubt that - always worth a try. Never used it myself though. [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Sleepy-zz-John on 2014-06-10
My belated thanks for your reply,  Elfy.   Sorry, I didn't see the notification of your post earlier because of the chaotic state my e-mail has been in since this disaster.

No,  nothing in /tmp or my seamonkey folder.  I did try PhotoRec which comes with Testdisk,  and it recovered tens of thousands of files, some with good recognisable extensions like .jpg, .gif .gz  .java etc, and including many many with .txt extension,  but they had all lost their original file names and their original directory structure.  By chance I did find one SeaMonkey originated mail file there,  and perhaps if I'd spent a few **years** looking,  I'd have found some more,  but it was impossibe to seperate my lost Mail files in the ocean of other files that PhotoRec had given a .txt extn to.  It was the lack of the original folder structure of my lost Mail folder that eventually made me give up on trying to recover this way.

---

