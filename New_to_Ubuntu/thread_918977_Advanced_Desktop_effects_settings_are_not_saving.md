---
title: "Advanced Desktop effects settings are not saving"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by ninch on 2008-09-13
So I go to system->advanced desktop effects settings and I configure the settings to how I want it (compiz fusion). I first made a new profile and then checked all the effects I wanted there. It is the default profile, so whenever I log in, the computer always uses this profile.

However, sometimes when I turn off my computer then turn it back on, the profile's settings get erased. I then went to system->preferences->apearence and I click the tab "visual effects." Normally when ubuntu is using the compiz fusion, none of the the three options in "visual effects" are checked. However, sometimes when I turn off then turn on my computer, the option "none" is checked. I then have to go to system->advanced desktop effects and settings and I have to start over by checking all the options I want for my computer.

I would like to find out a way to save the options, so that everytime I turn off and turn on the computer, the options save. Plus, my screenlets get erased as well. 

This only happens sometimes, by the way. Any help is appreciated.
I am using ubuntu 8.04 (hardy)
Thanks.

---

### Post by silvagroup on 2008-09-13
I have a similar problem.

With my system when I log out and back in my emerald is not running. I have no windows decorations.
Also my Avant windows manager bar does not load up.

I have to reload the Window Manager using the fusion icon, to make it easy, and everything loads and works great.

I tried using system session preferences setting Emerald and Avant as startup items, with no luck. I tried saving current sessions with everything working and I have selected save session to no avail.

Any help would be greatly appreciated also. 

Thanks in advance.

---

### Post by ninch on 2008-09-14
I just fixed my awn and my emerald too, but my compizfusion effects still are not saving. Try this:

Go to: system->preferences->sessions

then you will see a bunch of sessions that have commands.
click "add" and for your avant window navigator (awn) type in as name "Awn" and for the command type in "avant-window-navigator" (without quotes). This should make it start up automatically.

For emerald, click "add" and for name type in emerald, and for the command type in: "emerald --replace" (without quotes).

Hope this helps
Ninch

EDIT:
oh, i think you already tried this..
oh well ;p

---

### Post by silvagroup on 2008-09-15
ninch thanks,but I already have those set up in sessions and when I boot up I have no borders from emerald and avant window manager won't load until I do a reload window manager from fusion icon.

Somethings broken some where but I am not sure where or where to look at this point.
Must be some gnome config issue. I would like to get it resolved I have several installs I am going to be doing for some friends which loved my system. They are moving over from Windows but with this issue it would look just be a layer of frustration for them that would drive them back to Windows so I've been putting them off till I can get this resolved on my system.

Didn't think this would be such a huge stumper. I really thought I would be an easy fix.

Thanks you.

---

### Post by MegaJim on 2008-09-15
You can try changing from the gconf backend to flat-file config. 

This used to happen to me after upgrading to 8.04, but using flat-file fixed it.

---

### Post by silvagroup on 2008-09-15
MegaJim, could you be so kind as to explain that a little more.
I know there is a .gconf on my $Home and there are some kind of config files there but that's as far as my knowledge goes and as for flat file I don't know what that isat all.
Pleae excuse the ignorance.

---

### Post by MegaJim on 2008-09-15
Sorry i missed your reply.

Open up the compiz config settings manager as usual, go to the preferences section and there will be a dropdown labelled "backend".  You can choose flat-file config from there.

---

### Post by silvagroup on 2008-09-15
MegaJim tired your suggestion and still have the exact same problem, with an added layer. Using flat-file messes up the emerald theme. Not sure what the theme is, looks like a mix of one or more themes, but it's not the emarld theme it should be.

Thanks for the try.

---

### Post by ft23002 on 2008-10-02
Hello,

Install the fusion icon:
Open Synaptic Package manager
Click search and type: fusion-icon
Highlight, right click and mark for install
Click aplly check mark, and follow instructions to complete the install.

Once installed:
Open Sessions
Remove emerald from start-up (if command is listed/used) It is not needed when using the fusion icon as start-up method!

Add:

Name: Fusion Icon
Command: fusion-icon
Comment: (Whatever you like)

This will start fusion & emerald (if used) at login & automatically place icon in taskbar.

With the fusion icon in the taskbar, right click and make sure the "select window manager" is compiz & if emerald is used make sure it is selected in "select window decorator".

Also as described in above post#5 use the Flatfile backend to save settings & profiles in compiz fusion when the default backend doesn't work.

Open CompizConfig Settings Manager and click "Preferences".
Once changed to Flatfile it will revert all settings to defualt.
Recommend creating a new profile right after changing the backend to flatfile. Click the plus sign next to the profile name, enter a name for the new profile and click Add.Then change/customize all the compiz settings you wish to use, then save/export the profile. If you wish to have other profiles; create a new profile, customize and then save/export.

When restoring a profile, click Import, go to the Folder the profiles are kept and in the bottom right where it says "Profiles(*.profile)", click and select "all" to show the saved profiles. Double click the profile to Import or highlight it and click Open. This will load the profile settings into Compiz.

---

### Post by silvagroup on 2008-10-06
ft23002,
Thanks, tried flat file again but emerald doesn't work when I switch to flat file.
I can select different themes and nothing changes. Reloaded window manager and nothing changes.

Also with flat file my Avant Window manager icons also disappear, I have the bar but no icons.

When I switch back to gconf everything works again.

I also have some screenlets on my desktop. When I log in I notice that a couple give me a message about the screenlets wanting to take control of settings I select no for both. At this point my screenlets are not all properly sized and Avant has not loaded yet. 
I then go to my fusion icon reload window manager and my screenlets go to proper size and Avant loads and icons appear.

