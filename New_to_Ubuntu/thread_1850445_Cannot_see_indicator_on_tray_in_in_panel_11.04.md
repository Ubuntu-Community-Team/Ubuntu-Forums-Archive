---
title: "Cannot see indicator on tray in in panel 11.04"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Paddy Landau on 2011-09-26
I'm sure this must have been asked before, but I must be putting in the wrong search terms.

I am experimenting with 11.04.

If I start TrueCrypt in 10.04 (my usual desktop), it puts an indicator in the panel so that I can perform various tasks.

Now, in 11.04, there is no indicator in the panel, so I cannot do anything in TrueCrypt. If I try to start TrueCrypt again, it tells me (correctly) that it is already running.

If I try to right-click on the panel so that I can add an indicator, nothing happens.

How can I get the indicator back in the panel?

---

### Post by wildmanne39 on 2011-09-26
Hi, the panel is locked by default, there are some applets that can be added but I am not sure that is one of them, here is a link for the ones available.
[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
Does it not show up in the launcher on the left of the screen so you can click on it?
Thank you

---

### Post by An Sanct on 2011-09-26
I installed TC 7.1 right now in my test Oneiric (11.10) Virtual machine. There is no indicator for me neither ... so I googled up [a probable solution]("http://askubuntu.com/questions/35076/how-do-i-whitelist-truecrypt-to-work-under-unity") for you.

Still, it has to be tested, I have not done that part yet.

-------------
Edit:

Well, in Oneiric it seems slightly more confusing, since there is no *gconf-editor* ... like there also is no *synaptic* (_What are they thinking ?!?!?!?!?!?_) so you have to install them via software center. But I cannot find those settings...

---

### Post by Paddy Landau on 2011-09-26
Thanks for the info. Unfortunately, TrueCrypt is not listed (but I'm glad to see DropBox listed). Those are not the only ones I use where I need access; for example, I notice with dismay that Skype is not listed.

TrueCrypt shows in the launcher once launched, but as soon as I close the window, it disappears from there. It expects further commands to come from the indicator (you can also open the main window from there). But you cannot open it by running the command again.

Most inconvenient! This is no good if it makes its way into the next LTS version. What must newcomers to Ubuntu think? What a backward step!

May I raise this as a bug, or has someone found a solution?

---

### Post by Paddy Landau on 2011-09-26
@An Sanct: I missed your post. I am signing off for tonight (it's late here). I'll try your solution tomorrow and let you know whether or not it works.

---

### Post by An Sanct on 2011-09-26
> **wildmanne39 said:**
> Hi, the panel is locked by default, there are some applets that can be added but I am not sure that is one of them, here is a link for the ones available.
[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
Does it not show up in the launcher on the left of the screen so you can click on it?
Thank you

It is in the launcher, is clickable, but has only the most common commands and not the wished menu.

---

### Post by Krytarik on 2011-09-26
Just something to give you at hand for tomorrow: It's about "dconf-editor", not "gconf-editor", as also mentioned in those thread. Therefore, make sure the package "dconf-tools" is installed.

And yes, it's really awkward that they even removed "gconf-editor" from the default installation of Oneiric! Also given the fact that they just removed Synaptic, another very unpopular decision. #-o

And reg. the need to specifically 'whitelist' tray icons, by that way Canonical is trying to force the devs of the concerning apps to build indicators instead. Well, it's more than questionable who is in the stronger position here, given that Ubuntu is not the the only Linux distro out there, and Unity is not the only available UI. ;-)

Greetings.

---

### Post by Paddy Landau on 2011-09-27
Well, thank you all for your ideas. I can mark this solved.

For other people reading this thread, the easiest way is this:


[LIST=1]
[*]Open a terminal and enter the command:```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```
[*]Log out and in again.
[/LIST]

That command whitelists everything, so you don't have to add each item individually.

Why in heck Canonical decided to blacklist by default, goodness knows! I think I should raise this as a bug.

---

### Post by An Sanct on 2011-09-28
Definitely .. well it is more of a "paper cut" ... a *BIG* one, that is...

---

### Post by Paddy Landau on 2011-09-28
> **An Sanct said:**
> Definitely .. well it is more of a "paper cut" ... a *BIG* one, that is...
I'd forgotten about paper cuts. Where do we log those?

---

### Post by An Sanct on 2011-09-28
> **Paddy Landau said:**
> I'd forgotten about paper cuts. Where do we log those?
[https://launchpad.net/hundredpapercuts](https://launchpad.net/hundredpapercuts) shold be the place to look :)

Altho, my guess would be, that they re-organize bug reports and put them, where they should be...

---

### Post by Paddy Landau on 2011-09-28
It has already been reported as a [Unity bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/779210").

Unbelievably, it has been marked as invalid, with the statement that the systray support will be removed from 11.10 or 12.04!

That means that the next LTS will be released with a known, deliberate major bug!

What will happen when people try to use programs whose programmers are interested in supporting Linux but not specifically Ubuntu?

I will ask this question on another forum and then decide what to do. Perhaps raise it as a bug and get people to add their names.

---

### Post by An Sanct on 2011-09-29
Ubuntu became an unknown "wild" animal for me, with versions after 10.10 ... :)

If you raise this as a "supportable" issue, please post here or notify me, I will co-sign.

---

