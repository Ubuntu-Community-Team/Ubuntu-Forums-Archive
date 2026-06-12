---
title: "Disk Usage Analyzer - Need help understanding result"
date: 2023-06-18
forum: New to Ubuntu
---

### Post by bhubunt on 2023-06-18
Hi,
Is there anyone here who can help me understand the disk analysis I just received, see screenshot below.

There are several things that puzzle me:

1/ at the top it says:

Error opening directory: 'tmp/snap-private-tmp': Permission denied 

Why is permission denied?

2/

var, etc, and tmp were modified today, yet I was not at home today and just opened my computer minutes ago, while I was offline. So I could not have downloaded anything from the internet.

---

### Post by bhubunt on 2023-06-18
And a P S: I just did a disk analysis of my Home Folder and here too there is a long list of files that were modified today, though I was not at home. 

I got the feeling that my computer may have been tampered with. 

How can I check if items were added to my computer?

---

### Post by bhubunt on 2023-06-18
Finally, I hate to have to post this again, as I have done this in the past, but while I was typing this message on the Ubuntu Forum, my laptop about which I am reporting in this thread (Lenovo x240, with Ubuntu 20.04 OS) was hacked again. 

Two screenshots of the disk analysis  that I tried to upload for this forum were deleted repeatedly from the Manage Attachment Window.

And a Libre office writer file turned into a remote file, even though I never use remote files, see top bar of the screenshot attached, which says remote. I never use remote files, ever.
 
Any idea?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292395&stc=1[/IMG]

---

### Post by ajgreeny on 2023-06-18
Every time you use your computer, even if you do nothing but start a new session or restore it from suspend, some files in your home and in the root filesystem will be changed or accessed.
You do not mention by name any file as an example of one that has apparently changed but I suspect that what you have noted is completely normal and expected.

Tell us more detail of specific files/folders that have changed and we might be able to give you more information.

---

### Post by bhubunt on 2023-06-18
Hi,
Thanks for replying. To answer your question: all of the items that are in my home folder and that say "modified today." The same for the items that say "modified today" in the first screenshot: greener-Thinkpad-x240. 

Also, why is permission denied for Error opening directory: 'tmp/snap-private-tmp': Permission denied

If any and all of this is harmless, then I'd like to hear that.

However, the deletions while I am typing and the bizarre remote file are not harmless. I also have had logs changed, screenshots of irregularities that I made changed into 0 bytes.

---

### Post by ajgreeny on 2023-06-18
It was me who removed the large images from your first two posts!  The images were already there but as attachments (small icons which show at the bottom of the posts) which open as a large image when clicked.

These attachments must have been added by you using the paperclip icon in the "Reply to Thread" toolbar, but I see you did not add the third image in this way but added it as an inline item which we try to avoid; they make life difficult for users with limited bandwidth or who pay for their downloads (yes, it still works that way for some) and it makes viewing the forum similarly a problem on small screen mobile devices such as tablets or phones.

Please use the Attachment facility in future.

---

### Post by Holger_Gehrke on 2023-06-18
'/tmp/snap-private-tmp/' is owned by root with no permissions for anybody else. AFAIK it's a directory for temporary files used by the snap background process (snapd).

Stuff in '/var' is getting modified all the time. The logs live there. So do snap packages. So do databases.

Same goes for '/tmp'. It's for temporary files. You might not see them with 'ls' or the file manager since an old trick is to create a temporary file, open it for reading and writing and then deleting it. The program still has a valid handle on the file, so the only thing that gets removed is the name, the program can still use the file and nobody else can even tell the file exists unless they look with lsof - 'list open files' - then they'll see it but still can't access it since there's no name to use for opening it. The used blocks will be freed as soon as the program using the temporary file closes it.

Changes in '/etc/' are more cause for concern. Nothing should be able to make changes in '/etc/' unless it has rather high level permissions.

I'd try using find and the '-mmin' test to look for the changed files in the directories. Something like 
```

find /etc ~/Videos ~/Downloads ~/Pictures ~/Music ~/.cache ~/.config ~/Desktop ~/.mozilla ~/.local ~/.gnupg -mmin +180 -a -mmin -720

```
This would look for files changed more than 3 hours (180 minutes) but less than 12 hours (720 minutes) ago. Change the times to fit the time where nothing *should* have happened.

Holger

---

### Post by bhubunt on 2023-06-18
> **ajgreeny said:**
> It was me who removed the large images from your first two posts!  The images were already there but as attachments (small icons which show at the bottom of the posts) which open as a large image when clicked.