Thank you.

---

### Post by ft23002 on 2008-10-07
If your now using the fusion icon & have it sessions/startup programs, you may now be OK with gconf...dunno

I'm by no means a guru and only knew about the fusion icon and running it in startup to get settings to save and have compiz & emerald automatically load at startup.
As far as the backend, think I was having to use flatfile prior to the fusion icon to restore profiles. Since the icon, have not tried to save any profiles because settings are being retained at startup now.

Have screenlets too and have had problems with them as well. If they continue to not operate the way they should, I had to reset and unselect the run at startup for each screenlet in screenlets manager and remove all the screenlets entries (except "screenlets-manager/screenlets-daemon", which is the icon in taskbar) from sessions/startup programs & current session. Then start over with setting them up and placing them. ...Errggg

There is a newer version of screenlets that isn't included in ubuntu updates, it can be downloaded at gnomelook. Version 0.1.2
Please read info on how to update from previous versions if you don't have 0.1.2 and wish to use it.

Screenlets homepage:
[http://www.screenlets.org/index.php/Home]("http://www.screenlets.org/index.php/Home")

Can't comment about Avant, don't have it here.

Since adding the fusion-icon to startup...

Have you tried to save/restore profiles with the gconf backend?

Are compiz & emerald settings being retained after restarts/startups with the gconf backend?

Good Luck

---

### Post by Therion on 2008-10-07
I think what's happening here is... If you go into CCSM and modify things there; say you configure the Cube, adjust some open/close animations and such, you "overwrite" (for lack a better word) or clear, the radio button for "Advanced" effects in lieu of what you've just turned on via CCSM.

Make your adjustments in CCSM and ignore the settings buttons in System/Preferences/Appearance or simply use the default set of effects that come with "Advanced" preset button.  

In short, do one or do the other; but not both.

---

### Post by bopomofo on 2008-10-12
I too have had enormous problems with backing up my settings in Compiz, which I only contemplated doing today. But no luck, as this thread seems to attest. I had to remember my settings and **manually** restore them probably 7 times this morning while trying to export them and test the export. I've given up even trying to follow the advice in this thread. Enormously frustrating. I'm not going to touch the Profile settings again... lesson learned.:mad:

For the record, I had similarly bad experiences with trying to save the settings on AWN, although at least export/import actually works. It's just a UI problem.

One thing a program should never lose your settings. NEVER. Compiz is not playing nice here...

---

### Post by bopomofo on 2008-10-12
> **Therion said:**
> 

Make your adjustments in CCSM and ignore the settings buttons in System/Preferences/Appearance or simply use the default set of effects that come with "Advanced" preset button.  

In short, do one or do the other; but not both.


This just really seems like a Bug. I got into this mess when I wanted to try toggling Compiz on and off.


LESSON: if you have customized your Compiz settings, DON'T TOUCH the Appearance:Visual Effects options.:mad:


But how can this not be a bug? :confused:


But this experience did make me realize how bad the Default Compiz settings are. :)

---

### Post by bopomofo on 2008-10-12
> **bopomofo said:**
> This just really seems like a Bug. I got into this mess when I wanted to try toggling Compiz on and off.


Of course I can use the Fusion icon to do this, but I had become unwittingly curious about the Appearance:Visual Effects tab. :(

---

### Post by silvagroup on 2008-10-15
Here may the answer to this problem, just updated my system and after a reboot I got this error at system startup:
"User $Home/.dmrc file is being ignored. This prevents the default session and languages from being saved. File should be owned by user and have 644 permissions. User $Home directory must be owned by user and not writable by others."

I know that states that there is permissions problem with my home directory and that's all. I also gather I have to change my permissions to 644.

This is a fresh install of 8.04 so this has been going on since the get go (I a bug, maybe, abd that's why the new kernel) anyway not sure where to go from here I guess I'll search for permissions on other threads to get this sorted out.

If anyone has any ideas it would be greatly appreciated.

OK looks the solution maybe here: [URL="http://ubuntuforums.org/showthread.php?t=940535&highlight=chmod+644"]http:
//ubuntuforums.org/showthread.php?t=940535&highlight=chmod+644[/URL]

Well this got rid of the error message at login but still my session settings are not being saved !!!!!

Just wondering if this is more system related than compiz real;etd. I am going to cahnge to metacity and and gtk and see what happens.

---

### Post by silvagroup on 2008-10-15
This is does no appear to be a compiz problem, but some system problem.
Changed to metacity and gtk and session setting are fully saved, some weird stuff going on here. Not sure where to dg and what to do.

It's not a show stopper but sure is an anoyance and can be seen as a deterant for new users if they have to try and deal with this.

---

### Post by silvagroup on 2008-10-16
Be extremely careful withe the permissions after experimenting with it I still can't get sessions save to work correctly with everything and I spent a whole day trying to get my system working after several things got messed up in the process and almost lost the system.

---

### Post by Tbagged on 2008-10-28
Here's the fix, it's a permissions problem, open up a root session of Nautilus:
$ sudo nautilus
 

1.  in /home/[username]/ 
2.  hit Ctrl+H to view the hidden files
3.  open the .config folder
4.  right click on properties
5.  click on the permissions tab
6.  change the owner to whatever your log on name is.

---

### Post by silvagroup on 2008-10-28
Tbagged thanks already did that after finally fixingthe system and still have the same problems.
It's a mnir problem, whatever it is it's not that big a deal since I rarely have to reboot and if I do need to reboot I just close out ecerything do reload of compiz fusion when I am back in the system and I am up and running in less than one minute.
But if anybody has found a solution it would be good for those less Linux oriented, not that I am that much of an expert, duh, or I wouldn't have this small problem.

---

