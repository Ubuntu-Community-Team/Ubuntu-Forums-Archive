---
title: "Can't enter my password in the terminal!"
date: 2013-12-15
forum: New to Ubuntu
---

### Post by Soonageek on 2013-12-15
When I press 'enter' after writing in my password, I get 'command not found'.  It's the same password I always use when the xubuntu starts up, so I don't understand...  (I am new to the forum and quite bewildered about figuring out how to use it to get help, to be honest.)

---

### Post by bapoumba on 2013-12-15
> **Soonageek said:**
> When I press 'enter' after writing in my password, I get 'command not found'.  It's the same password I always use when the xubuntu starts up, so I don't understand...  (I am new to the forum and quite bewildered about figuring out how to use it to get help, to be honest.)

What command are you issuing ?
Make sure you do not have capslock on.

---

### Post by deadflowr on 2013-12-15
Yes, post the command you are trying to run.
You can sudo anything, but not everything is a command.
If you try something like 
```
sudo i like eating donuts
```
it'll ask for a password, and then tell you "command not found".

I doubt you tried a command like this, more likely you ran a command with a bad line in it.
post and we can see what to do.

---

### Post by Soonageek on 2013-12-15
Thank you for your answers.  I didn't enter a command! I didn't get that far.  I just wrote in my password and got that message when I pressed Enter. Are you saying you have to write the command in first, before you put in your password?  You can see how green I am!:redface: (Although I have been using a computer for years and years!)

---

### Post by deadflowr on 2013-12-15
> **Soonageek said:**
> Thank you for your answers.  I didn't enter a command! I didn't get that far.  I just wrote in my password and got that message when I pressed Enter. Are you saying you have to write the command in first, before you put in your password?  You can see how green I am!:redface:

Yes, enter the command, then enter your password when it asks you for it.
In fact, only enter your password when it asks for it.
The password field will be blank when entering it.
Type it as best you remember it.

---

### Post by bapoumba on 2013-12-15
Eheh, yes, enter the **sudo <whatever command>** and you'll be prompted to enter you password. As deadflowr pointed out, there is no visual feedback of the password itself in a terminal window. Then hit the <enter> key.

---

### Post by jackdalton00 on 2013-12-15
Screenshot please.

---

### Post by philinux on 2013-12-15
Anyone who wants visual feedback on terminal see this [http://superuser.com/questions/420815/feedback-when-typing-password-at-a-sudo-prompt](http://superuser.com/questions/420815/feedback-when-typing-password-at-a-sudo-prompt)

---

### Post by deadflowr on 2013-12-15
> **jackdalton00 said:**
> Screenshot please.

Screenshot of what?

I would highly advise AGAINST posting any screenshot where the users password has been mistakenly entered.
And is visible.

---

### Post by Soonageek on 2013-12-15
> **deadflowr said:**
> Yes, enter the command, then enter your password when it asks you for it. Well, that might have accounted for it and I thought my problem was solved...  But now that I do it the right way round it still doesn't work.  I can't enter the password - I type it, but it doesn't appear!:confused::frown:

---

### Post by philinux on 2013-12-15
> **Soonageek said:**
> Well, that might have accounted for it and I thought my problem was solved...  But now that I do it the right way round it still doesn't work.  I can't enter the password - I type it, but it doesn't appear!:confused::frown:

It doesn't appear by default.  Just Type it in amd press enter. Or see post 8

---

### Post by Iowan on 2013-12-15
> **Soonageek said:**
>  I can't enter the password - I type it, but it doesn't appear!:confused::frown:

> **deadflowr said:**
> 
The password field will be blank when entering it.This has been mentioned (at least) twice.

---

### Post by deadflowr on 2013-12-15
> **Soonageek said:**
> Well, that might have accounted for it and I thought my problem was solved...  But now that I do it the right way round it still doesn't work.  I can't enter the password - I type it, but it doesn't appear!:confused::frown:

As stated before, the password field will be blank/invisible(as you type the password), by default, if you want it to appear follow the link philinux posted.

double ninja'd by Iowan and philinux!

---

### Post by Soonageek on 2013-12-15
> **deadflowr said:**
> As stated before, the password field will be blank[COLOR=#800080]/invisible[/COLOR] I AM sorry!:redface: I have understood at last what you guys were saying!  (Well, it is disconcerting to type and not see anything happen!).  Thank you, and chances are I will be back soon...

---

### Post by bapoumba on 2013-12-15
> **Soonageek said:**
> I AM sorry!:redface: I have understood at last what you guys were saying!  (Well, it is disconcerting to type and not see anything happen!).  Thank you, and chances are I will be back soon...
philinux has given a link where you can have the terminal output stars for each letter you type : [http://ubuntuforums.org/showthread.php?t=2193904&p=12874760#post12874760](http://ubuntuforums.org/showthread.php?t=2193904&p=12874760#post12874760)
Entering the password has no visual feedback for security reasons.

---

