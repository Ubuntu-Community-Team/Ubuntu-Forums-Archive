---
title: "Help to play song as email notification!"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by mrdosa on 2008-08-27
Hi! I am using Xubuntu for sometime now. I have added "Mail Watcher" to the panel. I simply loved the application. And to impress my friends, I wanted to make the watcher notify a new mail with my fave song. In order to do that, I added the line "vlc /home/****/mymusic/letter.wav" to the blank next to "run on new messages"
The next time I got a mail, the song started. everything is fin, but I wanted to know a way in which, i could play the song without vlc being visible, and automatically close vlc after the song is played...it could be better if I could keep playing the song every 2 mins or so, until i click the icon.
Any help would be greatly appreciated.
Thanks a ton.
Mahi:guitar:

---

### Post by mcduck on 2008-08-28
You could try either mplayer instead of VLC, or some other command-line player.

Simple "play /path/to/yourfile.wav" should work.

---

### Post by mrdosa on 2008-08-28
I tried the play command. It worked great. Had down install sox, and some libraries I guess. But, is there any way, I can keep repeating the notification every 10 mins or so, till the mails are checked?

---

### Post by eightmillion on 2008-08-28
Try:
> mplayer /path/to/file

---

### Post by eightmillion on 2008-08-28
You should probably make sure you have mplayer installed too.

---

### Post by mrdosa on 2008-08-28
Well, its working. The one thing that would make it even more cooler would be to keep repeating the song, till the mails are checked. Is there any way I can do that?

---

### Post by mrdosa on 2008-08-28
I am quite new to writing scripts and all, but managed to write a file called loop.sh in mousepad.
with following text:
while :
do
play /home/mahi/Music/mail.mp3
sleep 1
done 

Saved it, and used chmod 755 to change it to executable..I guess..
Now, when a new mail arrives, the music loops, but i am not able to stop it! 
Can anyone make a better script?
In mail watcher, I get an option to run a command if I click the icon. Is there a way, by which I can run the script to loop on the arrival of a new message, and when i click the icon, run another command to stop that script running?
Can someone please help me out?
Thanks!!

---

### Post by Neural oD on 2008-10-29
hey - sorry for the late bump on this post - but thought it could be useful to others. I'm not that great at scripting - not yet anyway - but have a look at sleep - if you insert that into your script you should be good to go.
Have a look at the man pages for how sleep works


Cheers

---

