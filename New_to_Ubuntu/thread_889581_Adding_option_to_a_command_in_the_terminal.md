---
title: "Adding option to a command in the terminal"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Nasa01 on 2008-08-14
Hi

I was just wondering if it's possible to add an option to a command as a standard. What I want is this:

instead of having to write 'root -l' all the time, I want the terminal recognize the command 'root' as if I wrote 'root -l'

Did I make any sense?

FYI, ROOT is a Object-Oriented Analysis Framework ([http://root.cern.ch](http://root.cern.ch)) so I'm not confusing it with the root usr. ;)

/Oscar

---

### Post by ds[de] on 2008-08-14
Hi,

this is done by typing 
```
alias root='root -l'
```

or, if you want the change to be permanent, you can add

```
alias root='root -l'
```
to your /home/user/.bashrc in the 'alias'-section.

Regards,
ds[de]

---

### Post by Oldsoldier2003 on 2008-08-14
> **Nasa01 said:**
> Hi

I was just wondering if it's possible to add an option to a command as a standard. What I want is this:

instead of having to write 'root -l' all the time, I want the terminal recognize the command 'root' as if I wrote 'root -l'

Did I make any sense?

FYI, ROOT is a Object-Oriented Analysis Framework ([http://root.cern.ch](http://root.cern.ch)) so I'm not confusing it with the root usr. ;)

/Oscar

Edit your .bash_aliases file:

```
alias root='root -l'
```
please note that there is no space before or after the "="

The next time you start a shell your alias will be sourced.

edit: as stated above you can edit your bashrc, but it is "cleaner" to use the alias file,

---

### Post by Separ on 2008-08-14
The bashrc file is actually located at ~/.bashrc. You may also have to create the ~/.bash_aliases file manually.

---

### Post by sayakb on 2008-08-14
You may create a script file and copy it to /usr/bin
For example, a standard bash script **test.sh** looks like this:
```

#!/bin/bash
command1
command2
.
.

```
After making the file, do:
```
chmod +x test.sh
sudo cp test.sh /usr/bin/test.sh
```

---

### Post by Nasa01 on 2008-08-14
Thank you!

I didn't get the .bash_aliases file to work, though adding the alias-line to the .bashrc worked nicely! 

Cheers!
:)

---

