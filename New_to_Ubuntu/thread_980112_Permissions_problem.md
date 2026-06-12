---
title: "Permissions problem"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by victorcrane on 2008-11-12
Hi folks, I installed the zsnes emulator today and tried to install some snes roms I have had for a long while on a dvd. There are just over 1200 files in a folder totalling 1.6gb. Each rom file is zipped seperately. I copied the folder to my desktop no problem but when I try to unzip one or any of the files I get a warning telling me I do not have permission to do this. I get the same warning if I try to move the folder or even if I try to delete it. I've tried every way I know of doing anything at all with this folder but I can't do anything at all with it. 

Any advice? It's getting me a little frustrated now. 

:guitar:

Victor.

---

### Post by bodhi.zazen on 2008-11-12
Open nautilus as root and change the ownership / permissions as needed.

```
gksu nautilus
```

See also : [uhelp]community/FilePermissions[/uhelp]

---

### Post by victorcrane on 2008-11-14
Hi there, I don't fully understand what to do with nautilus, when I run it I get the root file browser come up, but none of my files are visible in it and I'm not entirely certain what I should be doing. I checked out the link to permissions and have followed to the letter the instructions given for the use of chmod etc but every time I try it i get a message telling there's no such file or directory, even though there very clearly is. I'm clearly doing something wrong. 

It's been a full week of assorted ubuntu disasters now, I do love it to bits but why in the name of god can't it just be a little more friendly to people like me who don't have the time or the skill to configure every tiny little thing. Even the majority of the applications I've added via the package manager don't work, I don't miss windows at all but I do miss the fact that when you install an application in windows it works, just like that, no stupid permissions, no endless errors you can't understand... I'm considered by most people I know as a 'whizz with computers' and this system baffles the hell out of me. No wonder I can't convince anyone else to try it. 

Ah that feels better. :)

---

### Post by Sirron on 2008-11-14
When you run nautilus as root like that, it opens to root's Home folder, not yours - this can be confusing as initially it looks like all your files are missing.

Navigate to your home folder, which will be /home/YOUR_USERNAME/ then open the Desktop folder.

You should see the folder you copied from the CD there, and then it's merely a matter of right clicking the folder, selecting Properties, then the Permissions tab, and changing them to grant your user unrestricted access.

Click the button at the bottom to Apply Permissions to Enclosed Files.

---

### Post by victorcrane on 2008-11-14
Thank you! Sorted. That's one less thing to annoy the hell out of me. 

Now all i need to do is work out why my processor occasionally cripples itself at 100% even when there's not a single program running, and why the hell my volume control only works 50% of the time, the rest of the time it doesn't respond and then ten minutes later it turns itself up or down. I'll end up using this as a frisbee. :)

---

