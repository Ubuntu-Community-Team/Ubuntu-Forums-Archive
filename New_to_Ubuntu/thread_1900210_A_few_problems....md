---
title: "A few problems..."
date: 2011-12-25
forum: New to Ubuntu
---

### Post by onipar on 2011-12-25
I am setting up my parent's new computer.  Their old computer is a G5, their new computer is a PC running Linux Ubuntu. Everything seems fine thus far, but 
 two things that are giving me trouble: 


[LIST=1]
[*]The computer froze a couple times,  which is disconcerting since I built it this month.  I am running Ubuntu 11.10.  The computer froze the couple times when I was  trying to switch from one user desktop to another (I have two user  accounts on the system).  It doesn't do it every time, but even once or  twice is bothersome.
[*]I need to migrate all of my dad's saved e-mail folders from Thunderbird on the Mac to the Thunderbird on the PC.
[/LIST]
  
I searched a bunch online, but there are a lot of different methods and  all seem vaguely confusing.  Any help would be appreciated.  :D

---

### Post by drdos2006 on 2011-12-25
Check the hidden folders for hidden Thunderbird user files.

Maybe the MAC has hidden folders as well.

regards

---

### Post by onipar on 2011-12-25
I clicked to show hidden files on the PC, but there didn't seem to be anything new showing up.  Thank you for the suggestion.

Any other ideas are greatly appreciated.  I'm stuck.

---

### Post by onipar on 2011-12-26
I also tried the import feature with no luck.  Any advice?  thanks.

---

### Post by Learning Linux 2011 on 2011-12-26
The Macintosh does have hidden folders, just like Ubuntu.  You have to issue a special command in the Mac's terminal to view them.

I haven't used Thunderbird in awhile, but isn't there an export or save feature?

---

### Post by Learning Linux 2011 on 2011-12-26
I found this at: [http://www.mozillamessaging.com/en-US/thunderbird/3.0/releasenotes/](http://www.mozillamessaging.com/en-US/thunderbird/3.0/releasenotes/)

---

### Post by Learning Linux 2011 on 2011-12-26
Here is one more thing:

[http://support.mozillamessaging.com/en-US/kb/profiles?s=backup&as=s#w_moving-a-profile](http://support.mozillamessaging.com/en-US/kb/profiles?s=backup&as=s#w_moving-a-profile)

---

### Post by onipar on 2011-12-26
Well, thanks for the help.  i think that stuff is all a little over my head though.  I start getting confused once they ask to change lines of text for the path of profiles and this and that.  :confused:

---

### Post by Kslawdog on 2011-12-26
hey, 
    The command line is not as hard as you think, just takes a little know how.  this is what learning linux was trying to show you.  im not to sure how macs command line works but I know its similar to linux.

              Path to thunderbirds file in linux would be
            
                                cd ~/.thunderbird/
Then you can use the command _**ls**_ to see whats in the file

  If you have anymore questions just ask ill be keeping an eye on this.:)

---

### Post by onipar on 2011-12-26
> **Kslawdog said:**
> hey, 
    The command line is not as hard as you think, just takes a little know how.  this is what learning linux was trying to show you.  im not to sure how macs command line works but I know its similar to linux.

              Path to thunderbirds file in linux would be
            
                                cd ~/.thunderbird/
Then you can use the command _**ls**_ to see whats in the file

  If you have anymore questions just ask ill be keeping an eye on this.:)

Okay, thanks!  So I should type this into the terminal, correct?  

I'm very new to Linux, never used terminal commands and things like that (only once), so I'm feeling a little out of my depth.

I *did* try something with the terminal yesterday to get to the profile manager of Thunderbird.  It was supposed to be the way to set up the old profile by searching for the correct profile folder using the profile manager.  Everything worked okay, but when I was done, the old folders and e-mails still didn't show up in the program, so I guess I did something wrong.

I guess my question is once I do the above and I can see the files, what do I do next to get the old e-mails to import into Thunderbird?

Thanks for all your help, I really appreciate it.

---

### Post by onipar on 2011-12-26
Thanks for the help, I figured out how to do what i needed to do:

I downloaded an "import/export" addon to Thunderbird and then simply imported the old folders.  Much simpler than I was making it out to be  somehow.  :P

New problem occurred, however.  I had to import the old "inbox" as well, because he had files saved in it that he wanted.  But now Thunderbird won't let me delete it, and he has 2 inboxes.  Any idea how to delete the second inbox?

---

### Post by Kslawdog on 2011-12-26
I just set up my email account with thunderbird I already like it alot more than evolution.  But I was just thinking about your question. You shouldn't have to transfer anything because thunderbird uses your existing email account (hotmail for example) just set up the account on  your pc and you shouldn't have to import anything.:P

---

