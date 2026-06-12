---
title: "HOWTO: Hide unix file structure"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Wolki on 2005-10-15
The unix file structure developed over decades, and has withstood the test of time pretty well, for a large variety of uses - servers, computer pools, home desktops, and more. But for new users it can be confusing - "What exactly is a /var? What's /usr, I am the user, so do I put my stuff there? And why can't I write into that directory? Linux is so hard!" The answer is, of course, if you don't know about it, you probably don't need to do anything there, or even know it exists. Default Breezy already makes going outside the boundaries of the /home/ directory mostly unnecessary. But some people, even new users, like exploring, and are used from other operating systems to start at the top of the structure. So the next time you set up a Ubuntu install for inexperienced users, consider the following:

1. Open a terminal and execut "ls -1 / | sudo tee /.hidden"

2. Do "sudo chmod a+r .hidden"

3. If you want all standard files hidden, skip to 5. Otherwise. open the file with "sudo gedit /.hidden".

4. Remove every directory you don't want to hide from the file. Here's how mine looks like, as an example:
```

bin
boot
opt
usr
etc
sys
tmp
srv
proc
root
sbin
lib
lost+found
mnt
initrd
dev
debootstrap
var
cdrom
initrd.img
initrd.img.old
vmlinuz
vmlinuz.old
home
media

```

5. Now, let's create some entries that are easier for new users: select "home" and create a link to link to it (for example, by dragging it and holding <ctrl>+<shift>. Your mouse cursor should show two linked circles when dragging while holding them, if they do you're creating a link). Rename that link to "User Data" or something similar. Do the same with media; rename it to "Drives" or "Media" or what you want. (If the files are already hidden. show them with <ctrl>-<h>.)

6. If you want to have a discoverable way to some or all of the now hidden files, create a folder called "System Data". Create links to all the other files and directories there.

7. You're done! :) Update an open Nautilus with <ctrl>-<r>, or restart it with "killall nautilus".

I attached a screenshot of how it looks like.

Now, some anticipated FAQs:

Q: Won't this royally screw my system?
A: I see no reson why it should. Everything is still in it's original place, only no longer visible by default. It definitely works fine here and on several other Ubuntu installations.

Q: Are there any negative side effects?
A: Not that I know of. From the command line, everything stays the same. If you encounter any problem, please tell me!

Q: I want to access one of the hidden folders. How do I do that?
A: View -> Show Hidden Files. Or press <ctrl>-h

Q: I don't like this! How can I undo it?
A: Simple, just remove the .hidden file. Delete the links you created in step 5 and 6 if you want, or leave them there. Just make sure you don't accidentally delete the original folders. :)

Q: Can I have all the files shown automatically if I have a sudo'd nautilus?
A: Certainly. Make sure that the .hidden file is owned by root (should be automatically), then, in the permissions tab, disallow read access for the owner.

Q: Can I do that .hidden stuff in other directories too?
A: Yes. It's a pretty cool feature.

Q: Are there any limitations to this?
A: Yes, the file selector (ie open dialog) will still show all the files. The .hidden file currently only applies to Nautilus.

---

### Post by macgyver2 on 2005-10-15
Very interesting howto.  I wonder, though, would it not be better to educate a new user rather than hide things from her or him?  It's not at all hard to go over the directory structure with someone after you install Linux on her or his computer.  If new users ask about not being able to write to certain directories, it would be far better to use that question as a jump-off to teach them about permissions.

---

### Post by Wolki on 2005-10-15
[QUOTE=macgyver2]Very interesting howto.  I wonder, though, would it not be better to educate a new user rather than hide things from her or him?[/QUOTE]

It's a good idea to teach users, but not everyone wants to learn that much. I've intended this howto to leave options for future learning open, so people can advance at their own pace. There is a lot to learn when you start using an unfamiliar system, and I think there are things that matter more than the classical file system.

Thank you for reading and commenting :)

---

### Post by joelito on 2005-10-17
Does the hidden file goes in / ?

EDIT: BTW, I found another trick by setting the permisions of / as 722

or sudo chmod 722 /

---

### Post by Wolki on 2005-10-17
[QUOTE=joelito]Does the hidden file goes in / ?[/quote]

Exactly. My instructions above were not clear, thanks for pointing it out!
And it's ".hidden", the dot is important

