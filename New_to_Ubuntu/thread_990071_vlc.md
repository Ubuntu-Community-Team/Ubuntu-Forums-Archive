---
title: "vlc"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-22
the new vlc media player that comes with intrepid is a bit annoying.while making a playlist,how do i select multiple files,i mean i am supposed to click a file,press Ctrl,and then click all the files i want,then release Ctrl,and click open.But,in the new one,a single click opens the file,but then how do i select multiple files to be opened i.e loaded into the playlist?

---

### Post by shifty_powers on 2008-11-22
not in mine.

are you using kubuntu by any chance?

---

### Post by stonecoldjha on 2008-11-22
i have got KDE 4.1 installed,but this thing happened whwn i was in a gnome session.

---

### Post by stonecoldjha on 2008-11-22
nyone dere to help me out?

---

### Post by stonecoldjha on 2008-11-22
i have been a linux user for the past 8 months,and i can say that linux does have a wide range of players.But,none of them worth using.i wanted to compile a playlist in vlc,but could not,because of that.i tried doing that in kaffeine,but it could not play my files,then i added the medibuntu repo and installed win32 codecs,but still kaffeine failed me.now,i have to log into windows to listen to the music since at the moment i do not have much time to get the job done in linux, 'coz i have got an exam in two days.
its frustrating.

---

### Post by stonecoldjha on 2008-11-22
why does the open source community not develop a player that is as good as something like GOM player?there are a lot of players,that do not serve a purpose.amarok is a nice music player,but can't play my video songs and some audio formats.with mplayer i have difficulty playing HD.with VLC,it is difficult to advance the file(when you seek ahead,the video gets distorted and takes some seconds to stabilise),banshee again doesn't play any video.

---

### Post by irish66 on 2008-11-22
okay i don't know if this would work or not. I'm in windows at the moment.
1. go into Krusader. I think it has a option
to copy the name and path of a file. if it doesn't, you could install total commander in windows, or if you know how to in linux, run it through wine, and then highlight the files you want to listen to, create an empy playlist file,
copy the names and paths of the stuff you wish to play. save it, right click, and choose to open in
vlc.    

2. you could use winamp through wine to play the the playlist.

---

### Post by stonecoldjha on 2008-11-22
anyone there to help me out?

---

### Post by Mr_JMM on 2008-11-22
Stop bumping the thread every few minutes.

It annoys me, and it will annoy a lot of other people. If you read the rules of the forum then you will see that bumping a thread is acceptable about once every 24 hours.

You will be answered when someone knows the answer assuming you don't alienate yourself first.

Yes, I appreciate the irony that this post will bump your thread. That one you can have for free.

---

### Post by stonecoldjha on 2008-11-22
first of all,i hate windows,wine,winamp and all that jazz.i hate logging into windows,i don't remember when i last did that.but its true that with so much unsettled, linux may never be able to take on mac or windows.
so much of sofware all around,but not a surprise if you come across a good number of them that just do not work as one would expect them to.and may be this is the reason why we linux users are ditched everytime,we are not in the mainstream,be it DirectX,gmail video chat,google chrome,a nice video player like GOM player,kmplayer,mplayer(now i am not gonna buy on the **** that they are there for linux too,i mean its not even half as good as the one for windows) and now silverlight.

i hope all this does not annoy you,and if it does i am sorry,truth does hurt,it hurts me too,but at the same time i can't give up linux,i love linux and linux loves me.

a couple of moments ago,i refreshed the page to see if any angel was there to save me,but,alas,an admonition.
i am sorry to have annoyed you.

---

### Post by stonecoldjha on 2008-11-22
and one more thing,winamp does not work through wine.

---

### Post by ellgor on 2008-11-22
Hi,

Haven't got a fix as such, but I know exactly what you mean, Vlc used to be great now your'e lucky if it will play anything all the way through, I digress. Go to the Vlc site and download an earlier version (this is assuming you know how to install packages yourself) uninstall the current Vlc load in the file you downloaded and away you go, this is what I did and incidentally, Kpackage, aka Adept, you might have seen some posts on that as well, I have done the same with that, hope this is of use.

Regards, Ellgor.

---

### Post by stonecoldjha on 2008-11-22
thanks Ellgor for replying,but i really do not know how to install things that way.is there a .deb or .rpm available for vlc?i think,it is not.

---

### Post by stonecoldjha on 2008-11-23
no one there facing this problem?is there no solution to the problem?how can i make vlc open files on doble-click instead of a single-click?

---

### Post by mbsullivan on 2008-11-23
Hi stonecoldjha,

I think the sparsity of responses may be due to the fact that other people aren't having the same problem. Shift+click for opening multiple files works fine for me.

> and one more thing,winamp does not work through wine. 

No reason to try winamp through wine... there are winamp replacements in Linux. Audacious and xmms (the original, not 2) both come to mind.

> how can i make vlc open files on doble-click instead of a single-click?

Do you mean through the VLC file search dialog, or under Konquerer? Again, for both VLC and Nautilus (I'm not using KDE) the default is double click, so I cannot reproduce your problem.

Mike

---

### Post by stonecoldjha on 2008-11-23
i am not talking of the konqueror,but vlc.
Pressing shift and selecting multiple files doesn't work,because the moment a file is clicked(no matter whether shift is pressed)it is opened.moreover,it only happened to me n the new vlc that comes for intrepid.

---

### Post by stonecoldjha on 2008-11-23
can audacious and xmms play my video songs,of a number of codecs?

---

### Post by mbsullivan on 2008-11-23
> 
i am not talking of the konqueror,but vlc.
Pressing shift and selecting multiple files doesn't work,because the moment a file is clicked(no matter whether shift is pressed)it is opened.moreover,it only happened to me n the new vlc that comes for intrepid.

I dunno... I have the version that comes with Intrepid, and it works fine for me. The behavior is not how you describe.

> can audacious and xmms play my video songs,of a number of codecs? 

Nope... I generally use VLC to play videos, and a different player to manage music playlists.

> 
thanks Ellgor for replying,but i really do not know how to install things that way.is there a .deb or .rpm available for vlc?i think,it is not.

If you really wanted, it would be possible to downgrade your VLC to a previous version in the Ubuntu repositories through [apt-pinning]("http://jaqque.sbih.org/kplug/apt-pinning.html") or through the package->lock version functionality of Synaptic. 

Mike

---

### Post by laurielegit on 2008-11-23
stonecoldjha can you *please* stop posting multiple times in succsesion. I was interested in your problem when I first read it but now I see that you are unable to post more than one point per post I think people should stop helping you. Unless you are able to gather your thoughts and put several points in one post, please learn how to use the edit button.

---

### Post by stonecoldjha on 2008-11-23
sorry for that,but is that the reason why you did not help m.OK,i'll stop doing that,and see if people help me now.so far,no help.

---

### Post by stonecoldjha on 2008-11-23
how do i delete a thread?i want to delete this thread.

---

### Post by stonecoldjha on 2008-11-23
plese tell me how do i delete this thread?

---

