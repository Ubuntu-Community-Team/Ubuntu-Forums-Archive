---
title: "Missing new packages from &quot;Installed&quot; section of &quot;Ubuntu Software&quot; after update"
date: 2018-12-16
forum: New to Ubuntu
---

### Post by kamsien on 2018-12-16
**Disclaimer:** Totally new to Ubuntu (less than a month). I am not totally ignorant, but I believe in the K.I.S.S. principle, so I would appreciate to keep answers as basic as possible.  I've been sifting through the forums and the internet **(2 hours) **in general but I have not come through this specific issue.  I did my best to ensure this issue is not a repeat, but I apologize if I missed it. As I said, it's been 2 hours. I believe I'm using the correct terminology, but if not please do correct me. I do want to learn everything there is to know.

**Ubuntu 18.04.1 LTS 64-bit.** **GNOME 3.28.2**  All packages and software up-to-date. I don't believe hardware is an issue here.

I'll explain my problem in chronological form but the basic issue is **after my morning update of Ubuntu my packages** do show in "Show Applications" but **are not showing in "Installed"** part of "Ubuntu Software".

1. This morning I had NO KNOWN ISSUES.
2. Installed Synaptic through "Ubuntu Software"
3. Synaptic showed updates available to Ubuntu, which I believe were directly related to the "Ubuntu Software" package updater (Ubuntu Software Center), and installed such updates.
4. Installed Xarchive and ClamTK.  (Originally only Xarchive through Synaptic, then when I noticed the issue in (5) I uninstalled through Synaptic, and installed both packages through "Ubuntu Software".)
5. Went to "Ubuntu Software" to group software in "Show Applications" into folders of my liking. "Installed" under "Ubuntu Software" does not show anything I installed after Synoptic.  However, all (Xarchive, ClamTK) is showing under "Show Applications".  The applications themselves work perfectly fine, I have tried them; they're just not showing up under "Installed" in "Ubuntu Software".  Both packages show in Synaptic.

I believe the update I did through Synaptic of the Ubuntu Software Center went awry.
My guess is there is a file somewhere that is not being updated with the new installed software, but even if I manually updated such file, I would have to do just that forever in the future, so I don't believe that is a solution.
**My next guess is that I need to uninstall and/or re-install this morning update of Ubuntu Software Center so that a good install will start to show up my new installations.**

And hence...How do I go about making sure new software does show up in the Ubuntu Software Center so that I can group things in folders and uninstall through it if I choose to do so?

---

### Post by Frogs Hair on 2018-12-16
Hello:

AFIK synaptic and Ubuntu Software don't  have a shared history, but I don't see this as a problem as long as the installed applications show in the menu or dash depending on the Ubuntu flavor installed. I have many applications installed via synaptic not listed in the software center. If you want see a list of_ everything _installed anytime run  the following command in the terminal. Copy it in the text editor and save for later use. For package removal I use synaptic which does list all my installed programs . 

