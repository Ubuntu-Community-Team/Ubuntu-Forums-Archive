---
title: "bash"
date: 2010-06-01
forum: Programming Talk
---

### Post by Drenriza on 2010-06-01
i don't know if this is the right place, since bash aren't a full "language". 

But here goes. I'am at the moment trying to learn bash. And its going slowwwwwww.

I'm on my second very very basic bash script. to just use the command apt-get to update and upgrade. But i cant get it to work.

I wanted the script to

#1 log in as root
#2 type password
#3 apt-get update
#4 apt-get upgrade
#5 exit

What i did

```
#!/bin/bash

apt-get update

apt-get upgrade

echo "dit system er nu fuldt opgraderet"

exit
```

Then i gave the file 4755 permissions. Since i don't know how to give root permissions through a script. And then exit again.

But when i try to execute the script it says,

E: Kunne ikke åbne låsefilen /var/lib/apt/lists/lock - open (13: Permission denied)
E: Kunne ikke låse listemappen
E: Kunne ikke åbne låsefilen /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


My first script was. Was fun to try out. And also im lazy so this makes it easy if i need to do it again :p

```
#!/bin/bash
clear
echo -n "press 'G' to start "
read n
if [ "$n" = "G" ]; then
wget www.kegel.com/wine/winetricks
clear
sh winetricks corefonts tahoma vcrun2005sp1 wsh56js
fi

clear
echo "gå -> programmer -> wine -> konfigurer wine"
echo "gå i biblioteker-fanen"
echo "slet alle brugere"
echo "lav 2 nye brugere"
echo "riched20 og usp10"
echo "editer riched20. Gør denne bruger til microsoft infødt."
echo -n "press 'G' for at lukke dette "
read n
if [ "$n" = "G" ]; then
exit
else
echo "haha lukker ned NU"
exit
fi

```

Thanks on advance.
Kind Regards.

---

### Post by Drenriza on 2010-06-01
What i found out i could do was.

```
visudo
```

```
username ALL = NOPASSWD: /path/to/script
```

to give it root permissions.

But why does the 4755 permissions not work? maybe its to early in the morning, but i cant quite figure it out.

---

### Post by roccivic on 2010-06-01
even 777 will not work. The permission only establishes who can run the script. But it doesn't just give anyone super user powers out of the blue, that would be nuts. You still need to authenticate. Besides you need:

```
sudo apt-get update -y
sudo apt-get upgrade -y
```

No need for exit either, it's implied

---

### Post by BoneKracker on 2010-06-01
> **roccivic said:**
> even 777 will not work. The permission only establishes who can run the script. But it doesn't just give anyone super user powers out of the blue, that would be nuts. You still need to authenticate. Besides you need:

```
sudo apt-get update -y
sudo apt-get upgrade -y
```

No need for exit either, it's implied

Actually, on some linux distros, you can indeed achieve this with permissions, although it won't work on Ubuntu and a number of other distros): [Edited to reflect comments by geirha below, thanks geirha]
```
chown root:admin chmod 4750

```(Replace admin with whatever group on your system is appropriate.
However, making things SUID root like that is a _bad practice_ that creates security holes, and SUID root should only be used very reluctantly when there's no other way to get something accomplished.

Better is to just run the script using
```
sudo <script>
```

If you happen to be planning to run this script from the system cron, it will run as root anyway.

Also, for any script that needs to be run as root, it's more secure to use the full path to commands (a good practice, where it's not terribly inconvenient):```
aptget="/usr/sbin/apt-get"
$aptget update -y
$aptget upgrade -y
```

**Note:** replace "/bin/apt-get" above with the correct path.  I don't use a Debian derivative, so I don't know what the right path is.

---

### Post by geirha on 2010-06-01
> **BoneKracker said:**
> Actually, you can indeed achieve this with permissions:
```
chown root:admin chmod 4750

```(Replace admin with whatever group on your system is appropriate.
However, making things SUID root like that is a _bad practice_ that creates security holes, and SUID root should only be used very reluctantly when there's no other way to get something accomplished.


Actually, no you can't. suid on scripts are disabled on most systems, including Ubuntu. (It works on binaries though)

---

### Post by BoneKracker on 2010-06-01
> **geirha said:**
> Actually, no you can't. suid on scripts are disabled on most systems, including Ubuntu. (It works on binaries though)
I was not aware this is disabled on Ubuntu (or Debian or whoever did this).  That seems like it's probably a good idea.

Can you point me to another source that says this is true about "most systems", because this is first time I've run into it.

---

### Post by geirha on 2010-06-01
[http://en.wikipedia.org/wiki/Setuid#setuid_on_executables](http://en.wikipedia.org/wiki/Setuid#setuid_on_executables)

The «most» could be an exaggeration on my part. Wikipedia says «many», that's probably a safer word to use.

---

### Post by BoneKracker on 2010-06-01
> **geirha said:**
> [http://en.wikipedia.org/wiki/Setuid#setuid_on_executables](http://en.wikipedia.org/wiki/Setuid#setuid_on_executables)

The «most» could be an exaggeration on my part. Wikipedia says «many», that's probably a safer word to use.
On the three or four occasions I've been really tempted to set SUID on one of my own scripts, I've found a way to avoid it.  So I'd say this is probably a good policy.

Thanks for the link.  Corrected above to minimize confusion.

---