> EDIT: BTW, I found another trick by setting the permisions of / as 722

or sudo chmod 722 /

Hm, what do you accomplish with this? rwx--x--x does not make sense to me as a setting for root, but maybe I'm missing something.

---

### Post by poofyhairguy on 2005-10-17
Great Guide. I will use this for new users in the future. Good job.

---

### Post by joelito on 2005-10-17
I did the chmod thing because I wanted to hide all the directories in / to everyone but the admin mode (gksudo nautilus) however I still wanted applications to run so I used the 722.

---

### Post by Mon on 2005-10-17
Sounds good. Unfortunatly... it doesn't work for me.
I did a "ls > .hidden" as root in /.
View hidden files is off in nautilus and everyone has reading rights on the .hidden file. What else can it be?

---

### Post by joelito on 2005-10-17
Ok wolki, I tried your methot, It worked better than mine...

All we need now is enough people to want this by default.

I mean, it would be cool to have that in dapper

---

### Post by bluck on 2005-10-17
[QUOTE=macgyver2]Very interesting howto.  I wonder, though, would it not be better to educate a new user rather than hide things from her or him?  It's not at all hard to go over the directory structure with someone after you install Linux on her or his computer.  If new users ask about not being able to write to certain directories, it would be far better to use that question as a jump-off to teach them about permissions.[/QUOTE]

good point about educating the user.  but i can see a use for this in situations like publicly available workstations, student labs, etc.

most people will stay honest if they arent tempted by something...
of course, this shouldnt be considered your entire security strategy, but a little abstraction goes a long way ;)

---

### Post by Brando569 on 2005-10-17
im prolly gonna have to do this for my dad, im trying to get him away from windows cuz he always get a lot of spyware and all that nasty stuff, plus hes an "explorer" like me and he could royally screw things up. another thing is he has an awesome gaming computer but all he does is  go on the internet (dont ask me to explain why he got it cuz idk :confused: ) it runs breezy with kde so fast its amazing. it would prolly be a pretty easy transition cuz he doesnt really do much in windows, he rarely ever installs anything or stuff liek that, so he doesnt need to know how to compile anything. ill teach him how to use synaptic though....

---

### Post by The Warlock on 2005-10-18
[QUOTE=bluck]good point about educating the user.  but i can see a use for this in situations like publicly available workstations, student labs, etc.

most people will stay honest if they arent tempted by something...
of course, this shouldnt be considered your entire security strategy, but a little abstraction goes a long way ;)[/QUOTE]

Um, if they don't have root, it's not like they could do anything with those folders anyway.

---

### Post by Wolki on 2005-10-19
[quote=mon]
Sounds good. Unfortunatly... it doesn't work for me.
I did a "ls > .hidden" as root in /.
View hidden files is off in nautilus and everyone has reading rights on the .hidden file. What else can it be?[/quote]

I just tried your method and it works fine if i become root with "sudo su". It's pretty smart actually, if I find a way to do it with sudo I'll add it to the howto.
You might have to refresh nautilus though.

[QUOTE=joelito]All we need now is enough people to want this by default.

I mean, it would be cool to have that in dapper[/QUOTE]

I'd agree, if the file selectro bug is fixed by then. If new directories and links are created like in my howto (you can also just leave relevant folders out of the .hidden file) they should be localized automatically, so that complicates the situation a little.

---

### Post by macgyver2 on 2005-10-19
[QUOTE=Wolki][QUOTE=joelito]
All we need now is enough people to want this by default.

I mean, it would be cool to have that in dapper[/QUOTE]
I'd agree, if the file selectro bug is fixed by then. If new directories and links are created like in my howto (you can also just leave relevant folders out of the .hidden file) they should be localized automatically, so that complicates the situation a little.[/QUOTE]
I disagree with making it like this by default.  However...how about talking to arnieboy about it.  This sounds like something that belongs (and would be easy to implement) in his Easy Ubuntu/Automatix script.

---

