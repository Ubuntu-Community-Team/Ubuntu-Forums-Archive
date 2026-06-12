---
title: "video conversion help"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Vyaas on 2008-08-26
I've taken the ubuntu plunge an i'm loving it!Over the last few weeks i've learnt a few things but not in great detail(so please excuse me for using the absolute beginner talk forum for this post)

I came across a neat script [here]("http://ubuntuforums.org/showthread.php?t=539398") for converting my videos to a zen compatible format.It works and I'm using it left and right!But...
Is there a way you can get it to convert an entire folder full of videos?If so...how?

I'd be forever grateful.

---

### Post by nicedude on 2008-08-26
Looks like a handy script, but the guy is using just "mencoder" with a bunch of settings for ZEN to do all that work. To make it do multiple files you would have to significantly modify his script to work multiple selected files at once and I am not sure how to do it, I have a feeling that the author of the script didn't want to spend that kind of time to figure it out or write it himself. I would suggest that if you want to do this that you will need to read up on bash scripting and try to figure out how to pass multiple files through the process.

HAVE A LOOK HERE & SCROLL DOWN TO MENCODER FRONTENDS & LOOK FOR ONES FOR GNOME
[http://www.mplayerhq.hu/design7/projects.html](http://www.mplayerhq.hu/design7/projects.html)

Using one of those would let you have a GUI based way to use mencoder and may or may not have any batch functionality.

Hope that helps

EDIT - I looked it up for you

Gmencoder which is a GUI frontend for mencoder has a batch option, here is the list of features and you can find it via the link I gave previosly
**20030613** - [gmencoder-0.1.0.tgz]("http://sourceforge.net/project/showfiles.php?group_id=77186")
							
[LIST]
[*] 									Added divx4linux/divx5linux encoding codec.
[*] 									Misc encoding options tab added. In this tab you can find output frames per second and output aspect ratio.
[*] 									Detected aspect ratio and length of the source is displayed and can be edited.
[*] 									Now you can choose the header of the output file (avi or mpeg).
[*] 									The size of the output file do not have to be a CD size. You can choose the one you want.
[*] 									Added a bach mode based in a queue. This way you can encode more than one source in one session.  <<---- THERE YA GO
[*] 									Config window added (yes, it has DVD/CD Device).
[*] 									MPlayer/MEncoder path detected in run time.
[*] 									Man page has been added thanks to [EMAIL="ben@tutuxclan.org"]Benjamin Zores[/EMAIL].  It is not installed automaticaly.
[*] 									I have started the TV source. It is planned network stream and (S)VCD as sources.
[*] 									Added gentoo linux ebuild file. Thanks to Raptor.
[/LIST]

---

### Post by Vyaas on 2008-08-26
Thanks for the link.But now I'm having problems installing.I get this at the end...

make  all-recursive
make[1]: Entering directory `/home/vyaas/Desktop/gmencoder-0.1.0'
Making all in src
make[2]: Entering directory `/home/vyaas/Desktop/gmencoder-0.1.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/vyaas/Desktop/gmencoder-0.1.0/src'
Making all in po
make[2]: Entering directory `/home/vyaas/Desktop/gmencoder-0.1.0/po'
make[2]: *** No rule to make target `esNONE', needed by `all-yes'.  Stop.
make[2]: Leaving directory `/home/vyaas/Desktop/gmencoder-0.1.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vyaas/Desktop/gmencoder-0.1.0'
make: *** [all-recursive-am] Error 2


what now?

---

### Post by whitethorn on 2008-08-26
I use ffmpeg to convert videos for my mp3 player.  There's a gui for it called WinFF, You can do batch converting with it.  

You can find it :

[http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60](http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60)

---

### Post by Vyaas on 2008-08-28
>Nicedude
Thanks for the search...but gmencoder just wasn't installing for me....hopefully someone reopens the project sometime soon.

>Whitehorn
THANKS!!!!Winff works well.I can now take a nap while my vids are being encoded!

Few pointers for those who might need some info on running they're zen on ubuntu.

>Winff is the best conversion software(gui) out there.It uses ffmpeg.
You've gotta download ffmpeg from medibuntu(the one in the ubuntu repositories is outdated for some reason).
>If you're having trouble with choosing the right format,get [this]("http://winff.org/forums/index.php?topic=187.0")
>You might have some a/v sync issues....just delete the frame-rate preset value and it should run smoothly.(i.e...don't meddle with the framerate!)
>.rm files don't convert very well on winff.Thankfully all my rm files are available as .flv on youtube...downloading replacements as I type.
>I use banshee 1.1 to sync my vids.And as for music....(drumroll)......AMAROK!!!
>You can use gnomad 2 too...but it's got a lousy interface.

I still haven't figured out how to use the sd card that came with the zen.My internal card reader doesn't seem to read it....oh well...you can't always get what you want!

---

