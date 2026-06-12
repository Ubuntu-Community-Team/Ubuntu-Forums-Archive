---
title: "how can i make my music collection appear in two user's rhythmbox?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by w.g.hanna on 2008-10-06
i have a 90 gig music collection.  i don't want to chew up 180 gigs of hard drive space to make it available on my fiance's user account through rhythmbox.  i want it so that she can open rhythm box and just use it.  but, of course, i need all those tunes in my account's rhythmbox?  

anyway to do that?

---

### Post by vanadium on 2008-10-06
Is something prohibiting you from pointing the Rhythmbox instance in each  account to the same music directory? Besides, there is a lot you can do with symbolic links in Linux: both could have the same music files in a Music directory in their home.

---

### Post by Joeb454 on 2008-10-06
You could put the music in a shared folder on the system (or your home directory) then point rythmbox on your fiance's account to that directory :)

---

### Post by dioltas on 2008-10-06
You could give others permissions to read from your music folder
**chmod a+r -R /home/you/Music**
Replacing /home/you/Music with the folder where your music is.
Then in rythmbox, in his account go to Edit -> Preferences -> Music tab and set his default library as your music folder. That should work.


Or if you don't want him to have access to your Music folder inside your home you could just make a new directory like /Music
**sudo mkdir /Music**
Then just move all your music from your default music folder into this folder.
Set this folder as the default library in rhythmbox in both of your accounts.

_OR_

In his music folder create a symbolic link to your Music folder

**ln -s /home/you/Music /home/his_user_name/Music/your_names_music**

replacing the folder names for wherever your music is stored and the second one for where his music folder is.
Then rhythmbox will "see" all of your music inside his folder, but it will really be just a link / shortcut. That's what I did for my brother's account, but I think you'd be better off with the first option.

---

### Post by jamesjohnson65 on 2008-10-30
The simplest way i could find here is you could put the music in a folder on the system (or your home directory) share the same folder then point rythmbox on your fiance's account to that directory the files will be made available :guitar:

---

