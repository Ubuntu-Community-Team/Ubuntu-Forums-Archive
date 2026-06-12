---
title: "Empathy .. looks good .. one question though"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by ubrox on 2008-10-19
Did anyone figure out how to disable chat history?

---

### Post by ariel on 2009-04-28
> **kalyanakrishna said:**
> Did anyone figure out how to disable chat history?

I'm wondering the same - I can't find any setting to disable this

---

### Post by alre on 2009-04-28
If i am right there is no possibility to disable the chat history at the moment. Empathy logs conversations by default.

---

### Post by tone77 on 2009-11-06
bump, has anyone figured out how to delete chat history yet?

---

### Post by rarsa on 2009-11-10
This is one of those things that I have no clue how the developers thought was a good idea.

In this day and age where privacy is important forcing to log all the conversations?

Well, here is how to delete them. You may create a script to click on when you want to delete them or you may turn it into a cron process to delete de logs at regular intervals.

The logs are under 
```
~/.local/share/Empathy/logs
```

To remove the logs just execute:
```
rm -fr ~/.local/share/Empathy/logs
```

I tried making that folder read-only but Empathy chokes and closes down.

Setting that option should not be difficult. Hopefuly someone is working on that.

Edit:
I just noticed that in another system where I have Empathy 2.26.1, the logs are saved to a different location.
```
rm -fr ~/.gnome2/Empathy/logs
```

---

### Post by mr_steve on 2009-11-10
Looks like the Empathy developers are working on this, and there is a patch which at least adds a somewhat-hidden configuration option to disable logging. If I can get the patch to work for the current version of Empathy in Ubuntu, I'll roll up some patched packages and put them in my PPA.

Watch this space for updates...

---

### Post by mr_steve on 2009-11-11
For those that are interested in this, I just created a patch for Empathy which allows you to disable logging.

I've created some patched packages for Karmic, which you can get from [my PPA]("https://launchpad.net/%7Esmcgrath23/+archive/smcgrath"). There are instructions there for installing packages from a PPA.

Once you've installed the new package, you will have to edit a GConf key to disable logging. If you don't have "Configuration Editor" on your Applications->System Tools menu, just hit Alt-F2 for the Run dialog and enter "gconf-editor"

You'll want to browse through the tree on the right until you find /apps/empathy/conversation, and then clear the checkbox for enable_logging on the right.

I'm still testing this package myself, but it works great for me. It's identical to the existing version, except for the ability to disable logging.

I'll keep this package up-to-date until the Empathy developers get this option added to the official packages.

Please let me know what you think.

---

### Post by mr_steve on 2009-11-13
I've updated my PPA package of Empathy, the current version is now 2.28.1.1-0ubuntu2~ppa3. Get it from [https://launchpad.net/~smcgrath23/+archive/smcgrath]("https://launchpad.net/%7Esmcgrath23/+archive/smcgrath").

This version has a new patch. In addition to adding the GConf key, there is now also a checkbox in the preferences dialog. This should make it much easier to use this functionality. 

I've also sent the patch to the Empathy developers, so this will hopefully be taken care of in the official packages soon.

Hope this helps someone! :P

---

### Post by mlnease on 2009-11-17
This is one of those things that I have no clue how the developers thought was a good idea.

In this day and age where privacy is important forcing to log all the conversations?

Well, here is how to delete them. You may create a script to click on when you want to delete them or you may turn it into a cron process to delete de logs at regular intervals.

The logs are under 
```
~/.local/share/Empathy/logs
```To remove the logs just execute:
```
rm -fr ~/.local/share/Empathy/logs
```Thanks, Rarsa--very helpful, worked a treat.

mike

---