These attachments must have been added by you using the paperclip icon in the "Reply to Thread" toolbar, but I see you did not add the third image in this way but added it as an inline item which we try to avoid; they make life difficult for users with limited bandwidth or who pay for their downloads (yes, it still works that way for some) and it makes viewing the forum similarly a problem on small screen mobile devices such as tablets or phones.

Please use the Attachment facility in future.


Hi AJGreeny,
I will not use inline again. Thanks for pointing that out!

However, I think you misunderstood me. When I mentioned that two pics were deleted while I tried to place them in my post, I did not mean you compressing the pics in my post at all. I referred to the attachments that disappeared repeatedly while I was trying to post them. Nothing to do with you.

---

### Post by bhubunt on 2023-06-18
> **Holger_Gehrke said:**
> '
Changes in '/etc/' are more cause for concern. Nothing should be able to make changes in '/etc/' unless it has rather high level permissions.

I'd try using find and the '-mmin' test to look for the changed files in the directories. Something like 
```

find /etc ~/Videos ~/Downloads ~/Pictures ~/Music ~/.cache ~/.config ~/Desktop ~/.mozilla ~/.local ~/.gnupg -mmin +180 -a -mmin -720

```
This would look for files changed more than 3 hours (180 minutes) but less than 12 hours (720 minutes) ago. Change the times to fit the time where nothing *should* have happened.

Holger

Thanks a million for the code. I typed it in with and without sudo. 

Without sudo I got the following result:

```
 find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/etc/cups/ssl’: Permission denied

```

With the sudo, for which I typed in  my password, I got no result.

---

### Post by bhubunt on 2023-06-18
When I posted the following code, which, I take it, was a search to see what had been changed in the last 24 hours

```
 find /usr mtime -1 
```

I got an enormous list in return, 4865 code lines, a list so long, I had to put it in pastebin

