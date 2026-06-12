---
title: "Can not remove all of tint2 for the life of me!"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Malacant on 2012-10-12
Hey guys...I have been pulling my hair out over this. Somehow I managed to install the older version of tint2. I thought for sure I removed it by doing:
```
sudo apt-get remove tint2
```
I think downloaded the stable version(2-0.10 I believe) and installed it. Well, it still isn't working properly. All this started when I was trying to add launcher icons to my tint2 bar.
So, I figured I would remove everything tint2 related so I did:
```
sudo apt-get remove tint2
```
Althought when I typed
```
tint2 -v
```
It says:
```
tint2 version 0.11
``` 

I've even tried going into the Synaptic Package Manager to see if anything was in there. I saw quite a few tint2 entries but non appeared to be installed

I just want to remove all traces of tint2 and get the proper one working(which will probably be another post since after hours of trying this I am ready to pull my hair out).

---

### Post by vasa1 on 2012-10-12
Did you try sudo apt-get purge instead of apt-get remove?
Also, have you checked in your home folder for remnants? They could be hidden (dot) files.

---

### Post by Malacant on 2012-10-12
Yes. Everytime I try sudo apt-get purge the output is:
```
sudo apt-get purge tint2
[sudo] password for malacant: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tint2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

And I went through every folder I could remember it had. Ctrl+H and deleted all the configs and tint2 folders I used. I do know there is still a file that I can't delete:
```
whereis tint2
tint2: /usr/local/bin/tint2

```

Can't delete that one, could that one file be causing this many problems?

---

### Post by vasa1 on 2012-10-12
Well, something is messed. Let's hope an expert drops by!

---

### Post by Pletched on 2012-10-12
Everything outside of your home folder is owned by root. I think that is kind of true.

Issue this command to delete the file.

```
sudo rm /usr/local/bin/tint2
```This works too.

```
sudo rm `which tint2`
```

Is this what you saw? tint2 (0.11+svn20111022-2build1)

---

### Post by DuckHook on 2012-10-12
> **Pletched said:**
> Everything outside of your home folder is owned by root. I think that is kind of true.

Issue this command to delete the file.

```
sudo rm /usr/local/bin/tint2
```

This will not work. The *rm* command will not delete directories containing files or subdirectories without the *-r* option. You must also add the *-f* option for forced deletion.

**!!!!HOWEVER!!!!**

I ***never*** recommend using the *rm* option to new users, especially those coming from Windows. And doing so with *sudo* is just asking for trouble. The old Linux habits are not ingrained enough in new users to avoid trouble.

For example, in the situation above, the user should first *ls* the directory to see what it contains, and, if satisfied that it is safe to delete, should first *mv* (move/rename) the directory to a location not defined on their path. If this breaks a dependency needed elsewhere, then it's easy to recover.

It is never a good idea to remove packages outside of apt, or it's GUI front ends, in this case, Software Centre or Synaptic. However, since the user has assured him/herself that the package is no longer recognized by apt, s/he should do the following:

1. open a terminal
run:

```
gksu nautilus
```type in your password at the prompt. ***WARNING***. You are now exploring, moving, deleting and working with root privileges. You can really hose your system if you are not careful.

The advantage of using *nautilus* is that most new users, especially from Windows, are used to it and will take the time to see what is inside a directory before deleting anything.

2. Now, drag the directory in question to your desktop. You have just relocated it to a spot where the system cannot find it.

3. ***Immediately*** close *nautilus*. You do not want to do anything else with a file manager while in *sudo* mode.

Leave this directory on your desktop for a week or so while you continue to launch programs and otherwise work with your system. It does no harm having it lying around. If apt continues to function without generating errors, and if everything remains hunky dory, then delete it permanently after a week. If any part of your OS complains, then put the directory back by reversing the steps above and no harm done.

Be safe. Be happy.;)

---

### Post by Pletched on 2012-10-13
Programs complied by the user are places in /usr/local/bin. It wasn't installed by apt and so not listed.

---

