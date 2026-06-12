---
title: "[SOLVED] Media players and music tagging..."
date: 2008-06-30
forum: New to Ubuntu
---

### Post by bob_hilton on 2008-06-30
After 3 or 4 years of toying with the idea, I finally made the switch to linux a few weeks ago. So far its been great and i'm disapointed i didn't do it sooner! 

One of the things i never really used was a media library for my music. I've spent the past two weeks or so rating my music and creating loads of playlists and i'm loving having it all organized.. or so i thought.

thing is that i've been using Rhythmbox and where i thought i'd constructively spent two weeks tagging everything, it turns out its all kept in rhythmbox's own database and means its all useless when i use it anywhere else.

Which raises a few questions;

1) Is there a way to write rythmbox's tags to the music files for the tags already altered (and automatically from now on)?

2) Which media players do you use? any alternatives on different desktop environments are welcome too. (i believe rhythmbox is gnome only?)

Thanks in advance for any help you can give me :D

btw, most of my music is mp3 but some is ogg, wma & flac.

---

### Post by TusharG on 2008-07-02
Well I'll suggest Amarok. But first of all I'm surprise how come your tagging changes are not getting reflected in file? Which version of Rhythmbox you are using? Have you given rw_rw_ permissions to all the music files that you are updating? I've 0.11.5 version and it updates local files when I update tags of the music files.
  Apart from that there are various ID3Tagging programs. You can easily install them using System->Administration->Synaptic

---

### Post by rossjman1 on 2008-07-02
I use Amarok also, works great. It seems to have about 10x the features (including integrated last.fm support) than iTunes and uses about half the resources.

---

### Post by TusharG on 2008-07-02
These tool can be handy for you...

[http://more-cowbell.org/index.php/Main_Page](http://more-cowbell.org/index.php/Main_Page)
[http://www.listen-project.org/](http://www.listen-project.org/)
[http://pwp.netcabo.pt/paol/tagtool/](http://pwp.netcabo.pt/paol/tagtool/)

---

### Post by Kosimo on 2008-07-02
Rythmbox should write the new tag information directly to the file you're using it.  Do you have witting permissions to the folder where this MP3 are?

---

### Post by bob_hilton on 2008-07-02
When i edit a tag it'll accept the change but revert to the original a few seconds later? All of my mp3's are store on a drive i share with xp, so it's formated in NTFS. Do you think this could be part of the problem?

---

### Post by tmcarson1 on 2008-07-02
I removed Rhythm box and installed Amarok, I love the layout of it and it works perfectly with my mp3 player.  RB worked with my mp3 player too, just the RB interface seemed so bland to me.

:KS

---

### Post by bob_hilton on 2008-07-04
If anyone's interested or having the problem i was (rhythmbox not saving tags) it appears to have been the NTFS disc.

I had all my music on a separate disk i shared between ubuntu and xp formatted in NTFS so i could access it from either o/s.

I backed up the disk and then reformatted it as ext3 using gparted. I restored my music and pointed rhythmbox back at my music. Now when i tag them they stay tagged.

---