[https://pastebin.com/aHLAsEUj](https://pastebin.com/aHLAsEUj)

---

### Post by Holger_Gehrke on 2023-06-18
Without 'sudo' it couldn't access some things which only root has access to, but otherwise found nothing changed within the given time frame. With sudo it could access those places and still found nothing. So whatever happened didn't happen while you were away. I'd try again (several times) but leave out ~/.cache and ~/.mozilla (those directories are full of stuff that changes all the time) and decrease the '+180' part and increase the '-720' to see what was changed. BTW the '+' and '-' in those time values is important; the '+' means 'more than' and the '-' means 'less than'. If you give a time without either, find will look for files changed exactly that many minutes ago.

Holger

---

### Post by ajgreeny on 2023-06-18
Something very strange going on there!

When I run that command I see nothing listed which is much as expected.

---

### Post by bhubunt on 2023-06-18
> **Holger_Gehrke said:**
> Without 'sudo' it couldn't access some things which only root has access to, but otherwise found nothing changed within the given time frame. With sudo it could access those places and still found nothing. So whatever happened didn't happen while you were away. I'd try again (several times) but leave out ~/.cache and ~/.mozilla (those directories are full of stuff that changes all the time) and decrease the '+180' part and increase the '-720' to see what was changed. BTW the '+' and '-' in those time values is important; the '+' means 'more than' and the '-' means 'less than'. If you give a time without either, find will look for files changed exactly that many minutes ago.

Holger



OK. 

Thanks for the tip.


And what about the last post, where I got more than 4,000 code lines in response?

---

### Post by bhubunt on 2023-06-18
> **ajgreeny said:**
> Something very strange going on there!

When I run that command I see nothing listed which is much as expected.

Is this addressed to me or to Holger?

And what command are you referring to?

---

### Post by Holger_Gehrke on 2023-06-18
> **bhubunt said:**
> When I posted the following code, which, I take it, was a search to see what had been changed in the last 24 hours

```
 find /usr [COLOR=#ff0000]**-**[/COLOR]mtime -1 
```

I got an enormous list in return, 4865 code lines, a list so long, I had to put it in pastebin

[https://pastebin.com/aHLAsEUj](https://pastebin.com/aHLAsEUj)

That's just the latest kernel update, specifically the modules and the includes. Look at the last few items in /var/log/apt/history.log. The files themselves get the modification time from the tar-file inside the deb-package, but the directories get modified during the update and show up in your search results.

Holger

---

### Post by ajgreeny on 2023-06-18
> **bhubunt said:**
> Is this addressed to me or to Holger?

And what command are you referring to?

It was an answer to you about the command **find /usr  -mtime -1**

---

### Post by bhubunt on 2023-06-18
> **Holger_Gehrke said:**
>  Look at the last few items in /var/log/apt/history.log. The files themselves get the modification time from the tar-file inside the deb-package, but the directories get modified during the update and show up in your search results.

Holger


OK -- so this is what I got without sudo 

```
 bash: /var/log/apt/history.log: Permission denied 
```

---

### Post by #&amp;thj^% on 2023-06-18
Try "cat" and not bash
```
cat /var/log/apt/history.log
```

---

### Post by bhubunt on 2023-06-18
Holger, I did get a syslog through the gedit command but there is something wrong with it. I am attaching a screenshot, as there are more than 12,000 code lines. Perhaps you could look at the screenshot to assess what is wrong with the syslog?

---

### Post by Holger_Gehrke on 2023-06-18
For looking at log files use 'less' (it's an enhanced replacement for an older pager named 'more' - 'less is more than more'). You can freely move through a file, search it, mark places in the file and return to them later and it can open multiple files at once and switch between them. You can even start an editor from 'less' to change files if you spot an error.

And I don't see anything catastrophically wrong in that syslog screenshot. Looks like networkd-dispatcher is loosing it's mind about the loopback interface (which it really shouldn't bother with, it's for your machine talking to itself ...) and 'enp0s25' (probably a wired ethernet connection which isn't plugged in). Nothing to see here, except for gedit throwing a fit at not being able to automatically deduce the encoding of the file. Might be a bit of binary in there somewhere from a misbehaving program or some terminal control sequences. 12000 lines isn't especially much,  considering that the first second after boot already produces more than 1500 lines ...

Holger

---

### Post by oldfred on 2023-06-18
You really only need to see errors or warnings. 
I get a couple of pages, some just have error in a comment or various warnings.

Review log files
sudo grep -Ei 'warn|error' /var/log/*g

---

### Post by bhubunt on 2023-06-19
Double post  -- REMOVED.  Sorry for the double posting.

---

### Post by bhubunt on 2023-06-19
Old Fred and Holger, this is what I get with the grep command


```
  /var/log/auth.log:Jun 19 07:11:21 greener-ThinkPad-X240 sudo:  greener : TTY=pts/0 ; PWD=/home/greener ; USER=root ; COMMAND=/usr/bin/grep -Ei warn|error /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var/log/dmesg /var/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/kern.log /var/log/lastlog /var/log/syslog /var/log/ubuntu-advantage.log /var/log/ubuntu-advantage-timer.log /var/log/ufw.log/var/log/bootstrap.log:2023-03-16 15:37:17 URL:http://ftpmaster.internal/ubuntu/pool/main/libg/libgpg-error/libgpg-error0_1.37-1_amd64.deb [58004/58004] -> "/build/chroot//var/cache/apt/archives/partial/libgpg-error0_1.37-1_amd64.deb" [1]
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60 package 'dpkg':
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Selecting previously unselected package libgpg-error0:amd64.
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.37-1_amd64.deb ...
/var/log/bootstrap.log:Unpacking libgpg-error0:amd64 (1.37-1) ...
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
/var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.37-1) ...
/var/log/dmesg:[    0.174913] kernel: ACPI Error: Needed type [Reference], found [Integer] 00000000e311c65e (20210730/exresop-66)
/var/log/dmesg:[    0.174928] kernel: ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20210730/dswexec-431)
/var/log/dmesg:[    0.174960] kernel: ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERAND_TYPE) (20210730/psparse-529)
/var/log/dmesg:[    0.683047] kernel: RAS: Correctable Errors collector initialized.
/var/log/dmesg:[   28.873323] kernel: EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro. Quota mode: none.
/var/log/kern.log:Jun 18 21:04:20 greener-ThinkPad-X240 kernel: [    0.175054] ACPI Error: Needed type [Reference], found [Integer] 000000008cbac508 (20210730/exresop-66)
/var/log/kern.log:Jun 18 21:04:20 greener-ThinkPad-X240 kernel: [    0.175069] ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20210730/dswexec-431)
/var/log/kern.log:Jun 18 21:04:20 greener-ThinkPad-X240 kernel: [    0.175101] ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERAND_TYPE) (20210730/psparse-529)
Binary file /var/log/kern.log matches
/var/log/syslog:Jun 19 00:00:41 greener-ThinkPad-X240 gnome-shell[2262]: [ERROR viaduct::backend::ffi] Missing HTTP status
/var/log/syslog:Jun 19 00:00:41 greener-ThinkPad-X240 gnome-shell[2262]: [ERROR viaduct::backend::ffi] Missing HTTP status
/var/log/syslog:Jun 19 00:01:15 greener-ThinkPad-X240 libreoffice-writer.desktop[5735]: Warning: failed to read path from javaldx
/var/log/syslog:Jun 19 00:01:55 greener-ThinkPad-X240 gnome-shell[1775]: Window manager warning: WM_TRANSIENT_FOR window 0x180298f for 0x1802a61 window override-redirect is an override-redirect window and this is not correct according to the standard, so we'll fallback to the first non-override-redirect window 0x180009b.
/var/log/syslog:Jun 19 00:02:42 greener-ThinkPad-X240 gnome-shell[5867]: MESA-INTEL: warning: Haswell Vulkan support is incomplete
/var/log/syslog:Jun 19 00:02:43 greener-ThinkPad-X240 gnome-shell[5867]: [5860:5860:0619/000243.062475:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.portal.Settings.Read: object_path= /org/freedesktop/portal/desktop: org.freedesktop.portal.Error.NotFound: Requested setting not found
/var/log/syslog:Jun 19 00:02:45 greener-ThinkPad-X240 gnome-shell[5867]: [5860:5860:0619/000245.302099:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
/var/log/syslog:Jun 19 00:03:56 greener-ThinkPad-X240 gnome-shell[6435]: [Child 6435, MediaDecoderStateMachine #1] WARNING: Decoder=7f44c7e62e00 Decode error: NS_ERROR_DOM_MEDIA_FATAL_ERR (0x806e0005) - Error no decoder found for audio/mp4a-latm: file /build/firefox-9qNWb6/firefox-114.0.1+build1/dom/media/MediaDecoderStateMachineBase.cpp:164
/var/log/syslog:Jun 19 00:04:10 greener-ThinkPad-X240 gnome-shell[6542]: [Child 6542, MediaDecoderStateMachine #1] WARNING: Decoder=7fe9e90bd500 Decode error: NS_ERROR_DOM_MEDIA_FATAL_ERR (0x806e0005) - Error no decoder found for audio/mp4a-latm: file /build/firefox-9qNWb6/firefox-114.0.1+build1/dom/media/MediaDecoderStateMachineBase.cpp:164
/var/log/syslog:Jun 19 00:09:13 greener-ThinkPad-X240 gnome-shell[6198]: [ERROR viaduct::backend::ffi] Missing HTTP status
/var/log/syslog:Jun 19 00:09:13 greener-ThinkPad-X240 gnome-shell[6198]: [ERROR viaduct::backend::ffi] Missing HTTP status
/var/log/syslog:Jun 19 00:09:18 greener-ThinkPad-X240 gnome-shell[5867]: [5903:5903:0619/000918.190840:ERROR:shared_image_manager.cc(217)] SharedImageManager::ProduceSkia: Trying to Produce a Skia representation from a non-existent mailbox.
/var/log/syslog:Jun 19 00:09:18 greener-ThinkPad-X240 gnome-shell[5867]: [5903:5903:0619/000918.194751:ERROR:shared_image_manager.cc(217)] SharedImageManager::ProduceSkia: Trying to Produce a Skia representation from a non-existent mailbox.
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 pulseaudio[1557]: ICE default IO error handler doing an exit(), pid = 1557, errno = 32
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 gnome-shell[1775]: JS ERROR: Error: Argument 'instance' (type interface) may not be null#012_init/GObject.Object.prototype.disconnect@resource:///org/gnome/gjs/modules/core/overrides/GObject.js:571:24#012_onDestroy@/usr/share/gnome-shell/extensions/desktop-icons@csoriano/desktopGrid.js:209:45#012_init/<@/usr/share/gnome-shell/extensions/desktop-icons@csoriano/desktopGrid.js:148:44
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 xdg-desktop-por[2186]: xdg-desktop-portal-gtk: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 xdg-desktop-por[4021]: xdg-desktop-portal-gtk: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 tracker-miner-f[1559]: Error while sending AddMatch() message: The connection is closed
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 tracker-miner-f[1559]: Error while sending AddMatch() message: The connection is closed
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 tracker-miner-f[1559]: Error while sending AddMatch() message: The connection is closed
/var/log/syslog:Jun 19 00:09:45 greener-ThinkPad-X240 evolution-calen[1842]: Error setting property 'ConnectionStatus' on interface org.gnome.evolution.dataserver.Source: The connection is closed (g-io-error-quark, 18)
/var/log/syslog:Jun 19 00:09:46 greener-ThinkPad-X240 gnome-session[7056]: gnome-session-binary[7056]: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 00:09:46 greener-ThinkPad-X240 gnome-session-binary[7056]: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 00:09:48 greener-ThinkPad-X240 gnome-shell[7095]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
/var/log/syslog:Jun 19 00:09:48 greener-ThinkPad-X240 gsd-sharing[7197]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 00:09:48 greener-ThinkPad-X240 gsd-sharing[7197]: message repeated 3 times: [ Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1]
/var/log/syslog:Jun 19 00:09:49 greener-ThinkPad-X240 org.gnome.Shell.desktop[7311]: > Warning:          Unsupported maximum keycode 569, clipping.
/var/log/syslog:Jun 19 00:09:49 greener-ThinkPad-X240 org.gnome.Shell.desktop[7311]: > Internal error:   Could not resolve keysym Invalid
/var/log/syslog:Jun 19 00:09:49 greener-ThinkPad-X240 org.gnome.Shell.desktop[7311]: Errors from xkbcomp are not fatal to the X server
/var/log/syslog:Jun 19 00:09:54 greener-ThinkPad-X240 gnome-shell[7095]: Warning: Failed to start gsd-xsettings
/var/log/syslog:Jun 19 00:09:55 greener-ThinkPad-X240 gnome-shell[7095]: JS WARNING: [resource:///org/gnome/shell/ui/layout.js 24]: reference to undefined property "MetaWindowXwayland"
/var/log/syslog:Jun 19 07:04:21 greener-ThinkPad-X240 kernel: [    0.174913] ACPI Error: Needed type [Reference], found [Integer] 00000000e311c65e (20210730/exresop-66)
/var/log/syslog:Jun 19 07:04:21 greener-ThinkPad-X240 kernel: [    0.174928] ACPI Error: AE_AML_OPERAND_TYPE, While resolving operands for [Store] (20210730/dswexec-431)
/var/log/syslog:Jun 19 07:04:21 greener-ThinkPad-X240 kernel: [    0.174960] ACPI Error: Aborting method \_PR.CPU0._PDC due to previous error (AE_AML_OPERAND_TYPE) (20210730/psparse-529)
/var/log/syslog:Jun 19 07:04:21 greener-ThinkPad-X240 kernel: [    0.683047] RAS: Correctable Errors collector initialized.
/var/log/syslog:Jun 19 07:04:21 greener-ThinkPad-X240 kernel: [   28.873323] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro. Quota mode: none.
/var/log/syslog:Jun 19 07:04:21 greener-ThinkPad-X240 systemd[1]: Condition check resulted in Process error reports when automatic reporting is enabled (file watch) being skipped.
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 thermald[958]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 thermald[958]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 thermald[958]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 thermald[958]: error: could not parse file /etc/thermald/thermal-conf.xml
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 thermald[958]: error: could not parse file /etc/thermald/thermal-conf.xml
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 thermald[958]: error: could not parse file /etc/thermald/thermal-conf.xml
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 networkd-dispatcher[1061]: WARNING: systemd-networkd is not running, output will be incomplete.
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 networkd-dispatcher[933]: ERROR:Unknown state for interface NetworkctlListState(idx=1, name='lo', type='loopback', operational='n/a', administrative='unmanaged'): n/a
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 networkd-dispatcher[933]: ERROR:Unknown state for interface NetworkctlListState(idx=2, name='enp0s25', type='ether', operational='n/a', administrative='unmanaged'): n/a
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 NetworkManager[926]: <warn>  [1687151062.4852] ifupdown: interfaces file /etc/network/interfaces doesn't exist
/var/log/syslog:Jun 19 07:04:22 greener-ThinkPad-X240 NetworkManager[926]: <warn>  [1687151062.7133] Error: failed to open /run/network/ifstate
/var/log/syslog:Jun 19 07:04:23 greener-ThinkPad-X240 gnome-session[1098]: gnome-session-binary[1098]: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 07:04:23 greener-ThinkPad-X240 gnome-session-binary[1098]: WARNING: Falling back to non-systemd startup procedure due to error: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 07:04:25 greener-ThinkPad-X240 gnome-shell[1150]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
/var/log/syslog:Jun 19 07:04:25 greener-ThinkPad-X240 gsd-sharing[1330]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 07:04:25 greener-ThinkPad-X240 gsd-sharing[1330]: message repeated 3 times: [ Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1]
/var/log/syslog:Jun 19 07:04:29 greener-ThinkPad-X240 org.gnome.Shell.desktop[1500]: > Warning:          Unsupported maximum keycode 569, clipping.
/var/log/syslog:Jun 19 07:04:29 greener-ThinkPad-X240 org.gnome.Shell.desktop[1500]: > Internal error:   Could not resolve keysym Invalid
/var/log/syslog:Jun 19 07:04:29 greener-ThinkPad-X240 org.gnome.Shell.desktop[1500]: Errors from xkbcomp are not fatal to the X server
/var/log/syslog:Jun 19 07:04:30 greener-ThinkPad-X240 gsd-sharing[1330]: Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1
/var/log/syslog:Jun 19 07:04:30 greener-ThinkPad-X240 gsd-sharing[1330]: message repeated 3 times: [ Failed to StopUnit service: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.freedesktop.systemd1 exited with status 1]
/var/log/syslog:Jun 19 07:04:31 greener-ThinkPad-X240 gnome-shell[1150]: Warning: Failed to start gsd-xsettings
/var/log/syslog:Jun 19 07:04:32 greener-ThinkPad-X240 gnome-shell[1150]: JS WARNING: [resource:///org/gnome/shell/ui/layout.js 24]: reference to undefined property "MetaWindowXwayland"
/var/log/syslog:Jun 19 07:04:40 greener-ThinkPad-X240 /usr/lib/gdm3/gdm-x-session[1623]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/syslog:Jun 19 07:04:42 greener-ThinkPad-X240 gnome-session-c[1751]: Error creating FIFO: File exists
/var/log/syslog:Jun 19 07:04:46 greener-ThinkPad-X240 gnome-shell[1772]: Error looking up permission: GDBus.Error:org.freedesktop.portal.Error.NotFound: No entry for geolocation
/var/log/syslog:Jun 19 07:04:48 greener-ThinkPad-X240 pulseaudio[1553]: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
/var/log/syslog:Jun 19 07:04:49 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
/var/log/syslog:Jun 19 07:04:50 greener-ThinkPad-X240 gnome-session[1098]: gnome-session-binary[1098]: WARNING: Lost name on bus: org.gnome.SessionManager
/var/log/syslog:Jun 19 07:04:50 greener-ThinkPad-X240 gnome-session-binary[1098]: WARNING: Lost name on bus: org.gnome.SessionManager
/var/log/syslog:Jun 19 07:05:00 greener-ThinkPad-X240 tracker-miner-f[1081]: Error while sending AddMatch() message: The connection is closed
/var/log/syslog:Jun 19 07:05:00 greener-ThinkPad-X240 tracker-miner-f[1081]: message repeated 2 times: [ Error while sending AddMatch() message: The connection is closed]
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
/var/log/syslog:Jun 19 07:05:06 greener-ThinkPad-X240 gnome-shell[1772]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
/var/log/syslog:Jun 19 07:05:17 greener-ThinkPad-X240 snap-store[2032]: not handling error failed for action refresh: E: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/focal/InRelease  #012E: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  #012E: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease  #012E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  #012E: Failed to fetch https://dl.google.com/linux/chrome/deb/dists/stable/InRelease  #012E: Some index files failed to download. They have been ignored, or old ones used instead.
/var/log/syslog:Jun 19 07:06:55 greener-ThinkPad-X240 gnome-shell[2844]: [ERROR viaduct::backend::ffi] Missing HTTP status
/var/log/syslog:Jun 19 07:06:55 greener-ThinkPad-X240 gnome-shell[2844]: [ERROR viaduct::backend::ffi] Missing HTTP status
/var/log/syslog:Jun 19 07:07:31 greener-ThinkPad-X240 gnome-shell[4160]: MESA-INTEL: warning: Haswell Vulkan support is incomplete
/var/log/syslog:Jun 19 07:07:32 greener-ThinkPad-X240 gnome-shell[4160]: [4153:4153:0619/070732.282938:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.portal.Settings.Read: object_path= /org/freedesktop/portal/desktop: org.freedesktop.portal.Error.NotFound: Requested setting not found
/var/log/syslog:Jun 19 07:07:34 greener-ThinkPad-X240 gnome-shell[4160]: [4153:4153:0619/070734.412872:ERROR:object_proxy.cc(590)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
/var/log/ubuntu-advantage.log:["2023-06-10T20:19:15.488", "WARNING", "root", "update_esm_caches", 744, "Failed to fetch the ESM Apt Cache", {}]
/var/log/ubuntu-advantage.log:["2023-06-14T08:18:48.489", "WARNING", "root", "update_esm_caches", 744, "Failed to fetch the ESM Apt Cache", {}]
/var/log/ubuntu-advantage.log:["2023-06-14T08:27:28.386", "WARNING", "root", "update_esm_caches", 744, "Failed to fetch the ESM Apt Cache", {}]
greener@greener-ThinkPad-X240:~$ ^C
greener@greener-ThinkPad-X240:~$ 


  
```

---

### Post by bhubunt on 2023-06-19
To Holger and others helping me with the reading of the syslogs. I just tried to paste yesterday's syslogs of June 18, 2023 (of the time I was being hacked, see post nr 19) on pastebin.com, but I was hacked again while I tried to do so. As I was logged in to pastebin.com, my mouse was disabled, turned into a vertical bar, the page went completely blank and I could not post the portion of the syslog session documenting the time when I was hacked yesterday (at around 9:00 PM and earlier, see posts number 3  and 19 in this thread). 

Below is a screen shot showing that I was making remote connection just a few minutes ago, indicative of being hacked, as I do not use remote files ever. 

I will keep at it and try posting the section of the June 18 syslog again later.

Here's the screenshot of evidence of the hack from just a few minutes ago, showing "remote" in the top bar. I also do not have a server set up, just use desktop Ubuntu 20.04.

---

### Post by oldfred on 2023-06-19
I do not use gnome, as I have Kubuntu. So not familiar with those issues.

Did you at some point use LibreOffice and click on file, use remote files. And it made that the default?

---

### Post by Rubi1200 on 2023-06-19
Do you share the computer with others? Maybe someone inadvertently changed something?

---

### Post by bhubunt on 2023-06-19
> **oldfred said:**
> 

Did you at some point use LibreOffice and click on file, use remote files. And it made that the default?

Hi,
No, I did not click on file, use remote files. In fact, when I open remote on libre office, there is a completely empty window, as I never use remote. I have a simple laptop, no server, no one I work with, no one I share the computer with. 

If anyone can tell me what to look for in the syslogs to check for a remote desktop connection, I would appreciate it.

However, as I mentioned earlier in this thread, I have had logs changed as well as screenshots of irregularities I made turned into 0 bytes. Same with logs I saved that were turned into 0 bytes. So I reckon my syslogs may also have been tampered with. But I'd be glad to look for irregularities in the logs.

---

### Post by bhubunt on 2023-06-19
> **Rubi1200 said:**
> Do you share the computer with others? Maybe someone inadvertently changed something?

Hi Rubi,
Thanks for asking but the answer is no. See my answer in the previous post. Suggestions about what to look for in the syslogs are appreciated.

---

### Post by bhubunt on 2023-06-27
Hi,
Just now, I did another disk usage analysis and again the etc folder was updated today, which Holger earlier had called attention to.

This time, however, I clicked on the etc folder to see what had been changed:

1/cups: when I clicked on cups, two items were updated: subscriptions.conf and subscriptions.confO
Cups is the printing system. Any idea what subscriptions is about and why it would have been updated? 

2/printcap was changed, which is related to cups 

3/resolv.config

```
 This file is managed by man:systemd-resolved(8). Do not edit.#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
options edns0 trust-ad
search home  
```

I'd be grateful for explanations as to why these files in etc were updated today.  I use a commercial modem and Ubuntu 20.04 LTS on a desktop, I have no personal server, no router, nor am I a member of a private network. I do not print files on this computer. Earlier Holger noted: > : [COLOR=#000000]Changes in '/etc/' are more cause for concern. Nothing should be able to make changes in '/etc/' unless it has rather high level permissions.[/COLOR]

---

### Post by #&amp;thj^% on 2023-06-27
Well i had updates for cups:
```
 2022-10-20 07:07:29 install libcups2:amd64 <none> 2.4.2-1ubuntu2
2022-10-20 07:07:29 status half-installed libcups2:amd64 2.4.2-1ubuntu2
2022-10-20 07:07:29 status unpacked libcups2:amd64 2.4.2-1ubuntu2
```

---

### Post by Holger_Gehrke on 2023-06-27
cups can send notifications to programs that subscribe to them. /etc/cups/subscriptions.conf is the file cups uses to keep track of these subscriptions. There's a manual page in section 5 (file formats) of the manual. On my system - which has no printer except the 'print to pdf-file' pseudo-printer -  there are two subscriptions, one owned by root for 'Printer changed' events and one that sends all notifcations to the dbus. The file is owned by root and belongs to the group 'lp' (line printer) and is rw for root and read-only for members of lp. Since cups is run by root, that's okay. If there was an update, then subscriptions.conf was updated and subscription.confO is probably the 'O'riginal file from before the update.

Are you sure about '/etc/resolv.conf**ig**' ? It should only be 'resolv.conf' and that should be a symbolic link to a file in /run/systemd/resolve/. And since /run is normally a ram-disk (tmpfs), this file is created by systemd on every boot. So if your disk analyzer examines the file the link points to then it will find it has changed and will find so each and every day that you reboot your system ...

Holger

---

### Post by TheFu on 2023-06-28
Reviewing this, here's what it seems to me.

We have someone who believes that computers don't do things when they aren't using it.  If the computer is on, it does things. File get changed.  If you allow automatic updates or use snap packages, then the system will update things for your. You've allowed it by allowing automatic updates. If you don't like that, disable it.

In your HOME directory, files are changed all the time related to the DE session management and assorted end-user programs that save data, especially cached files.  Browsers and email programs do this all the time.  Some more than others.

Some browsers will automatically refresh pages and some will pre-follow links to make your browsing appear faster. If you never click on the link, it was all wasted download and wasted cache files placed in your $HOME, somewhere.

**I don't see anything to make me think anyone is hacking the system.**  If the system isn't properly tuned for the workload, it is easy for some programs to eat lots of CPU and RAM, forcing swap to be used.  I suspect this is the most likely issue happening.

There are things called "standard warnings".  Gnome is known to shovel a ton of those into logs.  Same for snap packages.  If you don't like those messages, you can quiet them. I don't know how, but google does.  I suspect for Gnome there would be a mix of settings in gconf and possibly an environment variable to be set to drastically reduce output from GTK+ programs.

Of course, if you are a target by someone - perhaps you work for a govt or NGO, then people may actively be trying to hack you.  I don't see anything to make me think this is true, but I didn't look at the logs THAT closely.  My $day_job has me looking at system logs far too much already. No interest whatsoever in looking at anyone else's logs.

To learn about logs, look for warnings and errors, then use google to look up what each means.  There's no shortcut. Sorry.

There's are sticky threads in the "Security" subforum.  Have your read those and are you following what those say to do?  For 95+% of Ubuntu Users, that's all the security they need.  If you are in the last 5%, you'll need to learn much more or pay someone $xxxx.xx to help setup your entire connected life to mitigate all the risks across all your platforms, especially phones and tablets. Handling just 1 device when you use 3+ devices, will just shift where the attackers try to enter your life.

---

### Post by bhubunt on 2023-06-28
> **Holger_Gehrke said:**
> cups can send notifications to programs that subscribe to them. /etc/cups/subscriptions.conf is the file cups uses to keep track of these subscriptions. There's a manual page in section 5 (file formats) of the manual. On my system - which has no printer except the 'print to pdf-file' pseudo-printer -  there are two subscriptions, one owned by root for 'Printer changed' events and one that sends all notifcations to the dbus. The file is owned by root and belongs to the group 'lp' (line printer) and is rw for root and read-only for members of lp. Since cups is run by root, that's okay. If there was an update, then subscriptions.conf was updated and subscription.confO is probably the 'O'riginal file from before the update.

Are you sure about '/etc/resolv.conf**ig**' ? It should only be 'resolv.conf' and that should be a symbolic link to a file in /run/systemd/resolve/. And since /run is normally a ram-disk (tmpfs), this file is created by systemd on every boot. So if your disk analyzer examines the file the link points to then it will find it has changed and will find so each and every day that you reboot your system ...

Holger

Hi Holger,
Thanks for your thoughtful reply. 

Earlier you said that the changes in the etc file were cause for worry, see post #7. But I take it based on your comments that the three file folders I pegged, are no cause for worry, which is good to know.

Thanks again for your expert explanations. Much appreciated:

---

### Post by bhubunt on 2023-06-28
> **TheFu said:**
> Reviewing this, here's what it seems to me.




Hi The Fu,

Just to update you:

Holger already replied to the three file folder changes I posted earlier (cups, printcap). I posted those because in an earlier comment Holger suggested that changes in the etc file folder might be cause for worry (see #7). He asked me to check which files had been changed, which I did. As it turns out, these specific changes were no cause for worry after all, see his post # 31.

So that was good to know.

However, my laptop is still producing mysterious remote files, about which I have posted here and elsewhere. I repeat that I do not have remote set up, not did I by accident check off remote desktop, as someone asked. I also do not share my laptop with anyone, as yet another person here asked. Plus I am not a member of a private or other network. So there is no reason in the world, why I should have remote files on my laptop. Every single day, my laptop generates such remote files.

Below is today's latest screenshot of such a bizarre remote file. The cause of these mysterious remote files, so far is unknown. 

BTW, I also get these remote files on another laptop, which is in fact an airgap laptop (no internet connection, no wifi and no bluetooth modules, which have been removed.)

---

