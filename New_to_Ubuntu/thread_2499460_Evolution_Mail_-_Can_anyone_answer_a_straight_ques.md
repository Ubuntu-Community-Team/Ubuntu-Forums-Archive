---
title: "Evolution Mail - Can anyone answer a straight question?!"
date: 2024-07-28
forum: New to Ubuntu
---

### Post by 42pjcqyy on 2024-07-28
hi all, I am new to Linux, having spent 20 years or so on Mac. 
So far the only gripe I have and struggling to overcome is Mail clients!
I have 20 years of email in LOCAL folders (not on a server, on my machine), and I like it that way. can't afford to spend money to store 30-40GB of data I only need access to on my local machine (often offline too). 
Mac Mail had local folders, Outlook does, Thunderbird does. 
I have managed to get Thunderbird set up and all my nested local folders are organised properly. However I just can't stand Thunderbird any more. No point boring you with the reasons, search issues and other stuff is just making it hell. 
I heard about Evolution and it at least LOOKS like the closest thing to Mac Mail I have seen yet. I love it, BUT, I can't get a straight answer as to whether it can provide the same local folders functionality for me to store my mail. 
So I just thought I'd ask in here as users seem to be better at answering questions than developers for some projects. 
Can Evolution do local folders? If so, is there a relatively easy way to migrate from Thunderbird to Evolution Mail? (I am yet to find one after hours scouring the DuckDuckGo pages! 

Thanks

---

### Post by &amp;KyT$0P# on 2024-07-28
> **42pjcqyy said:**
> Can Evolution do local folders?

Yes, it calls it "On This Computer".

> If so, is there a relatively easy way to migrate from Thunderbird to Evolution Mail?

What specific things do you want to migrate?

---

### Post by 42pjcqyy on 2024-07-28
Thanks, sorry I should have clarified. I don't use any of the other stuff thrown into Thunderbird (a web browser, wth?!). I have a few contracts but they can be moved manually. All I am referring to is email, nothing else. If I could manage to get Evolution running and showing me the same emails/folders as Thunderbird, i think it will be a breath of fresh air. 

"[COLOR=#000000]Yes, it calls it "On This Computer"." - Great, but I heard that from someone before then found it wasn't quite as simple as I assumed (i.e. right click, create folder, drag emails into it, right click create sub folder, etc). Do you know if it's really that usable, similar to Thunderbird/MacMail/Outlook in terms of organising/creating/deleting local folders?

Thanks again[/COLOR]

---

### Post by &amp;KyT$0P# on 2024-07-28
> **42pjcqyy said:**
> All I am referring to is email, nothing else. 

Emails are straightforward to import, but if you have a lot of local folders, it might be time-consuming.

First, in Thunderbird, for each folder/subfolder you want to import into Evolution, right-click the folder and select compact folder.

Then, in Evolution, File > Import..., Next, select "Import a single file", then you can pick the email folder file from your [Thunderbird profile]("https://kb.mozillazine.org/Profile_folder_-_Thunderbird") (file type should be "Berkeley Mailbox (mbox)") and select which local Evolution folder you want to import the emails into.

> right click, create folder, drag emails into it, right click create sub folder, etc). Do you know if it's really that usable, 

It has been exactly like that for me after I got it set up.

---

### Post by 42pjcqyy on 2024-07-28
Thank you SO much. I have asked and asked and even the main support people for Evolution couldn't put it that simply, or even confirm it's doable like that. Instead I just get 'why on earth would you want emails on your computer instead of on the server?'. I got sick of explaining my perfectly valid reasons! (I wouldn't have expected any different in an Apple forum! But Linux?!)

I am not sure about the folder structure (i.e. in Files app rather than in Thunderbird GUI), I will have to find where that is and see if I can work out which folders correspond to my visible 'Local Folders' in TB, but I should suss that with a bit of time. 
I am assuming (hoping!) my TB data is in mbox format! 

So just to clarify, I think you're saying I need to set Evolution up just with the email account details/imap first, then manually create a load of local folders to match the structure I have in TB, THEN import the emails into those folders one at a time? If so, that's fine, thanks again!

---

### Post by &amp;KyT$0P# on 2024-07-28
> **42pjcqyy said:**
> So just to clarify, I think you're saying I need to set Evolution up just with the email account details/imap first, then manually create a load of local folders to match the structure I have in TB, THEN import the emails into those folders one at a time? If so, that's fine, thanks again!

Yes exactly.  Just make sure that before importing, you compact each folder in Thunderbird, then completely quit Thunderbird before importing.

---

### Post by 42pjcqyy on 2024-07-28
Right, notes made! Thanks very much, will see how I get on tomorrow.

---

