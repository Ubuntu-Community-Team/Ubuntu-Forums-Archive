---
title: "[SOLVED] Subtitles trouble AS.S/SRT"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Betziana on 2008-08-11
Okay, after googling and searching the forum like mad with no results I thought to register and ask. Not sure if this is the correct thread, but since I'm an idiot with Linux, I guess it is the right place to ask to get the reply in general English. 

So here is the problem: 
I like to watch anime. Nowadays AS.S/SRT subtitles are popular so they pop up a lot. And since it's anime, you might know that there is a lot of Notes. (eg. Note: Urashima Tarou is a story in which the protagonist jumps forward in time and finds no one he knew alive.)

Well, these notes are supposed to appear on the top of the video. But, on linux this doesn't happen. I've tried 3 players with different results. 

1) VLC Media Player: The note and the normal subtitle of what the character is saying appear on the movie simultaneously at the bottom. -> a big mess of which I wish you good luck digging what's being said and what's the note. Especially if the note is very long, and the replic is very long! 

2) Mplayer Movie Player: Only the note appears at the bottom of the video.

3) Movie Player: Only the replic appears at the bottom of the video. After the replic is gone, the note is shown for a fraction of a second so you have time to see there was text but not what it said. Sometimes notes and replics can come out as a big mess. Sometimes it is possible to separate these by playing the video at snail speed. But, I think it goes without saying it's not very enjoyable. 

I've tried all the settings one by one I dared to touch and could find, but no effect on this problem. 

Any suggestions? If you know another player that does them properly, please announce. 

The subtitles are sort of inside the file, you put them on by right-clicking the video and selecting subtitles and click if you wish to use track 1 AS.S or 2 SRT. I tried both. And this keeps repeating itself with different animes. On windows I heard there's something that makes them always work, but I'd like to watch with linux. 

P.S. Ignore the dot in AS.S.

---

### Post by ggaaron on 2008-08-11
mplayer has really many options (see it's manual) and I bet this can be done with it. I can't test it though as I don't have any such video files. Can they be downloaded from somewhere, as samples or anything? Then I would try to help.

---

### Post by shirilover on 2008-08-11
If you use an svn version of MPlayer (please note that MPlayer and Movie Player[totem] are very different), you should not have any problems with subtitles.

To use libass for rendering subtitles, you need to pass some arguments ( which, unfortunately, will be edited out by the forum software. You should get the idea.

```

mplayer -*** -embeddedfonts -vf ***,screenshot "filename.mkv"

```

An excellent howto build svn MPlayer can be found here -> [http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

---

### Post by Betziana on 2008-08-12
Uhh... well about the manual I tried to open Mplayer by opening the video, but instead I get an error. I swear I didn't do anything about it and actually already yesterday evening it suddenly refused to play any of my videos - I tried several. I was hoping it to pass but it didn't.. 

"Fatal Error!

Error opening/initializing the selected video_out (-vo) device." 

I don't get it. So I thought of looking the manual from somewhere there. Anyway I didn't find it. Where can I perhaps find this manual and what does it do? And I don't think there's any samples, you need to load a whole full episode. The most disturbing this trouble has been to me with Clannad because in the last real episode there's a song and the **** lyrics come on top of the replics.. Episode 22 by SS_Eclipse, if you want to try. 

Shirilover, what's this code thing...? I've never used the black window, the one that looks like a hole, I believe it's called terminal.. So step by step instructions on that please :D I'll try that Howto thing you linked then.

---

### Post by Betziana on 2008-08-12
Uh oh.. that Howto you linked Shirilover says it's more for advanced users and those who like the black hole command thing. I don't think I should poke the bomb...

Well I try the link then which he had linked and the newer version of it.

---

### Post by Betziana on 2008-08-12
Well, even that guide from the link of the link you pasted, I only resulted with gray hair. The author completely forgets about Ubuntu at some point and then anyway even that is way above my level. I can't simply modify anything or put in right form, I can hardly copy/paste stuff in Terminal. 

Is there any key to this problem I'm having even a total idiot can handle?

I feel as stupid as a rubberboot. :'<

---

### Post by iv2101 on 2008-08-12
I never watched anime but maybe this would help. In vlc you can change the placement of the subtitles (find it under preferences). You can further customize the output.

---

### Post by shirilover on 2008-08-12
> **iv2101 said:**
> I never watched anime but maybe this would help. In vlc you can change the placement of the subtitles (find it under preferences). You can further customize the output.

That would be fine, but VLC totally fails at rendering styled subtitles. In fact, many subbing groups go out of there way to make sure that you don't get to see the subtitles if you use VLC.

[QUOTE=Betziana]Error opening/initializing the selected video_out (-vo) device.[/QUOTE]

OK. let's try this instead.
Open the GUI MPlayer from the menu.
Right-click on the player interface and choose 'Preferences'.
Select the video tab, and choose xv from the list.
Select the Subtitles/OSS tab and place a check in the box 'Use SSA/*** library to render subtitles'

Keep in mind that the XVideo overlay and compiz/desktop effects do not play well together. I suggest disabling desktop effect while playing video.

Another option is to use SMplayer, which is an excellent GUI front-end for MPlayer.

---

### Post by Betziana on 2008-08-12
Okay I try that immediately I unstuck my computer.

---

### Post by Betziana on 2008-08-13
Thank you, thank you so much!! It works properly now. It's pretty big font but it is bearable. After all, it is AS.S, but most important, it is readable!

---

