---
title: "how do you arrange your folders in home"
date: 2009-02-09
forum: Other OS Talk
---

### Post by cmay on 2009-02-09
hi. i was just wondering how you arrange the folders in your home.
i have learned something of crunch bang linux and from having debian which do not create any folders named music documents and so on but just an empty home folder i am used to use in ubuntu the few folders which i find useful and i delete the rest. so i have the folders

Documents. ( all my writings there is subfolders for all things including a personal folder)

Music ( just all my cd collection)

Video ( some movies and webcam recordings)

development ( i am learning but it sounds better than pratice )

projects ( what ever i do ,html ,audio, movie editing in subfolders and my smaller 
hobbywritings i place in here also al in their own subfolder)

samples (which is my audio samples and only on the computers i use for audio recording)

bin ( my shelscripts and gdm-themes and unofficial deb packages will go in here also if i should compile something from source i would place it here to begin with)




i started to think about how do others arrange  their home folder. 
i ask since i need some inspiration to as how it could be arranged in a more uniform but intuitive manner with out confusing certain programs that look for these ubuntu made fodlers such as music and video folders.  cheese and rythmbox as example does this.

---

### Post by smartboyathome on 2009-02-09
My folders are messy. I use general folders (Documents, Music, Packages, Pictures, Videos), then use other folders in and out. I keep track stuff via good file/folder names.

---

### Post by richg on 2009-02-09
I arrange them to suit me. Your mileage may vary. This not rocket science, just computer science. Don't make things more complicated then they have to be.

Rich

---

### Post by cardinals_fan on 2009-02-09
I keep most of my data on a separate partition, mounted as /data.  Inside that, I have the following directories: docs, music, photos, scripts, config, stuff.

Stuff contains vast amounts of superfluous junk.

Upper-case directory names should be used sparingly.

---

### Post by smartboyathome on 2009-02-09
> **cardinals_fan said:**
> Upper-case directory names should be used sparingly.

Upper case characters don't affect me since I use ZSH, and it can tell if a lower case letter should be upper case or vice versa. Plus, I don't mind using the shift key. :P

---

### Post by cardinals_fan on 2009-02-09
> **smartboyathome said:**
> Upper case characters don't affect me since I use ZSH, and it can tell if a lower case letter should be upper case or vice versa. Plus, I don't mind using the shift key. :P
I also use Zsh, but lowercase directories just seem simpler to me.  No more work than necessary :)

---

### Post by -grubby on 2009-02-09
I use a directory inside my home directory to store data, containing the following directories (each split into even more directories):

apps, backups, docs, links, media, programming, temp

> **cardinals_fan said:**
> I also use Zsh, but lowercase directories just seem simpler to me.  No more work than necessary :)

It also encourages consistency and makes tab-completion simpler.

---

### Post by markusf21 on 2009-02-09
keep it simple video pics thats about it

---

### Post by kk0sse54 on 2009-02-09
I share my home between two operating systems while I put all my data on an external with just the usual Music, Pictures, videos, Downloads etc etc along with the black hole called Misc. It's all just organized chaos :P

---

### Post by Sorivenul on 2009-02-09
My /home is fairly sparse, IMO...
doc, media, devel, trans

**doc:** 
important documents for work, paperwork, and personal writing
**media:**
media files (music, video, images), arranged into subfolders
**devel:**
current personal and professional programming projects i am working on
**trans:**
default Firefox download location, as I don't access my "Desktop", autocleaned on each mount (similar to /tmp)

---

### Post by steveneddy on 2009-02-09
I arrange them by the number of letters in the name of the folder.

---

### Post by dannytatom on 2009-02-10
Left a couple out for embarassment reasons ;)

```

[COLOR="DarkRed"]~/[/COLOR] ls
[COLOR="RoyalBlue"]audio  dev  documents  downloads  ebooks  heritage  images  torrents  videos[/COLOR]
[COLOR="DarkRed"]~/audio/[/COLOR] ls
[COLOR="RoyalBlue"]music  playlists  podcasts  radio[/COLOR]
[COLOR="DarkRed"]~/dev/[/COLOR] ls
[COLOR="RoyalBlue"]ruby  web design[/COLOR]
[COLOR="DarkRed"]~/downloads/ [/COLOR]ls
[COLOR="RoyalBlue"]distros  software[/COLOR]
[COLOR="DarkRed"]~/ebooks/[/COLOR] 
[COLOR="RoyalBlue"]historical  Mieville, China  misc[/COLOR]
[COLOR="DarkRed"]~/images/[/COLOR] ls
[COLOR="RoyalBlue"]*  *** ******  ***  me  misc  scrots  wallpapers[/COLOR]
[COLOR="DarkRed"]~/torrents/[/COLOR] ls
[COLOR="RoyalBlue"]distros[/COLOR]
[COLOR="DarkRed"]~/videos/[/COLOR] ls
[COLOR="RoyalBlue"]movies  television series[/COLOR]

```

