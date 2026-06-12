---
title: "gnome-panel jammed"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ofb on 2008-06-20
Had a crash and gnome-panel has been badly jammed up since. It takes several minutes to get any reaction from a selection. Other apps are not affected, and I can't see the source of the slowdown in System Monitor. Have tried reinstalling gnome-panel via Synaptic, but no difference.

Lacking a better idea I'm considering reinstalling Heron. I have a separate Home partition, so figuring formatting root and going fresh.

Is there a better way? Like an overwrite install that simply corrects corrupted files?

---

### Post by sisco311 on 2008-06-20
Maybe the configuration files of the panel are corrupted.
Try to rename the config directory(~/.gconf/apps/panel) and let the system to set the default config files.

After the directory is renamed type:
```
killall gnome-panel
```in a terminal. press Alt+F2 and type:
```
gnome-panel
```Note: this will restore (hopefully) the default panels. If this doesn't work just rename the directory[FONT=monospace] to [/FONT]~/.gconf/apps/panel.

---

### Post by ofb on 2008-06-20
No luck. 

Renamed as /panelBAK. Running 'killall gnome-panel' refreshed the existing panel. Alt+F2 'gnome-panel' did nothing visible. No new /panel directory was created. Rebooted and waited about ten minutes for any panel to show up. Having none, I checked and found there was a new /panel dir now, deleted that and renamed the old one back.

Rebooted, and back to my original jammed up panel.

---

### Post by AndThenWhat on 2008-06-20
I just found a website for fixing messed up gnome-panel's.  You can check it out as I really don't know if it applies to the problem you are having:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by iaculallad on 2008-06-20
On your terminal, Try this:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/panel
sudo pkill gnome-panel
```

---

### Post by ofb on 2008-06-21
iaculallad, i think you meant 'sudo rm -rf ~/.gconf/apps/panel'? That would be the same as AndThenWhat's link. It is for restoring the default panel configuration.

(People reading along are advised to back up their current ~/.gconf/apps/panel if they want the option of returning to it after that procedure.)

Okay, have done this, which is essentially the same as sisco311's advice, with the same result: no panels on reboot. After five minutes i restored my backup, & rebooted back to the jammed version. Opening the first menu takes seven minutes.

So now we know it has nothing to do with user config. Is there a way to kill the panel and then start it again in terminal? If we can see the output during that seven minutes, we may have the culprit.

---

### Post by iaculallad on 2008-06-21
> **ofb said:**
> iaculallad, i think you meant 'sudo rm -rf ~/.gconf/apps/panel'? That would be the same as AndThenWhat's link. It is for restoring the default panel configuration.

(People reading along are advised to back up their current ~/.gconf/apps/panel if they want the option of returning to it after that procedure.)

Okay, have done this, which is essentially the same as sisco311's advice, with the same result: no panels on reboot. After five minutes i restored my backup, & rebooted back to the jammed version. Opening the first menu takes seven minutes.

So now we know it has nothing to do with user config. Is there a way to kill the panel and then start it again in terminal? If we can see the output during that seven minutes, we may have the culprit.

My mistake, that should be **sudo rm -rf ~/.gconf/apps/panel**. Another way to do a reset is to create another user, logout from your current user account and log back in using the newly created account. Copy the values of ~/.gconf/apps/panel to your account, overwritting it.

---

### Post by ofb on 2008-06-21
Gnome-panel works in the new account. With that configuration imported to my account, it took about ten minutes before the panels appeared. Reverting to original panel config, I get the panel on login but there's a seven minute delay before it recognizes the first click.

So the problem is not in that directory, but it is on the user side, and reinstalling without wiping /home probably won't fix what's wrong. Sound right?

---

### Post by ofb on 2008-06-22
There are other consistent delays when I try to do Gnome related things. Here are some terminal outputs.

```

o@redfish:~$ opera  -notrayicon -nomail
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

```

Those lines are normal for Opera on start-up. Now ctrl-click an image to Save As,

```

(<unknown>:6884): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/o/.recently-used.xbel', but the parser failed: Error reading file '/home/o/.recently-used.xbel': Is a directory.

(<unknown>:6884): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

```

There is a consistent 25 second jam before the Gnome Save dialog comes up. Now save the image and you get,

```

(<unknown>:6884): Gtk-WARNING **: Attempting to store changes into `/home/o/.recently-used.xbel', but failed: Failed to rename file '/home/o/.recently-used.xbel.V3BVCU' to '/home/o/.recently-used.xbel': g_rename() failed: Is a directory

```

Note that the operation succeeds, we simply have a jammed computer during it. This happens for every Save in Opera -- images, PDF, whatever.

Similar, there is a 50 second jam when we select Save for the first time for a Gedit document. In terminal,

```

o@redfish:~$ gedit

(gedit:7024): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/o/.recently-used.xbel', but the parser failed: Error reading file '/home/o/.recently-used.xbel': Is a directory.

(gedit:7024): GLib-CRITICAL **: g_bookmark_file_get_size: assertion `bookmark != NULL' failed

```

Those lines are not normal. Gedit should simply open after the command.

Enter some text and hit Save, get a 50 sec delay, get the Save dialog, hit Save.

```

