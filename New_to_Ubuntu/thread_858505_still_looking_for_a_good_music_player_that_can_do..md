---
title: "still looking for a good music player that can do..."
date: 2008-07-13
forum: New to Ubuntu
---

### Post by kaston on 2008-07-13
after having tried the 3 big music players that i know of (banshee, amarok, rhythmbox), i have to say that itunes is still better than them all.  i currently am using amarok because i think it is the best of the 3 but i still have a list of things that i wish it could do (see below).  i'm hoping that someone can either suggest a tweak to amarok that i don't know about that can fix them or can suggest a new player that can do them.

- i want to be able to play songs in amarok by double clicking them instead of having to add to a playlist.  i want the itunes style browser where it lists all the songs i have and if i double click one it will immediately start playing instead of adding to a playlist.
- i can't easily add songs to an ipod playlist.  right clicking a song on my ipod and choosing add to playlist doesnt work for some reason
- amarok can't seem to handle podcasts
- if i delete all the songs from one artist in my "collection" in amarok, it only deletes the files from hard drive, but leaves the artist directory empty.  it would be nice if it got rid of the empty directory too (this isn't too big of a deal)
- ideally, i'd like to have 2 windows open simultaneously: one displaying what's on my ipod and one displaying what's in my music library so that i see what i have on each of them and can easily drag songs back and forth between them.  without this, it's hard to know if i already have a certain song in my ipod before i transfer it to my ipod from my computer or vice versa.

any help would be great

---

### Post by appi2012 on 2008-07-13
I'm not sure if it has what you want but you could try songbird:

[http://getsongbird.com/](http://getsongbird.com/)

---

### Post by ubuntu-freak on 2008-07-13
Have you tried Exaile? It's a GTK fork of Amarok, though. What I really think you should try is Songbird, it's in very early devolopement, but is similar to iTunes and uses the same engine as Firefox. You can even search for artists/songs within it and it will search the web for full tracks to listen to. Give it a try:
 
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)
 
I recommend the Pure White skin (feather), looks fantastic. If there is no application icon, just search Google Images for one, it's a Blackbird.
 
Edit: Actually, here is a download location with icons also:
 
[http://www.songbirdnest.com/download](http://www.songbirdnest.com/download)

---

### Post by kaston on 2008-07-13
alright, i'll give songbird a go.  is it pretty new?  all i ever hear about are the 3 that i mentioned

---

### Post by rossjman1 on 2008-07-13
Well I'm using Amarok, and while I don't know about your other points (I don't own an iPod), if you go to playlists > collection > all collection it lists all your music, and you can double click to play songs. This works just like iTunes (plus has a queue, which is always good). Also, there is a Podcasts folder in the playlist browser, so I'm assuming it works.

---

### Post by kaston on 2008-07-13
songbird doesn't seem to recognize my ipod (a problem i also had with banshee).  also, i don't like how it doesn't organize my music on my harddrive like itunes does.  i want to be able to change my directory structure (delete files, rename files) from within the player

---

### Post by Tim Sharitt on 2008-07-13
Have you tried Banshee 1.0? It is a complete rewrite from Banshee 0.13.2 in the Ubuntu repositories. 
Add the following to your sources.list
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
and install with
```
sudo apt-get install banshee-1
```

---

### Post by kk0sse54 on 2008-07-13
I've tried Banshee and for my large library it was way to buggy so now I'm using songbird. If you're used to using Winamp then songbird will be a breeze. As for recognizing your ipod did you make sure you installed the ipod plugin? As for re-organizing your file structure I would have to look at songbird to check since the OS I'm using right now doesn't have it installed yet but try checking out the extra add-ons and plugins that are available and see if there is something there to suit your needs. If you can't get your ipod working then I wouldn't be too surprised since it's still very new and I occasionally find bugs. Another alternative is to use other application to manage your ipod and music files and use songbird to play your media which can be a little bit of a pain. If you are still looking then I would recommend Exaile.

---

### Post by kaston on 2008-07-13
so this may be a dumb question but how do i start up songbird?  i ran it immediately after i installed it but now i can't find it in any of the menus and typing songbird in the command line didn't do anything.

i did install the ipod device support during installation of songbird.

---

### Post by kk0sse54 on 2008-07-13
Songbird doesn't have to be installed so it's files aren't where all the other program files are. In order to start it go to the songbird folder and just double click on the executable I thinks it's called songbird. In order to stick it to your menu just go into the menu editor click add new item and then browse for the executable as the command which to open it with.

---

### Post by ubuntu-freak on 2008-07-13
> **kaston said:**
> songbird doesn't seem to recognize my ipod (a problem i also had with banshee).  also, i don't like how it doesn't organize my music on my harddrive like itunes does.  i want to be able to change my directory structure (delete files, rename files) from within the player

 
I did say Songbird was in very early developement, it's not a proper release, it's a pre-release for developers and those who want to test it and help out. Also, as someone else pointed out, Songbird supports add-ons (just like Firefox), so it might be worth doing a search for suitable extensions.
 
Edit: There's deffinately an iPod extension. Have a look for a library organising-type extension as well. Keep an eye on Songbird, it seems like such a promising app.

---

### Post by kaston on 2008-07-13
there is actually a library organizer add on that i found.  but when i went to install it from within songbird it said that it's not compatible with my songbird!  i'm assuming this means linux versions

---

### Post by kk0sse54 on 2008-07-13
It could be although I have not had any troubles at all with installing any of my Add-ons. What was the add-on called? what release of Songbird did you download, nightly build or 0.6.1?

---

### Post by kaston on 2008-07-13
i installed 0.6.1.  it was the first "download here for free!" button that i found.  the add on is called songbird library organizer ([http://addons.songbirdnest.com/addon/8](http://addons.songbirdnest.com/addon/8))

---

### Post by ubuntu-freak on 2008-07-14
> **kaston said:**
> there is actually a library organizer add on that i found.  but when i went to install it from within songbird it said that it's not compatible with my songbird!  i'm assuming this means linux versions

 
I'm guessing the extension hasn't been updated for the latest version of Songbird. I had a similar problem with a Firefox extension, which I had to hack in order for it to install in FF3.

---

### Post by Paz13 on 2008-07-14
Whaaaat amarok is the king of music players i've never used a better player, the problem only with it is that it's made for kde i think and it runs a little slower than others. 
I skim read your points what you can do with amarok is just add all of your music to a collection either ipod, hard drive or a external 1 like me. it added all the songs to the collection and i just search a specific song or if i want to just randomise what i want then go to playlists and dynamic and it will create a simple playlist of 20 random songs and when you finsh listening to one it will replace with another i think it's a wikid idea, you could just copy you collection to the playlist it will take a while but you can click and play like you want but itunes is lame!

---

### Post by Ganael on 2008-07-14
Hi

I'm searching for a player with a search function which looks also in the name of my directories, not just in the details of the files, Winamp did so, but I gave up windows a month ago..^^

I've instaled songbird, Exail, etc.. and all of them just keep searching for artist, album, etc..  but I have a lot of mp3s whithout any information, just named trackX ..they are in directories named after the artist and the album..

thanks for any suggestions

---

### Post by ubuntu-freak on 2008-07-14
> **Ganael said:**
> Hi

I'm searching for a player with a search function which looks also in the name of my directories, not just in the details of the files, Winamp did so, but I gave up windows a month ago..^^

I've instaled songbird, Exail, etc.. and all of them just keep searching for artist, album, etc..  but I have a lot of mp3s whithout any information, just named trackX ..they are in directories named after the artist and the album..

thanks for any suggestions

 
Audacious can work with filenames and directories.

---

### Post by Ganael on 2008-07-14
humm, its not bad, but I miss the library ..and its a litle buggy :/

I think I'll try to find a way to rename my files :(

thank you for your help

---

### Post by K-D on 2008-07-15
Can Songbird play Mp4's?

Or does anyone know a programme that easily converts it into mp3.

The files looks as if it was originally saved as mp4 despite not being a video.

---

