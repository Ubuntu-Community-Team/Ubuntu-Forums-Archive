---
title: "[SOLVED] 'Synaptic-installed-software' listing?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by egalvan on 2008-10-06
I remember reading that a file exists that has a list of all installed software. Synaptic/atp-get use this.

But I cannot remember the name of the file.

sources.list is the repos, which I have backed up.

I want to re-install Ubuntu, and don't want to go through the whole Synaptic search again...

I'm lost.

Thanks

ErnestG

---

### Post by drs305 on 2008-10-06
Run this to get a list on your desktop:
```
sudo dpkg --get-selections >~/Desktop/package-list

```

Restore/import it with:
```

sudo apt-get update
sudo dpkg --clear-selections  # to be used only immediately prior to next command
sudo dpkg --set-selections <~/Desktop/package-list # see note
sudo apt-get dselect-upgrade

```

Added:
The "--clear-selections" is used to change the status to deinstall of any non-essential packages. Use this command if you want to clone your other machine. If you might have additional packages on the new machine you wish to retain do not use this command.
Before running the --set-selections command, you might want to inspect the 'package-list' file to ensure what will happen when you run the command. You can view it with "cat ~/Desktop/package-list"

---

### Post by ghantoos on 2008-10-06
You can do this:
```

dpkg --get-selections > /backup/installed-software.log

```

To reinstall your applications later:
```

dpkg --set-selections < /backup/installed-software.log
sudo dselect

```

Cheers,

---

### Post by egalvan on 2008-10-07
Thanks for the help on this, it's going to be archived.

My computer just crashed, so restoring the data to other drives and fixing what broke is taking priority.

Thanks

ErnestG

---

### Post by Orange_and_Green on 2008-10-07
Dear egalvan,

I am working on a program that tries to automatise this task. Care to take a look?

[http://ubuntuforums.org/showthread.php?t=915712](http://ubuntuforums.org/showthread.php?t=915712)

Hope it helps, good luck:KS

---

### Post by hyper_ch on 2008-10-07
Run this
```

dpkg -l | awk '/ii/ { print $2 }' > packages.txt

```
and it'll put all installed packages into the textfile. Each packe on a seperate line.

Run this
```

dpkg -l | awk '/ii/ { print $2 }' | tr '\n' ' ' > packages.txt

```
and it will put all packages on one line. You can then reinstall by issuing:
```

sudo apt-get install `cat packages.txt`

```

---

### Post by drs305 on 2008-10-07
hyper_ch,

I like your solution better. It uses the more-familiar "apt-get install" rather than dselect (which is not installed by default).

---

### Post by egalvan on 2008-10-08
> **hyper_ch said:**
> Run this
```

dpkg -l | awk '/ii/ { print $2 }' > packages.txt

```
and it'll put all installed packages into the textfile. Each packe on a seperate line.

Run this
```

dpkg -l | awk '/ii/ { print $2 }' | tr '\n' ' ' > packages.txt

```
and it will put all packages on one line. You can then reinstall by issuing:
```

sudo apt-get install `cat packages.txt`

```

Extremely useful code, with good comments on what it's doing.
It's going into my permanent files.
Thank you very much.
ErnestG

---

### Post by oldos2er on 2008-10-08
You can also see this in Synaptic; in the lower left corner click Sections, Status; upper left corner click Installed.

---

