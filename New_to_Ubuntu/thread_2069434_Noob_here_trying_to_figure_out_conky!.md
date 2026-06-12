---
title: "Noob here trying to figure out conky!"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by MoralAnarchy on 2012-10-10
Hey guys I'm new to ubuntu and I was trying to get conky put on my desktop.  Well I think I messed something up on the first time I tried to configure it with a custom design so I wanted to uninstall it completely and reinstall it to see if it would work again.  The problem I'm having is that in my /etc folder the conky package won't go away and it says I don't have permission to delete it.  I believe this might be causing me trouble when trying to reinstall conky because of the residual package.  Can somebody please help and tell me how to get rid of a folder in /etc?

I have to leave for work in an hour or so where I won't have internet access so I hope I can get some help quick!

---

### Post by twipley on 2012-10-10
Well -- here you go, in all its quickiness:

chmod a file through the terminal (ctrl-alt-t);

for example, chmod 777 /etc/this-folder

makes "this-folder" writable, editable, deletable.

---

### Post by MoralAnarchy on 2012-10-10
It's giving me the response-

chmod: changing permissions of '/etc/conky': Operation not permitted

---

### Post by twipley on 2012-10-10
Can you try appending sudo to chmod?

e.g.,

sudo chmod -R 777 /etc/folder

(uppercase R is important for recursive chowning)

[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by MoralAnarchy on 2012-10-10
It's just restating the @terminal command line as if I didn't type anything :/ .  I have to get going to work now but I will try to use my phone browser if I can.  Thank you for you help twipley! I hope I can figure this out! :p

---

### Post by twipley on 2012-10-10
I think it is mission accomplished, meaning you should now have the permission to delete it!

(Alternatively, one could have used "sudo rm -r /etc/conky" for the conky folder, and all its contents, to be deleted.)

Cheers, MoralAnarchy! ;)

---

### Post by MoralAnarchy on 2012-10-10
Been messing around at work on my laptop and all of a sudden PRESTO! The file was gone. Thank you for all your help!:D

---

### Post by stinkeye on 2012-10-11
How are you trying to customize conky?
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12275031&postcount=6")
Uninstalling conky completely will not remove the **~/.conkyrc** file you may have created.
Conky looks for a config @ **~/.conkyrc** and if it doesn't exist, will then use the config @  **/etc/conky/conky.conf**

---

### Post by LuisGMarine on 2012-11-18
> **stinkeye said:**
> How are you trying to customize conky?
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12275031&postcount=6")
Uninstalling conky completely will not remove the **~/.conkyrc** file you may have created.
Conky looks for a config @ **~/.conkyrc** and if it doesn't exist, will then use the config @  **/etc/conky/conky.conf**

Thank you for this information, it was great in answering my questions.

---