sys:1: GtkWarning: Attempting to store changes into `/home/o/.recently-used.xbel', but failed: Failed to rename file '/home/o/.recently-used.xbel.XPTWCU' to '/home/o/.recently-used.xbel': g_rename() failed: Is a directory

```

Close gedit,

```

sys:1: GtkWarning: Attempting to store changes into `/home/o/.recently-used.xbel', but failed: Failed to rename file '/home/o/.recently-used.xbel.06R7CU' to '/home/o/.recently-used.xbel': g_rename() failed: Is a directory

```

---

### Post by ofb on 2008-06-22
Well, poop. That's all unrelated. It's just noise from .recently-used.xbel being made a directory to get rid of Places > Recent Documents. Restore that to default and I still have all the Gnome jams and no related terminal outputs to tell me why.

Is there another way to find out what the machine is hanging on?

---

### Post by ofb on 2008-06-23
Reinstalled, formatting / but not /home. First boot, everything was fine. Got Nvidia & resolution sorted, and did the next restart. Still fine. Did the major update, the ensuing reboot, and I've got the Gnome-jam problem again. Takes seven minutes to get the first menu open.

---

### Post by ofb on 2008-06-24
I went Bowman on it. Reinstalled, this time formatting /, and removing all the '.' files and directories from /home except for recognizeable apps that I wanted to preserve settings for, like Bluefish, Gimp, Opera, etc. The idea was to remove everything that's more of a system configuration file.

All the removed files were copied to a BAK directory just in case, then deleted from their place in /home. In theory a copy preserves ownership, while a move does not. 

Noticed over a gig of tracker db index files, even though I had stopped & uninstalled trackerd pretty early in original Heron install. Also over a gig of thumbs. I deleted those rather than copy to BAK. Took a while even in terminal -- 'argument too long'. Had to do it in sections with wildcards.

The result so far is good. I've got the machine pretty much back to the previous state, and have done several updates and reboots without any trouble.

Other note is I use the single icon for the Main Menu, not the default three-panel style. I've used it since Drake. Unlike the three-panel the single has always been slow to open the first time after a login. Roughly 20 seconds. Right now it's about 5 seconds.

So the bottom line is the machine seems fixed, but the problem remains unidentified.

---

### Post by Motorhead Kaze on 2008-06-30
I had the same problem with Gnome!
Gnome froze up last week, I deleted .g named files in Home (yup, except .gimp) and it was cool.  But yesterday, everything froze. Nothing clickable at all.  I tried restarting X, restarting the computer, several times.  The only way to get in to Ubuntu that worked was through failsafe mode.  I tried deleting the .g files again, to no avail.

Tried running a previous kernel, no dice.

I said screw it and reinstalled Hardy fresh. After that, things in Gnome were cool...until I ran the updates.  I restarted the computer, came back and Gnome is stuck.  Similar problems that you listed. I am in failsafe mode again...

BTW, I just tried the link above for killing my panels and rebooting them, with zero results in Normal mode.  Gnome still refuses to do anything but LOOK like it is there. (nothing is clickable).

I have spent 2 days trying to fix this, reading through several similar sounding forum threads, but I need Ubuntu to run to do my JOB. So, because time is an issue, I am going to reinstall GUTSY and hope that whatever evil is oozing from the updates doesn't affect me there. What a drag though.

---

### Post by Motorhead Kaze on 2008-07-01
Checking back in, I actually reinstalled Hardy again fresh. And THIS time I went slower, and did NOT accept the updates which made any mention of Gnome or Libgnome, etc.  Hardy is now running great.  Ah, I even installed the new kernel 19? and Hardy is still fine.  So, I have to assume that one of those updates for Hardy is messing up Gnome.

---

### Post by ofb on 2008-07-01
> **Motorhead Kaze said:**
> So, I have to assume that one of those updates for Hardy is messing up Gnome.

That might be jumping to conclusion. For instance, you could have a corrupt dot file that is not called or activated until you hit that update. That's only a hypothesis, but one that would fit both of our descriptions.

My machine's been fine since going Bowman as described, so the bad update theory doesn't work for this machine.

... Thinking about it, my technique would have wiped out quite a bit that'd been carried over from earlier installs. It /could/ be that an update conflicts with a non-corrupt leftover config from Gusty or earlier install.

---

### Post by mrtorture on 2008-12-02
Sorry for bump this thread, but i'm with the same "jam" in some clients of my job. All stations are Hardy 8.04, and got recent updates. One of the users reported that this "jams" started on his computer before using a pendrive. It may be associated to opening a file directly from the device, then closed and removed the device without umount. May be, or not, but it's possible that the jam is caused by an attempt to read a file on the device, but it can't, like a "recently used files" service.

All softwares, like gedit or soffice, jam when try to open or save a file. And it's _only happen in his profile_, all other profiles, even opening in the same machine, don't get this jam. It IS a problem on the profile configuration, and i've lurked it for hours without help. Once time i've solved it changing all permissions on files and folders of the profile, but it returned to happen, maybe because of the system update.

So, it's directly related with the profile, not with the whole system. And the only "error line" that i got was this:

g_bookmark_file_get_size: assertion `bookmark != NULL' failed

And I believe that's may be related with the usb device.

If someone more experienced this problem and got a solution, please, help!

* sorry my bad english

---