### Post by Wolki on 2005-10-19
The problem with that solution is that - unless such a script becomes included in default ubuntu - it is hard to discover for new users (those who are likely to want this functionality) and rather easy to discover for more experienced and forum-reading users (who often don't want such functionality). As such, it seems to make more sense to add this by default, and put a way to disable it into a Automatix/EasyUbuntu type script.

---

### Post by macgyver2 on 2005-10-19
[QUOTE=Wolki]The problem with that solution is that - unless such a script becomes included in default ubuntu - it is hard to discover for new users (those who are likely to want this functionality) and rather easy to discover for more experienced and forum-reading users (who often don't want such functionality). As such, it seems to make more sense to add this by default, and put a way to disable it into a Automatix/EasyUbuntu type script.[/QUOTE]
That's quite understandable, and good argument for why it should be default.

However, I'm not fond of the default idea because I see it possibly turning into a situation where I'd have to spend two or three hours *undoing* all of the beginner tweaks that make Linux not as...Linux-y.  You know, it starts with one thing, like this, but then before you know it you look at a new install and have to recheck the disk to make sure you really installed Ubuntu instead of Windows. :)

Maybe another solution could be to make this and other beginner tweaks selectable during the install.  Not individually as that would probably get to be a bit overwhelming.  But make it so a user can choose the "I'm new to Linux" option which would implement a bunch of stuff like this.

---

### Post by heimo on 2005-10-19
[quote=Wolki]
4. In that file, write the name of every file and directory on a new line. For reference, here's how mine looks like:
[/quote]

To automate this part a bit, you could probably just run
```
 ls -1 / | sudo tee /.hidden
```

---

### Post by Wolki on 2005-10-19
[QUOTE=heimo]To automate this part a bit, you could probably just run
```
 ls -1 / | sudo tee /.hidden
```[/QUOTE]

Cool, thanks! I'll update the howto.

Didn't know about tee. You learn something new every day... :)

[QUOTE=macgyver2]
However, I'm not fond of the default idea because I see it possibly turning into a situation where I'd have to spend two or three hours undoing all of the beginner tweaks that make Linux not as...Linux-y. You know, it starts with one thing, like this, but then before you know it you look at a new install and have to recheck the disk to make sure you really installed Ubuntu instead of Windows.[/QUOTE]

Well, that's what scripts are for. There's nothing wrong with activating advanced stuff with a script, be it graphical or shell. I'd say such a script should be available by default, and it should be mentioned in the relevant guides. Maybe even include in Automatix/EasyUbuntu. I still see no reason not to have this setup as default - those who want to disable it will find a way, but not everyone who would have an easier time with this enabled will find out how to do it.

---

### Post by joelito on 2005-10-19
[quote=macgyver2]
However, I'm not fond of the default idea because I see it possibly turning into a situation where I'd have to spend two or three hours undoing all of the beginner tweaks that make Linux not as...Linux-y.
[/quote]
Actually, I Think that to undo the directory hiding it would only be necessary to clear the /.hidden file, doesn't seem like a three hours job.

---

### Post by macgyver2 on 2005-10-20
[QUOTE=joelito]Actually, I Think that to undo the directory hiding it would only be necessary to clear the /.hidden file, doesn't seem like a three hours job.[/QUOTE]
Yes, I was referring to the case if one default beginner tweak turns into a hundred such default tweaks. :)  Wolki has good points though...such removals can be scripted just as additions are.  Maybe a script called HardUbuntu or something... :)

---

### Post by Mon on 2005-10-21
[QUOTE=Wolki]I just tried your method and it works fine if i become root with "sudo su". It's pretty smart actually, if I find a way to do it with sudo I'll add it to the howto.
You might have to refresh nautilus though.
[/QUOTE]

The next day i found out a "killall nautilus" did the trick. Maybe you could add it to your post though it seems no-one else has had this problem?

---

### Post by Wolki on 2005-10-21
[QUOTE=Mon]The next day i found out a "killall nautilus" did the trick. Maybe you could add it to your post though it seems no-one else has had this problem?[/QUOTE]

Probably an issue with Nautilus not updating. I've added some instructions to the howto, thanks!

---

### Post by Ptero-4 on 2005-10-26
Do konq hide the folders/files defined in the .hidden file or modded with the chmod 7** trick? or is this a Nautilus specific thing?

---

### Post by gladstone on 2008-05-11
Wish this worked in Thunar :(

[https://bugs.launchpad.net/thunar/+bug/110521](https://bugs.launchpad.net/thunar/+bug/110521)

---

