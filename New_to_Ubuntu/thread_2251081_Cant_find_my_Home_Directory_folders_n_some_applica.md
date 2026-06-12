---
title: "Cant find my Home Directory folders n some applications after system upgrade"
date: 2014-11-01
forum: New to Ubuntu
---

### Post by tictactoe2 on 2014-11-01
I cant locate or find my home directory files and folders including some application softwares after Ubuntu system upgrade t0 14.04 lts.But when I checked these on the Terminal its all in there. How can I retrieved it back just the way it used to be. Thanks guys.

---

### Post by yancek on 2014-11-01
I'm not sure what the problem is.  Are you able to see your /home directory by running a command such as: ls /
from a terminal but not see them in a filemanager?  What's the output of the command:  df -h

---

### Post by tictactoe2 on 2014-11-02
Hi Yancek, Thanks for your message. Yes I can see all my files and folders from the terminal itself by typing ls command/ Unfortunately  I cant find  the Home Folder where my Documents Music folders resides. Also on the System Settings,Appearance Icon is also missing, where you can tweak or manipulate screen and serves as another route to get into your Home Folder directory..  I dont know what sudo command I need, for it to pop back into my screen? Do i need to encrypt these folders on the terminal just to be safe?

Which among the lists on df -h you want to know?
Filesystem Size Used Avail Use% Mount on

Hope to hearing from you soon. Cheers mate

---

### Post by deadflowr on 2014-11-02
What did you upgrade from?
(I default to guess basic normal Ubuntu, so...)
Have you tried running a simple dash search for an app called Files?

---

### Post by tictactoe2 on 2014-11-02
I can only see my files and folders on the terminal unfortunately

---

### Post by deadflowr on 2014-11-02
I should rephrase myself.
What version of 'buntu, normal or something else, like Xubuntu?
Which version was it before the upgrade?

ftr, Home Folder was renamed Files, after 12.04.

From a terminal run
```
nautilus
```
 Do you get a window open for the home folder directory?

If normal Ubuntu, do you have a launcher dock down the leftside?
If when you ran the command above, does an icon now appear in that launcher dock?


Sorry for the seemingly random questions, it's just we would need some more to go on...

---

### Post by tictactoe2 on 2014-11-02
Hey, Thanks for your message. I now have Ubuntu 14.04 from 13.10.I dont have nautilus. Do I need to install it? FYI Also use gnome shell.
Post Script: It was my friend who 1st installed ubuntu on my laptop. Its quite strange I dont have nautilus since Im using Gnome shell for its the default file manager. Just learned it few minutes ago. Im sure he made some changes.Lately I tried to install Apache2 Actually the LAMP Stack,It didnt work out pretty well , thats why I decided to just upgrade the system but while ,  I started  to encounter problems with Samba winbind and  Gnome display manager.To resolved the issue, I used GNU GRUB  to sort things out. Unfortunately I dont see my Home Folder now. Im not a computer geek, so please bare with me guys.need your patience here. thanks

---

### Post by deadflowr on 2014-11-02
Odd, nautlius is the gnome file manager, so seems weird it wouldn't be installed, or that it was somehow uninstalled.
so yes install it.

Edit: unless you purposely uninstalled it and installed a different file manager, which I assume you did not do.

---

### Post by tictactoe2 on 2014-11-02
kindly read my previous post, .. Oppss hang on a minute .I will install it now.

---

### Post by deadflowr on 2014-11-02
Well, now knowing that your friend helped install the system, it's quite possible they have added or remove packages.
Perhaps they replaced nautilus with something else, like the Linux Mint built/sponsored(?) file manager known as nemo.
It could be that if that's the case, then maybe during the upgrade the configurations for nemo got messed up, or something.
Of course this is total speculation on my part.

And if by some miracle it's right, and nemo was set as the file manager. Installing nautilus will not hurt the system.
In case you wonder about having two or more file managers installed.

---

### Post by tictactoe2 on 2014-11-02
aww, I think youre right, so what do I do now? I just finished installing it.Do i need to restart my laptop to see if it works? SORRY if Im now asking a very stupid question.I just dont want to messed things up again.

---

### Post by deadflowr on 2014-11-02
nautilus should start, like any other app, just try to open it, or look for an app called Files.
There should be no need to restart.

It would probably also be best to ask your friend if they did indeed do anything, like change file managers.
That way, when you might be in need of support, you will as least have an idea of what's not typically there.
If that makes sense.

---

### Post by tictactoe2 on 2014-11-02
Amazing!! It worked :) it really is !! I can now see my files. Thank  you so much!!
!! Youve got no idea how happy I am right now!! over the moon really :) 

Have a great week ahead Flwr 
Cheers!!

---

