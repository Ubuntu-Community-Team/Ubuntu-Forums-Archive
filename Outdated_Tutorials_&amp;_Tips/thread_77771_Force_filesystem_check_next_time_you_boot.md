---
title: "Force filesystem check next time you boot"
date: 2005-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by fedetxf on 2005-10-17
This is easy and sometimes needed.
```

sudo touch /forcefsck

```

---

### Post by Velox Letum on 2005-10-19
Nice tip...making a simple script into a /usr/bin file for easy access.

---

### Post by kittcankitt on 2005-10-27
Will this just check the filesystem or prompt to fix/repair any problems?  If not, how would you go about fixing if problems were reported?

Nice tip however.  Thanks

---

### Post by fedetxf on 2005-10-28
[QUOTE=kittcankitt]If not, how would you go about fixing if problems were reported?[/QUOTE]
If it finds problems a command line appears and you have to enter some sommand I don't remember, but it was somethign like fsck -f /dev/hdaX or something like it. You can use man fsck to check, but it depends on the error it finds...

---

### Post by shooterae5 on 2006-02-18
I'm learning how to wright scripts, and used this command as one of my first lesions. Here's how I've setup a shortcut using this command:

- make a directory in your home directory named "bin".
	(most of us have done this already) 

- right click and create a "new file", name it "checkfs.sh"

- open this file in gedit, and add the lines:

		sudo touch /forcefsck
		sudo reboot 

-save this file.

- How in your user home dir. go to the view menu and select "show hidden files"

- locate the ".bashrc" file. This is where you can add aliases to your scripts. About the middle of this file is a section that already has some useful aliases. Add this alias to that section:
  
		#beginning user added aliases
		alias restart='sh /home/dale/bin/checkfs.sh'

		note: I added the comment (# bla bla bla) so I can find
		all the changes I've made easy. It's a good idea in case
		you break somethnig down the road.

-save this file.

Now open a thermal or the run command and type "restart". you'll be asked for the root password, then be logged out, and reboot with the fsck. I know this is very sample to a lot of users, but, this little setup spark a whole bunch of scripts I how use on a regularly. It was kinda like my own "hello world".

---

### Post by dominikgeisler on 2008-01-10
isn't 
```
alias restart='sudo touch /forcefsck && sudo reboot'
```
a lot easier than the sh file?

---

### Post by zamolxis on 2008-06-30
I'd rather do all my customizations in a separate file.

Here is an example of a mybashrc file in your ~/bin directory:
[http://ralf.beckesch.de/download/dev/bash/mybashrc](http://ralf.beckesch.de/download/dev/bash/mybashrc)

To call it, you would just add this to your .bashrc:```
#if [ -e ~/bin/mybashrc ]; then
        . ~/bin/mybashrc
fi
```

The reason why you would do that is that on large systems, on upgrades, the admin would push a new .bashrc file into your home directory, making you lose your customizations. Although ubuntu might not be doing that, I still think it's a good idea.

Besides, the existing .bashrc contains the following as a suggestion: ```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```

---

### Post by monoufo on 2008-06-30
this didn't work.  i made it check both my / and /home partition. (you guys should really be using separate partitions for home, I do that in linux and windows), but it didn't fix either of them.

---