---

### Post by cmay on 2009-02-10
thanks for the input. i just wonder why ubuntu creates all these folders when it installs and it recreates the same folders when you do a dist-upgrade. i never found out what they are for and i wonder if anyone even uses them. in crunch bang using open-box the folder layout is more simple but i still do not use them as they are as the default installtion creates them.  in debian you just create the ones you want or need and that i like the best.

---

### Post by notwen on 2009-02-10
I mount all of my storage folders/partition via NFS under /home.  Everything other than these generally ends up in a 'temp' folder on my Desktop.  Folders shared via NFS are 'Media' for audio/video files, 'FTP' for files currently available on my ftp and 'Keep' for personal/work related items.

---

### Post by SuperSonic4 on 2009-02-10
music, pictures and documents for backup reasons (they are on /media/music /media/pictures and /media/documents).

kmess_recevied for files sent over msn (I hate spaces in directories makes it harder to cd to it)

soundKonverter for converting audio files and $Artist for k3b rips

kmess for kmess and svn updating

---

### Post by mohitchawla on 2009-02-10
Bah ! I throw everything in /home, no organization whatsoever. Sometimes it gets terrible, but that's okay.

---

### Post by markp1989 on 2009-02-10
i have

IMG : which contains isos or images made using DD 
Pics: which contains pictures
Scripts: Contains Scripts 
Text: Contains Random notes in txt format

---

### Post by wolfen69 on 2009-02-10
i really never got into the home folder thing. just like i never used my documents, my music, etc. in windows. i just make a couple folders on my desktop (yeah, i know technically it's still in home) that i backup every 2 to 3 days. the only 2 things i care about in home is my .mozilla and .mozilla-thunderbird config files.

---

### Post by tommcd on 2009-02-11
Since I have several linux distros installed I use a /data partition for my stuff. I use a basic Music, Pictures, Info (various text files), and some other stuff. The other "stuff" is various tidbits of linux knowledge that I have picked up over the last 3.5 years. So I have directories named Ubuntu-stuff, Debian-stuff, Zenwalk-stuff, Slackware-stuff, etc.

One of the first things I do after installing Ubuntu is to delete the pre-installed Pictures, Documents, Music, etc folders that Ubuntu has set up *for me* in the /home directory. When I first started using Ubuntu (about 3.5 years ago) the home directory did not have those folders already set up. The home directory was blank (except for the .hidden files). I always thought that was just fine, since I could then set up home any way I wanted.
 I would be happier if the Ubuntu devs would not try to *decide for me* how my home directory should be set up!

---

### Post by cmay on 2009-02-11
> **tommcd said:**
> 
 I would be happier if the Ubuntu devs would not try to *decide for me* how my home directory should be set up!
i feel a bit the same way. but then again i used debian first.  the folders i do not understand the uses for are as example the public folder . i could very easy understand if they made a single folder with examples and  i actually would like that. 

i think its great with the examples in this default folder with some stuff to test out the video player and to print out the cover for the cd  but i delete it pretty fast anyway.

 if they could make a basic how to use ubuntu and stick in a folder that is created per default install instead of just emty folders with names that suggest predfined uses like public then i could see more of a point in it.

---

### Post by handy on 2009-02-11
The way I arrange the folders on my /home is so unimaginative that you would die of boredom because everyone said the same thing.

What I do, do, is copy them over to another partion on the same drive (which of course is not entirely safe) but where I may get slightly interesting, is that I also have a headless FreeNAS box which I only turn on (due to my environmental responsibilities;-)) when I need to use it.

So I copy everything across to the FreeNAS box.  

No one can rely on data being safe on a single machine, nomatter how many drives are involved.  I certainly feel better about my data if the backup machine is not even turned on! :-D

---

