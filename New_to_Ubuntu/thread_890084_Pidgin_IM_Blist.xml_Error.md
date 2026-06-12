---
title: "Pidgin IM Blist.xml Error"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Socca on 2008-08-14
Everytime I open Pidgin Internet Messenger I receive the same continuous error. It's about loading the Buddy list ( Blist.xml )

Here is the error:
```
Error Reading blist.xml

An error was encountered reading your buddy list.  They have not been loaded, and the old file has been renamed to /home/sean/.purple/blist.xml~.
```

Is there anyway I can solve this error which popups every time I open up Pidgin IM?

---

### Post by drs305 on 2008-08-14
have you tried just deleting the list entirely? does the regenerated blist cause the error as well? of course, you will lose any info you have in the file. you can back it up although it looks like pidgin has done that already.

```

cp $HOME/.purple/blist.xml $HOME/.purple/blist.xml.bak
rm $HOME/.purple/blist.xml

```

an empty blist.xml should be generated the next time pidgin is started or when you try to add a buddy.

---

### Post by Socca on 2008-08-14
What I have tried is deleting Both the blist.xml and the new file that is loaded blist.xml~ . Logged in without a problem. Quit and Started again..get the error message again. I tried deleting the blist.xml and I opened it up and closed it without a problem. Tried it again and the error message came back

Any other suggestions?

---

### Post by drs305 on 2008-08-14
> **Socca said:**
> Any other suggestions?

You can start pidgin with the following and look through the generated file to see where the error might lie:
```
pidgin -d log
```

I can't provide a solution, but might be able to explain what is happening. Pidgin will start ok if there is no blist.xml, but the next time it starts it will reincorporate data from your accounts. If there is bad data, it will produce an error, which is what is happening to you - one good start followed by a bad one. 

You could try disabling various accounts (if you have more than one) and see if you can get it to start twice in a row. You may be able to figure out which account is producing the errors. The procedure would be:
Disable an account.
Delete blist.xml
Start pidgin, then close it.
Restart pidgin and see if the error is gone.

---

