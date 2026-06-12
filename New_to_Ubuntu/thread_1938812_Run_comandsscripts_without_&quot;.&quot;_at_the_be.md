---
title: "Run comands/scripts without &quot;./&quot; at the beginning"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by UnknownFearNG on 2012-03-10
Probably been asked hundreds of times, but I never know how to fix this. How do I make it so, if I enter a command, preferably from any folder, I can run it without having to put "./" at the beginning?

---

### Post by evilsoup on 2012-03-10
You need to put the file in a directory that is in your $PATH, that is: the list of directories Linux keeps, that it will search for when you type in a command. More info [here]("http://linuxcommand.org/wss0010.php#path").

The easiest (and best) way to do this is to create a directory at ~/bin. So in a terminal, type 

mkdir ~/bin

or you can do this by opening the file manager and create the directory through that. By default, Ubuntu has a line in your .profile that adds this folder to your $PATH if it exists. Note that you'll have to log out and then log in again for this to take effect. Any scripts that you put in this directory will be run just by typing their name, no matter where you are in the filesystem, and they can also be set to keybindings.

If for some reason you need to add a different folder (you almost certainly don't, if you need to store the script in another folder you'd be better off making a symbolic link to that file in your ~/bin), then open up your .profile - in a terminal type

gedit ~/.profile

and then add a line like this:

export PATH=/path/to/directory:$PATH

---

### Post by Cheesemill on 2012-03-10
Having to type ./ when an executable is not in your path is in some ways a security feature.

What would happen if I managed to save a file called ls or sudo (or any other frequently used command name) in your home folder with some nasty code in it and you then tried to use that command.....

---

### Post by AnojiRox on 2012-03-10
just put this into terminal:"bash /path/to/file/here.sh"

---

### Post by UnknownFearNG on 2012-03-11
> **evilsoup said:**
> You need to put the file in a directory that is in your $PATH, that is: the list of directories Linux keeps, that it will search for when you type in a command. More info [here]("http://linuxcommand.org/wss0010.php#path").


Ah, I remember seeing this link awhile ago. Thanks for reminding me about it and linking it :). This will be great help!

> **Cheesemill said:**
> 
What would happen if I managed to save a file called ls or sudo (or any other frequently used command name) in your home folder with some nasty code in it and you then tried to use that command.....

It would execute the custom script first, which would not be good.

---

