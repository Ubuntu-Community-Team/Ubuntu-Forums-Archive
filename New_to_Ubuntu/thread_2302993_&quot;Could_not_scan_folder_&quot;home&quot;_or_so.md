---
title: "&quot;Could not scan folder &quot;/home&quot; or some of the folders it contains&quot;"
date: 2015-11-15
forum: New to Ubuntu
---

### Post by franklin4 on 2015-11-15
Ok, I've ran into a problem with my Ubuntu machine. I'm a recovering Windows user who's trying to learn another OS. Running 14.04 on a dual boot HP laptop.

Received "***Could not scan folder "/home" or some of the folders it contains***" with a small "***permission denied***" when I ran the Ubuntu disk usage analyser. I've ran this utility several times over the past few months w/o receiving this error. I'd like help on what I need to do to clear this error. I've searched the exact term, without result. And searching of related keywords produces thousands of response. If this has been covered elsewhere, I apologize.

Background: Over the past few months my machine has become increasingly slow. Usually manifested by the system briefly locking up, screen going light gray, and then starting working again a few minutes later.

So a few days ago, I ran BleachBit, which is where I think my problems began. Due to my own misunderstanding of what the overwrite function did, I mistakenly selected this option. The software seemed to execute ok, except it would repeatedly get to the last 10% or so of the process and hang up ... all but locking the machine. It would usually be accompanied by a message about less than xxxMB of space left on hard drive.

In an attempt to recover the machine, I had to reboot. I ran BleachBit again last night, this time not using the rewrite, and the system is running much faster. I ran the disk utility this morning, and got the error. I'm not sure if helps or not, but also attached is a screenshot of my GParteEd display.

Thanks,
Frank

[ATTACH=CONFIG]265592[/ATTACH]

---

### Post by furtom on 2015-11-18
Most likely, you have some files or folders written with as root (ownership), probably hidden. This happens, even though it probably shouldn't.

It usually doesn't cause any problem, but it's true you can't scan for disk usage for those folders as a regular user. It's usually some config file of 8kb, so it's really not much of a disk usage issue.

I really wouldn't fret over it. Nevertheless, if you want to change this behavior, change the ownership of files in your home directory. 

[FONT=Courier New]```
sudo chown -R $USER:$USER $HOME

```
[/FONT]
Should do it.

---

