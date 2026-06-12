---
title: "super user log out!"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2012-01-30
okay, i accidentally hit su -i in ubuntu and gave my password! i typed 'exi't before completing the task for which i hit su -i, and terminal was exiteed.  now it appears like- <username>@<username>:~$         which is against earlier display. don't know i am root logged in or else! whoami returns my username (bijay, that i've used) but the problem is that i gave the same username(same 'bijay' that i had used during installation of ubuntu 10.04lts) after hitting su -i in terminal. now it's giving me problem in mounting installation cd's of oneric. help to get out of this, please. i apologize for not being aware of not logging in as root as awared in many ubuntu sites.

---

### Post by lechien73 on 2012-01-30
Hello & welcome to the forums,

What you are describing sounds to be the correct behaviour.

When you type *sudo -i* the prompt should change to something like:

```
root@computer_name:~#
```

Typing *whoami* here will answer *root*

When you type *exit* to quit this shell, the prompt should change back to:

```
your_username@computer_name:~$
```

Typing *whoami* here will answer *your_username*

It seems, then, that the problem mounting the CD is unrelated. What problem are you having with this, exactly?

---

### Post by tojonukokhadush on 2012-01-30
thankyou for such a fast reply! though i've been using ubuntu since 9.04 version but this is my first registered visit in forum. i'm lovin' it!

okay, the problem was that- i typed 'exit' after hitting 'su -i' [i don't remember what i was actually tryin' to do, as i keep indulging in terminal ;-) as i love learning about linux].
the terminal was terminated then and when i again open the terminal, it shows-
username@username:~$
instead of earlier-
username:~$(i guess)
this was troubling me since after this when i browsed defferent sites regarding super user login, everywhere there were strictly recommended- 'not to root login unless you actually need it coz it might bring your whole system down in case of any nominal mistakes'

i could not find what has happened good or bad! 
and now i notice that my username and computer name are same. even i gave same password when it prompted!
when i type ' sudo passwd -dl root' now, it prints 'password expiry information changed'. what the heck!
so was worried!
thankyou for your help. can i stay cool now, if it's all okay?

---

### Post by lechien73 on 2012-01-30
Everything seems to be normal :)

If you type:

```
cat /etc/hostname
```

That will confirm your computer name for you.

What problem did you have mounting CDs?

---

### Post by grahammechanical on 2012-01-30
May I suggest that you read this information?

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

It may ease your mind because Ubuntu is protecting you from yourself! This does not happen with other distributions. We do need to take note of the warning about logging in as Root. Notice what is said under the Heading

> **root account**

> Enabling the root account

> Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent Root login, the best alternative is to _simulate_ a Root login shell using the following command...

Oh, one more thing. No one types a command in a terminal and then types in their password by accident. We may do it without thinking about what we are doing. And that is never a good thing to do.

Regards.

---

### Post by tojonukokhadush on 2012-01-30
thankyou lichien for your help.
and while installing from live cd, it says could not mount the installation cd and displays a long error message in boot screen which i was not able to read as it did not allowed me to finish before it went for rebooting. but now i have decided to wait till april 26th and upgrade to 12.04 lts. isn't that a great idea? ;-) i am hopefull for your help in further ubuntu problems.

and grahammechanical, 
thankyou too for your help.
and referring to your suggestion on the last line, yeah i agree that's not a good thing to do and that's why i have apologized in first hand for my carelessness! it happened so because learning linux is completely upto one's own effort in country like ours where, one can learn c programming only in few of the colleges offering computer or IT education! you would love to google about nepal i guess!
anyway thankyou very much for your help.

---

### Post by anewguy on 2012-01-30
Not that it may go there, though there was a hint earlier, but refrain from showing/discussing enabling of the root account - that's not allowed in this forum.  If you need to reference that you have done so, just say "I enabled the root account" and leave it at that.

Like I said, not that it's going that way, but just in case!  ;)

Dave ;)

---

### Post by tojonukokhadush on 2012-01-30
okay and thankyou.
'i enabled root account' only ;-)

---

### Post by tojonukokhadush on 2012-01-30
okay, this was what i was trying to do.

i was tryin' to fix gpg error and got all this. i followed what was instructed in this-(screenshot-1.png)

and again when i hit  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
following message shows up-(screenshot-2.png)

the gpg error remains unsolved :-(

---

### Post by lechien73 on 2012-01-30
The command shown in screenshot-2.png is wrong. There were no spaces between the options, and you had put --keyserver.ubuntu.com together, rather than --keyserver keyserver.ubuntu.com

Try copying the command to the clipboard:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

and paste it into the terminal by pressing Ctrl+Shift+V

---

### Post by tojonukokhadush on 2012-01-30
thankyou very much Mr. Ireland ;-) it worked! gpg problem is solved. HOORRAY! 
now i must be marking this thread as solved, right?

---

### Post by lechien73 on 2012-01-31
You're welcome...I'm glad it's working for you now & I think that's the only time I'll ever be called Mr Ireland! :D

You can mark the thread as [SOLVED] using the **Thread Tools** menu near the top of the page.

---

