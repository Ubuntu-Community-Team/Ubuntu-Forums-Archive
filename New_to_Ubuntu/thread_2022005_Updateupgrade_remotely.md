---
title: "Update/upgrade remotely"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-07-10
I'm using Terminal on my iMac to check for any updates/upgrades on my Ubuntu machine.

The commands I use are :

sudo apt-get update

followed by sudo apt-get upgrade

When I go to my Ubu machine to see the results, in the Update Manager window it shows 19 updates have been selected, but clearly not installed.

What further commands should I be using?

(I have Googled, but, as is so often the case, the info is a bit more technically pitched than I understand and I don't want to guess at what to do.)

---

### Post by nothingspecial on 2012-07-10
Click the "check" button in the update manager which will reload your sources.

It should then say "There are no updates to install"

---

### Post by SlugSlug on 2012-07-10
You will have updated the box, but behind update manager's back.

If you close / refresh update manager the updates shown as available will disappear.

---

### Post by Penfold1971 on 2012-07-10
Thanks both.

Is there some command then, that will do the equivalent of either :

clicking the 'check' button in the update manager, or

closing/refreshing the update manager ?

I really am very new to this. Eventually I want to be able to remove the monitor, keyboard and mouse on the Ubu machine and let it get on with its sole task - processing Folding@home work units.

---

### Post by SlugSlug on 2012-07-10
You don't really need to but I guess you could

```
sudo pkill update-manager
```

To get rid of it after you have ran apt-get commands

---

### Post by Paqman on 2012-07-10
> **Penfold1971 said:**
> 
Is there some command then, that will do the equivalent of either :

clicking the 'check' button in the update manager, or

closing/refreshing the update manager ?


Yep:
```
sudo apt-get update
```

Your system will periodically check for updates this way anyway, and spawns Update Manager or the little notification icon if it detects that there are updates to install. You can control how often it quietly checks for updates through Software Sources.

---

### Post by Penfold1971 on 2012-07-10
Thanks, SlugSlug!

---

### Post by arubislander on 2012-07-10
Not all updates are applied with ```
$ sudo apt-get upgrade
``` Updates that would require installing new packages, or deïnstalling old ones are skipped. I am guessing that it is these kinds of updates that you are still seeing in the Update Manager.

---

### Post by SlugSlug on 2012-07-10
> **arubislander said:**
> Not all updates are applied with ```
$ sudo apt-get upgrade
``` Updates that would require installing new packages, or deïnstalling old ones are skipped. I am guessing that it is these kinds of updates that you are still seeing in the Update Manager.


This is right, 

you can ```
sudo apt-get dist-upgrade
``` 

This is needed for stuff like kernel updates

---

### Post by Penfold1971 on 2012-07-10
Ooops. Maybe I marked the thread as 'Solved' too soon.

> **SlugSlug said:**
> you can ```
sudo apt-get dist-upgrade
``` 
This is needed for stuff like kernel updates
So, are these the commands, one at a time, that I should use in order to get the full range of any and all updates that are available via Software Manager ? :

 ```
sudo apt-get update
``` or should it be ? : ```
sudo apt-get dist-update
```
 ```
sudo apt-get dist-upgrade
sudo pkill update-manager
```

Why the two commands 'update' and 'upgrade'? Does 'update' see what is available, and 'upgrade' perform the installing?

---

### Post by SlugSlug on 2012-07-10
> **Penfold1971 said:**
> Ooops. Maybe I marked the thread as 'Solved' too soon.


So, are these the commands, one at a time, that I should use in order to get the full range of any and all updates that are available via Software Manager ? :

 ```
sudo apt-get update
``` or should it be ? : ```
sudo apt-get dist-update
``` ```
sudo apt-get dist-upgrade
sudo pkill update-manager
```Why the two commands 'update' and 'upgrade'? Does 'update' see what is available, and 'upgrade' perform the installing?


Yes update sees whats there and upgrade grabs them

I wouldn't bother with the kill tbh, if its not got a monitor you wont see it :)

I have a alias in my ~/.bashrc...

```
alias qq="sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get autoremove"
```
so when I log in I just hit qq to update the system :)

---

### Post by Penfold1971 on 2012-07-10
So for the first command, the updater, it's just plain ```
sudo apt-get update
``` and not ```
sudo apt-get dist-update
``` ?

---

### Post by SlugSlug on 2012-07-10
yer update pulls down the repo lists so apt can check if there is an update for any app, upgrade or dist-upgrade downloads / installs updates that apt is now aware of thanks to the update

if that makes sense? got a bit carried away with the word update :)

---

### Post by Penfold1971 on 2012-07-10
Sure, but I'm wondering if it's just plain ```
sudo apt-get update
``` as opposed to ```
sudo apt-get dist-update
```
There's no need for "dist-" in front of "update"?

See how easy it is for a noob to flounder in the dark?:grin:

---

### Post by SlugSlug on 2012-07-10
No, there's no need for dist- in front of update,  update just updates the list of available software

---

### Post by Paqman on 2012-07-10
> **Penfold1971 said:**
> 
There's no need for "dist-" in front of "update"?


Correct, apt-get dist-upgrade is a completely separate command, you don't just go around sticking dist- on the front of other commands.

---

### Post by Penfold1971 on 2012-07-10
> **Paqman said:**
> Correct, apt-get dist-upgrade is a completely separate command, you don't just go around sticking dist- on the front of other commands.
Cheers.

And one final question just to pin this down, please :

Is the command ... [FONT="Courier New"]sudo apt-get dist-upgrade[/FONT] ... all-inclusive?

I don't need to do plain ... [FONT="Courier New"]sudo apt-get upgrade[/FONT] ... as well, do I?

---

### Post by SlugSlug on 2012-07-10
> **Penfold1971 said:**
> Cheers.

And one final question just to pin this down, please :

Is the command ... [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] ... all-inclusive?

I don't need to do plain ... [FONT=Courier New]sudo apt-get upgrade[/FONT] ... as well, do I?


Correct :)

---

### Post by Penfold1971 on 2012-07-10
Brilliant! Thanks SlugSlug.

Many thanks to verybody for the help.

I think this thread really is 'Solved' now. :lol:

---

