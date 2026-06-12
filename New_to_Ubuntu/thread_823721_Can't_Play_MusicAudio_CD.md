---
title: "Can't Play Music/Audio CD"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by jethin on 2008-06-09
Well, I tried to solve this one by myself but no luck. Here's the scenario: I insert a regular old music cd into my cdrom drive; Totem starts but says "An error occurred: Location not found." Permissions? I've tried the Xubuntu multimedia guide, installing multimedia codecs, installing grip and xmms (no dice) all to no avail.

As an aside, when I insert a data cd with mp3s on it, Totem gives me a permissions error when I try to play them. I believe the problem may be that the files are set to 501 permissions by default. Any way to make such files playable/executable on disc mount? Thanks, Jeremy

---

### Post by wootah on 2008-06-09
After inserting a disc, can you copy the song directly to your hdd ? Perhaps try that and then see if you can play the song from your hdd. That will also give us a clue as to what is happening with the permissions :)

---

### Post by jethin on 2008-06-09
Nope, I can't copy from the disk to my desktop. Here's the error:

```
Failed to copy "/media/cdrom0/music/jive.wav" to "/home/jeremy/Desktop/jive.wav": Failed to open "/media/cdrom0/music/jive.wav" for reading (Permission denied).
```

So in this case, I can't play the jive-talking scene from Airplane. How sad is that? :)

---

### Post by wootah on 2008-06-09
> **jethin said:**
> Nope, I can't copy from the disk to my desktop. Here's the error:

```
Failed to copy "/media/cdrom0/music/jive.wav" to "/home/jeremy/Desktop/jive.wav": Failed to open "/media/cdrom0/music/jive.wav" for reading (Permission denied).
```So in this case, I can't play the jive-talking scene from Airplane. How sad is that? :)

Alright, let's take a look at your fstab... maybe something got messed up somehow.

```
cat /etc/fstab
```
Your cdrom(s) should look similar to the following:
```

/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Also, you may want to take a look to see if you are part of the *cdrom *group (as silly as it sounds):
```

groups

```

---

### Post by jethin on 2008-06-09
My fstab entries are similar, though they also include "exec,utf8":

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

And it appears that I am a member of the cdrom group. Though I'm not sure I'd want to join any group...

---

### Post by Bachstelze on 2008-06-09
Have you tried another player, like Amarok, Kaffeine, MPlayer or *shudders* VLC?

---

### Post by jethin on 2008-06-09
Hi HymnToLife. I installed grip but it didn't work with cds either. I tried to install xmms, but can't seem to get it to run. I installed xmms using Synaptic b/c apt-get returned errors. I'm guessing that I didn't get all the necessary packages.

In any case, I think Totem is functioning properly. I can play files that are on my computer that don't have any permission problems. But hey, I'll try anything. My only stipulation is that if I install a new player that it be lightweight. I'm on an old machine and I really only want to play cds.

---

### Post by Elyseum on 2008-06-13
I'm having the same problem: I can play music cd's with sound juicer but not with Totem (same error as above), nor Exaile (song names get loaded but they don't start to play).
It did work on Feisty, but stopped working after updating to Hardy...

---

### Post by jethin on 2008-07-16
Update: I uninstalled Totem and Grip began to recognize my cd drive(s). I still can't hear cd audio, but Grip appears to play the cds properly and can rip/encode them. So, I think cd drive permissions problem may have had something to do with Totem, but I now believe the lack of cd sound is related to my sound card, which is an M-Audio Delta 66. I can hear mp3s however, so in the meantime I s'pose I'll keep ripping.

---

### Post by fred.warren on 2008-08-02
Hi I just solved this problem myself and will be filing a bug report.

Thunar has the association for audio cds cdda:/ instead of the proper cdda:// and for dvds as dvd:/ instead of dvd://

To correct this do the following
[LIST=1]
[*]Open Thunar (Can be found on the Menu under Accessories)
[*]From the menu at the top of Thunar select **_E_dit**
[*]From the **_E_dit** menu select **Pr_e_ferences**
[*]From the **File Manager Preferences** dialog, click on the tab labeled **Advanced**
[*]From the **Advanced** tab click on the blue linked word **Configure**
[*]From the **Removable Drives and Media** dialog, click on the tab labeled **Multimedia**
[*]From the **Multimedia** tab for the **Audio CDs _C_ommand** locate the entry **totem cdda:/**
[*]Change that to **totem cdda://**
[*]From the **Multimedia** tab for the **Video CDs/DVDs C_o_mmand** locate the entry **totem dvd:/**
[*]Change that to **totem dvd://**
[*]Close all dialogs and exit Thunar
[*]Insert your CD or DVD and enjoy
[/LIST]

---

