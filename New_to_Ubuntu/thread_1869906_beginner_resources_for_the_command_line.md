---
title: "beginner resources for the command line?"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by eyehatehippies on 2011-10-26
Looking for any and all resources on the command line. Starting from introduction to more advanced functions. Any help appreciated!

---

### Post by haqking on 2011-10-26
> **eyehatehippies said:**
> Looking for any and all resources on the command line. Starting from introduction to more advanced functions. Any help appreciated!

[http://linuxcommand.org](http://linuxcommand.org)

and remember

```
man <command>
```

```
apropos <description or command>
```

---

### Post by ubume2 on 2011-10-26
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Not ubuntu specific:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

[http://www.tuxfiles.org/linuxhelp/linuxfiles.html](http://www.tuxfiles.org/linuxhelp/linuxfiles.html)

---

### Post by metalf8801 on 2011-10-26
CLI Companion might be able to help you 

I haven't really used it much even though I did install all it. I manly know about it from hearing about it on The Linux Action Show here's a link to that episode. 
[http://www.jupiterbroadcasting.com/5916/noobie-linux-bsd-tips-las-s15e09/](http://www.jupiterbroadcasting.com/5916/noobie-linux-bsd-tips-las-s15e09/) Which also had some other "Noobie Tips". However, CLI Companion is not in the main repository so you will need to getClicompanio...3.1_all.deb (or a newer version) from its page on Launchpad [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion)

It also has a nightly PPA on Launchpad but it may be less stable because its for developers [https://launchpad.net/~clicompanion-devs/+archive/clicompanion-nightlies](https://launchpad.net/~clicompanion-devs/+archive/clicompanion-nightlies)


Heres a cheat sheet I've used in the past 
[http://www.rain.org/~mkummel/unix.html](http://www.rain.org/~mkummel/unix.html)

I hope this helps 
Dan

---

### Post by Lars Noodén on 2011-10-26
[Bash Reference Sheet](http://mywiki.wooledge.org/BashSheet)
[Bash Guide](http://mywiki.wooledge.org/BashGuide)
[Bash Pitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by JRV on 2011-10-26
These are my favorites:

[http://ss64.com/bash/](http://ss64.com/bash/)
[http://freeos.com/guides/lsst/](http://freeos.com/guides/lsst/)

---

### Post by nothingspecial on 2011-10-26
> **Lars Noodén said:**
> [Bash Reference Sheet](http://mywiki.wooledge.org/BashSheet)
[Bash Guide](http://mywiki.wooledge.org/BashGuide)
[Bash Pitfalls](http://mywiki.wooledge.org/BashPitfalls)

+1

If, however, you are looking for guides on how to use command line apps. Have a look here

[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)

---

### Post by collisionystm on 2011-10-26
> **eyehatehippies said:**
> Looking for any and all resources on the command line. Starting from introduction to more advanced functions. Any help appreciated!

In Ubuntu, you will find the following useful.

**sudo** allows you to do "administrative" things in the system. ROOT is the windows equivalent of administrator and **sudo** gives you these privileges.

when typing something, use the **TAB** key on your keyboard to auto complete your text

If you are not sure what variations you can do with a command, try typing the command word and then --help

I.E.  **sudo --help**
To read about the command, prefix it with **man** ( short for manual)

I.E. **man sudo**

If you read the manual on something, you will need to know how to close out of it. You use **:q**  that is a **colon** and the letter **Q** this will close the manual.

**apt-get **is a the command line of the software center.
You use **apt-get update** to refresh the packages that are available
**apt-get upgrade** to install the latest versions.
**apt-get install** to install a program.
**apt-get remove **to uninstall something.
Remember, you can use **TAB **anywhere in the command line. So instead of typing out an entire program name, just type the first few letters and hit **TAB**. FYI, commands are almost always case sensitive. 

You will want to brush up on **Chown** it is the method of setting folder and file permissions via the command line.
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

Also read up on **Chgrp** . It is the method of Changing what group a folder or file belongs to to. It goes hand in hand with **Chown**.
[http://en.wikipedia.org/wiki/Chgrp](http://en.wikipedia.org/wiki/Chgrp)

**rm **removes a file
**rm -R **removes folders and whatever is inside of them. The **-R **means recursive. 
**cp** is copy and can also be used with the **-R**
**mv** is move, and can also be used to rename a file. This also works with the **-R**
**ls** lists the files in the current directory
**ls -lh** lists the files and their permissions. This will be used with **chown and chgrp**

**cd** will change you to a different folder or directory in the system.
I.E. When you first open terminal you are at your /**home/username** directory. To move to your Downloads folder you would, **cd Downloads** . You should now be in your downloads. You can use **ls** to view the files in here.

**cd ..** takes you back a directory. So to get out of Downloads and back to home, you **cd ..** and now you are back in **/home/username**

If you want to edit a file from the terminal, I strongly suggest you use **nano**. You will see a lot of references to **vi** but you should use **nano** in place of it. Both Nano and VI are text editors. Nano is just easier to use.

To **nano **a file you just simply, **nano filename** 
When done, you press **CTRL +X **then **Y **to save or **N **to discard changes.
**CTRL + W **to search for a word in the file.

Anything outside of your /home/username folder generally requires **sudo** unless you have set permissions on it using chgrp or chown to allow yourself to access it.


I think that is pretty much the basics that I would want to know. The rest of it you will figure out as time go's by and you want to do things with your system. Always **google** for stuff. I say google because it always returns the best results.

Good Luck!!! I hope I helped. :D

---

### Post by decoherence on 2011-10-26
Classic Shell Scripting by O'Reilly. It's a dry read and not specific to Bash but as the name implies, it's a classic and a good addition to any command line user's library. Work your way through that book and you'll know your stuff.

---

### Post by eyehatehippies on 2011-10-27
Thanks to everyone who responded. Didn't expect such an outpouring of help here. Thanks to everyone. I have enough links, etc. to keep me busy for some time. Much appreciated! =D

---

### Post by dfarrell07 on 2011-10-27
[http://www.playterm.org/](http://www.playterm.org/) is great. I highly recommend it. It has videos of experts doing things and giving some explanation. PlayTerm has been very helpful to me.

---