### Post by pubo68 on 2009-11-24
I think the solution could be (From user's home directory):

```
$ rm -rf .local/share/Empathy/logs

$ ln -s /dev/null .local/share/Empathy/logs
```


UHMM.. no... doesn't work :(

---

### Post by mmzepedab on 2010-03-31
Nice mate it really worked, thank you very much for your help.:KS

---

### Post by pjones0404 on 2010-05-08
Sorry for the noob question but how do i install from the ppa? I have added it using the instructions for 10.4. When i do the sudo apt-get update, it does not show as an available update for me? 

What do i need to do? Thanks in advance.

---

### Post by Muhammad Ahmed on 2010-05-08
sudo apt-get install empathy

---

### Post by pjones0404 on 2010-05-08
I tried that and it did not work. I added the ppa following these steps. 



sudo add-apt-repository ppa:smcgrath23/smcgrath

sudo apt-get update

Once these finish I ran sudo apt-get install empathy. It says that the latest version is already installed. But i do no thave the logging option.

---

### Post by pjones0404 on 2010-05-09
anyone else have any ideas on this?

thanks

---

### Post by pjones0404 on 2010-05-12
Bump

Curious what i need to do to install the ppa patch. I would love to be able to turn off th elogging feature in Empathy,

---

### Post by Sale on 2010-05-25
"Installing from PPA" rally means "adding a new software repository" to your Ubuntu.
In this case, go here:
[https://launchpad.net/~smcgrath23/+archive/smcgrath]("https://launchpad.net/~smcgrath23/+archive/smcgrath")
and follow the instructions. Although it looks like the patch is not hosted there any more (I've copied the link from one of the earlier postings in this thread).

---

### Post by elidoperezmd on 2010-06-07
will all this work in Empathy 2.30.1???

---

### Post by Krissi on 2010-07-08
> **mr_steve said:**
> I've updated my PPA package of Empathy, the current version is now 2.28.1.1-0ubuntu2~ppa3. Get it from [https://launchpad.net/~smcgrath23/+archive/smcgrath]("https://launchpad.net/%7Esmcgrath23/+archive/smcgrath").

This version has a new patch. In addition to adding the GConf key, there is now also a checkbox in the preferences dialog. This should make it much easier to use this functionality. 

I've also sent the patch to the Empathy developers, so this will hopefully be taken care of in the official packages soon.

Hope this helps someone! :P


This is excellent! Followed the instructions and pim pam, no more history. Dude you're a star. It is absolutely ridiculous that the history is kept, was imagining my girlfriend reading some stuff.... lets say I don't want her to read. Ubuntu and the whole open source experience rocks, just feel a bit guilty as at the moment there is little I can do to contribute in terms of coding (am just learning the ABC.. at the moment) but I'm pushing the concept to all my friends and people at my work. Have now got half the office operating on linux and a few friends and have had to little to no trouble shooting for them. And they all know I won't stop until I have them all off Windows. This community and the solutions that are so willingly given should be pointed out as an example of how the world "should" work though I know it never will.

Sorry for rambling, just a bit impressed guys. Good luck with the rest of 2010!

---

### Post by ithcy on 2010-07-12
In Ubuntu 10, the logs are found at ~/.local/share/Empathy/logs . Here's another easy way to disable them from a bash prompt:

[FONT="Courier New"]rm -rf ~/.local/share/Empathy/logs/*
chmod 000 ~/.local/share/Empathy/logs[/FONT]

This will delete all of the chat logs and make the logs folder unreadable and unwritable by everyone including you and Empathy. Empathy seems to deal with this gracefully.

If you're running an older Ubuntu, do the same thing for ~/.gnome2/Empathy/logs instead.

---

### Post by zargeus on 2010-07-13
> **ithcy said:**
> In Ubuntu 10, the logs are found at ~/.local/share/Empathy/logs . Here's another easy way to disable them from a bash prompt:

[FONT="Courier New"]rm -rf ~/.local/share/Empathy/logs/*
chmod 000 ~/.local/share/Empathy/logs[/FONT]

This will delete all of the chat logs and make the logs folder unreadable and unwritable by everyone including you and Empathy. Empathy seems to deal with this gracefully.

If you're running an older Ubuntu, do the same thing for ~/.gnome2/Empathy/logs instead.

Did not work for me using Ubuntu 10.4 and Empathy 2.30.2.  It put Empathy into a loop and I had to recreate the directory and chmod 755 for it to work again.

---

### Post by tenach on 2010-07-26
> **zargeus said:**
> Did not work for me using Ubuntu 10.4 and Empathy 2.30.2.  It put Empathy into a loop and I had to recreate the directory and chmod 755 for it to work again.

I think that the solution for this, aside from adding the ppa, would be to do what was suggested earlier:

> **pubo68 said:**
> 
```

$ rm -rf .local/share/Empathy/logs
$ ln -s /dev/null .local/share/Empathy/logs

```

Make sure that you're in your home directory when you type those in. (The $ shouldn't be typed.) I am currently employing this little trick.

---

### Post by koolander143 on 2010-08-17
> **tone77 said:**
> bump, has anyone figured out how to delete chat history yet?

You can do it through Rarsa's suggestion:

The logs are under 

Code:
    ~/.local/share/Empathy/logs 

To remove the logs just execute: 

Code:
     rm -fr ~/.local/share/Empathy/logs 

...or you can go about it this way if you feel unsure about using a terminal.

1. Click on PLACES, then HOME FOLDER

 2. Press CTRL + H (this will show you hidden files)

 3. Then, open these folders or double-click .local/share/Empathy/logs

 4. In logs you'll see your IM clients you have added.  Click on the  folder(s) and you'll see each contact you have had a conversation with.   If you double click on a contact you'll see the saved conversation  file.
 
 5. At this point you can just select the file and delete or you can  select your contact's folder and delete it.

I, completely, understand why people don't want their conversations stored. I hate my conversations to be stored somewhere too.  Hopefully the Ubuntu developers can fix this on Empathy.  I hope this was helpful.

---

### Post by potatan on 2010-09-23
For anyone still interested, this bug (or lack of a feature) will be fixed in Ubuntu Maverick, 10.10 due out next month.

See last page of 
[https://bugs.launchpad.net/empathy/+bug/411898](https://bugs.launchpad.net/empathy/+bug/411898)

---

### Post by commrad2002 on 2010-11-13
The others didn't work for me. 


I had use 

rm -fr ~/.local/share/TpLogger/logs

to clear chat logs in 10.10

---

### Post by marbss on 2011-01-03
> **koolander143 said:**
> You can do it through Rarsa's suggestion:

The logs are under 

Code:
    ~/.local/share/Empathy/logs 

To remove the logs just execute: 

Code:
     rm -fr ~/.local/share/Empathy/logs 

...or you can go about it this way if you feel unsure about using a terminal.

1. Click on PLACES, then HOME FOLDER

 2. Press CTRL + H (this will show you hidden files)

 3. Then, open these folders or double-click .local/share/Empathy/logs

 4. In logs you'll see your IM clients you have added.  Click on the  folder(s) and you'll see each contact you have had a conversation with.   If you double click on a contact you'll see the saved conversation  file.
 
 5. At this point you can just select the file and delete or you can  select your contact's folder and delete it.

I, completely, understand why people don't want their conversations stored. I hate my conversations to be stored somewhere too.  Hopefully the Ubuntu developers can fix this on Empathy.  I hope this was helpful.

Thanks this worked wonderfully on 10.10.  Thank you!

Ubuntu developers: Consider bringing back Pidgin-- why? Empathy lacks chat log deletion and lacks email notifications.

---

### Post by pcm_man on 2011-07-09
Folks I am running Ubuntu 10.10 which I think is the BEST release yet of Ubuntu.

Here is where the log and conversation files for Empathy are kept.

~/.local/share/TpLogger/logs

if you use the Nautilus to browse the directories you will see a sub-directory there with a name that is based on the IM service you are using like *yahoo*.  Go into that directory and ALL of your conversations for a contact are kept in a directory by the contacts name.  The nice thing about this is that you can be selective about which logs you wish to delete.

If you want to delete all the conversations just issue this command:

rm -fr ~/.local/share/TpLogger/logs

By the way for Empathy 2.23.1 there is an option in the Preferences under the "General" setting to disable logging.  It is a check box called "Log conversations".  That's it.  Like they say, if you know how to do it then it's easy!

---

