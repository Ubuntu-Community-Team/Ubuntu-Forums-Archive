---
title: "Help with Notification Popup:   &quot;Mail Dispatcher Agent&quot;"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by GregA on 2011-10-17
Just updated from Kubuntu 11.4 to 11.10.   After login, a notification popup keeps appearing advising:

"mail dispatcher agent cound not access the outbox folder" - - any ideas how I can fix that?  

I had Kmail as the default mail client, . . .  tried switching to Claws mail - - but still get the same popup message.

---

### Post by timshel86 on 2011-10-17
I tried the solution from [here]("http://forum.ubuntu-fr.org/viewtopic.php?id=669521"), and it worked for me.

Just delete the configuration by typing:
```
rm ~/.config/akonadi/*

```

---

### Post by GregA on 2011-10-17
Tim,

Thanks much for your help, . . . .  . that totally fixed the issue!

---

### Post by craq on 2012-12-01
that seemed a little drastic. The forum linked below has two more conservative suggestions. I can confirm that the first one worked for me.
1. Delete the email resource labelled "Local Folder" in the Akonadi Configuration. The Akonadi Configuration was under Personal Information in the System Settings window.
2. Rather than removing the akonadi configuration, I edited ~/.config/akonadi/aknoadiserverrc and changed "StartServer=true" to "StartServer=false", and then rebooted (although logging out and back in should have been sufficient). 

[http://forum.kde.org/viewtopic.php?f=20&t=97385](http://forum.kde.org/viewtopic.php?f=20&t=97385)

---

### Post by wildmanne39 on 2012-12-01
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