> [QUOTE][COLOR=#000000]I can group things in folders and uninstall through it if I choose to do so?[/COLOR]
[/QUOTE]

Linux programs and their dependencies may be installed in various locations unlike windows program files. More than one application at a time can be removed via synaptic or the terminal. 

```
sudo dpkg --get-selections
```

---

### Post by kamsien on 2018-12-16
Thank you for the reply and the info.  It's useful and great to know, but I believe I still have a problem.

I did mention I re-installed both missing packages through Software Center, making me think they should show up there. ClamTK i strictly installed via the Software Center (not Synaptic) and it didn't show up either.  Plus my second (and last) installation of Xarchiver was also down through the Software Center.

I would think if I install through the Software Center that it should show up in the "Installed" section, should it not?  Plus this issue still stops me from grouping software in folders under "Show Applications".

---

### Post by Frogs Hair on 2018-12-16
Linux programs and dependencies are installed in various locations unlike windows which offers program files or a location you specify. Removing a number of programs is possible via synaptic or the terminal . I have not used clamtk in along time so I'd have to experiment. Xarchiver seems to work fine here but does not show up in Ubuntu Software.

---

### Post by kamsien on 2018-12-16
> **Frogs Hair said:**
> Xarchiver seems to work fine here but does not show up in Ubuntu Software.

Did I understand this right?: you have installed Xarchiver through Ubuntu Software and it didn't show up in the "Installed" section for you?  (Just like me)

If this is the case, I find counter-intuitive that an app that you installed through Ubuntu Software won't show up in the "Installed" section of the same "Ubuntu Software".  Is this normal?

But past all that and assuming I have a problem with installations (which I honestly would rather resolve)...I can live with the fact that it doesn't show up in there....so long as I can organize my software in folders in the "Show Applications" part of GNOME. Is there a way to do this that is not in the "Installed" section of the "Ubuntu Software"?  That's the only way I know of so far...

---

### Post by kamsien on 2018-12-17
**Update**:  I went ahead and uninstalled both packages, then tried installing again through the Ubuntu Software.  I found if **immediately after** installation I go to the "Installed" section, the package shows up in the section just **one time and one time only**. This gave me the opportunity to while it's showing up to put the package into the folder of my liking for when I go to "Installed Applications".  However, it is obvious to me I have something wrong since it only shows that one time and if I lose the boat I never see it again in the "Installed " section.

Something else I found through trial and error prior to all this is that if I do a search inside "Ubuntu Software" the package shows with it's brief description and the check-marked installed icon in the corner.  Meaning "Ubuntu Software" knows the packages are there and installed, but it's not showing them in its "Installed" section, except for that exclusive moment right after installation.

Therefore, I've found a way to solve the grouping of software, **so long as I do it IMMEDIATELY after installing**.  However, there is a bug here for me still for what I can tell with new software not showing in the "Installed" section.

And here is the kicker:  Once I've put the package into the folder of my liking...then it shows permanently in the "Installed" section with the greyed name of the folder in it.

I think if I pay close attention I can hear that "Ubuntu Software" center just laughing...

---

### Post by kamsien on 2018-12-18
**Final update:** (or so I hope). I'm adding this for those who might run into the same issue, to hopefully make their life easier than my experience. 

After trying out ClamTK I decided it wasn't worth it, therefore I uninstalled via Synaptic, and didn't retry anything with this package.
Prior to this I had mentioned in a prior post, seeing Xarchiver through "Ubuntu Software" for an instance (I uninstalled and reinstall several times to make sure I could recreate this behavior), and was able to group it into a folder, therefore took care of that part.
As to fixing my "Ubuntu Software" (which I discovered is actually called gnome-software as per its package name), I went to Synaptic with this info.
In Synaptic, it gives you the option to "Mark for reinstallation" any package, and I went ahead and did this for gnome-software. After that I did a trial install of Chromium, and it did show up in the "Installed" section, therefore I am assuming I have fixed my botched update of "Ubuntu Software" due to the results.

Final thought: It's discouraging to hear that not all software will show up in gnome-software "Installed" section from the words of the kind moderator who took the time to reply to my post.  Especially software that you install through "Ubuntu Software" Center. I'm not abandoning Ubuntu, but I wish this wasn't an issue since it prohibits you (until I discover some other way) to group software in folders, if it doesn't show up in the "Installed" section.

---

### Post by oldrocker99 on 2018-12-18
Back when I started with Ubuntu 8.4, Synaptic was pre-installed. It became my "software center."  It is very useful if, with synaptic not running, you do this:
```
sudo apt install apt-xapian-index
sudo update-apt-xapian-index -vf
```
This will put a little extra window at the top, which will filter searches. Search, using the Search button for "strategy," then enter "real" in the small window. This will list, for example, all the real time strategy games.

Thee idea is to search for a type of program, say an "editor," then filter with "video." That gets you, obviously, video editors. Filter with "text," text editors; "audio," etc.

You can also do this:
```
apt search editor | grep video
```
Replace, of course, whatever you're looking for. Note that both methods do the same things.

---

### Post by Frogs Hair on 2018-12-19
After reboot Xarchiver is showing in Ubuntu Software.

---

### Post by kamsien on 2018-12-20
Thanks! Great info to know Oldrocker. It will certainly make things easier.

---

### Post by kamsien on 2018-12-20
As I mentioned Frogs Hair...there was something wrong with the installation of that update for gnome-software, hence me asking for help.  I'm new to Ubuntu, but I'm most certainly technically inclined therefore I had no doubt there was a problem. The reinstall via synaptic of the software worked and I have had no issues since.  Thanks for your replies though.

**Alternative: **This is for others like me, new to Ubuntu, that might run into these posts, I found an alternate solution to the folders organization...I did some digging and installed Gnome shell extensions which is a must IMO, although some not-inclined people might see it daunting at first.  One of the extensions is called **Appfolders Management Extension** and it gives you the ability to organize any application from the applications view (a.k.a. "Show Applications") into folders and categories also.  Therefore more than likely from now on I will never use the "Installed" section of gnome-software since I can just organize them straight from the apps view.

P.S. I also recommend Dash To Panel extension.

---

