---
title: "Turn off trash and delete all trash from Ubuntu 15.04"
date: 2015-08-14
forum: New to Ubuntu
---

### Post by SImpleManMike on 2015-08-14
When I delete a file from USB it hides and and calls it trash. So now I want to disable trash completely from Ubuntu so that when I delete something anywhere it is gone forever.

OS: Ubuntu Mate 15.04


(If there is a more privacy oriented release of Ubuntu please suggest that instead)

---

### Post by howefield on 2015-08-14
Files > Edit > Preferences > Behaviour tab and check the option for "Include a Delete command that bypasses the Rubbish Bin" and you will have a Delete option on the right click context menu as well as the standard "Move to the Rubbish Bin"

Alternatively, Shift + Delete will bypass the rubbish bin.

"Gone forever" isn't so easy though.....

---

### Post by SImpleManMike on 2015-08-14
Thanks that helps for now but I still have my original problem. I didn't mean I want it gone forever I meant I want to turn off the trash function in Ubuntu completely so that it does not attempt to manage my choices for me.

---

### Post by monkeybrain20122 on 2015-08-14
> **SImpleManMike said:**
> Thanks that helps for now but I still have my original problem. I didn't mean I want it gone forever I meant I want to turn off the trash function in Ubuntu completely so that it does not attempt to manage my choices for me.

I can completely understand, I personally don't use trash, always use delete bypass but unfortunately there is no way to disable trash as far as I know. The bad news is upstream (gnome) seems to try to force people to use trash so that the delete bypass option is removed from gnome 3.16 [https://bugzilla.redhat.com/show_bug.cgi?id=1227946](https://bugzilla.redhat.com/show_bug.cgi?id=1227946) Ubuntu modifies upstream's nautilus I hope that it will be restored in Ubuntu next, or if not hopefully there will be a ppa that does (or perhaps switch to a different file manager like nemo, but don't know how well it plays with Unity)

---

### Post by howefield on 2015-08-14
There are workarounds but not sure I'd recommend them, a search with your favourite engine should reveal what you want though.

---

### Post by The Cog on 2015-08-15
Thunar (the default file manager for Xubuntu) contains the menu options "Move to Wastebasket" and "Delete" next to each other. 
However, the Delete key still moves to the wastebasket, and shift-delete deletes and I see no option to change this.

---

### Post by SImpleManMike on 2015-08-15
Thanks guys I guess I have found something with Ubuntu I don't like so now it is time to go to the other distros forums to ask if it is solved using another distro.

---

### Post by oldos2er on 2015-08-15
Barring version changes, Mate is going to behave the same regardless of which distro you run. You can "disable" Trash completely by using **rm** in terminal, or use a different file manager as The Cog suggested.

---

### Post by buzzingrobot on 2015-08-16
Trash is a hidden directory. What happens when you "Trash" something is that it's moved to that directory.  What happens when you empty the trash is that the files in that directory are removed. As far as I know, every OS implements trash that way.

Adding the "Delete" option bypasses Trash and just removes the file, as if you'd used "rm" in a terminal.

Removal of a file from the filesystem makes that space available for re-use, but it does not delete the actual data on the drive that represents that file. That data remains until it's overwritten.

Setting up a cron job to manually remove files in the Trash directory, say, every hour, is certainly doable.

---

### Post by vasa1 on 2015-08-16
> **SImpleManMike said:**
> Thanks guys I guess I have found something with Ubuntu I don't like so now it is time to go to the other distros forums to ask if it is solved using another distro.I'm not sure it has so much to do with the distro as it has to do with the file manager. Most self-respecting file managers provide "Trash". I don't know of any "minimal" file manager.

---

### Post by mc4man on 2015-08-16
> **SImpleManMike said:**
> When I delete a file from USB it hides and and calls it trash. So now I want to disable trash completely from Ubuntu s_o that when I delete something anywhere it is gone forever._

OS: Ubuntu Mate 15.04


(If there is a more privacy oriented release of Ubuntu please suggest that instead)

> **SImpleManMike said:**
> Thanks that helps for now but I still have my original problem. _I didn't mean I want it gone forever_ I meant I want to turn off the trash function in Ubuntu completely so that it does not attempt to manage my choices for me.
Which is it?
removing the context menu option for trash likely can only be done in source *if* that's your "orig" issue. 
(or find a file manager that doesn't use trash at all

---

### Post by mc4man on 2015-08-17
> **monkeybrain20122 said:**
> I can completely understand, I personally don't use trash, always use delete bypass but unfortunately there is no way to disable trash as far as I know. The bad news is upstream (gnome) seems to try to force people to use trash so that the delete bypass option is removed from gnome 3.16 [https://bugzilla.redhat.com/show_bug.cgi?id=1227946](https://bugzilla.redhat.com/show_bug.cgi?id=1227946) Ubuntu modifies upstream's nautilus I hope that it will be restored in Ubuntu next, or if not hopefully there will be a ppa that does (or perhaps switch to a different file manager like nemo, but don't know how well it plays with Unity)
It would be unlikely that Ubuntu changes this when or if it moves to 3.16, I'd be ok if they stuck with 3.14 for 16.04 though that's also unlikely.

While adding back a context menu option would be fairly simple, getting it to do anything not so as the delete command is now 'move to trash' 
don't have 3.16, is there a 'permanently delete' option somewhere?

---

### Post by monkeybrain20122 on 2015-08-17
> **mc4man said:**
> 
don't have 3.16, is there a 'permanently delete' option somewhere?

Not that I can find. But see comment 8 [https://bugzilla.redhat.com/show_bug.cgi?id=1227946](https://bugzilla.redhat.com/show_bug.cgi?id=1227946)

---

### Post by MiSt77 on 2015-10-21
[SIZE=2][FONT=arial][COLOR=#111111]I too am one of those who have been bugged by this problem for a number of years ... unsatisfied with the existing proposals, I've recently taken the time to investigate a solution myself.
[/COLOR]
[COLOR=#111111]Starting with the premise that I want the Trash to be gone system-wide, I've found that -- for the time being -- the only real solution is to create a custom-compiled version of **libgio** (» [GIO]("http://en.wikipedia.org/wiki/GIO_(software)")) which is modified to call **g_file_delete()** every time an application calls **g_file_trash()**.
[/COLOR]
[COLOR=#111111]For all technology savvy users interested in this solution: I've just recently posted a step-by-step guide on *The IT community*:[/COLOR]
[/FONT][/SIZE][INDENT][SIZE=2][FONT=arial][COLOR=#111111][URL="http://www.theitcommunity.com/wiki/Globally_disable_GNOME%27s_Trash_in_Debian-based_distributions"]
Globally disable GNOME's Trash in Debian-based distributions[/URL]

[/COLOR][/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=arial][COLOR=#111111]I hope this is of (some) help to those who hate the Trash with the same passion as I do ...[/COLOR][/FONT][/SIZE]

---

