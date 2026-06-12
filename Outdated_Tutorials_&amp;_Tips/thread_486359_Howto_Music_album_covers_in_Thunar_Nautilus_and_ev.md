---
title: "Howto: Music album covers in Thunar Nautilus and everywhere!"
date: 2007-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Yuzem on 2007-06-27
**INTRODUCTION**

This began as a tiny script and now I have a lot of ideas for it.
If you just want to know what is this about then take a look at the screen shots:

Thunar (CD theme):
[[IMG]http://img209.imageshack.us/img209/1/pantallazo10ax2.th.jpg[/IMG]](http://img209.imageshack.us/my.php?image=pantallazo10ax2.jpg)

**This is Nautilus with some vinyls (I can only post 8 images):**
[http://img176.imageshack.us/my.php?image=pantallazo06kr3.jpg](http://img176.imageshack.us/my.php?image=pantallazo06kr3.jpg)

The DVD theme is used by the imdb grabber (for firefox bookmarks) and the film grabber (for video files)
Nautilus with a custom background:
[[IMG]http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.th.png[/IMG]](http://img379.imageshack.us/my.php?image=avatarfactoryfg3lk3.png)

Nautilus again (picture avatars and photo theme) :
[[IMG]http://img178.imageshack.us/img178/411/pictureavatarssd8.th.png[/IMG]](http://img178.imageshack.us/my.php?image=pictureavatarssd8.png)

YouTube Avatars
[[IMG]http://img360.imageshack.us/img360/4616/avatarfactoryyoutubeax3.th.jpg[/IMG]](http://img360.imageshack.us/my.php?image=avatarfactoryyoutubeax3.jpg)

tv-show grabber:
[[IMG]http://img518.imageshack.us/img518/8694/avatarfactorytvshowwx8.th.png[/IMG]](http://img518.imageshack.us/my.php?image=avatarfactorytvshowwx8.png)

The music widget (support drag and drop):
[[IMG]http://img374.imageshack.us/img374/8009/musicwidgetkr4.th.jpg[/IMG]](http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg)

mame Avatars in nautilus:
[[IMG]http://img165.imageshack.us/img165/5421/mameavatarsop9.th.jpg[/IMG]](http://img165.imageshack.us/my.php?image=mameavatarsop9.jpg)

comic Avatars:
They can be bookmarked as shown on the screenshot:
[[IMG]http://img163.imageshack.us/img163/8576/comicavatarsbk3.th.jpg[/IMG]](http://img163.imageshack.us/my.php?image=comicavatarsbk3.jpg)

**DESCRIPTION**

Avatar Factory is a bash script that creates shortcuts (Desktop Entry files) with eye candy icons that represent music albums, photo albums, DVD films, youtube videos, mame roms and more. When clicked the avatars can perform different actions as launching a video, start playing some music (compatible with many music players), open a folder, etc...
They can be viewed in Nautilus, Thunar or any application that support Desktop Entry files.

**BEFORE INSTALL**

I have to say that I don't have any previous knowledge about programing. I have learned most of what I know by doing this script. If something is implemented in an inconvenient way just tell me. I am really a beginner at this.

Check this post to see what a newbie I am:
[http://ubuntuforums.org/showthread.php?t=460259](http://ubuntuforums.org/showthread.php?t=460259)

Thanks to the people there for helping me out with some very basic things.

**INSTALLATION**

You can install it from the deb or the rpm package
If you prefer to install it  from the tar file follow the instructions in the README.
[**_[COLOR="Red"]Download (gnomefiles)[/COLOR]_**]("http://www.gnomefiles.org/app.php/Avatar_Factory")

**USAGE**

You can use the graphic interface (zenity) from the applications menu but it is much more powerful to use the command line.

**From the command line:**

For instructions type:
```
man avatar-factory
```

For grabbers specific instructions and description type:
```
avatar-factory -g grabber_name --help
```

To get a list of available grabbers:
```
avatar-factory -lg
```

**Automatic cover download (for the music grabber)**

You can check this posts about mass grabbing covers directly to the correct folders:
[Album Cover Art Downloader]("http://ubuntuforums.org/showpost.php?p=3266072&postcount=50")
[Sonata]("http://ubuntuforums.org/showpost.php?p=3332652&postcount=136")
[exaile-cover-mover]("http://ubuntuforums.org/showpost.php?p=4401335&postcount=379")

---

### Post by Bossieman on 2007-06-29
Really nice work. 
But there is some problems. The first one is that when I change the player to Amarok it wont play them. A error message in Amarok saying the file is not supported/readable or something like that.
Is there anyway you can make this script open upp the folder with the album when you dubbelklick the albums? That would be very sweet. 
The skript crashed when I sat the path to my whole harddrive. Worked fine when I specified the folder with the music.

---

### Post by Yuzem on 2007-06-29
Yes, you can make it open up the folder, add to the following to the command:
```
--type 0
```
I don't know why it crashed. Right now the script does not detect if a folder has music inside. It will make an album for every folder with a jpg or a png picture inside.
It is better right now to point it to your music folder.

---

### Post by edmondt on 2007-06-29
That looks so cool!

---

### Post by Bossieman on 2007-06-29
> **Yuzem said:**
> Yes, you can make it open up the folder, add to the following to the command:
```
--type 0
```
I don't know why it crashed. Right now the script does not detect if a folder has music inside. It will make an album for every folder with a jpg or a png picture inside.
It is better right now to point it to your music folder.


Very nice, thank yoy! This is awsome! :popcorn:

---

### Post by MetalMusicAddict on 2007-06-29
Ok so does this work recursively and does on work on any folder structure?

ie: **/artist/album/image.jpg?**

---

### Post by MetalMusicAddict on 2007-06-29
Ok. Looking into this further I know realize this does NOT make your folders for your music look like the covers contained inside. Kinda like XP can do with the image inside.

I wonder if there's a way to adapt this to do that?:-k

Don't get me wrong. This is still cool. Just not what I was expecting.

---

### Post by Yuzem on 2007-06-29
You can use the "--type 0" option to make it go inside the folder when you clic on the albums.

---

### Post by schnupi on 2007-06-29
love it! really good thanks! my avatar-launcher was in /usr/local/bin btw

pity exaile doesnt work with it but im really impressed with the whole thing

---

### Post by Yuzem on 2007-06-29
There is a new version:
Now it should work with exaile and it should be easier to configure amarok and M.O.C.

You must set them in the configuration file:
```
gedit ~/.avatar-factory/avatar-launcher
```

For moc:
(this will clear the current playlist)
```
music=mocp
```
For exaile:
```
music=exaile
```
For amarok:
(this will clear the current playlist)
```
music=amarok
```

---

### Post by Yuzem on 2007-06-29
> **schnupi said:**
> love it! really good thanks! my avatar-launcher was in /usr/local/bin btw

pity exaile doesnt work with it but im really impressed with the whole thing

Ahh thats not the configuration file. If you set the options there they will be overwritten every time you update the script.
The configuration file is: ~/.avatar-factory/avatar-launcher
If it doesn't exist, create it.

---

### Post by schnupi on 2007-06-30
oopsy:oops:.. never thought of that, thanks!:-\"

---

### Post by Bossieman on 2007-06-30
Amazing work really. I have a request for a future release.
I use the option --type 0 and its awsome, but when i enter a album and hit back in nautilus I get back to the folder with my albums, not the folder where the pictures are. Is it possible to make it work that way?

---

### Post by Yuzem on 2007-06-30
You should use the up button (alt+up)

---

### Post by Bossieman on 2007-07-01
> **Yuzem said:**
> You should use the up button (alt+up)

That doesnt work. Still the same. I end up in my music-album-folder.

---

### Post by andrek on 2007-07-01
Looks REALLY great, but could you make it work with mpd and sonata ( mpd client ) ?

---

### Post by djdp on 2007-07-01
It would be cool if the cd cover removed itself from the desktop if you exit the music player.
Nonetheless great work!

---

### Post by Yuzem on 2007-07-01
> **Bossieman said:**
> That doesnt work. Still the same. I end up in my music-album-folder.

Thats really strange.

Maybe I am not understanding:

you are in ~/pretty-covers
you clic on mysteriousAlbum
then you are in ~/Music/mysteriousCategory/mysteriousAlbum
If you hit the back button it should send you to ~/pretty-covers
The up button (the third button from the left) should send you to ~/Music/mysteriousCategory/

If the up button is sending you to ~/pretty-covers then I really have no clue about that.
Could it be a Nautilus bug? :(

> **andrek said:**
> Looks REALLY great, but could you make it work with mpd and sonata ( mpd client ) ?

Thanks. mpd and sonata support in the next version

> **djdp said:**
> It would be cool if the cd cover removed itself from the desktop if you exit the music player.
Nonetheless great work!

I will see what I can do. Thanks.

---

### Post by Bossieman on 2007-07-01
My bad, it workes with back #-o

---

### Post by cwood06 on 2007-07-02
is there a way to make it just make the folder icon the avatar install of having the avatar picture for a .m3u list? i know i can do manually but i got a huge libarry of music

made a small script 

```
gedit ~/.gnome2/nautilus-scripts/avatar-factory
```

then insert

```


avatar-factory -mg . .


```

. stands for the current folder you are in with nautilst

so it will create the image and create the playlist for you saves alot of typing

not sure if its aoutmatic right click then scripts, might be just me and whyone else who installed the nautilist scripts from automatix
[IMG]http://s26.photobucket.com/albums/c143/cwood06/th_myalbums2.png[/IMG]
[http://s26.photobucket.com/albums/c143/cwood06/myalbums2.png](http://s26.photobucket.com/albums/c143/cwood06/myalbums2.png)

---

### Post by Bossieman on 2007-07-02
Anyway to change the size of the pictures? :popcorn:

---

### Post by Yuzem on 2007-07-02
> **cwood06 said:**
> is there a way to make it just make the folder icon the avatar install of having the avatar picture for a .m3u list? i know i can do manually but i got a huge libarry of music

made a small script 

```
gedit ~/.gnome2/nautilus-scripts/avatar-factory
```

then insert

```


avatar-factory -mg . .


```

. stands for the current folder you are in with nautilst

so it will create the image and create the playlist for you saves alot of typing

not sure if its aoutmatic right click then scripts, might be just me and whyone else who installed the nautilist scripts from automatix
[IMG]http://s26.photobucket.com/albums/c143/cwood06/th_myalbums2.png[/IMG]
[http://s26.photobucket.com/albums/c143/cwood06/myalbums2.png](http://s26.photobucket.com/albums/c143/cwood06/myalbums2.png)

I think that I don't understand you (me english doesn't help me much)
The script works on folders. You want it to work on .m3u lists?
Or you want a script for nautilus so you don't have to type the commands....?

> **Bossieman said:**
> Anyway to change the size of the pictures? :popcorn:
In Nautilus or Thunar press: ctrl and + or ctrl and -

---

### Post by cwood06 on 2007-07-02
i want it to change the folder image to the png that avatart factory makes instead of having a .m3u

---

### Post by Yuzem on 2007-07-02
Avatar-Factory doesn't create any m3u file. Drag an avatar to gedit and you will see that they are not m3u files.

Changing the folder icon is out of the scope of this application and the principal problem in doing that is that it would be only compatible with nautilus plus no desktop widget, no flat view, no clic and play, no stars ratings (I would have to adapt them) etc...

I understand that it isn't very practical right now but I will implement tools to automatically add new albums, sort them, fix broken albums etc...

Sorry but right now I have no plans to implement that feature.

If someone else wants to contribute by doing it himself, I will include it.

---

### Post by Yuzem on 2007-07-05
New version:

05.07.07------0.1.5
[INDENT]+Added support for mpd (music player daemon)
	+Added support for muine
	+Added support for quodlibet
	+avatar-music-widget (automatically show/hide the album widget)
	+Existing avatar won't be overwritten (now you can scan the whole music dir for new albums)
	+Minor internal changes[/INDENT]

mpd users: read "MPD INSTRUCTIONS"

---

### Post by Bossieman on 2007-07-07
Tried the latest version and it worked like a charm. Thanks.

---

### Post by andrek on 2007-07-07
Thanks for the mpd support, will try it.

edit:
I did 'avatar-factory -mg /var/lib/mpd/music/mp3 /home/andrzej/Albums' and it actually works. BUT : when i try to open an album cover, it plays songs in totem, not mpd.

---

### Post by Yuzem on 2007-07-07
```
gedit ~/.avatar-factory/avatar-launcher
```
Insert or change your player and save it:
```
music="mpd"
```

If you want to use avatar-music-widget to automatically show hide the desktop widget then insert the client name.
Example:
```
music="sonata"
```

Right now the supported mpd clients (to automatically show hide the widget) are:
sonata
pygmy
ncmpc
gmpc

---

### Post by djdp on 2007-07-08
The music widget doesn't hide it self when i close the music player :(

---

### Post by Yuzem on 2007-07-09
avatar-music-widget must be running to automatically show hide the widget.
Type alt+F2 and insert:
```
avatar-music-widget
```

---

### Post by Washington Irving on 2007-07-12
I followed the instructions but it hasn't made a difference. The script went through all of the folders and made images in ~./albums which is the folder I specified but they don't show up in thunar or nautilus. Have I missed something?

---

### Post by Yuzem on 2007-07-12
> **Washington Irving said:**
> made images in ~./albums
That dot there is very strange...
The images or icons should be in:
~/.avatar-factory/icons/cd/
or
~/.avatar-factory/icons/vinyl/

Now if you see images in:
~/.albums
If that is the folder you specified then those are not images. Those are the albums.
The script does not change folder icons, it creates a flat view of all your albums in a different location.

---

### Post by Washington Irving on 2007-07-12
Ah yes, my mistake, I meant:
~/.albums
I also misunderstood the nature of the script.
Thanks for your help.

---

### Post by Washington Irving on 2007-07-12
Please disregard this post.

EDIT: I accidentally double posted.

---

### Post by swede_hac on 2007-08-02
I am dying for updates on this, im wondering how can I make my albums sort by artist name?

and again a great script!

---

### Post by Yuzem on 2007-08-02
Thanks. Is nice to know that someone is waiting for a new version.
I think that I will have a new version ready for the next week.

Regarding your question, the avatars don't hold any information about the artist.
What you can do is sort them by folder structure and if your folder structure have artist info then it should be very similar to sort by artist.

Folder structure example:
~/music/artist1/album1
~/music/artist1/album2
~/music/artist1/album3
~/music/artist2/album1
etc...

or:
~/music/artist1 - album1
~/music/artist1 - album2
~/music/artist1 - album3
~/music/artist2 - album1

To sort by folder structure use the default option for name (do not set any) or use option 1 (--name 1) and sort by name in nautilus, thunar or any other.

---

### Post by swede_hac on 2007-08-03
It should work, but I dont want to show foldernames under the icons, and nautilus doesnt sort them properly, I will try one of your commands.


aha it seems like the script sorts them by creation dates of the folders now i have like


/Mpr/Artist/Album

And the first album i put in there is first in my "album-cover" folder

---

### Post by Yuzem on 2007-08-11
Here it is the new version:

12.08.07------0.1.9
[INDENT]+index number will reflect better the real number when adding new avatars.
	+existing icons won't be overwritten (If you delete your avatars it will be much faster to create them again)
	+"-f" option to force icon overwrite.
	+dvd theme
	+film grabber[/INDENT]

The film grabber isn't finish and it will only work for imdb firefox bookmarks.
The first post has been updated with a new screenshot and usage instructions for the film grabber. In the future it will be able to make avatars for launching video files.

Another version is coming soon...

If you like the film grabber I had made another script for movies:
[http://ubuntuforums.org/showthread.php?p=3154074#post3154074](http://ubuntuforums.org/showthread.php?p=3154074#post3154074)

---

### Post by isaacj87 on 2007-08-13
I have a question...I have all the album covers downloaded...amarok did it for me, but each album cover is not in each folder! Is there any way to get amarok to redownload covers and put them in each separate folder? or maybe banshee?

---

### Post by Yuzem on 2007-08-13
I don't know but my guess is that they can't do that.
You can try other programs for that:
[Album Cover Art Downloader]("http://album-cover-art-downloader.en.softonic.com/")
It is for windows but it works with wine. In Configuration window > Targets > mp3 files Uncheck enable if you don't want that to happen.

Another:
[CoverDownloader]("http://www.hydrogenaudio.org/forums/index.php?showtopic=43429&pid=381964&mode=threaded&show=&st=&")

---

### Post by ayoli on 2007-08-15
> **Yuzem said:**
> I don't know but my guess is that they can't do that.
You can try other programs for that:
[Album Cover Art Downloader]("http://album-cover-art-downloader.en.softonic.com/")
It is for windows but it works with wine. In Configuration window > Targets > mp3 files Uncheck enable if you don't want that to happen.

Another:
[CoverDownloader]("http://www.hydrogenaudio.org/forums/index.php?showtopic=43429&pid=381964&mode=threaded&show=&st=&")

i hvaen't try already but there is also this:
[http://ubuntuforums.org/showthread.php?p=2809331#post2809331](http://ubuntuforums.org/showthread.php?p=2809331#post2809331)

---

### Post by searayman on 2007-08-27
i get this error:

mike@mike-desktop:~$ avatar-factory -mg music musictest
Building list of folders to process...
There is no cover for music
There is no cover for Audioslave
There is no cover for Steve Vai
There is no cover for U2
There is no cover for Van Halen
There is no cover for AC_DC
There is no cover for Back In Black (Disc 1)
There is no cover for Highway To Hell (Disc 1)
There is no cover for John Mayer
There is no cover for Billy Joel
There is no cover for Piano Man (Disc 1)
There is no cover for Blues Traveler
There is no cover for Travelogue_ Blues Traveler Classics
There is no cover for Dispatch
There is no cover for FrDocious
There is no cover for Greenday
There is no cover for American Idiot
There is no cover for O.A.R
There is no cover for 34th & 8th
There is no cover for Souls Aflame
There is no cover for Stories of a Stranger
There is no cover for Ryan Montblue
There is no cover for Jet
There is no cover for Queen
There is no cover for Led Zeppelin
There is no cover for Silvertide
There is no cover for Show & Tell
There is no cover for Maroon 5
There is no cover for Rascal Flatts
There is no cover for Feels Like Today (Disc 1)
There is no cover for FrDocious
There is no cover for Red Hot Chili Peppers
There is no cover for Stadium Arcadium - JUPITER (Disc 1)
There is no cover for cover art
mike@mike-desktop:~$  avatar-factory -mg music musictest
Building list of folders to process...
There is no cover for music
There is no cover for Audioslave
There is no cover for Steve Vai
There is no cover for U2
There is no cover for Van Halen
There is no cover for AC_DC
There is no cover for Back In Black (Disc 1)
There is no cover for Highway To Hell (Disc 1)
There is no cover for John Mayer
There is no cover for Billy Joel
There is no cover for Piano Man (Disc 1)
There is no cover for Blues Traveler
There is no cover for Travelogue_ Blues Traveler Classics
There is no cover for Dispatch
There is no cover for FrDocious
There is no cover for Greenday
There is no cover for American Idiot
There is no cover for O.A.R
There is no cover for 34th & 8th
There is no cover for Souls Aflame
There is no cover for Stories of a Stranger
There is no cover for Ryan Montblue
There is no cover for Jet
There is no cover for Queen
There is no cover for Led Zeppelin
There is no cover for Silvertide
There is no cover for Show & Tell
There is no cover for Maroon 5
There is no cover for Rascal Flatts
There is no cover for Feels Like Today (Disc 1)
There is no cover for FrDocious
There is no cover for Red Hot Chili Peppers
There is no cover for Stadium Arcadium - JUPITER (Disc 1)
There is no cover for cover art
identify: TokenLengthExceedsLimit `/home/mike/music/covers/1c0facec9c4cf05020cf755f81fe3864.jpg
/home/mike/music/covers/4a40e278257dfc5a745fcc045342c5f8.jpg
/home/mike/music/covers/05cb615cf8ba496c6f2c6918eb1f25ef.jpg
/home/mike/music/covers/6c6591834fd40903658c7966b6cb0393.jpg
/home/mike/music/covers/8b09fcb7edfa1aa585904ab67ba40ae4.jpg
/home/mike/music/covers/9d3977f520bdc74e054331bc9d6ebaf7.jpg
/home/mike/music/covers/9e875cda14dc1d4d73413004eebc1bd3.jpg
/home/mike/music/covers/012fdf6487acd682eddc8d3debdc4eac.jpg
/home/mike/music/covers/28f287fc12f4028bebd43048501e02f2.jpg
/home/mike/music/covers/35c680106dba364c1d0b3910af904d98.jpg
/home/mike/music/covers/038f00991df75a44a53607ffedd72bde.jpg
/home/mike/music/covers/64b24b1461747d8832f0a8b896d2e49d.jpg
/home/mike/music/covers/424bc2394c71ae38f151dfa3046aa8f5.jpg
/home/mike/music/covers/529df7221b38ca46cb0921a885658f43.jpg
/home/mike/music/covers/537a4b745758bb930982ff58172cb47a.jpg
/home/mike/music/covers/3662acc2310e9d1b47866f3ff1025376.jpg
/home/mike/music/covers/5439f748b6b6cb7265d13f9dbe4905a1.jpg
/home/mike/music/covers/6913b2f4809b4087ed246ad61ccc25ca.jpg
/home/mike/music/covers/642651a96ffd14b97de5594bc2a920d7.jpg
/home/mike/music/covers/58566327cd70bca0df04781190e09d55.jpg
/home/mike/music/covers/208138004869cfc67bfc0206cfaff47a.jpg
/home/mike/music/covers/035002826953711fe075a0bc3786ed3f.jpg
/home/mike/music/covers/a409c69ed123b9c0c23a0d1557c1e93b.jpg
/home/mike/music/covers/a56936337e7254e11d24f7d561d06dc9.jpg
/home/mike/music/covers/bf65789f52b77c303d464f6a524781d0.jpg
/home/mike/music/covers/c2aa5b9a9c26024cbb498645efee50a3.jpg
/home/mike/music/covers/c6ac890b10573720672dd318244a321b.jpg
/home/mike/music/covers/d6dcbb4369713223e241b9ef240d258a.jpg
/home/mike/music/covers/d968f7d4eb44cf83bb49ee6615a63157.jpg
/home/mike/music/covers/ed1981aae2869f0910e82c14acde3f47.jpg
/home/mike/music/covers/f05dffa148d28e0bcd33d81d862cf602.jpg
/home/mike/music/covers/f32b3e575bdc8be170a2a3a9cfe8872b.jpg
/home/mike/music/covers/fcbe0872344f43a7ba2c52f48581d5e1.jpg
/home/mike/music/covers/fda2a17f7147e93aced77cc72472d6f8.jpg
/home/mike/music/covers/fe0336e95c7c52687b627153d891ebc1.jpg'.
identify: TokenLengthExceedsLimit `/home/mike/music/covers/1c0facec9c4cf05020cf755f81fe3864.jpg
/home/mike/music/covers/4a40e278257dfc5a745fcc045342c5f8.jpg
/home/mike/music/covers/05cb615cf8ba496c6f2c6918eb1f25ef.jpg
/home/mike/music/covers/6c6591834fd40903658c7966b6cb0393.jpg
/home/mike/music/covers/8b09fcb7edfa1aa585904ab67ba40ae4.jpg
/home/mike/music/covers/9d3977f520bdc74e054331bc9d6ebaf7.jpg
/home/mike/music/covers/9e875cda14dc1d4d73413004eebc1bd3.jpg
/home/mike/music/covers/012fdf6487acd682eddc8d3debdc4eac.jpg
/home/mike/music/covers/28f287fc12f4028bebd43048501e02f2.jpg
/home/mike/music/covers/35c680106dba364c1d0b3910af904d98.jpg
/home/mike/music/covers/038f00991df75a44a53607ffedd72bde.jpg
/home/mike/music/covers/64b24b1461747d8832f0a8b896d2e49d.jpg
/home/mike/music/covers/424bc2394c71ae38f151dfa3046aa8f5.jpg
/home/mike/music/covers/529df7221b38ca46cb0921a885658f43.jpg
/home/mike/music/covers/537a4b745758bb930982ff58172cb47a.jpg
/home/mike/music/covers/3662acc2310e9d1b47866f3ff1025376.jpg
/home/mike/music/covers/5439f748b6b6cb7265d13f9dbe4905a1.jpg
/home/mike/music/covers/6913b2f4809b4087ed246ad61ccc25ca.jpg
/home/mike/music/covers/642651a96ffd14b97de5594bc2a920d7.jpg
/home/mike/music/covers/58566327cd70bca0df04781190e09d55.jpg
/home/mike/music/covers/208138004869cfc67bfc0206cfaff47a.jpg
/home/mike/music/covers/035002826953711fe075a0bc3786ed3f.jpg
/home/mike/music/covers/a409c69ed123b9c0c23a0d1557c1e93b.jpg
/home/mike/music/covers/a56936337e7254e11d24f7d561d06dc9.jpg
/home/mike/music/covers/bf65789f52b77c303d464f6a524781d0.jpg
/home/mike/music/covers/c2aa5b9a9c26024cbb498645efee50a3.jpg
/home/mike/music/covers/c6ac890b10573720672dd318244a321b.jpg
/home/mike/music/covers/d6dcbb4369713223e241b9ef240d258a.jpg
/home/mike/music/covers/d968f7d4eb44cf83bb49ee6615a63157.jpg
/home/mike/music/covers/ed1981aae2869f0910e82c14acde3f47.jpg
/home/mike/music/covers/f05dffa148d28e0bcd33d81d862cf602.jpg
/home/mike/music/covers/f32b3e575bdc8be170a2a3a9cfe8872b.jpg
/home/mike/music/covers/fcbe0872344f43a7ba2c52f48581d5e1.jpg
/home/mike/music/covers/fda2a17f7147e93aced77cc72472d6f8.jpg
/home/mike/music/covers/fe0336e95c7c52687b627153d891ebc1.jpg'.
/usr/local/share/avatar-factory/themes/cd: line 9: - : syntax error: operand expected (error token is " ")
mike@mike-desktop:~$ 


any ideas?

---

### Post by searayman on 2007-08-27
any ideas?

---

### Post by Yuzem on 2007-08-27
mmm... thats a bug I think. I will try to fix it for the next version.

---

### Post by SQuark on 2007-08-27
This is wonderful!
One issue though: I use Quod Libet. It seems the avatar-launcher only works when Quod Libet is already running.

---

### Post by searayman on 2007-08-27
> **Yuzem said:**
> mmm... thats a bug I think. I will try to fix it for the next version.

so, i can't use it untill you fix this bug?

---

### Post by Yuzem on 2007-08-27
I will try to fix it today. :)

About the Quod Libet issue: Yes that is probably the way it works but I will take a look.

---

### Post by searayman on 2007-08-27
> **Yuzem said:**
> I will try to fix it today. :)

About the Quod Libet issue: Yes that is probably the way it works but I will take a look.

great! Just let me know when the fix is done, thanks!

---

### Post by Yuzem on 2007-08-27
Here it is the new version, the bug should be fixed now and also the problem with quodlibet.
There was another problem, some times the avatars weren't sorted in the correct order, that is also fixed. (it was reported by swede_hac)

There are picture avatars in this version:
The picture avatars can provide a flat view of all your picture folders showing the 3 last added pictures of each folder. They act as folders (when clicked they send you inside the respective folder)
[[IMG]http://img178.imageshack.us/img178/411/pictureavatarssd8.th.png[/IMG]](http://img178.imageshack.us/my.php?image=pictureavatarssd8.png)

The first post was updated and here it is the changelog:

27.08.07------0.2.5
[INDENT]+picture grabber
	+photos theme
	+added 2 dvd theme variations
	+fixed sorting problem (they should be processed by path)
	+fixed music grabber bug
	+fixed problem with quodlibet[/INDENT]

---

### Post by isaacj87 on 2007-08-28
Great job! I finally found that Album Cover Art Downloader for Linux (it was even a deb!) and I thought I'd share it with others. I really love the work you've done. Any future plans for banshee support? I was looking through avatar-launcher.py and was going to modify it to include banshee...but wasn't sure if banshee could handle it. Anywho, download the deb and follow this instructions to get the program working...It won't work upon initial installation.

> There is one bug with the package that needs to be fixed before you can use Album Cover Art Downloader in Feisty.

1) Open a terminal, and navigate to the folder that contains the files for the application:
```
cd /usr/lib/albumart/
```
2) Open the offending file in gedit as root:
```
gksudo gedit albumart_images.py
```
3) Insert the following as the first line of the file:
```
#coding:utf-8
```
4) Save the file, then exit gedit.


To run the program, either issue the following from a terminal or the Run window in GNOME (Alt+F2):
```
albumart-qt
```

You are now good to go find gorgeous album covers! Many thanks to Sami Kyöstilä for this wonderful program. I hope that the project was not taken down at the request of Amazon or Walmart, and that it will be back up and running soon.

---

### Post by aidanr on 2007-08-28
first of all, really nice scripts

had a few problems getting it going though, first you might want to specify that mpc is required for the mpd clients

secondly mpc was bitching about the port, also spaces weren't being converted to underscores

/usr/local/bin/avatar-launcher
```
#!/bin/bash
#############Global Options
music=mpd
comic=comix
video=mplayer
x1=
x2=
x3=
music_widget=yes
mpd_music_directory=/var/lib/mpd/music
[COLOR="Red"]mpd_port=6600[/COLOR]
[COLOR="Red"]mpd_host=127.0.0.1[/COLOR]

.....stuff......

mpd_support ()
{
[COLOR="Red"]export MPD_PORT=$mpd_port[/COLOR]
[COLOR="Red"]export MPD_HOST=$mpd_host[/COLOR]
mpc clear
mpc ls $(echo "$1" | sed "s|$mpd_music_directory/||" [COLOR="Red"]| sed "s| |_|g"[/COLOR]) | mpc add
mpc play
}

```

edit:// actually it'll probably also bitch about a non-default MPD_HOST as well, might want to add that also

---

### Post by Nonno Bassotto on 2007-08-28
Your scripts are really nice! Fancy eyecandy in bash! One never knows...

Just an advice for the picture grabber. If one tags his photos with gThumb, each photo folder contains a subdirectory named .comments; you may want to ignore these, as they contain no pictures and get a blank preview. More generally avatar-factory should ignore directories without images.

Keep on with your really good work.

---

### Post by ayoli on 2007-08-28
> **Nonno Bassotto said:**
> 
Just an advice for the picture grabber. If one tags his photos with gThumb, each photo folder contains a subdirectory named .comments; you may want to ignore these, as they contain no pictures and get a blank preview. 
i totally second that
> **Nonno Bassotto said:**
> More generally avatar-factory should ignore directories without images.

but i do not agree this because i have many albums (or like) without cover.

---

### Post by Nonno Bassotto on 2007-08-28
Well, I was refering to the picture grabber, not the album one. A picture grabber should not consider directories without pictures in it.

---

### Post by -SpaZ on 2007-08-28
This is especially great for OSX themes, but I find it to look good with any of the themes I have.  Thanks a bunch.

---

### Post by ayoli on 2007-08-28
> **Nonno Bassotto said:**
> Well, I was refering to the picture grabber, not the album one. A picture grabber should not consider directories without pictures in it.
sorry, my mistake, a bit tired (or/and too drunk :) )

---

### Post by Yuzem on 2007-08-28
Thanks to all for your comments. :)

aidanr:
I have included your code for the mpd function and now the mpc requirement is specified in the instrucions. Thanks.
I didn't know that spaces needed to be converted to underscores...

Bassotto:
The picture grabber shouldn't process directories without images. This is the command:
```
ls -t1 | egrep -i '\.jpg|\.png' | head -n 3
```
The problem is that any file that contains ".jpg" or ".png" on it name will be processed as a picture.
I will see if I can make it to ignore hidden folders.

isaacj87:
I am trying to get Banshee to work but I am having some problems...

If there is an expert reading this that can help me out the problem is this:
From a directory with mp3 files the following command gives me what I need:
```
find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' '
```

If I paste the result in front of the following command it works:
```
banshee --play --enqueue
```

But if I put all together it doesn't work:
```
banshee --play --enqueue $(find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```
:(

---

### Post by malachi on 2007-08-29
The --name parameter doesn't seem to work for me.

---

### Post by atlas95 on 2007-08-29
could you make working it for banshee? thanks for this very good job !

---

### Post by atlas95 on 2007-08-29
How to do, with nautilus-actions, for when right clic a on folder with a movie or a album have just it is vinyl folder or movie folder for a movie....?

---

### Post by isaacj87 on 2007-08-29
> **Yuzem said:**
> Thanks to all for your comments. :)

isaacj87:
I am trying to get Banshee to work but I am having some problems...

If there is an expert reading this that can help me out the problem is this:
From a directory with mp3 files the following command gives me what I need:
```
find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' '
```

If I paste the result in front of the following command it works:
```
banshee --play --enqueue
```

But if I put all together it doesn't work:
```
banshee --play --enqueue $(find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```
:(

I have a question though about this...When you click an avatar, it opens the entire album as a playlist, like in Amarok. But Amarok supports this, and I was pretty sure Banshee doesn't. Maybe that's why you're having troubles?

---

### Post by Yuzem on 2007-08-29
> **malachi said:**
> The --name parameter doesn't seem to work for me.
mmm... it was working in the last version I think. Remember that "--name 0" does not work with thunar. Tell me if that wasn't the problem.

> **atlas95 said:**
> could you make working it for banshee? thanks for this very good job !
Yes, I am trying to make it work with banshee.

> **atlas95 said:**
> How to do, with nautilus-actions, for when right clic a on folder with a movie or a album have just it is vinyl folder or movie folder for a movie....?
I am not sure if I understand but film avatars right now doesn't work for movie files.
If you are asking about the command to select a different theme it is:
for vinyl:
```
avatar-factory -mg music/album/path folder/2/save -t vinyl
```
for cd:
```
avatar-factory -mg music/album/path folder/2/save -t cd
```
For a list of themes:
```
avatar-factory -lt
```

> **isaacj87 said:**
> I have a question though about this...When you click an avatar, it opens the entire album as a playlist, like in Amarok. But Amarok supports this, and I was pretty sure Banshee doesn't. Maybe that's why you're having troubles?
Yes, Banshee doesn't support that but it can work in other way. The next command works:
```
banshee --play --enqueue "file1.mp3" "file2.mp3" "etc.mp3"
```

But if I make the list of files to play with a command it doesn't work:
```
banshee --play --enqueue $(find "$PWD" -maxdepth 1 -type f -iname '*.mp3' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```

It isn't a Banshee problem, the same happens with moc and with totem. I will ask in the "Programming Talk" forum category.

---

### Post by isaacj87 on 2007-08-30
Hey Yuzem,

Any luck with banshee support? What was the response over in the Programming section? What language are you coding in...C or python or something else?

---

### Post by Yuzem on 2007-08-30
Yes, it is done. :)
I am coding in bash.
I just finished to fix the problem with the gThumb folders so here it is the new version:

30.08.07------0.2.7
[INDENT]+better mpd support (thanks to aidanr)
+hidden folders are skipped now
+added support for banshee  (thanks to duff)
+fixed "--list-themes" command problem[/INDENT]

---

### Post by isaacj87 on 2007-08-30
Awesome! I'm going to try it out right now. 

You say you're a linux noobie...but this is some pretty good stuff. Tell me, how did you learn to do this?

and I found your thread in Programming Talk and saw you found a fix. :)

---

### Post by isaacj87 on 2007-08-30
**THIS IS GREAT!**

Works perfectly...I'll do more playing/testing with it and make sure it's all good. But so far it works great...thanks for this!

**EDIT**: I was looking through the code...it doesn't look like you added the same command for Totem support so I'm assuming Totem won't play the album like it should...Not hard to add it though :)
I also noticed that your command (for the banshee support) only calls for mp3 files. Am I wrong? If I'm right it might be a good idea to widen the call for aac and m4a files too...just in case.

Great stuff Yuzem, you've inspired me to starting coding something!

---

### Post by aidanr on 2007-08-30
you have and extra sed that shouldn't be there

```
mpc ls $(echo "$1" | sed -e "s|$mpd_music_directory/||" -e [COLOR="Red"]sed[/COLOR] "s| |_|g") | mpc add
```

other than that, working just fine for me :)

---

### Post by Yuzem on 2007-08-31
> **isaacj87 said:**
> You say you're a linux noobie...but this is some pretty good stuff. Tell me, how did you learn to do this?

Well... I am not sure. I am very curious about how things work. One day a discover the possibilities of desktop entry files (avatars are desktop entry files) and one thing lead to the other...

> **isaacj87 said:**
> 
I was looking through the code...it doesn't look like you added the same command for Totem support so I'm assuming Totem won't play the album like it should...Not hard to add it though :)
Totem works in a different way. It only need one parameter, the folder. The problem with Banshee was that it needed every audio file as a parameter but I don't really know why it wasn't working... :(

> **isaacj87 said:**
> 
I also noticed that your command (for the banshee support) only calls for mp3 files. Am I wrong? If I'm right it might be a good idea to widen the call for aac and m4a files too...just in case.
Yes, you are right. m4a and aac? Ok, no problem.

> **isaacj87 said:**
> 
Great stuff Yuzem, you've inspired me to starting coding something!
I am glad to hear that. :)

> **aidanr said:**
> you have and extra sed that shouldn't be there

```
mpc ls $(echo "$1" | sed -e "s|$mpd_music_directory/||" -e [COLOR="Red"]sed[/COLOR] "s| |_|g") | mpc add
```

other than that, working just fine for me :)
Ops, it is fixed now. still the same version...

---

### Post by Yuzem on 2007-08-31
I added more file formats (m4a aac ogg) for Banshee and other players. It is still the same version. Just redownload it.

---

### Post by isaacj87 on 2007-08-31
Great, I noticed all the supported formats now.

But you deleted an important part of the command.

The sort function.

What looks like this:
```

'*.m4a' -or -iname '*.ogg' |  sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')

```

Should look like this
```

'*.m4a' -or -iname '*.ogg' **| sort |** sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')

```

---

### Post by aidanr on 2007-08-31
here's a deb package for anyone who wants it

---

### Post by ayoli on 2007-08-31
Awesome ! This thread should be now a subforum of the third party projects section, Yuzem you may ask for that :)
aidanr, thanks for the deb :)

---

### Post by Yuzem on 2007-08-31
> **isaacj87 said:**
> Great, I noticed all the supported formats now.

But you deleted an important part of the command.

The sort function.

What looks like this:
```

'*.m4a' -or -iname '*.ogg' |  sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')

```

Should look like this
```

'*.m4a' -or -iname '*.ogg' **| sort |** sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')

```
Yes, I deleted that because it give me the impression that it wasn't making any difference and that Banshee sorted the songs in function of the list view sort configuration in the list.
Are you sure that it makes a difference?

> **aidanr said:**
> here's a deb package for anyone who wants it, including the correction from the post above
I added that to the instructions. Thanks!

> **ayoli said:**
> Awesome ! This thread should be now a subforum of the third party projects section, Yuzem you may ask for that :)
aidanr, thanks for the deb :)
Do you think that it will be accepted? Where should I ask?

---

### Post by ayoli on 2007-08-31
> **Yuzem said:**
> 
Do you think that it will be accepted? Where should I ask?

I don't know what are the condition(s) to have a subforum in third party project , but i guess at least you must have a (good) project (which is the case for you IMO).
I think it doesn't cost much to ask, try to ask that to moderators.

---

### Post by isaacj87 on 2007-08-31
> **Yuzem said:**
> Yes, I deleted that because it give me the impression that it wasn't making any difference and that Banshee sorted the songs in function of the list view sort configuration in the list.
Are you sure that it makes a difference?


Yeah, it does...
I was confused at first as to why my songs were playing in a random order. Upon clicking the avatar, banshee would open up and place the songs in a random order (like, 9, 3, 10, 5,) and it was driving me crazy! Now that I've put "sort" back in there it works like normal! :)

---

### Post by Yuzem on 2007-08-31
> **ayoli said:**
> I don't know what are the condition(s) to have a subforum in third party project , but i guess at least you must have a (good) project (which is the case for you IMO).
I think it doesn't cost much to ask, try to ask that to moderators.
Done, lets wait for the answer... :popcorn:

> **isaacj87 said:**
> Yeah, it does...
I was confused at first as to why my songs were playing in a random order. Upon clicking the avatar, banshee would open up and place the songs in a random order (like, 9, 3, 10, 5,) and it was driving me crazy! Now that I've put "sort" back in there it works like normal! :)
Ok, it is fixed and the version remains the same. :)

---

### Post by isaacj87 on 2007-08-31
Everything is looking and working great! Can't wait for the next version. ;)

---

### Post by ayoli on 2007-09-01
ok i found some errors (but not how to fix them at the moment):
this one seems to raise when you have more than one cover image in a music folder (ie: front cover and back cover):

```
There is no cover for _Eek-A-Mouse-15-Albums_
identify: unable to open image `/media/store/musique/reggae/_Eek-A-Mouse-15-Albums_/(1978) eek a mouse - his first (EP)/side b.jpg
/media/store/musique/reggae/_Eek-A-Mouse-15-Albums_/(1978) eek a mouse - his first (EP)/side a.jpg': Aucun fichier ou répertoire de ce type.
identify: unable to open image `/media/store/musique/reggae/_Eek-A-Mouse-15-Albums_/(1978) eek a mouse - his first (EP)/side b.jpg
/media/store/musique/reggae/_Eek-A-Mouse-15-Albums_/(1978) eek a mouse - his first (EP)/side a.jpg': Aucun fichier ou répertoire de ce type.
/usr/local/share/avatar-factory/themes/cd: line 9: - : erreur de syntaxe : opérande attendu (error token is " ")
```
 and i had just this line alone for an music folder with a jpg file corrumpted:
```
/usr/local/share/avatar-factory/themes/cd: line 9: - : erreur de syntaxe : opérande attendu (error token is " ")
```

EDIT : weird, i manage to have all my album "avatar-ed" but i used --type 0 because i wanted to open dir instead of play, this didn't work for me it said unable to open in nautilus, so i trashed all avatars and try to make them again and no errors like previous described and it play files on clic ...
btw it's a pretty tool in its early stages, that was just a feedback to try to help :) Keep it up :)

---

### Post by Yuzem on 2007-09-01
All the feedback is welcome and encouraged. :)
Trying to fix the problem with the music grabber I found another.
Well... here it is the new version with the problem fixed (I hope):
```

01.09.07------0.2.8
	+added audio formats (m4a aac ogg) for Banshee and other players.
	+fixed bug with music grabber not getting the covers in the correct order.
	+fixed bug with --type option.

```

---

### Post by ayoli on 2007-09-01
> **Yuzem said:**
> All the feedback is welcome and encouraged. :)
Trying to fix the problem with the music grabber I found another.
Well... here it is the new version with the problem fixed (I hope):
```

01.09.07------0.2.8
	+added audio formats (m4a aac ogg) for Banshee and other players.
	+fixed bug with music grabber not getting the covers in the correct order.
	+fixed bug with --type option.

```

You rock :) I'll give a try.
Btw, whay about adding support for audacious ?

@aidanr : Do you think you can continue to provide debs ?

---

### Post by ayoli on 2007-09-01
Just found how to do audacious support : same as banshee. I ve just replaced banshee command with audacious one (same options after) and ... it works, yay :)
here's the modified code : 
```
banshee_support ()
{
eval audacious --play --enqueue  $(find "$1" -maxdepth 1 -type f -iname '*.mp3' -or -iname '*.aac' -or -iname '*.m4a' -or -iname '*.ogg' | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
}
```
Looks like it need some factorisation, ie a player_support function that take args like player command/options ...

---

### Post by isaacj87 on 2007-09-01
Hey yuzem, you forgot the "sort" function in the line to launch Banshee.

---

### Post by Yuzem on 2007-09-01
Ok, I will add audacious support in the next version and I will set the banshee function as the default behavior for unknown players.
Today I had an idea about avatar-factory and youtube. I am working on that right now and if everything goes well it will be on the next version too. :)

---

### Post by Yuzem on 2007-09-01
> **isaacj87 said:**
> Hey yuzem, you forgot the "sort" function in the line to launch Banshee.

Ops... I was in another computer so I downloaded and fixed the sort problem but I forgot to update that on my computer.

Now it is fixed. (again)

---

### Post by isaacj87 on 2007-09-01
> **Yuzem said:**
> Ops... I was in another computer so I downloaded and fixed the sort problem but I forgot to update that on my computer.

Now it is fixed. (again)

Thank you :)

I'm interested about this youtube idea...can't wait!

---

### Post by ayoli on 2007-09-01
> **Yuzem said:**
> Ok, I will add audacious support in the next version and I will set the banshee function as the default behavior for unknown players.
)
I guess there is a bit  more work to do for a real audacious support than what i said before, I've just seen for exemple that the music widget seems  to not work with my "simple tweak"
btw, any answer from mod to your ask about a project subforum ?

---

### Post by Lord Illidan on 2007-09-01
This is incredibly cool..

---

### Post by ayoli on 2007-09-01
> **Lord Illidan said:**
> This is incredibly cool..

yes indeed :)

---

### Post by Yuzem on 2007-09-01
> **ayoli said:**
> I guess there is a bit  more work to do for a real audacious support than what i said before, I've just seen for exemple that the music widget seems  to not work with my "simple tweak"
btw, any answer from mod to your ask about a project subforum ?

Yes, they send me this link:
[http://ubuntuforums.org/showthread.php?t=393914](http://ubuntuforums.org/showthread.php?t=393914)

Having read that I saw that it isn't about a different category for the topic but an entire forum for it and I don't believe that that is necessary. A topic is good enough for now.
I wouldn't know what to do with an entire forum. :???:
Maybe in the future if avatar-factory becomes more popular...

---

### Post by ayoli on 2007-09-02
> **Yuzem said:**
> Yes, they send me this link:
[http://ubuntuforums.org/showthread.php?t=393914](http://ubuntuforums.org/showthread.php?t=393914)

Having read that I saw that it isn't about a different category for the topic but an entire forum for it and I don't believe that that is necessary. A topic is good enough for now.
I wouldn't know what to do with an entire forum. :???:
Maybe in the future if avatar-factory becomes more popular...
It's already popular :) 
Look at third party project forums there is not many thread but it still better than having one thread with 80 pages /800 replies (as it goes for the mac menu bar).
That is perhaps not an emergency (lol) but could be interesting in the future.

---

### Post by foxy123 on 2007-09-02
It is an awesome app. Thanks a lot, great job.

I have a few questions though:

1. Is it possible add albums to a current play-list in mpd? Currently clicking on avatar replace the content of the play-list. What if I want to put a few albums into play-list in one go?

2. Is it possible to have a different name for avatars? I would like to have them in the format artist - year - album.

3. I wonder if it is possible to configure a custom view for a particular folder in Thunar. I like View as compact list for most of my folders, but I would prefer View as icon and zoomed for the Album folder.

---

### Post by ayoli on 2007-09-02
> **foxy123 said:**
> It is an awesome app. Thanks a lot, great job.

I have a few questions though:

1. Is it possible add albums to a current play-list in mpd? Currently clicking on avatar replace the content of the play-list. What if I want to put a few albums into play-list in one go?

2. Is it possible to have a different name for avatars? I would like to have them in the format artist - year - album.

I think avatar-factory uses the album folder name for avatars names, so you may want to rename your album folders artist-year-album and use the --name 2 option when generating avatars (this makes avata-factory not use the index number in the name).
> **foxy123 said:**
> 
3. I wonder if it is possible to configure a custom view for a particular folder in Thunar. I like View as compact list for most of my folders, but I would prefer View as icon and zoomed for the Album folder.
Nautilus can do that, i m not sure for thunar.

For the 1rst point, i do not have an answer.

---

### Post by foxy123 on 2007-09-02
> **ayoli said:**
> I think avatar-factory uses the album folder name for avatars names, so you may want to rename your album folders artist-year-album and use the --name 2 option when generating avatars (this makes avata-factory not use the index number in the name).

Nautilus can do that, i m not sure for thunar.

For the 1rst point, i do not have an answer.
Thanks a lot for the reply. For my first questions I have just commented out
```
mpc clear
``` in the script, I would rather clear my play-list manually now and then. Maybe it is possible to come up with a more elegant solution.

I wonder if the script can read info from tags? Then you could pick any name format for avatars.

I have asked about No.3 on the xfce mailing list.

---

### Post by ayoli on 2007-09-02
> **foxy123 said:**
> Thanks a lot for the reply. For my first questions I have just commented out
```
mpc clear
``` in the script, I would rather clear my play-list manually now and then. Maybe it is possible to come up with a more elegant solution.

I wonder if the script can read info from tags? Then you could pick any name format for avatars.

I have asked about No.3 on the xfce mailing list.
At the moment it cant read tags it only use find and sed i guess, but with use of a tool like id3tool for ex, this could be possible and maybe a good suggestion
edit: here's the outpout of id3tool on one of my mp3:
```
&#9492;&#9472; $ -> id3tool downloads/music/x2c_-_Ragga_JungleTek_Mix2.mp3 
Filename: downloads/music/x2c_-_Ragga_JungleTek_Mix2.mp3
Song Title:     x2c -  Ragga JungleTek MIX2   
Artist:         smokering.co.uk               
Album:          djx2c.co.uk                   
Year:           2006
```
means your files should be well tagged. And now i m finally not sure that is possible to use since avatar-factory is made for albums. If the script use mp3 tags for avatar name you will have an avatar for each song instead of each album.

---

### Post by SQuark on 2007-09-02
A simple solution would be to use the (sub)directory structure in the naming scheme. E.g. I have subdirectories for every artist in my music directory, each of them having subdirectories for every album. The avatars would be called "Artist - Album" accordingly.
To have "Artist - Year - Album", you just have to use another level of subdirectories.

---

### Post by foxy123 on 2007-09-02
> **ayoli said:**
> At the moment it cant read tags it only use find and sed i guess, but with use of a tool like id3tool for ex, this could be possible and maybe a good suggestion
edit: here's the outpout of id3tool on one of my mp3:
```
&#9492;&#9472; $ -> id3tool downloads/music/x2c_-_Ragga_JungleTek_Mix2.mp3 
Filename: downloads/music/x2c_-_Ragga_JungleTek_Mix2.mp3
Song Title:     x2c -  Ragga JungleTek MIX2   
Artist:         smokering.co.uk               
Album:          djx2c.co.uk                   
Year:           2006
```
means your files should be well tagged. And now i m finally not sure that is possible to use since avatar-factory is made for albums. If the script use mp3 tags for avatar name you will have an avatar for each song instead of each album.

well, you can still use it. Something like that:
```
~$ id3tool ~/Music/The\ Rolling\ Stones/1969\ -\ Let\ It\ Bleed/*.*|grep -E -m 3 "Artist|Year|Album"
Artist:         Rolling Stones                
Album:          Let It Bleed                  
Year:           1969

```

I have no idea how to code it though.

---

### Post by lzfy on 2007-09-02
I have to ask, can you make this work with Konqueror? :)

---

### Post by Nonno Bassotto on 2007-09-02
Just a couple of ideas for your application. I think the things you implemented work very well. I can think of two other avatars which would be nice to implement.

1) Avatars for your movies. This shouldn't be much more difficult than the imdb avatars, assuming one uses the proper title as a name for the file. The page to look for on imdb has an url like
```

http://www.imdb.com/find?q=%22arancia%20meccanica%22;s=tt;site=aka

```
This is an example for "Arancia meccanica", which is the italian name for "A clockwork orange". The last two parameters are used in order to look for alternative names too (in this case the italian one).

Once you have the page I think you can grab the cover art with the same code you used for the imdb avatars.

EDIT: D'oh. It seems that this sintax only works for alternative names, like the Jugoslavian "Beri Lindon" for "Barry Lindon". I couldn't find a sintax that always works and directly leads to the title main page.
EDIT: Even worst. There is a problem with articles. For example if you search "L'impero colpisce ancora" (italian title for "The empire strikes back") you are not lead to the main page, but to the search page. To get to the main page you should insert "impero colpisce ancora, L'" with the article at the end. Now I begin to understand why you didn't implement this yet... :)
I think there is no obvious workaround to parsing the search result page.

2) Anobii avatars. [Anobii]("http://www.anobii.com") is an analogue of imdb, but for books. This is more difficult, since you usually have an account, where you register the books you have or you'd like to have. So it is not obvious how to extract information about the books you have. Anyway, one could use links too, like with imdb.

---

### Post by aidanr on 2007-09-02
> **ayoli said:**
> @aidanr : Do you think you can continue to provide debs ?

yeah, sorry was away for the weekend, updated my other [post]("http://ubuntuforums.org/showpost.php?p=3284554&postcount=71")

---

### Post by aidanr on 2007-09-02
> **foxy123 said:**
>  I wonder if it is possible to configure a custom view for a particular folder in Thunar. I like View as compact list for most of my folders, but I would prefer View as icon and zoomed for the Album folder.

This is something I'd also like, right now I'm using rox-filler for avatar-factory and thunar for everything else. A profiles option or a command line option to use a different thunarrc would be cool, or perhaps a simple gtk window/app just for avatar factory.

---

### Post by ayoli on 2007-09-02
> **aidanr said:**
> yeah, sorry was away for the weekend, updated my other [post]("http://ubuntuforums.org/showpost.php?p=3284554&postcount=71")

thanks for those who prefer deb facilities :)

---

### Post by Yuzem on 2007-09-02
> **ayoli said:**
> It's already popular :) 
Look at third party project forums there is not many thread but it still better than having one thread with 80 pages /800 replies (as it goes for the mac menu bar).
That is perhaps not an emergency (lol) but could be interesting in the future.
Yes. Lets see what the future brings... :)

> **foxy123 said:**
> It is an awesome app. Thanks a lot, great job.

I have a few questions though:

1. Is it possible add albums to a current play-list in mpd? Currently clicking on avatar replace the content of the play-list. What if I want to put a few albums into play-list in one go?
Already done but not released yet. It will work with mocp, mpd, audacious and totem for now.

> **foxy123 said:**
> 
2. Is it possible to have a different name for avatars? I would like to have them in the format artist - year - album.
I will implement that but not for the next version.

> **SQuark said:**
> A simple solution would be to use the (sub)directory structure in the naming scheme. E.g. I have subdirectories for every artist in my music directory, each of them having subdirectories for every album. The avatars would be called "Artist - Album" accordingly.
To have "Artist - Year - Album", you just have to use another level of subdirectories.
mmm... this is easy. Maybe I could implement it in this way instead...

> **lzfy said:**
> I have to ask, can you make this work with Konqueror? :)
The avatars are desktop entry files that should work practically anywhere:
[http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec](http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec)
For example, if you go to: "/usr/share/applications" you will see a lot of desktop entry files.
If Konqueror doesn't work then it is probably a Konqueror problem.

> **Nonno Bassotto said:**
> Just a couple of ideas for your application. I think the things you implemented work very well. I can think of two other avatars which would be nice to implement.

1) Avatars for your movies. This shouldn't be much more difficult than the imdb avatars, assuming one uses the proper title as a name for the file. The page to look for on imdb has an url like
```

http://www.imdb.com/find?q=%22arancia%20meccanica%22;s=tt;site=aka

```
This is an example for "Arancia meccanica", which is the italian name for "A clockwork orange". The last two parameters are used in order to look for alternative names too (in this case the italian one).

Once you have the page I think you can grab the cover art with the same code you used for the imdb avatars.

EDIT: D'oh. It seems that this sintax only works for alternative names, like the Jugoslavian "Beri Lindon" for "Barry Lindon". I couldn't find a sintax that always works and directly leads to the title main page.
EDIT: Even worst. There is a problem with articles. For example if you search "L'impero colpisce ancora" (italian title for "The empire strikes back") you are not lead to the main page, but to the search page. To get to the main page you should insert "impero colpisce ancora, L'" with the article at the end. Now I begin to understand why you didn't implement this yet... :)
I think there is no obvious workaround to parsing the search result page.

2) Anobii avatars. [Anobii]("http://www.anobii.com") is an analogue of imdb, but for books. This is more difficult, since you usually have an account, where you register the books you have or you'd like to have. So it is not obvious how to extract information about the books you have. Anyway, one could use links too, like with imdb.

1 ) It is already in my todo list. I will make it search in google first. For example for: imdb A clockwork orange. Then from the result I will get the page.
But internal changes are needed first to be able to select multiples files.

2 ) Yes, from links it will be very easy but I don't know when I will be able to do that. There is a lot in the to do list.

---

### Post by SQuark on 2007-09-02
> **aidanr said:**
> This is something I'd also like, right now I'm using rox-filler for avatar-factory and thunar for everything else. A profiles option or a command line option to use a different thunarrc would be cool, or perhaps a simple gtk window/app just for avatar factory.

Well, if you don't mind using a dock (and a composite window manager), the stacks in [AWN](http://ubuntuforums.org/showthread.php?t=385981) are ideal for avatar-factory!

> **lzfy said:**
> I have to ask, can you make this work with Konqueror? :)

If it doesn't work, it might be that Konqueror derives the file type from the extension. Running this in your folder of avatars may do the trick:
```
for file in *; do mv "$file" "`basename "$file" .avatar`".desktop; done
```
(Not tested, prone to typos.)

---

### Post by Nonno Bassotto on 2007-09-02
> **Yuzem said:**
> 1 ) It is already in my todo list. I will make it search in google first. For example for: imdb A clockwork orange. Then from the result I will get the page.
But internal changes are needed first to be able to select multiples files.


The first Google result for: imdb movie_name isn't always the imdb page. Here an implementation of what I was saying (well, I mostly copied your function get_cover_picture)
```

get_imdb_page ()
{
search_url="http://www.imdb.com/find?q="\"$SOURCE\"";s=tt;site=aka"
search_page="$(wget -qO - "$search_url")"
metadata_line_number=$(( $(echo "$search_page" | grep -n -i '<meta name="title"' | cut -d: -f1 ) ))
if [ "$(echo "$search_page" | sed -n "$metadata_line_number p" | sed "s|.*content=||" | cut -d\" -f2)" = "IMDb Title  Search" ]; then
	title_line_number=$(( $(echo "$search_page" | grep -n -i 'Popular Titles' | cut -d: -f1 ) ))
	aux1=$(echo "$search_page" | sed -n "$title_line_number p")
	aux2=${aux1#*"Popular Titles"}
	imdb_url="http://www.imdb.com"$(echo ${aux2%%"/table"*} | sed "s|.*href=||" | cut -d\" -f2)
	imdb_page="$(wget -qO - "$imdb_url")"
else
	imdb_page=$search_page
fi
}

```
You may probably rewrite the step with aux1 and aux2 using sed, but I don't know how to handle regular expressions, so I used the bash builtin string functions % and #. I just needed to isolate the table containing the string "Popular Titles".

I tried with, say, 30 random titles both in english and in italian and it seems that it works.

Btw, what multiple files are refering to? Is it because of movies split into two files?

---

### Post by Nonno Bassotto on 2007-09-02
> **SQuark said:**
> the stacks in [AWN](http://ubuntuforums.org/showthread.php?t=385981) are ideal for avatar-factory!

It seems nice, but the avatar are far too little, especially the picture ones. Is there any way to have stacks with bigger icons?

---

### Post by Yuzem on 2007-09-02
> **Nonno Bassotto said:**
> The first Google result for: imdb movie_name isn't always the imdb page. Here an implementation of what I was saying (well, I mostly copied your function get_cover_picture)
```

get_imdb_page ()
{
search_url="http://www.imdb.com/find?q="\"$SOURCE\"";s=tt;site=aka"
search_page="$(wget -qO - "$search_url")"
metadata_line_number=$(( $(echo "$search_page" | grep -n -i '<meta name="title"' | cut -d: -f1 ) ))
if [ "$(echo "$search_page" | sed -n "$metadata_line_number p" | sed "s|.*content=||" | cut -d\" -f2)" = "IMDb Title  Search" ]; then
	title_line_number=$(( $(echo "$search_page" | grep -n -i 'Popular Titles' | cut -d: -f1 ) ))
	aux1=$(echo "$search_page" | sed -n "$title_line_number p")
	aux2=${aux1#*"Popular Titles"}
	imdb_url="http://www.imdb.com"$(echo ${aux2%%"/table"*} | sed "s|.*href=||" | cut -d\" -f2)
	imdb_page="$(wget -qO - "$imdb_url")"
else
	imdb_page=$search_page
fi
}

```
You may probably rewrite the step with aux1 and aux2 using sed, but I don't know how to handle regular expressions, so I used the bash builtin string functions % and #. I just needed to isolate the table containing the string "Popular Titles".

I tried with, say, 30 random titles both in english and in italian and it seems that it works.

Btw, what multiple files are refering to? Is it because of movies split into two files?

Great. :)
I have to finish the next release and then I will see how I will do it but I was thinking in something more simple. (remember that I am a newbie :( )
I will not take the first result from google, I plan to grep the result from google for the first line containing something like "imdb.com/title/" and once I have the url I will use the existing grabber:

```

get_cover_picture () {
#First the code to get the imdb page and then:
URL="the url"
. /usr/local/share/avatar-factory/grabbers/imdb  #I will rename the film grabber to imdb
get_cover_picture
}

```

About the multiple files, to do something like:
```
avatar-factory --video-grabber ./*.avi ./destination
```
The music grabber can add only one album but if I make the video grabber to work on folders it will not be able to chose only one video. But I don't know if it is really an important thing...

---

### Post by SQuark on 2007-09-02
> **Nonno Bassotto said:**
> It seems nice, but the avatar are far too little, especially the picture ones. Is there any way to have stacks with bigger icons?

All settings for the stack are in gconf for the moment. Run "gconf-editor" and got to /apps/avant-window-navigator/applets/*some number*. There should be something about the icon size there.

> **Yuzem said:**
> I will not take the first result from google, I plan to grep the result from google for the first line containing something like "imdb.com/title/" and once I have the url I will use the existing grabber:

It seems easier to take the first result from Google for the query "site:imdb.com/title fight club", for example.

---

### Post by Yuzem on 2007-09-03
> **SQuark said:**
> 
It seems easier to take the first result from Google for the query "site:imdb.com/title fight club", for example.

Yes, that seems better.

Could someone confirm if the problem with konqueror was because of the avatar extension?

---

### Post by ayoli on 2007-09-03
> **Yuzem said:**
> Yes, that seems better.

Could someone confirm if the problem with konqueror was because of the avatar extension?

I can see the avatars bu I got an error when i click on the avatar with .avatar or .dektop ext (see screenshot)
btw, i don't care i donot use konqueror that was just for the test :)

---

### Post by Yuzem on 2007-09-03
mmm... I want this to work everywhere. I will install konqueror and see if there is something that I can do about that.

---

### Post by ayoli on 2007-09-03
Ah, I had a strange issue.
I tried several times to generate my avatars due to a prob with the --type opt.
My avatars were working yesterday, launching audacious on click, but today (after a reboot) my first try was in konqueror for the test, and after in nautilus and, surprise ! same error : "can't open destiantion is not a folder".
I think my ~/.avatar-factory was messed up, so I delete it, delete my avatars, regenerate (without problems) and then re-test.
It works now in nautilus,  and surpriiiise it works also nice in konqueror :D
so forget my previous post :)

---

### Post by isaacj87 on 2007-09-03
I saw a post about the icons being to small when combined with the stacks applet for AWN.

I modified the settings so the icons are bigger and I modified the columns and rows to look better. Have a look at the screenshot.

---

### Post by ayoli on 2007-09-03
> **isaacj87 said:**
> I saw a post about the icons being to small when combined with the stacks applet for AWN.

I modified the settings so the icons are bigger and I modified the columns and rows to look better. Have a look at the screenshot.

yep, seen in sept desktop thread. really nice :) unfortunately, change the icon size in the stack applet is for all the folder you browse, not a big problem, but I dont like big size for other folders I browse with stacks.
btw, stacks :guitar: and avatar-factory :guitar: also
AND I VOTE FOR A 3RD PARTY FORUM FOR AVATAR-FACTORY :D
this can bring a better organisation, I think before this thread becomes huge :D

---

### Post by isaacj87 on 2007-09-03
> **ayoli said:**
> yep, seen in sept desktop thread. really nice :) unfortunately, change the icon size in the stack applet is for all the folder you browse, not a big problem, but I dont like big size for other folders I browse with stacks.
btw, stacks :guitar: and avatar-factory :guitar: also
AND I VOTE FOR A 3RD PARTY FORUM FOR AVATAR-FACTORY :D
this can bring a better organisation, I think before this thread becomes huge :D

Yeah, I turned off browsing in stacks so I can't look at other folders. I figure stacks is meant for only one folder...not to be another filemanager.

---

### Post by Nonno Bassotto on 2007-09-03
> **isaacj87 said:**
> I saw a post about the icons being to small when combined with the stacks applet for AWN.

I modified the settings so the icons are bigger and I modified the columns and rows to look better. Have a look at the screenshot.

How did you modify the icon size? I tried to do it in gconf, but the setting had no effect. Maybe is it just that I'm using an old version of AWN? I installed it from the repos linked a few posts before. My version is 0.1.2-bzr78-1 (for AWN) and 0.1.0-bzr43-1 (for the core applets).

EDIT: Forget it. I needed to restart twice (the first time nothing had changed).

---

### Post by PurposeOfReason on 2007-09-05
Will we be seeing XMMS support for this anytime soon? It'd be amazing.

EDIT - It's not listed (or I missed it) but it still works.

---

### Post by Yuzem on 2007-09-05
> **PurposeOfReason said:**
> 
EDIT - It's not listed (or I missed it) but it still works.
Great, I will add it to the list.

---

### Post by Yuzem on 2007-09-06
Here it is the new version. Now it comes in a deb package and if you are lucky, it will also work. :)
There are a lot of changes in this version but most of them are internal changes. Because of that some unknown bugs could pop up. Report them with no mercy. :mad:

Some of the changes:

**Player-add**
Now is possible to configure the music launcher with some players to add the albums to the playlist without clearing it.
To do that set the following instead of the name of the player in the configuration file:
For mocp: "mocp-add"
For mpd: "mpd-add"
For audacious: "audacious-add"
For totem: "totem-add"

**YouTube grabber**
I don't know if the youtube idea was a good idea. At least I will use it. :)
The youtube grabber uses the film theme that isn't very pretty, it needs some improvements.
This is the situation:
There are a lot of videos that you like in youtube.
You could download them but it seems more practical to bookmark them.
The problem is that you don't get a preview.
Avatar Factory will create a previews of your bookmarked youtube videos and when clicked they will use epiphany as a player. (no toolbar, and don't mess your firefox window size):

[[IMG]http://img360.imageshack.us/img360/4616/avatarfactoryyoutubeax3.th.jpg[/IMG]](http://img360.imageshack.us/my.php?image=avatarfactoryyoutubeax3.jpg)

```
avatar-factory -g youtube folder/2/save
```

The film grabber doesn't exist anymore the equivalent is:
```
avatar-factory -g imdb folder/2/save
```

Something similar could be made for apple trailers using the dvd theme and mplayer.


**Cleaning up**
Te icons folder structure has been changed. You can remove the old icons with this command:
```
rm -r  ~/.avatar-factory/icons/
```
And remove avatar-launcher:
```
sudo rm /usr/local/bin/avatar-launcher
```

The changelog:
```
06.09.07------0.3.0
	+added support for audacious
	+added mocp-add (doesn't clear the playlist)
	+added mpd-add (doesn't clear the playlist)
	+added audacious-add (doesn't clear the playlist)
	+added totem-add (doesn't clear the playlist)
	+better support for unknown players
	+film grabber renamed to imdb
	+added film theme
	+added youtube grabber
	+added -g option to use a custom grabber
	+added -lg to list available grabbers
	+avatar-launcher was remplaced by avatar-factory -al
	+internal changes for the music launcher
	+changed the icon folder structure
	+redesigned grabbers structure
	+many internal changes in avatar-factory
```

---

### Post by aidanr on 2007-09-06
sweet, good job  \\:D/

---

### Post by ayoli on 2007-09-07
Wow, what a changelog ! This new major version looks r eally nice, thanks for your job Yuzem :-D

---

### Post by Nonno Bassotto on 2007-09-07
I have some problem with the picture avatars. Actually, they... ehm, do nothing. The old version used to work, but now double clicking a picture avatar has no effect whatsoever. I had a look to the .desktop files and while the old looked like
```

Type=Link
URL=file:///whatever

```

the new ones have
```

Type=Application
Exec=avatar-factory -al picture "whatever" "/whatever.png"

```

Launching the command in a terminal results in
```

picture launcher does not exist

```
which seems a pretty good reason to silently fail.
Why is this change?

Anyway, thank you again for your impressive work. :)

---

### Post by Nonno Bassotto on 2007-09-07
Just another question. Why for the youtube grabber you look for firefox bookmarks, but default to opening links with epiphany? It would seem more reasonable to use firefox instead, so that people don't have to keep two different browsers installed (ok, I saw there is the option to do so, I was just curious to ask).

---

### Post by Nonno Bassotto on 2007-09-07
Ok, my last feedback for now. :) I tried the imdb grabber and the creation of images for avatars fails, saying something like
```

convert: unable to open image `/usr/local/share/avatar-factory/themes/DVD/base.png': Nessun file o directory.

```
Indeed the image base.png has been renamed to base4.png in this release.

Moreover I'm a bit confused about the names for the files. I tried the script various times, and sometimes the avatar had a name like 1.Film, some other times (I wasn't able to guess a rule) it had no name. The no-name version looks better to me: if you want to use the shelf as a background, you need this version to have the avatars properly aligned. Just to be precise: the --name option works for me. The fact is that sometimes I obtained a no-name imdb avatar without specifying
```

--name 0

```

If the name has to be kept, consider translating the entity
```
&# 39;
```
(without the space) into the apostrophe '.

---

### Post by foxy123 on 2007-09-07
It does not work for me after the update.

---

### Post by Yuzem on 2007-09-07
Ops, I knew that some horrible bugs could come out with this version.
Thanks for the feedback! :)

> **Nonno Bassotto said:**
> I have some problem with the picture avatars. Actually, they... ehm, do nothing. 
Fixed.

> **Nonno Bassotto said:**
> Just another question. Why for the youtube grabber you look for firefox bookmarks, but default to opening links with epiphany? It would seem more reasonable to use firefox instead, so that people don't have to keep two different browsers installed (ok, I saw there is the option to do so, I was just curious to ask).
My intention was to launch the videos with a player but I don't know any youtube player (for streaming). Epiphany with no toolbar was the closest option I found, but you are right, I have changed the default behavior for the youtube grabber.

> **Nonno Bassotto said:**
> Ok, my last feedback for now. :) I tried the imdb grabber and the creation of images for avatars fails, saying something like
```

convert: unable to open image `/usr/local/share/avatar-factory/themes/DVD/base.png': Nessun file o directory.

```
Indeed the image base.png has been renamed to base4.png in this release.

Fixed.
> **Nonno Bassotto said:**
> 
Moreover I'm a bit confused about the names for the files. I tried the script various times, and sometimes the avatar had a name like 1.Film, some other times (I wasn't able to guess a rule) it had no name. The no-name version looks better to me: if you want to use the shelf as a background, you need this version to have the avatars properly aligned. Just to be precise: the --name option works for me. The fact is that sometimes I obtained a no-name imdb avatar without specifying
```

--name 0

```

If the name has to be kept, consider translating the entity
```
&# 39;
```
(without the space) into the apostrophe '.
mmm... I don't know about that one.
The names are taken not form the imdb page but from the firefox bookmarks.
What could be the problem...? :-k

> **foxy123 said:**
> It does not work for me after the update.
Try the new version:
```
07.09.07------0.3.0-1
	+fixed bug in music launcher
	+fixed picture grabber bug
	+changed default behavior for youtube grabber
```

---

### Post by isaacj87 on 2007-09-08
Hmmm...it makes the youtube avatar, but everytime I click it to run it opens up Totem?? and not firefox...

---

### Post by Yuzem on 2007-09-08
Ok, for the moment do this:
```
gedit ~/.avatar-factory/avatar-launcher
```
and add:
```
youtube=firefox

```
or for opening in a new window:
```
youtube="firefox -new-window"
```

Then use the --type 1 option:
```
avatar-factory -g youtube folder/2/save --type 1
```

---

### Post by foxy123 on 2007-09-08
> **Yuzem said:**
> 
Try the new version:
```
07.09.07------0.3.0-1
	+fixed bug in music launcher
	+fixed picture grabber bug
	+changed default behavior for youtube grabber
```

no, nothing happens :(

---

### Post by foxy123 on 2007-09-08
I tried to run an exec line in terminal and got the following error:
```
error: ACK [50@0] {lsinfo} directory not found
``` I am not sure if it is supposed to be run in terminal at all though.

---

### Post by Yuzem on 2007-09-08
Yes, it should run from the terminal. Maybe you are trying to run old avatars with the new version. You must delete the old ones and make them again with the new version.

If that isn't the problem post the content of a non working avatar.

---

### Post by foxy123 on 2007-09-08
> **Yuzem said:**
> Yes, it should run from the terminal. Maybe you are trying to run old avatars with the new version. You must delete the old ones and make them again with the new version.

If that isn't the problem post the content of a non working avatar.
no, I removed everything before installing. Here  the content of the avatar:

```
[Desktop Entry]
Encoding=UTF-8
Name=6.1974 - Warrior On The Edge Of TIme
X-MultipleArgs=false
Type=Application
Exec=avatar-factory -al music "/home/foxy/Music/Hawkwind/1974 - Warrior On The Edge Of TIme" "/home/foxy/.avatar-factory/icons/music/cd/_home_foxy_Music_Hawkwind_1974 - Warrior On The Edge Of TIme.png"
Icon=/home/foxy/.avatar-factory/icons/music/cd/_home_foxy_Music_Hawkwind_1974 - Warrior On The Edge Of TIme.png
URL=file:///home/foxy/Music/Hawkwind/1974 - Warrior On The Edge Of TIme

```

---

### Post by Yuzem on 2007-09-08
Are you using mpd?
If that is the case delete all the icons again and follow the mpd instructions in the first post.
If not, then set a different player in the configuration file and tell me what happens.
Try totem.

---

### Post by foxy123 on 2007-09-08
> **Yuzem said:**
> Are you using mpd?
If that is the case delete all the icons again and follow the mpd instructions in the first post.
If not, then set a different player in the configuration file and tell me what happens.
Try totem.

oh, yes. It works now, thanks a lot. 

I wonder if it is possible to use amazon for sourcing images. I've got covers in the directories only for those albums for which sonata cannot get the image remotely. It means that avatars are not generated for them. What if the avatar-factory first looks in the folder and then if there is nothing there on amazon?

---

### Post by Yuzem on 2007-09-08
To automatically download many covers you can use this program:
[http://ubuntuforums.org/showpost.php?p=3266072&postcount=50](http://ubuntuforums.org/showpost.php?p=3266072&postcount=50)

---

### Post by ayoli on 2007-09-08
> **Yuzem said:**
> To automatically download many covers you can use this program:
[http://ubuntuforums.org/showpost.php?p=3266072&postcount=50](http://ubuntuforums.org/showpost.php?p=3266072&postcount=50)

holy **** ! I ve seen that tool some time ago but I've jus tried it now. It 's just exactly what i needed to do a massive cover grabbing from amazon :D

---

### Post by aidanr on 2007-09-08
> **foxy123 said:**
> oh, yes. It works now, thanks a lot. 

I wonder if it is possible to use amazon for sourcing images. I've got covers in the directories only for those albums for which sonata cannot get the image remotely. It means that avatars are not generated for them. What if the avatar-factory first looks in the folder and then if there is nothing there on amazon?

in sonata's preferences you can set it to store the cover art it fetches in the albums folder instead of ~/.covers, then just play a song from each album you don't have album art for and sonata will fetch it and store it

---

### Post by foxy123 on 2007-09-08
> **aidanr said:**
> in sonata's preferences you can set it to store the cover art it fetches in the albums folder instead of ~/.covers, then just play a song from each album you don't have album art for and sonata will fetch it and store it
excellent advice. thanks a lot!

---

### Post by isaacj87 on 2007-09-08
> **ayoli said:**
> holy **** ! I ve seen that tool some time ago but I've jus tried it now. It 's just exactly what i needed to do a massive cover grabbing from amazon :D

I know it took some digging...but I actually found a working .deb!!!

---

### Post by isaacj87 on 2007-09-09
> **Yuzem said:**
> Ok, for the moment do this:
```
gedit ~/.avatar-factory/avatar-launcher
```
and add:
```
youtube=firefox

```
or for opening in a new window:
```
youtube="firefox -new-window"
```

Then use the --type 1 option:
```
avatar-factory -g youtube folder/2/save --type 1
```

hey, I followed these directions...working great now. :)

---

### Post by Yuzem on 2007-09-09
Good :)
I uploaded a new version and now it should work with firefox by default:
```
avatar-factory -g youtube folder/2/save
```

No --type option is needed.

---

### Post by davim on 2007-09-11
great! I love avatar-factory please keep developing :)

---

### Post by sriram on 2007-09-11
Kick ***

---

### Post by Yuzem on 2007-09-11
Thanks, I am still developing this.
Maybe for the weekend I will have a new version. :)

---

### Post by ayoli on 2007-09-12
Yo Yuzem :)
I have a little bug to submit:
I've choosed audaucious add as launcher, when I click on a cover it opens audacious with the album that I cliked on, that's ok. 
Now, if I click on another cover it should fill the playlist with the new album that I choose but it doesn't.
Actually, it freezes audacious. If I do a *ps -A* I have two adacious process and 2 avatar-factory process running. 
I have to kill the 2 audacious process (then avatar-factory ones kill themselves).

---

### Post by ayoli on 2007-09-12
A new cover finder tool that could be interesting to try:
[http://mookooh.org/coverfinder/](http://mookooh.org/coverfinder/)

---

### Post by foxy123 on 2007-09-12
> **ayoli said:**
> A new cover finder tool that could be interesting to try:
[http://mookooh.org/coverfinder/](http://mookooh.org/coverfinder/)

I wonder if there is a deb for Feisty...

---

### Post by ayoli on 2007-09-12
> **foxy123 said:**
> I wonder if there is a deb for Feisty...

Unfortunately, it seems that they provide only gusty debs

---

### Post by Yuzem on 2007-09-12
> **ayoli said:**
> Yo Yuzem :)
I have a little bug to submit:
I've choosed audaucious add as launcher, when I click on a cover it opens audacious with the album that I cliked on, that's ok. 
Now, if I click on another cover it should fill the playlist with the new album that I choose but it doesn't.
Actually, it freezes audacious. If I do a *ps -A* I have two adacious process and 2 avatar-factory process running. 
I have to kill the 2 audacious process (then avatar-factory ones kill themselves).

It is working here. Try audacious alone:
```
audacious -e file1.mp3 file2.mp3 file3.mp3 etc...
```

---

### Post by ayoli on 2007-09-12
> **Yuzem said:**
> It is working here. Try audacious alone:
```
audacious -e file1.mp3 file2.mp3 file3.mp3 etc...
```

trying at cli:
```
audacious -e file1.mp3 file2.mp3
```
that launch audacious , then I played the files and without quiting I type again in cli:
```
audacious -e file3.mp3 file4.mp3
```
that appends file3 and file4 to my playlist without freeze.
Unfortunately that does not work when I use avatar factory :(

EDIT: nevermind, I funckin dunno what was the prob. It seems to work now :D

---

### Post by Yuzem on 2007-09-12
Try this:
```
avatar-factory -al music folder/with/music
```

If that works then something must be wrong with the avatars. Post the content of one of them.
If that doesn't work, I don't know...
What version of audacious are you running?
It happens with any avatar or only with some of them?

Ops... ok, I read that it is working now...

---

### Post by Yuzem on 2007-09-14
There is a new version!
There are some important internal changes. Now it is possible to do something like:
```
avatar-factory -mg "folder1" "folder2" "folder3" folder/2/save
```

The film grabber will make dvds from your video files. Multiples disc are recognized with [cC][dD][1-9]
For example: cd1, Cd1, CD1, cD1, etc...
```
avatar-factory -fg ./*.avi folder/2/save
```

The same screenshot:
[[IMG]http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.th.png[/IMG]](http://img379.imageshack.us/my.php?image=avatarfactoryfg3lk3.png)

```

14.09.07------0.3.3
	+internal changes in avatar-factory
	+added files source type
	+added film grabber

```

---

### Post by wounded on 2007-09-15
This is absolutely awesome but I'm having some problems getting it working.

First of all, I am using this in THUNAR.

I installed the deb from the first post and then ran

```
avatar-factory -mg /media/hdb5/Audio/ ~/music --name 2
```

And it went through and put all the little cd cases in ~/music for the albums I had covers for.

But my music directory is set up so that I have a folder with the artist name and all of their albums in folders inside it. This makes it so that I have a cd case for each artist as well as their albums in the same folder. I guess the only way to fix this is to remove the albums and put them all in the first folder? That wouldn't be too bad, I guess, but is there a way to make it so that the folders without music files in them (The artist folders, with only more folders in them) to open up when double clicked?

Also, while I have 

```
music="mpd"
```

in the config file... I don't know how to make the albums play in mpd with the little cd cases >< I am running mpd on a non-stand port (7700 instead of the default 6600) but I have the MPD_PORT environment variable set to 7700. When I double click them or select "Execute" from the right click menu nothing happens.

As a side note, I opened one up in Mousepad out of curiosity and saw it was simply a desktop entry file. What you did here with this awesome program was what I was trying to figure out how to do just yesterday, although for my ROM files. I wanted the games to be represented by their cover and then run in zsnes/fceu when opened and now I know more about how to get that done than I did :P Really great program.

---

### Post by Nonno Bassotto on 2007-09-15
Fantastic! Now we have the movie grabber too! Let me give some feedback.

First, the movies are opened in mPlayer by default, unless I explicitly write
```

film=totem

```
which seems strange since Totem is my default video player. By the way, you  may want to correct the film grabber instructions, since you suggest to put
```

music="your video player"

```

Second, when the image is missing on IMDB, avatar-factory uses the last one, rather than a black cover. So if I have, say, eraserhaed.avi and L'armata Brancaleone.avi, the latter will be displayed with the eraserhead cover.

---

### Post by Yuzem on 2007-09-15
> **wounded said:**
> 
But my music directory is set up so that I have a folder with the artist name and all of their albums in folders inside it. This makes it so that I have a cd case for each artist as well as their albums in the same folder. I guess the only way to fix this is to remove the albums and put them all in the first folder? That wouldn't be too bad, I guess, but is there a way to make it so that the folders without music files in them (The artist folders, with only more folders in them) to open up when double clicked?
You don't need to move the folders. Avatars will not be created for folders without pictures inside. Just remove the pictures in the artist folders.
I have to fix that and make it work only if there are music files inside the folders.

> **wounded said:**
> 
Also, while I have 

```
music="mpd"
```

in the config file... I don't know how to make the albums play in mpd with the little cd cases >< I am running mpd on a non-stand port (7700 instead of the default 6600) but I have the MPD_PORT environment variable set to 7700. When I double click them or select "Execute" from the right click menu nothing happens.
Read the mpd instructions in the first post, I added some info about that.

> **wounded said:**
> 
As a side note, I opened one up in Mousepad out of curiosity and saw it was simply a desktop entry file. What you did here with this awesome program was what I was trying to figure out how to do just yesterday, although for my ROM files. I wanted the games to be represented by their cover and then run in zsnes/fceu when opened and now I know more about how to get that done than I did :P Really great program.
Thanks. :)
A rom grabber is a good idea. I thought about that too but I don't know when I will be able to do ti. :(

---

### Post by Yuzem on 2007-09-15
> **Nonno Bassotto said:**
> Fantastic! Now we have the movie grabber too! Let me give some feedback.
Thanks, I was waiting for your feedback. :)

> **Nonno Bassotto said:**
> 
First, the movies are opened in mPlayer by default, unless I explicitly write
```

film=totem

```
which seems strange since Totem is my default video player. By the way, you  may want to correct the film grabber instructions, since you suggest to put
```

music="your video player"

```
The instructions are good now.
I thought that mplayer was more popular but since totem is the default in gnome and ubuntu I will set totem as the film player by default.

> **Nonno Bassotto said:**
> 
Second, when the image is missing on IMDB, avatar-factory uses the last one, rather than a black cover. So if I have, say, eraserhaed.avi and L'armata Brancaleone.avi, the latter will be displayed with the eraserhead cover.
Ops, I will try to fix that.
Tell me if you find any other problem.

---

### Post by SQuark on 2007-09-16
Wow! Great work on the film grabber! =D>

Now for some feedback:
[LIST]
[*]Could you make it so that you can use a directory as input, and it will automatically detect all movie files inside it? The *.avi method is kind of limiting.
[*]In addition to the CD1 thing, could you also check for the popular (1of2) and [2of2] format? Or should I just rename all my files. :)
[*]When I run this in my movie folder, I get this output a couple of times:
```
EOF encountered in a comment.
(standard_in) 1: parse error
/usr/local/share/avatar-factory/themes/dvd: line 38: [: -gt: unary operator expected
convert: missing an image filename `/tmp/thumb8326.png'.
convert: unable to open image `/tmp/thumb8326.png': No such file or directory.
convert: unable to open image `/tmp/thumb8326.png': No such file or directory.
rm: cannot remove `/tmp/thumb8326.png': No such file or directory
```
When this pops up, the movie in question gets a black avatar. Maybe a more user friendly output could be generated?
[*]I always get an avatar for The Host, eventhough I don't have the movie The Host. :p
[/LIST]

---

### Post by Yuzem on 2007-09-16
> **SQuark said:**
> Wow! Great work on the film grabber! =D>

Now for some feedback:
[LIST]
Could you make it so that you can use a directory as input, and it will automatically detect all movie files inside it? The *.avi method is kind of limiting.
You can do the same without the extension and it will process all the files.
Or maybe you want it to be recursive and to process also the sub folders?

> **SQuark said:**
> 
In addition to the CD1 thing, could you also check for the popular (1of2) and [2of2] format? Or should I just rename all my files. :)
Ok: [1-9][oO][fF][1-9]
It will be on the next version.

> **SQuark said:**
> 
When I run this in my movie folder, I get this output a couple of times:
```
EOF encountered in a comment.
(standard_in) 1: parse error
/usr/local/share/avatar-factory/themes/dvd: line 38: [: -gt: unary operator expected
convert: missing an image filename `/tmp/thumb8326.png'.
convert: unable to open image `/tmp/thumb8326.png': No such file or directory.
convert: unable to open image `/tmp/thumb8326.png': No such file or directory.
rm: cannot remove `/tmp/thumb8326.png': No such file or directory
```
When this pops up, the movie in question gets a black avatar. Maybe a more user friendly output could be generated?
That will be fixed in the next version (I hope)

> **SQuark said:**
> 
I always get an avatar for The Host, eventhough I don't have the movie The Host. :p
[/LIST]
To what file is it pointing? You can try to rename the file to get a better result.
Avatar-Factory does a search in goolge for something like this:
site:imdb.com/title filename
The first result is used.

---

### Post by Nonno Bassotto on 2007-09-16
Just a really minor thing. I think there is a 1 pixel difference between the height of the dvd avatars (at 150% size) and that of the shelf pattern. This is almost unnoticeable unless you have lots of avatars.

By the way, does anybody know how to apply a background only for a specific folder (in nautilus)?

---

### Post by Yuzem on 2007-09-16
> **Nonno Bassotto said:**
> Just a really minor thing. I think there is a 1 pixel difference between the height of the dvd avatars (at 150% size) and that of the shelf pattern. This is almost unnoticeable unless you have lots of avatars.
Are you sure? Sometimes nautilus does not align the background as it should be aligned. Try to close the nautilus window and open it again.

> **Nonno Bassotto said:**
> 
By the way, does anybody know how to apply a background only for a specific folder (in nautilus)?
From nautilus: edit > backgrounds and emblems and drag with the middle mouse button or use alt and the left button.

---

### Post by Nonno Bassotto on 2007-09-17
Ok, you're right about the alignment, now it works as it should. And now I can have customized backgrounds per folder too! :-D

---

### Post by brainiac on 2007-09-17
i ahve put audacious as mp3 player in the launcher config.. in thunar and awn everything works fine, but when i click the avatar in nautilus it only opens the .desktop file in gedit.
other .destop files will launch correctly, this only happens with avatars(and on 2 different machines).

im running the script on gutsy with yout latest deb file from the first post

---

### Post by Yuzem on 2007-09-17
Could you post the content of a non working avatar?

---

### Post by aidanr on 2007-09-17
Just messing about with screenlets, the screenlets launcher + compiz widget layer makes for a pretty nice way to use the album covers. Except it's slow(ish) with lots of launchers. I might make a script or a screenlet if I get the time.

---

### Post by aidanr on 2007-09-17
Yuzem, any chance you have an svg of the cd theme?

edit:// Nevermind, I made one up myself. I just replaced all my album art with high res versions and I want to use the cd theme so it looks all pretty in sonata :)

---

### Post by Yuzem on 2007-09-17
I don't have an svg. I didn't make the theme.
But I have a bigger png.

---

### Post by brainiac on 2007-09-18
here you are :)

```
[Desktop Entry]
Encoding=UTF-8
Name=! (1983) The Police - Synchronicity
X-MultipleArgs=false
Type=Application
Exec=avatar-factory -al music "/media/hdb1/mp3/_old/unsorted/! (1983) The Police - Synchronicity" "/home/johannes/.avatar-factory/icons/music/cd/_media_hdb1_mp3__old_unsorted_! (1983) The Police - Synchronicity.png"
Icon=/home/johannes/.avatar-factory/icons/music/cd/_media_hdb1_mp3__old_unsorted_! (1983) The Police - Synchronicity.png
URL=file:///media/hdb1/mp3/_old/unsorted/! (1983) The Police - Synchronicity

```

but as i said.. working everything except in nautilus

---

### Post by Yuzem on 2007-09-18
Here it is working as it should work.
Try to replace that content with the following and tell me if it works:
```
[Desktop Entry]
Name=! (1983) The Police - Synchronicity
Type=Application
Exec=avatar-factory -al music '/media/hdb1/mp3/_old/unsorted/! (1983) The Police - Synchronicity' '/home/johannes/.avatar-factory/icons/music/cd/_media_hdb1_mp3__old_unsorted_! (1983) The Police - Synchronicity.png'
Icon=/home/johannes/.avatar-factory/icons/music/cd/_media_hdb1_mp3__old_unsorted_! (1983) The Police - Synchronicity.png
URL=file:///media/hdb1/mp3/_old/unsorted/! (1983) The Police - Synchronicity
```

If that doesn't work I don't know... maybe a nautilus bug? :confused:

---

### Post by brainiac on 2007-09-19
nope.. also gets opened by gedit

---

### Post by Nonno Bassotto on 2007-09-19
Well, now I'd say that everything works perfectly, but I'll propose an improvement to the film grabber. Currently the cover art is downloaded from imdb; the problem is that some posters are [missing]("http://italian.imdb.com/title/tt0095869/") (especially for local or older movies) and some don't have a flat view, but rather they are a [photo of the actual dvd]("http://italian.imdb.com/title/tt0121164/"). The result is either an empty dvd avatar or an avatar of a dvd containing another dvd.

I tried to add some missing covers, but they require a 35$ fee to do this, which of course rules out the possibility that casual imdb users will update the covers.

On the other hand there are other sites than imdb which have covers for many movies. An example is the italian site [MyMovies]("http://www.mymovies.it/"). As far as I know it has covers for every film in the database, and these are all flat views of the actual posters. The problem with this site are:
1) I guess the database is  smaller than the imdb one
2) the titles are in italian only,so if you look for, say
```

pride and prejudice site:http://www.mymovies.it/

```
on Google, you are lead to the wrong page.

I could easily write a grabber to download the covers from this site, but of course it would be useful only to italian people. So I was thinking that avatar-factory could be improved in the following way.

One allows to call avatar-factory with the option "language", like in
```

avatar-factory -fg --language italian sourcefolder/*.avi targetfolder

```
When this option is called a specific grabber, called "italian", is used to download covers from a site different from imdb, in this case MyMovies. If the grabber returns an error, the generic imdb grabber is used.

In this way everyone could write a few lines to have a localized grabber which uses a more complete site than imbd for movies in that language, and these grabbers could be incorporated into your program.

Let me know what you think about this. I don't know if it is too much of a hassle, but I think it is worth the pain.

---

### Post by Yuzem on 2007-09-19
> **brainiac said:**
> nope.. also gets opened by gedit

Did you tried to change the extension to .desktop?
Try to change it from the command line. Changing the name from nautilus will not affect the extension.

> **Nonno Bassotto said:**
> 
Currently the cover art is downloaded from imdb; the problem is that some posters are missing (especially for local or older movies) and some don't have a flat view, but rather they are a photo of the actual dvd. The result is either an empty dvd avatar or an avatar of a dvd containing another dvd.
Yes, that is a problem. :(

> **Nonno Bassotto said:**
> 
I could easily write a grabber to download the covers from this site, but of course it would be useful only to italian people. So I was thinking that avatar-factory could be improved in the following way.

One allows to call avatar-factory with the option "language", like in
```

avatar-factory -fg --language italian sourcefolder/*.avi targetfolder

```
When this option is called a specific grabber, called "italian", is used to download covers from a site different from imdb, in this case MyMovies. If the grabber returns an error, the generic imdb grabber is used.

In the beginning I have thought about implementing "-go" or "--grabber-options" and "-to" or "--theme-options" to configure themes or grabbers.
For example:
```
avatar-factory -fg -go italian sourcefolder/*.avi targetfolder
```
But it was never necessary...

For now I have implemented a way to set a different picture for the film grabber by drag and drop. (it doesn't work with thunar)
If you don't like the cover just drag and drop a different picture to the avatar and thats all.
It support urls so there is no need to download the cover.
It is already working and it will be on the next version. :)

---

### Post by Nonno Bassotto on 2007-09-19
Drag and drop? Wow, these desktop files always reserve another surprise...

---

### Post by ayoli on 2007-09-21
> **foxy123 said:**
> I wonder if there is a deb for Feisty...
As I answered first , there are only gusty deb for [coverfinder on the site]("http://mookooh.org/coverfinder/").
But it's not really difficult to build. Here"s what I did
```
sudo apt-get build-essential checkinstall libgtk2.0-dev  libxml2-dev libcurl3-gnutls-dev
```
then untar [coverfinder-0.1.tar.gz]("http://mookooh.org/coverfinder/releases/coverfinder-0.1.tar.gz")
 and go in coverfinder-0.1/ directory. And finally :
```
./configure --prefix=/usr/local
```
```
make
```
```
sudo checkinstall
```
Now you have a quick made deb for coverfinder (see attachement)

---

### Post by xhilyn on 2007-09-21
Hi all.

I'm rather new to all this command line stuff so I get lost easily, so please bare with me, thanks.

Anyway I installed this one: 'avatar-factory_0.2.7-1_i386.deb' and now want to update to this one: 'AvatarFactory-0.3.3_i386.deb' but it fails with an error saying that it cannot overwrite the old one. Could anyone give me some idiot proof instructions on how to update to the latest one.

Thanks.

xhi.

---

### Post by wounded on 2007-09-21
> **xhilyn said:**
> Hi all.

I'm rather new to all this command line stuff so I get lost easily, so please bare with me, thanks.

Anyway I installed this one: 'avatar-factory_0.2.7-1_i386.deb' and now want to update to this one: 'AvatarFactory-0.3.3_i386.deb' but it fails with an error saying that it cannot overwrite the old one. Could anyone give me some idiot proof instructions on how to update to the latest one.

Thanks.

xhi.

I think it will be listed in Synaptic so you can open that and search for avatar-factory and mark it for removal and then install the newer .deb

---

### Post by xhilyn on 2007-09-21
> **wounded said:**
> I think it will be listed in Synaptic so you can open that and search for avatar-factory and mark it for removal and then install the newer .deb

Hiya.

Thanks for the quick reply.

I feel stupid as I should have thought of that myself but it did the trick so thanks again.

xhi.

---

### Post by reda_ea on 2007-09-21
that's only because package names are different
avatar-factory
and
AvatarFactory

otherwise, the package would have been automatically replaced

so the real problem here is the package creator that didn't correctly name his package (avatar-factory is the correct name)

---

### Post by brainiac on 2007-09-22
> **Yuzem said:**
> Did you tried to change the extension to .desktop?
Try to change it from the command line. Changing the name from nautilus will not affect the extension.


yeah that does the trick... so renaming every avatar is the only way to fix it?

---

### Post by Yuzem on 2007-09-22
I think that for the next version the extension will be ".desktop" by default.

---

### Post by SQuark on 2007-09-22
> **Yuzem said:**
> You can do the same without the extension and it will process all the files.
That's not an option. When I use * instead of *.avi, it breaks on subfolders. When I use *.*, it creates avatars for the subtitle files as well. It would be best if AvatarFactory could check the mimetype of the files before creating the avatar, and ignore everything that isn't a movie file.

> **Yuzem said:**
> To what file is it pointing? You can try to rename the file to get a better result.
Well, that's the weirdest thing. It's not pointing to any file at all! It's created last - after all the other avatars - and is called ".avatar".
Here are the contents:
```
[Desktop Entry]
Encoding=UTF-8
Name=
X-MultipleArgs=false
Type=Application
Exec=avatar-factory -al film ""
Icon=/home/squark/.avatar-factory/icons/film/dvd/.png
URL=file://
```

Edit:
If mimetype checking is implemented, I still think it'd be a good idea to also accept directories as input. With optional subdirectory crawling (-r). A cool extra feature would then be to add avatars for subdirectories that are called VIDEO_TS (I know at least VLC can play these). The movie title can be derived from their parent directory.
But I understand if you've got other things you want to do first. :)

---

### Post by kingofpain on 2007-09-22
> **Yuzem said:**
> There is a new version!

The film grabber will make dvds from your video files. Multiples disc are recognized with [cC][dD][1-9]
For example: cd1, Cd1, CD1, cD1, etc...
```
avatar-factory -fg ./*.avi folder/2/save
```

The same screenshot:
[[IMG]http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.th.png[/IMG]](http://img379.imageshack.us/my.php?image=avatarfactoryfg3lk3.png)



Yeah, but if you have more than 5 movies the code line takes a loong time to write. I mean: "folder1", "foler2", "folder3".... oh...
Why doesn't automatically scan one folder, like it does for music?

P.S.: I like your movie collection. Good tastes! :P

I saw some of your screenshots. Can you tell me what skin you use for pidgin?

---

### Post by Yuzem on 2007-09-22
> **SQuark said:**
> That's not an option. When I use * instead of *.avi, it breaks on subfolders. When I use *.*, it creates avatars for the subtitle files as well. It would be best if AvatarFactory could check the mimetype of the files before creating the avatar, and ignore everything that isn't a movie file.
Yes, I will implement a filter for the file source type. Already in the todo list. :)

> **SQuark said:**
> 
Well, that's the weirdest thing. It's not pointing to any file at all! It's created last - after all the other avatars - and is called ".avatar".
Here are the contents:
```
[Desktop Entry]
Encoding=UTF-8
Name=
X-MultipleArgs=false
Type=Application
Exec=avatar-factory -al film ""
Icon=/home/squark/.avatar-factory/icons/film/dvd/.png
URL=file://
```

That is already fixed (next version)

> **SQuark said:**
> 
Edit:
If mimetype checking is implemented, I still think it'd be a good idea to also accept directories as input. With optional subdirectory crawling (-r). 
You can do something like:
```
find . -type d | while read -r folder ; do cd "$folder" ; avatar-factory -fg *.avi folder/2/save ; cd "$OLDPWD" ; done
```

> **SQuark said:**
> 
A cool extra feature would then be to add avatars for subdirectories that are called VIDEO_TS (I know at least VLC can play these). The movie title can be derived from their parent directory.
But I understand if you've got other things you want to do first. :)
I am making a tv-show grabber that will work on folders. I think that it shouldn't be hard to adapt it to do that.

> **kingofpain said:**
> Yeah, but if you have more than 5 movies the code line takes a loong time to write. I mean: "folder1", "foler2", "folder3".... oh...
Why doesn't automatically scan one folder, like it does for music?

Yes, I know. But if it works on folders (recursively) it wouldn't be possible to select only one movie. Suppose that you add a new movie...
Try something like:
```
find . -type d | while read -r folder ; do cd "$folder" ; avatar-factory -fg *.avi folder/2/save ; cd "$OLDPWD" ; done
```

> **kingofpain said:**
> 
P.S.: I like your movie collection. Good tastes! :P
:)

> **kingofpain said:**
> 
I saw some of your screenshots. Can you tell me what skin you use for pidgin?

It is based on eternal aqua. I just tweaked the default skin.
Here it is if you want it:
[http://www.mytempdir.com/2025393](http://www.mytempdir.com/2025393)

---

### Post by kingofpain on 2007-09-23
> **Yuzem said:**
> Yes, I know. But if it works on folders (recursively) it wouldn't be possible to select only one movie. Suppose that you add a new movie...
Then, maybe you should make an option for that command. Say.. "avatar-factory -fg -all" will scan all folders recursively, and "avatar-factory -fg" will work with just a movie.
I don't know, It's just a suggestion, I just find that more useful.

Anyway, nice work, and thanks for the pidgin skin. ):P

---

### Post by Yuzem on 2007-09-27
In the next version the film grabber will work on folders (recursively) if a folder is specified and on files if files are specified.
The filter will get the followings formats:
avi, ogm, mpg, divx

Is there another format that should be included?

---

### Post by SQuark on 2007-09-27
mpeg (with e), mov, mp4, mkv ([Matroska](http://en.wikipedia.org/wiki/Matroska)), maybe even wmv, asf and flv? That's it off the top of my head.

---

### Post by Yuzem on 2007-09-29
Here it is the new version. :)

**tv-show grabber**
Each tv show must be in its own folder and each folder must contain a picture that will be used as the cover. When clicked a dialog will pop up asking from what episode to start playing.
[[IMG]http://img518.imageshack.us/img518/8694/avatarfactorytvshowwx8.th.png[/IMG]](http://img518.imageshack.us/my.php?image=avatarfactorytvshowwx8.png)
```
avatar-factory -g tv-show tv/shows/folder folder/2/save
```

**Graphic user interface (with zenity)**
You will find Avatar Factory in the applications menu. :)
You can also launch the gui from the console and chose what part of the gui you want. Just replace the parameter/s with "--gui"
For example:
```
avatar-factory -g music -t vinyl --name 0 music/folder folder/2/save
```

The equivalent with gui is:
```
avatar-factory -g --gui -t --gui --name --gui --gui --gui
```

Full changelog:
```
29.09.07------0.3.9
	+change to totem as the default player for film avatars
	+$avatar_title and $URL from bookmarks are set by default
	+fixed bug with folders and files source types
	+added dvd-3 theme
	+allow to set a film avatar cover by drag and drop
	+changed the extension to ".desktop"
	+added tv-show grabber
	+gui implementation with zenity
	+added [1-9][oO][fF][1-9] disc detection for the film grabber
	+allow to process folders in files  source type (film grabber)
	+added a filter for files source type
	+the music grabber will skip folders without music files inside
	+fixed bugs in film grabber
	+internal changes for launchers
```

---

### Post by aidanr on 2007-09-29
Nice work with the gui :)

Problem though, the --gui-progress progress bar reaches 100% before it's finished processing all the folders (I can see in Thunar it's still running) and hitting ok terminates the processing prematurely.

For example, I have 315 albums, if I press ok when the progress bar reaches 100% I'm left with about 110 .desktop files.

---

### Post by Nonno Bassotto on 2007-09-29
Great, a gui is just what was missing to help adoption of avatar-factory. I tried it and it seems to work well. :)

Other than that, the film grabber behaves oddly. When a cover is not found, the film is just skipped, instead that, say, displayed with a black cover. Since you implemented the cover drag and drop, this would be a better solution: one can change the cover later, if the avatar is at least created.

EDIT: I installed avatar-factory on another pc and there it creates black cover avatars. Did you change anything? Anyway, now I really don't know what improvements to suggest: it really works like a charm!

---

### Post by isaacj87 on 2007-09-30
Yuzem!!

This is the best version yet...keep up the incredible work! :)

---

### Post by CupofDice on 2007-09-30
I don't think it is working correctly for me. It creates the avatars and the avatars open the folders, but the folders are not replaced by the avatars. Am I supposed to do something else?

---

### Post by Nonno Bassotto on 2007-09-30
The folders are not supposed to be replaced by the avatars. You can access your folders as before, or use the avatars instead.

---

### Post by Yuzem on 2007-10-01
Thanks for the comments. :)

> **aidanr said:**
> Nice work with the gui :)

Problem though, the --gui-progress progress bar reaches 100% before it's finished processing all the folders (I can see in Thunar it's still running) and hitting ok terminates the processing prematurely.

For example, I have 315 albums, if I press ok when the progress bar reaches 100% I'm left with about 110 .desktop files.
mmm... I will try to fix that but I have not clue about the cause.

> **Nonno Bassotto said:**
> Great, a gui is just what was missing to help adoption of avatar-factory. I tried it and it seems to work well. :)

Other than that, the film grabber behaves oddly. When a cover is not found, the film is just skipped, instead that, say, displayed with a black cover. Since you implemented the cover drag and drop, this would be a better solution: one can change the cover later, if the avatar is at least created.
Ok, in the next version avatars for all movies will be created.

> **Nonno Bassotto said:**
> 
Sometimes I have a double album, and I usually put the cover in the main folder, together with two subfolders called CD1 and CD2. Your previous implementation created an avatar, but now that you check that a folder actually contains music, these albums are skipped.

I'm not sure if this makes sense or if I should just put two covers, one for each volume. But then I'd have plenty of avatars called CD1 or CD2...

EDIT: The music grabber works well. I think I couldn't find those albums because of the bug that aidanr pointed out.
If an avatar is created for a folder that doesn't contain any music maybe it is because the icon already exist (probably created by a previous version).
If you use the -f option or just delete the icons no avatar should be created for folders without music.
I have multiple discs in the same folder and the mp3s are named: 
"$disc.$track - $title"
They are also tagged with a disc tag, but if you prefer to use sub folders for different discs you can create a dummy file in the first folder (the one with the cover) and name it for example "album.mp3"
Avatar Factory will take that as an audio file and an avatar will be created for that folder.

---

### Post by s_spiff on 2007-10-02
I keep gettin the following error when I try to install :
```
spiff@spiffed:~/Setups/Beautify/Misc/Avatar$ sudo ./install
Password:
cp: cannot stat `avatar-factory.png': No such file or directory
cp: cannot stat `avatar-factory.desktop': No such file or directory
done
spiff@spiffed:~/Setups/Beautify/Misc/Avatar$ 

```

I didn't go through all the previous pages, so dunno if you have already provided the solution.

---

### Post by Nonno Bassotto on 2007-10-02
Did you try with the deb?

---

### Post by Yuzem on 2007-10-02
Try it again, it should work now.

---

### Post by Yuzem on 2007-10-07
New Version

**Music Widget**
Now it is posible to add an album to the playlist by drag and drop.
Just drag and drop the album to the music widget:
[[IMG]http://img374.imageshack.us/img374/8009/musicwidgetkr4.th.jpg[/IMG]](http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg)
It will work better if the widget is scaled to the maximum size.

**Avatar grabber**
The avatar grabber can edit existing avatars. It can change the theme, the name and the type.
The following comand will hide the name of the specified avatars:
```
avatar-factory -ag avatar1 avatar2 avatar3 --name 0
```
It can be used to edit the avatars from thunar or nautilus by adding a custom action.
For example in thunar go to custom actions and add this command to change the theme:
```
avatar-factory -ag -t --gui %F --gui-progress
```
To change the name:
```
avatar-factory -ag --name --gui %F --gui-progress
```
The avatar grabber will allow to implement star ratings in a future version.

```
07.10.07------0.4.2
	+fixed --gui-progress problem
	+changed the music_widget extension
	+added Index and Title tags to avatars
	+added avatar grabber
	+added --gui for --type option
	+added drag and drop support to the music widget
	+the film grabber now makes avatars for all files even if no cover was found.
```

---

### Post by aidanr on 2007-10-07
> **Yuzem said:**
> 
	+fixed --gui-progress problem


Ah much better, thanks :)

---

### Post by Nonno Bassotto on 2007-10-07
I have a couple of questions.

1) What are Index and Title tags? Where do they show up?

2) I tried to modify a theme using the avatar grabber. For example I tried

```

avatar-factory -ag -t vinyl _media_disk_Musica_King\ Crimson_1969\ -\ In\ the\ court\ of\ the\ Crimson\ King.desktop

```
but the output was
```

/usr/local/bin/avatar-factory: line 88: /usr/local/share/avatar-factory/grabbers/avatar: Nessun file o directory
/usr/local/bin/avatar-factory: line 89: grabber_primary_options: command not found
invalid source type: 
/usr/local/bin/avatar-factory: line 332: grabber_secondary_options: command not found
/usr/local/bin/avatar-factory: line 362: get_grabber_picture: command not found
There is no cover for 

```

How is it supposed to work? Actually I have no "avatar" in the grabbers directory, so I guess I'm missing something...

By the way, for those who are able to make this work and want to add an action to Nautilus there's [Nautilus actions]("http://www.grumz.net/?q=taxonomy/term/2/9").

Finally, I guess you wanted to put an image of the music widget in the original post, but it's not showing up.

---

### Post by Yuzem on 2007-10-07
> **Nonno Bassotto said:**
> I have a couple of questions.

1) What are Index and Title tags? Where do they show up?
The index and title tags are inside the avatars. Open an avatar with a text editor to see them. With those tags the avatar grabber can get the title and the index of the avatars. If you use the avatar grabber with --name 0 to hide the name you will be able to restore it.

> **Nonno Bassotto said:**
> 
2) I tried to modify a theme using the avatar grabber. For example I tried

```

avatar-factory -ag -t vinyl _media_disk_Musica_King\ Crimson_1969\ -\ In\ the\ court\ of\ the\ Crimson\ King.desktop

```
but the output was
```

/usr/local/bin/avatar-factory: line 88: /usr/local/share/avatar-factory/grabbers/avatar: Nessun file o directory
/usr/local/bin/avatar-factory: line 89: grabber_primary_options: command not found
invalid source type: 
/usr/local/bin/avatar-factory: line 332: grabber_secondary_options: command not found
/usr/local/bin/avatar-factory: line 362: get_grabber_picture: command not found
There is no cover for 

```

How is it supposed to work? Actually I have no "avatar" in the grabbers directory, so I guess I'm missing something...
Ops, sorry. I forgot to add the avatar grabber to the deb. It is fixed now.

> **Nonno Bassotto said:**
> 
Finally, I guess you wanted to put an image of the music widget in the original post, but it's not showing up.
Yes, you are right. Now it should work. :)

---

### Post by Nonno Bassotto on 2007-10-13
The music widget works fine, and it queues discs as it should. But when you close the music program and double click on the widget, only the first disc is played, even if there are more than one shown in the widget.

Can it be made to remember the discs queued and play them all?

---

### Post by Yuzem on 2007-10-13
Yes, that makes sense.
I will add that to the list. It may be on the next version.

---

### Post by isaacj87 on 2007-10-15
Hey,

How did you rotate the widgets like in your pictures?

Thanks!

---

### Post by Yuzem on 2007-10-15
You have to Drag and drop an album to the widget. The album will be added to the playlist.

---

### Post by DarkJesus on 2007-10-17
Could someone help me figure out how to make the CD and vinyl covers without using this program, just imagemagick?

---

### Post by Yuzem on 2007-10-17
If you have avatar-factory installed the themes are located in:
/usr/local/share/avatar-factory/themes

For example, you can view the source for the cd theme with:
```
gedit /usr/local/share/avatar-factory/themes/cd
```

Here it is the source for the cd theme:
```
#!/bin/bash

create_theme ()
{
convert  \
           /usr/local/share/avatar-factory/themes/CD/base.png -geometry  +0+0  -composite \
           /tmp/thumb$$.png  -geometry  +19+5  -composite \
           /usr/local/share/avatar-factory/themes/CD/top.png  -geometry +0+0  -composite \
           "$icons_PATH/$avatar_filename.png"
}
picture_aspect=$(($(identify -format %w "$grabber_picture") - $(identify -format %h "$grabber_picture")))

if [ "$picture_aspect" = "0" ]; then
        convert "$grabber_picture"  -thumbnail 98x98 /tmp/thumb$$.png
elif [ "$picture_aspect" -gt "0" ]; then
        convert "$grabber_picture"  -thumbnail 300x98 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+$(( ($(identify -format %w /tmp/thumb$$.png) - 98) / 2))+0  +repage /tmp/thumb$$.png
else
        convert "$grabber_picture"  -thumbnail 98x500 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+0+$(( ($(identify -format %h /tmp/thumb$$.png) - 98) / 2))  +repage /tmp/thumb$$.png
fi
create_theme

rm  /tmp/thumb$$.???
```

Now, you must replace the $grabber_picture variable with the path to the picture that you want to use as the cover.
You could just add this to the beginning:
```
grabber_picture=/path/2/picture.jpg
```

Finally replace "$icons_PATH/$avatar_filename.png" with something like:
/folder/2/save/album.png

This should work for almost all themes.

---

### Post by DarkJesus on 2007-10-17
I replaced "$icons_PATH/$avatar_filename.png" with ~/cover.png and I get:

```
convert: missing an image filename `~/album.png'.
```

Thanks for helping so far.

---

### Post by Yuzem on 2007-10-17
mmm... it is working here.
Here it is the code:
```
#!/bin/bash
grabber_picture=~/cover.jpg

create_theme ()
{
convert  \
           /usr/local/share/avatar-factory/themes/CD/base.png -geometry  +0+0  -composite \
           /tmp/thumb$$.png  -geometry  +19+5  -composite \
           /usr/local/share/avatar-factory/themes/CD/top.png  -geometry +0+0  -composite \
           ~/album.png
}
picture_aspect=$(($(identify -format %w "$grabber_picture") - $(identify -format %h "$grabber_picture")))

if [ "$picture_aspect" = "0" ]; then
        convert "$grabber_picture"  -thumbnail 98x98 /tmp/thumb$$.png
elif [ "$picture_aspect" -gt "0" ]; then
        convert "$grabber_picture"  -thumbnail 300x98 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+$(( ($(identify -format %w /tmp/thumb$$.png) - 98) / 2))+0  +repage /tmp/thumb$$.png
else
        convert "$grabber_picture"  -thumbnail 98x500 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+0+$(( ($(identify -format %h /tmp/thumb$$.png) - 98) / 2))  +repage /tmp/thumb$$.png
fi
create_theme

rm  /tmp/thumb$$.???
```

Take a look at the lines 2 and 10.
You only need a picture named "cover.jpg" in your home folder.

---

### Post by DarkJesus on 2007-10-18
Changed it just a teeny bit:

```
#!/bin/bash
grabber_picture=~/cover.png

create_theme ()
{
convert  \
           /home/shane-arch/Desktop/avatar-factory-0.4.2/themes/CD/base.png -geometry  +0+0  -composite \
           /tmp/thumb$$.png  -geometry  +19+5  -composite \
           /home/shane-arch/Desktop/avatar-factory-0.4.2/themes/CD/top.png  -geometry +0+0  -composite \
           ~/album.png
}
picture_aspect=$(($(identify -format %w "$grabber_picture") - $(identify -format %h "$grabber_picture")))

if [ "$picture_aspect" = "0" ]; then
        convert "$grabber_picture"  -thumbnail 98x98 /tmp/thumb$$.png
elif [ "$picture_aspect" -gt "0" ]; then
        convert "$grabber_picture"  -thumbnail 300x98 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+$(( ($(identify -format %w /tmp/thumb$$.png) - 98) / 2))+0  +repage /tmp/thumb$$.png
else
        convert "$grabber_picture"  -thumbnail 98x500 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+0+$(( ($(identify -format %h /tmp/thumb$$.png) - 98) / 2))  +repage /tmp/thumb$$.png
fi
create_theme

rm  /tmp/thumb$$.???
```

And as you can see from [the screenshot]("ftp://light.londonmet.ac.uk/uploads/albumnotworking.png"), it doesn't work.

---

### Post by Yuzem on 2007-10-18
Strange...
Try this:
```
#!/bin/bash
grabber_picture=$HOME/cover.png

create_theme ()
{
convert  \
           /home/shane-arch/Desktop/avatar-factory-0.4.2/themes/CD/base.png -geometry  +0+0  -composite \
           /tmp/thumb$$.png  -geometry  +19+5  -composite \
           /home/shane-arch/Desktop/avatar-factory-0.4.2/themes/CD/top.png  -geometry +0+0  -composite \
           $HOME/album.png
}
picture_aspect=$(($(identify -format %w "$grabber_picture") - $(identify -format %h "$grabber_picture")))

if [ "$picture_aspect" = "0" ]; then
        convert "$grabber_picture"  -thumbnail 98x98 /tmp/thumb$$.png
elif [ "$picture_aspect" -gt "0" ]; then
        convert "$grabber_picture"  -thumbnail 300x98 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+$(( ($(identify -format %w /tmp/thumb$$.png) - 98) / 2))+0  +repage /tmp/thumb$$.png
else
        convert "$grabber_picture"  -thumbnail 98x500 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+0+$(( ($(identify -format %h /tmp/thumb$$.png) - 98) / 2))  +repage /tmp/thumb$$.png
fi
create_theme

rm  /tmp/thumb$$.???
```

If it doesn't work try this:
```
#!/bin/bash
grabber_picture=/home/shane-arch/cover.png

create_theme ()
{
convert  \
           /home/shane-arch/Desktop/avatar-factory-0.4.2/themes/CD/base.png -geometry  +0+0  -composite \
           /tmp/thumb$$.png  -geometry  +19+5  -composite \
           /home/shane-arch/Desktop/avatar-factory-0.4.2/themes/CD/top.png  -geometry +0+0  -composite \
           /home/shane-arch/album.png
}
picture_aspect=$(($(identify -format %w "$grabber_picture") - $(identify -format %h "$grabber_picture")))

if [ "$picture_aspect" = "0" ]; then
        convert "$grabber_picture"  -thumbnail 98x98 /tmp/thumb$$.png
elif [ "$picture_aspect" -gt "0" ]; then
        convert "$grabber_picture"  -thumbnail 300x98 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+$(( ($(identify -format %w /tmp/thumb$$.png) - 98) / 2))+0  +repage /tmp/thumb$$.png
else
        convert "$grabber_picture"  -thumbnail 98x500 /tmp/thumb$$.png
        convert /tmp/thumb$$.png -crop 98x98+0+$(( ($(identify -format %h /tmp/thumb$$.png) - 98) / 2))  +repage /tmp/thumb$$.png
fi
create_theme

rm  /tmp/thumb$$.???
```

---

### Post by DarkJesus on 2007-10-18
Neither work. I still get:

```
convert: missing an image filename `/home/shane-arch/album.png'.
```

---

### Post by Yuzem on 2007-10-18
You got a P.M.

---

### Post by SQuark on 2007-10-20
Alright, I've got some more requests! :D

I've got two files, named "Chocolat (1of2).avi" and "Chocolat (2of2).avi", these get turned into two .desktop files, both named "Chocolat ()". Since launching either .desktop file enqueues both .avis, it'd be better to have just one .desktop file. And I'd prefer if it was just called "Chocolat", without the extra space and brackets.

Could you also include .cue files? These are part of .bin/.cue image and can be played in VLC (not sure about other movie players though).

Would it be possible to make a variant of the tv-show grabber that functions like the film grabber? (I.e. it gets the DVD covers from an IMDb search.)

Oh and btw, avatar-factory rocks!

---

### Post by Yuzem on 2007-10-20
> **SQuark said:**
> Alright, I've got some more requests! :D

I've got two files, named "Chocolat (1of2).avi" and "Chocolat (2of2).avi", these get turned into two .desktop files, both named "Chocolat ()". Since launching either .desktop file enqueues both .avis, it'd be better to have just one .desktop file. And I'd prefer if it was just called "Chocolat", without the extra space and brackets.
It is fixed. (next version) :)

> **SQuark said:**
> 
Could you also include .cue files? These are part of .bin/.cue image and can be played in VLC (not sure about other movie players though).
Ok, no problem. (in the next version)

> **SQuark said:**
> 
Would it be possible to make a variant of the tv-show grabber that functions like the film grabber? (I.e. it gets the DVD covers from an IMDb search.)
I can make it search first for a picture (like it is now)
If it doesn't find any cover it search imdb like the film grabber but based on the name of the folder.

---

### Post by SQuark on 2007-10-20
Cool!
You're the best! :)

---

### Post by SQuark on 2007-10-21
Hi, me again. :)

Could you make the tv-show grabber list every movie file, not only in the selected directory, but also in all subdirs? Because more often than not, I'd have a subdir for each season.

Could you add a "picture=" option to the config file, to open the picture directory in a picture viewer (gqview, gthumb,...) instead of the file browser?

And maybe an option to pick the pictures at random (or uniformly spread), instead of the last three?

Ok, I think I've run out of requests for now. :D

---

### Post by Yuzem on 2007-10-22
> **SQuark said:**
> Hi, me again. :)

Could you make the tv-show grabber list every movie file, not only in the selected directory, but also in all subdirs? Because more often than not, I'd have a subdir for each season.
Maybe instead of listing all the chapters in the same dialog if there are many seasons a dialog to select the season could pop up first and then another for the episodes for the chosen season.
But there is one problem, the grabbers checks if there are video files inside the folders.
If you have subdirs for each season how to differentiate a directory with no video files that have subdirs for seasons and should be processed from a directory with no video files that should not be processed.
And how to know if the subdirs are seasons and not entire shows.
I like the idea but I don't want to implement it in a nasty way.

> **SQuark said:**
> 
Could you add a "picture=" option to the config file, to open the picture directory in a picture viewer (gqview, gthumb,...) instead of the file browser?
Yes, of course, in the next version.

> **SQuark said:**
> 
And maybe an option to pick the pictures at random (or uniformly spread), instead of the last three?
I will add that to the toDO list but I don't know when it will be implemented.

> **SQuark said:**
> 
Ok, I think I've run out of requests for now. :D
Thanks for the good ideas! :)

---

### Post by Hakimio on 2007-10-28
How do I make the album art displayed on desktop by music widget bigger and how do make that album art would be removed from desktop when I exit the player (audacious)?

---

### Post by Nonno Bassotto on 2007-10-28
You can resize the widget, like any other icon, by right clicking on it and choosing resize.

---

### Post by Yuzem on 2007-10-28
> **Hakimio said:**
> how do make that album art would be removed from desktop when I exit the player (audacious)?
For that you must run avatar-music-widget but it is broken in the last version. I will fix it for the next one.

---

### Post by Timsy321 on 2007-10-28
Could you please post some of those backgrounds that you have for your windows. Especially the DVD shelf one that would be awesome. Also is there any way to make the DVD thumbnails better quality?

---

### Post by Yuzem on 2007-10-28
The backgrounds are included in the tar archive.
You can increase the size of the icons with ctrl ++ key from thunar or nautilus.
If you want to apply a background to only one folder you can do it by dragging it with the middle mouse button.

---

### Post by Timsy321 on 2007-10-29
Hey thanks for the tips! But when i try and move the image file for the background over with the middle click, it still changes all of the older folders. Is there another way to do this? Like a keyboard shortcut or something? Thanks!

---

### Post by Timsy321 on 2007-10-29
Alright i figured that out. Thanks anyways! Is there anyway to have it monitor a folder? So i don't have to keep adding the folder everytime after i make a new movie?

---

### Post by Yuzem on 2007-10-29
You can use a cron to do that:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Or use the graphic interface:
```
sudo apt-get install gnome-schedule
```

---

### Post by Forlong on 2007-11-01
I can't believe this hasn't already been requested: please add support for [Listen](http://www.listen-project.org/).
Thanks.

Project looks cool.

---

### Post by meindian523 on 2007-11-02
The --type 0 option for music grabber doesn't work for me.:(

When I double click the avatar,it opens a new amaroK window and starts playing......doesn't send me to the music folder.I used this command:
```

easwarh@l1nuxr0cks:~$ avatar-factory --type 0 -mg /home/easwarh/Music/ /home/easwarh/Avatars/

```

Isn't that correct?

---

### Post by Yuzem on 2007-11-02
> **Forlong said:**
> I can't believe this hasn't already been requested: please add support for [Listen](http://www.listen-project.org/).
Thanks.

Project looks cool.
Ok, no problem.

> **meindian523 said:**
> The --type 0 option for music grabber doesn't work for me.:(

When I double click the avatar,it opens a new amaroK window and starts playing......doesn't send me to the music folder.I used this command:
```

easwarh@l1nuxr0cks:~$ avatar-factory --type 0 -mg /home/easwarh/Music/ /home/easwarh/Avatars/

```

Isn't that correct?
Each grabber sets some default options. The default options for the music grabber are --type 1 --name 3 and -t cd.
You must specified any option after the grabber so it overwrites the default grabber option:
```
avatar-factory -mg --type 0 /home/easwarh/Music/ /home/easwarh/Avatars/
```

---

### Post by Yuzem on 2007-11-02
New version:
-----------------------------------------------------------------

Avatar launcher:
If you have for example your music avatars acting like folders (--type 0) you will be able to execute the launcher action (--type 1) with the following command:
avatar-factory -al path/2/avatar.desktop
It can be used to make a thunar or a nautilus action.

Picture launcher:
Now there is a launcher for the picture grabber.
The default associated program is eog but it can be changed by adding the following to the configuration file (~/.avatar-factory/avatar-launcher):
picture="app-name"

02.11.07------0.4.6
+music widget: allow to play all discs when clicked
+film grabber: fixed duplicated files with [1-9][oO][fF][1-9] disc detection
+film grabber: added [(][1-9][oO][fF][1-9][)] disc detection
+film grabber: added cue file type
+avatar launcher: added support for avatar files
+added picture launcher
+now running avatar-factory with no parameter brings the GUI
+avatar-music-widget: fixes
+avatar-music-widget replaced by avatar-factory --widget
+tv-show: if no cover is found it searches online like the film grabber
+music grabber: added support for flac files.
+music launcher: added support for "listen" music player

---

### Post by meindian523 on 2007-11-03
```

easwarh@l1nuxr0cks:~$ avatar-factory -mg --type 0 /home/easwarh/Music/ /home/easwarh/Avatars/
--type does not exist
easwarh@l1nuxr0cks:~$ 
```
:(

---

### Post by Yuzem on 2007-11-03
Strange... that is working here.
I have no clue. :confused:

What distro are you using?
What is your bash version? (bash --version)

Try uninstalling avatar-factory and installing the latest version.

If that doesn't work try this:
```
avatar-factory -mg  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
```

and/or this:
```
avatar-factory -g music  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
```

---

### Post by meindian523 on 2007-11-03
> **Yuzem said:**
> Strange... that is working here.
I have no clue. :confused:

What distro are you using?
What is your bash version? (bash --version)

Try uninstalling avatar-factory and installing the latest version.

Ubuntu Feisty,bash version 3.2.13
> **Yuzem said:**
> 
If that doesn't work try this:
```
avatar-factory -mg  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
```

This worked......thanks.

> **Yuzem said:**
> 
and/or this:
```
avatar-factory -g music  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
```

The one above just gave me the error with the tutorial,if I may call it that,telling us about the "proper" options.

Suggestion:Please put that options page in a man page....easier to access than purposely make a mistake and get the correction....

---

### Post by Yuzem on 2007-11-03
Yes, I am working on a man page, but that error that you had is very strange, I can't reproduce it.

---

### Post by meindian523 on 2007-11-04
I'm able to reproduce it...I can help with debugging,but beware I know very little about shell scripting and you would have to guide(train?) me to look out for the fault in the logic.

---

### Post by SQuark on 2007-11-04
My .mkv files aren't being picked up anymore (neither by the film grabber, nor the tv show grabber).

Apart from that, really nice update! Everything seems to be working rather well!

Just waiting for the season support for the tv-show grabber now. :D

---

### Post by Yuzem on 2007-11-04
> **meindian523 said:**
> I'm able to reproduce it...I can help with debugging,but beware I know very little about shell scripting and you would have to guide(train?) me to look out for the fault in the logic.
Ok, then do this:
```
sudo gedit /usr/local/bin/avatar-factory
```
Change the first line:
```
#!/bin/bash
```
with:
```
#!/bin/bash -x
```
save and execute the non working commands:
```
avatar-factory -mg --type 0 /home/easwarh/Music/ /home/easwarh/Avatars/
```
and:
```
avatar-factory -g music  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
```
...and post the output.
Oh, and thanks for your help :)

> **SQuark said:**
> My .mkv files aren't being picked up anymore (neither by the film grabber, nor the tv show grabber).
mmm... another error that a can't reproduce.
I just create a blank file called "kill bill.mkv" and the grabber worked as expected.

> **SQuark said:**
> 
Just waiting for the season support for the tv-show grabber now. :D
I was thinking in detecting seasons by the name of the folder. If the name start with "season" then it will be skipped and taken as a season.

---

### Post by jayde6 on 2007-11-04
First I'd like to say thank you for an amazing bit of software. Secondly I am having the same problem as SQuark's with the addition of having some .mp4 files that were also not grabbed. As a temporary fix I have changed the extension to .avi (since mplayer will play it regardless) and everything works fine.

---

### Post by meindian523 on 2007-11-04
Yuzem:

```
easwarh@l1nuxr0cks:~$ avatar-factory -mg --type 0 /home/easwarh/Music/ /home/easwarh/Avatars/debugtest/
+ '[' 5 = 0 ']'
+ '[' -mg '!=' '' ']'
+ case $1 in
+ grabber_name=music
+ theme_name=cd
+ Link_or_Application=Application
+ shift
+ '[' -e --type ']'
+ echo '--type does not exist'
--type does not exist
+ exit
easwarh@l1nuxr0cks:~$ 
```

and:

```
easwarh@l1nuxr0cks:~$ avatar-factory -g music  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
+ '[' 6 = 0 ']'
+ '[' -g '!=' '' ']'
+ case $1 in
+ usage
+ echo '-mg --music-grabber     Make music avatars.
        Example: avatar-factory -mg music/album/path folder/2/save

-cg --comic-grabber     Make comic avatars. (not working yet)
-pg --picture-grabber   Make picture avatars.
-fg --film-grabber      Make film avatars. (Right now this will create dvd avatars from imdb firefox bookmarks)
        Example: avatar-factory -fg -firefox folder/2/save

-t --theme              Set a different theme.
        Example: avatar-factory -mg . "somepath" -t vinyl

-lt --list-themes       List available themes.
--name                  Set the avatar name. 0=no name, 1=index, 2=title, 3(1+2)=index.title
        Example: --name 0

--type                  Play or Open the folder. 0=open the folder, 1=play
-h --help               Print usage and exit.'
-mg --music-grabber     Make music avatars.
        Example: avatar-factory -mg music/album/path folder/2/save

-cg --comic-grabber     Make comic avatars. (not working yet)
-pg --picture-grabber   Make picture avatars.
-fg --film-grabber      Make film avatars. (Right now this will create dvd avatars from imdb firefox bookmarks)
        Example: avatar-factory -fg -firefox folder/2/save

-t --theme              Set a different theme.
        Example: avatar-factory -mg . "somepath" -t vinyl

-lt --list-themes       List available themes.
--name                  Set the avatar name. 0=no name, 1=index, 2=title, 3(1+2)=index.title
        Example: --name 0

--type                  Play or Open the folder. 0=open the folder, 1=play
-h --help               Print usage and exit.
+ exit
easwarh@l1nuxr0cks:~$ 

```

and BTW,I downloaded the deb for 0.4.6.Had to remove the old package( 0.2.8 ) which had the above problems....I think the same problem exists in this version but to be sure I need a clarification: (I'm using the GUI)
Is the name scheme dialog just asking us to select the --type option?If yes,the option 0(no name) doesn't send me to the folder.It opens the album in Amarok,clearing the current playlist.....the same occurs with all the other options too.....!

---

### Post by Yuzem on 2007-11-04
> **jayde6 said:**
> First I'd like to say thank you for an amazing bit of software. Secondly I am having the same problem as SQuark's with the addition of having some .mp4 files that were also not grabbed. As a temporary fix I have changed the extension to .avi (since mplayer will play it regardless) and everything works fine.
I can reproduce that neither.
Could you or someone with the same problem do the same thing that meindian523 did?

> **meindian523 said:**
> Yuzem:

```
easwarh@l1nuxr0cks:~$ avatar-factory -mg --type 0 /home/easwarh/Music/ /home/easwarh/Avatars/debugtest/
+ '[' 5 = 0 ']'
+ '[' -mg '!=' '' ']'
+ case $1 in
+ grabber_name=music
+ theme_name=cd
+ Link_or_Application=Application
+ shift
+ '[' -e --type ']'
+ echo '--type does not exist'
--type does not exist
+ exit
easwarh@l1nuxr0cks:~$ 
```

and:

```
easwarh@l1nuxr0cks:~$ avatar-factory -g music  /home/easwarh/Music/  /home/easwarh/Avatars/  --type 0
+ '[' 6 = 0 ']'
+ '[' -g '!=' '' ']'
+ case $1 in
+ usage
+ echo '-mg --music-grabber     Make music avatars.
        Example: avatar-factory -mg music/album/path folder/2/save

-cg --comic-grabber     Make comic avatars. (not working yet)
-pg --picture-grabber   Make picture avatars.
-fg --film-grabber      Make film avatars. (Right now this will create dvd avatars from imdb firefox bookmarks)
        Example: avatar-factory -fg -firefox folder/2/save

-t --theme              Set a different theme.
        Example: avatar-factory -mg . "somepath" -t vinyl

-lt --list-themes       List available themes.
--name                  Set the avatar name. 0=no name, 1=index, 2=title, 3(1+2)=index.title
        Example: --name 0

--type                  Play or Open the folder. 0=open the folder, 1=play
-h --help               Print usage and exit.'
-mg --music-grabber     Make music avatars.
        Example: avatar-factory -mg music/album/path folder/2/save

-cg --comic-grabber     Make comic avatars. (not working yet)
-pg --picture-grabber   Make picture avatars.
-fg --film-grabber      Make film avatars. (Right now this will create dvd avatars from imdb firefox bookmarks)
        Example: avatar-factory -fg -firefox folder/2/save

-t --theme              Set a different theme.
        Example: avatar-factory -mg . "somepath" -t vinyl

-lt --list-themes       List available themes.
--name                  Set the avatar name. 0=no name, 1=index, 2=title, 3(1+2)=index.title
        Example: --name 0

--type                  Play or Open the folder. 0=open the folder, 1=play
-h --help               Print usage and exit.
+ exit
easwarh@l1nuxr0cks:~$ 

```

Could you do the same but with the last version?

> **meindian523 said:**
> 
and BTW,I downloaded the deb for 0.4.6.Had to remove the old package( 0.2.8 ) which had the above problems....I think the same problem exists in this version but to be sure I need a clarification: (I'm using the GUI)
Is the name scheme dialog just asking us to select the --type option?If yes,the option 0(no name) doesn't send me to the folder.It opens the album in Amarok,clearing the current playlist.....the same occurs with all the other options too.....!
No, there is no gui for the --type option.

---

### Post by jayde6 on 2007-11-05
I made a fake mkv file, using the previous example of kill bill and found that for me film grabber works but tv-show grabber does not. This is the output for the tv-show grabber.
Thanks for your time.


```
jayde6@jayde6-desktop:~$ avatar-factory -g tv-show /home/jayde6/test/ /home/jayde6/ --type 0
+ grabbers_PATH=/usr/local/share/avatar-factory/grabbers
+ launchers_PATH=/usr/local/share/avatar-factory/launchers
+ themes_PATH=/usr/local/share/avatar-factory/themes
+ ratings_PATH=/usr/local/share/avatar-factory/themes
+ '[' 6 = 0 ']'
+ number=0
+ '[' -g '!=' '' ']'
+ case $1 in
+ shift
+ '[' tv-show = --gui ']'
+ '[' -f /usr/local/share/avatar-factory/grabbers/tv-show ']'
+ grabber_name=tv-show
+ . /usr/local/share/avatar-factory/grabbers/tv-show
+ grabber_primary_options
+ theme_name=dvd-3
+ Link_or_Application=Application
+ SOURCE_type=folders
+ shift
+ '[' /home/jayde6/test/ '!=' '' ']'
+ case $1 in
+ number=1
+ SOURCE_input[$number]=/home/jayde6/test/
+ shift
+ '[' /home/jayde6/ '!=' '' ']'
+ case $1 in
+ number=2
+ SOURCE_input[$number]=/home/jayde6/
+ shift
+ '[' --type '!=' '' ']'
+ case $1 in
+ shift
+ Link_or_Application=0
+ '[' 0 = --gui ']'
+ case $Link_or_Application in
+ Link_or_Application=Link
+ shift
+ '[' '' '!=' '' ']'
+ '[' tv-show = avatar ']'
+ '[' /home/jayde6/ = --gui ']'
+ '[' -d /home/jayde6/ ']'
+ cd /home/jayde6/
++ pwd
+ folder2save=/home/jayde6
+ cd /home/jayde6
+ SOURCE_input[$number]=
+ max_number=1
+ case $SOURCE_type in
+ [[ /home/jayde6/test/  = '' ]]
+ number=0
+ '[' 0 -lt 1 ']'
+ number=1
+ '[' /home/jayde6/test/ = --gui ']'
+ '[' -d /home/jayde6/test/ ']'
+ '[' 1 -lt 1 ']'
+ number=0
+ echo 'Building list of folders to process...'
Building list of folders to process...
+ '[' 0 -lt 1 ']'
+ number=1
+ cd /home/jayde6/test/
++ pwd
+ SOURCE_input=/home/jayde6/test
+ cd /home/jayde6
+ [[ -n '' ]]
++ find -L /home/jayde6/test -type d '!' -path '/home/jayde6/test*/.*' -print
++ sort
+ SOURCE_list[$number]='/home/jayde6/test
/home/jayde6/test/kill bill'
+ [[ 1 != \1 ]]
+ '[' 1 -lt 1 ']'
+ number=1
+ index=1
+ set_index=
++ echo '/home/jayde6/test
/home/jayde6/test/kill bill'
++ wc -l
+ total_lines=2
+ echo '/home/jayde6/test
/home/jayde6/test/kill bill'
+ read -r SOURCE_item
+ [[ folders = bookmarks ]]
+ grabber_secondary_options
+ avatar_title=test
++ echo /home/jayde6/test
+ [[ -n '' ]]
+ cat
++ sed 's/\//\_/g'
+ avatar_filename=_home_jayde6_test
+ avatar_name=test
+ URL=file:///home/jayde6/test
+ Launcher='avatar-factory -al tv-show --URL "/home/jayde6/test" --name "test" --title "test" --icon "/_home_jayde6_test.png" --DND'
+ icons_PATH=/home/jayde6/.avatar-factory/icons/tv-show/dvd-3
+ '[' -f /home/jayde6/_home_jayde6_test.desktop -a -z '' ']'
+ '[' -n '' ']'
+ '[' -f /home/jayde6/.avatar-factory/icons/tv-show/dvd-3/_home_jayde6_test.png -a -z '' ']'
+ get_grabber_picture
++ find /home/jayde6/test -maxdepth 1 -type f '(' -iname '*.avi' -or -iname '*.ogg' -or -iname '*.mpg' ')' -print -quit
+ [[ '' != '' ]]
+ grabber_picture=
+ '[' -n '' ']'
+ grabber_picture=no
+ '[' no = no ']'
+ grabber_picture=
+ echo 'There is no cover for test'
There is no cover for test
+ read -r SOURCE_item
+ [[ folders = bookmarks ]]
+ grabber_secondary_options
+ avatar_title='kill bill'
++ echo /home/jayde6/test/kill bill
++ sed 's/\//\_/g'
+ avatar_filename='_home_jayde6_test_kill bill'
+ avatar_name='kill bill'
+ URL='file:///home/jayde6/test/kill bill'
+ Launcher='avatar-factory -al tv-show --URL "/home/jayde6/test/kill bill" --name "kill bill" --title "kill bill" --icon "/home/jayde6/.avatar-factory/icons/tv-show/dvd-3/_home_jayde6_test_kill bill.png" --DND'
+ icons_PATH=/home/jayde6/.avatar-factory/icons/tv-show/dvd-3
+ '[' -f '/home/jayde6/_home_jayde6_test_kill bill.desktop' -a -z '' ']'
+ '[' -n '' ']'
+ '[' -f '/home/jayde6/.avatar-factory/icons/tv-show/dvd-3/_home_jayde6_test_kill bill.png' -a -z '' ']'
+ get_grabber_picture
++ find '/home/jayde6/test/kill bill' -maxdepth 1 -type f '(' -iname '*.avi' -or -iname '*.ogg' -or -iname '*.mpg' ')' -print -quit
+ [[ '' != '' ]]
+ grabber_picture=
+ '[' -n '' ']'
+ grabber_picture=no
+ '[' no = no ']'
+ grabber_picture=
+ echo 'There is no cover for kill bill'
There is no cover for kill bill
+ read -r SOURCE_item

```

---

### Post by meindian523 on 2007-11-05
> **Yuzem said:**
> 
Could you do the same but with the last version?

You mean that I give the above(non-working) commands with 0.4.6?

> **Yuzem said:**
> 
No, there is no gui for the --type option.

Ok,then how do we make the avatars cd to the directory where the music is stored?Using CLI?

---

### Post by ayoli on 2007-11-05
I have an issue with the latest version 0.46. I used the GUI to create music avatars, it worked but now, when I double click on an avatar in nautilus it opens the desktop file in the text editor.
The weird thing is that the AWN file-browser plugin open avatars in my music player, but don't show the icons !
Did I miss something ?
Also, how do I turn the music widget on ?

edit : I copy and paste in a term an exec line from an avatar, it launches audacious well and give info about the music widget:
```

&#9484;-(1003:lun,05 nov 07.ayoli@zone)&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;(/home/ayoli)&#9472;&#9472;
&#9492;&#9472;($)&#9472;> avatar-factory -al music --URL "/media/store/musique/dub/Augustus_Pablo-Dubbing_Inna_Africa_Goibes-1976-[mute]" --name "Augustus_Pablo-Dubbing_Inna_Africa_Goodvibes-1976-[mute]" --title "Augustus_Pablo-Dubbing_Inna_Africa_Goodvibes-1976-[mute]" --icon "/home/ayoli/.avatar-factory/icons/music/cd/_media_store_musique_dub_Augustus_Pablo-Dubbing_Inna_Africa_Goodvibes-1976-[mute].png" --DND
/home/ayoli/.avatar-factory/avatar-launcher: line 2: music-widget=yes : commande introuvable
/usr/local/share/avatar-factory/launchers/music: line 137: /home/ayoli/Desktop/music_widget.desktop: Aucun fichier ou répertoire de ce type

```
Last line says that music can't find home/ayoli/Desktop/music_widget.desktop and this is normal since Im french and the Desktop folder is named Bureau in french.
But I still don't understatnd why double clic opens text editor instead of launching the album in audacious.

edit 2 : ok edited music-widget and launchers/music, changed 'Desktop' for 'Bureau'  3 times, now the music-widget works. You got a localisation problem here :)

---

### Post by jayde6 on 2007-11-05
I don't know if it is related to your problem ayoli but I keep both my media and my avatars on a seperate partition and if I go into the partition and click them it loads up the 'do you want to open in text editor dialog'. However I have a symlink in my home folder that leads to there and when I go through my symlink and click the avatar it works correctly. Don't know if any of this will help in a solution but worth noting I think.

---

### Post by Yuzem on 2007-11-05
> **jayde6 said:**
> I made a fake mkv file, using the previous example of kill bill and found that for me film grabber works but tv-show grabber does not. This is the output for the tv-show grabber.
Thanks for your time.


```
jayde6@jayde6-desktop:~$ avatar-factory -g tv-show /home/jayde6/test/ /home/jayde6/ --type 0
+ grabbers_PATH=/usr/local/share/avatar-factory/grabbers
+ launchers_PATH=/usr/local/share/avatar-factory/launchers
+ themes_PATH=/usr/local/share/avatar-factory/themes
+ ratings_PATH=/usr/local/share/avatar-factory/themes
+ '[' 6 = 0 ']'
+ number=0
+ '[' -g '!=' '' ']'
+ case $1 in
+ shift
+ '[' tv-show = --gui ']'
+ '[' -f /usr/local/share/avatar-factory/grabbers/tv-show ']'
+ grabber_name=tv-show
+ . /usr/local/share/avatar-factory/grabbers/tv-show
+ grabber_primary_options
+ theme_name=dvd-3
+ Link_or_Application=Application
+ SOURCE_type=folders
+ shift
+ '[' /home/jayde6/test/ '!=' '' ']'
+ case $1 in
+ number=1
+ SOURCE_input[$number]=/home/jayde6/test/
+ shift
+ '[' /home/jayde6/ '!=' '' ']'
+ case $1 in
+ number=2
+ SOURCE_input[$number]=/home/jayde6/
+ shift
+ '[' --type '!=' '' ']'
+ case $1 in
+ shift
+ Link_or_Application=0
+ '[' 0 = --gui ']'
+ case $Link_or_Application in
+ Link_or_Application=Link
+ shift
+ '[' '' '!=' '' ']'
+ '[' tv-show = avatar ']'
+ '[' /home/jayde6/ = --gui ']'
+ '[' -d /home/jayde6/ ']'
+ cd /home/jayde6/
++ pwd
+ folder2save=/home/jayde6
+ cd /home/jayde6
+ SOURCE_input[$number]=
+ max_number=1
+ case $SOURCE_type in
+ [[ /home/jayde6/test/  = '' ]]
+ number=0
+ '[' 0 -lt 1 ']'
+ number=1
+ '[' /home/jayde6/test/ = --gui ']'
+ '[' -d /home/jayde6/test/ ']'
+ '[' 1 -lt 1 ']'
+ number=0
+ echo 'Building list of folders to process...'
Building list of folders to process...
+ '[' 0 -lt 1 ']'
+ number=1
+ cd /home/jayde6/test/
++ pwd
+ SOURCE_input=/home/jayde6/test
+ cd /home/jayde6
+ [[ -n '' ]]
++ find -L /home/jayde6/test -type d '!' -path '/home/jayde6/test*/.*' -print
++ sort
+ SOURCE_list[$number]='/home/jayde6/test
/home/jayde6/test/kill bill'
+ [[ 1 != \1 ]]
+ '[' 1 -lt 1 ']'
+ number=1
+ index=1
+ set_index=
++ echo '/home/jayde6/test
/home/jayde6/test/kill bill'
++ wc -l
+ total_lines=2
+ echo '/home/jayde6/test
/home/jayde6/test/kill bill'
+ read -r SOURCE_item
+ [[ folders = bookmarks ]]
+ grabber_secondary_options
+ avatar_title=test
++ echo /home/jayde6/test
+ [[ -n '' ]]
+ cat
++ sed 's/\//\_/g'
+ avatar_filename=_home_jayde6_test
+ avatar_name=test
+ URL=file:///home/jayde6/test
+ Launcher='avatar-factory -al tv-show --URL "/home/jayde6/test" --name "test" --title "test" --icon "/_home_jayde6_test.png" --DND'
+ icons_PATH=/home/jayde6/.avatar-factory/icons/tv-show/dvd-3
+ '[' -f /home/jayde6/_home_jayde6_test.desktop -a -z '' ']'
+ '[' -n '' ']'
+ '[' -f /home/jayde6/.avatar-factory/icons/tv-show/dvd-3/_home_jayde6_test.png -a -z '' ']'
+ get_grabber_picture
++ find /home/jayde6/test -maxdepth 1 -type f '(' -iname '*.avi' -or -iname '*.ogg' -or -iname '*.mpg' ')' -print -quit
+ [[ '' != '' ]]
+ grabber_picture=
+ '[' -n '' ']'
+ grabber_picture=no
+ '[' no = no ']'
+ grabber_picture=
+ echo 'There is no cover for test'
There is no cover for test
+ read -r SOURCE_item
+ [[ folders = bookmarks ]]
+ grabber_secondary_options
+ avatar_title='kill bill'
++ echo /home/jayde6/test/kill bill
++ sed 's/\//\_/g'
+ avatar_filename='_home_jayde6_test_kill bill'
+ avatar_name='kill bill'
+ URL='file:///home/jayde6/test/kill bill'
+ Launcher='avatar-factory -al tv-show --URL "/home/jayde6/test/kill bill" --name "kill bill" --title "kill bill" --icon "/home/jayde6/.avatar-factory/icons/tv-show/dvd-3/_home_jayde6_test_kill bill.png" --DND'
+ icons_PATH=/home/jayde6/.avatar-factory/icons/tv-show/dvd-3
+ '[' -f '/home/jayde6/_home_jayde6_test_kill bill.desktop' -a -z '' ']'
+ '[' -n '' ']'
+ '[' -f '/home/jayde6/.avatar-factory/icons/tv-show/dvd-3/_home_jayde6_test_kill bill.png' -a -z '' ']'
+ get_grabber_picture
++ find '/home/jayde6/test/kill bill' -maxdepth 1 -type f '(' -iname '*.avi' -or -iname '*.ogg' -or -iname '*.mpg' ')' -print -quit
+ [[ '' != '' ]]
+ grabber_picture=
+ '[' -n '' ']'
+ grabber_picture=no
+ '[' no = no ']'
+ grabber_picture=
+ echo 'There is no cover for kill bill'
There is no cover for kill bill
+ read -r SOURCE_item

```
Ah, the tv-show grabber doesn't support all the formats that the film grabber does. It only supports .avi .ogg and .mpg. If the folder does not contain a file with one of those extensions it will not be processed.
I will add more formats for the next version.


> **meindian523 said:**
> You mean that I give the above(non-working) commands with 0.4.6?
Yes, the -g music option should work with the latest version.

> **meindian523 said:**
> 
Ok,then how do we make the avatars cd to the directory where the music is stored?Using CLI?
Actually there is a gui for the --type option but it doesn't show by default:
```
avatar-factory -g --gui --name --gui --type --gui --gui --gui --gui-progress
```

> **ayoli said:**
> 
But I still don't understatnd why double clic opens text editor instead of launching the album in audacious.
Could you post the content of a working avatar and the content of a non working avatar?

> **ayoli said:**
> 
edit 2 : ok edited music-widget and launchers/music, changed 'Desktop' for 'Bureau'  3 times, now the music-widget works. You got a localisation problem here :)
Strange...
It has never worked or does it stopped with the latest version?
I have my Ubuntu in Spanish and in Nautilus and Thunar the Desktop is called Escritorio but the real name for the folder is Desktop.
I don't know a variable for the desktop.
You could do:
```
ln -s ~/Bureau ~/Desktop
```

---

### Post by ayoli on 2007-11-05
Well the problem isn't really that I have some non working avatars and some working.
For ex, I've just try to launch this one from nautilus : gedit has opened ...
So I've tried to launch the _same_ avatar from AWN file-browser plugin (which doesn't show the covers) and it worked.
here's the entry:
```
[Desktop Entry]
Encoding=UTF-8
Name=(2001) eek a mouse - eekexperience
X-MultipleArgs=false
Type=Application
Exec=avatar-factory -al music --URL "/media/store/musique/reggae/_Eek-A-Mouse-15-Albums_/(2001) eek a mouse - eekexperience" --name "(2001) eek a mouse - eekexperience" --title "(2001) eek a mouse - eekexperience" --icon "/home/ayoli/.avatar-factory/icons/music/cd/_media_store_musique_reggae__Eek-A-Mouse-15-Albums__(2001) eek a mouse - eekexperience.png" --DND
Icon=/home/ayoli/.avatar-factory/icons/music/cd/_media_store_musique_reggae__Eek-A-Mouse-15-Albums__(2001) eek a mouse - eekexperience.png
URL=file:///media/store/musique/reggae/_Eek-A-Mouse-15-Albums_/(2001) eek a mouse - eekexperience

Title=(2001) eek a mouse - eekexperience
Index=39
```
Concerning the Desktop folder, It was called Desktop until I switched to gusty. Now my Desktop folder is called Bureau. And this is my first try of avatar-factory on gusty (so I jump from ver .30 on feisty to .46 on gusty)

---

### Post by meindian523 on 2007-11-05
Yuzem:

Both the commands work now in 0.4.6 ie the -g music and the -mg /path/to/music /path/to/avatars --type 0

Gratz....

suggestion:Instead of clearing the current playlist,can we get the script to append the album tracks double clicked to the playlist.....?

---

### Post by Yuzem on 2007-11-05
A similar problem was reported with a pre release version of gutsy.
If your avatar were created with a previous version of avatar-factory they will not work. This is because of the extension.
It seems that .avatar extension does not work correctly on gutsy. The latest version of avatar-factory uses the .desktop extension.

I will ask about the Desktop folder name in the "Programming Talk" subforums.

---

### Post by Yuzem on 2007-11-05
> **meindian523 said:**
> Yuzem:
suggestion:Instead of clearing the current playlist,can we get the script to append the album tracks double clicked to the playlist.....?

This is possible with some player for example for mpd, sonata or any other supported player "-add" must be added to the name of the player in the configuration file:
```
music=sonata-add
```

If you are using amarok I think that it doesn't allow to add files to the playlist from the command line. I don't have it installed but you could check it by running:
```
amarok --help
```
or:
```
man amarok
```

---

### Post by meindian523 on 2007-11-05
For amaroK:

-e enqueues but doesn't start it playing.

without -e ,amaroK starts playing but doesn't clear the playlist.

The command is

```
amarok -e /path/to/file/or/URL
```

Interestingly,it doesn't hang up the terminal and gives back control(ie the prompt) without using the & option,so you can close the terminal w/o risk of the track being stopped from playing.

I did the following:

Opened up the avatar-launcher file in ~/.avatar-factory and put music=amarok -e

made a new avatar(without the type 0 option) for one of my albums.....ie

```
avatar-factory -mg /home/easwarh/Music/Evanescence/Fallen /home/easwarh/Avatars/test
```
double clicked the avatar and to my surprise,it started playing in Totem!Meanwhile,the track playing in amaroK continued as if nothing had happened.:confused:

---

### Post by ayoli on 2007-11-05
> **Yuzem said:**
> A similar problem was reported with a pre release version of gutsy.
If your avatar were created with a previous version of avatar-factory they will not work. This is because of the extension.
It seems that .avatar extension does not work correctly on gutsy. The latest version of avatar-factory uses the .desktop extension.

I will ask about the Desktop folder name in the "Programming Talk" subforums.

These avatars have been created with the last version and have a .desktop ext

---

### Post by jayde6 on 2007-11-05
> Ah, the tv-show grabber doesn't support all the formats that the film grabber does. It only supports .avi .ogg and .mpg. If the folder does not contain a file with one of those extensions it will not be processed.
I will add more formats for the next version.
Ahh, since SQuark stated they tried it in both I just assumed that both were suppose to handle the mkv format. I appreciate you looking into it none the less. And look foward to the added formats in the next version. : )

---

### Post by Yuzem on 2007-11-05
> **meindian523 said:**
> For amaroK:

-e enqueues but doesn't start it playing.

without -e ,amaroK starts playing but doesn't clear the playlist.

The command is

```
amarok -e /path/to/file/or/URL
```

Ok, I will add amarok-add for the next version.

> **meindian523 said:**
> 
I did the following:
Opened up the avatar-launcher file in ~/.avatar-factory and put music=amarok -e
made a new avatar(without the type 0 option) for one of my albums.....ie
```
avatar-factory -mg /home/easwarh/Music/Evanescence/Fallen /home/easwarh/Avatars/test
```
double clicked the avatar and to my surprise,it started playing in Totem!Meanwhile,the track playing in amaroK continued as if nothing had happened.:confused:
mmm... I don't know about that, try:
```
/bin/bash -x avatar-factory -al music --URL "/home/easwarh/Music/Evanescence/Fallen"&
```
What is the output?

> **ayoli said:**
> These avatars have been created with the last version and have a .desktop ext
Strange... :confused:
Does it happens with any kind of avatar (--type 1 and --type 0)?
It sounds like a nautilus problem...

---

### Post by SQuark on 2007-11-05
> **Yuzem said:**
> 
mmm... another error that a can't reproduce.
I just create a blank file called "kill bill.mkv" and the grabber worked as expected.
Strange. I'll do some more testing when I get home.

> **Yuzem said:**
> 
I was thinking in detecting seasons by the name of the folder. If the name start with "season" then it will be skipped and taken as a season.
Make sure to filter out "Series" as well for British shows. :)
You might even want to add an option for custom filters so it can be made to work with other languages without too much hastle.

---

### Post by meindian523 on 2007-11-06
```
easwarh@l1nuxr0cks:~$ /bin/bash -x avatar-factory -al music --URL "/home/easwarh/Music/Evanescence/Fallen" &
[1] 6929
easwarh@l1nuxr0cks:~$ + grabbers_PATH=/usr/local/share/avatar-factory/grabbers
+ launchers_PATH=/usr/local/share/avatar-factory/launchers
+ themes_PATH=/usr/local/share/avatar-factory/themes
+ ratings_PATH=/usr/local/share/avatar-factory/themes
+ '[' 4 = 0 ']'
+ number=0
+ '[' -al '!=' '' ']'
+ case $1 in
+ shift
+ [[ music = desktop ]]
+ '[' -f /usr/local/share/avatar-factory/launchers/music ']'
+ launcher_name=music
+ shift
+ '[' --URL '!=' '' ']'
+ case $1 in
+ shift
+ URL=/home/easwarh/Music/Evanescence/Fallen
+ shift
+ '[' '' '!=' '' ']'
+ . /usr/local/share/avatar-factory/launchers/music
++ music=totem
++ music_widget=yes
++ mpd_music_directory=/var/lib/mpd/music
++ mpd_port=6600
++ mpd_host=127.0.0.1
++ '[' -f /home/easwarh/.avatar-factory/avatar-launcher ']'
++ . /home/easwarh/.avatar-factory/avatar-launcher
+++ music=amarok
+++ -e
/home/easwarh/.avatar-factory/avatar-launcher: line 1: -e: command not found
+++ music_widget=no
++ case $music in
++ music_launcher=totem
++ music_launcher_add='totem --enqueue'
+++ echo totem
+++ cut -d- -f2
++ [[ totem = add ]]
++ icon_PATH=/home/easwarh/.avatar-factory/icons/music_widget.png
++ '[' -n '' ']'
++ '[' no = yes ']'
++ totem /home/easwarh/Music/Evanescence/Fallen
+ exit

```

I had to press Ctrl+C to regain control of the Terminal,and when I did that it gave the following lines
```


[1]+  Done                    /bin/bash -x avatar-factory -al music --URL "/home/easwarh/Music/Evanescence/Fallen"
easwarh@l1nuxr0cks:~$ 
```

Hope you get something out of that......

---

### Post by Yuzem on 2007-11-06
> **SQuark said:**
> Strange. I'll do some more testing when I get home.

Make sure to filter out "Series" as well for British shows. :)
You might even want to add an option for custom filters so it can be made to work with other languages without too much hastle.
Ok, I will add "Series" but I prefer to add other languages as they get requested to keep it simple. No need of unnecessary options to be set.

> **meindian523 said:**
> 
Hope you get something out of that......
Try this:
```
music="amarok -e"
```
With the quotes.

---

### Post by SQuark on 2007-11-06
> **Yuzem said:**
> Ok, I will add "Series" but I prefer to add other languages as they get requested to keep it simple. No need of unnecessary options to be set.

Ok, I understand. In that case, add "Seizoen" and "Reeks" (Dutch) as well. :)

---

### Post by ayoli on 2007-11-06
@Yuzem:
my avatars work now, without changing anything. I've just shut down to take my laptop at work today and tried after reboot and oooh :)
maybe I should have restart just nautilus ? A lil weird but it works now so I m happy.
thanks for your work and help :)

---

### Post by meindian523 on 2007-11-06
> **Yuzem said:**
> 
Try this:
```
music="amarok -e"
```
With the quotes.

That worked.Going Under was added to the end of the current playlist.

---

### Post by mukiex on 2007-11-07
This is a pretty neat tool. A few things, if I may :

First of all, IANAP, so I have no idea what proper patch structure is. Please forgive me if this looks messy.

1. In grabbers/film , the 7th line looks like this :

```
SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue
```

In the interest of helping people who're backing up their personal DVD collections directly :

```
SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue,iso
```

Might work better. Not sure if that's ommited on purpose, setting the media player to vlc works perfectly fine with an ISO file. It's pretty neat to see a cover, double-click it, and get the movie menu =3

2. In grabbers/tv-show, picture flexibility would get a small boost by changing line 19 to :

```
grabber_picture="$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' \) -print -quit)"
```

and line 23 to :

```
grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2 | egrep -i "jpg$|jpeg$|png$")
```

To allow for .jpeg extention files. (AniDB uses this)

I'd like to eventually code (or at least, mod grabbers/tv-show) a small adendum called "anime" that looks up AniDB instead of IMDB for that particular genre. =3

Thanks for the app!

Edit note : eww, Ubuntu's form system doesn't notice whitespace info for tabs.

---

### Post by nikoPSK on 2007-11-07
Thanks alot, great! Question: what guide did you use to make your .deb? Or did someone make it for you?

---

### Post by Yuzem on 2007-11-08
> **SQuark said:**
> Ok, I understand. In that case, add "Seizoen" and "Reeks" (Dutch) as well. :)
Ok, but seizoen is singular or plural? I guess that Reeks is plural and I should use Reek instead.

> **ayoli said:**
> @Yuzem:
my avatars work now, without changing anything. I've just shut down to take my laptop at work today and tried after reboot and oooh :)
maybe I should have restart just nautilus ? A lil weird but it works now so I m happy.
thanks for your work and help :)
You are welcome :)

> **mukiex said:**
> This is a pretty neat tool. A few things, if I may :

First of all, IANAP,
Me neither. :(

> **mukiex said:**
> 
1. In grabbers/film , the 7th line looks like this :

```
SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue
```

In the interest of helping people who're backing up their personal DVD collections directly :

```
SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue,iso
```

Ok, I will add iso in the next version.

> **mukiex said:**
> 
2. In grabbers/tv-show, picture flexibility would get a small boost by changing line 19 to :

```
grabber_picture="$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' \) -print -quit)"
```

and line 23 to :

```
grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2 | egrep -i "jpg$|jpeg$|png$")
```

To allow for .jpeg extention files. (AniDB uses this)

Ok, I will add jpeg extension.

> **mukiex said:**
> 
I'd like to eventually code (or at least, mod grabbers/tv-show) a small adendum called "anime" that looks up AniDB instead of IMDB for that particular genre. =3
Thanks for the app!
Edit note : eww, Ubuntu's form system doesn't notice whitespace info for tabs.
If the problem is that for some anime it does not find the cover I could make it search AniDB if it doesn't find anything on imdb to keep it simple instead of implementing an option tu use AniDB.

> **nikoPSK said:**
> Thanks alot, great! Question: what guide did you use to make your .deb? Or did someone make it for you?
Here it is:
[http://ubuntuforums.org/showthread.php?t=406069](http://ubuntuforums.org/showthread.php?t=406069)

---

### Post by nikoPSK on 2007-11-08
thanks! Because I've already made a .deb but it's awn+curves and it's not going so hot...:(

---

### Post by nikoPSK on 2007-11-08
thanks! Because I've already made a .deb but it's awn+curves and it's not going so hot...:(

[heres what I used.]("http://ubuntuforums.org/showthread.php?t=51003")

---

### Post by SQuark on 2007-11-08
> **Yuzem said:**
> Ok, but seizoen is singular or plural? I guess that Reeks is plural and I should use Reek instead.

They're both singular (the plurals would be seizoenen and reeksen).

> **mukiex said:**
> In the interest of helping people who're backing up their personal DVD collections directly :

That reminds me; since you're adding special support for folders called Season* anyway, could you also add support for VIDEO_TS folders? You should get the name of the movie/tv-show from the name of its parent directory.

---

### Post by Nonno Bassotto on 2007-11-08
Well, season in italian is translated to "serie" or "stagione" if you want to add it.

---

### Post by flightless bird on 2007-11-09
I have experienced an odd situation where avatar factory is consistently picking the wrong jpg for a folder, even though I have gone through and made sure there is only one picture on that path. No matter how many times I delete it and try again, it insists on the previous wrong cover. What is going on here? Is a previous version stored elsewhere? Can I define a custom image?

---

### Post by Nonno Bassotto on 2007-11-09
Yes, the created image is stored in ~/.avatar-factory/icons in order to be reused next times (so you have to wait less for the avatar creation). You can find it and manually delete it.

---

### Post by Yuzem on 2007-11-09
> **SQuark said:**
> 
That reminds me; since you're adding special support for folders called Season* anyway, could you also add support for VIDEO_TS folders? You should get the name of the movie/tv-show from the name of its parent directory.
I have thought about it but the tv-show grabber list files inside a folder and the film grabber uses the name of the file not the folder.
Is VIDEO_TS a dvd video?
Maybe a different grabber could be a better solution. What do you think?
dvd-video grabber...
The name comes from the folder name but what is the file that must be launched?

> **Nonno Bassotto said:**
> Well, season in italian is translated to "serie" or "stagione" if you want to add it.
Ok, right now:
Season
Serie
Stagione
Seizoen
Reeks
Temporada

---

### Post by flightless bird on 2007-11-09
Thank you for your helpful reply - since you asked for your English to be corrected:instead of "next times" you should use "next time" (this is always singular, and may either be expressed with or without the definite article, but never with the indefinite one, ie. the next time). This is the opposite of "sometimes", and not parallel to "some time", which is an indefinite measure of duration.

---

### Post by Nonno Bassotto on 2007-11-09
Thank you for your correction. :)

---

### Post by SQuark on 2007-11-09
> **Yuzem said:**
> I have thought about it but the tv-show grabber list files inside a folder and the film grabber uses the name of the file not the folder.
Is VIDEO_TS a dvd video?
Yes, it is. It results from a straightforward copy (instead of creating an image file) of a DVD.

> **Yuzem said:**
> Maybe a different grabber could be a better solution. What do you think?
dvd-video grabber...
I'd prefer if the existing grabbers could handle this. But if you decide against it, I'm sure it won't be too hard to adjust my Thunar custom actions to also inculde the DVDs.

> **Yuzem said:**
> The name comes from the folder name but what is the file that must be launched?
Both in VLC and Totem-xine, launching the VIDEO_TS folder, as well as launching its parent dir work. I assume launching the parent dir is the better choice, as there may be an AUDIO_TS folder as well (though this is rarely used).
So the usual structure is: a parent dir which is named after the movie/tv-show, and within that dir a VIDEO_TS folder and optionally an AUDO_TS folder. So check for folders that are called VIDEO_TS and work from there.

> **Yuzem said:**
> Ok, right now:
Season
Serie
Stagione
Seizoen
Reeks
Temporada

And "Series" for British/Irish shows.

---

### Post by xpronic on 2007-11-11
I might be missing the obvious, but how do I get the Films & TV Shows browser like in the screenshots on the first page of this thread?

I currently have the avatars saved in the Videos folder:
[INDENT][IMG]http://img256.imageshack.us/img256/5563/screenshotvideosfilebroga9.png[/IMG][/INDENT]

---

### Post by Forlong on 2007-11-11
It's "Nautilus with a custom background"

---

### Post by nikoPSK on 2007-11-11
> **Forlong said:**
> It's "Nautilus with a custom background"

which is possible how? Also out of the subject how do I get a nautilus icon on my awn dock?:)

---

### Post by Forlong on 2007-11-11
> **nikoPSK said:**
> which is possible how?
Edit &#8594; Background and Emblems

You'll need the OP's background image to add it there, of course.

---

### Post by nikoPSK on 2007-11-11
> **Forlong said:**
> Edit &#8594; Background and Emblems

You'll need the OP's background image to add it there, of course.

Op's background image = what?

:popcorn:

---

### Post by Yuzem on 2007-11-11
> **SQuark said:**
> 
I'd prefer if the existing grabbers could handle this. But if you decide against it, I'm sure it won't be too hard to adjust my Thunar custom actions to also inculde the DVDs.
Ok, I will maybe include it in the tv-show grabber.

> **SQuark said:**
> 
And "Series" for British/Irish shows.
Series should work with Serie

> **nikoPSK said:**
> Also out of the subject how do I get a nautilus icon on my awn dock?:)
Make a text file with the extension: ".desktop"
Open it with gedit and copy the following text:
```
[Desktop Entry]
Encoding=UTF-8
Name=Music Albums
X-MultipleArgs=false
Type=Application
Exec=nautilus "/your/music/folder"
Icon=rhythmbox
```

Change "/your/music/folder" to the path that you want.
You can also change the icon:
For movies try:
Icon=emblem-multimedia
For pictures:
Icon=emblem-pictures

Then drag it to AWN.

> **Forlong said:**
> Edit &#8594; Background and Emblems
You'll need the OP's background image to add it there, of course.
The backgrounds in the screenshots are included in the zipped package and if you want to apply the background to only one folder just drag it with the middle mouse button.

---

### Post by Forlong on 2007-11-11
> **nikoPSK said:**
> Op's background image = what?
OP = original poster = Yuzem (sorry, was too lazy to look it up)

I uploaded the images, so you can just download them and do as Yuzem said:
Grab the image (the file itself) - after you downloaded it into a folder - with the MIDDLE mouse button, drag it to an empty space in Nautilus, release and choose "Set as Background" (or add it to "Background and Emblems" and do it from there).


@Yuzem: thanks, being the lazy bum I am, I just downloaded the deb.

---

### Post by nikoPSK on 2007-11-11
> **Forlong said:**
> OP = original poster = Yuzem (sorry, was too lazy to look it up)

I uploaded the images, so you can just download them and do as Yuzem said:
Grab the image (the file itself) - after you downloaded it into a folder - with the MIDDLE mouse button, drag it to an empty space in Nautilus, release and choose "Set as Background" (or add it to "Background and Emblems" and do it from there).


@Yuzem: thanks, being the lazy bum I am, I just downloaded the deb.

thanks alot!:)

---

### Post by nikoPSK on 2007-11-11
how do I get it to find tv shows? I have tvtime installed and working...

---

### Post by nikoPSK on 2007-11-11
also what program did you use to rip music cds?

EDIT: nvm. But I still want to know why it isn't working with my TV shows. What folder do I make it look in?
EDIT EDIT: soundjuicer doesn't get album artwork. suggest some site or something
EDIT EDIT EDIT: nvm just need to know about the tv now...

---

### Post by nikoPSK on 2007-11-11
also what background for the photos did you use?:popcorn:

---

### Post by xpronic on 2007-11-11
> **Forlong said:**
> OP = original poster = Yuzem (sorry, was too lazy to look it up)

I uploaded the images, so you can just download them and do as Yuzem said:
Grab the image (the file itself) - after you downloaded it into a folder - with the MIDDLE mouse button, drag it to an empty space in Nautilus, release and choose "Set as Background" (or add it to "Background and Emblems" and do it from there).


@Yuzem: thanks, being the lazy bum I am, I just downloaded the deb.
Thanks. :)

Quick question, can you set the theme to just ONE folder?

---

### Post by Nonno Bassotto on 2007-11-11
There is a reason why Forlong told to use the MIDDLE mouse button. :)

---

### Post by nikoPSK on 2007-11-11
okay but where do I tell it to look for tv?

---

### Post by Yuzem on 2007-11-11
> **nikoPSK said:**
> also what program did you use to rip music cds?
EDIT: nvm. But I still want to know why it isn't working with my TV shows. What folder do I make it look in?
You need the video files for that, it doesn't work with tvtime.

> **nikoPSK said:**
> 
soundjuicer doesn't get album artwork. suggest some site or something
Web:
allmusic.com
amazon.com

Software:
[http://ubuntuforums.org/showthread.php?p=3266072#post3266072](http://ubuntuforums.org/showthread.php?p=3266072#post3266072)
[http://mookooh.org/coverfinder/](http://mookooh.org/coverfinder/)

> **nikoPSK said:**
> also what background for the photos did you use?:popcorn:
Here it is:
[http://manicho.deviantart.com/art/Plastic-Stripes-41981461](http://manicho.deviantart.com/art/Plastic-Stripes-41981461)

> **xpronic said:**
> Thanks. :)
Quick question, can you set the theme to just ONE folder?
You must drag it with the middle mouse button but from the "emblems and backgrounds" dialog (Nautilus > edit > emblem and background)

---

### Post by nikoPSK on 2007-11-11
it say epiphany is a game.... also how do I get vinyls? I have a bunch of beatles cd's ripped and they would look great. I used [www.coverhunt.com](www.coverhunt.com) Also I have no clue what imdb is.... also what does the music widgit do?

---

### Post by nikoPSK on 2007-11-11
Ok nautilus just got screwed... No icons and i can't browse anywhere...:(

---

### Post by -grubby on 2007-11-12
> **nikoPSK said:**
> Ok nautilus just got screwed... No icons and i can't browse anywhere...:(

to start over with nautilus I'm thinking you delete ./nautilus in your profile. 
sudo apt-get remove nautilus and 
sudo apt-get install nautilus

---

### Post by vishzilla on 2007-11-12
nice work....keep it up!!!

---

### Post by Yuzem on 2007-11-12
> **nikoPSK said:**
> how do I get vinyls? I have a bunch of beatles cd's ripped and they would look great. I used [www.coverhunt.com](www.coverhunt.com)
Try this:
```
avatar-factory -ag -t --gui --gui-progress /path/2/avatar.desktop
```
You can use that command to make a nautilus action. Then you will be able to right clic an avatar an chose a different theme.

> **nikoPSK said:**
> 
Also I have no clue what imdb is....
imdb grabber creates visual representation of imdb firefox bookmarks.
I have a list of a lot of movies in my firefox bookmarks but I use another script for it that allow me to have categories:
[http://ubuntuforums.org/showthread.php?p=3154074#post3154074](http://ubuntuforums.org/showthread.php?p=3154074#post3154074)

> **nikoPSK said:**
> 
also what does the music widgit do?
Apart from the obvious, it allows to add albums to the playlist. Just drag and drop the album to the music widget, but first, scale the music widget to the maximum size. (right click > resize icon)

> **nikoPSK said:**
> Ok nautilus just got screwed... No icons and i can't browse anywhere...:(
You can restart nautilus with:
```
nautilus -q
```

> **vishzilla said:**
> nice work....keep it up!!!
Thanks, I will. :)

---

### Post by nikoPSK on 2007-11-12
> **Yuzem said:**
> Try this:
```
avatar-factory -ag -t --gui --gui-progress /path/2/avatar.desktop
```
You can use that command to make a nautilus action. Then you will be able to right clic an avatar an chose a different theme.


imdb grabber creates visual representation of imdb firefox bookmarks.
I have a list of a lot of movies in my firefox bookmarks but I use another script for it that allow me to have categories:
[http://ubuntuforums.org/showthread.php?p=3154074#post3154074](http://ubuntuforums.org/showthread.php?p=3154074#post3154074)


Apart from the obvious, it allows to add albums to the playlist. Just drag and drop the album to the music widget, but first, scale the music widget to the maximum size. (right click > resize icon)


You can restart nautilus with:
```
nautilus -q
```


Thanks, I will. :)

I fixed nautilus by restarting. When i drag a music avatar down to the bottom left hand corner it just moves it.... Thatks for the notice about the script:D

---

### Post by Yuzem on 2007-11-12
> **nikoPSK said:**
> When i drag a music avatar down to the bottom left hand corner it just moves it.... 
Maybe AWN is blocking it. Move the widget a little to the top of the screen and try again to drag and drop an album over the widget.

---

### Post by xpronic on 2007-11-12
> **Yuzem said:**
> You must drag it with the middle mouse button but from the "emblems and backgrounds" dialog (Nautilus > edit > emblem and background)
Thanks. :)

What file type must the image be to replace the dvd covers? I've tried dragging and dropping a jpg file, but it doesn't work. :/

---

### Post by Yuzem on 2007-11-12
I think that there is a bug... It will be fixed for the next version.

---

### Post by xpronic on 2007-11-12
Alright thanks. Keep up the good work. It's a fantastic app! :)

---

### Post by BoardDWorld on 2007-11-14
This is quite impressive thank you! Is there anyway to get exaile to work with this?

I've always used Amarok but wanted a Gnome alternative. I spent a good few hours yesterday trialling literally "all" players available and exaile is by far, without question, the best! It's a shame not to have the 2 running together!

Any help would be greatly appreciated!

---

### Post by Yuzem on 2007-11-14
It should work with exaile.
I didn't found a way to launch a file or directory with exaile.
"man exaile" or "exaile --help" doesn't provide any help with that.
That is why it works with playlists and it doesn't start playing automatically.
If someone knows a way to launch a file with exaile, just tell me and I will improve the exaile support.

---

### Post by BoardDWorld on 2007-11-14
Yeah, it's odd. It will open of course but that's about it. Exaile may require a plug-in.

Another thing, does Avatar Factory not support mp4/acc at the moment? It's skipped all of my mp4 music files? If there's an answer to this already I'll track it down tomorrow. I just spent quite some time getting my Places menu to display custom icons (attached).

Again this is very cool, it's allowed me to shift all of my personal media to my storage drive giving me plenty of room on my main drive again.

---

### Post by nikoPSK on 2007-11-14
heres a screen of mine:

Also why when i make a movie it adds a random screen shot mainly the Simpsons....

---

### Post by BoardDWorld on 2007-11-15
Ok, I didn't find anything on the forum but it works perfect by completing the following:

```
cd /usr/local/share/avatar-factory/grabbers/
```
```
sudo gedit music
```
After *.flac' paste in the following:
```
 -or -iname '*.mp4'
```

Funny that it doesn't have this extension already???

---

### Post by BoardDWorld on 2007-11-15
> **nikoPSK said:**
> heres a screen of mine:

Also why when i make a movie it adds a random screen shot mainly the Simpsons....

I have just tried the film grabber myself. It's actually looking for the image on the internet! This idea should be flagged as the chances of getting the correct image are very slim. The big disadvantage with the film grabber is you can't do all your movies in batches. This makes it a big job for those who already have large libraries.

For those who want the film grabber to act like the music grabber you can do the following from terminal:

```
cd /usr/local/share/avatar-factory/grabbers/
```
```
sudo gedit film
```

Replace the entire contents with the following:
```
#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Application
	SOURCE_type=folders
}

grabber_secondary_options () {
	avatar_title="$(echo ${SOURCE_item##*/} | sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/_/ /' -e 's/\./ /' -e 's\....$\\')"
	avatar_filename="$(echo ${SOURCE_item%/*} | sed -e 's/\//\_/g')_$avatar_title"
	avatar_name="$avatar_title"
	URL="file://$SOURCE_item"
	Launcher="avatar-factory -al $grabber_name --URL \"$SOURCE_item\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$avatar_filename.png\" --DND"
}

get_grabber_picture () {
	if [[ "" != "$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname '*.avi' -or -iname '*.ogm' -or -iname '*.mpg' -or -iname '*.divx' -or -iname '*.mpeg' -or -iname '*.mov' -or -iname '*.mp4' -or -iname '*.mkv' -or -iname '*.wmv' -or -iname '*asf' -or -iname '*.flv' -or -iname '*.cue' \) -print -quit)" ]]; then
		grabber_picture="$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname 'cover.jpg' -or -iname 'cover.png' -or -iname 'folder.jpg' -or -iname 'folder.png' -or  -iname '*front*.jpg' -or -iname '*front*.png' \) -print -quit)"
		if [[ -n "$grabber_picture" ]]; then
			grabber_picture="$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname '*.jpg' -or -iname '*.png' \) -print -quit)"
		fi
	else
		grabber_picture=
	fi
}
```

---

### Post by ayoli on 2007-11-15
That's interesting. What about a choice like : "do you want to grab film covers from Internet or from local source ?"

---

### Post by Nonno Bassotto on 2007-11-15
> **BoardDWorld said:**
> It's actually looking for the image on the internet! This idea should be flagged as the chances of getting the correct image are very slim.

Actually the chances of getting the correct image are quite high if you put the exact title for your file. If the image is wrong you just need to drag the correct one onto the avatar.

---

### Post by BoardDWorld on 2007-11-15
> **Nonno Bassotto said:**
> Actually the chances of getting the correct image are quite high if you put the exact title for your file. If the image is wrong you just need to drag the correct one onto the avatar.

File titled "The Simpsons Movie 2007" and I received the cover for "The Host". Also I had the cover with the movie already, it should at least first check this. Again I love this app just some logical suggestions...

---

### Post by Nonno Bassotto on 2007-11-16
Searching on Google
```
the simpsons movie 2007 site:imdb.com
```
(which is what the program does, as far as I know) I get the correct page, so I guess it's a bug (maybe related to already downloaded covers?).

By the way, the title is "The Simpsons Movie", without the year.

The problem with a local image is: where do you think it should be searched? There is no logical place to put it. This is different with the album case, where the album consists of a folder which can also contain its cover art. Anyway, it's up to Yuzem to decide. :)

---

### Post by Yuzem on 2007-11-16
Just add -f to the command and the existing icon will be replaced.
Something like:
```
avatar-factory -fg -f "The Simpsons Movie 2007.avi" folder/2/save
```

---

### Post by BoardDWorld on 2007-11-16
As an X windows user I keep my movies in folders with the cover. That way if there's multiple parts it's tidy and the cover showed on the folder.

Most importantly I wasn't saying this should replace the original method, it should just be optional along with the ability to do it in batches.

---

### Post by Yuzem on 2007-11-16
You can use the tv-show grabber for that. Use the option "--type 0" to directly launch the movie. It should work with totem.

---

### Post by Ub1476 on 2007-11-19
Just heard about this, and it's super! However, I have a few questions:

How can you rotate the images (seen this on your screenshots)?

Where do you find those nautilus backgrounds, and is there anyway to specific one background to one special directory?

Is it possible to add a default folder where to save the avatars in the future (currently I have to choose location all the time)?

In the future, is it possible that it can search in subdirectories (I know this is possible for pictures already). 

Ok, that's all I got for the moment. Thanks:)

---

### Post by nikoPSK on 2007-11-19
> **Ub1476 said:**
> Just heard about this, and it's super! However, I have a few questions:
 
How can you rotate the images (seen this on your screenshots)?
 
Where do you find those nautilus backgrounds, and is there anyway to specific one background to one special directory?
 
Is it possible to add a default folder where to save the avatars in the future (currently I have to choose location all the time)?
 
In the future, is it possible that it can search in subdirectories (I know this is possible for pictures already). 
 
Ok, that's all I got for the moment. Thanks:)
 
use what forlong helped me.:)
 
> **Forlong said:**
> OP = original poster = Yuzem (sorry, was too lazy to look it up)
 
I uploaded the images, so you can just download them and do as Yuzem said:
Grab the image (the file itself) - after you downloaded it into a folder - with the MIDDLE mouse button, drag it to an empty space in Nautilus, release and choose "Set as Background" (or add it to "Background and Emblems" and do it from there).
 
 
@Yuzem: thanks, being the lazy bum I am, I just downloaded the deb.

---

### Post by Yuzem on 2007-11-19
> **Ub1476 said:**
> 
How can you rotate the images (seen this on your screenshots)?

If you are talking about the music widget:
[[IMG]http://img374.imageshack.us/img374/8009/musicwidgetkr4.th.jpg[/IMG]](http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg)

Drag a music avatar to the widget. Thats all, the album will be added to the playlist.

> **Ub1476 said:**
> 
Where do you find those nautilus backgrounds, and is there anyway to specific one background to one special directory?

They are in the zipped package.
To apply the background to only one folder drag it with the middle mouse button from the backgrounds and emblems dialog.

> **Ub1476 said:**
> 
Is it possible to add a default folder where to save the avatars in the future (currently I have to choose location all the time)?

You can make an alias for that:
```
gedit ~/.bashrc
```
and add:
```
alias music_avatars="avatar-factory -mg source/folder folder/2/save"
```

> **Ub1476 said:**
> 
In the future, is it possible that it can search in subdirectories (I know this is possible for pictures already). 

Practically all grabbers work recursively.
For example, if you want the film grabber to search subdirectories you must set a folder as the source instead of a file/s

---

### Post by Ub1476 on 2007-11-19
Thanks for the help, but it was [this]("http://img178.imageshack.us/my.php?image=pictureavatarssd8.png") picture I referred to.

---

### Post by Nonno Bassotto on 2007-11-19
They're automatically created by the picture avatar.

---

### Post by Ub1476 on 2007-11-19
Yes, I thought so too, but I got the "90*" version on 8/8 of the picture grabber.:-k

---

### Post by Ryan H on 2007-12-08
Actually, in your picture you show the TV shows names in bold, and their number beside them?  What format should each episode name be in so I can achieve this?
Currently they are titled "01 Title here.avi", "02 Other Title.avi", etc.

Thanks!

-Ryan H

---

### Post by adrianmak on 2007-12-08
I generated avatar from my music album, but what do next ??

Browsing music folder from nautilus, album folders still showing normal folder icon

---

### Post by Yuzem on 2007-12-09
> **Ryan H said:**
> Actually, in your picture you show the TV shows names in bold, and their number beside them?  What format should each episode name be in so I can achieve this?
Currently they are titled "01 Title here.avi", "02 Other Title.avi", etc.

Thanks!

-Ryan H

The episode names are based on the file names. It should not display the extension.
If your files are named "01 title.avi" you should see "01 title"
The names aren't in bold. It is the font I use "Lucida Mac" the size is 9.

> **adrianmak said:**
> I generated avatar from my music album, but what do next ??

Browsing music folder from nautilus, album folders still showing normal folder icon
It doesn't change folder icons (not yet) but you can use the avatar to access your folders with "--type 0" option:

```
avatar-factory -mg --type 0 source/folder  folder/2/save
```

---

### Post by Nonno Bassotto on 2007-12-16
Will you make grabbers and themes for books or for comics? If you don't have enough time, can we help in any way?

---

### Post by Yuzem on 2007-12-16
Yes I will make a comic grabber and it should be very easy to make.

The problem is that I want to implement a special feature for the comic grabber.
The ability to right clic a comic avatar and select bookmark from thunar or nautilus.
Then a dialog will pop up to select the page and the closed comic avatar will became an open comic at the specified page... when clicked it will open the bookmarked page.

It won't be ready for the next release... 

If someone wants to help, the book theme needs to be done, but it may be a little complicated. :(
Thanks anyways.
Now that I know that someone is interested in the comic grabber I will be more motivated to make it. :)

---

### Post by Yuzem on 2007-12-23
New version:

**mame grabber:**
[INDENT]The mame grabber creates avatars for your mame games collection. If there is no snapshots path specified it will search for the snaps on the internet.[/INDENT]

Screenshot in nautilus:
[[IMG]http://img165.imageshack.us/img165/5421/mameavatarsop9.th.jpg[/IMG]](http://img165.imageshack.us/my.php?image=mameavatarsop9.jpg)

Changelog:
```
23.12.07------0.5.0
	+added mame grabber
	+added shadow theme
	+music launcher: amarok-add support
	+film grabber: added iso filetype
	+fixed picture drag and drop problem and global icon problems
	+added a man page
	+youtube grabber: changed the default behavior
	+tv-show grabber: added season detection
	+tv-show grabber: added support for VIDEO_TS folders (dvd video)
	+tv-show grebber: added more video formats
	+grabber help implementation
	+added StartupNotify support
```

[[COLOR="Red"]**Download**[/COLOR]]("http://www.gnomefiles.org/app.php/Avatar_Factory")

---

### Post by ayoli on 2007-12-24
> **Yuzem said:**
> New version:

**mame grabber:**
[INDENT]The mame grabber creates avatars for your mame games collection. If there is no snapshots path specified it will search for the snaps on the internet.[/INDENT]

Screenshot in nautilus:
[[IMG]http://img165.imageshack.us/img165/5421/mameavatarsop9.th.jpg[/IMG]](http://img165.imageshack.us/my.php?image=mameavatarsop9.jpg)

Changelog:
```
23.12.07------0.5.0
	+added mame grabber
	+added shadow theme
	+music launcher: amarok-add support
	+film grabber: added iso filetype
	+fixed picture drag and drop problem and global icon problems
	+added a man page
	+youtube grabber: changed the default behavior
	+tv-show grabber: added season detection
	+tv-show grabber: added support for VIDEO_TS folders (dvd video)
	+tv-show grebber: added more video formats
	+grabber help implementation
	+added StartupNotify support
```

[[COLOR="Red"]**Download**[/COLOR]]("http://www.gnomefiles.org/app.php/Avatar_Factory")
Wow, a xmas version :) happy holidays here !

---

### Post by nikoPSK on 2007-12-24
> **Yuzem said:**
> New version:

**mame grabber:**[INDENT]The mame grabber creates avatars for your mame games collection. If there is no snapshots path specified it will search for the snaps on the internet.[/INDENT]Screenshot in nautilus:
[[IMG]http://img165.imageshack.us/img165/5421/mameavatarsop9.th.jpg[/IMG]]("http://img165.imageshack.us/my.php?image=mameavatarsop9.jpg")

Changelog:
```
23.12.07------0.5.0
    +added mame grabber
    +added shadow theme
    +music launcher: amarok-add support
    +film grabber: added iso filetype
    +fixed picture drag and drop problem and global icon problems
    +added a man page
    +youtube grabber: changed the default behavior
    +tv-show grabber: added season detection
    +tv-show grabber: added support for VIDEO_TS folders (dvd video)
    +tv-show grebber: added more video formats
    +grabber help implementation
    +added StartupNotify support
```[[COLOR=Red]**Download**[/COLOR]]("http://www.gnomefiles.org/app.php/Avatar_Factory")

bwahaha, sweet man. :)

---

### Post by v1ncent on 2007-12-29
Ohhh, it's not like i though, avatar factory only creates links to the real folders, it doesn't replace the folder icons... or maybe i'm doing something wrong?

---

### Post by Yuzem on 2008-01-01
Sorry for the delay...
You are right, it doesn't change folders/files icons but it is a planned feature.
Too bad thunar doesn't support this... :(

---

### Post by jayde6 on 2008-01-05
I had a couple of questions, if I understand correctly, both film and tv-show use the "film=" setting in the avatar-launcher config. Would it be possible to have a seperate entry for tv-show? I use additional filters and scaling for tv-shows (as many are not quite the same condition as my other media files) and those same filters applied to what I run under the film grabber actually detract from the quality. 

Also I use an opposite setup as recommended for the youtube grabber. I use epiphany as my browser and firefox for the grabber. I recently switched so the youtube avatars I made before work fine however new ones I  have bookmarked in epiphany are not detected. Is there a simple fix to this?

Thanks for any and all help and keep up the great work : ),
~Jennifer

---

### Post by Yuzem on 2008-01-05
> **jayde6 said:**
> Would it be possible to have a seperate entry for tv-show?

Yes, try this:
```
sudo gedit /usr/local/share/avatar-factory/launchers/tv-show
```

On line 10 insert:
```
film="$tv_show"
```

Add to the configuration file:
tv_show="your-video-player"

> **jayde6 said:**
> 
Also I use an opposite setup as recommended for the youtube grabber. I use epiphany as my browser and firefox for the grabber. I recently switched so the youtube avatars I made before work fine however new ones I  have bookmarked in epiphany are not detected. Is there a simple fix to this?

Sadly no, epiphany uses a different format to store the bookmarks. I will tray to add epiphany compatibility for the next version.

---

### Post by jayde6 on 2008-01-05
That worked beautifully, thanks, and thank you for looking into adding epiphany support.

---

### Post by Yuzem on 2008-01-31
New version:

New comic grabber:
The comic grabber creates comic avatars from folders with pictures.
The avatars created can be bookmarked and the icon will change to reflect the page you are reading. When launched, the bookmarked page will be opened.

Having the comics in folders instead of archives (cbz, cbr, etc) has some advantages:
-It is faster (larger comics are very slow to open in archived formats)
-Does't make unnecessary disk usage because there is no need to unpack anything.
-They can be viewed with any picture viewer.
-Thumbnails are remembered.

[[IMG]http://img163.imageshack.us/img163/8576/comicavatarsbk3.th.jpg[/IMG]](http://img163.imageshack.us/my.php?image=comicavatarsbk3.jpg)

Now the film grabber can change the video thumbnail to make it look like a DVD.
The sad part is that for some reason it doesn't work with thunar. (It is in beta state)

Full list of changes:
```
31.01.08------0.5.5
+added comic grabber
+added book theme
+avatar grabber: added --comic-bookmarks option
+added anobii grabber
+added epiphany bookmarks support
+added opera bookmarks support
+internal changes
+added --save-as icon option
+film grabber: --save-as thumbnail option
+added --picture-gui option
+mame grabber: basic prototype detection
+tv-show launcher: own player config option
```

---

### Post by fly3rman on 2008-01-31
Would you post an x64 version of the .deb file?

---

### Post by Yuzem on 2008-01-31
That deb should work just fine for x64 computers.
Avatar Factory doesn't need to be compiled.
I guess that because of that it is indifferent about the processor architecture but I am not sure.

---

### Post by nikoPSK on 2008-01-31
you got your deserved thanks. :)

---

### Post by jayde6 on 2008-01-31
Thanks for keeping this wonderful program alive and ever evolving : ).

To fly3rman; I also am running 64 bit, the way I always get 32 bit debs to work is by installing alien 
```
 sudo apt-get install alien
``` 
and then going to the directory where the deb is and type 
```
sudo alien -t nameof.deb
``` 
and then type
```
sudo alien nameof.tgz
```
there is probably a much easier way but this works for me.

---

### Post by Yuzem on 2008-01-31
> **nikoPSK said:**
> you got your deserved thanks. :)
Nice... :)
> **jayde6 said:**
> Thanks for keeping this wonderful program alive and ever evolving : ).

To fly3rman; I also am running 64 bit, the way I always get 32 bit debs to work is by installing alien 
```
 sudo apt-get install alien
``` 
and then going to the directory where the deb is and type 
```
sudo alien -t nameof.deb
``` 
and then type
```
sudo alien nameof.tgz
```
there is probably a much easier way but this works for me.

Oh... I didn't know that it wasn't working. I wonder why.
If anyone have any tips on how to make 64 bits compatible packages I would like to know.

---

### Post by aidanr on 2008-01-31
> **Yuzem said:**
> If anyone have any tips on how to make 64 bits compatible packages I would like to know.

In the control file change the architecture to "all" and then the one deb will work for both 32bit and 64bit (afaik).

---

### Post by ashmew2 on 2008-02-01
Thanks a HELL LOT for the awesome script. :D
I was just tired of changing the icons of the folders with my music to one of the album covers (LOL).

But I wanted to know if there's any way to hide all the folders for which a nice cover has been made ? (I m referring to the Music Grabber). Basically , I want the folders to be "invisible" and only the avatars created to be "visible" 
Any pointers ? 
Thanks ! :D

---

### Post by jayde6 on 2008-02-01
While not the quickest of solutions depending on your directory structure, you can always put a . in front of the source folder name. I have noticed (at least with the older versions of the script, I do not know if it is still like this) the folder that has the files in it can't have a . in front of it or the grabber wont work, however you can have say an .audio folder with regular folders inside and it will work from those regular folders, and then keep the avatars outside of the .audio folder. If there is an easier way I would be interested as well.

---

### Post by andrek on 2008-02-01
Hey, what do I have to do if I want an exactly result as showed on this pic [http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg](http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg) ?

---

### Post by Yuzem on 2008-02-01
> **aidanr said:**
> In the control file change the architecture to "all" and then the one deb will work for both 32bit and 64bit (afaik).
Thanks.
I am using epm package manager. I added "-a all" to the command parameters.
Could someone with a 64bit processor test the attached deb?
If it works I will upload it as the default deb.

> **jayde6 said:**
> While not the quickest of solutions depending on your directory structure, you can always put a . in front of the source folder name. I have noticed (at least with the older versions of the script, I do not know if it is still like this) the folder that has the files in it can't have a . in front of it or the grabber wont work, however you can have say an .audio folder with regular folders inside and it will work from those regular folders, and then keep the avatars outside of the .audio folder. If there is an easier way I would be interested as well.
Yes, folders with a dot in front will be ignored. The path specified can have dots in any place but not the sub folders.
I will maybe implement a way to build the folder structure. Then the avatars created will be categorized as the actual source.
Also, I will probably implement a way to change nautilus icons.
All this is in the maybe state....

> **andrek said:**
> Hey, what do I have to do if I want an exactly result as showed on this pic [http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg](http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg) ?
If you have already created some music avatars and they are not set to act like folders then when clicked the music widget should appear. Just drag and drop another music avatar to the widget to add it to the playlist. The widget should change and show two albums. You can add as many albums as you like.

---

### Post by jayde6 on 2008-02-01
> **Yuzem said:**
> Thanks.
I am using epm package manager. I added "-a all" to the command parameters.
Could someone with a 64bit processor test the attached deb?
If it works I will upload it as the default deb.


I tried out your deb file, it wouldn't let me install it because it said there was a later version installed, however it no longer gave the wrong architecture error.

> 
Yes, folders with a dot in front will be ignored. The path specified can have dots in any place but not the sub folders.
I will maybe implement a way to build the folder structure. Then the avatars created will be categorized as the actual source.
Also, I will probably implement a way to change nautilus icons.
All this is in the maybe state....


I'd love the folder structure option. I spent a very long morning creating a fake directory structure (genre/artist/album in most cases) just for the avatars. It would be a much welcomed feature.

---

### Post by ayoli on 2008-02-01
> **jayde6 said:**
> I tried out your deb file, it wouldn't let me install it because it said there was a later version installed, however it no longer gave the wrong architecture error.
.

you may need to uninstall you version to do the test.

---

### Post by jayde6 on 2008-02-01
> **ayoli said:**
> you may need to uninstall you version to do the test.

True, I just didn't have the time at that moment. Not that it takes a long time or anything but, I went ahead and uninstalled and was able to use the new deb fine without errors. I think why it came up with the newer version already installed error is because the new deb is version .5.5 where as the previously released one was .5.5.2.

---

### Post by aidanr on 2008-02-01
> **Yuzem said:**
> Could someone with a 64bit processor test the attached deb?

Works fine.

---

### Post by jayde6 on 2008-02-01
I am having a little bit of trouble with the comic viewer. Decided to check it out and try out the cool bookmark feature, however I can't get it to go back to page 1. If I set it to 1 the avatar goes back to the "closed" look but it still opens to what ever page I had it set to last. Taking a look at the avatar properties, it sets the thumbnail to the correct image but does not change the link back to "comictitle-001.jpg". Any help is greatly appreciated.

---

### Post by svtfmook on 2008-02-01
i must be a total moron because i can't figure out how to use this thing.

---

### Post by Yuzem on 2008-02-01
First, thanks to jayde6 and aidanr for the testing.

> **jayde6 said:**
> I am having a little bit of trouble with the comic viewer. Decided to check it out and try out the cool bookmark feature, however I can't get it to go back to page 1. If I set it to 1 the avatar goes back to the "closed" look but it still opens to what ever page I had it set to last. Taking a look at the avatar properties, it sets the thumbnail to the correct image but does not change the link back to "comictitle-001.jpg". Any help is greatly appreciated.
It is a bug and it is already fixed:
[http://www.gnomefiles.org/app.php/Avatar_Factory](http://www.gnomefiles.org/app.php/Avatar_Factory)
Oh, and thanks for the feedback.

> **svtfmook said:**
> i must be a total moron because i can't figure out how to use this thing.
Well, what do you want to do?
You can start by going to the applications menu, and launching avatar-factory from there. The gui provides the basic functions.
If you want to do advanced thing you must use the command line.
You can also make custom actions for thunar or nautilus to make it easier.

---

### Post by PurposeOfReason on 2008-02-01
Has anybody tried this out with dolphin?

---

### Post by jayde6 on 2008-02-02
> **Yuzem said:**
> First, thanks to jayde6 and aidanr for the testing.

Oh, and thanks for the feedback.



No problem, glad I could help. : )

---

### Post by svtfmook on 2008-02-02
> 
Well, what do you want to do?
You can start by going to the applications menu, and launching avatar-factory from there. The gui provides the basic functions.
If you want to do advanced thing you must use the command line.
You can also make custom actions for thunar or nautilus to make it easier.
well, i would like to build the cd library.  however, when i try, i don't understand what it's doing.  when i open it up, i select the grabber (music),  then it asks me for a type, i really don't know the difference between them, so i choose "name".  then it opens a browser, so i assume i select my music folder, then it opens another file browser, which i assume is where you want to leave the built avatar-factory.  then it starts searching.... and searching... and searching.... then a window pops up that it's building the avatars, so i press ok.  it closes.  nothing changed.

now, i have my music arranged as artists/albums/songs, so there are some artists folders that have several album folders.  will that work with this?

also, i don't get how this works with amarok.  if it's just building a fancy file browser,  what does that have to do with amarok?

---

### Post by Yuzem on 2008-02-02
> **svtfmook said:**
> well, i would like to build the cd library.  however, when i try, i don't understand what it's doing.  when i open it up, i select the grabber (music),  then it asks me for a type, i really don't know the difference between them, so i choose "name".  then it opens a browser, so i assume i select my music folder, then it opens another file browser, which i assume is where you want to leave the built avatar-factory.  then it starts searching.... and searching... and searching.... then a window pops up that it's building the avatars, so i press ok.  it closes.  nothing changed.
The interface is very limited, you must read the tilte of the window. The first browser is to chose the folder to save and the last one is for your music folder.
I have to change that to make the save window the last one.
The other dialog is to chose the name of the avatars. You can have them with no name like in this screenshot:
[[IMG]http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.th.png[/IMG]](http://img379.imageshack.us/my.php?image=avatarfactoryfg3lk3.png)
The "number.title" one is to arrange them by the folder structure when sorted by name.

> **svtfmook said:**
> now, i have my music arranged as artists/albums/songs, so there are some artists folders that have several album folders.  will that work with this?
Yes, you only need to have the covers on the albums folders.

> **svtfmook said:**
> also, i don't get how this works with amarok.  if it's just building a fancy file browser,  what does that have to do with amarok?
When you clic on an album it will immediately star playing with the specified player and a widget will appear on the desktop.
To set the player:
```
gedit ~/.avatar-factory/avatar-launcher
```
And add:
```
music=amarok

```

---

### Post by andrek on 2008-02-02
> **Yuzem said:**
> If you have already created some music avatars and they are not set to act like folders then when clicked the music widget should appear. Just drag and drop another music avatar to the widget to add it to the playlist. The widget should change and show two albums. You can add as many albums as you like.

I don't get it. Here's what I did :
I opened 'avatar factory' from Accessories menu and choosed music from the list and 'title' as a scheme. Then I specified a folder to save and a source path.. It made some nice-looking icons in a folder I set before. Now when I try to drag&drop one icon to another one - nothing happens.

---

### Post by Yuzem on 2008-02-02
You must drag it to the widget on the desktop not to any other avatar.
It will work if you are using nautilus for your desktop icons. It is the default on gnome.
Also you may want to resize the widget to the maximum size to have the best result.
Right clic the widget and chose resize or something like that (mine is in spanish)

---

### Post by svtfmook on 2008-02-02
ahh, ok, now i got it.  i had it backwards before.

now i just need to download all my album art.

---

### Post by svtfmook on 2008-02-02
ok, couple problems.

#1, it's not grabbing all of my album art.

for example, if i have 3 albums, for 1 artist, it for some reason is only grabbing one of the albums.

the other problem is when i click to play, it moves the avatar to my desktop.

---

### Post by Yuzem on 2008-02-02
> **svtfmook said:**
> #1, it's not grabbing all of my album art.

for example, if i have 3 albums, for 1 artist, it for some reason is only grabbing one of the albums.
It grabs the albums by folders. It doesn't read mp3 tags. If the 3 album are all in the same folder it will grab only one.
The rule for the grabbing is simple. If a folder has music files and at least one picture inside for the cover the avatar will be created.

> **svtfmook said:**
> the other problem is when i click to play, it moves the avatar to my desktop.
It isn't being moved. That is the widget. You can drag and drop other albums to it to add them to the playlist.

To turn off the music widget:
```
gedit ~/.avatar-factory/avatar-launcher
```
and add:
```
music_widget=no
```

You can have additional help about the music grabber with:
```
avatar-factory -g music --help
```

---

### Post by svtfmook on 2008-02-02
the three albums are in separate folders in the artist folder

---

### Post by Yuzem on 2008-02-02
I'm guessing that the three folders have covers.
mmm... maybe the covers are not jpg or png pictures.
Or maybe the pictures are damaged.
Try to download other covers in jpg or png format.
You can convert any picture to another format with:
```
convert  originarl.gif  converted.jpg
```
Replace originarl.gif with the original picture.

---

### Post by svtfmook on 2008-02-02
ok, i see what's happening.
it's not grabbing wma files.
which wma is about 80% of my music collection (~1500 albums).

---

### Post by Yuzem on 2008-02-02
Ok, I will add wma for the next version.
To fix it now you can do the following:
```
sudo gedit /usr/local/share/avatar-factory/grabbers/music
```

Line 71 should look like this:
```
	if [[ "" != "$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname '*.mp3' -or -iname '*.aac' -or -iname '*.m4a' -or -iname '*.ogg' -or -iname '*.flac' \) -print -quit)" ]]; then
```

Change it to:
```
	if [[ "" != "$(find "$SOURCE_item" -maxdepth 1 -type f \( -iname '*.mp3' -or -iname '*.aac' -or -iname '*.m4a' -or -iname '*.ogg' -or -iname '*.flac' -or -iname '*.wma' \) -print -quit)" ]]; then
```

---

### Post by svtfmook on 2008-02-02
worked

awesome!

thanks!

---

### Post by QwUo173Hy on 2008-02-10
Fantastic. Thank you.

Drag and drop for a new cover image is not working for me with the current .deb (0.5.5.1 I  believe).

Here is the ouput when I try to do a new avatar for a single movie

> ja@ja-desktop:~/.avatar-factory/icons/film/dvd$ avatar-factory 
EOF encountered in a comment.
(standard_in) 1: parse error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: missing an image filename `/tmp/thumb15819.png'.
convert: unable to open image `/tmp/thumb15819.png': No such file or directory.
rm: cannot remove `/tmp/thumb15819.???': No such file or directory
[email]ja@ja-desktop:~/.avat[/email]ar-factory/icons/film/dvd$ 


---

### Post by Yuzem on 2008-02-10
> **jarlath said:**
> Drag and drop for a new cover image is not working for me with the current .deb (0.5.5.1 I  believe).
It is a bug, it will be fixed for the next version.
To fix it now you can do the following:
```
sudo gedit /usr/local/share/avatar-factory/launchers/film
```
Line 21 should look like this:
```
		. /usr/local/share/avatar-factory/themes/$theme_name
```
Change it to:
```
		icon_NAME="$avatar_filename"
		. /usr/local/share/avatar-factory/themes/$theme_name
		create_theme_icon
```

> **jarlath said:**
> Here is the ouput when I try to do a new avatar for a single movie
Is this the same problem as above? If not, what command are you using?

---

### Post by QwUo173Hy on 2008-02-11
Ah that fixes it - thanks! And yes, that output I posted was for the same problem. Keep up the good work.

---

### Post by picpak on 2008-02-22
This doesn't work with Exaile 0.2.12b. I use

```
avatar-factory --type 0 -g music Music/ ~/.exaile/covers/
```

to run it. Any ideas?

---

### Post by Yuzem on 2008-02-22
To use it with Exaile:
```
gedit ~/.avatar-factory/avatar-launcher
```
add:
```
music=exaile
```
Then launch the created avatars.

The --type option goes after the grabber, like this:
```
avatar-factory -g music  --type 0 Music/ ~/.exaile/covers/
```
That will make the avatars act like folders.

To save the icons use:
```
avatar-factory -g music --save-as icons Music/ ~/.exaile/covers/
```
The previous command will not create any avatar just icons.

Have fun. :)

---

### Post by picpak on 2008-02-22
Thanks, but it says there's no cover for every song, despite the fact I just downloaded them all with Exaile's Album Art collector. Any ideas?

---

### Post by Yuzem on 2008-02-22
The covers must be inside each album folder. they must be in jpg or png format.
Try this, copy a cover to a folder with music files inside and do:

```
avatar-factory -g music folder/with/cover/and music ~/Desktop
```

---

### Post by picpak on 2008-02-22
But I have over 4500 songs, no way am I copying covers inside each folder...thanks though!

---

### Post by Yuzem on 2008-02-23
You can check this posts about mass grabbing covers directly to the correct folders:
[Album Cover Art Downloader]("http://ubuntuforums.org/showpost.php?p=3266072&postcount=50")
[Sonata]("http://ubuntuforums.org/showpost.php?p=3332652&postcount=136")

---

### Post by picpak on 2008-02-23
But this is the thing...I have 106MB of covers and it takes a long time to download them all again. I don't want to redownload them all and sort them in folders, and have 212MB worth of covers.

Is there nothing that can grab the same covers as Exaile and sort them in folders? By symlinking the covers, perhaps?

---

### Post by Yuzem on 2008-02-23
The problem is how to know where the covers should go.
I installed exaile and it seems that it saves the covers with an encoded name that could be based on the path to the file.
If that is true it is possible but it is very complicated and I don't know how the names are encoded.

---

### Post by picpak on 2008-02-23
It appears to me that the filenames are md5sum'ed.

```
kim@ubuntu:~$ cd .exaile/covers/
kim@ubuntu:~/.exaile/covers$ md5sum 0a04c1e4f29ed19038a5e7e20d079d52.jpg 
0a04c1e4f29ed19038a5e7e20d079d52  0a04c1e4f29ed19038a5e7e20d079d52.jpg
kim@ubuntu:~/.exaile/covers$
```

The md5sum and the filename are the same.

---

### Post by Yuzem on 2008-02-24
That was my first guess but the problem is to find out to what it is applied.
I tried:
```
echo -n "path/2/song" | md5sum
```
It didn't match the right cover.
Maybe it is based on the name of the albums or: artist - album...
I will check it later.

---

### Post by picpak on 2008-02-24
The code Exaile uses is under /usr/lib/exaile/xl/covers.py. Apparently it registers it under ~/.exaile/music.db. I don't know how to open db files, but if I did I could probably help.

---

### Post by ayoli on 2008-02-24
> **picpak said:**
> It appears to me that the filenames are md5sum'ed.

```
kim@ubuntu:~$ cd .exaile/covers/
kim@ubuntu:~/.exaile/covers$ md5sum 0a04c1e4f29ed19038a5e7e20d079d52.jpg 
0a04c1e4f29ed19038a5e7e20d079d52  0a04c1e4f29ed19038a5e7e20d079d52.jpg
kim@ubuntu:~/.exaile/covers$
```

The md5sum and the filename are the same.

The file is md5sum'ed not the file name, I guess exaile stores a relation btween the cover and the album in a sort of database.
It can be interesting and useful to ask exaile devs on their forums :
[http://www.exaile.org/forum/](http://www.exaile.org/forum/)

---

### Post by Yuzem on 2008-02-24
> **picpak said:**
> But this is the thing...I have 106MB of covers and it takes a long time to download them all again. I don't want to redownload them all and sort them in folders, and have 212MB worth of covers.

Is there nothing that can grab the same covers as Exaile and sort them in folders? By symlinking the covers, perhaps?
If the problem is the space. I have 4208 songs but only 147 avatars (albums).
Exaile downloads covers for single tracks too and thats could probable be the cause of the high disk usage.
If you count only albums, I checked the size of a cover in jpg 800x600, about 100 KBytes.
100x147=14.700 KBytes
It isn't much.

> **picpak said:**
> The code Exaile uses is under /usr/lib/exaile/xl/covers.py. Apparently it registers it under ~/.exaile/music.db. I don't know how to open db files, but if I did I could probably help.
I installed exaile and /usr/lib/exaile/xl/covers.py doesn't exist
locate covers.py returns nothing...

> **ayoli said:**
> The file is md5sum'ed not the file name, I guess exaile stores a relation btween the cover and the album in a sort of database.
It can be interesting and useful to ask exaile devs on their forums :
[http://www.exaile.org/forum/](http://www.exaile.org/forum/)
Yes, I think that it is based on the name of the album and the artist not the filename or path to prevent downloading twice the same cover.

---

### Post by ayoli on 2008-02-24
```
$)&#9472;> locate covers.py
/usr/lib/exaile/xl/covers.pyc
/usr/lib/exaile/xl/covers.pyo
/usr/lib/exaile/xl/covers.py
```
you should have update your locate db before
```
sudo updatedb
```
btw, it could also be under /usr/share/lib/exaile if you used /usr/share as prefix

---

### Post by Yuzem on 2008-02-24
You are right, it is on /usr/share/lib/exaile
I saw the md5 thing but I don't know to what it is applied.
I don't understand much python... :confused:

---

### Post by ayoli on 2008-02-24
> **Yuzem said:**
> You are right, it is on /usr/share/lib/exaile
I saw the md5 thing but I don't know to what it is applied.
I don't understand much python... :confused:

I think the md5 sum is applied to the image file. Not very useful for you.
I guess it will be more interesting to look how exaile stores the relation between the cover and the album.
btw, the trick could be to have a killer feature in exaile to save the cover where we want :)

---

### Post by picpak on 2008-02-24
> **Yuzem said:**
> If the problem is the space. I have 4208 songs but only 147 avatars (albums).
Exaile downloads covers for single tracks too and thats could probable be the cause of the high disk usage.
If you count only albums, I checked the size of a cover in jpg 800x600, about 100 KBytes.
100x147=14.700 KBytes
It isn't much.

My problem isn't about space, I just don't want to duplicate so many images if I don't have to.

Anyway, I ended up deleting my music.db (it listed way more tracks than I really had and it was the only solution) and now my songs don't have any covers set to them any more. Since the album art collector was buggy for me, I'll try playing around with Sonata.

---

### Post by picpak on 2008-02-25
Ladies and gentlemen, our prayers have been answered!

[https://bugs.launchpad.net/exaile/+bug/135936](https://bugs.launchpad.net/exaile/+bug/135936)

Scroll down to the bottom post, download exaile-cover-mover.py, and run it with "python exaile-cover-mover.py". And guess what? It works!

The only thing that didn't work was covers with non-Unicode characters. It also deletes them from ~/.exaile/covers afterwords, so I don't need to worry about duplicates. :)

---

### Post by Yuzem on 2008-02-25
Nice, I will add a link to your post on the first post.

I have something else to say, I made another little script. I think that those how like the film grabber will like this also:
[http://ubuntuforums.org/showthread.php?p=4398218](http://ubuntuforums.org/showthread.php?p=4398218)

---

### Post by picpak on 2008-02-25
Thanks, but I have another problem:

> **Yuzem said:**
> The --type option goes after the grabber, like this:
```
avatar-factory -g music  --type 0 Music/ ~/.exaile/covers/
```
That will make the avatars act like folders.

To save the icons use:
```
avatar-factory -g music --save-as icons Music/ ~/.exaile/covers/
```
The previous command will not create any avatar just icons.

Have fun. :)

I ran these commands, but they didn't work on my Music folder. It works on ~/.avatar-factory/covers, however (the path that I used to save them to). Is this the only folder it applies to?

---

### Post by Yuzem on 2008-02-25
Avatar Factory makes shortcuts too your music albums that look like the album. Those inside the folder where you save them are the avatars.

If you save them as icons you will only have the icons and if you use the type 0 option you will have the avatars behaving like if they were folders.
Nothing will change on your music folder.

You will have another folder with all your albums to play them from there.

---

### Post by picpak on 2008-02-25
That's not what I want...however, I found another script that does what I want:

[http://ubuntuforums.org/showpost.php?p=2799388&postcount=19](http://ubuntuforums.org/showpost.php?p=2799388&postcount=19)

Thanks, anyway! Thank you for all your help too. :)

---

### Post by swimb on 2008-03-05
Thanks for this its good stuff. Is there a way to have no theme? Can I request a new 'none' theme for just plain avatars? Ive tried --save-as icons/thumbnails and the -t options but none are what I want. Thanks again

---

### Post by swimb on 2008-03-05
my apologies, my first post and im already asking for stuff :)

---

### Post by jayde6 on 2008-03-06
you could try changing to the shadow theme. It is kinda like not having one (just the image with a drop shadow) I think it looks pretty good in place of the dvd and the cd themes.
If you are using nautilus you can make a script in /home/'user-name'/.gnome2/nautilus-scripts that says

```
avatar-factory -g avatar -t --gui --gui-progress "$1"
```

that will let you right click on an avatar and change it using the gui.

---

### Post by swimb on 2008-03-06
Yes that looks great, thank you! -t shadow was the one, It lets the avatars keep their aspect ratio too and allows them to look not so exactly the same, I like it.

---

### Post by jayde6 on 2008-03-06
Glad I could help : ).

---

### Post by Yuzem on 2008-03-12
New version:

+A new interface has been implemented. Now it is a little less intuitive but much more useful.
The "save as" dialog is now the last step.

+New option to replicate folder structure: "--folders"

+--avatar-launcher option can now overwrite the default launcher. It is possible now to make a nautilus/thunar action to for example add the album instead of replacing the playlist.

```
12.03.08------0.6
	+music grabber: added wma support
	+gui: save is now the last step
	+film launcher: fixed drag and drop to set the cover
	+film grabber: added bin file type
	+code cleanup
	+allows to execute without install
	+grabbers help abstracted from grabbers
	+the gui has been abstracted to one function
	+new and improved gui
	+music launcher: support for all players has been rewritten.
	+--avatar-launcher option can now overwrite the default launcher
	+added --folders option to replicate folder structure
	+mame grabber: speed improvement
```

---

### Post by jayde6 on 2008-03-12
Lots of great additions : ),

A couple things though,
When using the folders option it goes only 1 folder depth. Is there a way for it to go more than that. For example My Music folder is setup like
/Music/<Genre>/<Artist>/<Album>/
Currently it makes avatars for the albums in /Music/<Genre>/.
Also it stops about halfway through my music regardless of the folder option or not. 

All help is appreciated,
~Jennifer

p.s. for when i get this working what is the nautilus actions for add and send?
Thanks again.

EDIT:
It was easy enough to just make the genre folders first then use avatar factory. When I did, it no longer stopped half way through. No idea what caused it trouble when trying to process my entire music folder.

---

### Post by Yuzem on 2008-03-12
> **jayde6 said:**
> When using the folders option it goes only 1 folder depth. Is there a way for it to go more than that. For example My Music folder is setup like
/Music/<Genre>/<Artist>/<Album>/
Currently it makes avatars for the albums in /Music/<Genre>/.
It is a bug, I will try to fix it.

> **jayde6 said:**
> 
Also it stops about halfway through my music regardless of the folder option or not. 
That is using the gui or the same happens from the command line?

> **jayde6 said:**
> 
p.s. for when i get this working what is the nautilus actions for add and send?
Thanks again.
Something like this:
```
avatar-factory -al --launcher mpd-add album1.desktop album2.desktop etc
```
It is on the man page.
You are welcome.

---

### Post by jayde6 on 2008-03-12
> **Yuzem said:**
> It is a bug, I will try to fix it.


That is using the gui or the same happens from the command line?



Using the gui. I tested with the command line just now (after removing my .avatar-factory/icons/music/cd directory to do a clean test) and it worked fine (with the exception of the directory problem noted earlier). When I created the genre folders earlier to make avatars in I had used the command line as well.

> **Yuzem said:**
> 
Something like this:
```
avatar-factory -al --launcher mpd-add album1.desktop album2.desktop etc
```
It is on the man page.
You are welcome.

Thanks, I had looked at the help for -g music and saw the -add command but didnt know how to put it all together.

---

### Post by aidanr on 2008-03-12
> **jayde6 said:**
> Also it stops about halfway through my music regardless of the folder option or not

Same here, stops after 100 launchers with the gui, works fine on the command line.

---

### Post by jayde6 on 2008-03-12
Also with the add to playlist command you gave it has no effect as a nautilus action or through the command line, this is the output

```
jayde6@jayde6-desktop:~/Music/Metal/Within Temptation$ avatar-factory -al --launcher mpd-add "The Heart of Everything.desktop"
cat: mpd-add: No such file or directory
cat: The Heart of Everything.desktop: No such file or directory
jayde6@jayde6-desktop:~/Music/Metal/Within Temptation$ /usr/local/bin/avatar-factory: line 45: eval: --: invalid option
eval: usage: eval [arg ...]
/usr/local/bin/avatar-factory: line 45: eval: --: invalid option
eval: usage: eval [arg ...]
```

---

### Post by Yuzem on 2008-03-12
Ok, I think it is fixed now.
The deb is attached.
Could someone confirm that the bugs are gone?

---

### Post by jayde6 on 2008-03-12
> **Yuzem said:**
> Ok, I think it is fixed now.
The deb is attached.
Could someone confirm that the bugs are gone?

It just hangs on "Processing Music" doesn't actually do anything.

---

### Post by Yuzem on 2008-03-12
> **jayde6 said:**
> Also with the add to playlist command you gave it has no effect as a nautilus action or through the command line, this is the output

```
jayde6@jayde6-desktop:~/Music/Metal/Within Temptation$ avatar-factory -al --launcher mpd-add "The Heart of Everything.desktop"
cat: mpd-add: No such file or directory
cat: The Heart of Everything.desktop: No such file or directory
jayde6@jayde6-desktop:~/Music/Metal/Within Temptation$ /usr/local/bin/avatar-factory: line 45: eval: --: invalid option
eval: usage: eval [arg ...]
/usr/local/bin/avatar-factory: line 45: eval: --: invalid option
eval: usage: eval [arg ...]
```

mmm... I have no idea, let me see...

---

### Post by aidanr on 2008-03-12
Ok, so it now processes all the covers, but the progress bar seems to be broken now and also it names them all 1 (--name 1) instead of 1,2,3,... Again works fine on the command line.

---

### Post by jayde6 on 2008-03-12
Aidanr is right I thought it did nothing when i tried it, i didn't wait for the all done dialog. It works perfect (minus the progress bar) with -name 2 and the --folders options.

---

### Post by Yuzem on 2008-03-12
I think it is all fixed now.
Again, I attached a deb for testing.

---

### Post by jayde6 on 2008-03-12
> **Yuzem said:**
> I think it is all fixed now.
Again, I attached a deb for testing.

Everything seems to be fixed as far as making the avatars through the gui (tested -name 1 as well). Though I still can't get an action to add an avatar to the playlist. It now outputs

```
jayde6@jayde6-desktop:~/Music/Adult Alternative/Meredith Brooks$ avatar-factory -al --launcher mpd-add "Blurring the Edges.desktop"
cat: Blurring the Edges.desktop: No such file or directory
jayde6@jayde6-desktop:~/Music/Adult Alternative/Meredith Brooks$ /usr/local/bin/avatar-factory: line 44: eval: --: invalid option
eval: usage: eval [arg ...]
```

---

### Post by aidanr on 2008-03-12
That fixed things for me. I can confirm jayde6's problem, although it works if you supply the full path.

---

### Post by jayde6 on 2008-03-12
> **aidanr said:**
> That fixed things for me. I can confirm jayde6's problem, although it works if you supply the full path.

Awesome, that works great. Thanks

---

### Post by Yuzem on 2008-03-13
Ok, I will leave the full path problem for the next version.
aidanr and jayde6, thanks both for the feedback. :)

---

### Post by direk_ on 2008-03-14
How to use widgets? When i'm trying to run "avatar-factory --widget" nothin happens :/

---

### Post by Yuzem on 2008-03-14
The --widget option is to automatically show/hide the music widget.
The widget is created when you make click on a music avatar if it is configured to act as a launcher.

Then for example if you have totem configured as your music player for music avatars you can run "avatar-factory --widget" and the widget will hide if totem is not running and it will be shown if it is running.

---

### Post by direk_ on 2008-03-14
My config:
----------------------
music="mpd"
music_widget=yes
mpd_port=6600
mpd_host=127.0.0.1
----------------------
And when i'm clicking launcher-type avatar music starts, but nothing else happends.

---

### Post by Yuzem on 2008-03-14
> **direk_ said:**
> 
And when i'm clicking launcher-type avatar music starts, but nothing else happends.

You config seems ok, I am not sure if I understand correctly. My english is not very good.
You say that when you click on a music avatar the music start playing and no widget appears. Is that correct?

If it is, the problem could be the name of your desktop folder.
Go to your user folder:
```
nautilus $HOME
```
If your desktop folder name is not Desktop then that must be the cause.
I don't know how to get the Desktop folder name from bash.

To fix it you can do this from the terminal:
```
 ln -s ~/DesktopName ~/Desktop
```
Replace "DesktopName" with the name of your Desktop folder.

---

### Post by direk_ on 2008-03-14
Yeah, it was a problem. My desktop dir is "Pulpit" (polish version of ubuntu). But I found a file:
~/.config/user-dirs.dirs
There's defined desktop folder name:
XDG_DESKTOP_DIR="$HOME/Pulpit"

I think you can use it :)


Please tell me one more thing. How to create launcher-type avatars, that will ADD songs to mpd playlist, not overwrite it?

---

### Post by Yuzem on 2008-03-14
> **direk_ said:**
> Yeah, it was a problem. My desktop dir is "Pulpit" (polish version of ubuntu). But I found a file:
~/.config/user-dirs.dirs
There's defined desktop folder name:
XDG_DESKTOP_DIR="$HOME/Pulpit"

I think you can use it :)
Great, I will, thanks. :)

> **direk_ said:**
> 
Please tell me one more thing. How to create launcher-type avatars, that will ADD songs to mpd playlist, not overwrite it?
Add the following to the configuration file or overwrite the existing key:
```
music=mpd-add
```

Also, you can add albums to the playlist by dragging and dropping a music avatar to the widget. It will work better if you resize the widget to it maximum size.

---

### Post by QwUo173Hy on 2008-03-30
Hi Yuzem,

I'm getting errors with the Gui and the command line. I saved the output here. Could you take a look?

Nice work with the Gui by the way. I much prefer it.

Jarlath

---

### Post by Yuzem on 2008-03-31
> **jarlath said:**
> I'm getting errors with the Gui and the command line. I saved the output here. Could you take a look?
Of course, try this:
```
sudo gedit /usr/local/share/avatar-factory/grabbers/film
```

line 27 should look like this:
```
		grabber_picture="$themes_PATH/Vinyl/base.png"
```

Change it to:
```
		grabber_picture="$avatar_factory_PATH/themes/Vinyl/base.png"
```

Does it work?

> **jarlath said:**
> Nice work with the Gui by the way. I much prefer it.
Thanks :)

---

### Post by QwUo173Hy on 2008-03-31
Hi Yuzem. This still doesn't work. (By the way, it's line 27, not 24).

---

### Post by Yuzem on 2008-03-31
> **jarlath said:**
> Hi Yuzem. This still doesn't work. (By the way, it's line 27, not 24).
Hi.
You are right, it is line 27

Try to change line 22:
```
	grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2)
```
To:
```
	grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2 | egrep 'jpg$|gif$|png$')
```

---

### Post by QwUo173Hy on 2008-04-01
That didn't work either Yuzem.

The end result is the same. I get a folder full of blank icons.

And this is the output
```
jarlath@jarlath-laptop:~$ avatar-factory -g film -t dvd --name 2 /home/jarlath/Videos /home/jarlath/Movies
Building list of files to process...
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png'.
1/55 - added Atonement 2007
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Black Sheep.png'.
2/55 - added Black Sheep
There is no cover for Fleetwood Mac - Live In Boston 2004 - 
There is no cover for Fleetwood Mac - Live In Boston 2004 - 
/tmp/thumb16375.text/html;: No such file or directory
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
EOF encountered in a comment.
(standard_in) 1: syntax error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
convert: missing an image filename `/tmp/thumb16375.png'.
convert: unable to open image `/tmp/thumb16375.png': No such file or directory.
convert: unable to open file `/tmp/thumb16375.png'.
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-01.png'.
rm: cannot remove `/tmp/thumb16375.???': No such file or directory
3/53 - added go-open-episode-01
/tmp/thumb16375.text/html;: No such file or directory
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
EOF encountered in a comment.
(standard_in) 1: syntax error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
convert: missing an image filename `/tmp/thumb16375.png'.
convert: unable to open image `/tmp/thumb16375.png': No such file or directory.
convert: unable to open file `/tmp/thumb16375.png'.
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-02.png'.
rm: cannot remove `/tmp/thumb16375.???': No such file or directory
4/53 - added go-open-episode-02
/tmp/thumb16375.text/html;: No such file or directory
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
EOF encountered in a comment.
(standard_in) 1: syntax error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
convert: missing an image filename `/tmp/thumb16375.png'.
convert: unable to open image `/tmp/thumb16375.png': No such file or directory.
convert: unable to open file `/tmp/thumb16375.png'.
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-03.png'.
rm: cannot remove `/tmp/thumb16375.???': No such file or directory
5/53 - added go-open-episode-03
/tmp/thumb16375.text/html;: No such file or directory
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
EOF encountered in a comment.
(standard_in) 1: syntax error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
convert: missing an image filename `/tmp/thumb16375.png'.
convert: unable to open image `/tmp/thumb16375.png': No such file or directory.
convert: unable to open file `/tmp/thumb16375.png'.
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-04.png'.
rm: cannot remove `/tmp/thumb16375.???': No such file or directory
6/53 - added go-open-episode-04
/tmp/thumb16375.text/html;: No such file or directory
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
EOF encountered in a comment.
(standard_in) 1: syntax error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
convert: missing an image filename `/tmp/thumb16375.png'.
convert: unable to open image `/tmp/thumb16375.png': No such file or directory.
convert: unable to open file `/tmp/thumb16375.png'.
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-05.png'.
rm: cannot remove `/tmp/thumb16375.???': No such file or directory
7/53 - added go-open-episode-05
/tmp/thumb16375.text/html;: No such file or directory
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
EOF encountered in a comment.
(standard_in) 1: syntax error
/usr/local/share/avatar-factory/themes/dvd: line 24: [: -gt: unary operator expected
convert: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
convert: missing an image filename `/tmp/thumb16375.png'.
convert: unable to open image `/tmp/thumb16375.png': No such file or directory.
convert: unable to open file `/tmp/thumb16375.png'.
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-06.png'.
rm: cannot remove `/tmp/thumb16375.???': No such file or directory
8/53 - added go-open-episode-06
/tmp/thumb16375.text/html;: No such file or directory

```
Thanks for your time so far!

Jarlath

---

### Post by Yuzem on 2008-04-01
Strange, it worked here...
Could you post the result of this command:
```
cat /usr/local/share/avatar-factory/grabbers/film
```

---

### Post by QwUo173Hy on 2008-04-02
Sure, here you go

```
#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Application
	SOURCE_type=files
	SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue,iso,bin
}

grabber_secondary_options () {
	avatar_title="$(echo ${SOURCE_item##*/} | sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/_/ /' -e 's/\./ /' -e 's\....$\\')"
	avatar_filename="$(echo ${SOURCE_item%/*} | sed -e 's/\//\_/g')_$avatar_title"
	avatar_name="$avatar_title"
	URL="file://$SOURCE_item"
	icon_NAME="$avatar_filename"
	Launcher="avatar-factory -al $grabber_name --URL \"$SOURCE_item\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	imdb_page="$(wget -U firefox -qO - "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$(echo "$avatar_title" | sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')&btnI=I%27m+Feeling+Lucky&meta=")"
	photo_line_number=$(( $(echo "$imdb_page" | grep -n -i '<div class="photo">' | cut -d: -f1 ) + 1 ))
	grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2)
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	else
	grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2 | egrep 'jpg$|gif$|png$')
	fi
}
```

---

### Post by Yuzem on 2008-04-02
Ok, it seems that you didn't change line 22 but line 27.
It should be like this:
```
#!/bin/bash

grabber_primary_options () {
        theme_name=dvd
        Link_or_Application=Application
        SOURCE_type=files
        SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue,iso,bin
}

grabber_secondary_options () {
        avatar_title="$(echo ${SOURCE_item##*/} | sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/_/ /' -e 's/\./ /' -e 's\....$\\')"
        avatar_filename="$(echo ${SOURCE_item%/*} | sed -e 's/\//\_/g')_$avatar_title"
        avatar_name="$avatar_title"
        URL="file://$SOURCE_item"
        icon_NAME="$avatar_filename"
        Launcher="avatar-factory -al $grabber_name --URL \"$SOURCE_item\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
        imdb_page="$(wget -U firefox -qO - "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$(echo "$avatar_title" | sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')&btnI=I%27m+Feeling+Lucky&meta=")"
        photo_line_number=$(( $(echo "$imdb_page" | grep -n -i '<div class="photo">' | cut -d: -f1 ) + 1 ))
        grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2 | egrep 'jpg$|gif$|png$')
        if [[ -n $grabber_picture ]]; then
                wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
                grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
        else
                grabber_picture="$avatar_factory_PATH/themes/Vinyl/base.png"
        fi
}
```

---

### Post by QwUo173Hy on 2008-04-02
Still no luck Yuzem. Am I running the command properly? This is what's going on in my terminal:

```
jarlath@jarlath-laptop:~$ avatar-factory -g film -t dvd --name 2 /home/jarlath/Videos /home/jarlath/Movies
Building list of files to process...
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png'.
1/77 - added Atonement 2007
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Black Sheep.png'.
2/77 - added Black Sheep
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Fleetwood Mac - Live In Boston_Fleetwood Mac - Live In Boston 2004 - .png'.
3/77 - added Fleetwood Mac - Live In Boston 2004 - 
jarlath@jarlath-laptop:~$ sudo gedit /usr/local/share/avatar-factory/grabbers/film
jarlath@jarlath-laptop:~$ rm Movies/*
jarlath@jarlath-laptop:~$ avatar-factory -g film -t dvd --name 2 /home/jarlath/Videos /home/jarlath/Movies
Building list of files to process...
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png'.
1/77 - added Atonement 2007
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Black Sheep.png'.
2/77 - added Black Sheep
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Fleetwood Mac - Live In Boston_Fleetwood Mac - Live In Boston 2004 - .png'.
3/77 - added Fleetwood Mac - Live In Boston 2004 - 
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Fleetwood Mac - Live In Boston_Fleetwood Mac - Live In Boston 2004 - .png'.
4/77 - added Fleetwood Mac - Live In Boston 2004 - 
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-01.png'.
5/77 - added go-open-episode-01
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-02.png'.
6/77 - added go-open-episode-02
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-03.png'.
7/77 - added go-open-episode-03
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-04.png'.
8/77 - added go-open-episode-04
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-05.png'.
9/77 - added go-open-episode-05
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_go-open-vol-1_go-open-episode-06.png'.
10/77 - added go-open-episode-06
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Gorillaz-Demon Days-Live at Manchester Opera House.png'.
11/77 - added Gorillaz-Demon Days-Live at Manchester Opera House
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Hollow Man 2000.png'.
12/77 - added Hollow Man 2000

```

---

### Post by Yuzem on 2008-04-02
The command is ok.
Now it is a different error. All the:
```
/tmp/thumb16375.text/html;: No such file or directory
```
and:
```
identify: unable to open image `/tmp/thumb16375.text/html; charset=ISO-8859-1': No such file or directory.
```
are gone...

Tell me the output of this command:
```
bash -x avatar-factory -g film -t dvd --name 2 /home/jarlath/Videos/Atonement* /home/jarlath/Movies
```

---

### Post by QwUo173Hy on 2008-04-02
Okay - the result of that command is:

```
jarlath@jarlath-laptop:~$ bash -x avatar-factory -g film -t dvd --name 2 /home/jarlath/Videos/Atonement* /home/jarlath/Movies
++ which avatar-factory
+ [[ /usr/local/bin/avatar-factory != /usr/local/bin/avatar-factory ]]
+ avatar_factory_PATH=/usr/local/share/avatar-factory
+ app_config=/home/jarlath/.avatar-factory
+ gui_config=/home/jarlath/.avatar-factory/avatar-factory
+ app_icon=/usr/local/share/avatar-factory/avatar-factory.png
+ save_as=avatars
+ . /usr/local/share/avatar-factory/gui
+ '[' 8 = 0 ']'
+ number=0
+ '[' -g '!=' '' ']'
+ case $1 in
+ shift
+ '[' film = --gui ']'
+ '[' -f /usr/local/share/avatar-factory/grabbers/film ']'
+ grabber_name=film
+ . /usr/local/share/avatar-factory/grabbers/film
+ grabber_primary_options
+ theme_name=dvd
+ Link_or_Application=Application
+ SOURCE_type=files
+ SOURCE_filter=avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue,iso,bin
+ shift
+ '[' -t '!=' '' ']'
+ case $1 in
+ shift
+ '[' dvd = --gui ']'
+ '[' -f /usr/local/share/avatar-factory/themes/dvd ']'
+ theme_name=dvd
+ shift
+ '[' --name '!=' '' ']'
+ case $1 in
+ shift
+ '[' 2 = --gui ']'
+ set_name=2
+ shift
+ '[' '/home/jarlath/Videos/Atonement 2007.avi' '!=' '' ']'
+ case $1 in
+ number=1
+ SOURCE_input[$number]='/home/jarlath/Videos/Atonement 2007.avi'
+ shift
+ '[' /home/jarlath/Movies '!=' '' ']'
+ case $1 in
+ number=2
+ SOURCE_input[$number]=/home/jarlath/Movies
+ shift
+ '[' '' '!=' '' ']'
+ [[ -z film ]]
+ '[' film = avatar ']'
+ [[ avatars = thumbnails ]]
+ [[ avatars = nautilus_icons ]]
+ '[' /home/jarlath/Movies = --gui ']'
+ '[' -d /home/jarlath/Movies ']'
+ cd /home/jarlath/Movies
++ pwd
+ folder2save=/home/jarlath/Movies
+ cd /home/jarlath
+ SOURCE_input[$number]=
+ max_number=1
+ case $SOURCE_type in
+ [[ /home/jarlath/Videos/Atonement 2007.avi  = '' ]]
++ seq 1 1
+ for number in '$(seq 1 "$max_number")'
+ '[' '/home/jarlath/Videos/Atonement 2007.avi' = --gui ']'
+ '[' -f '/home/jarlath/Videos/Atonement 2007.avi' ']'
+ cd /home/jarlath/Videos
++ pwd
+ SOURCE_list[$number]='/home/jarlath/Videos/Atonement 2007.avi'
+ cd /home/jarlath
++ echo avi,ogm,mpg,divx,mpeg,mov,mp4,mkv,wmv,asf,flv,cue,iso,bin
++ sed -e 's/,$//' -e 's/,/\$|/g' -e 's/$/$/'
+ SOURCE_filter='avi$|ogm$|mpg$|divx$|mpeg$|mov$|mp4$|mkv$|wmv$|asf$|flv$|cue$|iso$|bin$'
++ echo '/home/jarlath/Videos/Atonement 2007.avi'
++ egrep -i 'avi$|ogm$|mpg$|divx$|mpeg$|mov$|mp4$|mkv$|wmv$|asf$|flv$|cue$|iso$|bin$'
+ SOURCE_list[$number]='/home/jarlath/Videos/Atonement 2007.avi'
+ [[ 1 != \1 ]]
+ shift
+ '[' /home/jarlath/Movies = --gui ']'
+ case $SOURCE_type in
+ number=1
+ index=1
+ set_index=
++ echo '/home/jarlath/Videos/Atonement 2007.avi'
++ wc -l
+ total_lines=1
+ [[ film != avatar ]]
+ . /usr/local/share/avatar-factory/themes/dvd
+ case $save_as in
+ icons_PATH=/home/jarlath/.avatar-factory/icons/film/dvd
+ echo '/home/jarlath/Videos/Atonement 2007.avi'
+ read -r SOURCE_item
++ echo '/home/jarlath/Videos/Atonement 2007.avi'
+ [[ -n '' ]]
+ cat
++ sed 's/||||.*$//'
+ folder_node='/home/jarlath/Videos/Atonement 2007.avi'
++ echo '/home/jarlath/Videos/Atonement 2007.avi'
++ sed 's/^.*||||//'
+ SOURCE_item='/home/jarlath/Videos/Atonement 2007.avi'
+ case $SOURCE_type in
+ grabber_secondary_options
++ echo Atonement 2007.avi
++ sed -e 's/[cC][dD][1-9]//' -e 's/[\(][1-9][oO][fF][1-9][\)]//' -e 's/[1-9][oO][fF][1-9]//' -e 's/_/ /' -e 's/\./ /' -e 's\....$\\'
+ avatar_title='Atonement 2007'
++ echo /home/jarlath/Videos
++ sed -e 's/\//\_/g'
+ avatar_filename='_home_jarlath_Videos_Atonement 2007'
+ avatar_name='Atonement 2007'
+ URL='file:///home/jarlath/Videos/Atonement 2007.avi'
+ icon_NAME='_home_jarlath_Videos_Atonement 2007'
+ Launcher='avatar-factory -al film --URL "/home/jarlath/Videos/Atonement 2007.avi" --name "Atonement 2007" --title "Atonement 2007" --icon "/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png" --DND'
+ [[ 0 = 1 ]]
+ '[' -n 2 ']'
+ case $set_name in
+ avatar_name='Atonement 2007'
+ case $save_as in
+ [[ -f /home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png ]]
+ [[ -z '' ]]
+ get_grabber_picture
+++ echo 'Atonement 2007'
+++ sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g'
++ wget -U firefox -qO - 'http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+Atonement+2007&btnI=I%27m+Feeling+Lucky&meta='
+ imdb_page='
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<title>Atonement (2007)</title>
<meta name="title" content="Atonement (2007)">
<meta name="description" content="Directed by Joe Wright.  With Saoirse Ronan, Ailidh Mackay, Brenda Blethyn. Fledgling writer Briony Tallis, as a 13-year-old, irrevocably changes the course of several lives when she accuses her older sister'\''s (Keira Knightley) lover (James McAvoy) of a crime he did not commit. Based on the British romance novel by Ian McEwan. Visit IMDb for Photos, Showtimes, Cast, Crew, Reviews, Plot Summary, Comments, Discussions, Taglines, Trailers, Posters, Fan Sites">

<meta name="keywords" content="Reviews, Showtimes, DVDs, Photos, Message Boards, User Ratings, Synopsis, Trailers, Credits">
<link rel="stylesheet" type="text/css" media="screen" href="http://i.media-imdb.com/images/SF01c175f07a3ed070f8f38d7f98c6ca3f/css2/consumersite.css" />
<link rel="icon" href="http://i.imdb.com/favicon.ico" />
<link rel="apple-touch-icon" href="http://i.media-imdb.com/apple-touch-icon.png" />
<style type="text/css">.showtimes { font-family: Arial, Helvetica, sans-serif }.showtimes .heading { font-size: 16px; font-weight: bold }.showtimes .time { color: #ff0000 }.tabular { border-collapse: collapse; border: 1px solid #9999ff }.tabular td.heading { background: #bbbbff }.tabular td.heading-right { background: #bbbbff; text-align: right; font-size: small }.tabular td.address { font-size: small; color: #666666; background: #eeeeee }.tabular td.detail { font-size: small; background: #eeeeee }.tabular tr.alternate { background: #eeeeee }.tabular td.item { border: 1px solid #9999ff }</style><link rel="stylesheet" type="text/css" href="http://i.media-imdb.com/images/SFae751da69684847117d205d2cbc0ae90/tn15/tn15.css" />

</head>
<!-- h=iop113 i=2008-04-01 s=legacy(default) t='\''Wed Apr  2 12:06:21 2008'\'' -->

<body bgcolor="#ffffff" text="#000000">
<div id="wrapper">
  
  

   <!-- sid : 35988 : TOP_BANNER --><div id="lea_728x90" style="height:90;" align="center"></div> 

<div id="root">
<layer name="root">

<div id="nb15">

  <div id="nb15home">
   <a href="/" onClick="(new Image()).src='\''/rg/nav-home/navbar/images/b.gif?link=/'\'';"><img src="http://i.media-imdb.com/images/nb15/logo2.gif" alt="Home" 
   title="The Internet Movie Database" border="0" width="177" height="78"></a>
  </div>
 <div id="nb15botbg">
 
  <div id="nb15tabs">
   <a id="nb15nowplaying" href="/nowplaying/" onClick="(new Image()).src='\''/rg/nav-nowplaying/navbar/images/b.gif?link=/nowplaying/'\'';"><i>Now Playing</i></a>
   <a id="nb15news" href="/news/" onClick="(new Image()).src='\''/rg/nav-news/navbar/images/b.gif?link=/news/'\'';"><i>Movie/TV News</i></a>
   <a id="nb15mm" href="/mymovies/list" onClick="(new Image()).src='\''/rg/nav-mymovies/navbar/images/b.gif?link=/mymovies/list'\'';"><i>My Movies</i></a>
   <a id="nb15dvd" href="/sections/dvd/" onClick="(new Image()).src='\''/rg/nav-video/navbar/images/b.gif?link=/sections/dvd/'\'';"><i>DVD New Releases</i></a>
   <a id="nb15imdbtv" href="/sections/tv/" onClick="(new Image()).src='\''/rg/nav-imdbtv/navbar/images/b.gif?link=/sections/tv/'\'';"><i>IMDbTV</i></a>
   <a id="nb15boards" href="/boards/" onClick="(new Image()).src='\''/rg/nav-boards/navbar/images/b.gif?link=/boards/'\'';"><i>Message Boards</i></a>
   <a id="nb15showtimes" href="/showtimes/" onClick="(new Image()).src='\''/rg/nav-showtimes/navbar/images/b.gif?link=/showtimes/'\'';"><i>Showtimes &amp; Tickets</i></a>
   <a id="nb15pro" href="http://pro.imdb.com/r/imdb-nav/" onClick="(new Image()).src='\''/rg/nav-pro/navbar/images/b.gif?link=http://pro.imdb.com/r/imdb-nav/'\'';"><i>IMDbPro</i></a>
   <a id="nb15resume" href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/nav-resume/navbar/images/b.gif?link=http://resume.imdb.com/'\'';"><i>IMDb Resume</i></a>
  </div>
 
  <div id="nb15topbg">
   <div id="nb15iesux">
    <div id="nb15personal">

     &nbsp;<span><a href="/register/login" onClick="(new Image()).src='\''/rg/sub-login/navbar/images/b.gif?link=/register/login'\'';">Login</a> | 
     <a href="/register/?why=personalize" onClick="(new Image()).src='\''/rg/sub-register/navbar/images/b.gif?link=/register/?why=personalize'\'';">Register</a></span>

    </div>
   </div>
  </div>
  <div id="nb15sub">
   <div>
   <a href="/" onClick="(new Image()).src='\''/rg/sub-home/navbar/images/b.gif?link=/'\'';">Home</a> |
   
    <a href="/chart/" onClick="(new Image()).src='\''/rg/sub-top/navbar/images/b.gif?link=/chart/'\'';">Top&nbsp;Movies</a> |
    <a href="/sections/gallery/" onClick="(new Image()).src='\''/rg/sub-gallery/navbar/images/b.gif?link=/sections/gallery/'\'';">Photos</a> |
    <a href="/indie/" onClick="(new Image()).src='\''/rg/sub-indie/navbar/images/b.gif?link=/indie/'\'';">Independent&nbsp;Film</a> |
    <a href="/sections/games/" onClick="(new Image()).src='\''/rg/sub-gamebase/navbar/images/b.gif?link=/sections/games/'\'';">GameBase</a> |
    <a href="/Browse/" onClick="(new Image()).src='\''/rg/sub-browse/navbar/images/b.gif?link=/Browse/'\'';">Browse</a> |
   
   <a href="/help/" onClick="(new Image()).src='\''/rg/sub-help/navbar/images/b.gif?link=/help/'\'';">Help</a>
   </div>
  </div>
  <div id="nb15search"> 
   <span class=search><a href="/search" onClick="(new Image()).src='\''/rg/search-img/navbar/images/b.gif?link=/search'\'';">search</a></span>
   <form method="get" action="/find" name="find">
    <select name="s">
     <option value="all" selected>All</option>
     <option value="tt">Titles</option>
     <option value="ep">TV Episodes</option>
     
      <option>My Movies</option>
     
     <option value="nm">Names</option>
     <option value="co">Companies</option>
     
      <option value="kw">Keywords</option>
      <option value="char">Characters</option>
      <option>Quotes</option>
      <option>Bios</option>
      <option>Plots</option>
    
    </select>
   <input name="q" size="28" value="">
    
    
    <input type="image"  id="nb15go_image"  src="http://i.media-imdb.com/images/intl/en/go.gif" alt="go" value="go" title="go">
    
    
    <span id="nb15searchlinks">
     <a href="/search" onClick="(new Image()).src='\''/rg/search-more/navbar/images/b.gif?link=/search'\'';">more</a> | 
     <a href="/help/show_leaf?searchtips" onClick="(new Image()).src='\''/rg/search-tips/navbar/images/b.gif?link=/help/show_leaf?searchtips'\'';">tips</a>
    </span>
   </form>
  </div>
 </div>
</div>
  

<div id="tn15" class="maindetails">

<div id="tn15shopbox" class="title uk">
<div class="left edge"></div><div class="right edge"></div>
<div class="label">SHOP <i>ATONEMENT</i></div>
<div class="logo"></div>
<div class="flags">
<script type="text/javascript">
<!--
function switchStore(co) {
  try { 
    var box = document.getElementById('\''tn15shopbox'\'');
    box.className = box.className.replace(/\b..\b$/, co); 
  } catch (e) { return true; }
  return false;
}
//-->
</script>
<a class="us" onclick="return switchStore('\''us'\'')" href="sales"><b>Amazon.com</b></a>
<a class="ca" onclick="return switchStore('\''ca'\'')" href="sales"><b>Amazon.ca</b></a>
<a class="uk" onclick="return switchStore('\''uk'\'')" href="sales"><b>Amazon.co.uk</b></a>
<a class="de" onclick="return switchStore('\''de'\'')" href="sales"><b>Amazon.de</b></a>
<a class="fr" onclick="return switchStore('\''fr'\'')" href="sales"><b>Amazon.fr</b></a>
</div>
<div class="stores">
<div class="us">
<a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047" title="Atonement DVD available at Amazon.com" class="dvd dvdon"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02057370000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.com for all '\''Atonement'\'' products" class="all allon"><b>All</b></a>
</div>
<div class="uk">
<a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.co.uk for all '\''Atonement'\'' products" class="all allon"><b>All</b></a>
</div>
<div class="ca"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.ca for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
<div class="de"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.de for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
<div class="fr"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.fr for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
</div>
</div>
<div id="tn15crumbs">
<a href="/">IMDb</a> &gt;
<b>Atonement (2007)</b>
</div>
<div id="tn15lhs">
  

<div class="photo">
<a name="poster" href="/media/rm2987758336/tt0783233" title="Atonement"><img border="0" alt="Atonement" title="Atonement" src="http://ia.media-imdb.com/images/M/MV5BMTM0ODc2Mzg1Nl5BMl5BanBnXkFtZTcwMTg4MDU1MQ@@._V1._SY140_SX100_.jpg" /></a>
</div>
  <a href="/mymovies/list?pending&amp;add=0783233" onClick="(new Image()).src='\''/rg/title-lhs/mymovies/images/b.gif?link=/mymovies/list?pending&amp;add=0783233'\'';">
  <img src="http://i.media-imdb.com/images//tn15/button_addtomymovies.gif" width="115" height="32" border="0" alt="[Add to My Movies]">
  </a>
<h6 style="margin-top: 4px">Quicklinks</h6><form><select id="quicklinks_select" onchange="document.location = this.options[this.selectedIndex].value">
<option value="maindetails" selected>main details</option><option value="combined">combined details</option><option value="fullcredits">full cast and crew</option><option value="companycredits">company credits</option><option value="usercomments">user comments</option><option value="externalreviews">external reviews</option><option value="newsgroupreviews">newsgroup reviews</option><option value="awards">awards</option><option value="ratings">user ratings</option><option value="parentalguide">parents guide</option><option value="recommendations">recommendations</option><option value="board">message board</option><option value="plotsummary">plot summary</option><option value="synopsis">plot synopsis</option><option value="keywords">plot keywords</option><option value="quotes">memorable quotes</option><option value="trivia">trivia</option><option value="goofs">goofs</option><option value="soundtrack">soundtrack listing</option><option value="movieconnections">movie connections</option><option value="faq">FAQ</option><option value="sales">merchandising links</option><option value="business">box office/business</option><option value="releaseinfo">release dates</option><option value="locations">filming locations</option><option value="technical">technical specs</option><option value="dvd">DVD details</option><option value="literature">literature listings</option><option value="news">news articles</option><option value="taglines">taglines</option><option value="trailers">trailers and videos</option><option value="posters">posters</option><option value="photogallery">photo gallery</option><option value="cinemashowtimes">showtimes</option><option value="officialsites">official sites</option><option value="miscsites">miscellaneous</option><option value="photosites">photographs</option><option value="soundsites">sound clips</option><option value="videosites">video clips</option>
</select></form>
<h6>Top Links</h6>
<a onClick="(new Image()).src='\''/rg/title-top-links/trailers/images/b.gif?link=/title/tt0783233/trailers'\'';" href="/title/tt0783233/trailers" class="link">trailers and videos</a><a onClick="(new Image()).src='\''/rg/title-top-links/fullcredits/images/b.gif?link=/title/tt0783233/fullcredits'\'';" href="/title/tt0783233/fullcredits" class="link">full cast and crew</a><a onClick="(new Image()).src='\''/rg/title-top-links/trivia/images/b.gif?link=/title/tt0783233/trivia'\'';" href="/title/tt0783233/trivia" class="link">trivia</a><a onClick="(new Image()).src='\''/rg/title-top-links/officialsites/images/b.gif?link=/title/tt0783233/officialsites'\'';" href="/title/tt0783233/officialsites" class="link">official sites</a><a onClick="(new Image()).src='\''/rg/title-top-links/quotes/images/b.gif?link=/title/tt0783233/quotes'\'';" href="/title/tt0783233/quotes" class="link">memorable quotes</a>
<h6>Overview</h6>
<a href="maindetails" class="link selected">main details</a><a href="combined" class="link">combined details</a><a href="fullcredits" class="link">full cast and crew</a><a href="companycredits" class="link">company credits</a><a href="tvschedule" class="link empty">tv schedule</a>
<h6>Awards &amp; Reviews</h6>
<a href="usercomments" class="link">user comments</a><a href="externalreviews" class="link">external reviews</a><a href="newsgroupreviews" class="link">newsgroup reviews</a><a href="awards" class="link">awards</a><a href="ratings" class="link">user ratings</a><a href="parentalguide" class="link">parents guide</a><a href="recommendations" class="link">recommendations</a><a href="board" class="link">message board</a>
<h6>Plot &amp; Quotes</h6>
<a href="plotsummary" class="link">plot summary</a><a href="synopsis" class="link">plot synopsis</a><a href="keywords" class="link">plot keywords</a><a href="amazon" class="link empty">Amazon.com summary</a><a href="quotes" class="link">memorable quotes</a>
<h6>Fun Stuff</h6>
<a href="trivia" class="link">trivia</a><a href="goofs" class="link">goofs</a><a href="soundtrack" class="link">soundtrack listing</a><a href="crazycredits" class="link empty">crazy credits</a><a href="alternateversions" class="link empty">alternate versions</a><a href="movieconnections" class="link">movie connections</a><a href="faq" class="link">FAQ</a>
<h6>Other Info</h6>
<a href="sales" class="link">merchandising links</a><a href="business" class="link">box office/business</a><a href="releaseinfo" class="link">release dates</a><a href="locations" class="link">filming locations</a><a href="technical" class="link">technical specs</a><a href="laserdisc" class="link empty">laserdisc details</a><a href="dvd" class="link">DVD details</a><a href="literature" class="link">literature listings</a><a href="news" class="link">news articles</a>
<h6>Promotional</h6>
<a href="taglines" class="link">taglines</a><a href="trailers" class="link">trailers and videos</a><a href="posters" class="link">posters</a><a href="photogallery" class="link">photo gallery</a>
<h6>External Links</h6>
<a href="cinemashowtimes" class="link">showtimes</a><a href="officialsites" class="link">official sites</a><a href="miscsites" class="link">miscellaneous</a><a href="photosites" class="link">photographs</a><a href="soundsites" class="link">sound clips</a><a href="videosites" class="link">video clips</a>  
</div>
<div id="tn15main">

<div id="tn15title">
<h1>Atonement <span>(<a href="/Sections/Years/2007">2007</a>)</span></h1>
</div>

<div id="tn15adrhs">
 <!-- sid : 35958 : TOP_RHS --><div id="lea_300x250"></div>   
advertisement
</div>

<div id="tn15content">

<div class="strip toplinks">
<table><tr>
<td>
<a href="/title/tt0783233/mediaindex" onClick="(new Image()).src='\''/rg/title-top/photos/images/b.gif?link=/title/tt0783233/mediaindex'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_photos.gif" width="16" height="22" alt="*" border="0">
<b>photos</b>
</a>
</td>
<td>
<a href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-top/boards/images/b.gif?link=/title/tt0783233/board'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_messageboard.gif" width="21" height="22" alt="*" border="0">
<b>board</b>
</a>
</td>
<td>
<a href="/title/tt0783233/trailers-me60827838" onClick="(new Image()).src='\''/rg/title-top/trailers/images/b.gif?link=/title/tt0783233/trailers-me60827838'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_trailer.gif" width="20" height="22" alt="*" border="0">
<b>trailer</b>
</a>
</td>
<td>
<a href="http://pro.imdb.com/title/tt0783233/" onClick="(new Image()).src='\''/rg/title-top/pro/images/b.gif?link=http://pro.imdb.com/title/tt0783233/'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_pro.gif" width="25" height="22" alt="*" border="0">
<b>details</b>
</a>
</td>
</tr></table>
</div>
 
 
 

<div id="tn15rating" class="two guest">
<div class="usr rating">

<a href="/register/?why=vote">Register</a> or <a href="/register/login">login</a> to rate this title

</div>
<div class="general rating">
<div class="starbar static"><div class="outer"><div class="inner" style="width: 158px"></div></div></div>
<b>User Rating:</b> 
<b>7.9/10</b> 
  <small>(<a href="ratings">37,863 votes</a>)</small>
<div class="bottom">

<a class="tn15more" href="ratings">more</a>

</div>

</div>

</div>
<script>
<!--
function tn15resize(timeout, chain) { 
  var timer;
  return function() { 
    window.clearTimeout(timer); 
    timer = window.setTimeout(function() { try { 
      var w;
      if (self.innerWidth) w = self.innerWidth;
      else if (document.documentElement && document.documentElement.clientWidth) w = document.documentElement.clientWidth;
      else if (document.body) w = document.body.clientWidth;
      document.getElementById('\''tn15content'\'').className = w < 950 ? '\''thin'\'' : '\''wide'\'';
    } catch (e) { } }, timeout);
    if (chain) chain();
  }
}
window.onload = tn15resize(1000, window.onload);
window.onresize = tn15resize(100, window.onresize);
(tn15resize(100))();
//-->
</script>

<style type="text/css">
.media_strip_thumbs {
  overflow: hidden;
  height: 90px;
}
.media_strip_thumbs img {
  margin-right: 0.2em;
}
</style>

<table style="border-collapse:collapse;">
<tr>

<td width="50%" class="media_strip_header">
<b>Photos</b>
<span>(<a href="/rg/photos-title/gallery-link/title/tt0783233/mediaindex">see all 50</a> | <a href="/rg/photos-title/slideshow-link/media/rm3527055360/tt0783233?slideshow=1">slideshow</a>)</span>
</td>

<td width="50%" class="media_strip_header">
<b>Videos</b>
</td>

</tr>
<tr>

<td>
<div class="media_strip_thumbs">
<a href="/rg/photos-title/summary/media/rm3527055360/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTUxMTYxMDYwMV5BMl5BanBnXkFtZTYwMjUyNzc4._V1._CR81,0,322,322_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3510278144/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTU1NDM1MjA1Nl5BMl5BanBnXkFtZTYwMzUyNzc4._V1._CR84,0,316,316_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3493500928/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTQ2ODQ1Mzk4MF5BMl5BanBnXkFtZTYwNDUyNzc4._V1._CR82,0,321,321_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3745159168/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTgwODMwNDE1Ml5BMl5BanBnXkFtZTYwNzIxMDM4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3728381952/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTMwNDQzNzU5Ml5BMl5BanBnXkFtZTYwODIxMDM4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3711604736/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTkyMTk4NTk3OF5BMl5BanBnXkFtZTYwNTUyNzc4._V1._CR82,0,320,320_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3694827520/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTQzNjc3NjcxOV5BMl5BanBnXkFtZTYwNjUyNzc4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3678050304/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMjA0ODE4MjU5OF5BMl5BanBnXkFtZTYwNzUyNzc4._V1._CR94,0,297,297_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3661273088/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTI2NzUwODUzM15BMl5BanBnXkFtZTYwODUyNzc4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3644495872/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTcwMjA1MjkxN15BMl5BanBnXkFtZTYwOTIxMDM4._V1._CR81,0,322,322_SS90_.jpg" border="0"></a>
</div>
</td>

<td>
<div class="media_strip_thumbs">
<a href="/rg/videos-title/summary//video/trailer/me60827838/"><img src="http://ia.media-imdb.com/images/M/MV5BMTM1MjUwMzgwMV5BMl5BanBnXkFtZTYwNDM3ODM4._V1._SY90_PIimdb-sprockets,BottomRight,0,0_SY90_.jpg" border="1"></a>
</div>
</td>

</tr>
</table>
  

<hr/>

<h3>Overview</h3>

<div class="info">
<h5>Director:</h5>
<a href="/name/nm0942504/">Joe Wright</a><br/>
</div>

<div class="info">
<h5>Writers:</h5>
<a href="/name/nm0568605/">Ian McEwan</a> (novel)<br/><a href="/name/nm0358960/">Christopher Hampton</a> (screenplay)<br/>
</div>

<div class="info">
<h5>Release Date:</h5> 
4 January 2008 (USA)
 <a class="tn15more inline" href="/title/tt0783233/releaseinfo" onClick="(new Image()).src='\''/rg/title-tease/releasedates/images/b.gif?link=/title/tt0783233/releaseinfo'\'';">more</a>

 <a style="margin-left: 1em" class="tn15more inline" href="/title/tt0783233/trailers-me60827838" onClick="(new Image()).src='\''/rg/title-tease/trailers/images/b.gif?link=/title/tt0783233/trailers-me60827838'\'';">view trailer</a>

</div>

<div class="info">
<h5>Genre:</h5>
<a href="/Sections/Genres/Drama/">Drama</a> / <a href="/Sections/Genres/Romance/">Romance</a> / <a href="/Sections/Genres/War/">War</a> <a class="tn15more inline" href="/title/tt0783233/keywords" onClick="(new Image()).src='\''/rg/title-tease/keywords/images/b.gif?link=/title/tt0783233/keywords'\'';">more</a>
</div>

<div class="info">
<h5>Tagline:</h5>
You can only imagine the truth. <a class="tn15more inline" href="/title/tt0783233/taglines" onClick="(new Image()).src='\''/rg/title-tease/taglines/images/b.gif?link=/title/tt0783233/taglines'\'';">more</a>
</div>

<div class="info">
<h5>Plot Outline:</h5> 
Fledgling writer Briony Tallis, as a 13-year-old, irrevocably changes the course of several lives when she accuses her older sister'\''s (Keira Knightley) lover (James McAvoy) of a crime he did not commit. Based on the British romance novel by Ian McEwan. <a class="tn15more inline" href="/title/tt0783233/plotsummary" onClick="(new Image()).src='\''/rg/title-tease/plotsummary/images/b.gif?link=/title/tt0783233/plotsummary'\'';">more</a>
</div>

<div class="info">
<h5>Plot Synopsis:</h5>
<a href="synopsis">View full synopsis. (warning! may contain spoilers)</a>
</div>

<div class="info">
<h5>Plot Keywords:</h5>

<a href="/keyword/profanity/">Profanity</a>
 / 
<a href="/keyword/manor/">Manor</a>
 / 
<a href="/keyword/long-take/">Long&#160;Take</a>
 / 
<a href="/keyword/underwater/">Underwater</a>
 / 
<a href="/keyword/dunkirk/">Dunkirk</a>

<a class="tn15more inline" href="/title/tt0783233/keywords" onClick="(new Image()).src='\''/rg/title-tease/keywords/images/b.gif?link=/title/tt0783233/keywords'\'';">more</a>

</div>

<div class="info">
<h5>Awards:</h5> 
Won Oscar.
 Another 20 wins
&amp;
60 nominations
<a class="tn15more inline" href="/title/tt0783233/awards" onClick="(new Image()).src='\''/rg/title-tease/awards/images/b.gif?link=/title/tt0783233/awards'\'';">more</a>
</div>

<div class="info">
<h5>User Comments:</h5>
A work of art...
<a class="tn15more inline" href="#comment">more</a>
</div>

<hr/>
<div class="headerinline"><h3>Cast</h3>&nbsp;<small style="position: relative; bottom: 1px">(Cast overview, first billed only)</small></div><div class="info"><table class="cast">  <tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1519680/">Saoirse Ronan</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027091/">Briony Tallis - Aged 13</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2854564/">Ailidh Mackay</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0053845/">Singing Housemaid</a></td></tr><tr class="odd"><td class="hs"><a href="/name/nm0000950/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0000950/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMjE5MjgwNDgyMV5BMl5BanBnXkFtZTcwNTgzNzQxMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0000950/">Brenda Blethyn</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027098/">Grace Turner</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0922169/">Julia West</a></td><td class="ddd"> ... </td><td class="char">Betty</td></tr><tr class="odd"><td class="hs"><a href="/name/nm0564215/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0564215/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMjA1NDI5NDA5NV5BMl5BanBnXkFtZTcwNjU0OTAzMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0564215/">James McAvoy</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027086/">Robbie Turner</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0910040/">Harriet Walter</a></td><td class="ddd"> ... </td><td class="char">Emily Tallis</td></tr><tr class="odd"><td class="hs"><a href="/name/nm0461136/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0461136/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMTg1NzUxOTE2MV5BMl5BanBnXkFtZTcwNTQzMDgyMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0461136/">Keira Knightley</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027082/">Cecilia Tallis</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1017334/">Juno Temple</a></td><td class="ddd"> ... </td><td class="char">Lola Quincey</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2328584/">Felix von Simson</a></td><td class="ddd"> ... </td><td class="char">Pierrot Quincey</td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2335109/">Charlie von Simson</a></td><td class="ddd"> ... </td><td class="char">Jackson Quincey</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0654295/">Alfie Allen</a></td><td class="ddd"> ... </td><td class="char">Danny Hardman</td></tr><tr class="even"><td class="hs"><a href="/name/nm1171145/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm1171145/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMTkwMzAzMzUwM15BMl5BanBnXkFtZTcwNzAwMDU2MQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm1171145/">Patrick Kennedy</a></td><td class="ddd"> ... </td><td class="char">Leon Tallis</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1212722/">Benedict Cumberbatch</a></td><td class="ddd"> ... </td><td class="char">Paul Marshall</td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0927835/">Peter Wight</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0061069/">Police Inspector</a></td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2852111/">Leander Deeny</a></td><td class="ddd"> ... </td><td class="char">Police Constable</td></tr></table><a class="tn15more" href="fullcredits#cast">more</a></div><div><form action="/character/create" method="post"><input type="hidden" name="title" value="tt0783233">Create a character page for: <select name="name" onchange="if (this.options[this.selectedIndex].value == '\''...'\'') document.location='\''fullcredits#cast'\''"><option>Betty</option><option>Emily Tallis</option><option>Lola Quincey</option><option>Pierrot Quincey</option><option>Jackson Quincey</option><option>Danny Hardman</option><option>Leon Tallis</option><option>Paul Marshall</option><option>Police Constable</option><option disabled="disabled">-----------</option><option value="...">more...</option></select> <input style="font: Tahoma, Verdana, sans-serif; font-size: 8pt; font-weight: bold; background-color: #eeeeee; border-color: #ccccee; color: black" type="submit" value="Create &raquo;"> <a target="_blank" href="/help/show_leaf?createchar"><img src="http://i.media-imdb.com/images/help13x10.gif" width="13" height="10" border="0" alt="?"></a></form></div>
<hr/>

<h3>Additional Details</h3>

<div class="info">
<h5>Also Known As:</h5>Reviens-moi (France)  <br>
  
  
<a class="tn15more" href="/title/tt0783233/releaseinfo#akas" onClick="(new Image()).src='\''/rg/title-tease/akas/images/b.gif?link=/title/tt0783233/releaseinfo#akas'\'';">more</a>

</div>

<div class="info">
<h5><a href="/mpaa">MPAA</a>:</h5> 
Rated R for disturbing war images, language and some sexuality.
</div>

<div class="info">
<h5>Parents Guide:</h5>
<a href="parentalguide">View content advisory for parents</a>
</div>

<div class="info">
<h5>Runtime:</h5>
130 min 
</div>

<div class="info">
<h5>Country:</h5>
<a href="/Sections/Countries/UK/">UK</a> / <a href="/Sections/Countries/France/">France</a>
</div>

<div class="info">
<h5>Language:</h5>
<a href="/Sections/Languages/English/">English</a> / <a href="/Sections/Languages/French/">French</a>
</div>

<div class="info">
<h5>Color:</h5>
<a href="/List?color-info=Color&&heading=13;Color">Color</a> 
</div>

<div class="info">
<h5>Aspect Ratio:</h5>
1.85 : 1 <a class="tn15more inline" href="/title/tt0783233/technical" onClick="(new Image()).src='\''/rg/title-tease/aspect/images/b.gif?link=/title/tt0783233/technical'\'';">more</a>
</div>

<div class="info">
<h5>Sound Mix:</h5>
<a href="/List?sound-mix=DTS&&heading=15;DTS">DTS</a>  / <a href="/List?sound-mix=Dolby%20Digital&&heading=15;Dolby%20Digital">Dolby Digital</a> 
</div>

<div class="info">
<h5>Certification:</h5>
<a href="/List?certificates=Ireland:15A&&heading=14;Ireland:15A">Ireland:15A</a>  / <a href="/List?certificates=Malaysia:U&&heading=14;Malaysia:U">Malaysia:U</a>  / <a href="/List?certificates=Brazil:14&&heading=14;Brazil:14">Brazil:14</a>  / <a href="/List?certificates=Taiwan:PG-12&&heading=14;Taiwan:PG-12">Taiwan:PG-12</a>  / <a href="/List?certificates=Argentina:16&&heading=14;Argentina:16">Argentina:16</a>  / <a href="/List?certificates=USA:R&&heading=14;USA:R">USA:R</a> <i>(certificate #43417)</i> / <a href="/List?certificates=Sweden:11&&heading=14;Sweden:11">Sweden:11</a>  / <a href="/List?certificates=Norway:11&&heading=14;Norway:11">Norway:11</a>  / <a href="/List?certificates=Switzerland:12&&heading=14;Switzerland:12">Switzerland:12</a> <i>(canton of Vaud)</i> / <a href="/List?certificates=Netherlands:12&&heading=14;Netherlands:12">Netherlands:12</a>  / <a href="/List?certificates=Switzerland:12&&heading=14;Switzerland:12">Switzerland:12</a> <i>(canton of Geneva)</i> / <a href="/List?certificates=Australia:MA&&heading=14;Australia:MA">Australia:MA</a>  / <a href="/List?certificates=Philippines:PG-13&&heading=14;Philippines:PG-13">Philippines:PG-13</a> <i>(MTRCB)</i> / <a href="/List?certificates=Canada:14A&&heading=14;Canada:14A">Canada:14A</a>  / <a href="/List?certificates=Japan:PG-12&&heading=14;Japan:PG-12">Japan:PG-12</a>  / <a href="/List?certificates=UK:15&&heading=14;UK:15">UK:15</a>  / <a href="/List?certificates=Finland:K-13&&heading=14;Finland:K-13">Finland:K-13</a>  / <a href="/List?certificates=Singapore:M18&&heading=14;Singapore:M18">Singapore:M18</a>  / <a href="/List?certificates=France:Unrated&&heading=14;France:Unrated">France:Unrated</a>  / <a href="/List?certificates=South%20Korea:15&&heading=14;South%20Korea:15">South Korea:15</a>  / <a href="/List?certificates=Portugal:M/12&&heading=14;Portugal:M/12">Portugal:M/12</a> <i>(Qualidade)</i> / <a href="/List?certificates=Germany:12&&heading=14;Germany:12">Germany:12</a> 
</div>

<div class="info">
<h5>Filming Locations:</h5> 

<a  href="/List?endings=on&&locations=Aldwych%20Underground%20Station,%20Aldwych,%20Holborn,%20London,%20England,%20UK&&heading=18;with+locations+including;Aldwych%20Underground%20Station,%20Aldwych,%20Holborn,%20London,%20England,%20UK">Aldwych Underground Station, Aldwych, Holborn, London, England, UK</a>

<a class="tn15more inline" href="/title/tt0783233/locations" onClick="(new Image()).src='\''/rg/title-tease/locations/images/b.gif?link=/title/tt0783233/locations'\'';">more</a>

</div>

<div class="info">
<h5>MOVIEmeter: <a href="/help/show_leaf?prowhatisstarmeter"><img src="http://i.media-imdb.com/images/tn15/meter_help.gif" width="12" height="12" border="0" alt="?"></a></h5>
<span class="meter">
<span class="down"><img src="http://i.media-imdb.com/images/tn15/meter_down.gif" width="9" height="8" alt="V" valign="middle"/> 27% </span>since last week
<a href="http://pro.imdb.com/title/tt0783233/graph-data" onClick="(new Image()).src='\''/rg/meter-tease/title/images/b.gif?link=http://pro.imdb.com/title/tt0783233/graph-data'\'';">why?</a>
</span>
</div>

<div class="info">
<h5>Company:</h5>
<a href="/company/co0057311/">Working Title Films</a>

<a class="tn15more inline" href="/title/tt0783233/companycredits">more</a>
</div>

<hr/> 

<h3>Fun Stuff</h3>

<div class="info">
<h5>Trivia:</h5>
The set of Dunkirk, built at Redcar, was the most expensive set, costing an estimated 1 million pounds.
<a class="tn15more inline" href="/title/tt0783233/trivia" onClick="(new Image()).src='\''/rg/title-tease/trivia/images/b.gif?link=/title/tt0783233/trivia'\'';">more</a>
</div>

<div class="info">
<h5>Goofs:</h5>
Continuity: During the library scene, Cecelia slips her shoe off while making love but when Briony interrupts, we see that both of her shoes are still on.
<a class="tn15more inline" href="/title/tt0783233/goofs" onClick="(new Image()).src='\''/rg/title-tease/goofs/images/b.gif?link=/title/tt0783233/goofs'\'';">more</a>
</div>

<div class="info">
<h5>Quotes:</h5>

<b><a href="/name/nm0461136/">Cecilia Tallis</a></b>:
Come back. Come back to me.
<a class="tn15more inline" href="/title/tt0783233/quotes" onClick="(new Image()).src='\''/rg/title-tease/quotes/images/b.gif?link=/title/tt0783233/quotes'\'';">more</a>
</div>

<div class="info">
<h5>Movie Connections:</h5> 
Featured in <a href="/title/tt1154617/">&#34;Siskel &#38; Ebert &#38; the Movies: (2007-12-08)&#34;</a> (2007)
<a class="tn15more inline" href="/title/tt0783233/movieconnections" onClick="(new Image()).src='\''/rg/title-tease/movieconnections/images/b.gif?link=/title/tt0783233/movieconnections'\'';">more</a>
</div>

<div class="info">
<h5>Soundtrack:</h5> 
(There'\''ll Be Bluebirds Over) The White Cliffs of Dover
<a class="tn15more inline" href="/title/tt0783233/soundtrack" onClick="(new Image()).src='\''/rg/title-tease/soundtrack/images/b.gif?link=/title/tt0783233/soundtrack'\'';">more</a>
</div>

<hr/>

<h3>FAQ</h3>

<a href="/title/tt0783233/faq#.2.1.3" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.3'\'';">Music in the Atonement trailer</a>
<br/>

<a href="/title/tt0783233/faq#.2.1.2" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.2'\'';">Was Robbie guilty of the rape of Lola?</a>
<br/>

<a href="/title/tt0783233/faq#.2.1.6" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.6'\'';">Is this based on a true story?</a>
<br/>

<a class="tn15more" href="/title/tt0783233/faq" onClick="(new Image()).src='\''/rg/title-tease/faq-more/images/b.gif?link=/title/tt0783233/faq'\'';">more</a>

<hr/>
<div class="headerinline">
<a name="comment"><h3>User Comments</h3></a>&nbsp;&nbsp;&nbsp;<a href="usercomments-enter"><span>(Comment on this title)</span></a>
</div>

<div class="comment">
<script type="text/javascript">
<!--
function yn(id, vote) {
  if (!document.getElementById || !document.createElement || !document.removeChild || !document.appendChild || !document.childNodes || !document.createTextNode) return true;
  var i = new Image();
  i.onload =  function() { ynd(id, 1) };
  i.onerror = function() { ynd(id, 0) };
  i.src = '\''usercomments-vote?yni_'\''+id+'\''='\''+vote;
  return false;
}
function ynd(id, status) {
  var d, s, t;
  if (!(d = document.getElementById('\''ynd_'\''+id))) return true;
  while (d.childNodes.length) d.removeChild(d.childNodes[0]);
  var s = document.createElement('\''span'\'');
  if (!status) s.setAttribute('\''class'\'', '\''error'\'');
  var t = document.createTextNode(status ? '\''Thank you, your vote will be counted and appear on this page within 24 hours.'\'' : '\''Sorry, there was a problem collecting your vote.'\'');
  s.appendChild(t);
  d.appendChild(s);
}
//-->
</script>

<div class="small">
17 out of 30 people found the following comment useful:-
</div>

<b>A work of art...</b>, 26 September 2007<br>
<img width="102" height="12" alt="10/10" src="http://i.media-imdb.com/images/showtimes/100.gif"><br>
<div class="small">
Author:
<a href="/user/ur8640608/comments">ChrisD1984</a> <small>from Canada</small>
</div>

</p>
<p>
Crafted in Britain by director Joe Wright, Atonement tells the story of
young author Briony Tallis who becomes jealous of her older sister&#39;s
illicit love affair with a servant. And with this, she finds a love
letter meant for Cecilia (her sister) written by the servant Robbie
Turner and misconstrues it as a letter written with sadistic-perverted
undertones when in reality it was a second draft that Robbie deemed to
silly to use. Briony assumes that Robbie is a nymphomaniac and it is
with this notion that she accuses Robbie with the rape of her younger
sister. Upon hearing this, the Tallis family has him arrested and he
ends up in World War II whilst Cecilia winds ups being a nurse. The
rest of the movie revolves around Robbie trying to find his way back to
Cecilia and also displays the cathartic process that Briony faces upon
reaching adolescence and realizing the life-changing mistakes that she
made. Atonement is sort of stuck in the middle in regards to whether it
renders primarily on emotion or story. It is based on an Ian McEwen
novel, so it does use some story elements in the latter segment of the
film, such as when the story falls into the &#39;war-romance&#39;-type
category. The first half however feels highly eastern-oriented with
well-placed shots around staircases and through windows that draw us
into the secret love affair that Cecilia and Robbie have undertaken.
The first part of the movie feels almost like a different film
altogether. It feels quite artsy in spots and a lot of shots do not
help to push the story forward. Having only seen two of Wright&#39;s films
(Pride and Prejudice being the other) it&#39;s hard to lump his style into
being specifically east or west. Pride and Prejudice had a lot of
eastern elements in its use of detailed steady cam shots that follow
its main characters around the sprawling English countryside. Atonement
also has this, with an amazing 10-minute long steady cam shot that
follows Robbie on a beach through the after effects of war. The shot is
so magnificent that you forget about the lack of cutting and you start
to feel as if you can taste the acrid flavor of rusted steel on a
battleship or the stolid stench of soldiers&#39; breath and spent bombs.
The shot is very well choreographed as well as we see literally
hundreds of extras that weave in and out of frame, each doing their own
duty. Joe Wright uses background action nicely to tell different
stories of different people without even giving them lines. Just watch
the steady shot as it follows Robbie past a somber-looking band play a
waltz or as he shoves into another soldier; a very well executed shot
indeed. This shot does have an eastern-feel to it as it does not push
the story forward but focuses on allowing the audience to see through
the eyes of the main character. Editor Paul Tohill does a great job as
well; his editing is never too fast paced but doesn&#39;t lag behind
either. When he splices, he makes sure that we have enough time to
fully incorporate ourselves within the basis of a shot. Again, his lack
of editing in the steady camera scene helps to reinforce this. This can
also be seen by assessing the scene that takes place near the end when
Briony has come back to apologize to Cecilia and Robbie. His edits are
now quick and slightly robust and help move the story along as we feel
and see the tension-filled apartment room. The medium shot of Robbie
when he almost decks Briony is tremendously powerful.
</p>

<div class="yn" id="ynd_1736819">
<form method="get" action="/register/">
<input type="hidden" name="why" value="comment_vote">Was the above comment useful to you?
<input class="click" type="image"  value="yes" src="http://i.media-imdb.com/images/tn15/btn_yes.gif" width="34" height="19">
<input class="click" type="image"  value="no" src="http://i.media-imdb.com/images/tn15/btn_no.gif" width="34" height="19">

</form>
</div>

</div>

<a class="tn15more" href="/title/tt0783233/usercomments" onClick="(new Image()).src='\''/rg/title-tease/comments-bottom/images/b.gif?link=/title/tt0783233/usercomments'\'';">more</a>

<hr/>
<h3>Message Boards</h3>
Discuss this title with other users on <a href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-tease/boards-top/images/b.gif?link=/title/tt0783233/board'\'';">IMDb message board for Atonement (2007)</a>

<table class="boards">
<tr><th class="left">Recent Posts (updated daily)</th><th class="right">User</th></tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/100232145">The chinese burns  on Lola</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur10853560/boards/profile">kehindebamgboye</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101850429">More contrivances and misunderstandings than a season of Three'\''s Company</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur6456707/boards/profile">slop101</a></td>
</tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101769005">Needs to be seen at least twice</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur13076570/boards/profile">scoochie9</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101894197">angry, angry, angry</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur10215948/boards/profile">smj274</a></td>
</tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/95026725">Different nationalities, different tastes?</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur15051762/boards/profile">wirelessaxis</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101974304">Wright'\''s DVD director commentary</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur9394104/boards/profile">nshifley</a></td>
</tr>

</table>
<a class="tn15more" href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-tease/boards-bottom/images/b.gif?link=/title/tt0783233/board'\'';">more</a>

<hr/>

<h3>Recommendations</h3>
<div class="strip">
If you enjoyed this title, our database also recommends:
<table class="recs">
<tr class="poster">

<td><a href="/title/tt0332280/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/60/95/28m.jpg"></a></td>

<td><a href="/title/tt0175880/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/27/36/14/10m.jpg"></a></td>

<td><a href="/title/tt0301390/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/95/65/28m.jpg"></a></td>

<td><a href="/title/tt0319524/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/99/65/28m.jpg"></a></td>

<td><a href="/title/tt0213149/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/68/97/95m.jpg"></a></td>

</tr>
<tr>

<td><a href="/title/tt0332280/">The Notebook</a></td>

<td><a href="/title/tt0175880/">Magnolia</a></td>

<td><a href="/title/tt0301390/">The Heart of Me</a></td>

<td><a href="/title/tt0319524/">How to Deal</a></td>

<td><a href="/title/tt0213149/">Pearl Harbor</a></td>

</tr>
<tr class="rating">

<td class="first">
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 80px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 80px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 63px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 53px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 53px"></div></div>
</td>

</tr>
</table>
<a href="/AddRecommendation?const=0783233">Add a recommendation</a> |
<a href="/title/tt0783233/recommendations" onClick="(new Image()).src='\''/rg/title-tease/recommendations/images/b.gif?link=/title/tt0783233/recommendations'\'';">Show more recommendations</a>
</div>
<h3>Related Links</h3><table>
<tr><td width="33%" style="width: 400px"> <a href="/title/tt0783233/fullcredits" onClick="(new Image()).src='\''/rg/title-related/maindetails-fullcredits/images/b.gif?link=/title/tt0783233/fullcredits'\'';">Full cast and crew</a></td><td width="33%" style="width: 400px"> <a href="/title/tt0783233/companycredits" onClick="(new Image()).src='\''/rg/title-related/maindetails-companycredits/images/b.gif?link=/title/tt0783233/companycredits'\'';">Company credits</a></td><td width="33%" style="width: 400px"> <a href="/title/tt0783233/externalreviews" onClick="(new Image()).src='\''/rg/title-related/maindetails-externalreviews/images/b.gif?link=/title/tt0783233/externalreviews'\'';">External reviews</a></td></tr><tr><td width="33%" style="width: 400px"> <a href="/title/tt0783233/news" onClick="(new Image()).src='\''/rg/title-related/maindetails-news/images/b.gif?link=/title/tt0783233/news'\'';">News articles</a></td><td width="33%" style="width: 400px"> <a href="/Sections/Genres/Drama/" onClick="(new Image()).src='\''/rg/title-related/maindetails-genre/images/b.gif?link=/Sections/Genres/Drama/'\'';">IMDb Drama section</a></td><td width="33%" style="width: 400px"> <a href="/Sections/Countries/UK/" onClick="(new Image()).src='\''/rg/title-related/maindetails-country/images/b.gif?link=/Sections/Countries/UK/'\'';">IMDb UK section</a></td></tr><tr><td width="33%" style="width: 400px"> <a href="/mymovies/list?pending&amp;add=0783233" onClick="(new Image()).src='\''/rg/title-related/maindetails-mymovies/images/b.gif?link=/mymovies/list?pending&amp;add=0783233'\'';">Add this title to MyMovies</a></td>
</table>
<div id="tn15bot">
 <div class="right">
   <!-- sid : 46422 : GOOGLE --><div style="text-align:center">
<iframe name="GoogleAd" src="http://i.imdb.com/images/3pads/google/google-afc.html?channel=t-channel" align="top" scrolling="no" width="500" height="240" frameborder="0" marginheight="0" marginwidth="0" align="middle"></iframe>
</div>
 
 </div>
 <div class="left">
  <p><form method="post" action="/updates"><input type="hidden" name="auto" value="legacy/title/tt0783233/"><input type="image" width="67" height="21" name="Update" src="http://i.media-imdb.com/images/tn15/update.gif" border="0" alt="Update"></p><p><i>You may report errors and omissions on this page to the IMDb database managers. They will be examined and if approved will be included in a future update. Clicking the '\''Update'\'' button  will take you through a step-by-step process.</i></p></form>

 </div>
 <br clear="right"/>
</div>

</div>
</div> 
</div> 
<br clear="both" />

<div id="footer" class="ft">
<hr width="100%" size=1>
<p class="footer" align="center">
<a href="/">Home</a>&nbsp;
  | <a href="/search">Search</A>&nbsp;
  | <a href="/NowPlaying/">Now Playing</a>&nbsp;
  | <a href="/News/">News</A>&nbsp;
  | <a href="/register/?why=mymovies_footer">My Movies</A>&nbsp;
  | <a href="/Games/">Games</A>&nbsp;
  | <a href="/boards/">Boards</A>&nbsp;
| <a href="/help/">Help</a>&nbsp;
  | <A HREF="/Showtimes">US&nbsp;Movie&nbsp;Showtimes</A>&nbsp;
| <A HREF="/top_250_films">Top 250</A>&nbsp;
| <a href="/register/?why=footer">Register</a>&nbsp;
  | <A HREF="/recommends/">Recommendations</A>&nbsp;
  | <A HREF="/widgets/">Widgets</A><br>
  <A HREF="/Charts/">Box&nbsp;Office</A> 
  | <A HREF="/a2z">Index</A> 
  | <A HREF="/Sections/Trailers/">Trailers</A> 
  
  | <a href="/jobs"><b>Jobs</b></a>&nbsp;
  | <a href="https://secure.imdb.com/register/subscribe?c=a394d4442664f6f6475627" onClick="(new Image()).src='\''/rg/PRO_FOOT/FOOTER/images/b.gif?link=https://secure.imdb.com/register/subscribe?c=a394d4442664f6f6475627'\'';">
    <span style="color:#cc3333"><b>IMDbPro.com&nbsp;-&nbsp;Free&nbsp;Trial</b></span></a> 
  | <a href="http://resume.imdb.com" onClick="(new Image()).src='\''/rg/resume-footer/footer/images/b.gif?link=http://resume.imdb.com'\'';"><span style="color:#cc3333"><b>IMDb Resume</b></span></a>
<br><br>
<a href="/help/show_article?conditions">Copyright &copy;</a> 1990-2008 
<a href="/help/">IMDb.com, Inc.</a><br>
<a href="/help/show_article?conditions">Terms</a> and <a href="/privacy">Privacy Policy</a> under which this service is provided to you.<br>
An <a href="http://www.amazon.com/exec/obidos/redirect-home/internetmoviedat">
<img align="middle" width="86" height="18" border="0" src="http://i.imdb.com/amazon_logo.gif" alt="Amazon.com"></a> company.&nbsp;
<a href="/advertising/">Advertise</a> on IMDb.&nbsp;
<a href="/tiger_redirect?FT_LIC&/Licensing/">License</a> our content.
</p>
<p class="footer" align="center">IMDb is powered by Perl and <b><a href="/rg/jobs/footer-pbp/help/show_leaf?jobatimdb">we are hiring</a></b>!</p>
</div>

</layer>
</div>
 <!-- sid : 78101 : BOTTOM_BANNER -->
<div align="center">
<script language="JavaScript">
var rnd = Math.round(Math.random()*10000000);
document.writeln('\''<iframe src="http://uac.advertising.com/wrapper/aceUAC.htm#Site=705838&Size=728090&bnum='\''+rnd+'\''" scrolling="no" width="728" height="090" frameborder="0" marginheight="0" marginwidth="0" title="Advertisement"></iframe>'\'');
</script>
</div>
 
  
 <!-- sid : 55807 : BOTTOM_SCRIPT -->  <script type="text/javascript">
  function lycos_census ()
  {
     _rsCI='\''lycos-ie'\'';
     _rsCG='\''0'\'';
     _rsDT=1;
     _rsSI=escape(window.location);
     var _rsLP=location.protocol.indexOf('\''https'\'')>-1?'\''https:'\'':'\''http:'\'';
     _rsRP=escape(document.referrer);
     _rsND=_rsLP+'\''//secure-uk.imrworldwide.com/'\'';

     if (parseInt(navigator.appVersion)>=4) {
	 _rsRD=(new Date()).getTime();
	 _rsSE=0;
	 _rsSV='\'''\'';
	 _rsSM=0;
	 _rsCL='\''<scr'\''+'\''ipt language="JavaScript" type="text/javascript" src="'\''+_rsND+'\''v5.js"><\/scr'\''+'\''ipt>'\'';
     } else {
	 _rsCL='\''<img src="'\''+_rsND+'\''cgi-bin/m?ci='\''+_rsCI+'\''&cg='\''+_rsCG+'\''&si='\''+_rsSI+'\''&rp='\''+_rsRP+'\''">'\'';
     }
     document.write(_rsCL);
     document.write('\''<noscript><img src="//secure-uk.imrworldwide.com/cgi-bin/m?ci=lycos-ie&amp;cg=0" alt=""></noscript>'\'');
}

    var alldiv = document.body.getElementsByTagName('\''div'\'');
    var call_lycos = 0;
    for (i=0;i<alldiv.length;i++) {
       if (alldiv[i].id.indexOf('\''lea_'\'') == 0) { call_lycos = 1; break;}
    }
    if (call_lycos == 1) {
      document.write('\''<scr'\''+'\''ipt src="http://fe.lea.lycos.co.uk/ats/adfunction.js"></scr'\''+'\''ipt>'\'')
    }
  </script>
  <script type="text/javascript">
    if (call_lycos == 1) {
      var refurl = document.URL;
      //var other = "ee=0";
      var other = "ee=0|ly12=Drama|ly12=Romance|ly12=War";
      lea_getter(refurl,other,"ie");
      lycos_census();
    }
  </script>
 
<img src="/rd/?q=50403000000030a090f29616f226e276966600000010c6a0622303038303430323c23353935383c25353830373c24363432323c27383130313c233539383830000001037a040379646370000001047&cb=120716318116503" width="1" height="1" alt="" border="0">
</div> <!-- id="wrapper" -->
</body>
</html>'
++ grep -n -i '<div class="photo">'
++ cut -d: -f1
++ echo '
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<title>Atonement (2007)</title>
<meta name="title" content="Atonement (2007)">
<meta name="description" content="Directed by Joe Wright.  With Saoirse Ronan, Ailidh Mackay, Brenda Blethyn. Fledgling writer Briony Tallis, as a 13-year-old, irrevocably changes the course of several lives when she accuses her older sister'\''s (Keira Knightley) lover (James McAvoy) of a crime he did not commit. Based on the British romance novel by Ian McEwan. Visit IMDb for Photos, Showtimes, Cast, Crew, Reviews, Plot Summary, Comments, Discussions, Taglines, Trailers, Posters, Fan Sites">

<meta name="keywords" content="Reviews, Showtimes, DVDs, Photos, Message Boards, User Ratings, Synopsis, Trailers, Credits">
<link rel="stylesheet" type="text/css" media="screen" href="http://i.media-imdb.com/images/SF01c175f07a3ed070f8f38d7f98c6ca3f/css2/consumersite.css" />
<link rel="icon" href="http://i.imdb.com/favicon.ico" />
<link rel="apple-touch-icon" href="http://i.media-imdb.com/apple-touch-icon.png" />
<style type="text/css">.showtimes { font-family: Arial, Helvetica, sans-serif }.showtimes .heading { font-size: 16px; font-weight: bold }.showtimes .time { color: #ff0000 }.tabular { border-collapse: collapse; border: 1px solid #9999ff }.tabular td.heading { background: #bbbbff }.tabular td.heading-right { background: #bbbbff; text-align: right; font-size: small }.tabular td.address { font-size: small; color: #666666; background: #eeeeee }.tabular td.detail { font-size: small; background: #eeeeee }.tabular tr.alternate { background: #eeeeee }.tabular td.item { border: 1px solid #9999ff }</style><link rel="stylesheet" type="text/css" href="http://i.media-imdb.com/images/SFae751da69684847117d205d2cbc0ae90/tn15/tn15.css" />

</head>
<!-- h=iop113 i=2008-04-01 s=legacy(default) t='\''Wed Apr  2 12:06:21 2008'\'' -->

<body bgcolor="#ffffff" text="#000000">
<div id="wrapper">
  
  

   <!-- sid : 35988 : TOP_BANNER --><div id="lea_728x90" style="height:90;" align="center"></div> 

<div id="root">
<layer name="root">

<div id="nb15">

  <div id="nb15home">
   <a href="/" onClick="(new Image()).src='\''/rg/nav-home/navbar/images/b.gif?link=/'\'';"><img src="http://i.media-imdb.com/images/nb15/logo2.gif" alt="Home" 
   title="The Internet Movie Database" border="0" width="177" height="78"></a>
  </div>
 <div id="nb15botbg">
 
  <div id="nb15tabs">
   <a id="nb15nowplaying" href="/nowplaying/" onClick="(new Image()).src='\''/rg/nav-nowplaying/navbar/images/b.gif?link=/nowplaying/'\'';"><i>Now Playing</i></a>
   <a id="nb15news" href="/news/" onClick="(new Image()).src='\''/rg/nav-news/navbar/images/b.gif?link=/news/'\'';"><i>Movie/TV News</i></a>
   <a id="nb15mm" href="/mymovies/list" onClick="(new Image()).src='\''/rg/nav-mymovies/navbar/images/b.gif?link=/mymovies/list'\'';"><i>My Movies</i></a>
   <a id="nb15dvd" href="/sections/dvd/" onClick="(new Image()).src='\''/rg/nav-video/navbar/images/b.gif?link=/sections/dvd/'\'';"><i>DVD New Releases</i></a>
   <a id="nb15imdbtv" href="/sections/tv/" onClick="(new Image()).src='\''/rg/nav-imdbtv/navbar/images/b.gif?link=/sections/tv/'\'';"><i>IMDbTV</i></a>
   <a id="nb15boards" href="/boards/" onClick="(new Image()).src='\''/rg/nav-boards/navbar/images/b.gif?link=/boards/'\'';"><i>Message Boards</i></a>
   <a id="nb15showtimes" href="/showtimes/" onClick="(new Image()).src='\''/rg/nav-showtimes/navbar/images/b.gif?link=/showtimes/'\'';"><i>Showtimes &amp; Tickets</i></a>
   <a id="nb15pro" href="http://pro.imdb.com/r/imdb-nav/" onClick="(new Image()).src='\''/rg/nav-pro/navbar/images/b.gif?link=http://pro.imdb.com/r/imdb-nav/'\'';"><i>IMDbPro</i></a>
   <a id="nb15resume" href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/nav-resume/navbar/images/b.gif?link=http://resume.imdb.com/'\'';"><i>IMDb Resume</i></a>
  </div>
 
  <div id="nb15topbg">
   <div id="nb15iesux">
    <div id="nb15personal">

     &nbsp;<span><a href="/register/login" onClick="(new Image()).src='\''/rg/sub-login/navbar/images/b.gif?link=/register/login'\'';">Login</a> | 
     <a href="/register/?why=personalize" onClick="(new Image()).src='\''/rg/sub-register/navbar/images/b.gif?link=/register/?why=personalize'\'';">Register</a></span>

    </div>
   </div>
  </div>
  <div id="nb15sub">
   <div>
   <a href="/" onClick="(new Image()).src='\''/rg/sub-home/navbar/images/b.gif?link=/'\'';">Home</a> |
   
    <a href="/chart/" onClick="(new Image()).src='\''/rg/sub-top/navbar/images/b.gif?link=/chart/'\'';">Top&nbsp;Movies</a> |
    <a href="/sections/gallery/" onClick="(new Image()).src='\''/rg/sub-gallery/navbar/images/b.gif?link=/sections/gallery/'\'';">Photos</a> |
    <a href="/indie/" onClick="(new Image()).src='\''/rg/sub-indie/navbar/images/b.gif?link=/indie/'\'';">Independent&nbsp;Film</a> |
    <a href="/sections/games/" onClick="(new Image()).src='\''/rg/sub-gamebase/navbar/images/b.gif?link=/sections/games/'\'';">GameBase</a> |
    <a href="/Browse/" onClick="(new Image()).src='\''/rg/sub-browse/navbar/images/b.gif?link=/Browse/'\'';">Browse</a> |
   
   <a href="/help/" onClick="(new Image()).src='\''/rg/sub-help/navbar/images/b.gif?link=/help/'\'';">Help</a>
   </div>
  </div>
  <div id="nb15search"> 
   <span class=search><a href="/search" onClick="(new Image()).src='\''/rg/search-img/navbar/images/b.gif?link=/search'\'';">search</a></span>
   <form method="get" action="/find" name="find">
    <select name="s">
     <option value="all" selected>All</option>
     <option value="tt">Titles</option>
     <option value="ep">TV Episodes</option>
     
      <option>My Movies</option>
     
     <option value="nm">Names</option>
     <option value="co">Companies</option>
     
      <option value="kw">Keywords</option>
      <option value="char">Characters</option>
      <option>Quotes</option>
      <option>Bios</option>
      <option>Plots</option>
    
    </select>
   <input name="q" size="28" value="">
    
    
    <input type="image"  id="nb15go_image"  src="http://i.media-imdb.com/images/intl/en/go.gif" alt="go" value="go" title="go">
    
    
    <span id="nb15searchlinks">
     <a href="/search" onClick="(new Image()).src='\''/rg/search-more/navbar/images/b.gif?link=/search'\'';">more</a> | 
     <a href="/help/show_leaf?searchtips" onClick="(new Image()).src='\''/rg/search-tips/navbar/images/b.gif?link=/help/show_leaf?searchtips'\'';">tips</a>
    </span>
   </form>
  </div>
 </div>
</div>
  

<div id="tn15" class="maindetails">

<div id="tn15shopbox" class="title uk">
<div class="left edge"></div><div class="right edge"></div>
<div class="label">SHOP <i>ATONEMENT</i></div>
<div class="logo"></div>
<div class="flags">
<script type="text/javascript">
<!--
function switchStore(co) {
  try { 
    var box = document.getElementById('\''tn15shopbox'\'');
    box.className = box.className.replace(/\b..\b$/, co); 
  } catch (e) { return true; }
  return false;
}
//-->
</script>
<a class="us" onclick="return switchStore('\''us'\'')" href="sales"><b>Amazon.com</b></a>
<a class="ca" onclick="return switchStore('\''ca'\'')" href="sales"><b>Amazon.ca</b></a>
<a class="uk" onclick="return switchStore('\''uk'\'')" href="sales"><b>Amazon.co.uk</b></a>
<a class="de" onclick="return switchStore('\''de'\'')" href="sales"><b>Amazon.de</b></a>
<a class="fr" onclick="return switchStore('\''fr'\'')" href="sales"><b>Amazon.fr</b></a>
</div>
<div class="stores">
<div class="us">
<a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047" title="Atonement DVD available at Amazon.com" class="dvd dvdon"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02057370000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.com for all '\''Atonement'\'' products" class="all allon"><b>All</b></a>
</div>
<div class="uk">
<a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.co.uk for all '\''Atonement'\'' products" class="all allon"><b>All</b></a>
</div>
<div class="ca"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.ca for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
<div class="de"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.de for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
<div class="fr"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.fr for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
</div>
</div>
<div id="tn15crumbs">
<a href="/">IMDb</a> &gt;
<b>Atonement (2007)</b>
</div>
<div id="tn15lhs">
  

<div class="photo">
<a name="poster" href="/media/rm2987758336/tt0783233" title="Atonement"><img border="0" alt="Atonement" title="Atonement" src="http://ia.media-imdb.com/images/M/MV5BMTM0ODc2Mzg1Nl5BMl5BanBnXkFtZTcwMTg4MDU1MQ@@._V1._SY140_SX100_.jpg" /></a>
</div>
  <a href="/mymovies/list?pending&amp;add=0783233" onClick="(new Image()).src='\''/rg/title-lhs/mymovies/images/b.gif?link=/mymovies/list?pending&amp;add=0783233'\'';">
  <img src="http://i.media-imdb.com/images//tn15/button_addtomymovies.gif" width="115" height="32" border="0" alt="[Add to My Movies]">
  </a>
<h6 style="margin-top: 4px">Quicklinks</h6><form><select id="quicklinks_select" onchange="document.location = this.options[this.selectedIndex].value">
<option value="maindetails" selected>main details</option><option value="combined">combined details</option><option value="fullcredits">full cast and crew</option><option value="companycredits">company credits</option><option value="usercomments">user comments</option><option value="externalreviews">external reviews</option><option value="newsgroupreviews">newsgroup reviews</option><option value="awards">awards</option><option value="ratings">user ratings</option><option value="parentalguide">parents guide</option><option value="recommendations">recommendations</option><option value="board">message board</option><option value="plotsummary">plot summary</option><option value="synopsis">plot synopsis</option><option value="keywords">plot keywords</option><option value="quotes">memorable quotes</option><option value="trivia">trivia</option><option value="goofs">goofs</option><option value="soundtrack">soundtrack listing</option><option value="movieconnections">movie connections</option><option value="faq">FAQ</option><option value="sales">merchandising links</option><option value="business">box office/business</option><option value="releaseinfo">release dates</option><option value="locations">filming locations</option><option value="technical">technical specs</option><option value="dvd">DVD details</option><option value="literature">literature listings</option><option value="news">news articles</option><option value="taglines">taglines</option><option value="trailers">trailers and videos</option><option value="posters">posters</option><option value="photogallery">photo gallery</option><option value="cinemashowtimes">showtimes</option><option value="officialsites">official sites</option><option value="miscsites">miscellaneous</option><option value="photosites">photographs</option><option value="soundsites">sound clips</option><option value="videosites">video clips</option>
</select></form>
<h6>Top Links</h6>
<a onClick="(new Image()).src='\''/rg/title-top-links/trailers/images/b.gif?link=/title/tt0783233/trailers'\'';" href="/title/tt0783233/trailers" class="link">trailers and videos</a><a onClick="(new Image()).src='\''/rg/title-top-links/fullcredits/images/b.gif?link=/title/tt0783233/fullcredits'\'';" href="/title/tt0783233/fullcredits" class="link">full cast and crew</a><a onClick="(new Image()).src='\''/rg/title-top-links/trivia/images/b.gif?link=/title/tt0783233/trivia'\'';" href="/title/tt0783233/trivia" class="link">trivia</a><a onClick="(new Image()).src='\''/rg/title-top-links/officialsites/images/b.gif?link=/title/tt0783233/officialsites'\'';" href="/title/tt0783233/officialsites" class="link">official sites</a><a onClick="(new Image()).src='\''/rg/title-top-links/quotes/images/b.gif?link=/title/tt0783233/quotes'\'';" href="/title/tt0783233/quotes" class="link">memorable quotes</a>
<h6>Overview</h6>
<a href="maindetails" class="link selected">main details</a><a href="combined" class="link">combined details</a><a href="fullcredits" class="link">full cast and crew</a><a href="companycredits" class="link">company credits</a><a href="tvschedule" class="link empty">tv schedule</a>
<h6>Awards &amp; Reviews</h6>
<a href="usercomments" class="link">user comments</a><a href="externalreviews" class="link">external reviews</a><a href="newsgroupreviews" class="link">newsgroup reviews</a><a href="awards" class="link">awards</a><a href="ratings" class="link">user ratings</a><a href="parentalguide" class="link">parents guide</a><a href="recommendations" class="link">recommendations</a><a href="board" class="link">message board</a>
<h6>Plot &amp; Quotes</h6>
<a href="plotsummary" class="link">plot summary</a><a href="synopsis" class="link">plot synopsis</a><a href="keywords" class="link">plot keywords</a><a href="amazon" class="link empty">Amazon.com summary</a><a href="quotes" class="link">memorable quotes</a>
<h6>Fun Stuff</h6>
<a href="trivia" class="link">trivia</a><a href="goofs" class="link">goofs</a><a href="soundtrack" class="link">soundtrack listing</a><a href="crazycredits" class="link empty">crazy credits</a><a href="alternateversions" class="link empty">alternate versions</a><a href="movieconnections" class="link">movie connections</a><a href="faq" class="link">FAQ</a>
<h6>Other Info</h6>
<a href="sales" class="link">merchandising links</a><a href="business" class="link">box office/business</a><a href="releaseinfo" class="link">release dates</a><a href="locations" class="link">filming locations</a><a href="technical" class="link">technical specs</a><a href="laserdisc" class="link empty">laserdisc details</a><a href="dvd" class="link">DVD details</a><a href="literature" class="link">literature listings</a><a href="news" class="link">news articles</a>
<h6>Promotional</h6>
<a href="taglines" class="link">taglines</a><a href="trailers" class="link">trailers and videos</a><a href="posters" class="link">posters</a><a href="photogallery" class="link">photo gallery</a>
<h6>External Links</h6>
<a href="cinemashowtimes" class="link">showtimes</a><a href="officialsites" class="link">official sites</a><a href="miscsites" class="link">miscellaneous</a><a href="photosites" class="link">photographs</a><a href="soundsites" class="link">sound clips</a><a href="videosites" class="link">video clips</a>  
</div>
<div id="tn15main">

<div id="tn15title">
<h1>Atonement <span>(<a href="/Sections/Years/2007">2007</a>)</span></h1>
</div>

<div id="tn15adrhs">
 <!-- sid : 35958 : TOP_RHS --><div id="lea_300x250"></div>   
advertisement
</div>

<div id="tn15content">

<div class="strip toplinks">
<table><tr>
<td>
<a href="/title/tt0783233/mediaindex" onClick="(new Image()).src='\''/rg/title-top/photos/images/b.gif?link=/title/tt0783233/mediaindex'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_photos.gif" width="16" height="22" alt="*" border="0">
<b>photos</b>
</a>
</td>
<td>
<a href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-top/boards/images/b.gif?link=/title/tt0783233/board'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_messageboard.gif" width="21" height="22" alt="*" border="0">
<b>board</b>
</a>
</td>
<td>
<a href="/title/tt0783233/trailers-me60827838" onClick="(new Image()).src='\''/rg/title-top/trailers/images/b.gif?link=/title/tt0783233/trailers-me60827838'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_trailer.gif" width="20" height="22" alt="*" border="0">
<b>trailer</b>
</a>
</td>
<td>
<a href="http://pro.imdb.com/title/tt0783233/" onClick="(new Image()).src='\''/rg/title-top/pro/images/b.gif?link=http://pro.imdb.com/title/tt0783233/'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_pro.gif" width="25" height="22" alt="*" border="0">
<b>details</b>
</a>
</td>
</tr></table>
</div>
 
 
 

<div id="tn15rating" class="two guest">
<div class="usr rating">

<a href="/register/?why=vote">Register</a> or <a href="/register/login">login</a> to rate this title

</div>
<div class="general rating">
<div class="starbar static"><div class="outer"><div class="inner" style="width: 158px"></div></div></div>
<b>User Rating:</b> 
<b>7.9/10</b> 
  <small>(<a href="ratings">37,863 votes</a>)</small>
<div class="bottom">

<a class="tn15more" href="ratings">more</a>

</div>

</div>

</div>
<script>
<!--
function tn15resize(timeout, chain) { 
  var timer;
  return function() { 
    window.clearTimeout(timer); 
    timer = window.setTimeout(function() { try { 
      var w;
      if (self.innerWidth) w = self.innerWidth;
      else if (document.documentElement && document.documentElement.clientWidth) w = document.documentElement.clientWidth;
      else if (document.body) w = document.body.clientWidth;
      document.getElementById('\''tn15content'\'').className = w < 950 ? '\''thin'\'' : '\''wide'\'';
    } catch (e) { } }, timeout);
    if (chain) chain();
  }
}
window.onload = tn15resize(1000, window.onload);
window.onresize = tn15resize(100, window.onresize);
(tn15resize(100))();
//-->
</script>

<style type="text/css">
.media_strip_thumbs {
  overflow: hidden;
  height: 90px;
}
.media_strip_thumbs img {
  margin-right: 0.2em;
}
</style>

<table style="border-collapse:collapse;">
<tr>

<td width="50%" class="media_strip_header">
<b>Photos</b>
<span>(<a href="/rg/photos-title/gallery-link/title/tt0783233/mediaindex">see all 50</a> | <a href="/rg/photos-title/slideshow-link/media/rm3527055360/tt0783233?slideshow=1">slideshow</a>)</span>
</td>

<td width="50%" class="media_strip_header">
<b>Videos</b>
</td>

</tr>
<tr>

<td>
<div class="media_strip_thumbs">
<a href="/rg/photos-title/summary/media/rm3527055360/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTUxMTYxMDYwMV5BMl5BanBnXkFtZTYwMjUyNzc4._V1._CR81,0,322,322_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3510278144/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTU1NDM1MjA1Nl5BMl5BanBnXkFtZTYwMzUyNzc4._V1._CR84,0,316,316_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3493500928/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTQ2ODQ1Mzk4MF5BMl5BanBnXkFtZTYwNDUyNzc4._V1._CR82,0,321,321_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3745159168/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTgwODMwNDE1Ml5BMl5BanBnXkFtZTYwNzIxMDM4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3728381952/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTMwNDQzNzU5Ml5BMl5BanBnXkFtZTYwODIxMDM4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3711604736/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTkyMTk4NTk3OF5BMl5BanBnXkFtZTYwNTUyNzc4._V1._CR82,0,320,320_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3694827520/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTQzNjc3NjcxOV5BMl5BanBnXkFtZTYwNjUyNzc4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3678050304/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMjA0ODE4MjU5OF5BMl5BanBnXkFtZTYwNzUyNzc4._V1._CR94,0,297,297_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3661273088/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTI2NzUwODUzM15BMl5BanBnXkFtZTYwODUyNzc4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3644495872/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTcwMjA1MjkxN15BMl5BanBnXkFtZTYwOTIxMDM4._V1._CR81,0,322,322_SS90_.jpg" border="0"></a>
</div>
</td>

<td>
<div class="media_strip_thumbs">
<a href="/rg/videos-title/summary//video/trailer/me60827838/"><img src="http://ia.media-imdb.com/images/M/MV5BMTM1MjUwMzgwMV5BMl5BanBnXkFtZTYwNDM3ODM4._V1._SY90_PIimdb-sprockets,BottomRight,0,0_SY90_.jpg" border="1"></a>
</div>
</td>

</tr>
</table>
  

<hr/>

<h3>Overview</h3>

<div class="info">
<h5>Director:</h5>
<a href="/name/nm0942504/">Joe Wright</a><br/>
</div>

<div class="info">
<h5>Writers:</h5>
<a href="/name/nm0568605/">Ian McEwan</a> (novel)<br/><a href="/name/nm0358960/">Christopher Hampton</a> (screenplay)<br/>
</div>

<div class="info">
<h5>Release Date:</h5> 
4 January 2008 (USA)
 <a class="tn15more inline" href="/title/tt0783233/releaseinfo" onClick="(new Image()).src='\''/rg/title-tease/releasedates/images/b.gif?link=/title/tt0783233/releaseinfo'\'';">more</a>

 <a style="margin-left: 1em" class="tn15more inline" href="/title/tt0783233/trailers-me60827838" onClick="(new Image()).src='\''/rg/title-tease/trailers/images/b.gif?link=/title/tt0783233/trailers-me60827838'\'';">view trailer</a>

</div>

<div class="info">
<h5>Genre:</h5>
<a href="/Sections/Genres/Drama/">Drama</a> / <a href="/Sections/Genres/Romance/">Romance</a> / <a href="/Sections/Genres/War/">War</a> <a class="tn15more inline" href="/title/tt0783233/keywords" onClick="(new Image()).src='\''/rg/title-tease/keywords/images/b.gif?link=/title/tt0783233/keywords'\'';">more</a>
</div>

<div class="info">
<h5>Tagline:</h5>
You can only imagine the truth. <a class="tn15more inline" href="/title/tt0783233/taglines" onClick="(new Image()).src='\''/rg/title-tease/taglines/images/b.gif?link=/title/tt0783233/taglines'\'';">more</a>
</div>

<div class="info">
<h5>Plot Outline:</h5> 
Fledgling writer Briony Tallis, as a 13-year-old, irrevocably changes the course of several lives when she accuses her older sister'\''s (Keira Knightley) lover (James McAvoy) of a crime he did not commit. Based on the British romance novel by Ian McEwan. <a class="tn15more inline" href="/title/tt0783233/plotsummary" onClick="(new Image()).src='\''/rg/title-tease/plotsummary/images/b.gif?link=/title/tt0783233/plotsummary'\'';">more</a>
</div>

<div class="info">
<h5>Plot Synopsis:</h5>
<a href="synopsis">View full synopsis. (warning! may contain spoilers)</a>
</div>

<div class="info">
<h5>Plot Keywords:</h5>

<a href="/keyword/profanity/">Profanity</a>
 / 
<a href="/keyword/manor/">Manor</a>
 / 
<a href="/keyword/long-take/">Long&#160;Take</a>
 / 
<a href="/keyword/underwater/">Underwater</a>
 / 
<a href="/keyword/dunkirk/">Dunkirk</a>

<a class="tn15more inline" href="/title/tt0783233/keywords" onClick="(new Image()).src='\''/rg/title-tease/keywords/images/b.gif?link=/title/tt0783233/keywords'\'';">more</a>

</div>

<div class="info">
<h5>Awards:</h5> 
Won Oscar.
 Another 20 wins
&amp;
60 nominations
<a class="tn15more inline" href="/title/tt0783233/awards" onClick="(new Image()).src='\''/rg/title-tease/awards/images/b.gif?link=/title/tt0783233/awards'\'';">more</a>
</div>

<div class="info">
<h5>User Comments:</h5>
A work of art...
<a class="tn15more inline" href="#comment">more</a>
</div>

<hr/>
<div class="headerinline"><h3>Cast</h3>&nbsp;<small style="position: relative; bottom: 1px">(Cast overview, first billed only)</small></div><div class="info"><table class="cast">  <tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1519680/">Saoirse Ronan</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027091/">Briony Tallis - Aged 13</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2854564/">Ailidh Mackay</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0053845/">Singing Housemaid</a></td></tr><tr class="odd"><td class="hs"><a href="/name/nm0000950/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0000950/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMjE5MjgwNDgyMV5BMl5BanBnXkFtZTcwNTgzNzQxMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0000950/">Brenda Blethyn</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027098/">Grace Turner</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0922169/">Julia West</a></td><td class="ddd"> ... </td><td class="char">Betty</td></tr><tr class="odd"><td class="hs"><a href="/name/nm0564215/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0564215/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMjA1NDI5NDA5NV5BMl5BanBnXkFtZTcwNjU0OTAzMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0564215/">James McAvoy</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027086/">Robbie Turner</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0910040/">Harriet Walter</a></td><td class="ddd"> ... </td><td class="char">Emily Tallis</td></tr><tr class="odd"><td class="hs"><a href="/name/nm0461136/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0461136/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMTg1NzUxOTE2MV5BMl5BanBnXkFtZTcwNTQzMDgyMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0461136/">Keira Knightley</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027082/">Cecilia Tallis</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1017334/">Juno Temple</a></td><td class="ddd"> ... </td><td class="char">Lola Quincey</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2328584/">Felix von Simson</a></td><td class="ddd"> ... </td><td class="char">Pierrot Quincey</td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2335109/">Charlie von Simson</a></td><td class="ddd"> ... </td><td class="char">Jackson Quincey</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0654295/">Alfie Allen</a></td><td class="ddd"> ... </td><td class="char">Danny Hardman</td></tr><tr class="even"><td class="hs"><a href="/name/nm1171145/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm1171145/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMTkwMzAzMzUwM15BMl5BanBnXkFtZTcwNzAwMDU2MQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm1171145/">Patrick Kennedy</a></td><td class="ddd"> ... </td><td class="char">Leon Tallis</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1212722/">Benedict Cumberbatch</a></td><td class="ddd"> ... </td><td class="char">Paul Marshall</td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0927835/">Peter Wight</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0061069/">Police Inspector</a></td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2852111/">Leander Deeny</a></td><td class="ddd"> ... </td><td class="char">Police Constable</td></tr></table><a class="tn15more" href="fullcredits#cast">more</a></div><div><form action="/character/create" method="post"><input type="hidden" name="title" value="tt0783233">Create a character page for: <select name="name" onchange="if (this.options[this.selectedIndex].value == '\''...'\'') document.location='\''fullcredits#cast'\''"><option>Betty</option><option>Emily Tallis</option><option>Lola Quincey</option><option>Pierrot Quincey</option><option>Jackson Quincey</option><option>Danny Hardman</option><option>Leon Tallis</option><option>Paul Marshall</option><option>Police Constable</option><option disabled="disabled">-----------</option><option value="...">more...</option></select> <input style="font: Tahoma, Verdana, sans-serif; font-size: 8pt; font-weight: bold; background-color: #eeeeee; border-color: #ccccee; color: black" type="submit" value="Create &raquo;"> <a target="_blank" href="/help/show_leaf?createchar"><img src="http://i.media-imdb.com/images/help13x10.gif" width="13" height="10" border="0" alt="?"></a></form></div>
<hr/>

<h3>Additional Details</h3>

<div class="info">
<h5>Also Known As:</h5>Reviens-moi (France)  <br>
  
  
<a class="tn15more" href="/title/tt0783233/releaseinfo#akas" onClick="(new Image()).src='\''/rg/title-tease/akas/images/b.gif?link=/title/tt0783233/releaseinfo#akas'\'';">more</a>

</div>

<div class="info">
<h5><a href="/mpaa">MPAA</a>:</h5> 
Rated R for disturbing war images, language and some sexuality.
</div>

<div class="info">
<h5>Parents Guide:</h5>
<a href="parentalguide">View content advisory for parents</a>
</div>

<div class="info">
<h5>Runtime:</h5>
130 min 
</div>

<div class="info">
<h5>Country:</h5>
<a href="/Sections/Countries/UK/">UK</a> / <a href="/Sections/Countries/France/">France</a>
</div>

<div class="info">
<h5>Language:</h5>
<a href="/Sections/Languages/English/">English</a> / <a href="/Sections/Languages/French/">French</a>
</div>

<div class="info">
<h5>Color:</h5>
<a href="/List?color-info=Color&&heading=13;Color">Color</a> 
</div>

<div class="info">
<h5>Aspect Ratio:</h5>
1.85 : 1 <a class="tn15more inline" href="/title/tt0783233/technical" onClick="(new Image()).src='\''/rg/title-tease/aspect/images/b.gif?link=/title/tt0783233/technical'\'';">more</a>
</div>

<div class="info">
<h5>Sound Mix:</h5>
<a href="/List?sound-mix=DTS&&heading=15;DTS">DTS</a>  / <a href="/List?sound-mix=Dolby%20Digital&&heading=15;Dolby%20Digital">Dolby Digital</a> 
</div>

<div class="info">
<h5>Certification:</h5>
<a href="/List?certificates=Ireland:15A&&heading=14;Ireland:15A">Ireland:15A</a>  / <a href="/List?certificates=Malaysia:U&&heading=14;Malaysia:U">Malaysia:U</a>  / <a href="/List?certificates=Brazil:14&&heading=14;Brazil:14">Brazil:14</a>  / <a href="/List?certificates=Taiwan:PG-12&&heading=14;Taiwan:PG-12">Taiwan:PG-12</a>  / <a href="/List?certificates=Argentina:16&&heading=14;Argentina:16">Argentina:16</a>  / <a href="/List?certificates=USA:R&&heading=14;USA:R">USA:R</a> <i>(certificate #43417)</i> / <a href="/List?certificates=Sweden:11&&heading=14;Sweden:11">Sweden:11</a>  / <a href="/List?certificates=Norway:11&&heading=14;Norway:11">Norway:11</a>  / <a href="/List?certificates=Switzerland:12&&heading=14;Switzerland:12">Switzerland:12</a> <i>(canton of Vaud)</i> / <a href="/List?certificates=Netherlands:12&&heading=14;Netherlands:12">Netherlands:12</a>  / <a href="/List?certificates=Switzerland:12&&heading=14;Switzerland:12">Switzerland:12</a> <i>(canton of Geneva)</i> / <a href="/List?certificates=Australia:MA&&heading=14;Australia:MA">Australia:MA</a>  / <a href="/List?certificates=Philippines:PG-13&&heading=14;Philippines:PG-13">Philippines:PG-13</a> <i>(MTRCB)</i> / <a href="/List?certificates=Canada:14A&&heading=14;Canada:14A">Canada:14A</a>  / <a href="/List?certificates=Japan:PG-12&&heading=14;Japan:PG-12">Japan:PG-12</a>  / <a href="/List?certificates=UK:15&&heading=14;UK:15">UK:15</a>  / <a href="/List?certificates=Finland:K-13&&heading=14;Finland:K-13">Finland:K-13</a>  / <a href="/List?certificates=Singapore:M18&&heading=14;Singapore:M18">Singapore:M18</a>  / <a href="/List?certificates=France:Unrated&&heading=14;France:Unrated">France:Unrated</a>  / <a href="/List?certificates=South%20Korea:15&&heading=14;South%20Korea:15">South Korea:15</a>  / <a href="/List?certificates=Portugal:M/12&&heading=14;Portugal:M/12">Portugal:M/12</a> <i>(Qualidade)</i> / <a href="/List?certificates=Germany:12&&heading=14;Germany:12">Germany:12</a> 
</div>

<div class="info">
<h5>Filming Locations:</h5> 

<a  href="/List?endings=on&&locations=Aldwych%20Underground%20Station,%20Aldwych,%20Holborn,%20London,%20England,%20UK&&heading=18;with+locations+including;Aldwych%20Underground%20Station,%20Aldwych,%20Holborn,%20London,%20England,%20UK">Aldwych Underground Station, Aldwych, Holborn, London, England, UK</a>

<a class="tn15more inline" href="/title/tt0783233/locations" onClick="(new Image()).src='\''/rg/title-tease/locations/images/b.gif?link=/title/tt0783233/locations'\'';">more</a>

</div>

<div class="info">
<h5>MOVIEmeter: <a href="/help/show_leaf?prowhatisstarmeter"><img src="http://i.media-imdb.com/images/tn15/meter_help.gif" width="12" height="12" border="0" alt="?"></a></h5>
<span class="meter">
<span class="down"><img src="http://i.media-imdb.com/images/tn15/meter_down.gif" width="9" height="8" alt="V" valign="middle"/> 27% </span>since last week
<a href="http://pro.imdb.com/title/tt0783233/graph-data" onClick="(new Image()).src='\''/rg/meter-tease/title/images/b.gif?link=http://pro.imdb.com/title/tt0783233/graph-data'\'';">why?</a>
</span>
</div>

<div class="info">
<h5>Company:</h5>
<a href="/company/co0057311/">Working Title Films</a>

<a class="tn15more inline" href="/title/tt0783233/companycredits">more</a>
</div>

<hr/> 

<h3>Fun Stuff</h3>

<div class="info">
<h5>Trivia:</h5>
The set of Dunkirk, built at Redcar, was the most expensive set, costing an estimated 1 million pounds.
<a class="tn15more inline" href="/title/tt0783233/trivia" onClick="(new Image()).src='\''/rg/title-tease/trivia/images/b.gif?link=/title/tt0783233/trivia'\'';">more</a>
</div>

<div class="info">
<h5>Goofs:</h5>
Continuity: During the library scene, Cecelia slips her shoe off while making love but when Briony interrupts, we see that both of her shoes are still on.
<a class="tn15more inline" href="/title/tt0783233/goofs" onClick="(new Image()).src='\''/rg/title-tease/goofs/images/b.gif?link=/title/tt0783233/goofs'\'';">more</a>
</div>

<div class="info">
<h5>Quotes:</h5>

<b><a href="/name/nm0461136/">Cecilia Tallis</a></b>:
Come back. Come back to me.
<a class="tn15more inline" href="/title/tt0783233/quotes" onClick="(new Image()).src='\''/rg/title-tease/quotes/images/b.gif?link=/title/tt0783233/quotes'\'';">more</a>
</div>

<div class="info">
<h5>Movie Connections:</h5> 
Featured in <a href="/title/tt1154617/">&#34;Siskel &#38; Ebert &#38; the Movies: (2007-12-08)&#34;</a> (2007)
<a class="tn15more inline" href="/title/tt0783233/movieconnections" onClick="(new Image()).src='\''/rg/title-tease/movieconnections/images/b.gif?link=/title/tt0783233/movieconnections'\'';">more</a>
</div>

<div class="info">
<h5>Soundtrack:</h5> 
(There'\''ll Be Bluebirds Over) The White Cliffs of Dover
<a class="tn15more inline" href="/title/tt0783233/soundtrack" onClick="(new Image()).src='\''/rg/title-tease/soundtrack/images/b.gif?link=/title/tt0783233/soundtrack'\'';">more</a>
</div>

<hr/>

<h3>FAQ</h3>

<a href="/title/tt0783233/faq#.2.1.3" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.3'\'';">Music in the Atonement trailer</a>
<br/>

<a href="/title/tt0783233/faq#.2.1.2" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.2'\'';">Was Robbie guilty of the rape of Lola?</a>
<br/>

<a href="/title/tt0783233/faq#.2.1.6" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.6'\'';">Is this based on a true story?</a>
<br/>

<a class="tn15more" href="/title/tt0783233/faq" onClick="(new Image()).src='\''/rg/title-tease/faq-more/images/b.gif?link=/title/tt0783233/faq'\'';">more</a>

<hr/>
<div class="headerinline">
<a name="comment"><h3>User Comments</h3></a>&nbsp;&nbsp;&nbsp;<a href="usercomments-enter"><span>(Comment on this title)</span></a>
</div>

<div class="comment">
<script type="text/javascript">
<!--
function yn(id, vote) {
  if (!document.getElementById || !document.createElement || !document.removeChild || !document.appendChild || !document.childNodes || !document.createTextNode) return true;
  var i = new Image();
  i.onload =  function() { ynd(id, 1) };
  i.onerror = function() { ynd(id, 0) };
  i.src = '\''usercomments-vote?yni_'\''+id+'\''='\''+vote;
  return false;
}
function ynd(id, status) {
  var d, s, t;
  if (!(d = document.getElementById('\''ynd_'\''+id))) return true;
  while (d.childNodes.length) d.removeChild(d.childNodes[0]);
  var s = document.createElement('\''span'\'');
  if (!status) s.setAttribute('\''class'\'', '\''error'\'');
  var t = document.createTextNode(status ? '\''Thank you, your vote will be counted and appear on this page within 24 hours.'\'' : '\''Sorry, there was a problem collecting your vote.'\'');
  s.appendChild(t);
  d.appendChild(s);
}
//-->
</script>

<div class="small">
17 out of 30 people found the following comment useful:-
</div>

<b>A work of art...</b>, 26 September 2007<br>
<img width="102" height="12" alt="10/10" src="http://i.media-imdb.com/images/showtimes/100.gif"><br>
<div class="small">
Author:
<a href="/user/ur8640608/comments">ChrisD1984</a> <small>from Canada</small>
</div>

</p>
<p>
Crafted in Britain by director Joe Wright, Atonement tells the story of
young author Briony Tallis who becomes jealous of her older sister&#39;s
illicit love affair with a servant. And with this, she finds a love
letter meant for Cecilia (her sister) written by the servant Robbie
Turner and misconstrues it as a letter written with sadistic-perverted
undertones when in reality it was a second draft that Robbie deemed to
silly to use. Briony assumes that Robbie is a nymphomaniac and it is
with this notion that she accuses Robbie with the rape of her younger
sister. Upon hearing this, the Tallis family has him arrested and he
ends up in World War II whilst Cecilia winds ups being a nurse. The
rest of the movie revolves around Robbie trying to find his way back to
Cecilia and also displays the cathartic process that Briony faces upon
reaching adolescence and realizing the life-changing mistakes that she
made. Atonement is sort of stuck in the middle in regards to whether it
renders primarily on emotion or story. It is based on an Ian McEwen
novel, so it does use some story elements in the latter segment of the
film, such as when the story falls into the &#39;war-romance&#39;-type
category. The first half however feels highly eastern-oriented with
well-placed shots around staircases and through windows that draw us
into the secret love affair that Cecilia and Robbie have undertaken.
The first part of the movie feels almost like a different film
altogether. It feels quite artsy in spots and a lot of shots do not
help to push the story forward. Having only seen two of Wright&#39;s films
(Pride and Prejudice being the other) it&#39;s hard to lump his style into
being specifically east or west. Pride and Prejudice had a lot of
eastern elements in its use of detailed steady cam shots that follow
its main characters around the sprawling English countryside. Atonement
also has this, with an amazing 10-minute long steady cam shot that
follows Robbie on a beach through the after effects of war. The shot is
so magnificent that you forget about the lack of cutting and you start
to feel as if you can taste the acrid flavor of rusted steel on a
battleship or the stolid stench of soldiers&#39; breath and spent bombs.
The shot is very well choreographed as well as we see literally
hundreds of extras that weave in and out of frame, each doing their own
duty. Joe Wright uses background action nicely to tell different
stories of different people without even giving them lines. Just watch
the steady shot as it follows Robbie past a somber-looking band play a
waltz or as he shoves into another soldier; a very well executed shot
indeed. This shot does have an eastern-feel to it as it does not push
the story forward but focuses on allowing the audience to see through
the eyes of the main character. Editor Paul Tohill does a great job as
well; his editing is never too fast paced but doesn&#39;t lag behind
either. When he splices, he makes sure that we have enough time to
fully incorporate ourselves within the basis of a shot. Again, his lack
of editing in the steady camera scene helps to reinforce this. This can
also be seen by assessing the scene that takes place near the end when
Briony has come back to apologize to Cecilia and Robbie. His edits are
now quick and slightly robust and help move the story along as we feel
and see the tension-filled apartment room. The medium shot of Robbie
when he almost decks Briony is tremendously powerful.
</p>

<div class="yn" id="ynd_1736819">
<form method="get" action="/register/">
<input type="hidden" name="why" value="comment_vote">Was the above comment useful to you?
<input class="click" type="image"  value="yes" src="http://i.media-imdb.com/images/tn15/btn_yes.gif" width="34" height="19">
<input class="click" type="image"  value="no" src="http://i.media-imdb.com/images/tn15/btn_no.gif" width="34" height="19">

</form>
</div>

</div>

<a class="tn15more" href="/title/tt0783233/usercomments" onClick="(new Image()).src='\''/rg/title-tease/comments-bottom/images/b.gif?link=/title/tt0783233/usercomments'\'';">more</a>

<hr/>
<h3>Message Boards</h3>
Discuss this title with other users on <a href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-tease/boards-top/images/b.gif?link=/title/tt0783233/board'\'';">IMDb message board for Atonement (2007)</a>

<table class="boards">
<tr><th class="left">Recent Posts (updated daily)</th><th class="right">User</th></tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/100232145">The chinese burns  on Lola</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur10853560/boards/profile">kehindebamgboye</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101850429">More contrivances and misunderstandings than a season of Three'\''s Company</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur6456707/boards/profile">slop101</a></td>
</tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101769005">Needs to be seen at least twice</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur13076570/boards/profile">scoochie9</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101894197">angry, angry, angry</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur10215948/boards/profile">smj274</a></td>
</tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/95026725">Different nationalities, different tastes?</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur15051762/boards/profile">wirelessaxis</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101974304">Wright'\''s DVD director commentary</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur9394104/boards/profile">nshifley</a></td>
</tr>

</table>
<a class="tn15more" href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-tease/boards-bottom/images/b.gif?link=/title/tt0783233/board'\'';">more</a>

<hr/>

<h3>Recommendations</h3>
<div class="strip">
If you enjoyed this title, our database also recommends:
<table class="recs">
<tr class="poster">

<td><a href="/title/tt0332280/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/60/95/28m.jpg"></a></td>

<td><a href="/title/tt0175880/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/27/36/14/10m.jpg"></a></td>

<td><a href="/title/tt0301390/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/95/65/28m.jpg"></a></td>

<td><a href="/title/tt0319524/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/99/65/28m.jpg"></a></td>

<td><a href="/title/tt0213149/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/68/97/95m.jpg"></a></td>

</tr>
<tr>

<td><a href="/title/tt0332280/">The Notebook</a></td>

<td><a href="/title/tt0175880/">Magnolia</a></td>

<td><a href="/title/tt0301390/">The Heart of Me</a></td>

<td><a href="/title/tt0319524/">How to Deal</a></td>

<td><a href="/title/tt0213149/">Pearl Harbor</a></td>

</tr>
<tr class="rating">

<td class="first">
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 80px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 80px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 63px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 53px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 53px"></div></div>
</td>

</tr>
</table>
<a href="/AddRecommendation?const=0783233">Add a recommendation</a> |
<a href="/title/tt0783233/recommendations" onClick="(new Image()).src='\''/rg/title-tease/recommendations/images/b.gif?link=/title/tt0783233/recommendations'\'';">Show more recommendations</a>
</div>
<h3>Related Links</h3><table>
<tr><td width="33%" style="width: 400px"> <a href="/title/tt0783233/fullcredits" onClick="(new Image()).src='\''/rg/title-related/maindetails-fullcredits/images/b.gif?link=/title/tt0783233/fullcredits'\'';">Full cast and crew</a></td><td width="33%" style="width: 400px"> <a href="/title/tt0783233/companycredits" onClick="(new Image()).src='\''/rg/title-related/maindetails-companycredits/images/b.gif?link=/title/tt0783233/companycredits'\'';">Company credits</a></td><td width="33%" style="width: 400px"> <a href="/title/tt0783233/externalreviews" onClick="(new Image()).src='\''/rg/title-related/maindetails-externalreviews/images/b.gif?link=/title/tt0783233/externalreviews'\'';">External reviews</a></td></tr><tr><td width="33%" style="width: 400px"> <a href="/title/tt0783233/news" onClick="(new Image()).src='\''/rg/title-related/maindetails-news/images/b.gif?link=/title/tt0783233/news'\'';">News articles</a></td><td width="33%" style="width: 400px"> <a href="/Sections/Genres/Drama/" onClick="(new Image()).src='\''/rg/title-related/maindetails-genre/images/b.gif?link=/Sections/Genres/Drama/'\'';">IMDb Drama section</a></td><td width="33%" style="width: 400px"> <a href="/Sections/Countries/UK/" onClick="(new Image()).src='\''/rg/title-related/maindetails-country/images/b.gif?link=/Sections/Countries/UK/'\'';">IMDb UK section</a></td></tr><tr><td width="33%" style="width: 400px"> <a href="/mymovies/list?pending&amp;add=0783233" onClick="(new Image()).src='\''/rg/title-related/maindetails-mymovies/images/b.gif?link=/mymovies/list?pending&amp;add=0783233'\'';">Add this title to MyMovies</a></td>
</table>
<div id="tn15bot">
 <div class="right">
   <!-- sid : 46422 : GOOGLE --><div style="text-align:center">
<iframe name="GoogleAd" src="http://i.imdb.com/images/3pads/google/google-afc.html?channel=t-channel" align="top" scrolling="no" width="500" height="240" frameborder="0" marginheight="0" marginwidth="0" align="middle"></iframe>
</div>
 
 </div>
 <div class="left">
  <p><form method="post" action="/updates"><input type="hidden" name="auto" value="legacy/title/tt0783233/"><input type="image" width="67" height="21" name="Update" src="http://i.media-imdb.com/images/tn15/update.gif" border="0" alt="Update"></p><p><i>You may report errors and omissions on this page to the IMDb database managers. They will be examined and if approved will be included in a future update. Clicking the '\''Update'\'' button  will take you through a step-by-step process.</i></p></form>

 </div>
 <br clear="right"/>
</div>

</div>
</div> 
</div> 
<br clear="both" />

<div id="footer" class="ft">
<hr width="100%" size=1>
<p class="footer" align="center">
<a href="/">Home</a>&nbsp;
  | <a href="/search">Search</A>&nbsp;
  | <a href="/NowPlaying/">Now Playing</a>&nbsp;
  | <a href="/News/">News</A>&nbsp;
  | <a href="/register/?why=mymovies_footer">My Movies</A>&nbsp;
  | <a href="/Games/">Games</A>&nbsp;
  | <a href="/boards/">Boards</A>&nbsp;
| <a href="/help/">Help</a>&nbsp;
  | <A HREF="/Showtimes">US&nbsp;Movie&nbsp;Showtimes</A>&nbsp;
| <A HREF="/top_250_films">Top 250</A>&nbsp;
| <a href="/register/?why=footer">Register</a>&nbsp;
  | <A HREF="/recommends/">Recommendations</A>&nbsp;
  | <A HREF="/widgets/">Widgets</A><br>
  <A HREF="/Charts/">Box&nbsp;Office</A> 
  | <A HREF="/a2z">Index</A> 
  | <A HREF="/Sections/Trailers/">Trailers</A> 
  
  | <a href="/jobs"><b>Jobs</b></a>&nbsp;
  | <a href="https://secure.imdb.com/register/subscribe?c=a394d4442664f6f6475627" onClick="(new Image()).src='\''/rg/PRO_FOOT/FOOTER/images/b.gif?link=https://secure.imdb.com/register/subscribe?c=a394d4442664f6f6475627'\'';">
    <span style="color:#cc3333"><b>IMDbPro.com&nbsp;-&nbsp;Free&nbsp;Trial</b></span></a> 
  | <a href="http://resume.imdb.com" onClick="(new Image()).src='\''/rg/resume-footer/footer/images/b.gif?link=http://resume.imdb.com'\'';"><span style="color:#cc3333"><b>IMDb Resume</b></span></a>
<br><br>
<a href="/help/show_article?conditions">Copyright &copy;</a> 1990-2008 
<a href="/help/">IMDb.com, Inc.</a><br>
<a href="/help/show_article?conditions">Terms</a> and <a href="/privacy">Privacy Policy</a> under which this service is provided to you.<br>
An <a href="http://www.amazon.com/exec/obidos/redirect-home/internetmoviedat">
<img align="middle" width="86" height="18" border="0" src="http://i.imdb.com/amazon_logo.gif" alt="Amazon.com"></a> company.&nbsp;
<a href="/advertising/">Advertise</a> on IMDb.&nbsp;
<a href="/tiger_redirect?FT_LIC&/Licensing/">License</a> our content.
</p>
<p class="footer" align="center">IMDb is powered by Perl and <b><a href="/rg/jobs/footer-pbp/help/show_leaf?jobatimdb">we are hiring</a></b>!</p>
</div>

</layer>
</div>
 <!-- sid : 78101 : BOTTOM_BANNER -->
<div align="center">
<script language="JavaScript">
var rnd = Math.round(Math.random()*10000000);
document.writeln('\''<iframe src="http://uac.advertising.com/wrapper/aceUAC.htm#Site=705838&Size=728090&bnum='\''+rnd+'\''" scrolling="no" width="728" height="090" frameborder="0" marginheight="0" marginwidth="0" title="Advertisement"></iframe>'\'');
</script>
</div>
 
  
 <!-- sid : 55807 : BOTTOM_SCRIPT -->  <script type="text/javascript">
  function lycos_census ()
  {
     _rsCI='\''lycos-ie'\'';
     _rsCG='\''0'\'';
     _rsDT=1;
     _rsSI=escape(window.location);
     var _rsLP=location.protocol.indexOf('\''https'\'')>-1?'\''https:'\'':'\''http:'\'';
     _rsRP=escape(document.referrer);
     _rsND=_rsLP+'\''//secure-uk.imrworldwide.com/'\'';

     if (parseInt(navigator.appVersion)>=4) {
	 _rsRD=(new Date()).getTime();
	 _rsSE=0;
	 _rsSV='\'''\'';
	 _rsSM=0;
	 _rsCL='\''<scr'\''+'\''ipt language="JavaScript" type="text/javascript" src="'\''+_rsND+'\''v5.js"><\/scr'\''+'\''ipt>'\'';
     } else {
	 _rsCL='\''<img src="'\''+_rsND+'\''cgi-bin/m?ci='\''+_rsCI+'\''&cg='\''+_rsCG+'\''&si='\''+_rsSI+'\''&rp='\''+_rsRP+'\''">'\'';
     }
     document.write(_rsCL);
     document.write('\''<noscript><img src="//secure-uk.imrworldwide.com/cgi-bin/m?ci=lycos-ie&amp;cg=0" alt=""></noscript>'\'');
}

    var alldiv = document.body.getElementsByTagName('\''div'\'');
    var call_lycos = 0;
    for (i=0;i<alldiv.length;i++) {
       if (alldiv[i].id.indexOf('\''lea_'\'') == 0) { call_lycos = 1; break;}
    }
    if (call_lycos == 1) {
      document.write('\''<scr'\''+'\''ipt src="http://fe.lea.lycos.co.uk/ats/adfunction.js"></scr'\''+'\''ipt>'\'')
    }
  </script>
  <script type="text/javascript">
    if (call_lycos == 1) {
      var refurl = document.URL;
      //var other = "ee=0";
      var other = "ee=0|ly12=Drama|ly12=Romance|ly12=War";
      lea_getter(refurl,other,"ie");
      lycos_census();
    }
  </script>
 
<img src="/rd/?q=50403000000030a090f29616f226e276966600000010c6a0622303038303430323c23353935383c25353830373c24363432323c27383130313c233539383830000001037a040379646370000001047&cb=120716318116503" width="1" height="1" alt="" border="0">
</div> <!-- id="wrapper" -->
</body>
</html>'
+ photo_line_number=151
++ sed -n '151 p'
++ sed 's|.*src=||'
++ cut '-d"' -f2
++ egrep 'jpg$|gif$|png$'
++ echo '
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1">
<title>Atonement (2007)</title>
<meta name="title" content="Atonement (2007)">
<meta name="description" content="Directed by Joe Wright.  With Saoirse Ronan, Ailidh Mackay, Brenda Blethyn. Fledgling writer Briony Tallis, as a 13-year-old, irrevocably changes the course of several lives when she accuses her older sister'\''s (Keira Knightley) lover (James McAvoy) of a crime he did not commit. Based on the British romance novel by Ian McEwan. Visit IMDb for Photos, Showtimes, Cast, Crew, Reviews, Plot Summary, Comments, Discussions, Taglines, Trailers, Posters, Fan Sites">

<meta name="keywords" content="Reviews, Showtimes, DVDs, Photos, Message Boards, User Ratings, Synopsis, Trailers, Credits">
<link rel="stylesheet" type="text/css" media="screen" href="http://i.media-imdb.com/images/SF01c175f07a3ed070f8f38d7f98c6ca3f/css2/consumersite.css" />
<link rel="icon" href="http://i.imdb.com/favicon.ico" />
<link rel="apple-touch-icon" href="http://i.media-imdb.com/apple-touch-icon.png" />
<style type="text/css">.showtimes { font-family: Arial, Helvetica, sans-serif }.showtimes .heading { font-size: 16px; font-weight: bold }.showtimes .time { color: #ff0000 }.tabular { border-collapse: collapse; border: 1px solid #9999ff }.tabular td.heading { background: #bbbbff }.tabular td.heading-right { background: #bbbbff; text-align: right; font-size: small }.tabular td.address { font-size: small; color: #666666; background: #eeeeee }.tabular td.detail { font-size: small; background: #eeeeee }.tabular tr.alternate { background: #eeeeee }.tabular td.item { border: 1px solid #9999ff }</style><link rel="stylesheet" type="text/css" href="http://i.media-imdb.com/images/SFae751da69684847117d205d2cbc0ae90/tn15/tn15.css" />

</head>
<!-- h=iop113 i=2008-04-01 s=legacy(default) t='\''Wed Apr  2 12:06:21 2008'\'' -->

<body bgcolor="#ffffff" text="#000000">
<div id="wrapper">
  
  

   <!-- sid : 35988 : TOP_BANNER --><div id="lea_728x90" style="height:90;" align="center"></div> 

<div id="root">
<layer name="root">

<div id="nb15">

  <div id="nb15home">
   <a href="/" onClick="(new Image()).src='\''/rg/nav-home/navbar/images/b.gif?link=/'\'';"><img src="http://i.media-imdb.com/images/nb15/logo2.gif" alt="Home" 
   title="The Internet Movie Database" border="0" width="177" height="78"></a>
  </div>
 <div id="nb15botbg">
 
  <div id="nb15tabs">
   <a id="nb15nowplaying" href="/nowplaying/" onClick="(new Image()).src='\''/rg/nav-nowplaying/navbar/images/b.gif?link=/nowplaying/'\'';"><i>Now Playing</i></a>
   <a id="nb15news" href="/news/" onClick="(new Image()).src='\''/rg/nav-news/navbar/images/b.gif?link=/news/'\'';"><i>Movie/TV News</i></a>
   <a id="nb15mm" href="/mymovies/list" onClick="(new Image()).src='\''/rg/nav-mymovies/navbar/images/b.gif?link=/mymovies/list'\'';"><i>My Movies</i></a>
   <a id="nb15dvd" href="/sections/dvd/" onClick="(new Image()).src='\''/rg/nav-video/navbar/images/b.gif?link=/sections/dvd/'\'';"><i>DVD New Releases</i></a>
   <a id="nb15imdbtv" href="/sections/tv/" onClick="(new Image()).src='\''/rg/nav-imdbtv/navbar/images/b.gif?link=/sections/tv/'\'';"><i>IMDbTV</i></a>
   <a id="nb15boards" href="/boards/" onClick="(new Image()).src='\''/rg/nav-boards/navbar/images/b.gif?link=/boards/'\'';"><i>Message Boards</i></a>
   <a id="nb15showtimes" href="/showtimes/" onClick="(new Image()).src='\''/rg/nav-showtimes/navbar/images/b.gif?link=/showtimes/'\'';"><i>Showtimes &amp; Tickets</i></a>
   <a id="nb15pro" href="http://pro.imdb.com/r/imdb-nav/" onClick="(new Image()).src='\''/rg/nav-pro/navbar/images/b.gif?link=http://pro.imdb.com/r/imdb-nav/'\'';"><i>IMDbPro</i></a>
   <a id="nb15resume" href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/nav-resume/navbar/images/b.gif?link=http://resume.imdb.com/'\'';"><i>IMDb Resume</i></a>
  </div>
 
  <div id="nb15topbg">
   <div id="nb15iesux">
    <div id="nb15personal">

     &nbsp;<span><a href="/register/login" onClick="(new Image()).src='\''/rg/sub-login/navbar/images/b.gif?link=/register/login'\'';">Login</a> | 
     <a href="/register/?why=personalize" onClick="(new Image()).src='\''/rg/sub-register/navbar/images/b.gif?link=/register/?why=personalize'\'';">Register</a></span>

    </div>
   </div>
  </div>
  <div id="nb15sub">
   <div>
   <a href="/" onClick="(new Image()).src='\''/rg/sub-home/navbar/images/b.gif?link=/'\'';">Home</a> |
   
    <a href="/chart/" onClick="(new Image()).src='\''/rg/sub-top/navbar/images/b.gif?link=/chart/'\'';">Top&nbsp;Movies</a> |
    <a href="/sections/gallery/" onClick="(new Image()).src='\''/rg/sub-gallery/navbar/images/b.gif?link=/sections/gallery/'\'';">Photos</a> |
    <a href="/indie/" onClick="(new Image()).src='\''/rg/sub-indie/navbar/images/b.gif?link=/indie/'\'';">Independent&nbsp;Film</a> |
    <a href="/sections/games/" onClick="(new Image()).src='\''/rg/sub-gamebase/navbar/images/b.gif?link=/sections/games/'\'';">GameBase</a> |
    <a href="/Browse/" onClick="(new Image()).src='\''/rg/sub-browse/navbar/images/b.gif?link=/Browse/'\'';">Browse</a> |
   
   <a href="/help/" onClick="(new Image()).src='\''/rg/sub-help/navbar/images/b.gif?link=/help/'\'';">Help</a>
   </div>
  </div>
  <div id="nb15search"> 
   <span class=search><a href="/search" onClick="(new Image()).src='\''/rg/search-img/navbar/images/b.gif?link=/search'\'';">search</a></span>
   <form method="get" action="/find" name="find">
    <select name="s">
     <option value="all" selected>All</option>
     <option value="tt">Titles</option>
     <option value="ep">TV Episodes</option>
     
      <option>My Movies</option>
     
     <option value="nm">Names</option>
     <option value="co">Companies</option>
     
      <option value="kw">Keywords</option>
      <option value="char">Characters</option>
      <option>Quotes</option>
      <option>Bios</option>
      <option>Plots</option>
    
    </select>
   <input name="q" size="28" value="">
    
    
    <input type="image"  id="nb15go_image"  src="http://i.media-imdb.com/images/intl/en/go.gif" alt="go" value="go" title="go">
    
    
    <span id="nb15searchlinks">
     <a href="/search" onClick="(new Image()).src='\''/rg/search-more/navbar/images/b.gif?link=/search'\'';">more</a> | 
     <a href="/help/show_leaf?searchtips" onClick="(new Image()).src='\''/rg/search-tips/navbar/images/b.gif?link=/help/show_leaf?searchtips'\'';">tips</a>
    </span>
   </form>
  </div>
 </div>
</div>
  

<div id="tn15" class="maindetails">

<div id="tn15shopbox" class="title uk">
<div class="left edge"></div><div class="right edge"></div>
<div class="label">SHOP <i>ATONEMENT</i></div>
<div class="logo"></div>
<div class="flags">
<script type="text/javascript">
<!--
function switchStore(co) {
  try { 
    var box = document.getElementById('\''tn15shopbox'\'');
    box.className = box.className.replace(/\b..\b$/, co); 
  } catch (e) { return true; }
  return false;
}
//-->
</script>
<a class="us" onclick="return switchStore('\''us'\'')" href="sales"><b>Amazon.com</b></a>
<a class="ca" onclick="return switchStore('\''ca'\'')" href="sales"><b>Amazon.ca</b></a>
<a class="uk" onclick="return switchStore('\''uk'\'')" href="sales"><b>Amazon.co.uk</b></a>
<a class="de" onclick="return switchStore('\''de'\'')" href="sales"><b>Amazon.de</b></a>
<a class="fr" onclick="return switchStore('\''fr'\'')" href="sales"><b>Amazon.fr</b></a>
</div>
<div class="stores">
<div class="us">
<a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047" title="Atonement DVD available at Amazon.com" class="dvd dvdon"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02057370000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02057370000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.com for all '\''Atonement'\'' products" class="all allon"><b>All</b></a>
</div>
<div class="uk">
<a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02057b60000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.co.uk for all '\''Atonement'\'' products" class="all allon"><b>All</b></a>
</div>
<div class="ca"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02036160000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.ca for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
<div class="de"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02046560000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.de for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
<div class="fr"><a href="/r/50403000000050a0904747037383332333330000001036a03046674600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="dvd"><b>DVD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03067863700000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="vhs"><b>VHS</b></a><a href="/r/50403000000050a0904747037383332333330000001036a0a037f657e64647271636b600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047"  class="soundtrack"><b>CD</b></a><a href="/r/50403000000050a0904747037383332333330000001036a03016c6c600000010d6a02066270000001037a0104700000010f5a0403786f6070000001047" title="Search Amazon.fr for all '\''Atonement'\'' products" class="all allon"><b>All</b></a></div>
</div>
</div>
<div id="tn15crumbs">
<a href="/">IMDb</a> &gt;
<b>Atonement (2007)</b>
</div>
<div id="tn15lhs">
  

<div class="photo">
<a name="poster" href="/media/rm2987758336/tt0783233" title="Atonement"><img border="0" alt="Atonement" title="Atonement" src="http://ia.media-imdb.com/images/M/MV5BMTM0ODc2Mzg1Nl5BMl5BanBnXkFtZTcwMTg4MDU1MQ@@._V1._SY140_SX100_.jpg" /></a>
</div>
  <a href="/mymovies/list?pending&amp;add=0783233" onClick="(new Image()).src='\''/rg/title-lhs/mymovies/images/b.gif?link=/mymovies/list?pending&amp;add=0783233'\'';">
  <img src="http://i.media-imdb.com/images//tn15/button_addtomymovies.gif" width="115" height="32" border="0" alt="[Add to My Movies]">
  </a>
<h6 style="margin-top: 4px">Quicklinks</h6><form><select id="quicklinks_select" onchange="document.location = this.options[this.selectedIndex].value">
<option value="maindetails" selected>main details</option><option value="combined">combined details</option><option value="fullcredits">full cast and crew</option><option value="companycredits">company credits</option><option value="usercomments">user comments</option><option value="externalreviews">external reviews</option><option value="newsgroupreviews">newsgroup reviews</option><option value="awards">awards</option><option value="ratings">user ratings</option><option value="parentalguide">parents guide</option><option value="recommendations">recommendations</option><option value="board">message board</option><option value="plotsummary">plot summary</option><option value="synopsis">plot synopsis</option><option value="keywords">plot keywords</option><option value="quotes">memorable quotes</option><option value="trivia">trivia</option><option value="goofs">goofs</option><option value="soundtrack">soundtrack listing</option><option value="movieconnections">movie connections</option><option value="faq">FAQ</option><option value="sales">merchandising links</option><option value="business">box office/business</option><option value="releaseinfo">release dates</option><option value="locations">filming locations</option><option value="technical">technical specs</option><option value="dvd">DVD details</option><option value="literature">literature listings</option><option value="news">news articles</option><option value="taglines">taglines</option><option value="trailers">trailers and videos</option><option value="posters">posters</option><option value="photogallery">photo gallery</option><option value="cinemashowtimes">showtimes</option><option value="officialsites">official sites</option><option value="miscsites">miscellaneous</option><option value="photosites">photographs</option><option value="soundsites">sound clips</option><option value="videosites">video clips</option>
</select></form>
<h6>Top Links</h6>
<a onClick="(new Image()).src='\''/rg/title-top-links/trailers/images/b.gif?link=/title/tt0783233/trailers'\'';" href="/title/tt0783233/trailers" class="link">trailers and videos</a><a onClick="(new Image()).src='\''/rg/title-top-links/fullcredits/images/b.gif?link=/title/tt0783233/fullcredits'\'';" href="/title/tt0783233/fullcredits" class="link">full cast and crew</a><a onClick="(new Image()).src='\''/rg/title-top-links/trivia/images/b.gif?link=/title/tt0783233/trivia'\'';" href="/title/tt0783233/trivia" class="link">trivia</a><a onClick="(new Image()).src='\''/rg/title-top-links/officialsites/images/b.gif?link=/title/tt0783233/officialsites'\'';" href="/title/tt0783233/officialsites" class="link">official sites</a><a onClick="(new Image()).src='\''/rg/title-top-links/quotes/images/b.gif?link=/title/tt0783233/quotes'\'';" href="/title/tt0783233/quotes" class="link">memorable quotes</a>
<h6>Overview</h6>
<a href="maindetails" class="link selected">main details</a><a href="combined" class="link">combined details</a><a href="fullcredits" class="link">full cast and crew</a><a href="companycredits" class="link">company credits</a><a href="tvschedule" class="link empty">tv schedule</a>
<h6>Awards &amp; Reviews</h6>
<a href="usercomments" class="link">user comments</a><a href="externalreviews" class="link">external reviews</a><a href="newsgroupreviews" class="link">newsgroup reviews</a><a href="awards" class="link">awards</a><a href="ratings" class="link">user ratings</a><a href="parentalguide" class="link">parents guide</a><a href="recommendations" class="link">recommendations</a><a href="board" class="link">message board</a>
<h6>Plot &amp; Quotes</h6>
<a href="plotsummary" class="link">plot summary</a><a href="synopsis" class="link">plot synopsis</a><a href="keywords" class="link">plot keywords</a><a href="amazon" class="link empty">Amazon.com summary</a><a href="quotes" class="link">memorable quotes</a>
<h6>Fun Stuff</h6>
<a href="trivia" class="link">trivia</a><a href="goofs" class="link">goofs</a><a href="soundtrack" class="link">soundtrack listing</a><a href="crazycredits" class="link empty">crazy credits</a><a href="alternateversions" class="link empty">alternate versions</a><a href="movieconnections" class="link">movie connections</a><a href="faq" class="link">FAQ</a>
<h6>Other Info</h6>
<a href="sales" class="link">merchandising links</a><a href="business" class="link">box office/business</a><a href="releaseinfo" class="link">release dates</a><a href="locations" class="link">filming locations</a><a href="technical" class="link">technical specs</a><a href="laserdisc" class="link empty">laserdisc details</a><a href="dvd" class="link">DVD details</a><a href="literature" class="link">literature listings</a><a href="news" class="link">news articles</a>
<h6>Promotional</h6>
<a href="taglines" class="link">taglines</a><a href="trailers" class="link">trailers and videos</a><a href="posters" class="link">posters</a><a href="photogallery" class="link">photo gallery</a>
<h6>External Links</h6>
<a href="cinemashowtimes" class="link">showtimes</a><a href="officialsites" class="link">official sites</a><a href="miscsites" class="link">miscellaneous</a><a href="photosites" class="link">photographs</a><a href="soundsites" class="link">sound clips</a><a href="videosites" class="link">video clips</a>  
</div>
<div id="tn15main">

<div id="tn15title">
<h1>Atonement <span>(<a href="/Sections/Years/2007">2007</a>)</span></h1>
</div>

<div id="tn15adrhs">
 <!-- sid : 35958 : TOP_RHS --><div id="lea_300x250"></div>   
advertisement
</div>

<div id="tn15content">

<div class="strip toplinks">
<table><tr>
<td>
<a href="/title/tt0783233/mediaindex" onClick="(new Image()).src='\''/rg/title-top/photos/images/b.gif?link=/title/tt0783233/mediaindex'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_photos.gif" width="16" height="22" alt="*" border="0">
<b>photos</b>
</a>
</td>
<td>
<a href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-top/boards/images/b.gif?link=/title/tt0783233/board'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_messageboard.gif" width="21" height="22" alt="*" border="0">
<b>board</b>
</a>
</td>
<td>
<a href="/title/tt0783233/trailers-me60827838" onClick="(new Image()).src='\''/rg/title-top/trailers/images/b.gif?link=/title/tt0783233/trailers-me60827838'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_trailer.gif" width="20" height="22" alt="*" border="0">
<b>trailer</b>
</a>
</td>
<td>
<a href="http://pro.imdb.com/title/tt0783233/" onClick="(new Image()).src='\''/rg/title-top/pro/images/b.gif?link=http://pro.imdb.com/title/tt0783233/'\'';">
<img src="http://i.media-imdb.com/images/tn15/icon_pro.gif" width="25" height="22" alt="*" border="0">
<b>details</b>
</a>
</td>
</tr></table>
</div>
 
 
 

<div id="tn15rating" class="two guest">
<div class="usr rating">

<a href="/register/?why=vote">Register</a> or <a href="/register/login">login</a> to rate this title

</div>
<div class="general rating">
<div class="starbar static"><div class="outer"><div class="inner" style="width: 158px"></div></div></div>
<b>User Rating:</b> 
<b>7.9/10</b> 
  <small>(<a href="ratings">37,863 votes</a>)</small>
<div class="bottom">

<a class="tn15more" href="ratings">more</a>

</div>

</div>

</div>
<script>
<!--
function tn15resize(timeout, chain) { 
  var timer;
  return function() { 
    window.clearTimeout(timer); 
    timer = window.setTimeout(function() { try { 
      var w;
      if (self.innerWidth) w = self.innerWidth;
      else if (document.documentElement && document.documentElement.clientWidth) w = document.documentElement.clientWidth;
      else if (document.body) w = document.body.clientWidth;
      document.getElementById('\''tn15content'\'').className = w < 950 ? '\''thin'\'' : '\''wide'\'';
    } catch (e) { } }, timeout);
    if (chain) chain();
  }
}
window.onload = tn15resize(1000, window.onload);
window.onresize = tn15resize(100, window.onresize);
(tn15resize(100))();
//-->
</script>

<style type="text/css">
.media_strip_thumbs {
  overflow: hidden;
  height: 90px;
}
.media_strip_thumbs img {
  margin-right: 0.2em;
}
</style>

<table style="border-collapse:collapse;">
<tr>

<td width="50%" class="media_strip_header">
<b>Photos</b>
<span>(<a href="/rg/photos-title/gallery-link/title/tt0783233/mediaindex">see all 50</a> | <a href="/rg/photos-title/slideshow-link/media/rm3527055360/tt0783233?slideshow=1">slideshow</a>)</span>
</td>

<td width="50%" class="media_strip_header">
<b>Videos</b>
</td>

</tr>
<tr>

<td>
<div class="media_strip_thumbs">
<a href="/rg/photos-title/summary/media/rm3527055360/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTUxMTYxMDYwMV5BMl5BanBnXkFtZTYwMjUyNzc4._V1._CR81,0,322,322_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3510278144/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTU1NDM1MjA1Nl5BMl5BanBnXkFtZTYwMzUyNzc4._V1._CR84,0,316,316_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3493500928/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTQ2ODQ1Mzk4MF5BMl5BanBnXkFtZTYwNDUyNzc4._V1._CR82,0,321,321_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3745159168/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTgwODMwNDE1Ml5BMl5BanBnXkFtZTYwNzIxMDM4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3728381952/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTMwNDQzNzU5Ml5BMl5BanBnXkFtZTYwODIxMDM4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3711604736/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTkyMTk4NTk3OF5BMl5BanBnXkFtZTYwNTUyNzc4._V1._CR82,0,320,320_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3694827520/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTQzNjc3NjcxOV5BMl5BanBnXkFtZTYwNjUyNzc4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3678050304/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMjA0ODE4MjU5OF5BMl5BanBnXkFtZTYwNzUyNzc4._V1._CR94,0,297,297_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3661273088/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTI2NzUwODUzM15BMl5BanBnXkFtZTYwODUyNzc4._V1._CR0,0,450,450_SS90_.jpg" border="0"></a>
<a href="/rg/photos-title/summary/media/rm3644495872/tt0783233"><img height="90" width="90" src="http://ia.media-imdb.com/images/M/MV5BMTcwMjA1MjkxN15BMl5BanBnXkFtZTYwOTIxMDM4._V1._CR81,0,322,322_SS90_.jpg" border="0"></a>
</div>
</td>

<td>
<div class="media_strip_thumbs">
<a href="/rg/videos-title/summary//video/trailer/me60827838/"><img src="http://ia.media-imdb.com/images/M/MV5BMTM1MjUwMzgwMV5BMl5BanBnXkFtZTYwNDM3ODM4._V1._SY90_PIimdb-sprockets,BottomRight,0,0_SY90_.jpg" border="1"></a>
</div>
</td>

</tr>
</table>
  

<hr/>

<h3>Overview</h3>

<div class="info">
<h5>Director:</h5>
<a href="/name/nm0942504/">Joe Wright</a><br/>
</div>

<div class="info">
<h5>Writers:</h5>
<a href="/name/nm0568605/">Ian McEwan</a> (novel)<br/><a href="/name/nm0358960/">Christopher Hampton</a> (screenplay)<br/>
</div>

<div class="info">
<h5>Release Date:</h5> 
4 January 2008 (USA)
 <a class="tn15more inline" href="/title/tt0783233/releaseinfo" onClick="(new Image()).src='\''/rg/title-tease/releasedates/images/b.gif?link=/title/tt0783233/releaseinfo'\'';">more</a>

 <a style="margin-left: 1em" class="tn15more inline" href="/title/tt0783233/trailers-me60827838" onClick="(new Image()).src='\''/rg/title-tease/trailers/images/b.gif?link=/title/tt0783233/trailers-me60827838'\'';">view trailer</a>

</div>

<div class="info">
<h5>Genre:</h5>
<a href="/Sections/Genres/Drama/">Drama</a> / <a href="/Sections/Genres/Romance/">Romance</a> / <a href="/Sections/Genres/War/">War</a> <a class="tn15more inline" href="/title/tt0783233/keywords" onClick="(new Image()).src='\''/rg/title-tease/keywords/images/b.gif?link=/title/tt0783233/keywords'\'';">more</a>
</div>

<div class="info">
<h5>Tagline:</h5>
You can only imagine the truth. <a class="tn15more inline" href="/title/tt0783233/taglines" onClick="(new Image()).src='\''/rg/title-tease/taglines/images/b.gif?link=/title/tt0783233/taglines'\'';">more</a>
</div>

<div class="info">
<h5>Plot Outline:</h5> 
Fledgling writer Briony Tallis, as a 13-year-old, irrevocably changes the course of several lives when she accuses her older sister'\''s (Keira Knightley) lover (James McAvoy) of a crime he did not commit. Based on the British romance novel by Ian McEwan. <a class="tn15more inline" href="/title/tt0783233/plotsummary" onClick="(new Image()).src='\''/rg/title-tease/plotsummary/images/b.gif?link=/title/tt0783233/plotsummary'\'';">more</a>
</div>

<div class="info">
<h5>Plot Synopsis:</h5>
<a href="synopsis">View full synopsis. (warning! may contain spoilers)</a>
</div>

<div class="info">
<h5>Plot Keywords:</h5>

<a href="/keyword/profanity/">Profanity</a>
 / 
<a href="/keyword/manor/">Manor</a>
 / 
<a href="/keyword/long-take/">Long&#160;Take</a>
 / 
<a href="/keyword/underwater/">Underwater</a>
 / 
<a href="/keyword/dunkirk/">Dunkirk</a>

<a class="tn15more inline" href="/title/tt0783233/keywords" onClick="(new Image()).src='\''/rg/title-tease/keywords/images/b.gif?link=/title/tt0783233/keywords'\'';">more</a>

</div>

<div class="info">
<h5>Awards:</h5> 
Won Oscar.
 Another 20 wins
&amp;
60 nominations
<a class="tn15more inline" href="/title/tt0783233/awards" onClick="(new Image()).src='\''/rg/title-tease/awards/images/b.gif?link=/title/tt0783233/awards'\'';">more</a>
</div>

<div class="info">
<h5>User Comments:</h5>
A work of art...
<a class="tn15more inline" href="#comment">more</a>
</div>

<hr/>
<div class="headerinline"><h3>Cast</h3>&nbsp;<small style="position: relative; bottom: 1px">(Cast overview, first billed only)</small></div><div class="info"><table class="cast">  <tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1519680/">Saoirse Ronan</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027091/">Briony Tallis - Aged 13</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2854564/">Ailidh Mackay</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0053845/">Singing Housemaid</a></td></tr><tr class="odd"><td class="hs"><a href="/name/nm0000950/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0000950/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMjE5MjgwNDgyMV5BMl5BanBnXkFtZTcwNTgzNzQxMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0000950/">Brenda Blethyn</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027098/">Grace Turner</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0922169/">Julia West</a></td><td class="ddd"> ... </td><td class="char">Betty</td></tr><tr class="odd"><td class="hs"><a href="/name/nm0564215/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0564215/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMjA1NDI5NDA5NV5BMl5BanBnXkFtZTcwNjU0OTAzMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0564215/">James McAvoy</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027086/">Robbie Turner</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0910040/">Harriet Walter</a></td><td class="ddd"> ... </td><td class="char">Emily Tallis</td></tr><tr class="odd"><td class="hs"><a href="/name/nm0461136/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm0461136/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMTg1NzUxOTE2MV5BMl5BanBnXkFtZTcwNTQzMDgyMQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm0461136/">Keira Knightley</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0027082/">Cecilia Tallis</a></td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1017334/">Juno Temple</a></td><td class="ddd"> ... </td><td class="char">Lola Quincey</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2328584/">Felix von Simson</a></td><td class="ddd"> ... </td><td class="char">Pierrot Quincey</td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2335109/">Charlie von Simson</a></td><td class="ddd"> ... </td><td class="char">Jackson Quincey</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0654295/">Alfie Allen</a></td><td class="ddd"> ... </td><td class="char">Danny Hardman</td></tr><tr class="even"><td class="hs"><a href="/name/nm1171145/" onClick="(new Image()).src='\''/rg/title-tease/tinyhead/images/b.gif?link=/name/nm1171145/'\'';"><img src="http://ia.media-imdb.com/images/M/MV5BMTkwMzAzMzUwM15BMl5BanBnXkFtZTcwNzAwMDU2MQ@@._V1._SX23_SY30_.jpg" width="23" height="32" border="0"></a><br></td><td class="nm"><a href="/name/nm1171145/">Patrick Kennedy</a></td><td class="ddd"> ... </td><td class="char">Leon Tallis</td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm1212722/">Benedict Cumberbatch</a></td><td class="ddd"> ... </td><td class="char">Paul Marshall</td></tr><tr class="even"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm0927835/">Peter Wight</a></td><td class="ddd"> ... </td><td class="char"><a href="/character/ch0061069/">Police Inspector</a></td></tr><tr class="odd"><td class="hs"><a href="http://resume.imdb.com/" onClick="(new Image()).src='\''/rg/title-tease/resumehead/images/b.gif?link=http://resume.imdb.com/'\'';"><img src="http://i.media-imdb.com/images/tn15/addtiny.gif" width="25" height="31" border="0"></td><td class="nm"><a href="/name/nm2852111/">Leander Deeny</a></td><td class="ddd"> ... </td><td class="char">Police Constable</td></tr></table><a class="tn15more" href="fullcredits#cast">more</a></div><div><form action="/character/create" method="post"><input type="hidden" name="title" value="tt0783233">Create a character page for: <select name="name" onchange="if (this.options[this.selectedIndex].value == '\''...'\'') document.location='\''fullcredits#cast'\''"><option>Betty</option><option>Emily Tallis</option><option>Lola Quincey</option><option>Pierrot Quincey</option><option>Jackson Quincey</option><option>Danny Hardman</option><option>Leon Tallis</option><option>Paul Marshall</option><option>Police Constable</option><option disabled="disabled">-----------</option><option value="...">more...</option></select> <input style="font: Tahoma, Verdana, sans-serif; font-size: 8pt; font-weight: bold; background-color: #eeeeee; border-color: #ccccee; color: black" type="submit" value="Create &raquo;"> <a target="_blank" href="/help/show_leaf?createchar"><img src="http://i.media-imdb.com/images/help13x10.gif" width="13" height="10" border="0" alt="?"></a></form></div>
<hr/>

<h3>Additional Details</h3>

<div class="info">
<h5>Also Known As:</h5>Reviens-moi (France)  <br>
  
  
<a class="tn15more" href="/title/tt0783233/releaseinfo#akas" onClick="(new Image()).src='\''/rg/title-tease/akas/images/b.gif?link=/title/tt0783233/releaseinfo#akas'\'';">more</a>

</div>

<div class="info">
<h5><a href="/mpaa">MPAA</a>:</h5> 
Rated R for disturbing war images, language and some sexuality.
</div>

<div class="info">
<h5>Parents Guide:</h5>
<a href="parentalguide">View content advisory for parents</a>
</div>

<div class="info">
<h5>Runtime:</h5>
130 min 
</div>

<div class="info">
<h5>Country:</h5>
<a href="/Sections/Countries/UK/">UK</a> / <a href="/Sections/Countries/France/">France</a>
</div>

<div class="info">
<h5>Language:</h5>
<a href="/Sections/Languages/English/">English</a> / <a href="/Sections/Languages/French/">French</a>
</div>

<div class="info">
<h5>Color:</h5>
<a href="/List?color-info=Color&&heading=13;Color">Color</a> 
</div>

<div class="info">
<h5>Aspect Ratio:</h5>
1.85 : 1 <a class="tn15more inline" href="/title/tt0783233/technical" onClick="(new Image()).src='\''/rg/title-tease/aspect/images/b.gif?link=/title/tt0783233/technical'\'';">more</a>
</div>

<div class="info">
<h5>Sound Mix:</h5>
<a href="/List?sound-mix=DTS&&heading=15;DTS">DTS</a>  / <a href="/List?sound-mix=Dolby%20Digital&&heading=15;Dolby%20Digital">Dolby Digital</a> 
</div>

<div class="info">
<h5>Certification:</h5>
<a href="/List?certificates=Ireland:15A&&heading=14;Ireland:15A">Ireland:15A</a>  / <a href="/List?certificates=Malaysia:U&&heading=14;Malaysia:U">Malaysia:U</a>  / <a href="/List?certificates=Brazil:14&&heading=14;Brazil:14">Brazil:14</a>  / <a href="/List?certificates=Taiwan:PG-12&&heading=14;Taiwan:PG-12">Taiwan:PG-12</a>  / <a href="/List?certificates=Argentina:16&&heading=14;Argentina:16">Argentina:16</a>  / <a href="/List?certificates=USA:R&&heading=14;USA:R">USA:R</a> <i>(certificate #43417)</i> / <a href="/List?certificates=Sweden:11&&heading=14;Sweden:11">Sweden:11</a>  / <a href="/List?certificates=Norway:11&&heading=14;Norway:11">Norway:11</a>  / <a href="/List?certificates=Switzerland:12&&heading=14;Switzerland:12">Switzerland:12</a> <i>(canton of Vaud)</i> / <a href="/List?certificates=Netherlands:12&&heading=14;Netherlands:12">Netherlands:12</a>  / <a href="/List?certificates=Switzerland:12&&heading=14;Switzerland:12">Switzerland:12</a> <i>(canton of Geneva)</i> / <a href="/List?certificates=Australia:MA&&heading=14;Australia:MA">Australia:MA</a>  / <a href="/List?certificates=Philippines:PG-13&&heading=14;Philippines:PG-13">Philippines:PG-13</a> <i>(MTRCB)</i> / <a href="/List?certificates=Canada:14A&&heading=14;Canada:14A">Canada:14A</a>  / <a href="/List?certificates=Japan:PG-12&&heading=14;Japan:PG-12">Japan:PG-12</a>  / <a href="/List?certificates=UK:15&&heading=14;UK:15">UK:15</a>  / <a href="/List?certificates=Finland:K-13&&heading=14;Finland:K-13">Finland:K-13</a>  / <a href="/List?certificates=Singapore:M18&&heading=14;Singapore:M18">Singapore:M18</a>  / <a href="/List?certificates=France:Unrated&&heading=14;France:Unrated">France:Unrated</a>  / <a href="/List?certificates=South%20Korea:15&&heading=14;South%20Korea:15">South Korea:15</a>  / <a href="/List?certificates=Portugal:M/12&&heading=14;Portugal:M/12">Portugal:M/12</a> <i>(Qualidade)</i> / <a href="/List?certificates=Germany:12&&heading=14;Germany:12">Germany:12</a> 
</div>

<div class="info">
<h5>Filming Locations:</h5> 

<a  href="/List?endings=on&&locations=Aldwych%20Underground%20Station,%20Aldwych,%20Holborn,%20London,%20England,%20UK&&heading=18;with+locations+including;Aldwych%20Underground%20Station,%20Aldwych,%20Holborn,%20London,%20England,%20UK">Aldwych Underground Station, Aldwych, Holborn, London, England, UK</a>

<a class="tn15more inline" href="/title/tt0783233/locations" onClick="(new Image()).src='\''/rg/title-tease/locations/images/b.gif?link=/title/tt0783233/locations'\'';">more</a>

</div>

<div class="info">
<h5>MOVIEmeter: <a href="/help/show_leaf?prowhatisstarmeter"><img src="http://i.media-imdb.com/images/tn15/meter_help.gif" width="12" height="12" border="0" alt="?"></a></h5>
<span class="meter">
<span class="down"><img src="http://i.media-imdb.com/images/tn15/meter_down.gif" width="9" height="8" alt="V" valign="middle"/> 27% </span>since last week
<a href="http://pro.imdb.com/title/tt0783233/graph-data" onClick="(new Image()).src='\''/rg/meter-tease/title/images/b.gif?link=http://pro.imdb.com/title/tt0783233/graph-data'\'';">why?</a>
</span>
</div>

<div class="info">
<h5>Company:</h5>
<a href="/company/co0057311/">Working Title Films</a>

<a class="tn15more inline" href="/title/tt0783233/companycredits">more</a>
</div>

<hr/> 

<h3>Fun Stuff</h3>

<div class="info">
<h5>Trivia:</h5>
The set of Dunkirk, built at Redcar, was the most expensive set, costing an estimated 1 million pounds.
<a class="tn15more inline" href="/title/tt0783233/trivia" onClick="(new Image()).src='\''/rg/title-tease/trivia/images/b.gif?link=/title/tt0783233/trivia'\'';">more</a>
</div>

<div class="info">
<h5>Goofs:</h5>
Continuity: During the library scene, Cecelia slips her shoe off while making love but when Briony interrupts, we see that both of her shoes are still on.
<a class="tn15more inline" href="/title/tt0783233/goofs" onClick="(new Image()).src='\''/rg/title-tease/goofs/images/b.gif?link=/title/tt0783233/goofs'\'';">more</a>
</div>

<div class="info">
<h5>Quotes:</h5>

<b><a href="/name/nm0461136/">Cecilia Tallis</a></b>:
Come back. Come back to me.
<a class="tn15more inline" href="/title/tt0783233/quotes" onClick="(new Image()).src='\''/rg/title-tease/quotes/images/b.gif?link=/title/tt0783233/quotes'\'';">more</a>
</div>

<div class="info">
<h5>Movie Connections:</h5> 
Featured in <a href="/title/tt1154617/">&#34;Siskel &#38; Ebert &#38; the Movies: (2007-12-08)&#34;</a> (2007)
<a class="tn15more inline" href="/title/tt0783233/movieconnections" onClick="(new Image()).src='\''/rg/title-tease/movieconnections/images/b.gif?link=/title/tt0783233/movieconnections'\'';">more</a>
</div>

<div class="info">
<h5>Soundtrack:</h5> 
(There'\''ll Be Bluebirds Over) The White Cliffs of Dover
<a class="tn15more inline" href="/title/tt0783233/soundtrack" onClick="(new Image()).src='\''/rg/title-tease/soundtrack/images/b.gif?link=/title/tt0783233/soundtrack'\'';">more</a>
</div>

<hr/>

<h3>FAQ</h3>

<a href="/title/tt0783233/faq#.2.1.3" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.3'\'';">Music in the Atonement trailer</a>
<br/>

<a href="/title/tt0783233/faq#.2.1.2" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.2'\'';">Was Robbie guilty of the rape of Lola?</a>
<br/>

<a href="/title/tt0783233/faq#.2.1.6" onClick="(new Image()).src='\''/rg/title-tease/faq-question/images/b.gif?link=/title/tt0783233/faq#.2.1.6'\'';">Is this based on a true story?</a>
<br/>

<a class="tn15more" href="/title/tt0783233/faq" onClick="(new Image()).src='\''/rg/title-tease/faq-more/images/b.gif?link=/title/tt0783233/faq'\'';">more</a>

<hr/>
<div class="headerinline">
<a name="comment"><h3>User Comments</h3></a>&nbsp;&nbsp;&nbsp;<a href="usercomments-enter"><span>(Comment on this title)</span></a>
</div>

<div class="comment">
<script type="text/javascript">
<!--
function yn(id, vote) {
  if (!document.getElementById || !document.createElement || !document.removeChild || !document.appendChild || !document.childNodes || !document.createTextNode) return true;
  var i = new Image();
  i.onload =  function() { ynd(id, 1) };
  i.onerror = function() { ynd(id, 0) };
  i.src = '\''usercomments-vote?yni_'\''+id+'\''='\''+vote;
  return false;
}
function ynd(id, status) {
  var d, s, t;
  if (!(d = document.getElementById('\''ynd_'\''+id))) return true;
  while (d.childNodes.length) d.removeChild(d.childNodes[0]);
  var s = document.createElement('\''span'\'');
  if (!status) s.setAttribute('\''class'\'', '\''error'\'');
  var t = document.createTextNode(status ? '\''Thank you, your vote will be counted and appear on this page within 24 hours.'\'' : '\''Sorry, there was a problem collecting your vote.'\'');
  s.appendChild(t);
  d.appendChild(s);
}
//-->
</script>

<div class="small">
17 out of 30 people found the following comment useful:-
</div>

<b>A work of art...</b>, 26 September 2007<br>
<img width="102" height="12" alt="10/10" src="http://i.media-imdb.com/images/showtimes/100.gif"><br>
<div class="small">
Author:
<a href="/user/ur8640608/comments">ChrisD1984</a> <small>from Canada</small>
</div>

</p>
<p>
Crafted in Britain by director Joe Wright, Atonement tells the story of
young author Briony Tallis who becomes jealous of her older sister&#39;s
illicit love affair with a servant. And with this, she finds a love
letter meant for Cecilia (her sister) written by the servant Robbie
Turner and misconstrues it as a letter written with sadistic-perverted
undertones when in reality it was a second draft that Robbie deemed to
silly to use. Briony assumes that Robbie is a nymphomaniac and it is
with this notion that she accuses Robbie with the rape of her younger
sister. Upon hearing this, the Tallis family has him arrested and he
ends up in World War II whilst Cecilia winds ups being a nurse. The
rest of the movie revolves around Robbie trying to find his way back to
Cecilia and also displays the cathartic process that Briony faces upon
reaching adolescence and realizing the life-changing mistakes that she
made. Atonement is sort of stuck in the middle in regards to whether it
renders primarily on emotion or story. It is based on an Ian McEwen
novel, so it does use some story elements in the latter segment of the
film, such as when the story falls into the &#39;war-romance&#39;-type
category. The first half however feels highly eastern-oriented with
well-placed shots around staircases and through windows that draw us
into the secret love affair that Cecilia and Robbie have undertaken.
The first part of the movie feels almost like a different film
altogether. It feels quite artsy in spots and a lot of shots do not
help to push the story forward. Having only seen two of Wright&#39;s films
(Pride and Prejudice being the other) it&#39;s hard to lump his style into
being specifically east or west. Pride and Prejudice had a lot of
eastern elements in its use of detailed steady cam shots that follow
its main characters around the sprawling English countryside. Atonement
also has this, with an amazing 10-minute long steady cam shot that
follows Robbie on a beach through the after effects of war. The shot is
so magnificent that you forget about the lack of cutting and you start
to feel as if you can taste the acrid flavor of rusted steel on a
battleship or the stolid stench of soldiers&#39; breath and spent bombs.
The shot is very well choreographed as well as we see literally
hundreds of extras that weave in and out of frame, each doing their own
duty. Joe Wright uses background action nicely to tell different
stories of different people without even giving them lines. Just watch
the steady shot as it follows Robbie past a somber-looking band play a
waltz or as he shoves into another soldier; a very well executed shot
indeed. This shot does have an eastern-feel to it as it does not push
the story forward but focuses on allowing the audience to see through
the eyes of the main character. Editor Paul Tohill does a great job as
well; his editing is never too fast paced but doesn&#39;t lag behind
either. When he splices, he makes sure that we have enough time to
fully incorporate ourselves within the basis of a shot. Again, his lack
of editing in the steady camera scene helps to reinforce this. This can
also be seen by assessing the scene that takes place near the end when
Briony has come back to apologize to Cecilia and Robbie. His edits are
now quick and slightly robust and help move the story along as we feel
and see the tension-filled apartment room. The medium shot of Robbie
when he almost decks Briony is tremendously powerful.
</p>

<div class="yn" id="ynd_1736819">
<form method="get" action="/register/">
<input type="hidden" name="why" value="comment_vote">Was the above comment useful to you?
<input class="click" type="image"  value="yes" src="http://i.media-imdb.com/images/tn15/btn_yes.gif" width="34" height="19">
<input class="click" type="image"  value="no" src="http://i.media-imdb.com/images/tn15/btn_no.gif" width="34" height="19">

</form>
</div>

</div>

<a class="tn15more" href="/title/tt0783233/usercomments" onClick="(new Image()).src='\''/rg/title-tease/comments-bottom/images/b.gif?link=/title/tt0783233/usercomments'\'';">more</a>

<hr/>
<h3>Message Boards</h3>
Discuss this title with other users on <a href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-tease/boards-top/images/b.gif?link=/title/tt0783233/board'\'';">IMDb message board for Atonement (2007)</a>

<table class="boards">
<tr><th class="left">Recent Posts (updated daily)</th><th class="right">User</th></tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/100232145">The chinese burns  on Lola</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur10853560/boards/profile">kehindebamgboye</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101850429">More contrivances and misunderstandings than a season of Three'\''s Company</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur6456707/boards/profile">slop101</a></td>
</tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101769005">Needs to be seen at least twice</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur13076570/boards/profile">scoochie9</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101894197">angry, angry, angry</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur10215948/boards/profile">smj274</a></td>
</tr>

<tr class="odd">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/95026725">Different nationalities, different tastes?</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur15051762/boards/profile">wirelessaxis</a></td>
</tr>

<tr class="even">
<td><a href="/rg/title-tease/boards-subject/title/tt0783233/board/nest/101974304">Wright'\''s DVD director commentary</a></td>
<td><a href="/rg/title-tease/boards-user/user/ur9394104/boards/profile">nshifley</a></td>
</tr>

</table>
<a class="tn15more" href="/title/tt0783233/board" onClick="(new Image()).src='\''/rg/title-tease/boards-bottom/images/b.gif?link=/title/tt0783233/board'\'';">more</a>

<hr/>

<h3>Recommendations</h3>
<div class="strip">
If you enjoyed this title, our database also recommends:
<table class="recs">
<tr class="poster">

<td><a href="/title/tt0332280/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/60/95/28m.jpg"></a></td>

<td><a href="/title/tt0175880/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/27/36/14/10m.jpg"></a></td>

<td><a href="/title/tt0301390/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/95/65/28m.jpg"></a></td>

<td><a href="/title/tt0319524/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/99/65/28m.jpg"></a></td>

<td><a href="/title/tt0213149/"><img class="poster" alt="-" width="93" src="http://ia.media-imdb.com/media/imdb/01/I/68/97/95m.jpg"></a></td>

</tr>
<tr>

<td><a href="/title/tt0332280/">The Notebook</a></td>

<td><a href="/title/tt0175880/">Magnolia</a></td>

<td><a href="/title/tt0301390/">The Heart of Me</a></td>

<td><a href="/title/tt0319524/">How to Deal</a></td>

<td><a href="/title/tt0213149/">Pearl Harbor</a></td>

</tr>
<tr class="rating">

<td class="first">
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 80px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 80px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 63px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 53px"></div></div>
</td>

<td>
<small>IMDb User Rating:</small>
<br/>
<div class="tinystarbar"><div style="width: 53px"></div></div>
</td>

</tr>
</table>
<a href="/AddRecommendation?const=0783233">Add a recommendation</a> |
<a href="/title/tt0783233/recommendations" onClick="(new Image()).src='\''/rg/title-tease/recommendations/images/b.gif?link=/title/tt0783233/recommendations'\'';">Show more recommendations</a>
</div>
<h3>Related Links</h3><table>
<tr><td width="33%" style="width: 400px"> <a href="/title/tt0783233/fullcredits" onClick="(new Image()).src='\''/rg/title-related/maindetails-fullcredits/images/b.gif?link=/title/tt0783233/fullcredits'\'';">Full cast and crew</a></td><td width="33%" style="width: 400px"> <a href="/title/tt0783233/companycredits" onClick="(new Image()).src='\''/rg/title-related/maindetails-companycredits/images/b.gif?link=/title/tt0783233/companycredits'\'';">Company credits</a></td><td width="33%" style="width: 400px"> <a href="/title/tt0783233/externalreviews" onClick="(new Image()).src='\''/rg/title-related/maindetails-externalreviews/images/b.gif?link=/title/tt0783233/externalreviews'\'';">External reviews</a></td></tr><tr><td width="33%" style="width: 400px"> <a href="/title/tt0783233/news" onClick="(new Image()).src='\''/rg/title-related/maindetails-news/images/b.gif?link=/title/tt0783233/news'\'';">News articles</a></td><td width="33%" style="width: 400px"> <a href="/Sections/Genres/Drama/" onClick="(new Image()).src='\''/rg/title-related/maindetails-genre/images/b.gif?link=/Sections/Genres/Drama/'\'';">IMDb Drama section</a></td><td width="33%" style="width: 400px"> <a href="/Sections/Countries/UK/" onClick="(new Image()).src='\''/rg/title-related/maindetails-country/images/b.gif?link=/Sections/Countries/UK/'\'';">IMDb UK section</a></td></tr><tr><td width="33%" style="width: 400px"> <a href="/mymovies/list?pending&amp;add=0783233" onClick="(new Image()).src='\''/rg/title-related/maindetails-mymovies/images/b.gif?link=/mymovies/list?pending&amp;add=0783233'\'';">Add this title to MyMovies</a></td>
</table>
<div id="tn15bot">
 <div class="right">
   <!-- sid : 46422 : GOOGLE --><div style="text-align:center">
<iframe name="GoogleAd" src="http://i.imdb.com/images/3pads/google/google-afc.html?channel=t-channel" align="top" scrolling="no" width="500" height="240" frameborder="0" marginheight="0" marginwidth="0" align="middle"></iframe>
</div>
 
 </div>
 <div class="left">
  <p><form method="post" action="/updates"><input type="hidden" name="auto" value="legacy/title/tt0783233/"><input type="image" width="67" height="21" name="Update" src="http://i.media-imdb.com/images/tn15/update.gif" border="0" alt="Update"></p><p><i>You may report errors and omissions on this page to the IMDb database managers. They will be examined and if approved will be included in a future update. Clicking the '\''Update'\'' button  will take you through a step-by-step process.</i></p></form>

 </div>
 <br clear="right"/>
</div>

</div>
</div> 
</div> 
<br clear="both" />

<div id="footer" class="ft">
<hr width="100%" size=1>
<p class="footer" align="center">
<a href="/">Home</a>&nbsp;
  | <a href="/search">Search</A>&nbsp;
  | <a href="/NowPlaying/">Now Playing</a>&nbsp;
  | <a href="/News/">News</A>&nbsp;
  | <a href="/register/?why=mymovies_footer">My Movies</A>&nbsp;
  | <a href="/Games/">Games</A>&nbsp;
  | <a href="/boards/">Boards</A>&nbsp;
| <a href="/help/">Help</a>&nbsp;
  | <A HREF="/Showtimes">US&nbsp;Movie&nbsp;Showtimes</A>&nbsp;
| <A HREF="/top_250_films">Top 250</A>&nbsp;
| <a href="/register/?why=footer">Register</a>&nbsp;
  | <A HREF="/recommends/">Recommendations</A>&nbsp;
  | <A HREF="/widgets/">Widgets</A><br>
  <A HREF="/Charts/">Box&nbsp;Office</A> 
  | <A HREF="/a2z">Index</A> 
  | <A HREF="/Sections/Trailers/">Trailers</A> 
  
  | <a href="/jobs"><b>Jobs</b></a>&nbsp;
  | <a href="https://secure.imdb.com/register/subscribe?c=a394d4442664f6f6475627" onClick="(new Image()).src='\''/rg/PRO_FOOT/FOOTER/images/b.gif?link=https://secure.imdb.com/register/subscribe?c=a394d4442664f6f6475627'\'';">
    <span style="color:#cc3333"><b>IMDbPro.com&nbsp;-&nbsp;Free&nbsp;Trial</b></span></a> 
  | <a href="http://resume.imdb.com" onClick="(new Image()).src='\''/rg/resume-footer/footer/images/b.gif?link=http://resume.imdb.com'\'';"><span style="color:#cc3333"><b>IMDb Resume</b></span></a>
<br><br>
<a href="/help/show_article?conditions">Copyright &copy;</a> 1990-2008 
<a href="/help/">IMDb.com, Inc.</a><br>
<a href="/help/show_article?conditions">Terms</a> and <a href="/privacy">Privacy Policy</a> under which this service is provided to you.<br>
An <a href="http://www.amazon.com/exec/obidos/redirect-home/internetmoviedat">
<img align="middle" width="86" height="18" border="0" src="http://i.imdb.com/amazon_logo.gif" alt="Amazon.com"></a> company.&nbsp;
<a href="/advertising/">Advertise</a> on IMDb.&nbsp;
<a href="/tiger_redirect?FT_LIC&/Licensing/">License</a> our content.
</p>
<p class="footer" align="center">IMDb is powered by Perl and <b><a href="/rg/jobs/footer-pbp/help/show_leaf?jobatimdb">we are hiring</a></b>!</p>
</div>

</layer>
</div>
 <!-- sid : 78101 : BOTTOM_BANNER -->
<div align="center">
<script language="JavaScript">
var rnd = Math.round(Math.random()*10000000);
document.writeln('\''<iframe src="http://uac.advertising.com/wrapper/aceUAC.htm#Site=705838&Size=728090&bnum='\''+rnd+'\''" scrolling="no" width="728" height="090" frameborder="0" marginheight="0" marginwidth="0" title="Advertisement"></iframe>'\'');
</script>
</div>
 
  
 <!-- sid : 55807 : BOTTOM_SCRIPT -->  <script type="text/javascript">
  function lycos_census ()
  {
     _rsCI='\''lycos-ie'\'';
     _rsCG='\''0'\'';
     _rsDT=1;
     _rsSI=escape(window.location);
     var _rsLP=location.protocol.indexOf('\''https'\'')>-1?'\''https:'\'':'\''http:'\'';
     _rsRP=escape(document.referrer);
     _rsND=_rsLP+'\''//secure-uk.imrworldwide.com/'\'';

     if (parseInt(navigator.appVersion)>=4) {
	 _rsRD=(new Date()).getTime();
	 _rsSE=0;
	 _rsSV='\'''\'';
	 _rsSM=0;
	 _rsCL='\''<scr'\''+'\''ipt language="JavaScript" type="text/javascript" src="'\''+_rsND+'\''v5.js"><\/scr'\''+'\''ipt>'\'';
     } else {
	 _rsCL='\''<img src="'\''+_rsND+'\''cgi-bin/m?ci='\''+_rsCI+'\''&cg='\''+_rsCG+'\''&si='\''+_rsSI+'\''&rp='\''+_rsRP+'\''">'\'';
     }
     document.write(_rsCL);
     document.write('\''<noscript><img src="//secure-uk.imrworldwide.com/cgi-bin/m?ci=lycos-ie&amp;cg=0" alt=""></noscript>'\'');
}

    var alldiv = document.body.getElementsByTagName('\''div'\'');
    var call_lycos = 0;
    for (i=0;i<alldiv.length;i++) {
       if (alldiv[i].id.indexOf('\''lea_'\'') == 0) { call_lycos = 1; break;}
    }
    if (call_lycos == 1) {
      document.write('\''<scr'\''+'\''ipt src="http://fe.lea.lycos.co.uk/ats/adfunction.js"></scr'\''+'\''ipt>'\'')
    }
  </script>
  <script type="text/javascript">
    if (call_lycos == 1) {
      var refurl = document.URL;
      //var other = "ee=0";
      var other = "ee=0|ly12=Drama|ly12=Romance|ly12=War";
      lea_getter(refurl,other,"ie");
      lycos_census();
    }
  </script>
 
<img src="/rd/?q=50403000000030a090f29616f226e276966600000010c6a0622303038303430323c23353935383c25353830373c24363432323c27383130313c233539383830000001037a040379646370000001047&cb=120716318116503" width="1" height="1" alt="" border="0">
</div> <!-- id="wrapper" -->
</body>
</html>'
+ grabber_picture=http://ia.media-imdb.com/images/M/MV5BMTM0ODc2Mzg1Nl5BMl5BanBnXkFtZTcwMTg4MDU1MQ@@._V1._SY140_SX100_.jpg
+ [[ -n http://ia.media-imdb.com/images/M/MV5BMTM0ODc2Mzg1Nl5BMl5BanBnXkFtZTcwMTg4MDU1MQ@@._V1._SY140_SX100_.jpg ]]
+ wget -q http://ia.media-imdb.com/images/M/MV5BMTM0ODc2Mzg1Nl5BMl5BanBnXkFtZTcwMTg4MDU1MQ@@._V1._SY140_SX100_.jpg -O /tmp/thumb18395.jpg
+ grabber_picture=/tmp/thumb18395.jpg
+ '[' -n /tmp/thumb18395.jpg ']'
+ '[' -d /home/jarlath/.avatar-factory/icons/film/dvd ']'
+ create_theme_icon
+ case $theme_name in
+ dvd_theme_base=base
+++ identify -format %w /tmp/thumb18395.jpg
++ bc
++ cut -d. -f 1
+++ identify -format %h /tmp/thumb18395.jpg
++ echo 'scale=2; 95/140*100'
+ picture_aspect=67
+ '[' 67 -gt 65 ']'
+ picture_aspect=555x106
+ convert /tmp/thumb18395.jpg -thumbnail 555x106 -crop 77x106+0+0 +repage /tmp/thumb18395.png
+ create_theme
+ convert /usr/local/share/avatar-factory/themes/DVD/base.png -geometry +0+0 -composite /tmp/thumb18395.png -geometry +10+17 -composite /usr/local/share/avatar-factory/themes/DVD/top.png -geometry +0+0 -composite '/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png'
convert: missing an image filename `/home/jarlath/.avatar-factory/icons/film/dvd/_home_jarlath_Videos_Atonement 2007.png'.
+ rm /tmp/thumb18395.jpg /tmp/thumb18395.png
+ [[ avatars = thumbnails ]]
+ report_icon_creation=yes
+ report_icon_created=1
+ [[ avatars = avatars ]]
+ '[' /tmp/thumb18395.jpg '!=' no ']'
+ [[ -n '' ]]
+ set +x
1/1 - added Atonement 2007
+ [[ -f /tmp/thumb18395.??? ]]
jarlath@jarlath-laptop:~$ 

```

---

### Post by Yuzem on 2008-04-02
mmm... everything looks ok to me.
The "convert: missing an image filename" error has been reported and it seems to be a problem with some versions of imagemagick or an error in the package.
Are you using ubuntu?
What imagemagick version do you have:
```
convert -version
```
Mine is 6.2.4

I think that this is the same problem:
[http://ubuntuforums.org/showthread.php?p=3553353#post3553353](http://ubuntuforums.org/showthread.php?p=3553353#post3553353)

And I also got some mails about this, all using a specific imagemagick version and if I remember correctly the distro was archlinux.

---

### Post by QwUo173Hy on 2008-04-02
Maybe that's the problem. Mine is  Version: ImageMagick 6.3.7 02/19/08 Q16 

I'm using Ubuntu Hardy Beta. If the problem lies in ImageMagick, I guess we just have to wait for it to be fixed. Oh well.

Keep up the good work Yuzem.

---

### Post by jayde6 on 2008-04-15
I decided to try out the beta for hardy heron and it appears that the latest version of nautilus processes desktop file thumbnails differently, they are the same size as regular icons now instead of being larger like picture thumbnails. Is anyone else encoutering this behaviour and/or perhaps have a fix?

---

### Post by pencilcheck on 2008-04-24
It's very strange to me too with the Hardy 8.04.
I have the latest ImageMagick and it's not working with current avatar-factory.

---

### Post by Yuzem on 2008-04-24
> **jayde6 said:**
> I decided to try out the beta for hardy heron and it appears that the latest version of nautilus processes desktop file thumbnails differently, they are the same size as regular icons now instead of being larger like picture thumbnails. Is anyone else encoutering this behaviour and/or perhaps have a fix?
I don't have hardy but maybe there is an option for that in gconf-editor.
If there is no option for that, the only solution that I can think of is editing the source code:
[http://ubuntuforums.org/showthread.php?t=549360](http://ubuntuforums.org/showthread.php?t=549360)

> **pencilcheck said:**
> It's very strange to me too with the Hardy 8.04.
I have the latest ImageMagick and it's not working with current avatar-factory.

I think that it is a problem with imagemagick.
Try the following command (replace image_1.jpg and image_2.jpg with some real pictures):
```
convert image_1.jpg -composite image_2.jpg -composite output.jpg
```

If that fails then there must be a problem with the installation of imagemagick.

ImageMagick usage:
[http://www.imagemagick.org/Usage/layers/#convert](http://www.imagemagick.org/Usage/layers/#convert)

---

### Post by pencilcheck on 2008-04-24
The command you suggested fails.
```
convert: missing an image filename `output.jpg'.
```

---

### Post by jayde6 on 2008-04-24
> **Yuzem said:**
> I don't have hardy but maybe there is an option for that in gconf-editor.
If there is no option for that, the only solution that I can think of is editing the source code:
[http://ubuntuforums.org/showthread.php?t=549360](http://ubuntuforums.org/showthread.php?t=549360)

There is an option in gconf that I normally do anyway which adjusts the thumbnail size. It had no effect on the avatars. I also noticed that I encounter the same problem when I set an image as a custom icon. Unfortunately from reading posts leading up to the release of hardy it might be working as intended as a 'fix' to another problem. I don't know if it is different in the actual release of hardy as your program is one of the reasons I use linux, so I've already switched back to gutsy a while ago.

---

### Post by pencilcheck on 2008-04-25
Do I have to reinstall ImageMagick?

---

### Post by Hells_Dark on 2008-04-25
I can't make it work with the tv-show grabber :
> avatar-factory -g tv-show . . --type 0
Building list of folders to process...
/usr/local/bin/avatar-factory: line 498: /usr/local/share/avatar-factory/themes/dvd-3: Aucun fichier ou répertoire de ce type
There is no cover for Series
/usr/local/bin/avatar-factory: line 615: create_theme_icon : commande introuvable
1/10 - added Darker Than Black
/usr/local/bin/avatar-factory: line 615: create_theme_icon : commande introuvable
2/10 - added Death Note
/usr/local/bin/avatar-factory: line 615: create_theme_icon : commande introuvable

etc.

By the way, i just discovered this app and i just love it :)

---

### Post by Yuzem on 2008-04-25
There is a new version.

I think that most of the problems should be gone now.

Changelog:
```
25.04.08------0.6.2
	+fixed problem with Desktop name for different languages (Thanks to direk_)
	+fixed bug in film grabber
	+fixed problem with dvd-1 dvd-2 and dvd-3 themes not being installed that causes the tv-show grabber to fail.
	+fixed an important problem with all the themes that causes avatar-factory to fail on some distributions like Ubuntu Hardy Heron and ArchLinux
```

[**[COLOR="Red"]Download[/COLOR]**]("http://www.gnomefiles.org/app.php/Avatar_Factory")

---

### Post by pencilcheck on 2008-04-25
Thank you for the update. Now at least the picture is working. 
I'm going to try some more and be amazed. :D

---

### Post by Hells_Dark on 2008-04-27
Thanks for the update !

---

### Post by herbster on 2008-04-27
Sorry, I must be missing the obvious, but having just installed this I'm unclear how this functions. I use amarok and for example if I have /media/mp3/Beatles with a few albums in there, how do I get this to go? I download the album covers myself from amazon or somewhere?

```
avatar-factory -g music input/folders folder/2/save
```

What's the input and output to be? Thanks for any help, this looks quite neat and would love to use it!

---

### Post by QwUo173Hy on 2008-04-27
Thanks Yuzem. It's working for me now. But the thumbnails are tiny! See the attachment.

---

### Post by pencilcheck on 2008-04-27
Yea, It's tiny.

---

### Post by Yuzem on 2008-04-27
> **herbster said:**
> Sorry, I must be missing the obvious, but having just installed this I'm unclear how this functions. I use amarok and for example if I have /media/mp3/Beatles with a few albums in there, how do I get this to go? I download the album covers myself from amazon or somewhere?

```
avatar-factory -g music input/folders folder/2/save
```

What's the input and output to be? Thanks for any help, this looks quite neat and would love to use it!
The command you are using is ok. You can use your music folder as the input and it will scan all folders recursively. It will process all folders that have music and at least one picture inside that will be used as the cover.
Check the first post, there is a section that says: "Automatic cover download (for the music grabber)"

> **jarlath said:**
> Thanks Yuzem. It's working for me now. But the thumbnails are tiny! See the attachment.
mmm... I think that it is nautilus fault. Maybe the new version on Hardy Heron. It is working fine here on Gutsy.
You can go to ~/.avatar-factory/icons/film/dvd/ and check the resolution.
It must be 128.
You could augment the zoom level. I think nautilus remembers that setting by folder.

---

### Post by Hells_Dark on 2008-04-28
Yes it's small...
And if it's hardy, then it's the new gnome i guess.

---

### Post by QwUo173Hy on 2008-04-28
You're right, it is a nautilus problem. The images in the folder you mentioned looks good. But in nautilus, I cannot get them to look good (Hardy) because the zoom level can only be 200% which is too small, or 400% which is too big and gets so anti-aliased that the image is distorted.

I've made attachments that might describe it better.

---

### Post by Hells_Dark on 2008-05-05
Any tips for the new nautilus ?

It's small :
[[img]http://pix.nofrag.com/d/8/f/16afa9348ebe8b6eee8a40aadd233t.jpg[/img]](http://pix.nofrag.com/d/8/f/16afa9348ebe8b6eee8a40aadd233.html)
...

---

### Post by s_spiff on 2008-05-05
> **Hells_Dark said:**
> Any tips for the new nautilus ?

It's small :
[[IMG]http://pix.nofrag.com/d/8/f/16afa9348ebe8b6eee8a40aadd233t.jpg[/IMG]]("http://pix.nofrag.com/d/8/f/16afa9348ebe8b6eee8a40aadd233.html")
...
ok this may be a noobish solution, and I haven't got this installed to try it. But try pressing and holding ctrl key, and moving the mouse wheel up.

---

### Post by QwUo173Hy on 2008-05-05
That magnifies the avatars, but doesn't increase the resolution of the images. So in other words, they look bad if you enlarge them.

---

### Post by Hells_Dark on 2008-05-05
Yes and especially, that makes BIG spaces between icons which is awfull. I much prefer the fact they are small.

^^'

---

### Post by s_spiff on 2008-05-06
ouu ok. My bad. I installed to check, and yes, they do look bad if they're magnified beyond a certain point. Oh well, i guess we'll have to wait for someone to find a solution.

---

### Post by Hells_Dark on 2008-05-06
Yes..
Btw it's a really good apps and i still love it.

**A question** : when i put "--type1 -g tv-show", i have the window where i can choose the episode (really good idea) but i can't choose the player that is used next.
It's totem, i want mplayer, any idea ?

---

### Post by jayde6 on 2008-05-06
> **Hells_Dark said:**
> Yes..
Btw it's a really good apps and i still love it.

**A question** : when i put "--type1 -g tv-show", i have the window where i can choose the episode (really good idea) but i can't choose the player that is used next.
It's totem, i want mplayer, any idea ?

In your home folder there should be a .avatar-factory folder (ctrl-h to unhide) inside if there isnt already make a file called avatar-launcher and put ```
tv_show="mplayer"
``` inside it.

---

### Post by Hells_Dark on 2008-05-06
Thanks jayde6. Works fine :)

EDIT : NO !
It doesn't work well.
The application is launching every episode since the one you choose..
how to change that ?

---

### Post by jayde6 on 2008-05-06
> **Hells_Dark said:**
> Thanks jayde6. Works fine :)

EDIT : NO !
It doesn't work well.
The application is launching every episode since the one you choose..
how to change that ?

Do you mean one after another or at the same time? Because the program is designed to go down the list from the episode you selected and I am not sure if there is a way to change that. If it is at the same time, I am afraid I have no clue.

---

### Post by Hells_Dark on 2008-05-06
Yes, one after the other.
With totem, they are in a playlist so it's not bad.
But with mplayer, you close the window and the second episode starts, you close, it starts, you close...
The conclusion is : you CANT use mplayer with the type 1 of the tv-show grabber :(

---

### Post by jayde6 on 2008-05-06
Hmm, thats odd, because I use type 1 for my tvshows and if I close mplayer it does not continue on to the next.

---

### Post by Hells_Dark on 2008-05-07
The problem disappeared ! I don't know why..
But it's ok now :D

EDIT : Found ! Actually, if you close the window (with the cross) it close mplayer. But if you want to exit typing enter (as i used to do), you pass to the enxt file.

I would like to choose this behavior.

---

### Post by chrislazarus on 2008-05-12
My first post though I've been lurking and using Ubuntu since Dapper. I want to say thanks to Yuzem first of all for these wonderful scripts. It seems nobody has a problem with the widget appearing on the desktop. I'm running Hardy Heron and the latest version of avatar-factory. I have set music_widget=yes and music=quodlibet in the avatar-launcher file and the avatars are set as launchers. The desktop is also using Nautilus default and is named Desktop but the music widget on the desktop does not show the album picture and if I drag an avatar to it, it's not added as shown in the sample pictures. Double-clicking on the music widget produces this error message: "There was an error launching the application". It works fine if I double-clicked any of the avatars. How do I get the music widget to work?

---

### Post by Yuzem on 2008-05-12
> **Hells_Dark said:**
> Yes and especially, that makes BIG spaces between icons which is awfull. I much prefer the fact they are small.

^^'
For the big spaces:
Right clic in the folder background and select "organize elements" > "sort by name" (or any other except manual)
Right clic again and: "organize elements" > "compact organization"
I am not sure if the names are those in english.

> **jarlath said:**
> That magnifies the avatars, but doesn't increase the resolution of the images. So in other words, they look bad if you enlarge them.
I don't know if it will solve something but I made a new shadow theme in 256x256 format. It will be in the next version.

> **Hells_Dark said:**
> EDIT : Found ! Actually, if you close the window (with the cross) it close mplayer. But if you want to exit typing enter (as i used to do), you pass to the enxt file.

You could use the Escape key.

> **chrislazarus said:**
> My first post though I've been lurking and using Ubuntu since Dapper. I want to say thanks to Yuzem first of all for these wonderful scripts. It seems nobody has a problem with the widget appearing on the desktop. I'm running Hardy Heron and the latest version of avatar-factory. I have set music_widget=yes and music=quodlibet in the avatar-launcher file and the avatars are set as launchers. The desktop is also using Nautilus default and is named Desktop but the music widget on the desktop does not show the album picture and if I drag an avatar to it, it's not added as shown in the sample pictures. Double-clicking on the music widget produces this error message: "There was an error launching the application". It works fine if I double-clicked any of the avatars. How do I get the music widget to work?
You are welcome. :)
That is a problem with the new version of imagemagick.
I fixed it some days ago but it seems to be a bug with nautilus also. It doesn't update the icon when it is changed.
I will try to do something about that.

---

### Post by Hells_Dark on 2008-05-13
> **Yuzem said:**
> For the big spaces:
Right clic in the folder background and select "organize elements" > "sort by name" (or any other except manual)
Right clic again and: "organize elements" > "compact organization"
I am not sure if the names are those in english.

Nop, that's awful using this option. Icons are everywhere..

> **Yuzem said:**
> 
You could use the Escape key.

I will try this.


Thanks.

---

### Post by Yuzem on 2008-05-18
There is a new version:
[**[COLOR="Red"]Download[/COLOR]**]("http://www.gnomefiles.org/app.php/Avatar_Factory")

---

### Post by Hells_Dark on 2008-05-24
hi,

hey men, what about a new dvd case theme ?
Look at this new Manicho art :
[http://manicho.deviantart.com/art/dvd-Plastic-Case-PSD-file-86546288](http://manicho.deviantart.com/art/dvd-Plastic-Case-PSD-file-86546288)
Looks nice, heh ?

---

### Post by davim on 2008-05-24
you should post your debs on getdeb.net and what about putting your project on launchpad.net??

---

### Post by isaacj87 on 2008-05-24
> **Hells_Dark said:**
> hi,

hey men, what about a new dvd case theme ?
Look at this new Manicho art :
[http://manicho.deviantart.com/art/dvd-Plastic-Case-PSD-file-86546288](http://manicho.deviantart.com/art/dvd-Plastic-Case-PSD-file-86546288)
Looks nice, heh ?

Man, those are nice! and the author is so generous too :)

---

### Post by Yuzem on 2008-05-24
> **Hells_Dark said:**
> hi,

hey men, what about a new dvd case theme ?
Look at this new Manicho art :
[http://manicho.deviantart.com/art/dvd-Plastic-Case-PSD-file-86546288](http://manicho.deviantart.com/art/dvd-Plastic-Case-PSD-file-86546288)
Looks nice, heh ?
Yes, very nice.
I downloaded the file but it doesn't show as it should in gimp.
I will try to do it, if everything goes right it will be on the next version.

> **davim said:**
> you should post your debs on getdeb.net
Ok, I will.

> **davim said:**
>  and what about putting your project on launchpad.net??
It is already on launchpad but I don't know how to use most of it features.
I use it to upload the packages that are linked on gnomefiles:
[https://launchpad.net/avatar-factory](https://launchpad.net/avatar-factory)

---

### Post by Yuzem on 2008-05-24
> **davim said:**
> you should post your debs on getdeb.net
How? :confused:
I tried and I failed. :(

---

### Post by ayoli on 2008-05-24
> **Yuzem said:**
> How? :confused:
I tried and I failed. :(

you're a dev not a packager, ask for a packager to do that (maybe aidanr (or a nick something like this) who have been your first packager).

---

### Post by Yuzem on 2008-05-24
Ok then... it is not that important.
It is on gnomefiles and there is always a deb package available.

---

### Post by tad1073 on 2008-05-25
How do I get this to work?

---

### Post by trappy on 2008-05-25
I'm trying to test this with these options;

```
qix@sara:~$ avatar-factory -g music --type 0 /media/Music/AA/Ace\ of\ Base\ -\ Greatest\ Hits/ /media/Music/AA/
```

Though it doesn't seem to work at all, getting this output;


```
Building list of folders to process...
identify: unable to open image `/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-front_cover-ego.jpg
/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-back_cover-ego.jpg': No such file or directory.
identify: unable to open image `/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-front_cover-ego.jpg
/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-back_cover-ego.jpg': No such file or directory.
/usr/local/share/avatar-factory/themes/cd: line 11: - : syntax error: operand expected (error token is " ")
```

Anyone knows why? Seems like a hell of a nice app...

Edit: Tried to GUI, but nothing happens at all even though it says "All Done". :(

---

### Post by Yuzem on 2008-05-25
> **tad1073 said:**
> How do I get this to work?
At the terminal type:
```
man avatar-factory
```
If you are having problems tell me what is not working or what you want to do?

> **trappy said:**
> I'm trying to test this with these options;

```
qix@sara:~$ avatar-factory -g music --type 0 /media/Music/AA/Ace\ of\ Base\ -\ Greatest\ Hits/ /media/Music/AA/
```

Though it doesn't seem to work at all, getting this output;


```
Building list of folders to process...
identify: unable to open image `/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-front_cover-ego.jpg
/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-back_cover-ego.jpg': No such file or directory.
identify: unable to open image `/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-front_cover-ego.jpg
/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-back_cover-ego.jpg': No such file or directory.
/usr/local/share/avatar-factory/themes/cd: line 11: - : syntax error: operand expected (error token is " ")
```

Anyone knows why? Seems like a hell of a nice app...

Edit: Tried to GUI, but nothing happens at all even though it says "All Done". :(
Do you have access to that folder?
Maybe avatar-factory can't open the picture because it doesn't have permissions.
Try this at the terminal and tell me the result:
```
stat "/media/Music/AA/Ace of Base - Greatest Hits/00-ace_of_base-greatest_hits-front_cover-ego.jpg"
```

Edit: ups, I just checked and it is a bug with the latest version. I will fix it soon.

---

### Post by Yuzem on 2008-05-25
New version ready:
[**[COLOR="Red"]Download[/COLOR]**]("http://www.gnomefiles.org/app.php/Avatar_Factory")

---

### Post by trappy on 2008-05-25
> **Yuzem said:**
> New version ready:
[**[COLOR="Red"]Download[/COLOR]**]("http://www.gnomefiles.org/app.php/Avatar_Factory")
Thanks, now that works! Now I only have to find out why Exaile is unable to find any covers AT ALL at amazon. :confused:

---

### Post by tad1073 on 2008-05-25
I have "A Crow Left of the Murder" in /mnt/Music/Incubus/A Crow Left of the Murder/ and the image I want to use for the folder is in /mnt/Music/Incubus/A Crow Left of the Murder/Folder.jpg, how do I use that image for the folder?

---

### Post by Yuzem on 2008-05-25
The names that have priority are "cover", "folder" and any any that contains "front", case insensitive, jpg or png extension.

If no pictures with those names are found, the grabber will use any jpg or png picture inside the album folder.

If you are getting the wrong picture check the names and try again. Note that you will have to delete the existing icon or use the "-f" option to force overwriting the already created icon.

If you used the cd theme (default) then the icon should be:
~/.avatar-factory/icons/music/cd/_mnt_Music_Incubus_A Crow Left of the Murder.png

---

### Post by tad1073 on 2008-05-25
I guess I am an idiot because I have no clue how to use your program. The only file I have in ~/.avatar-factory is /gui

---

### Post by Yuzem on 2008-05-25
Don't worry, do this in the terminal:
```
mkdir ~/music_avatars
```
Then:
```
avatar-factory -g music /mnt/Music ~/music_avatars
```

That should create avatars for all folders inside /mnt/Music containing music files and at least one picture.
They will be saved in ~/music_avatars

There are many option that you can use, read the man page:
```
man avatar-factory
```

...and the music grabber help:
```
avatar-factory -g music --help
```

Let me know if you have any other question.

---

### Post by Hells_Dark on 2008-05-26
> **Yuzem said:**
> Yes, very nice.
I downloaded the file but it doesn't show as it should in gimp.
I will try to do it, if everything goes right it will be on the next version.


Yes, he did it with PhotoShop..

Btw, :guitar:

---

### Post by trappy on 2008-05-26
Yuzem , finally it works' amazing work. One more question though - I have zoom level 200% in Nautilus to be able to see what album it really is, but it's still very small, is there any way I could make the covers "larger" in nautilus?

---

### Post by Yuzem on 2008-05-26
Let me guess, you are using Hardy. Nautilus has some bugs on Hardy. You will have to wait until they get fixed.

You could also try thunar, it is excellent file manager.

---

### Post by trappy on 2008-05-26
Yey, you're the man. Thanks for all help, looks amazing.

---

### Post by Hells_Dark on 2008-05-27
> **Yuzem said:**
> Let me guess, you are using Hardy. Nautilus has some bugs on Hardy. You will have to wait until they get fixed.

You could also try thunar, it is excellent file manager.

I don't think it's a hardy bug.
It's just the way the new nautilus version is..

---

### Post by trappy on 2008-05-27
Well that's sounds pretty shitty - does anyone know how to replace nautilus with thunar completely?

---

### Post by SQuark on 2008-05-28
> **trappy said:**
> Well that's sounds pretty shitty - does anyone know how to replace nautilus with thunar completely?

I'm assuming you still want Nautilus to manage your desktop (otherwise, it's probably easiest to remove Nautilus all together).
There's a script [over at psychocats.net](http://www.psychocats.net/ubuntu/nonautilusplease) that'll do the trick.

---

### Post by trappy on 2008-05-29
> **SQuark said:**
> I'm assuming you still want Nautilus to manage your desktop (otherwise, it's probably easiest to remove Nautilus all together).
There's a script [over at psychocats.net](http://www.psychocats.net/ubuntu/nonautilusplease) that'll do the trick. 

Actually, I don't. I'm using Openbox. I just thought that if I just removed nautilus there could be problems further on, like when removing Internet Explorer from a Windows installation.

---

### Post by Gourgi on 2008-05-29
> **trappy said:**
> Actually, I don't. I'm using Openbox. I just thought that if I just removed nautilus there could be problems further on, like when removing Internet Explorer from a Windows installation.

hehe no it's nothing like that :D
you can remove nautilus via synaptic or
```
sudo apt-get remove nautilus
```

:popcorn:

---

### Post by trappy on 2008-05-30
Thanks. :guitar:

---

### Post by Hells_Dark on 2008-06-10
What's new ? °n___n°

---

### Post by Yuzem on 2008-06-10
Well... I am not spending much time on this.
I couldn't get the layers from Manicho's psd file and I will not be able to do the theme at least someone exports the file to a gimp compatible format or one file by layer in png format.

In the next version there will be a new interface to configure the grabbers, more simple and powerful.

Also the youtube grabber will be renamed to web-videos if I can't think of a better name and it will include other networks as dailymotion.(Ask here for other networks)

---

### Post by Hells_Dark on 2008-06-11
Ok, thank you Yuzem !

---

### Post by SQuark on 2008-08-03
How do I make this work with Banshee 1.2?

---

### Post by Yuzem on 2008-08-03
I will fix that for the next version.

You can do the following:
```
sudo gedit /usr/local/share/avatar-factory/launchers/music
```
Line 137 should say:
```
			eval banshee --play --enqueue  $(find "$1" -maxdepth 1 -type f -iname '*.mp3' -or -iname '*.aac' -or -iname '*.m4a' -or -iname '*.ogg' -or -iname '*.flac' -or -iname '*.wma' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```

Change banshee by banshee-1:
```
			eval banshee-1 --play --enqueue  $(find "$1" -maxdepth 1 -type f -iname '*.mp3' -or -iname '*.aac' -or -iname '*.m4a' -or -iname '*.ogg' -or -iname '*.flac' -or -iname '*.wma' | sort | sed -e 's/^/"/' -e 's/$/"/' | tr '\n' ' ')
```

I didn't test it but I think that it should work.

Edit:
I tried but it isn't working. It seems a banshee problem, "banshee-1 --help-all" gives some options but neither work.
For example:
banshee-1 --play-enqueued track.mp3
banshee-1 --play track.mp3
Neither work...

---

### Post by Drizzel on 2008-08-09
Hi Yuzem, I'm kinda lost here.. How do I get my stuff to look like what you have in the screenshots in your first post? I installed Avatar Factory, but cant figure out how to make it look like yours. How do I use the music widget? I dont see it in my screenlets. Also my music avatars dont look anything like yours. I'm using Nautilus in hardy heron btw.

Zenity doesnt work.. its not in the applications menu and when I hit alt+F2 to try and run it that way it doesnt work either. So I'm trying to do things through 'Avatar Factory' in the applications menu. There arent many options. I dont see how you got it looking so good, mine looks rather boring and lackluster. Here's a screenshot.. There are huge spaces in between the albums, they dont look as pretty as yours. Did all you guys just figure it out on your own or is there a tutorial I'm missing on how to fully customize everything?

---

### Post by Yuzem on 2008-08-09
Hi Drizzel.
Nautilus has changed in Hardy and some things doesn't work as before.
The icons size is one of the problems. I am planning to fix that in the next version.
You could try Thunar for now, it is a great file manager:
```
sudo apt-get install thunar
```

Another problem is the "no name" option, I don't know how to fix that...

The widget should appear automatically if the avatars are set to act as launchers (--type 1) but it doesn't work as before. The "no name" option doesn't work and when resized to the maximum size it doesn't match the icon maximum size.

---

### Post by Drizzel on 2008-08-09
So as I understand, the best way to configure everything is by using commands through the terminal? I really like the way that music pic looks. How can I achieve this?

[IMG]http://img374.imageshack.us/img374/8009/musicwidgetkr4.th.jpg[/IMG]


Sorry for all the questions.. I just really like all your screenshots and would like to get the same results. Thanks for making Avatar Factory. :)

---

### Post by Yuzem on 2008-08-09
No problem, make all the questions you want.
The gui is an interface for the commands. For advanced things you must use the command line.

To make the widget look like the picture:
```
gedit ~/.avatar-factory/avatar-launcher
```
And insert:
```
widget_name=.
```

That deals with the "no name" problem.
Then right click the widget and select "resize icon" or something like that.
Scale the widget to the maximum size.

To have multiple albums just drag an album to the widget. The album will be added to the playlist depending on the player of your choice.

If you are having problems when dragging an album to the widget and you are using AWN (avant window manager) it could be that AWN is getting in the way. You have to drag it to the upper part of the widget or move the widget up a little.

---

### Post by Drizzel on 2008-08-09
Ok I did what you said, but still am unsure what to do next.. Here's a screen. I ran that command and it brought up a text editor, then I typed widget_name=. and pushed 'save'. Now this is whats in my avatar factory folder. I tried dragging the avatar-launcher into the screenlets manager, but it wouldn't accept it. How do I use the widget? I'm not even sure I have the widget.. Maybe this is too advanced for me, I just dont get it at all.

[[IMG]http://img396.imageshack.us/img396/6916/screenshot1mg0.th.png[/IMG]](http://img396.imageshack.us/my.php?image=screenshot1mg0.png)

---

### Post by Yuzem on 2008-08-09
Oh... I didn't know that it wasn't showing at all. The widget works with nautilus as your desktop. Because of that it doesn't consume any resource.
You don't need screenlet for this.
You should have a file in your desktop folder called 'music_widget.desktop'
Thats the widget. From your desktop (nautilus) you can resize it and drag music avatars to it to enqueue albums.

---

### Post by Drizzel on 2008-08-10
I dont have that music_widget.desktop file.. I even searched my entire system with catfish looking for it thinking maybe it was placed somewhere else. I installed the Avatar Factory deb. Should I have got a different package? Seems I dont have half the stuff that your screenshots have.. No widgets.

Edit: When I open Avatar Factory gui I'm presented with several options. What grabber should I choose to get that music effect I've been talking about? I tried the music one, but it just gives one single icon with album art. Like in my first screenshot. Nothing like your awesome music screenshot.

I think I'm just done with this.. I've been messing with it for a long time now with no success. The pictures, avatar, film, dont work. I dont have the music widget.. I just dont understand why nothing works for me. I've wasted an entire day.

---

### Post by Yuzem on 2008-08-10
mmm... thats strange. Sorry that you have wasted an entire day. :(

In case that you want to try one more time I will give you step by step instructions from the beginning:

**Making the Avatars**
From the command line:
```
avatar-factory -g music --type 1 ~/your-music-folder -/destination
```

The --type 1 option isn't necessary because is the default option for the music grabber.
You must replace "~/your-music-folder" with the path to the folder where your music is and "-/destination" with the folder where you want to save the avatars.
Make sure that there is no avatar inside the destination folder.
Avatars should be created for any folder that contains music files and at least one picture that will be used as the cover.

**The rest of the story**
```
rm ~/.avatar-factory/avatar-launcher
```
That will force the default options. I assume that you have totem installed. (default in hardy)

**Testing it**
Now make click on one of the avatars that were created.
This is what it should happen:
1- Totem should open and start playing the selected album.
2- A file named 'music_widget.desktop' should be created in your desktop folder.

Does it work now?
I know that it is a little unintuitive at first but once that you understand how it works it is very easy.

---

### Post by SQuark on 2008-08-11
> **Yuzem said:**
> I will fix that for the next version.
Edit:
I tried but it isn't working. It seems a banshee problem, "banshee-1 --help-all" gives some options but neither work.
For example:
banshee-1 --play-enqueued track.mp3
banshee-1 --play track.mp3
Neither work...

Thanks for trying. I guess I'll have to wait for a new Banshee version.

---

### Post by Hells_Dark on 2008-08-20
Yuzem > How did you put a backgound for thunar ?
And is it possible to put a background in nautilus just for **one** folder ?
(and where did you find yours)

I keep waiting for a icon size fix.

---

### Post by Yuzem on 2008-08-20
> **Hells_Dark said:**
> Yuzem > How did you put a backgound for thunar ?
I didn't. I think you saw nautilus.

> **Hells_Dark said:**
> And is it possible to put a background in nautilus just for **one** folder ?
Yes: nautilus > edit > backgrounds and emblems > drag and drop with the middle button.

> **Hells_Dark said:**
> (and where did you find yours)
They are included in the tar zipped package.

> **Hells_Dark said:**
> I keep waiting for a icon size fix.
Coming soon... :)

---

### Post by Hells_Dark on 2008-08-21
Thanks a a lot !

And sometimes, i've no covers. Maybe you could add another cover source ? n__n

---

### Post by Yuzem on 2008-08-21
You mean with the music grabber?
The problem is that not all folders with music are albums.

---

### Post by Hells_Dark on 2008-08-21
> **Yuzem said:**
> You mean with the music grabber?
The problem is that not all folders with music are albums.

No, i was talking about the movie grabber.

---

### Post by Yuzem on 2008-08-21
Do you know if the imdb page for the movie with missing cover has a cover?
There are some bugs in the film grabber that I will fix for the next version. For example, the correct replacement of underscore chars (_).

If you could give me an example of a movie that doesn't work and/or suggest a site that could work better that would be great.

Right now I think imdb is the most complete site for this.

There is also another program that works automatically and does practically the same:
[imdb-thumbnailer]("http://www.gtkfiles.org/app.php/imdb-thumbnailer")
It works better with thunar since thunar doesn't move/rename the thumbnail along with the movie. It is the one I'm using now. :)

---

### Post by Gourgi on 2008-08-21
> **Yuzem said:**
> For example, the correct replacement of underscore chars (_).
i had the underscore problem some time ago and i think i solved it using tr

in the film grabber i replaced this 
```

query=$(echo "$avatar_title" | sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')

```
with this
```

query=$(echo $title | tr '_' ' ' | tr '.' ' ' | tr '-' ' '| sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')

```

i hope this helps a little 

and again your app is great, thanks

---

### Post by Yuzem on 2008-08-21
> **Gourgi said:**
> i had the underscore problem some time ago and i think i solved it using tr

in the film grabber i replaced this 
```

query=$(echo "$avatar_title" | sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')

```
with this
```

query=$(echo $title | tr '_' ' ' | tr '.' ' ' | tr '-' ' '| sed -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')

```
Thanks Gourgi. That should work. I will do exactly the same but all with sed. Thats what I did in imdb-thumbnailer.

> **Gourgi said:**
> 
and again your app is great, thanks
You are wellcome. :)

---

### Post by ENigma885 on 2008-08-22
Great Work Yuzem...Thanx

**1.** I have one question; suppose i have *Artist/Album *
but the Artist folder contains more than one Album ..
[COLOR="Red"]**is there a way **[/COLOR]to make the Artist folder show the inside-albums avatars that will look like [[COLOR="Blue"]this[/COLOR]]("http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg")? (the second pic where the folder shows the albums stack on each other)

**2.** It's **[COLOR="Red"]a request[/COLOR]** ..can u give more effort to the GUI? i just feel like it needs to be more organized and apparently u forgot to include the Theme choose step in the GUI process. indeed i wish i could help but i have no idea about making GUI.

Thanx again

---

### Post by Yuzem on 2008-08-22
> **ENigma885 said:**
> Great Work Yuzem...Thanx
Thanks, you're welcome.

> **ENigma885 said:**
> 
**1.** I have one question; suppose i have *Artist/Album *
but the Artist folder contains more than one Album ..
[COLOR="Red"]**is there a way **[/COLOR]to make the Artist folder show the inside-albums avatars that will look like [[COLOR="Blue"]this[/COLOR]]("http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg")? (the second pic where the folder shows the albums stack on each other)
Sadly not. It still can't change folder icons.

> **ENigma885 said:**
> 
**2.** It's **[COLOR="Red"]a request[/COLOR]** ..can u give more effort to the GUI? i just feel like it needs to be more organized and apparently u forgot to include the Theme choose step in the GUI process. indeed i wish i could help but i have no idea about making GUI.

Yes, the next version will have a big gui improvement. Nothing amazing because I'm using zenity for the gui that has many limitations but it will be more powerful and simple.
I didn't forgot about the theme choose step, I decided to sacrifice that in order to have less steps but that will not be a problem in the next version.

---

### Post by Yuzem on 2008-08-26
New version:
```
26.08.08------0.7.0
	+many gui improvements
	+added --icon-size option for nautilus
	+book theme: correction to center the picture for all grabbers except the comic grabber.
	+removed flags: -ag -mg -pg -fg
	+--save-as option was removed
	+book theme splitted in book and book-open themes
	+all themes have been changed, now they are independent scripts
	+folder grabbers (music comic picture etc): update the icon if the folder has changed
	+film grabber: some improvements
	+code cleanup
	+youtube: handle some special chars
	+youtube: icon names have changed
```

---

### Post by Gourgi on 2008-08-26
nice update , UI has more power now!

but... here are some bugs for imdb from UI options:
1 )  "Icons Size" options gives nothing as edit options (i use nautilus)
2 ) where did the 'source' option went in imdb grabber ?? how one can give source folder from UI ?
3 ) where is the 'launcher type' option ? how can i add this ?

[COLOR="Red"]edit[/COLOR]
i tried this, but i have errors
 ```
avatar-factory -g imdb --type --gui
cat: /home/gourgi/.avatar-factory/avatar-launcher: No such file or directory
/usr/local/bin/avatar-factory: line 333: SOURCE_input: bad array subscript
/usr/local/bin/avatar-factory: line 337: SOURCE_input: bad array subscript
/usr/local/bin/avatar-factory: line 344: SOURCE_input: bad array subscript
 does not exist or it is not a directory
 
```

---

### Post by Hells_Dark on 2008-08-26
[B]THX
[/B]
Yes :) I'll take a look at the new version.
I hope the icon-size works ;)

**EDIT** : size has no effect.. They ARE too small. 
Actually, i think the picture itself is bigger, but it still is too small in nautilus. 
We should have a descent size but keeping the zoom at **100%** (because putting a zoom at 200% makes the icons bigger, [but the spaces between icons too (->*ugly*)](http://pix.nofrag.com/6/a/f/a9219de67827cbeee0dd6777d4f27.png) ).
I guess it still is not possible :(. I'm waiting for a (sad) confirmation. 
A size such as [this picture](http://linux.softpedia.com/screenshots/Avatar-Factory_2.jpg) would be so nice..

---

### Post by Yuzem on 2008-08-26
> **Gourgi said:**
> nice update , UI has more power now!

but... here are some bugs for imdb from UI options:
1 )  "Icons Size" options gives nothing as edit options (i use nautilus)
2 ) where did the 'source' option went in imdb grabber ?? how one can give source folder from UI ?
3 ) where is the 'launcher type' option ? how can i add this ?
1 ) Yes, it is happening with all bookmark grabbers: youtube etc... :(
2 ) Bookmarks grabbers don't use a source. You have to set the browser (firefox, opera or epiphany) in the config file. Firefox is the default. For videos in your computer use the film grabber.
3 ) The launcher type option is there for folder grabbers (music comic picture and tv-show). The others use the avatar launcher by default.

> **Gourgi said:**
> 
[COLOR="Red"]edit[/COLOR]
i tried this, but i have errors
 ```
avatar-factory -g imdb --type --gui
cat: /home/gourgi/.avatar-factory/avatar-launcher: No such file or directory
/usr/local/bin/avatar-factory: line 333: SOURCE_input: bad array subscript
/usr/local/bin/avatar-factory: line 337: SOURCE_input: bad array subscript
/usr/local/bin/avatar-factory: line 344: SOURCE_input: bad array subscript
 does not exist or it is not a directory
 
```
You must set the destination, for example:
```
avatar-factory -g imdb --type --gui ~/Desktop
```
Those errors should be more user friendly I will take a look.

> **Hells_Dark said:**
> [B]THX
[/B]
Yes :) I'll take a look at the new version.
I hope the icon-size works ;)

EDIT : size has no effect..
Are you sure? Some times nautilus doesn't update the view correctly. You must close the window and open it again. If that doesn't work try to restart nautilus:
```
killall nautilus
```
> **Hells_Dark said:**
> 
A size such as [this picture](http://linux.softpedia.com/screenshots/Avatar-Factory_2.jpg) would be so nice..
Use 27 for that.

---

### Post by Hells_Dark on 2008-08-26
Wait. I try.

EDIT : Halleluja ! 

> killall nautilus

It worked.

Thanks Yuzem !

EDIT 2 : --name 0 display a name, is it what it should do ?

---

### Post by Yuzem on 2008-08-26
Some times to close and open the nautilus window again works. For me it worked in most of the cases.

> **Hells_Dark said:**
> 
EDIT 2 : --name 0 display a name, is it what it should do ?
No, thats a problem with the new nautilus version. I think that there is no way to fix that since nautilus no longer allows having no names.

If you want to use the background like in the picture you could try:
nautilus > edit > Preferences > text at a side of the icons (I am not sure how it is written in english)

I could also implement an option to have a dot for the name...

---

### Post by Hells_Dark on 2008-08-26
> **Yuzem said:**
> 
If you want to use the background like in the picture you could try:
nautilus > edit > Preferences > text at a side of the icons (I am not sure how it is written in english)


Yes, i've already tried this option. But if the first icons fit well on the background, the next are shifted.

---

### Post by Yuzem on 2008-08-26
Do you mean the first line of icons?
If that is the case I could edit the background. I am not in my computer right now to test it myself.

---

### Post by Hells_Dark on 2008-08-26
Yes, the first line is good and then, no.
So i don't think editing the background could fix it ;)

---

### Post by Hells_Dark on 2008-08-26
[double post]

---

### Post by Yuzem on 2008-08-26
Try the attached file.

---

### Post by Hells_Dark on 2008-08-27
It works perfectly.
Thanks !

---

### Post by Nonno Bassotto on 2008-08-27
Sorry I have not been here for long... Thank you for all the improvements! Sadly the Nautilus team seems to work against you :)

If I understand correctly you have found a hack to produce icon with the suitable size for Nautilus. Still I can't edit the Icon size option, not only with the bookmark grabbers, but with music, film and picture too. Is it there for a future implementation?

---

### Post by Hells_Dark on 2008-08-27
> **Nonno Bassotto said:**
>  Still I can't edit the Icon size option, not only with the bookmark grabbers, but with music, film and picture too. Is it there for a future implementation?
What do you mean ? You can change the icon size now.

Example :
> avatar-factory -g film --type 0 --icon-size 27 --name 2 -t dvd-1 /media/HD/Data/Films/.source /media/HD/Data/Films/

I have big icons now :)

---

### Post by Nonno Bassotto on 2008-08-27
I just tried the command line way and it works!!! :) Still I think there's something wrong with the gui, since it doesn't let me choose the icon size. Moreover the icon-size option has no effect when used with the music grabber and the --folders option.

---

### Post by Nonno Bassotto on 2008-08-27
Let me add also that I have some problem with the anobii and imdb grabbers: both don't find any link. I'm using Firefox; possibly it has something to do with Firefox 3 and its new way to manage bookmarks? I think they are inside a sqlite file now... I can save a html file with all my links, but I don't know how to tell Avatar-Factory to use that file.

Edit: I could trick Avatar-Factory into importing the bookmarks by manually substituting the bookmarks.html file, but I'm not sure if a more elegant solution exists.

I should also add that I have some problems with bookmarks whose contains an apostrophe ('). In the html file saved  by Firefox it is escaped as & # 39; (no spaces) but it is not correctly replaced by Avatar-Factory.

---

### Post by Nonno Bassotto on 2008-08-29
I see Anobii published an [API]("http://api.anobii.com/api/api_home.php") to retrieve user data within an application. If you are interested I may investigate on that and try to integrate that into AvatarFactory. Basically you just call a dedicated URL and get the data you want about books in XML.

---

### Post by Crafty Kisses on 2008-08-29
Nice tutorial! Thanks for all the tips and what not. :)

---

### Post by Yuzem on 2008-08-29
> **Nonno Bassotto said:**
> Sorry I have not been here for long... Thank you for all the improvements! Sadly the Nautilus team seems to work against you :)
Hello Nonno! Nice to see you here again. Sorry I didn't answer before. I didn't get a notification...
Yes, a lot of things got broken with the latest nautilus...

> **Nonno Bassotto said:**
> I just tried the command line way and it works!!! :) Still I think there's something wrong with the gui, since it doesn't let me choose the icon size. 
I can't reproduce the problem. It is working fine on my computer. I will try again in another computer.
> **Nonno Bassotto said:**
> Moreover the icon-size option has no effect when used with the music grabber and the --folders option.
That is a bug. :(

> **Nonno Bassotto said:**
> Let me add also that I have some problem with the anobii and imdb grabbers: both don't find any link. I'm using Firefox; possibly it has something to do with Firefox 3 and its new way to manage bookmarks? I think they are inside a sqlite file now... I can save a html file with all my links, but I don't know how to tell Avatar-Factory to use that file.

Edit: I could trick Avatar-Factory into importing the bookmarks by manually substituting the bookmarks.html file, but I'm not sure if a more elegant solution exists.
Yes, [here]("http://ubuntuforums.org/showpost.php?p=5552465&postcount=11")

> **Nonno Bassotto said:**
> 
I should also add that I have some problems with bookmarks whose contains an apostrophe ('). In the html file saved  by Firefox it is escaped as & # 39; (no spaces) but it is not correctly replaced by Avatar-Factory.
I fixed that for the youtube grabber in the latest version, I will do the same for the others.

> **Nonno Bassotto said:**
> I see Anobii published an [API]("http://api.anobii.com/api/api_home.php") to retrieve user data within an application. If you are interested I may investigate on that and try to integrate that into AvatarFactory. Basically you just call a dedicated URL and get the data you want about books in XML.
Do you mean, to create a gui dialog with the data or something like that?

---

### Post by Nonno Bassotto on 2008-08-30
> **Yuzem said:**
> Yes, [here]("http://ubuntuforums.org/showpost.php?p=5552465&postcount=11")

Fine, this solves the bookmarks issue. :) Maybe you could mention it in the instructions.

> **Yuzem said:**
> Do you mean, to create a gui dialog with the data or something like that?

What I mean is that now one could create a anobii-account grabber. A user could give the id of his account to the grabber and avatar-factory would create the avatars for all books in the shelf, without the need to create a bookmark for each book.

[This page]("http://api.anobii.com/api/api_method.php?id=A1") shows that, once you have a Anobii API account, you can use a dedicated URL to retrieve the list of all books in the shelf, in XML format. Actually for each book you only get the id; then you use [this other method]("http://api.anobii.com/api/api_method.php?id=B1") to get the title and the cover.

---

### Post by Nonno Bassotto on 2008-08-30
By the way, one could use something like [XMLStarlet]("http://xmlstar.sourceforge.net/") to parse the XML output, so the new grabber would be very simple. This would add a new dependency to avatar-factory, but one can just ignore it if he doesn't need the new grabber. Moreover the same thing could be done for other social websites (like IMDB itself, or flixster...) as soon as they provide a similar API.

---

### Post by Yuzem on 2008-08-30
> **Nonno Bassotto said:**
> Fine, this solves the bookmarks issue. :) Maybe you could mention it in the instructions.
I will. :)

> **Nonno Bassotto said:**
> 
What I mean is that now one could create a anobii-account grabber. A user could give the id of his account to the grabber and avatar-factory would create the avatars for all books in the shelf, without the need to create a bookmark for each book.

[This page]("http://api.anobii.com/api/api_method.php?id=A1") shows that, once you have a Anobii API account, you can use a dedicated URL to retrieve the list of all books in the shelf, in XML format. Actually for each book you only get the id; then you use [this other method]("http://api.anobii.com/api/api_method.php?id=B1") to get the title and the cover.
Oh, I see... I am not sure how to implement this since I am planning to change the way bookmark grabbers work.
Now it is:
```
avatar-factory -g anobii destination
```
I want to implement something like:
```
avatar-factory -g anobii source destination
```
Where source could be firefox, opera, epiphany, a list of links file and I could add your idea here. This way no additional grabber will be needed.

> **Nonno Bassotto said:**
> By the way, one could use something like [XMLStarlet]("http://xmlstar.sourceforge.net/") to parse the XML output, so the new grabber would be very simple. This would add a new dependency to avatar-factory, but one can just ignore it if he doesn't need the new grabber. Moreover the same thing could be done for other social websites (like IMDB itself, or flixster...) as soon as they provide a similar API.
XMLStarlet seems great. I didn't know about it.
I read a little the docs and it seems a like complex (I have almost no experience in XML)
I think that I can use sed for this.
Do you mean for example, to grab the links from a page like [this]("http://www.anobii.com/cyesuta/books")
I can get the links with:
```
wget -qO - http://www.anobii.com/cyesuta/books | sed -e 's/<a href="/\n/g' -e '/\/books\//!d' -e 's/".*$//g' | sed -e '/\/books\//!d' -e 's|^|http://www.anobii.com|'
```

---

### Post by Nonno Bassotto on 2008-08-30
I think your way to extract the data will not work with more than ten books, since they will end up on the next pages.

I think what you need to parse XML is just something like the following command
```

xmlstarlet sel -t -m "//item" -v "@id" -n shelf.xml

```
This should output the list of ids, one for each line. By the way, I just copied the second example [here]("http://arstechnica.com/articles/columns/linux/linux-20051115.ars/2").

Anyway, mine was just a suggestion, to avoid manual parsing of the XML (or HTML) file.

---

### Post by Hells_Dark on 2008-08-31
When i add movies, the icon stay small for a while.. weird.
killall nautilus fix it.. again :/

---

### Post by Yuzem on 2008-08-31
> **Nonno Bassotto said:**
> I think your way to extract the data will not work with more than ten books, since they will end up on the next pages.[/URL]
You are right, twelve actually.

[QUOTE=Nonno Bassotto;5697028]
I think what you need to parse XML is just something like the following command
```

xmlstarlet sel -t -m "//item" -v "@id" -n shelf.xml

```
This should output the list of ids, one for each line. By the way, I just copied the second example [here]("http://arstechnica.com/articles/columns/linux/linux-20051115.ars/2").

Anyway, mine was just a suggestion, to avoid manual parsing of the XML (or HTML) file.
If I understand this correctly, first I use the user id to get the books ids and then I get the books proprieties with the books ids but how do I get the user id?

> **Hells_Dark said:**
> When i add movies, the icon stay small for a while.. weird.
killall nautilus fix it.. again :/
Yes, this is because the icon size option is set for each file not for all files in a specific folder. This is how nautilus works.
It is strange that you have to killall nautilus every time. Try closing all nautilus windows, then add a movie and then open the avatars folder.
That works in my computer, even closing the window and open it again works. Some times you just have to wait a little.

---

### Post by Nonno Bassotto on 2008-09-01
> **Yuzem said:**
> If I understand this correctly, first I use the user id to get the books ids and then I get the books proprieties with the books ids but how do I get the user id?

Uhm... good question! :) I guess it is part of the URL of your own library. when I log into Anobii my library URL is
```

http://www.anobii.com/017109edf5f0b586a5/books

```
so I guess that my id is
```

017109edf5f0b586a5

```
I think you can ask for the id as a parameter, rather than the username. The only way to know for sure is register and try, if you want

---

### Post by Nonno Bassotto on 2008-09-01
By the way, I tried setting the icon size with the GUI on another PC and had the same problem. When I double-click the icon size line, the dialog flickers like if it's being reloaded, but I get no choice of the size.

Another thing: it seems that I'm not able to set the cover for a film avatar anymore. Last time I checked I could do this just by dragging the correct image over the avatar; is this another bug coming from Nautilus "improvement"?

---

### Post by Yuzem on 2008-09-01
> **Nonno Bassotto said:**
> Uhm... good question! :) I guess it is part of the URL of your own library. when I log into Anobii my library URL is
```

http://www.anobii.com/017109edf5f0b586a5/books

```
so I guess that my id is
```

017109edf5f0b586a5

```
I think you can ask for the id as a parameter, rather than the username. The only way to know for sure is register and try, if you want
mmm... if I ask for the user id I will have to do a lot of explanations about how to get it. I will ask for the user name, it is more intuitive.
I will have to use sed then.

> **Nonno Bassotto said:**
> By the way, I tried setting the icon size with the GUI on another PC and had the same problem. When I double-click the icon size line, the dialog flickers like if it's being reloaded, but I get no choice of the size.
Yes it is already fixed (next version). It wasn't happening in mine pc because it doesn't happen if there is a value. Try to manually edit the config files (~/.avatar-factory/grabbers/*) to add a value and the GUI should work.

> **Nonno Bassotto said:**
> 
Another thing: it seems that I'm not able to set the cover for a film avatar anymore. Last time I checked I could do this just by dragging the correct image over the avatar; is this another bug coming from Nautilus "improvement"?
Sadly, yes. :(
The god part is that it actually works, it just doesn't get updated immediately.
You can check it:
```
eog "$(grep 'Icon=' "path/to/avatar" | sed 's/Icon=//')"
```
Replace "path/to/avatar"

---

### Post by Nonno Bassotto on 2008-09-01
> **Yuzem said:**
> The god part is that it actually works, it just doesn't get updated immediately.

...I should always killall nautilus before posting anything!! :)

---

### Post by Nonno Bassotto on 2008-09-01
Well, I don't want to overwhelm you, but by casual browsing I just found [BUC]("http://buc.opensource.tk/"). It is a tool to create a GUI for bash scripts, easier to use and with nicer results than zenity.

On Ubuntu you can install it by the repository
```

deb http://buc.billera.eu/ubuntu/ binary/

```
or
```

deb http://buc.billera.eu/ubuntu64/ binary/

```
if you have 64-bit processor.

Basically you just create an XML file containing the list of buttons, comboboxes and so on, name it avatar-factory.mc and run it by
```

buc avatar-factory.mc

```
Unfortunately the documentation is in italian only. Luckily, though, this is my mother language. :)

In a few minutes I created the following basic GUI
```

 <?xml version="1.0"?>
<config>
<tab>
<title>
echo "Source mode"
</title>

<label>
echo "Choose the grabber"
</label>
<combobox var="grabber">
echo "comic"
echo "mame"
echo "film"
echo "music"
echo "picture"
echo "tv-show"
</combobox>

<label>
echo "Choose the source folder"
</label>
<file var="source" mode="dir">
</file>

<label>
echo "Choose the destination folder"
</label>
<file var="destination" mode="dir">
</file>

<label>
echo "Choose the icon size (27 = 128x128)"
</label>
<text var="size">
echo "27"
</text>

<button title="OK">
avatar-factory -g $grabber $source $destination --icon-size $size
</button>

<textlog>
</textlog>
</tab>

<tab>
<title>
echo "Bookmark mode"
</title>

<label>
echo "Choose the grabber"
</label>
<combobox var="grabber">
echo "anobii"
echo "imdb"
echo "youtube"
</combobox>

<label>
echo "Choose the destination folder"
</label>
<file var="destination" mode="dir">
</file>

<label>
echo "Choose the icon size (27 = 128x128)"
</label>
<text var="size">
echo "27"
</text>

<button title="OK">
avatar-factory -g $grabber $destination --icon-size $size
</button>

<textlog>
</textlog>
</tab>
</config>

```

Well, if you want, have a try. My GUI was just a test, so it doesn't support themes and saving settings, but I think the tool is worth a look.

---

### Post by Yuzem on 2008-09-01
> **Nonno Bassotto said:**
> Well, I don't want to overwhelm you, but by casual browsing I just found [BUC]("http://buc.opensource.tk/"). It is a tool to create a GUI for bash scripts, easier to use and with nicer results than zenity.
I have been looking for an application like that for a long time.
There are other similar projects:
[http://bror.org/mark/software/gtkbash/](http://bror.org/mark/software/gtkbash/)
and:
[http://www.turtle.dds.nl/gtk-server/](http://www.turtle.dds.nl/gtk-server/)
I Could not install them...
This apps share one problem, they are not available from the repositories by default. I don't like that since it would make avatar-factory harder to install.

Buc seems more powerful and easier than zenity but it doesn't support themes. That is very bad. :(
Nevertheless I did install it and played a little it is a very interesting tool.

I would like to have an application like that but with theme support. :)

---

### Post by Nonno Bassotto on 2008-09-02
Well, I don't think that BUC does not support themes, but it uses QT. If you don't mind, I played a bit and got a new interface. This one has translation support (well, just italian and english), a help, can load default options and has a "Save default" button which for now does nothing and sits there in all its unusefulness. :)

There are still many problems, for example
1) My name is hardcoded since I had a little problem with the home dir.
2) I didn't put apices, so I'm quite sure it won't work with directories with spaces.

Anyway, here it is
```

 <?xml version="1.0"?>
<config>
	<tab>
	
		<global var="language">
			temp=$(locale | grep LANG=)
			temp=${temp#*=}
			echo ${temp%_*}
		</global>
		
		<global var="string0">
			case $language in
			it) echo "Modalità cartella";;
			*) echo "Folder mode";;
			esac
		</global>
		<global var="string1">
			case $language in
			it) echo "Scegli l'azione";;
			*) echo "Choose the grabber";;
			esac
		</global>
		<global var="string2">
			case $language in
			it) echo "Scegli la cartella origine";;
			*) echo "Choose the source folder";;
			esac
		</global>
		<global var="string3">
			case $language in
			it) echo "Scegli la cartella destinazione";;
			*) echo "Choose the destination folder";;
			esac
		</global>
		<global var="string4">
			case $language in
			it) echo "Lascia vuoto per usare le scelte di default";;
			*) echo "Leave empty to use default";;
			esac
		</global>
		<global var="string5">
			case $language in
			it) echo "Scegli la dimensione delle icone";;
			*) echo "Choose the icon size";;
			esac
		</global>
	
		<title>
			echo $string0
		</title>
	
		<label>
			echo $string1
		</label>
		<combobox var="grabberf">
			echo "comic"
			echo "mame"
			echo "film"
			echo "music"
			echo "picture"
			echo "tv-show"
		</combobox>
	
		<label>
			echo $string2
			echo $string4
		</label>
		<file var="source_chosen" mode="dir">
		</file>
	
		<label>
			echo $string3
			echo $string4
		</label>
		<file var="destination_chosenf" mode="dir">
		</file>
	
		<label>
			echo $string5 "(27 = 128x128)"
			echo $string4
		</label>
		<text var="size_chosenf">			
		</text>
	
		<button title="Save default">
		</button>
	
		<button title="OK">
			path="/home/andrea/.avatar-factory/grabbers/"$grabberf
			if [ -z $source_chosen ]
				then if [ -e $path ]
					then temp1=$(cat $path | grep SOURCE_input=)
						temp1=${temp1#*=\"}
						source=${temp1%\"*}
					fi
				else source=$source_chosen
			fi
			if [ -z $destination_chosenf ]
				then if [ -e $path ]
					then temp1=$(cat $path | grep "SOURCE_input\[1\]=")
						temp1=${temp1#*=\"}
						destination=${temp1%\"*}
					fi
				else destination=$destination_chosenf
			fi
			if [ -z $size_chosenf ]
				then if [ -e $path ]
					then temp1=$(cat $path | grep icon_size)
						size=${temp1#*=}
					else size="27"
				fi
				else size=$size_chosenf
			fi
			avatar-factory -g $grabberf $source $destination --icon-size $size
		</button>
	
		<textlog>
		</textlog>
	</tab>

	<tab>
	
		<global var="language">
			temp=$(locale | grep LANG=)
			temp=${temp#*=}
			echo ${temp%_*}
		</global>
	
		<global var="string0">
			case $language in
				it) echo "Modalità segnalibro";;
				*) echo "Bookmark mode";;
			esac
		</global>
		<global var="string1">
			case $language in
				it) echo "Scegli l'azione";;
				*) echo "Choose the grabber";;
			esac
		</global>
		<global var="string2">
			case $language in
				it) echo "Scegli la cartella origine";;
				*) echo "Choose the source folder";;
			esac
		</global>
		<global var="string3">
			case $language in
				it) echo "Scegli la cartella destinazione";;
				*) echo "Choose the destination folder";;
			esac
		</global>
		<global var="string4">
			case $language in
				it) echo "Lascia vuoto per usare le scelte di default";;
				*) echo "Leave empty to use default";;
			esac
		</global>
		<global var="string5">
			case $language in
				it) echo "Scegli la dimensione delle icone";;
				*) echo "Choose the icon size";;
			esac
		</global>
	
		<title>
			echo $string0
		</title>
	
		<label>
			echo $string1
		</label>
		<combobox var="grabberb">
			echo "anobii"
			echo "imdb"
			echo "youtube"
		</combobox>
	
		<label>
			echo $string2
			echo $string4
		</label>
		<file var="destination_chosenb" mode="dir">
		</file>
	
		<label>
			echo $string5 "(27 = 128x128)"
			echo $string4
		</label>
		<text var="size">
		</text>
	
		<button title="Save default">
		</button>
	
		<button title="OK">
			path="/home/andrea/.avatar-factory/grabbers/"$grabberb
			if [ -z $destination_chosenb ]
				then if [ -e $path ]
					then temp1=$(cat $path | grep "SOURCE_input\[1\]=")
						temp1=${temp1#*=\"}
						destination=${temp1%\"*}
					fi
				else destination=$destination_chosenb
			fi
			if [ -z $size_chosenb ]
				then if [ -e $path ]
					then temp1=$(cat $path | grep icon_size)
						size=${temp1#*=}
					else size="27"
				fi
				else size=$size_chosenb
			fi
			avatar-factory -g $grabberb $destination --icon-size $size
		</button>
	
		<textlog>
		</textlog>
	</tab>

	<tab>
	
		<global var="language">
			temp=$(locale | grep LANG=)
			temp=${temp#*=}
			echo ${temp%_*}
		</global>
	
		<global var="string0">
			case $language in
				it) echo "Aiuto";;
				*) echo "Help";;
			esac
		</global>
		<global var="string1">
			case $language in
				it) echo "Scegli l'azione";;
				*) echo "Choose the grabber";;
			esac
		</global>
	
		<title>
			echo $string0
		</title>
	
		<label>
			echo $string1
		</label>
		<combobox var="grabberh">
			echo "anobii"
			echo "comic"
			echo "film"
			echo "imdb"
			echo "mame"
			echo "music"
			echo "picture"
			echo "tv-show"
			echo "youtube"
		</combobox>
	
		<button title="Help">
			avatar-factory -g $grabberh --help
		</button>
	
		<textlog>
		</textlog>
	
	</tab>
</config>

```

Here is a screenshot of how it looks.

By the way, I'm not trying to steal your work, I'm just playing a bit and posting here the results. If for any reason you don't want me to post this alternative GUI, just PM me or write me here. :)

---

### Post by Yuzem on 2008-09-02
> **Nonno Bassotto said:**
> Well, I don't think that BUC does not support themes, but it uses QT. 
Yes I remember seen "Q" something at the command line when running it.
I meant that doesn't support gtk themes.

> **Nonno Bassotto said:**
> 
If you don't mind, I played a bit and got a new interface.
Of course I don't mind... play all you want :)
> **Nonno Bassotto said:**
> 
This one has translation support (well, just italian and english)
Thats great, I am planning to include translation support for the help pages in a future version.

> **Nonno Bassotto said:**
> 
By the way, I'm not trying to steal your work, I'm just playing a bit and posting here the results. If for any reason you don't want me to post this alternative GUI, just PM me or write me here. :)
There is absolutely no problem. I have also thought about a gui design before choosing zenity.
This is what I would try to do if there were an application like buc for gtk:
[[IMG]http://img382.imageshack.us/img382/4268/avatarfactorymockupou2.th.jpg[/IMG]](http://img382.imageshack.us/my.php?image=avatarfactorymockupou2.jpg)
The about tab shows a description (the help page) Avatars that are not configured do not show a checkbox. The avatar grabber do not have an option tab.

---

### Post by Nonno Bassotto on 2008-09-02
Your mockup looks great, but is far beyond what BUC can do for now...

Anyway I cleaned the interface up a bit, this is last version. It now supports themes and types, reads the default (hopefully) but still can't write it and has a new preference tab. It still does not work with spaces.
What remains to do:
1) Make it work with spaces
2) Make it able to save settings
3) Use sed instead of current implementation

By the way, what is the way to use sed to remove everything up to string1 and after string2 (both included)? That is, from
"ajdksdjalstring1relevanttextstring2dspadokas"
I'd like to obtain "relevanttext".

I feel like I'm spamming your thread, maybe I should open a new one...

---

### Post by Yuzem on 2008-09-02
> **Nonno Bassotto said:**
> Your mockup looks great, but is far beyond what BUC can do for now...
Yes, thats what I thought.

> **Nonno Bassotto said:**
> 
Anyway I cleaned the interface up a bit, this is last version. It now supports themes and types, reads the default (hopefully) but still can't write it and has a new preference tab. It still does not work with spaces.
What remains to do:
1) Make it work with spaces
2) Make it able to save settings
3) Use sed instead of current implementation

It is getting better. :)

> **Nonno Bassotto said:**
> 
By the way, what is the way to use sed to remove everything up to string1 and after string2 (both included)? That is, from
"ajdksdjalstring1relevanttextstring2dspadokas"
I'd like to obtain "relevanttext".
This:
```
echo ajdksdjalstring1relevanttextstring2dspadokas | sed -e 's/.*string1//' -e 's/string2.*//'
```

> **Nonno Bassotto said:**
> 
I feel like I'm spamming your thread, maybe I should open a new one...
It is ok for me, it is related to avatar-factory but it is your choice. You are welcome here :)

By the way, anyone know what happened to gnomefiles?
When it will be online again? I think they have been hacked...

---

### Post by Yuzem on 2008-09-03
gnomefiles is still off line...
I will post the new version here, I didn't do a lot of testing. If someone wants to try it out and report bugs that would be great.

```
03.09.08------0.7.5
	+removed assisted x-mame installation.
	+fixed icon-size option in the gui
	+fixed bug in recreate folder structure mode
	+gui: music widget enable/disable
	+gui: launcher configuration
	+launchers configuration file has changed. The old config is obsolete.
	+gui: source configuration for bookmark grabbers
	+help files updated
	+name decoding for all bookmarks grabbers
	+anobii: account grabber using ~username as the source
	+fixed problem with icon-size when used with recreate folders
	+when running from the cli if there are no destination folder the gui generated config will be used. Now you can do "avatar-factory -g grabber"
```
	+fixed problem with book-open theme (--comic-bookmark)

---

### Post by Nonno Bassotto on 2008-09-03
Thank you for the update :). I think you already know, the anobii grabber just displays the first 12 books in the shelf. By the way, the username I had to use was exactly the code I gave you before for the user_id.

---

### Post by Nonno Bassotto on 2008-09-03
Ok, this should be the last spam for a while. I finished the alternative GUI. If anyone wants to try it (and tell me if it works for you), I recall here how.

First, you should have avatar-factory 7.5 installed, which is plausible if you are reading here.
Second, you should install BUC. You can do that from the repository
```

deb http://buc.billera.eu/ubuntu/ binary/

```
for 32 bit or
```

deb http://buc.billera.eu/ubuntu64/ binary/

```
for 64 bit. If you don't want to mess with the repositories, you find [here]("http://buc.billera.eu/portale/html/modules.php?name=Downloads&d_op=viewdownload&cid=2") the debs.
Last, download and uncompress the attached zip, and run the GUI with
```

buc avatar-factory.mc

```
Alternatively use the attached deb and you will get an entry in the Applications menu.

You can see the interface (in italian) in the attached screenshot. So here is what it does:
- Use avatar-factory on the fly or save default settings
- Mixed behaviour is allowed: you can modify some setting and use your saved default for the others.
- Save global preferences, like the music application
- Displays help for the grabbers
- Available in english and italian

And here is what it does not:
- Use some options (for instance delete broken links). This is a problem of space: once BUC is improved, so that I can dispose better the buttons and so on, I will add more options.
- Grabbers which are supposed to work with multiple folders, like film, with my GUI are limited to one folder at a time.
- The defaults for the grabbers are saved in a different folder than Yuzem's GUI. My first version was reading Yuzem files, but as soon as I added the option to write, I decided to use my own files, to avoid to mess with the functionality of the original program.
- The only exception to the above is that I modify the file ~/.avatar-factory/general containing the general options. I could not avoid it, so it is particularly important that I'm told if there are any bugs with this, since I don't want to create problems with the original program.

If I find some bugs I will just update the version here. Hope you like it. :)

EDIT (revision=2): I corrected a bug which prevented the use of the option -add for music avatars, and added a Check for updates button.
New translations in spanish, danish, dutch, swedish and (brazilian) portuguese available thanks to harlan, cmay, lode, Kvark and pedro3005 respectively.

---

### Post by Yuzem on 2008-09-04
> **Nonno Bassotto said:**
> I think you already know, the anobii grabber just displays the first 12 books in the shelf.
No, thats a bug. It is fixed now, I hope... re download the file from the previous post.

> **Nonno Bassotto said:**
> Ok, this should be the last spam for a while. I finished the alternative GUI. If anyone wants to try it (and tell me if it works for you), I recall here how.
I tried it, It is working for me but I didn't do a lot of testings. It is much faster for running one grabber at a time or for example if you just want to pick a source and a destination and go!

---

### Post by Nonno Bassotto on 2008-09-04
> **Yuzem said:**
> No, thats a bug. It is fixed now, I hope... re download the file from the previous post.

Wonderful!! No more keeping track of my Anobii books with bookmarks :) By the way, for the problem with the ' character, I have no problems now when using bookmark, but the character just disappears when using the account.

---

### Post by Yuzem on 2008-09-04
> **Nonno Bassotto said:**
> I have no problems now when using bookmark, but the character just disappears when using the account.
Try it again, I think that it is fixed now. :)

---

### Post by Truedream on 2008-09-05
i need some help please.

When i run the film grabber (source and the destination folders are same where my movies are stored) it runs for a while and creates the icons in ~/.avatar-factory/icons/theme. is this normal or is it supposed to change the folder icons in my movies folder?

EDIT: nvm i got it working thx :)

---

### Post by Hells_Dark on 2008-09-05
Truedream > avat-factory creates shortcuts.

---

### Post by Nonno Bassotto on 2008-09-07
> **Yuzem said:**
> Try it again, I think that it is fixed now. :)

Actually with the new version each book name ends with "<span class="

By the way, I've updated my GUI with some bug fixes and translations.

---

### Post by Yuzem on 2008-09-07
It isn't happening with all books. This account works without problems:
```
avatar-factory -g anobii ~cyesuta ~/Desktop
```

And this works until book 36:
```
avatar-factory -g anobii ~arcanewinter ~/Desktop
```

I did test the latest version before releasing it but I did not go beyond book 35. :(

I will take a look.
Thanks for the feedback. :)

---

### Post by Nonno Bassotto on 2008-09-07
If you want to test, my account is ~buendia

---

### Post by Yuzem on 2008-09-07
It seems empty:
[http://www.anobii.com/buendia](http://www.anobii.com/buendia)

---

### Post by Nonno Bassotto on 2008-09-08
The link you gave me actually opens my library with 111 books. :confused:

---

### Post by Yuzem on 2008-09-08
Thats strange, here it says: "No hay libros en esta estantería aún"
It means: There are no books on this shelf yet.

Oh, wait... it says there that you have more books in other languages.
mmm... but I don't know how to test it with avatar-factory since it doesn't find any book.

---

### Post by Nonno Bassotto on 2008-09-08
It is strange. It works for me, the only problem is the name of the books it produces.

---

### Post by Yuzem on 2008-09-08
Could you give me the command line output?:
```
avatar-factory -g anobii ~cyesuta ~/test
```
Or if you prefer just tell me whats wrong with the names. Is the span problem solved?

Edit: Something strange happened, I did write before with a new release to fix the span problem but the post isn't there...

---

### Post by Yuzem on 2008-09-08
Another re release of the latest version:
+fixed problem with book-open theme (--comic-bookmark)
+fixed problem with custom launchers
+fixed source not being displayed in the gui for some grabbers
+fixed name problem with anobii grabber

---

### Post by Nonno Bassotto on 2008-09-08
OK, now the span problem is fixed. :) There is just a problem with book names beginning with a long space, but that's not a great deal. Thank you!

---

### Post by Hells_Dark on 2008-09-09
Keep up the good job Yuzem !

---

### Post by Yuzem on 2008-09-10
> **Hells_Dark said:**
> Keep up the good job Yuzem !
Thanks, here there is another one, the spaces at the beginning problem is fixed now.

---

### Post by mocha on 2008-09-11
This is really cool!  Thanks!

---

### Post by Nonno Bassotto on 2008-09-11
Wow, now I have no complaints whatsoever! :)
By the way, what are your plans for the future? Star ratings? Other social network grabbers? Something else?

---

### Post by Hells_Dark on 2008-09-12
Sometimes, as i said before, i don't have any icon for a movie.
But maybe another day, the database could update, and a icon could be available. Maybe you could do a kind of save for icons without cover, and an update function ^^'
OK, just dreaming :P

---

### Post by Yuzem on 2008-09-13
> **mocha said:**
> This is really cool!  Thanks!
You are welcome. :)
> **Nonno Bassotto said:**
> Wow, now I have no complaints whatsoever! :)
By the way, what are your plans for the future? Star ratings? Other social network grabbers? Something else?
I have many things in the "to do" list but I am trying to not spend much time on this anymore as I want to spend more time in other things.

The star ratings thing has been in the to do list since the beginning. 

Also a deviantart grabber would be very nice. I have a lot of artist in my bookmarks that I have bookmarked to explore later. The idea is to use the photo theme to create one avatar by artist displaying the 3 most popular works for every artist.

Another idea is "automatic comic bookmarking" For example, you open a comic, got to page 35, and when when you close the comic the avatar will magically change to that page.

Other thing that I would like is an html output option. This feature will bring the avatars to web browsers in addition to having them on the file browser. This has some advantages, for example it will allow to have a flat view but separated by groups and a sidebar to list all groups, this is like picasa does.

Anyways... I don't know if any of this will ever be implemented and if it does, I don't know when...

> **Hells_Dark said:**
> Sometimes, as i said before, i don't have any icon for a movie.
But maybe another day, the database could update, and a icon could be available. Maybe you could do a kind of save for icons without cover, and an update function ^^'
OK, just dreaming :P
That should be easy, I will take a look, if there is no problems it will be in the next version.

---

### Post by sir_blargh on 2008-09-13
Yuzem,

Just downloaded this (v 0.7.5) yesterday and it is awesome!  Thanks for creating this!  

A few questions:

1)  The --icon-size option increases the size of the icon in the nautilus window, but the original icon is still only 128px.  For instance I run "avatar-factory -g film --icon-size 40" and in the ~/.avatar-factory/icons/film/dvd dir, all of those have a property of 128px but in the resulting Avatar directory the icons are blurry.  Am i doing something wrong?

2)  avatar-factory -g film --help shows:
```
To change the video thumbnail instead of creating the avatar:
                avatar-factory -g film --save-as thumbnails movie.avi
```

  This is ideally what I'd like to do.  So I execute "avatar-factory -g film --save-as thumbnails ~/Videos/Movies/movie.avi" and I get "/home/scott/Videos/Movies/movie.avi does not exist or it is not a directory"  But then if I point it to the directory, I get:  "--save-as is invalid". 

Thanks for your help, this is a very cool program for sure!

---

### Post by Gourgi on 2008-09-13
> **Yuzem said:**
> 
> 
Sometimes, as i said before, i don't have any icon for a movie.
But maybe another day, the database could update, and a icon could be available. Maybe you could do a kind of save for icons without cover, and an update function ^^'

That should be easy, I will take a look, if there is no problems it will be in the next version.

about that yuzem, you can use the default 'no poster' image from imdb 
[http://ia.media-imdb.com/media/imdb/01/I/37/58/83/10.gif](http://ia.media-imdb.com/media/imdb/01/I/37/58/83/10.gif)
i think it is a good icon representing the film's poster status.
of course you don't need to grab it all the time.
a check function if there is a poster image else the default 'no poster' image will be used , should be enough.

there is another thing i'd like to mention : 
if you try the film grabber for a large amount of films , 300-400 for example , then google thinks you have some kind of virus/mallware installed and requires CAPTCHA for google-search for both images ad web.
maybe you could and a delay option , (sleep x seconds ... whatever) just to avoid this. Of course it will require more time to complete image grabbing but surely you don't have to run the task twice or more.

---

### Post by Yuzem on 2008-09-13
> **sir_blargh said:**
> Yuzem,
Just downloaded this (v 0.7.5) yesterday and it is awesome!  Thanks for creating this!  
You are welcome :)

> **sir_blargh said:**
> 
1)  The --icon-size option increases the size of the icon in the nautilus window, but the original icon is still only 128px.  For instance I run "avatar-factory -g film --icon-size 40" and in the ~/.avatar-factory/icons/film/dvd dir, all of those have a property of 128px but in the resulting Avatar directory the icons are blurry.  Am i doing something wrong?
The --icon-size option is independent from the icons resolution which is determinate by the themes. It is more a display size option that only works for nautilus.
All themes have a size of 128px with the exception of the "shadow_hq" theme that is 256px large.
--icon-size "40" is much more than 128, you should use a value of "27"

> **sir_blargh said:**
> 
2)  avatar-factory -g film --help shows:
```
To change the video thumbnail instead of creating the avatar:
                avatar-factory -g film --save-as thumbnails movie.avi
```

  This is ideally what I'd like to do.  So I execute "avatar-factory -g film --save-as thumbnails ~/Videos/Movies/movie.avi" and I get "/home/scott/Videos/Movies/movie.avi does not exist or it is not a directory"  But then if I point it to the directory, I get:  "--save-as is invalid". 

I forgot to remove that in the film grabber help section. The --save-as option was removed in version 0.7 since I released imdb-thumbnailer:
[http://ubuntuforums.org/showthread.php?p=5780989](http://ubuntuforums.org/showthread.php?p=5780989)
imdb-thumbnailer is much better for that and it works automatically. It is also compatible with avatar-factory themes but they don't look very good on nautilus since it doesn't detect transparency in thumbnails.

> **Gourgi said:**
> about that yuzem, you can use the default 'no poster' image from imdb 
[http://ia.media-imdb.com/media/imdb/01/I/37/58/83/10.gif](http://ia.media-imdb.com/media/imdb/01/I/37/58/83/10.gif)
i think it is a good icon representing the film's poster status.
of course you don't need to grab it all the time.
a check function if there is a poster image else the default 'no poster' image will be used , should be enough.
Done, it is on the testing version.

> **Gourgi said:**
> 
there is another thing i'd like to mention : 
if you try the film grabber for a large amount of films , 300-400 for example , then google thinks you have some kind of virus/mallware installed and requires CAPTCHA for google-search for both images ad web.
maybe you could and a delay option , (sleep x seconds ... whatever) just to avoid this. Of course it will require more time to complete image grabbing but surely you don't have to run the task twice or more.
I did something different. If google fails, then use yahoo! It is also on the testing version if anyone want to test...

I have fixed another problem with the --comic-bookmark option. It is the last add to the 0.7.5 version. It comes in all flavors and it can be downloaded from:
[https://launchpad.net/avatar-factory/+download](https://launchpad.net/avatar-factory/+download)

Attached is the testing version which has:
	+yahoo fallback for the film grabber
	+film grabber: changed the no cover icon
	+film grabber: detect if there is a cover for a movie wich had no cover before

---

### Post by Yuzem on 2008-09-13
I forgot to say: for the icons with no cover to be updated if imdb get updated, icons created with older version must be deleted.

---

### Post by Hells_Dark on 2008-09-16
Just in order to thank you again..

---

### Post by sir_blargh on 2008-09-16
> **Yuzem said:**
> 

I forgot to remove that in the film grabber help section. The --save-as option was removed in version 0.7 since I released imdb-thumbnailer:
[http://ubuntuforums.org/showthread.php?p=5780989](http://ubuntuforums.org/showthread.php?p=5780989)
imdb-thumbnailer is much better for that and it works automatically. It is also compatible with avatar-factory themes but they don't look very good on nautilus since it doesn't detect transparency in thumbnails.



Excellent!  Installed it and it's performing great.  Thank you for the cool tools!

---

### Post by ayoli on 2008-09-22
@Yuzem :
Have you ever heard about autoglade ?
have a look to the first steps tutorial [here]("http://autoglade.wiki.sourceforge.net/autoglade+tutorial+-+first+steps")
It seems to be very easy to use and more powerfull than zenity. IMO, it is worth trying.

cheers.

---

### Post by Yuzem on 2008-09-22
I think that I have seen it at gnomefiles but I never gave it a try.
I will take a look.
Thanks ayoli.

---

### Post by Nonno Bassotto on 2008-09-30
Autoglade seems a very interesting tool indeed. This time I won't try to make a GUI, but it seems that the mockup Yuzem posted can be realized. By the way, I've [posted a Deb]("http://ubuntuforums.org/showpost.php?p=5723220&postcount=543") of the GUI I created. Ok, I think noone is using it, but I wanted to learn how to make debs. :)

---

### Post by mailbox on 2008-10-09
So... is there any way to use an image file I specify instead of using a grabber?

---

### Post by Yuzem on 2008-10-09
> **Nonno Bassotto said:**
> Autoglade seems a very interesting tool indeed. This time I won't try to make a GUI, but it seems that the mockup Yuzem posted can be realized.
I think it can't be realized or I don't know how. It seems that autoglade can't do treeviews or notebooks (tabs).

> **mailbox said:**
> So... is there any way to use an image file I specify instead of using a grabber?
Yes, use the "--picture-gui" option:
```
avatar-factory -g avatar --picture-gui avatar1.desktop etc...
```
For the film grabber you just have to drag and drop a picture to the avatar but you will have to restart nautilus to see the changes:
```
killall nautilus
```

---

### Post by m_ad on 2008-10-10
I'm having problems getting this to work. I'm using the command line, and it puts a icon in my ~/Videos but it's a blank icon.

```
~/ avatar-factory -g tv-show -t dvd-3 /mnt/wd-mybook/MOVIES/Looney.Tunes.Golden.Collection.Volume.1.Disc.1/ ~/Videos/
Building list of folders to process...
1/1 - added Looney.Tunes.Golden.Collection.Volume.1.Disc.1
```

---

### Post by Yuzem on 2008-10-10
Ok, fixed:
```
sudo gedit /usr/local/share/avatar-factory/grabbers/tv-show
```

Line 27 should be:
```
					grabber_picture="$themes_PATH/Vinyl/base.png"
```
Change it to:
```
					grabber_picture="$avatar_factory_PATH/imdb-nocover.gif"
```

---

### Post by mailbox on 2008-10-11
Yes, use the "--picture-gui" option:
```
avatar-factory -g avatar --picture-gui avatar1.desktop etc...
```
For the film grabber you just have to drag and drop a picture to the avatar but you will have to restart nautilus to see the changes:
```
killall nautilus
```[/QUOTE]Ah-ha, I'm getting closer.
I don't have a .desktop file for any of my films yet, and I'd also like to pass the images to shadow-hq (or whatever it's called) to get that nice drop shadow, then make a .desktop.
Thanks for the help so far, too.

Oh, and I'm using thunar.

---

### Post by Yuzem on 2008-10-11
I think that you can use the option with any grabber:
```
avatar-factory -g film -t shadow --picture-gui /input/folder /output/folder
```
But it will ask for a picture for every movie. I think that it is more practical to use it only on the avatars for which you want a custom cover.

---

### Post by mailbox on 2008-10-12
Thanks so much, guys!
With a little tweaking, I changed the film launcher to use gmplayer instead of totem, but I was wondering how I would go about adding arguments to that. I haven't gotten around to encoding some of the 1080p films I have, and they're still in raw .ts form, meaning that I need to start them with: `gmplayer "movie.ts" -really-quiet -cache 4096 -ni -lavdopts lowres=1:fast:skiploopfilter=all` to get them to play with a minimal amount of lag.
Now, I haven't tested this, but if I make a new launcher called film-hd, I would add all those arguments to the end of this line, after the final `)`, correct?:```
eval $film $(echo "$URL" | sed -e 's/^/"/' -e 's/$/"/' -e 's/[cC][dD][1-9]/"???"/' -e 's/[1-9][oO][fF][1-9]/"????"/')&
```

---

### Post by Yuzem on 2008-10-12
> **mailbox said:**
> Thanks so much, guys!
With a little tweaking, I changed the film launcher to use gmplayer instead of totem
If you change a program file it will be overwritten with a new version and there is no need to do that because it can be configured:
```
gedit ~/.avatar-factory/grabbers/film
```
insert:
```
launcher="gmplayer"
```
You can also do that from the gui:
1. launch avatar-factory
2. press ok
3. select the grabber
4. set the launcher

> **mailbox said:**
> 
 but I was wondering how I would go about adding arguments to that. I haven't gotten around to encoding some of the 1080p films I have, and they're still in raw .ts form, meaning that I need to start them with: `gmplayer "movie.ts" -really-quiet -cache 4096 -ni -lavdopts lowres=1:fast:skiploopfilter=all` to get them to play with a minimal amount of lag.
Now, I haven't tested this, but if I make a new launcher called film-hd, I would add all those arguments to the end of this line, after the final `)`, correct?:```
eval $film $(echo "$URL" | sed -e 's/^/"/' -e 's/$/"/' -e 's/[cC][dD][1-9]/"???"/' -e 's/[1-9][oO][fF][1-9]/"????"/')&
```

No, you should not touch the grabber for that but the launcher.
The grabbers are in:
/usr/local/share/avatar-factory/grabbers
the launchers in:
/usr/local/share/avatar-factory/launchers

The grabbers always set the avatars to use the launcher so you can configure the launcher without building again your avatars.

Again there is no need to edit the files on those paths.
To configure the launcher as you want you do:
```
gedit ~/.avatar-factory/grabbers/film
```
insert:
```
launcher="gmplayer -really-quiet -cache 4096 -ni -lavdopts lowres=1:fast:skiploopfilter=all"
```
Or from the gui... but I think that you can set those options in:
~/.mplayer/config

---

### Post by ashmew2 on 2008-10-25
Yuzem...Nice work and keep up the good work Please!!

I noticed Something , 
In the GUI , when i select a Grabber(Film/music or any other) , 

and double click this :

```
Delete Broken : No
```

It is changed to 
```

Delete Broken : Yes
```

But if i double click it again , it is still 

```
Delete Broken : Yes

```
Is it on purpose ?

---

### Post by Yuzem on 2008-10-26
> **ashmew2 said:**
> Is it on purpose ?
No, it is a bug. It will be fixed on the next version.
Thanks for reporting. :)

---

### Post by ashmew2 on 2008-10-26
[QUOTE=Yuzem]Thanks for reporting.[/QUOTE]

Nah man , We Thank You for making this GREAT piece of application.

Thanks Yuzem..You ROCK !:guitar:

---

### Post by soro2005 on 2008-10-26
> **Yuzem said:**
> No, it is a bug. It will be fixed on the next version.
Thanks for reporting. :)

I think that this might be the same bug, or you've been made aware long ago. Just in case: The option to disable the music widget does also not stick here. Thanks for the great work!

---

### Post by Yuzem on 2008-10-27
> **ashmew2 said:**
> Thanks Yuzem..You ROCK !:guitar:
You are welcome. :)
> **soro2005 said:**
> The option to disable the music widget does also not stick here.
Are you sure that is the same thing? I can't reproduce that error...

---

### Post by soro2005 on 2008-10-27
> **Yuzem said:**
> You are welcome. :)

Are you sure that is the same thing? I can't reproduce that error...

No, I'm not sure it's the same thing. Was just guessing. But if you can't reproduce it, here a fuller description:

If I open the music options dialog, the last entry is "widget." I double-click it, and the dialog reloads. "Widget" is now on "yes." I click "ok" to close the dialog, then open the dialog again, and "widget" has no value. The same if I double click on "yes" to get "no." Click "ok" to commit, and on next open, the value is gone again, and the widget keeps appearing on the desktop. In other words, I cannot disable the widget through the dialog.

I use Ubuntu 8.04 64 bit.

---

### Post by Yuzem on 2008-10-27
Ok, it is a different bug. It will be fixed in the next version.

By the way, if someone could test it and report some bugs, that would be great. It is attached.

Changelog:
```
??.??.08------0.7.7
	+film grabber: yahoo fallback
	+film & imdb grabbers: changed the no cover icon
	+film & imdb grabbers: detect if there is a cover for a movie wich had no cover before
	+fixed error message with file inputs
	+fixed error in picture launcher
	+tv-show grabber: fixed problem when no cover is found.
	+gui: fixed "delete broken" option problem
	+gui: fixed problem with music grabber configuration
	+gui: improved and simplified
```

---

### Post by soro2005 on 2008-10-28
> **Yuzem said:**
> Ok, it is a different bug. It will be fixed in the next version.

By the way, if someone could test it and report some bugs, that would be great. It is attached.

Thanks for fixing the widget option! It seems that it's not working with mpd at the moment. I click on a launcher and nothing happens. May be because my mpd is currently in a weird state, though. Audacious seems to work.

---

### Post by Yuzem on 2008-10-28
The config file has changed in the latest versions. If your mpd music directory is not in /var/lib/mpd/music you must edit the config file "~/.avatar-factory/grabbers/music"

You can read about that:
```
avatar-factory -g music --help
```
(MPD INSTRUCTIONS are at the end)

---

### Post by soro2005 on 2008-10-28
> **Yuzem said:**
> The config file has changed in the latest versions. If your mpd music directory is not in /var/lib/mpd/music you must edit the config file "~/.avatar-factory/grabbers/music"
Ah, ok, it didn't find the host and port. Could have figured that much. Wasn't it just using the hardcoded defaults from the launchers/music file before? I now have to add them manually to the config file you specify. Works nicely now.

---

### Post by Yuzem on 2008-10-29
> **soro2005 said:**
> Wasn't it just using the hardcoded defaults from the launchers/music file before? I now have to add them manually to the config file you specify.
Another bug. I will fix it.

---

### Post by jinjiru on 2008-10-30
Could anyone please explain a total newbie what this script is doing? I've installed it and carefully studied all the man pages but still have no idea how to use it :(
I have a huge music collection and there's a .folder.png and .desktop file in every album folder. I use exaile. How should I use this script?

Thanks a lot!

---

### Post by Yuzem on 2008-10-30
For the music grabber you have to read:
```
avatar-factory -g music --help
```

To set exaile as the player:
```
echo "launcher=exaile" >> ~/.avatar-factory/grabbers/music
```

To build the avatars:
```
avatar-factory -g music ~/your-music-folder  ~/destination-folder
```

You can use the --folders flag to replicate the folder structure:
```
avatar-factory -g music --folders ~/your-music-folder  ~/destination-folder
```

---

### Post by jinjiru on 2008-10-30
Yuzem, thanks a lot! Now it's much more clear. 
I just don't get clear enough what the destination folder is. Is it a folder i need to choose to store all the generated avatars?

---

### Post by Yuzem on 2008-10-30
> **jinjiru said:**
> I just don't get clear enough what the destination folder is. Is it a folder i need to choose to store all the generated avatars?

Exactly, you must make a new folder for the avatars.
For example:
```
mkdir ~/music-avatars
```

Then:
```
avatar-factory -g music ~/your-music-folder  ~/music-avatars
```

---

### Post by foutrelis on 2008-11-02
Hello,

I noticed that no licensing information is included in the source code. Therefore, I've placed a question on LP regarding this; you can read it and hopefully answer it at [https://answers.launchpad.net/avatar-factory/+question/49352](https://answers.launchpad.net/avatar-factory/+question/49352).

Thanks.

---

### Post by Yuzem on 2008-11-02
Sorry, I didn't get a notification...
I just answer your question.

---

### Post by Rubicon421 on 2008-11-11
> **Yuzem said:**
> **INTRODUCTION**

This began as a tiny script and now I have a lot of ideas for it.
If you just want to know what is this about then take a look at the screen shots:

Thunar (CD theme):
[[IMG]http://img209.imageshack.us/img209/1/pantallazo10ax2.th.jpg[/IMG]]("http://img209.imageshack.us/my.php?image=pantallazo10ax2.jpg")

**This is Nautilus with some vinyls (I can only post 8 images):**
[http://img176.imageshack.us/my.php?image=pantallazo06kr3.jpg](http://img176.imageshack.us/my.php?image=pantallazo06kr3.jpg)

The DVD theme is used by the imdb grabber (for firefox bookmarks) and the film grabber (for video files)
Nautilus with a custom background:
[[IMG]http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.th.png[/IMG]]("http://img379.imageshack.us/my.php?image=avatarfactoryfg3lk3.png")

Nautilus again (picture avatars and photo theme) :
[[IMG]http://img178.imageshack.us/img178/411/pictureavatarssd8.th.png[/IMG]]("http://img178.imageshack.us/my.php?image=pictureavatarssd8.png")

YouTube Avatars
[[IMG]http://img360.imageshack.us/img360/4616/avatarfactoryyoutubeax3.th.jpg[/IMG]]("http://img360.imageshack.us/my.php?image=avatarfactoryyoutubeax3.jpg")

tv-show grabber:
[[IMG]http://img518.imageshack.us/img518/8694/avatarfactorytvshowwx8.th.png[/IMG]]("http://img518.imageshack.us/my.php?image=avatarfactorytvshowwx8.png")

The music widget (support drag and drop):
[[IMG]http://img374.imageshack.us/img374/8009/musicwidgetkr4.th.jpg[/IMG]]("http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg")

mame Avatars in nautilus:
[[IMG]http://img165.imageshack.us/img165/5421/mameavatarsop9.th.jpg[/IMG]]("http://img165.imageshack.us/my.php?image=mameavatarsop9.jpg")

comic Avatars:
They can be bookmarked as shown on the screenshot:
[[IMG]http://img163.imageshack.us/img163/8576/comicavatarsbk3.th.jpg[/IMG]]("http://img163.imageshack.us/my.php?image=comicavatarsbk3.jpg")

**DESCRIPTION**

Avatar Factory is a bash script that creates shortcuts (Desktop Entry files) with eye candy icons that represent music albums, photo albums, DVD films, youtube videos, mame roms and more. When clicked the avatars can perform different actions as launching a video, start playing some music (compatible with many music players), open a folder, etc...
They can be viewed in Nautilus, Thunar or any application that support Desktop Entry files.

**BEFORE INSTALL**

I have to say that I don't have any previous knowledge about programing. I have learned most of what I know by doing this script. If something is implemented in an inconvenient way just tell me. I am really a beginner at this.

Check this post to see what a newbie I am:
[http://ubuntuforums.org/showthread.php?t=460259](http://ubuntuforums.org/showthread.php?t=460259)

Thanks to the people there for helping me out with some very basic things.

**INSTALLATION**

You can install it from the deb or the rpm package
If you prefer to install it  from the tar file follow the instructions in the README.
[**_[COLOR=Red]Download (gnomefiles)[/COLOR]_**]("http://www.gnomefiles.org/app.php/Avatar_Factory")

**USAGE**

You can use the graphic interface (zenity) from the applications menu but it is much more powerful to use the command line.

**From the command line:**

For instructions type:
```
man avatar-factory
```For grabbers specific instructions and description type:
```
avatar-factory -g grabber_name --help
```To get a list of available grabbers:
```
avatar-factory -lg
```**Automatic cover download (for the music grabber)**

You can check this posts about mass grabbing covers directly to the correct folders:
[Album Cover Art Downloader]("http://ubuntuforums.org/showpost.php?p=3266072&postcount=50")
[Sonata]("http://ubuntuforums.org/showpost.php?p=3332652&postcount=136")
[exaile-cover-mover]("http://ubuntuforums.org/showpost.php?p=4401335&postcount=379")

**CHANGELOG**

```
28.06.07------0.1.0
    +Initial release: 1 grabber and 2 themes (CD and Vinyl)
29.06.07------0.1.1
    +Added support for exaile.
    +Added support for amarok
    +Added support for moc
05.07.07------0.1.5
    +Added support for mpd (music player daemon)
    +Added support for muine
    +Added support for quodlibet
    +avatar-music-widget (automatically show/hide the album widget)
    +Existing avatar won't be overwritten (now you can scan the whole music dir for new albums)
    +Minor internal changes
12.08.07------0.1.9
    +index number will reflect better the real number when adding new avatars.
    +existing icons won't be overwritten (If you delete your avatars it will be much faster to create them again)
    +"-f" option to force icon overwrite.
    +dvd theme
    +film grabber
12.08.07------0.2.0
    +more speed if the icon exist
    +fixed bug in music grabber
    +better handling of path input
27.08.07------0.2.5
    +picture grabber
    +photos theme
    +added 2 dvd theme variations
    +fixed sorting problem (they should be processed by path)
    +fixed music grabber bug
    +fixed problem with quodlibet
30.08.07------0.2.7
    +better mpd support (thanks to aidanr)
    +hidden foldes are skipped now
    +added support for banshee  (thanks to duff)
    +fixed "--list-themes" command problem
01.09.07------0.2.8
    +added audio formats (m4a aac ogg) for Banshee and other players.
    +fixed bug with music grabber not getting the covers in the correct order.
    +fixed bug with --type option.
06.09.07------0.3.0
    +added support for audacious
    +added mocp-add (doesn't clear the playlist)
    +added mpd-add (doesn't clear the playlist)
    +added audacious-add (doesn't clear the playlist)
    +added totem-add (doesn't clear the playlist)
    +better support for unknown players
    +film grabber renamed to imdb
    +added film theme
    +added youtube grabber
    +added -g option to use a custom grabber
    +added -lg to list available grabbers
    +avatar-launcher was remplaced by avatar-factory -al
    +internal changes for the music launcher
    +changed the icon folder structure
    +redesigned grabbers structure
    +many internal changes in avatar-factory
07.09.07------0.3.0-1
    +fixed bug in music launcher
    +fixed picture grabber bug
    +changed default behavior for youtube grabber
09.09.07------0.3.0-1
    +now youtube avatars should be launched with firefox
14.09.07------0.3.3
    +internal changes in avatar-factory
    +added files source type
    +added film grabber
29.09.07------0.3.9
    +change to totem as the default player for film avatars
    +$avatar_title and $URL from bookmarks are set by default
    +fixed bug with folders and files source types
    +added dvd-3 theme
    +allow to set a film avatar cover by drag and drop
    +changed the extension to ".desktop"
    +added tv-show grabber
    +gui implementation with zenity
    +added [1-9][oO][fF][1-9] disc detection for the film grabber
    +allow to process folders in files  source type (film grabber)
    +added a filter for files source type
    +the music grabber will skip folders without music files inside
    +fixed bugs in film grabber
    +internal changes for launchers
07.10.07------0.4.2
    +fixed --gui-progress problem
    +changed the music_widget extension
    +added Index and Title tags to avatars
    +added avatar grabber
    +added --gui for --type option
    +added drag and drop support to the music widget
    +the film grabber now makes avatars for all files even if no cover was found.
02.11.07------0.4.6
    +music widget: allow to play all discs when clicked
    +film grabber: fixed duplicated files with [1-9][oO][fF][1-9] disc detection
    +film grabber: added [(][1-9][oO][fF][1-9][)] disc detection
    +film grabber: added cue file type
    +avatar launcher: added support for avatar files
    +added picture launcher
    +now running avatar-factory with no parameter brings the GUI
    +avatar-music-widget: fixes
    +avatar-music-widget replaced by avatar-factory --widget
    +tv-show: if no cover is found it searches online like the film grabber
    +music grabber: added support for flac files.
    +music launcher: added support for "listen" music player
23.12.07------0.5.0
    +added mame grabber
    +added shadow theme
    +music launcher: amarok-add support
    +film grabber: added iso filetype
    +fixed picture drag and drop problem and global icon problems
    +added a man page
    +youtube grabber: changed the default behavior
    +tv-show grabber: added season detection
    +tv-show grabber: added support for VIDEO_TS folders (dvd video)
    +tv-show grebber: added more video formats
    +grabber help implementation
    +added StartupNotify support
31.01.08------0.5.5
    +added comic grabber
    +added book theme
    +avatar grabber: added --comic-bookmarks option
    +added anobii grabber
    +added epiphany bookmarks support
    +added opera bookmarks support
    +internal changes
    +added --save-as icon option
    +film grabber: --save-as thumbnail option
    +added --picture-gui option
    +mame grabber: basic prototype detection
    +tv-show launcher: own player config option
02.02.08------0.5.5.1
    +avatar grabber: fixed bug with the new comic avatars.
12.03.08------0.6
    +music grabber: added wma support
    +gui: save is now the last step
    +film launcher: fixed drag and drop to set the cover
    +film grabber: added bin file type
    +code cleanup
    +allows to execute without install
    +grabbers help abstracted from grabbers
    +the gui has been abstracted to one function
    +new and improved gui
    +music launcher: support for all players has been rewritten.
    +--avatar-launcher option can now overwrite the default launcher
    +added --folders option to replicate folder structure
    +mame grabber: speed improvement
13.03.08------0.6.1
    +fixed --folder option not working correctly
    +fixed problem with gui
    +fixed bug in --avatar-launcher option
25.04.08------0.6.2
    +fixed problem with Desktop name for different languages (Thanks to direk_)
    +fixed bug in film grabber
    +fixed problem with dvd-1 dvd-2 and dvd-3 themes not being installed that causes the tv-show grabber to fail.
    +fixed an important problem with all the themes that causes avatar-factory to fail on some distributions like Ubuntu Hardy Heron and ArchLinux
18.05.08------0.6.5
    +added widget_name option
    +fixed the music widget in Ubuntu Hardy and other distros
    +music_widget: workaround to nautilus bugs
    +added shadow-hq theme (256x256 px)
    +added --delete option
    +added --folders-2 option
    +gui: added --delete y --folders options
    +added --folders option to bookmark grabbers (firefox only)
    +internal changes
25.05.08------0.6.5.1
    +music grabber: bug fixed (it wasn't working)
    +fix: --folder option not working properly with some grabbers.
26.08.08------0.7.0
    +many gui improvements
    +added --icon-size option for nautilus
    +book theme: correction to center the picture for all grabbers except the comic grabber.
    +removed flags: -ag -mg -pg -fg
    +--save-as option was removed
    +book theme splitted in book and book-open themes
    +all themes have been changed, now they are independent scripts
    +folder grabbers (music comic picture etc): update the icon if the folder has changed
    +film grabber: some improvements
    +code cleanup
    +youtube: handle some special chars
    +youtube: icon names have changed
13.09.08------0.7.5
    +removed assisted x-mame installation.
    +fixed icon-size option in the gui
    +fixed bug in recreate folder structure mode
    +gui: music widget enable/disable
    +gui: launcher configuration
    +launchers configuration file has changed. The old config is obsolete.
    +gui: source configuration for bookmark grabbers
    +help files updated
    +name decoding for all bookmarks grabbers
    +anobii: account grabber using ~username as the source
    +fixed problem with icon-size when used with recreate folders
    +when running from the cli if there are no destination folder the gui generated config will be used. Now you can do "avatar-factory -g grabber"
    +fixed problem with book-open theme (--comic-bookmark)
    +fixed problem with --comic-bookmark option

```**PLANNED FEATURES:** (maybe and I don`t know when)

star ratings
change nautilus icons
and more...
how can I just get the feature in the top thumbnail installed in Ubuntu? I want the browser where I can view thumbnails of music folders with the album art. It says it's for xfce. What exactly is that and will it work with Ubuntu/Gnome?

---

### Post by Yuzem on 2008-11-11
Yes it works in ubuntu gnome. The screenshot is from thunar, you can install thunar in gnome:
```
sudo apt-get install thunar
```
...but you can also use nautilus.

To have the pretty icons for example in ~/Albums type in the terminal:
```
mkdir ~/Albums
```
Then:
```
avatar-factory -g music your/music/folder  ~/Albums
```
(replace your/music/folder)

---

### Post by Rubicon421 on 2008-11-11
I'm up to the last code and am not sure how to edit it for my music folder. It's in

h /media/Back Up Drive/MUSIC/MUSIC - Full Albums

---

### Post by Yuzem on 2008-11-11
Here:
```
avatar-factory -g music '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

You can also drag and drop the folder to the terminal.

---

### Post by Rubicon421 on 2008-11-11
> **Yuzem said:**
> Here:
```
avatar-factory -g music '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

You can also drag and drop the folder to the terminal.
AWESOME! It's building the list now. We'll see how it looks in a few. So where should I start if I want to understand the types of code I just used? I'm completely new to linux and have no programming background except a little BASIC on a Commodore 64 (WAAAAAAAY old school) LOL.

---

### Post by Rubicon421 on 2008-11-11
> **Kill Vista said:**
> AWESOME! It's building the list now. We'll see how it looks in a few. So where should I start if I want to understand the types of code I just used? I'm completely new to linux and have no programming background except a little BASIC on a Commodore 64 (WAAAAAAAY old school) LOL.
OK, what just happened? It finished and now I have a folder called albums with all the album art thumbnails like I wanted (if I view it with Thunar) but they aren't folders, it says they are desktop configuration files. Double clicking does nothing and right click only gives execute (causes error in Totem) and open with.

---

### Post by Rubicon421 on 2008-11-11
> **Kill Vista said:**
> OK, what just happened? It finished and now I have a folder called albums with all the album art thumbnails like I wanted (if I view it with Thunar) but they aren't folders, it says they are desktop configuration files. Double clicking does nothing and right click only gives execute (causes error in Totem) and open with.
This seems to be based on tags. Not all my tags are correct (or some are missing). I'm looking for something that just takes the exiting meta data or image files in folder and uses it for the thumbnail like in windows. So far I prefer almost everything about linux way more than windows but this is getting annoying. It shouldn't be so hard. I don't want a new folder of config files or links, I just want to keep the same folders and folder structure, set it to icon view and have thumbnails of album covers.

I appreciate your help though, I did get it to work. It just wasn't what I was looking for. I'm sure that somewhere, someone is crankin' out some code for this right now, But this is the closest thing I can find so far, so I guess I'm gonna keep lookin.

---

### Post by Yuzem on 2008-11-11
Try this:

Delete all created avatars:
```
rm ~/Albums/*.desktop
```

Then:
```
avatar-factory -g music --folders --icon-size 27 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

Use nautilus and they should work as folders.

To understand that command you can read the manual:
```
man avatar-factory
```

---

### Post by Rubicon421 on 2008-11-11
> **Yuzem said:**
> Try this:

Delete all created avatars:
```
rm ~/Albums/*.desktop
```

Then:
```
avatar-factory -g music --folders --icon-size 2.7 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

Use nautilus and they should work as folders.

To understand that command you can read the manual:
```
man avatar-factory
```
line 272: Wrong: command not found

(after the second command)

---

### Post by Yuzem on 2008-11-11
> **Kill Vista said:**
> This seems to be based on tags. Not all my tags are correct (or some are missing).
It isn't based on tags. It should work for any folder containing music and at lest one picture.

> **Kill Vista said:**
> 
I don't want a new folder of config files or links, I just want to keep the same folders and folder structure, set it to icon view and have thumbnails of album covers.
Sadly thumbnails for folders are not supported in any file manager that I know. Nautilus allows to have custom icons but thunar doesn't. :(

---

### Post by Yuzem on 2008-11-11
> **Kill Vista said:**
> line 272: Wrong: command not found

(after the second command)

Sorry, try this:
```
avatar-factory -g music --folders --icon-size 27 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

---

### Post by Rubicon421 on 2008-11-11
> **Yuzem said:**
> Sorry, try this:
```
avatar-factory -g music --folders --icon-size 27 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```
OK, that's WAY closer. But when I open the albums folder, I have all the bands in folders first and there aren't any icons yet. Once I pick one and open it then all the albums have icons and they open to the folders now. It's the closest I have got so far. Is there more I (you) can do for the folder with all the bands?

---

### Post by Yuzem on 2008-11-11
I don't know if I understand correctly. Do you want all albums in the same folder?

If that is the case then delete all again and type:
```
avatar-factory -g music --icon-size 27 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

---

### Post by Rubicon421 on 2008-11-11
> **Yuzem said:**
> I don't know if I understand correctly. Do you want all albums in the same folder?

If that is the case then delete all again and type:
```
avatar-factory -g music --icon-size 27 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```
OK, just to clarify so I don't use the wrong code again:
I have the music folder as the "root" of all the music stuff. In there I have some random stuff I'm not worried about having icons for, then there is also the Music - full albums folder in it. In that folder is all the bands, then each band folder had the albums for that band. I only really want to get the full albums folder to display an icon for each band and the band folders to have an icon for each album. I have icons for each album now but the folder up one level with all the bands is still normal. Can you make a code to add that to what I have already- keep the album icons but add band icons in the folder above it?

Thanks again, you really know your stuff. I won't be up much longer but I will check back tomorrow if I can't finish this tonight. You've been a huge help in figuring this out.

---

### Post by Yuzem on 2008-11-11
There is a problem with that. I will try to explain.
You have:

```
    full albums
        band 1
            album 1
            album 2
            album 3
            etc
        band 2
        band 3
        etc
```

And the avatar are:

```
    ~/Albums
        band 1
            icon 1
            icon 2
            icon 3
            etc
        band 2
        band 3
        etc
```

If you clic in for example "icon 1" you enter "album 1" folder. "icon 1" is not a folder but an avatar (a .desktop file, a shortcut to a folder)

You want the bands folders to have icons and for that they have to be shortcuts not folders. Every band shortcut will point to the real band folder that means that the albums inside will be the real folders, with no icons...

This should give you the folders and the shortcuts for the bands:
```
avatar-factory -g picture -t cd --icon-size 27 --type 0 '/media/Back Up Drive/MUSIC/MUSIC - Full Albums' ~/Albums
```

I know It is not what you want but I can't think in a better option.
The result should be:
```

    ~/Albums
        band 1
            icon 1
            icon 2
            icon 3
            etc
        band 2
        band 3
        band 1 (icon)
        band 2 (icon)
        band 3 (icon)
        etc
```

Changing the actual folder icons is in the todo list but I don't know when it will be implemented...

---

### Post by dariusdwtt on 2008-11-18
I love it!

Good work!

---

### Post by Yuzem on 2008-12-04
I have posted an idea on ubuntu brainstorm that is related to this application. If you like it you can vote for it. [Here it is]("http://brainstorm.ubuntu.com/idea/16240/").

[[IMG]http://img230.imageshack.us/img230/5808/pantallazohu0.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=pantallazohu0.jpg)

---

### Post by dariusdwtt on 2008-12-06
Having a bit of a problem.

Whatever I do, the icons have writing beneath them... 
I'd like just to have the icon...?

---

### Post by atomo133 on 2008-12-07
ok
i installed tha program and nothing happened
then i rebooted and the folder with all my music files was empty

any advice??

we 're talking about ~160 gb of music wich i ve ripped from my cd's

it a major deal

help me fix this!!

---

### Post by andrek on 2008-12-07
> **Yuzem said:**
> I have posted an idea on ubuntu brainstorm that is related to this application. If you like it you can vote for it. [Here it is]("http://brainstorm.ubuntu.com/idea/16240/").

[[IMG]http://img230.imageshack.us/img230/5808/pantallazohu0.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=pantallazohu0.jpg)

By the way, what's the GTK theme you have used here?

---

### Post by Yuzem on 2008-12-07
> **dariusdwtt said:**
> Having a bit of a problem.

Whatever I do, the icons have writing beneath them... 
I'd like just to have the icon...?
Nautilus has removed that feature. It was working on Feisty and maybe also on Gutsy.

> **atomo133 said:**
> ok
i installed tha program and nothing happened
then i rebooted and the folder with all my music files was empty

any advice??

we 're talking about ~160 gb of music wich i ve ripped from my cd's

it a major deal

help me fix this!!
That is very strange, nothing should hapend after install. Nothing should hapend after reboot. To make it work you have to run the application.
Did you run it?

This should not delete any file, maybe your problem is caused by something else?

> **andrek said:**
> By the way, what's the GTK theme you have used here?
It is attached. It requires the aurora engine.

---

### Post by atomo133 on 2008-12-08
yes ,  i ran it

it asked for the folder where my music was

then it stuck there and i had to reboot

after that that particular folder was empty

i dont know  what went wrong
but if there s something i can do i would like to know about it
or are the files lost permanently
?

---

### Post by Yuzem on 2008-12-08
Did you run it from the command line?
If that is the case, what command did you use?
You can type "history" at the command line to see a list of the latest command used.

I really can't see how that could have been produced by avatar-factory... It is more likely that there was a disk error because of the hard reboot.

I am not an expert on lost data. I can give you some advices but it will be better to ask someone else.

First of all, do not write anything to that disk.
You can check the lost+found folder:
```
sudo nautilus /lost+found
```

If your disk is formated in ext3 you can try [extundel]("http://freshmeat.net/projects/ext3undel/?branch_id=74825&release_id=280489"), there is a deb package.

[R-linux]("http://www.data-recovery-software.net/es/Linux_Recovery.shtml") has a gui but it is for windows, maybe it works with wine.

Please let me know what happens and if there is anything more that I can do to help.

---

### Post by Nonno Bassotto on 2008-12-08
Is it possible to add support for getting the movies from a [Flixster]("http://www.flixster.com") page, similar to what you have done for Anobii? The avatars could link to the IMDB page as usual, it would be just nice to add all the films in your account rather than using dozens of IMDB bookmarks.

If you don't have time to add this feature, could you please tell me which parts should be modified to create a new grabber? I could try to create it myself (and maybe share it here if you don't mind) but I'm not sure if it is enough to create a new script in the grabbers directory.

---

### Post by Yuzem on 2008-12-08
I didn't know about Flixster, it seems a very good site.
I think it is time to make a tutorial on how to make a grabber. It is very easy.

Coming soon...

---

### Post by animaniac on 2008-12-08
OK, i got ubuntu running on my moms PC and she WANTS (note the capital letters) something like this to browse her pictures.

Is there any way to make the program apply the icons located in /home/user/.avatar-factory/icons/picture directly to the original folders instead of it making shortcuts. And possibly uppdate the parent directory actively?

Eg. if I have the folders i want previews of in ~/Pictures, i apply the script and have all the folders in that directory with previews and adapting to changes. (a bit (or even exactly) like Windows, even tho i hate that comparison)

Also, How do you change the icons to something like this...
[http://brainstorm.ubuntu.com/idea/16240/](http://brainstorm.ubuntu.com/idea/16240/)
?

---

### Post by atomo133 on 2008-12-08
> **Yuzem said:**
> Did you run it from the command line?
If that is the case, what command did you use?
You can type "history" at the command line to see a list of the latest command used.

I really can't see how that could have been produced by avatar-factory... It is more likely that there was a disk error because of the hard reboot.

I am not an expert on lost data. I can give you some advices but it will be better to ask someone else.

First of all, do not write anything to that disk.
You can check the lost+found folder:
```
sudo nautilus /lost+found
```

If your disk is formated in ext3 you can try [extundel]("http://freshmeat.net/projects/ext3undel/?branch_id=74825&release_id=280489"), there is a deb package.

[R-linux]("http://www.data-recovery-software.net/es/Linux_Recovery.shtml") has a gui but it is for windows, maybe it works with wine.

Please let me know what happens and if there is anything more that I can do to help.

firstly , thanx for your interest
i run it throught Applications > Accesories > avatar factory
i am in xubuntu..maybe theres a bug working with avatar+thunar??

the disk is ntfs because it holds all my music and i d like to listen to it throught windows too

it is possible it s not the applications fault , but the hd 's
any ideas though?

---

### Post by Yuzem on 2008-12-08
> **animaniac said:**
> Is there any way to make the program apply the icons located in /home/user/.avatar-factory/icons/picture directly to the original folders instead of it making shortcuts. And possibly uppdate the parent directory actively?

Eg. if I have the folders i want previews of in ~/Pictures, i apply the script and have all the folders in that directory with previews and adapting to changes. (a bit (or even exactly) like Windows, even tho i hate that comparison)
No, it isn't possible to do that. The [idea]("http://brainstorm.ubuntu.com/idea/16240/") I posted on ubuntu brainstorm is exactly for that purpose.
We will have to wait until it gets implemented...
Meanwhile anyone can help by [promoting the idea]("http://brainstorm.ubuntu.com/idea/16240/promote/").

> **animaniac said:**
> 
Also, How do you change the icons to something like this...
[http://brainstorm.ubuntu.com/idea/16240/](http://brainstorm.ubuntu.com/idea/16240/)
?
There are 3 screenshots there. If you are talking about the last one, it isn't possible because even if I make a theme to display the folder icon behind, the icon will not change according to the icon theme.

> **atomo133 said:**
> firstly , thanx for your interest
i run it throught Applications > Accesories > avatar factory
i am in xubuntu..maybe theres a bug working with avatar+thunar??
No that I know.

> **atomo133 said:**
> 
the disk is ntfs because it holds all my music and i d like to listen to it throught windows too

it is possible it s not the applications fault , but the hd 's
any ideas though?
You could try [NTFS Undelete]("http://ntfsundelete.com/"). I didn't test it but it seems very good. I did test [GetDataBack]("http://getdataback-for-ntfs.softonic.com/") and it is very good but it isn't free. If the other program fail you could download the evaluation version to see if the data is there.

---

### Post by dariusdwtt on 2008-12-08
> Nautilus has removed that feature. It was working on Feisty and maybe also on Gutsy.

that really sucks :(

but I know you'll find a work around :)

@ [atomo133]("http://ubuntuforums.org/member.php?u=661697")

that def sounds like the reboot killed your music.

One of those data "undelete"programs should definately work.

Good luck!

---

### Post by Yuzem on 2008-12-08
> **dariusdwtt said:**
> but I know you'll find a work around :)
Sadly, I think it isn't possible. Nautilus has the last word on that and if it doesn't want to allow nameless shortcuts thats all.

---

### Post by Yuzem on 2008-12-10
> **Yuzem said:**
> I think it is time to make a tutorial on how to make a grabber.

I started to write the howto but I don't know if it makes much sense since there isn't much to explain.

There is only one file needed to make a grabber.
It must be located in:
/usr/local/share/avatar-factory/grabbers

The name of the file will be the name of the grabber.

Other files are optional, a help file can be added in:
/usr/local/share/avatar-factory/help

A launcher can be added in:
/usr/local/share/avatar-factory/launchers

Both the launcher and the help file must be named exactly as the grabber.

> **Nonno Bassotto said:**
> If you don't have time to add this feature, could you please tell me which parts should be modified to create a new grabber? I could try to create it myself (and maybe share it here if you don't mind) but I'm not sure if it is enough to create a new script in the grabbers directory.

I hope this helps:
```

#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=flixster.com/movie
}

grabber_account_grabber () {(
	#This function must give the url and the title for each item
	#The first parameter, "$1", is the user name.
	#The url must be separated with "|" from the title:
	#URL|title
	#http://www.flixster.com/movie/the-dark-knight|The Dark Knight 
	#One item by line must be echoed.
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_name=$index.$avatar_title
	avatar_filename=${URL%/*}
	icon_NAME=$avatar_filename
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	#Here you only need to define the grabber_picture variable.
	#You should use the $URL variable. Something like this:
	#grabber_picture=$(wget -U firefox -qO - "$URL" | etc...)
}

```

Once you get the get_grabber_picture function working the grabber should work for bookmarks. Then the hardest part is to code the grabber_account_grabber function and that is all.

If you need anymore help let me know.

---

### Post by Nonno Bassotto on 2008-12-12
Thank you for your instructions, I will try to make my first grabber :)
I'm posting it here once it works.

---

### Post by QwUo173Hy on 2008-12-15
Hi Yuzem, would you consider using Launchpad as a bug tracker for Avatar Factory? A lot of people are asking the same questions again because they don't want to read 63 pages :) I have a bug I'd like to report there but it says 
> Avatar Factory does not use Launchpad as its bug tracker. 

---

### Post by Yuzem on 2008-12-15
Oh, :confused:, I thought that it was enabled. Thanks for reporting. It should work now.

---

### Post by Nonno Bassotto on 2008-12-21
I tried to create the flixster grabber. Actually I created two: flixster and flixster2imdb, which is the same thing but links to the imdb page instead of the flixster one. Here is the source; I still have to add code to get past page 1, but before I'd like to make these preliminary versions working.

flixster2imdb
```

#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=http://www.flixster.com/movie
}

grabber_account_grabber () {(
	web_account_page=$(wget -qO - "http://www.flixster.com/user/$1")
	web_page_url="http://www.flixster.com/"$(echo "$web_account_page" | grep 'li class="ratings"' | sed -e 's/.*href=\"//' -e 's/\"\ rel.*//' )
	web_page=$(wget -qO - "$web_page_url")
	titles=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*title=\"//' -e 's/\"\ href.*//' )
	number=$(echo "$titles" | wc -l )
	for i in $(seq 1 $number)
		do j=$(printf "%06d" $i)
		title=$(echo "$titles" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
		query=$(echo "$title" | sed -e 's/-/ /g' -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')
		url="http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$query&btnI=I%27m+Feeling+Lucky&meta="
		echo "$url"\|"$title"
	done
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_name=$index.$avatar_title
	avatar_filename=${URL%/*}
	icon_NAME=$avatar_filename
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	imdb_page="$(wget -U firefox -qO - "$URL")"
	photo_line_number=$(( $(echo "$imdb_page" | grep -n -i '<div class="photo">' | cut -d: -f1 ) + 1 ))
	grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2)
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	fi
}

```

flixster
```

#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=http://www.flixster.com/movie
}

grabber_account_grabber () {(
	web_account_page=$(wget -qO - "http://www.flixster.com/user/$1")
	web_page_url="http://www.flixster.com/"$(echo "$web_account_page" | grep 'li class="ratings"' | sed -e 's/.*href=\"//' -e 's/\"\ rel.*//' )
	web_page=$(wget -qO - "$web_page_url")
	titles=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*title=\"//' -e 's/\"\ href.*//' )
	urls=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*href=\"//' -e 's/\"\ \ >.*//' )
	number=$(echo "$titles" | wc -l )
	for i in $(seq 1 $number)
		do j=$(printf "%06d" $i)
		title=$(echo "$titles" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
		url="http://www.flixster.com"$(echo "$urls" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
		echo "$url"\|"$title"
	done
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_name=$index.$avatar_title
	avatar_filename=${URL%/*}
	icon_NAME=$avatar_filename
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	flixster_page="$(wget -U firefox -qO - "$URL")"
	grabber_picture=$(echo "$flixster_page" | grep 'class="movieImg"' | sed q | sed -e 's/.*src=\"//' -e 's/\"\ width.*//' )
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	fi
}

```

The problem is the same with both versions. The two functions grabber_account_grabber and get_grabber_picture work as expected, at least in my tests. But every time I launch avatar-factory I get a list of
```

1/25 - added Casablanca
convert: unable to open image `/home/andrea/.avatar-factory/icons/flixster/dvd/http://www.flixster.com/movie.png': No such file or directory.
/usr/local/bin/avatar-factory: line 931: /home/andrea/Prova/http://www.flixster.com/movie.desktop: Nessun file o directory

```
or
```

1/25 - added Casablanca
convert: unable to open image `/home/andrea/.avatar-factory/icons/flixster2imdb/dvd/http://www.google.com.png': No such file or directory.
/usr/local/bin/avatar-factory: line 931: /home/andrea/Prova/http://www.google.com.desktop: Nessun file o directory

```
and no avatar is actually created. I'm a bit puzzled...

I suspect that this has to do with the grabber secondary options, but I don't know how they should be set.

---

### Post by Yuzem on 2008-12-21
> **Nonno Bassotto said:**
> I suspect that this has to do with the grabber secondary options, but I don't know how they should be set.

You are right. It is my fault.The problem is the avatar_filename variable. That defines the actual name for the avatar and the icon. You should replace the '/' char that are not allow for filenames.

Something like this:
```
avatar_filename=$(echo $URL | sed -e 's|^http://||' -e 's/^www\.//' -e 's|/|_|g')
```

This should work too and it is all in bash:
```
avatar_filename=${URL//\//_}
```

---

### Post by Nonno Bassotto on 2008-12-21
Thank you, now it more or less works. :) At least the flixster grabber is working. The flixster2imdb grabber creates the avatars but they all link to
```

http://www.google.com/webhp

```
I guess somewhere avatar-factory cuts the full url, but I don't know why. Apart from this, I have to properly replace html entities, then it should be done. For now it looks like

flixster2imdb
```

#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=http://www.flixster.com/movie
}

grabber_account_grabber () {(
	web_account_page=$(wget -qO - "http://www.flixster.com/user/$1")
	web_page_url="http://www.flixster.com"$(echo "$web_account_page" | grep 'li class="ratings"' | sed -e 's/.*href=\"//' -e 's/\"\ rel.*//' )
	web_page=$(wget -qO - "$web_page_url")
	pages_number=$(echo "$web_page" | grep 'First | Prev' | sed q | sed -e 's/.*pageNav=//' -e 's/\">Last.*//' )
	for i in $(seq 1 $pages_number)
		do web_page_new_url="$web_page_url"\&"offset=25"\&"pageNav=$i"
		web_page=$(wget -qO - "$web_page_new_url")
		titles=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*title=\"//' -e 's/\"\ href.*//' )
		number=$(echo "$titles" | wc -l )
		for i in $(seq 1 $number)
			do j=$(printf "%06d" $i)
			title=$(echo "$titles" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			query=$(echo "$title" | sed -e 's/-/ /g' -e 's/ /+/g' -e 's/(/%28/g' -e 's/)/%29/g')
			url="http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$query&btnI=I%27m+Feeling+Lucky&meta="
			echo "$url"\|"$title"
		done
	done
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_name=$index.$avatar_title
	avatar_filename=$(echo $URL | sed -e 's|^http://||' -e 's/^www\.//' -e 's|/|_|g')
	icon_NAME="$avatar_filename"
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	imdb_page="$(wget -U firefox -qO - "$URL")"
	photo_line_number=$(( $(echo "$imdb_page" | grep -n -i '<div class="photo">' | cut -d: -f1 ) + 1 ))
	grabber_picture=$(echo "$imdb_page" | sed -n "$photo_line_number p" | sed "s|.*src=||" | cut -d\" -f2)
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	fi
}

```

flixster
```

#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=http://www.flixster.com/movie
}

grabber_account_grabber () {(
	web_account_page=$(wget -qO - "http://www.flixster.com/user/$1")
	web_page_url="http://www.flixster.com/"$(echo "$web_account_page" | grep 'li class="ratings"' | sed -e 's/.*href=\"//' -e 's/\"\ rel.*//' )
	web_page=$(wget -qO - "$web_page_url")
	pages_number=$(echo "$web_page" | grep 'First | Prev' | sed q | sed -e 's/.*pageNav=//' -e 's/\">Last.*//' )
	for i in $(seq 1 $pages_number)
		do web_page_new_url="$web_page_url"\&"offset=25"\&"pageNav=$i"
		web_page=$(wget -qO - "$web_page_new_url")
		titles=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*title=\"//' -e 's/\"\ href.*//' )
		urls=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*href=\"//' -e 's/\"\ \ >.*//' )
		number=$(echo "$titles" | wc -l )
		for i in $(seq 1 $number)
			do j=$(printf "%06d" $i)
			title=$(echo "$titles" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			url="http://www.flixster.com"$(echo "$urls" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			echo "$url"\|"$title"
		done
	done
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_name=$index.$avatar_title
	avatar_filename=$(echo $URL | sed -e 's|^http://||' -e 's/^www\.//' -e 's|/|_|g')
	icon_NAME="$avatar_filename"
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	flixster_page="$(wget -U firefox -qO - "$URL")"
	grabber_picture=$(echo "$flixster_page" | grep 'class="movieImg"' | sed q | sed -e 's/.*src=\"//' -e 's/\"\ width.*//' )
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	fi
}

```

---

### Post by Yuzem on 2008-12-22
> **Nonno Bassotto said:**
> Thank you, now it more or less works. :) At least the flixster grabber is working. The flixster2imdb grabber creates the avatars but they all link to
```

http://www.google.com/webhp

```
I guess somewhere avatar-factory cuts the full url, but I don't know why. Apart from this, I have to properly replace html entities, then it should be done. For now it looks like


The avatars link to the URL variable that is given by the account grabber function or the internal bookmark grabber.

If the account grabber gives the imdb url and the internal bookmark grabber gives the flixter url there will be problems when using the URL variable to get the cover.

If you want the flixter2imdb grabber to be exactly like the flixter grabber but linking to the imdb page instead (the cover also from flixter) then the grabber should be exactly the same but changing grabber_secondary_options function and a little the get_grabber_picture function:

flixster2imdb
```
#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=http://www.flixster.com/movie
}

grabber_account_grabber () {(
	web_account_page=$(wget -qO - "http://www.flixster.com/user/$1")
	web_page_url="http://www.flixster.com/"$(echo "$web_account_page" | grep 'li class="ratings"' | sed -e 's/.*href=\"//' -e 's/\"\ rel.*//' )
	web_page=$(wget -qO - "$web_page_url")
	pages_number=$(echo "$web_page" | grep 'First | Prev' | sed q | sed -e 's/.*pageNav=//' -e 's/\">Last.*//' )
	for i in $(seq 1 $pages_number)
		do web_page_new_url="$web_page_url"\&"offset=25"\&"pageNav=$i"
		web_page=$(wget -qO - "$web_page_new_url")
		titles=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*title=\"//' -e 's/\"\ href.*//' )
		urls=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*href=\"//' -e 's/\"\ \ >.*//' )
		number=$(echo "$titles" | wc -l )
		for i in $(seq 1 $number)
			do j=$(printf "%06d" $i)
			title=$(echo "$titles" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			url="http://www.flixster.com"$(echo "$urls" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			echo "$url"\|"$title"
		done
	done
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_name=$index.$avatar_title
	avatar_filename=$(echo $URL | sed -e 's|^http://||' -e 's/^www\.//' -e 's|/|_|g')
	icon_NAME="$avatar_filename"
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"

	#ADDED CODE:
	flixter_URL=$URL
	#URL=$(new imdb url)
	#the flixter_URL is to be use in the get grabber picture function
}

get_grabber_picture () {
	#EDITED CODE:
	flixster_page="$(wget -U firefox -qO - "$flixter_URL")"

	grabber_picture=$(echo "$flixster_page" | grep 'class="movieImg"' | sed q | sed -e 's/.*src=\"//' -e 's/\"\ width.*//' )
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	fi
}
```

A better solution (in my option) is to use the same grabber and to make a launcher. In that way you will be able to switch from flixter to imdb without having to rebuild the avatars.

flixter launcher (commented):
```
#!/bin/bash

#############Global Options
launcher=flixter    #this defines the launcher

#############User Options
#Load the the user config the get the launcher variable

if [ -f $app_config/grabbers/$launcher_name ]; then
	. $app_config/grabbers/$launcher_name
fi

#############Avatar Launcher 
#This is to use "avatar-factory -al etc..." to select
#a diferent launcher without changing the one set in 
#the config file. It can be used to make a nautilus/thunar
#menu to have an alternative launcher for your avatars.

if [[ -n $set_launcher ]]; then
	launcher=$set_launcher
fi

#############Launch
#This is the actual launcher

case $launcher in
	flixter )
		firefox "$URL"&
	;;
	imdb )
		query=$avatar_title
		firefox "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$query&btnI=I%27m+Feeling+Lucky&meta="
 &
	;;
	* )
		#If $launcher is epiphany, opera or any other this will launch the default url:
		$launcher "$URL"&
esac

```

---

### Post by Nonno Bassotto on 2008-12-22
Thank you, I'm starting to understand how it all works. I'm trying to make you launcher work, but... well, it doesn't. After a minor spelling correction it now looks like
```

#!/bin/bash

#############Global Options
launcher=flixster    #this defines the launcher

#############User Options
#Load the the user config the get the launcher variable

if [ -f $app_config/grabbers/$launcher_name ]; then
	. $app_config/grabbers/$launcher_name
fi

#############Avatar Launcher 
#This is to use "avatar-factory -al etc..." to select
#a different launcher without changing the one set in 
#the config file. It can be used to make a nautilus/thunar
#menu to have an alternative launcher for your avatars.

if [[ -n $set_launcher ]]; then
	launcher=$set_launcher
fi

#############Launch
#This is the actual launcher

case $launcher in
	flixster )
		firefox "$URL"&
	;;
	imdb )
		query=$avatar_title
		firefox "http://www.google.com/search?hl=en&q=site%3Aimdb.com%2Ftitle+$query&btnI=I%27m+Feeling+Lucky&meta="&
	;;
	* )
		#If $launcher is epiphany, opera or any other this will launch the default url:
		$launcher "$URL"&
esac

```

It is in a file called flixster inside /usr/local/share/avatar-factory/launchers, with execute permissions. But it looks like it's not executed. I can add whatever commands I like inside it and nothing happens when I double-click an avatar.

Moreover I don't understand fully how it works. First, it doesn't seem that it reads the options from the .avatar-factory/general file. Second, it is always called (if I understand right) with
```

avatar-factory -al flixster

```
because this is what the Launcher option in the grabber looks like:
```

Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"

```
So even if I declare the imdb option in the config files, it will be overwritten by the block
```

if [[ -n $set_launcher ]]; then
	launcher=$set_launcher
fi

```

By the way I've added a line in the flixster grabber to deal with html entities for & and ', now it looks like
```

#!/bin/bash

grabber_primary_options () {
	theme_name=dvd
	Link_or_Application=Link
	SOURCE_type=bookmarks
	SOURCE_filter=http://www.flixster.com/movie
}

grabber_account_grabber () {(
	web_account_page=$(wget -qO - "http://www.flixster.com/user/$1")
	web_page_url="http://www.flixster.com/"$(echo "$web_account_page" | grep 'li class="ratings"' | sed -e 's/.*href=\"//' -e 's/\"\ rel.*//' )
	web_page=$(wget -qO - "$web_page_url")
	pages_number=$(echo "$web_page" | grep 'First | Prev' | sed q | sed -e 's/.*pageNav=//' -e 's/\">Last.*//' )
	for i in $(seq 1 $pages_number)
		do web_page_new_url="$web_page_url"\&"offset=25"\&"pageNav=$i"
		web_page=$(wget -qO - "$web_page_new_url")
		titles=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*title=\"//' -e 's/\"\ href.*//' )
		urls=$(echo "$web_page" | grep 'onmouseover="mB' | sed -e 's/.*href=\"//' -e 's/\"\ \ >.*//' )
		number=$(echo "$titles" | wc -l )
		for i in $(seq 1 $number)
			do j=$(printf "%06d" $i)
			title=$(echo "$titles" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			url="http://www.flixster.com"$(echo "$urls" | nl -n rz -s "£" | grep "$j"£ | sed -e 's/.*£//' )
			echo "$url"\|"$title"
		done
	done
)}

grabber_secondary_options () {
	avatar_title=${avatar_title% - *}
	avatar_title=$(echo "$avatar_title" | sed -e "s/\&\#039;/\'/g" | sed -e 's/\&amp;/\&/g' )
	avatar_name=$index.$avatar_title
	avatar_filename=$(echo $URL | sed -e 's|^http://||' -e 's/^www\.//' -e 's|/|_|g')
	icon_NAME="$avatar_filename"
	Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"
}

get_grabber_picture () {
	flixster_page="$(wget -U firefox -qO - "$URL")"
	grabber_picture=$(echo "$flixster_page" | grep 'class="movieImg"' | sed q | sed -e 's/.*src=\"//' -e 's/\"\ width.*//' )
	if [[ -n $grabber_picture ]]; then
		wget -q $grabber_picture -O /tmp/thumb$$.${grabber_picture##*.}
		grabber_picture=/tmp/thumb$$.${grabber_picture##*.}
	fi
}

```

Thank you very much for your help, next time it will be easier ;)

---

### Post by Nonno Bassotto on 2008-12-22
Ok, I found it. I needed to declare it as an Application rather than a Link. So I attach the working version of it all. :) It contains the grabber, the launcher and the help file.

By the way, while inspecting your files I found some minor misprints which you may want to correct:
1) in /launchers/picture
```

if [ -f "$HOME/.avatar-factory/avatar-launcher" ]; then
	. $app_config/grabbers/$launcher_name
fi

```
should probably be
```

if [ -f "$app_config/grabbers/$launcher_name" ]; then
	. $app_config/grabbers/$launcher_name
fi

```
like the others.
2) The common help says
```

Source can be firefox, epiphany, opera. If there is no destination
	it wil try to use the config file. If there is no source the
	bookmarks for the defalut browser will be used.

```
where it should be "will" and "default".

Now I'm thinking about a Facebook grabber with links to your friends pages... ;)

---

### Post by Yuzem on 2008-12-22
> **Nonno Bassotto said:**
> Moreover I don't understand fully how it works. First, it doesn't seem that it reads the options from the .avatar-factory/general file. Second, it is always called (if I understand right) with
```

avatar-factory -al flixster

```
because this is what the Launcher option in the grabber looks like:
```

Launcher="avatar-factory -al $grabber_name --URL \"$URL\" --name \"$avatar_title\" --title \"$avatar_title\" --icon \"$icons_PATH/$icon_NAME.png\" --DND"

```
So even if I declare the imdb option in the config files, it will be overwritten by the block
```

if [[ -n $set_launcher ]]; then
	launcher=$set_launcher
fi

```

The set_launcher is only set when the -al option is used with an avatar for example:
```
avatar-factory -al avatar.desktop --launcher imdb
```
It isn't documented.

> **Nonno Bassotto said:**
> Ok, I found it. I needed to declare it as an Application rather than a Link. So I attach the working version of it all. :) It contains the grabber, the launcher and the help file.
Great! Can I include it in the next version?

> **Nonno Bassotto said:**
> 
By the way, while inspecting your files I found some minor misprints which you may want to correct:
1) in /launchers/picture
```

if [ -f "$HOME/.avatar-factory/avatar-launcher" ]; then
	. $app_config/grabbers/$launcher_name
fi

```
should probably be
```

if [ -f "$app_config/grabbers/$launcher_name" ]; then
	. $app_config/grabbers/$launcher_name
fi

```
like the others.
2) The common help says
```

Source can be firefox, epiphany, opera. If there is no destination
	it wil try to use the config file. If there is no source the
	bookmarks for the defalut browser will be used.

```
where it should be "will" and "default".
Thanks, both fixed.

> **Nonno Bassotto said:**
> 
Now I'm thinking about a Facebook grabber with links to your friends pages... ;)
I don't have a facebook account but I think that it would be a great addition. :)

---

### Post by Nonno Bassotto on 2008-12-23
> **Yuzem said:**
> Great! Can I include it in the next version?

I'd be glad if you did, but before doing so I realized I have to fix a bug with accented letters like àéèìòù.

---

### Post by Nonno Bassotto on 2008-12-23
For the facebook plugin the main problem is that you have to authenticate in order to access your friends list and their pages. In theory wget can use cookies from other browsers, so if you are logged in with firefox it should be doable. But the manual page for wget says
```

 --load-cookies file
           Load cookies from file before the first HTTP retrieval.  file
           is a textual file in the format originally used by Netscape’s
           cookies.txt file.

           You will typically use this option when mirroring sites that
           require that you be logged in to access some or all of their
           content.  The login process typically works by the web server
           issuing an HTTP cookie upon receiving and verifying your cre&#8208;
           dentials.  The cookie is then resent by the browser when
           accessing that part of the site, and so proves your identity.

           Mirroring such a site requires Wget to send the same cookies
           your browser sends when communicating with the site.  This is
           achieved by --load-cookies---simply point Wget to the location
           of the cookies.txt file, and it will send the same cookies
           your browser would send in the same situation.  Different
           browsers keep textual cookie files in different locations:

           Netscape 4.x.
               The cookies are in ~/.netscape/cookies.txt.

           Mozilla and Netscape 6.x.
               Mozilla’s cookie file is also named cookies.txt, located
               somewhere under ~/.mozilla, in the directory of your pro&#8208;
               file.  The full path usually ends up looking somewhat like
               ~/.mozilla/default/some-weird-string/cookies.txt.

           Internet Explorer.
               You can produce a cookie file Wget can use by using the
               File menu, Import and Export, Export Cookies.  This has
               been tested with Internet Explorer 5; it is not guaranteed
               to work with earlier versions.

           Other browsers.
               If you are using a different browser to create your cook&#8208;
               ies, --load-cookies will only work if you can locate or
               produce a cookie file in the Netscape format that Wget
               expects.

           If you cannot use --load-cookies, there might still be an
           alternative.  If your browser supports a ‘‘cookie manager’’,
           you can use it to view the cookies used when accessing the
           site you’re mirroring.  Write down the name and value of the
           cookie, and manually instruct Wget to send those cookies,
           bypassing the ‘‘official’’ cookie support:

                   wget --no-cookies --header "Cookie: <name>=<value>"


```

The problem is that latest firefox uses an sqlite file to store cookies, and I found no way to save them to a cookies.txt file. The last paragraph tells a possible solution, but it seems a little too demanding on the user to do so... after all we have computers to automate tasks. :confused:

---

### Post by Nonno Bassotto on 2008-12-23
Never mind, I found how to export the cookies with a python script.

[http://blog.schlunzen.org/2008/06/19/firefox-3-und-cookiestxt/](http://blog.schlunzen.org/2008/06/19/firefox-3-und-cookiestxt/)

---

### Post by Nonno Bassotto on 2008-12-23
Ok, here is the final working version of the flixster grabber

---

### Post by Yuzem on 2008-12-23
> **Nonno Bassotto said:**
> Never mind, I found how to export the cookies with a python script.

[http://blog.schlunzen.org/2008/06/19/firefox-3-und-cookiestxt/](http://blog.schlunzen.org/2008/06/19/firefox-3-und-cookiestxt/)
There is no need to use python, you can do it with wget. Also, I think it isn't a good idea to depend on firefox. I will add password support in the next version. The password will be the second parameter: "$2"

Save cookies with wget (the example works for youtube):
```
USER="your user name"
PASSWORD="your password"

wget \
    --save-cookies ~/Desktop/cookie \
    --post-data "login=$USER&password=$PASSWORD" \
    -O - \
   "http://www.youtube.com/login?next=/index" \
    > /dev/null
```
It should be similar for facebook.


> **Nonno Bassotto said:**
> Ok, here is the final working version of the flixster grabber
:)

---

### Post by Nonno Bassotto on 2008-12-23
In my test the login feature of wget didn't work, but I may investigate further. Any way, I don't think it would be a good idea to ask for the user password, since it would be in clear saved on the bash. I agree that relying on Firefox is not a good idea, but it shouldn't be difficult to add support for the most common browsers. I'm not sure what is the best way to do this, for now I'm using Firefox authentication.

I just have a problem with sed. I have a long line like
```

dfadfadkjhFriends.dnd(event, this, 0123456789, 'Meryl Streep')fjksa kflFriends.dnd(event, this, 1234567890, 'Ken Loach')sdaj djasifoj Friends.dnd(event, this, 1423536475, 'Antonio Banderas')dasda

```
and I'd like to extract the relevant pieces to obtain something like
```

Friends.dnd(event, this, 0123456789, 'Meryl Streep')
Friends.dnd(event, this, 1234567890, 'Ken Loach')
Friends.dnd(event, this, 1423536475, 'Antonio Banderas')

```
with a carriage return between each entry. So far I've not been able to do this, do you know a way?

---

### Post by Yuzem on 2008-12-23
> **Nonno Bassotto said:**
> In my test the login feature of wget didn't work, but I may investigate further.
I test it and the cookie get saved to the Desktop. I didn't test if the cookie works. Does it get saved for you?

> **Nonno Bassotto said:**
> 
Any way, I don't think it would be a good idea to ask for the user password, since it would be in clear saved on the bash.
The password is passed as a parameter to the account_grabber function and then it should be used to save a cookie. Then that cookie is loaded to get the page. I think it is safe. It doesn't get saved to the hard drive.

> **Nonno Bassotto said:**
> 
I just have a problem with sed. I have a long line like
```

dfadfadkjhFriends.dnd(event, this, 0123456789, 'Meryl Streep')fjksa kflFriends.dnd(event, this, 1234567890, 'Ken Loach')sdaj djasifoj Friends.dnd(event, this, 1423536475, 'Antonio Banderas')dasda

```
and I'd like to extract the relevant pieces to obtain something like
```

Friends.dnd(event, this, 0123456789, 'Meryl Streep')
Friends.dnd(event, this, 1234567890, 'Ken Loach')
Friends.dnd(event, this, 1423536475, 'Antonio Banderas')

```
with a carriage return between each entry. So far I've not been able to do this, do you know a way?
```
sed 's/Friends/\nFriends/g' | sed -e 1d -e 's/).*$//g'
```

Attached is the new version unfinished.

```
??.12.08------0.8.0
	+fixed nautilus icon size problem
	+new flixster grabber (by Nonno Bassotto from ubuntuforums)
	+enable to supply a password for bookmark grabbers
	+better cli output
	+html output
	+youtube: stream directly with vlc or mplayer using youtube-dl to get the url
```

You should add this variables to the grabber_primary_options function:
```
	account_grabber=yes
	account_password=yes
```

To use the html output option replace destination with --web:
```
avatar-factory -g imdb --web
```

To add avatar-factory as protocol handler, in firefox's address bar type about:config
Add a new key with this name:
network.protocol-handler.app.avatar-factory
value:
/usr/local/bin/avatar-factory

---

### Post by Nonno Bassotto on 2008-12-24
> **Yuzem said:**
> I test it and the cookie get saved to the Desktop. I didn't test if the cookie works. Does it get saved for you?


They are saved, but I've not been able to do a successful login this way. The best result was with the command
```

wget --save-cookies ~/cookies.txt --post-data "email=$user&pass=$password" -U firefox -O - "https://login.facebook.com/login.php?" > facebook.html

```
The page facebook.html seemed to be past the login, but there was a complain about my browser not supporting cookies. Even enabling
```

--keep-session-cookies

```
didn't work. I will investigate further.

> **Yuzem said:**
> 
The password is passed as a parameter to the account_grabber function and then it should be used to save a cookie. Then that cookie is loaded to get the page. I think it is safe. It doesn't get saved to the hard drive.


Actually it is. By default every command you type in the bash is saved under .bash_hystory. Not only it is saved, but you can easily show it out unwantedly by scrolling the bash history.

My opinion is that the best method is a sintax like
```

avatar-factory -g facebook ~firefox destination
avatar-factory -g facebook ~opera destination

```
according to the browser you use to login. Of course the choice is up to you, so if you go the password way, I will try to make wget work.

For now I attach a working but preliminary version of the facebook grabber. It assumes the script exportcookies.py is located under /usr/local/share/avatar-factory. By the way, is there a variable I can use for this path? Moreover it assumes you use firefox, it will be changed later according to your reply. :)

A final question. I had to create a launcher even if this is just a link grabber. The urls like
```

http://www.facebook.com/profile.php?id=123456789

```
were automatically cut to
```

http://www.facebook.com/profile.php

```
Is this a bug?

> **Yuzem said:**
> 
```
sed 's/Friends/\nFriends/g' | sed -e 1d -e 's/).*$//g'
```

Attached is the new version unfinished.

```
??.12.08------0.8.0
	+fixed nautilus icon size problem
	+new flixster grabber (by Nonno Bassotto from ubuntuforums)
	+enable to supply a password for bookmark grabbers
	+better cli output
	+html output
	+youtube: stream directly with vlc or mplayer using youtube-dl to get the url
```

You should add this variables to the grabber_primary_options function:
```
	account_grabber=yes
	account_password=yes
```

To use the html output option replace destination with --web:
```
avatar-factory -g imdb --web
```

To add avatar-factory as protocol handler, in firefox's address bar type about:config
Add a new key with this name:
network.protocol-handler.app.avatar-factory
value:
/usr/local/bin/avatar-factory

Thank you, I'm trying this one now. :)

---

### Post by Nonno Bassotto on 2008-12-24
Wow, the web output is absolutely cool!! :P
Still I have some problem, because for me is working only partially. I was able to create the page (by the way, it would be nice if it was automatically opened after the creation), but the links do not work. I entered the key you mentioned (maybe this should be done by the program) and when I clicked, Firefox asked if I wanted to associate the link with avatar-factory. I answered yes (and to remember the association) but now it does nothing. I don't get any feedback if it is trying to lanch anything.

---

### Post by Yuzem on 2008-12-24
> **Nonno Bassotto said:**
> They are saved, but I've not been able to do a successful login this way. The best result was with the command
```

wget --save-cookies ~/cookies.txt --post-data "email=$user&pass=$password" -U firefox -O - "https://login.facebook.com/login.php?" > facebook.html

```
The page facebook.html seemed to be past the login, but there was a complain about my browser not supporting cookies. Even enabling
```

--keep-session-cookies

```
didn't work.
In the example that I have read somewhere, you have to first save the cookie and then load it:
```
wget --save-cookies ~/cookies.txt --post-data "email=$user&pass=$password" -U firefox -O - "https://login.facebook.com/login.php?" > /dev/null
```
Then you access any page you want with:
```
wget --load-cookies ~/cookies.txt -U firefox -O - "https://facebook.com/" > facebook.html
```
Didn't test it.

> **Nonno Bassotto said:**
> 
Actually it is. By default every command you type in the bash is saved under .bash_hystory. Not only it is saved, but you can easily show it out unwantedly by scrolling the bash history.
Now I understand. You don't have to type the password in the command.
You type something like this:
```
avatar-factory -g facebook ~user destination
```
Then avatar-factory ask for your password. It doesn't get saved in the history. You can try it out in the latest version if you have added the variable:
```
account_password=yes
```

> **Nonno Bassotto said:**
> 
My opinion is that the best method is a sintax like
```

avatar-factory -g facebook ~firefox destination
avatar-factory -g facebook ~opera destination

```
according to the browser you use to login. Of course the choice is up to you, so if you go the password way, I will try to make wget work.
There is another problem with this method. What if you share your computer and you are not always loged in? You will have to login first in your browser and then run avatar-factory. It isn't very intuitive.

> **Nonno Bassotto said:**
> 
For now I attach a working but preliminary version of the facebook grabber. It assumes the script exportcookies.py is located under /usr/local/share/avatar-factory. By the way, is there a variable I can use for this path? Moreover it assumes you use firefox, it will be changed later according to your reply. :)
Yes, the variable is: $avatar_factory_PATH
The config folder is: $app_config
The cookies could be saved there for now.

> **Nonno Bassotto said:**
> 
A final question. I had to create a launcher even if this is just a link grabber. The urls like
```

http://www.facebook.com/profile.php?id=123456789

```
were automatically cut to
```

http://www.facebook.com/profile.php

```
Is this a bug?

That should not happend. Is still happening with the latest version?

> **Nonno Bassotto said:**
> Wow, the web output is absolutely cool!! :P
Still I have some problem, because for me is working only partially. I was able to create the page (by the way, it would be nice if it was automatically opened after the creation), but the links do not work. I entered the key you mentioned (maybe this should be done by the program) and when I clicked, Firefox asked if I wanted to associate the link with avatar-factory. I answered yes (and to remember the association) but now it does nothing. I don't get any feedback if it is trying to lanch anything.
That is a problem with firefox. Remove the key, set it again and when firefox ask to associate do not select avatar-factory. Navigate to avatar-factory and select it manually. That should work. I think that it is a bug in firefox.

---

### Post by dannytatom on 2008-12-24
Nonno, screenshots? :D

---

### Post by dannytatom on 2008-12-24
I'm having a problem using the Album Art downloader.  It finds my files alright, but when I click to download I get the following error:

```

Downloading cover images was interrupted by the following exception:

ExpatError: junk after document element: line 1, column 26

```

---

### Post by Nonno Bassotto on 2008-12-24
Mmm... I'm still not able to let wget download the right cookies. :( I will experiment a little bit more. The problem with the url being cut persists with the last version. By the way the same problem creates an issue with the change theme option: if I change theme the downloaded image is MY facebook photo.

Instead I solved the one with the web interface. :)

For now I don't know how to settle the cookies problem, but otherwise the grabber is working (with firefox). In any case you should be logged in when you use the avatars, otherwise the link won't open (facebook profiles are private).

This is a screenshot of the Facebook avatars, with the names erased. The flixster avatars look like any other dvd avatars; the only advantage is that they are automaticaly taken from your flixster account.

Merry Christmas :P

---

### Post by Yuzem on 2009-01-07
I didn't got a notification for the last two post... :(

> **dannytatom said:**
> I'm having a problem using the Album Art downloader.  It finds my files alright, but when I click to download I get the following error:

```

Downloading cover images was interrupted by the following exception:

ExpatError: junk after document element: line 1, column 26

```
I don't know about that. You can ask the developer.

> **Nonno Bassotto said:**
> Mmm... I'm still not able to let wget download the right cookies. :( I will experiment a little bit more. The problem with the url being cut persists with the last version. By the way the same problem creates an issue with the change theme option: if I change theme the downloaded image is MY facebook photo.
Thats strange, and the theme problem is even stranger.
You can try using the "$SOURCE_item" variable. That variable should give you exactly the output of the account grabber function. You will have to get the URL and the title from there.

Here there is a new version to test:
```
??.01.08------0.7.9
	+fixed nautilus icon size problem
	+new flixster grabber (by Nonno Bassotto from ubuntuforums)
	+enable to supply a password for bookmark grabbers
	+better cli output
	+youtube: stream directly with vlc or mplayer using youtube-dl to get the url
	+improved film theme
	+mame launcher: fullscreen by default
	+internal changes for all launchers
	+added --thumbnailer flag (imdb-thumbnailer has been integrated to allow the future implementation of folder thumbnailing)
	+set cover by drag & drop for all avatars (nautilus)
	+comix launcher: fixed problem with newest comix versions
	+automatic comic bookmarking with comix (wmctrl is required)
	+new theme: photos-2
```

A tiny screenshot of the improved film theme applied by the next version of imdb-thumbnailer:
[[IMG]http://img158.imageshack.us/img158/7549/imdbthumbnailerfilmnx9.th.png[/IMG]](http://img158.imageshack.us/my.php?image=imdbthumbnailerfilmnx9.png)

---

### Post by Yuzem on 2009-01-08
I forgot to say that for the auto bookmark option to work the following is needed:
* Build your avatars with the new version
* [The new version of comix]("http://www.getdeb.net/app/Comix")
* Set comix as the comic launcher
* wmctrl installed (sudo apt-get install wmctrl)

Thats all!

---

### Post by Nonno Bassotto on 2009-01-11
I'm having a look. :)
For the facebook plugin, I've been trying every known wget-based facebook bot I found with google, but none worked for me. Considering that you need to enable autologin in order to use the avatars, I don't think I will be changing much to the current plugin, except for the URl bug and maybe adding support for some more browsers

 If you think this is not good enough, I will keep it for personal use, or maybe post a deb here as an external, non official plugin. I simply do not have time to investigate further why wget authentication still doesn't work :(

If anyone has a facebook account and wants to try to improve this, feel free to do so and post it here.

---

### Post by ayoli on 2009-01-14
> **dannytatom said:**
> I'm having a problem using the Album Art downloader.  It finds my files alright, but when I click to download I get the following error:

```

Downloading cover images was interrupted by the following exception:

ExpatError: junk after document element: line 1, column 26

```

Maybe you can try this one : [http://mookooh.org/coverfinder/](http://mookooh.org/coverfinder/)

---

### Post by Yuzem on 2009-01-18
> **Nonno Bassotto said:**
> 
 If you think this is not good enough, I will keep it for personal use, or maybe post a deb here as an external, non official plugin. I simply do not have time to investigate further why wget authentication still doesn't work :(
It is ok, maybe you could put in the help about the the need of being logged in firefox. Also, if the user isn't logged, you could use "exit 1" then I will be able to say that he/she isn't logged in.

Anyway... here is the new version:
[http://www.gnomefiles.org/app.php/Avatar_Factory](http://www.gnomefiles.org/app.php/Avatar_Factory)

---

### Post by Nonno Bassotto on 2009-01-20
Here it is. The problem with the "change theme" option still exists, but I guess it is a problem with the way avatar-factory manages the URLs. I get the correct URL: indeed the facebook launcher is just
```

case $launcher in
	facebook )
		firefox "$URL"&
	;;
	* )
		#If $launcher is epiphany, opera or any other this will launch the default url:
		$launcher "$URL"&
esac

```

Inside the zip there is a python script to be placed inside /usr/local/share/avatar-factory. If you want to place it somewhere else just change the line 15 in the grabber
```

else /usr/local/share/avatar-factory/exportcookies.py facebook $cookies

```
to whatever you see fit.

---

### Post by Yuzem on 2009-01-20
> **Nonno Bassotto said:**
> Here it is. The problem with the "change theme" option still exists, but I guess it is a problem with the way avatar-factory manages the URLs. I get the correct URL: indeed the facebook launcher is just
I think that I don't understand the problem. Is it with the grabber or the launcher. Is the "change theme" thing about the -t or --theme flag or I am completely lost?

> **Nonno Bassotto said:**
> 
indeed the facebook launcher is just
```

case $launcher in
	facebook )
		firefox "$URL"&
	;;
	* )
		#If $launcher is epiphany, opera or any other this will launch the default url:
		$launcher "$URL"&
esac

```

The launchers have been changed with the last version from this:
```
#!/bin/bash

#############Global Options
launcher=facebook    #this defines the launcher

#############User Options

if [ -f $app_config/grabbers/$launcher_name ]; then
	. $app_config/grabbers/$launcher_name
fi

#############Avatar Launcher 

if [[ -n $set_launcher ]]; then
	launcher=$set_launcher
fi

#############Launch

case $launcher in
	facebook )
		firefox "$URL"&
	;;
	* )
		#If $launcher is epiphany, opera or any other this will launch the default url:
		$launcher "$URL"&
esac
```

to this:
```
#!/bin/bash

launcher_options () {
	launcher=facebook    #this defines the launcher
}

launcher () {
	case $launcher in
		facebook )
			firefox "$URL"&
		;;
		* )
			#If $launcher is epiphany, opera or any other this will launch the default url:
			$launcher "$URL"&
	esac
}

```
The options in the launcher_options function and the launcher in the launcher function.

Even simpler:
```
#!/bin/bash

launcher_options () {
	launcher=firefox    #this defines the launcher
}

launcher () {
	$launcher "$URL"&
}

```

> **Nonno Bassotto said:**
> 
Inside the zip there is a python script to be placed inside /usr/local/share/avatar-factory
Thats ok.

---

### Post by Nonno Bassotto on 2009-01-21
The problem is: the $URL variable is something like
```

http://www.facebook.com/profile.php?id=1234567890

```
I can use it with the launcher and a simple
```

firefox $URL &

```
works fine. Of course it is just a link, so I thought that I may declare the avatar type as 'Link' and it should work. Instead every link leads to
```

http://www.facebook.com/profile.php

```
which, vif you are logged in, is your own profile.

Now, it is not very relevant, since I can declare that the avatar is of type 'Application' and use a simple launcher. Still, when one uses the avatar grabber to change theme, avatar factory uses
```

http://www.facebook.com/profile.php

```
instead of the correct URL. So it downloads your own photo every time you change theme. This is not so important, since there is just one sensible theme for facebook, namely shadow, but I thought I should let you know.

---

### Post by Yuzem on 2009-01-21
Ok, the theme problem is fixed. I hope, didn't test it...
I think the other problem is caused by the '?' char. The url is not passed correctly by thunar or nautilus but if I encode it using '%3F' it doesn't work neither.
Try to drag and drop from the addresbar to the desktop an url with the '?' char. For example:
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6590373](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6590373)

Open the file in gedit. You will see that the url isn't encoded and it doesn't work. Maybe a bug in thunar and nautilus?

```
??.??.08------0.7.9.1
	+music launcher: fixed problem with totem, amarok and some changes
	+avatar grabber: some fixes
```

---

### Post by Yuzem on 2009-01-21
double post :(

---

### Post by Nonno Bassotto on 2009-01-25
Ok, now the "change theme" works as expected:):):)

---

### Post by Dawei87 on 2009-03-05
ok. i just found this and thought i'd give it a shot. im not sure im doing all the settings right or not. i put the source for my music files in (correctly this time) but when i hit finish it tries to process the grabber and then says "something went wrong". i will attach an image of what my settings look like.

p.s. where did you get the background pattern for nautilus for your videos? and can you set a specific pattern for certain folders?

---

### Post by Yuzem on 2009-03-05
> **Dawei87 said:**
> i put the source for my music files in (correctly this time) but when i hit finish it tries to process the grabber and then says "something went wrong".
You must specify a destination. For example:
```
mkdir ~/Albums
```
That should create a folder called Albums in your home folder. Select that folder as the destination.

> **Dawei87 said:**
> p.s. where did you get the background pattern for nautilus for your videos?
The backgrounds are in the .tar.gz2 archive.

> **Dawei87 said:**
> can you set a specific pattern for certain folders?
Yes, in nautilus: edit > backgrounds and emblems > drag it with the middle mouse button. If you don't have that button try dragging it with shift or control key pressed.

---

### Post by Dawei87 on 2009-03-05
ok. ive made some progress. i made a ~/Albums and ran avatar-factory again. it still said something went wrong, but now i have 107 album covers in ~/Albums, and at the bottom of ~/Music. a lot of them are duplicates, and i also have about 380 albums, so it didnt manage to get all of them. and they also don't do anything when i click on them. i'll attach my music grabber settings again. thanks again for all the help!

i actually just noticed, it did put a little widget on my desktop when i clicked on the album cover, but the widget was incredibly small and nothing really seemed to happen other than that.

---

### Post by Yuzem on 2009-03-05
> **Dawei87 said:**
> ok. ive made some progress. i made a ~/Albums and ran avatar-factory again. it still said something went wrong, but now i have 107 album covers in ~/Albums, and at the bottom of ~/Music. a lot of them are duplicates
It should not create anything in ~/Music maybe they are from a previous attempt.

> **Dawei87 said:**
> i also have about 380 albums, so it didnt manage to get all of them.
It will only work for folders with music inside and a picture that will be used as the cover.

> **Dawei87 said:**
> and they also don't do anything when i click on them.
Rhythmbox is not supported since it doesn't allow to play anything with a command.
You can use any of the following players:
totem
amarok
moc
mpd (sonata, Gimmix, Guimup, etc)
muine
quodlibet
banshee
xmms
exaile

> **Dawei87 said:**
> thanks again for all the help!
You are welcome. :)

> **Dawei87 said:**
> i actually just noticed, it did put a little widget on my desktop when i clicked on the album cover, but the widget was incredibly small
You can right click on it an resize it.

---

### Post by phyrewall on 2009-03-10
Just something I've run into in Jaunty Nautilus, not sure if it's been mentioned before:

After creation, the .desktop files won't show the icon/avatar until you dbl-click them, and choose "Trust" from the window that pops up... seems you have to do this for all of them, luckily after clicking "Trust" it doesn't run the command, so you can select all files, press enter, and then click "Trust" a hundred times.

---

### Post by Yuzem on 2009-03-10
I can't test it because I don't have Jaunty but I will install it when it get released.

Could it be a problem with permissions?
You can check it with:
```
ls -l some_avatar.desktop
```

If the launchers from /usr/share/applications are working it is just a matter of checking what is the difference with the avatars.

---

### Post by Yuzem on 2009-03-11
> **Dawei87 said:**
> ok. ive made some progress. i made a ~/Albums and ran avatar-factory again. it still said something went wrong
It seems that there was an error in avatar-factory.
Can you try the attached version?

---

### Post by breakolami on 2009-10-02
Hello

I try to install avatar factory but install not work

In terminal sudo ./install but have error message

> cp: ne peut évaluer `./avatar-factory.1': Aucun fichier ou dossier de ce type

Can't find avarat-factory.1

What to do

thanks and sorry my english is not good

---

### Post by Gourgi on 2009-10-02
> **breakolami said:**
> Hello

I try to install avatar factory but install not work

In terminal sudo ./install but have error message



Can't find avarat-factory.1

What to do

thanks and sorry my english is not good

you can install the .deb version if you want.
```
wget http://launchpadlibrarian.net/28183014/avatar-factory-0.8.deb
sudo dpkg -i avatar-factory-0.8.deb

```

---

### Post by Sharaazad on 2009-11-10
> **Yuzem said:**
> 
The music widget (support drag and drop):
[[IMG]http://img374.imageshack.us/img374/8009/musicwidgetkr4.th.jpg[/IMG]](http://img374.imageshack.us/my.php?image=musicwidgetkr4.jpg)


How to obtain this effect (the second one)?
I can't figure it out :(

---

### Post by Nonno Bassotto on 2009-11-10
IIRC drag an album cover over the album widget.

---

### Post by Sharaazad on 2009-11-11
I don't know how to start the music widget... i use avatar-factory --widget but nothing happens :(

Second question:
How did you remove the menubar in nautilus?
[http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.png](http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.png)


edit:
well, i created my avatars with the "widget" option enabled. Now when i click on a launcher a "music_widget.desktop" appear on my desktop.If i launch it, the last launcher used before is launched. If i drag and drop one of the other launcher on it,then the music_widget dont'change.

---

### Post by Yuzem on 2009-11-12
> **Sharaazad said:**
> 
Second question:
How did you remove the menubar in nautilus?
[http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.png](http://img379.imageshack.us/img379/758/avatarfactoryfg3lk3.png)

I use [globar menu bar]("http://www.google.com/search?q=global+menu+bar+karmic")

> **Sharaazad said:**
> 
well, i created my avatars with the "widget" option enabled. Now when i click on a launcher a "music_widget.desktop" appear on my desktop.If i launch it, the last launcher used before is launched. If i drag and drop one of the other launcher on it,then the music_widget dont'change.

There is no need to create the avatars with the option enabled, you can turn it on and off any time you want. There are to modes for the music widget.

In the simpler mode the widget will change every time you click on an avatar and you can drag and drop avatars to add them to the playlist instead of replacing it.
For this you only need to add:
```
music_widget=yes
```
To:
```
~/.avatar-factory/grabbers/music
```
You can set this from the gui.
You can read:
avatar-factory -g music --help

For The second mode you need to run:
```
avatar-factory --widget
```
This is exactly as before with the difference that the widget will be hidden if the player isn't running.

Ok, I just tried and it seems that there is a problem with the drag and drop functionality. I don't know if it is a problem with Karmic or a bug in avatar-factory. I will check it.

---

### Post by Yuzem on 2009-11-27
The problem with drag and drop has been fixed. If you don't want to wait the following should work:

```
sudo gedit $(which avatar-factory)
```

Line 229 should be:
```
DND[$((++num))]=$1
```

Change it to:
```
DND+=("$1")
```

Thats all.

---

### Post by R2D2! on 2009-12-06
Hey, I found a solution for the nameless .desktop in Nautilus.

Instead of leaving it empty, just use a non-breaking space (**#xA0**). Using a common space (#x20) doesn't work.

Also, the --icon-size seems to be broken in Karmic, due to ~/.nautilus/metafiles/ been moved to ~/.local/share/gvfs-metadata/&#8200;

—Ilhu&#305;temoc

---

### Post by Nonno Bassotto on 2009-12-07
Wow, someone is actually using Ubuntu in Esperanto! :D

---

### Post by Yuzem on 2009-12-07
Thanks R2D2!, I will add those fixed in the next version.

---

### Post by R2D2! on 2009-12-07
> **R2D2! said:**
> [...]due to ~/.nautilus/metafiles/ been moved to ~/.local/share/gvfs-metadata/

It seems that the structure in ~/.local/share/gvfs-metadata/ is different, so you'll have to rewrite the code for that option :roll:

—Ilhu&#305;temoc

---

### Post by R2D2! on 2009-12-08
I see that there's no apparent support for Rhythmbox, but there's rhythmbox-client, which does the job.

Here are some example commands to run (yes, I'm a noob, so don't expect anything ellaborate):

For the avatar:
```
rhythmbox-client --no-present --clear-queue --enqueue "$1" "$2" "$n" --play
```
Where $1 $2 $n are individual files. You can also add the whole folder, but if you have shuffle turned on, it will scramble the playlist.

For the music widget:
```
rhythmbox-client --no-present --enqueue "$1" "$2" "$n" --play
```
The difference here is that the avatar clears any previous playlist, but the widget adds them one after the other.

However, I don't know how to put them inside avatar-factory, but I hope this helps.

&#8212;Ilhu&#305;temoc

---

### Post by Yuzem on 2009-12-08
> **R2D2! said:**
> It seems that the structure in ~/.local/share/gvfs-metadata/ is different, so you'll have to rewrite the code for that option :roll:
—Ilhu&#305;temoc
mmm... it seems that it has changed a lot, I thought that it was just the path. I won't be able to fix that for now.

> **R2D2! said:**
> I see that there's no apparent support for Rhythmbox, but there's rhythmbox-client, which does the job.

Here are some example commands to run (yes, I'm a noob, so don't expect anything ellaborate):

For the avatar:
```
rhythmbox-client --no-present --clear-queue --enqueue "$1" "$2" "$n" --play
```
Where $1 $2 $n are individual files. You can also add the whole folder, but if you have shuffle turned on, it will scramble the playlist.

For the music widget:
```
rhythmbox-client --no-present --enqueue "$1" "$2" "$n" --play
```
The difference here is that the avatar clears any previous playlist, but the widget adds them one after the other.

However, I don't know how to put them inside avatar-factory, but I hope this helps.

—Ilhu&#305;temoc
Yes, it helps, thanks!

---

### Post by crimp2333 on 2009-12-15
Hey,
i have Cruncheee  (Crunchbang) on my Asus 901.

I had Pcmanfm as filemanager but switched to thunar.

Now I use avatarfactory for my musicfolders. Everthing is fine as it is on my ubuntu desktop-pc at home (with nautilus).

Just the Icons are too small without pressing ctrl+ "++" everytime. They are in ~/music.
In Nautilus on my other computer the icon-size-setting does a great job. I read that it has no sense for Thunar so I set 27.

Is there a way to set the iconsize in Thunar just for one folder(~/music). When I press ctrl+""++" the size for all folders in my system is changed,that's bad!

Hope you understood my bad english, sorry for that. But I need your help!!!

---

### Post by Yuzem on 2009-12-15
> **crimp2333 said:**
> 
Is there a way to set the iconsize in Thunar just for one folder(~/music). When I press ctrl+""++" the size for all folders in my system is changed,that's bad!

Not that I know. Thunar doesn't allow to have settings by folder.

---

### Post by R2D2! on 2009-12-26
@Nonno Bassotto: I've seen you made a Facebook grabber. I think it will be easier using [FBMCD]("http://fbcmd.dtompkins.com/commands/ppics"), and you would have no cookies problems or browser dependencies. However, you need to configure FBCMD first.

---

### Post by Nonno Bassotto on 2009-12-27
Thank you very much for the suggestion. I have currently no time, but it would be nice to rewrite the grabber this way. Maybe when I have more spare time...

---

### Post by R2D2! on 2009-12-27
Is there any tutorial about creating a new grabber? I'm too lazy to search through the whole thread...

—Ilhu&#305;temoc

---

### Post by Yuzem on 2009-12-27
> **R2D2! said:**
> Is there any tutorial about creating a new grabber? I'm too lazy to search through the whole thread...

No, I will try to explain but I don't know if I do remember correctly.

You need to create one file in:
```
/usr/local/share/avatar-factory/grabbers
```
You can take a look to the grabbers there.
The filename should be the name of the grabber.
Example:
```
/usr/local/share/avatar-factory/grabbers/your-grabber
```

The file must contain three functions:
grabber_primary_options
grabber_secondary_options
get_grabber_picture

**grabber_primary_options**
This function is executed only one time and contains the following options:
theme_name=theme
[INDENT]theme should be the name of any available theme, it defines the theme used by default.[/INDENT]
Link_or_Application=value
[INDENT]value should be Link or Application. This defines the default mode for the avatars, In Application mode the avatar launcher is used, in Link mode the default filemanager action takes place, for example, on folders, the folder should be opened[/INDENT]
SOURCE_type=value
[INDENT]This defines the grabber source type. There are three source types: value should be folders, files or bookmarks.[/INDENT]
SOURCE_filter=value
[INDENT]This must be used when source type is files or bookmarks. value must be a comma separated list of extensions or urls to filter the items to process.[/INDENT]

The other two functions are executed one time for every item.

**grabber_secondary_options**
avatar_name=
[INDENT]Defines the visible name of the avatar.[/INDENT]
avatar_filename=
[INDENT]Defines the real name of the avatar.[/INDENT]
icon_NAME=
[INDENT]Defines the icon name.[/INDENT]
Launcher=
[INDENT]This options defines the command that will be executed in Application mode.[/INDENT]
URL=
[INDENT]This is used in Link mode by the filemanager.[/INDENT]

**get_grabber_picture**
grabber_picture=
[INDENT]This function defines only the variable "grabber_picture" that should be the full path or url to the picture that will be used to make the icon.[/INDENT]

Ok, thats all, I probably forgot some things. If you have any question, just ask.
One last thing: The variable $SOURCE_item is the full path or url of the current item.

---

### Post by R2D2! on 2009-12-30
Well, I almost finish the FBCMD grabber. There's a small issue: you have to select /tmp/facebook as the source folder. Can this be set as default? or Is there a better way to achieve this?

—Ilhu&#305;temoc

---

### Post by Yuzem on 2009-12-31
> **R2D2! said:**
> Well, I almost finish the FBCMD grabber. There's a small issue: you have to select /tmp/facebook as the source folder. Can this be set as default? or Is there a better way to achieve this?


It can't be set as default but if you set the options from the gui you can run the grabber with only:
```
avatar-factory -g fbcmd
```

Maybe a more correct but complicated way to do it from the user perspective is to remove the following from grabber_secondary_options:
```
if [ ! -e "/tmp/facebook" ]; then
	fbcmd PPICS =all /tmp/facebook "-pf=[tid]-[tname].jpg" -ppsize=1
fi
```

You first run:
```
fbcmd PPICS =all some-folder "-pf=[tid]-[tname].jpg"
```

And then:
```
avatar-factory -g fbcmd some-folder destination
```
This way is more configurable.
I think that the tmp folder content gets deleted with every restart.
You can add an alias to ~/.bashrc
```
alias avatar-factory-fbcmd='fbcmd PPICS =all /tmp/facebook "-pf=[tid]-[tname].jpg" -ppsize=1 && avatar-factory -g fbcmd some-folder destination'
```
And run it with:
```
avatar-factory-fbcmd
```

But it is your choice...

---

### Post by R2D2! on 2010-01-02
Or how can I include the source folder as a variable in my grabber? So a user just have to run one command

—Ilhu&#305;temoc

---

### Post by Yuzem on 2010-01-02
It is: $SOURCE_input

But there is a problem. If you run fbcmd in grabber_secondary_options there will be nothing to process since that function is executed after the list of items get generated. That means that avatar-factory will try to get all the pics from the specified folder but it will be empty.

If you put fbcmd in grabber_primary_options there will be no imput folder since the options are generally specified in this order:
avatar-factory -g grabber source destination
You could try:
avatar-factory source -g grabber destination
I don't know if it will work.

---

### Post by Sharaazad on 2010-01-16
> **Yuzem said:**
> The problem with drag and drop has been fixed. If you don't want to wait the following should work:

```
sudo gedit $(which avatar-factory)
```

Line 229 should be:
```
DND[$((++num))]=$1
```

Change it to:
```
DND+=("$1")
```

Thats all.

Thx i'll try :)

---

### Post by Yuzem on 2010-02-07
Hello, I learned some new tricks and made a new application:
[[IMG]http://3.bp.blogspot.com/_EbNPUgfUDXs/S35zizifkbI/AAAAAAAAAsI/imKgYBOPBIk/s320/figuritas-0.jpg[/IMG]]("http://yuzem.blogspot.com/p/figuritas.html")
Enjoy! :D

---

### Post by Nonno Bassotto on 2010-02-08
Cool! :D

I think you should open a new thread to attract more testers. The only thing which is not clear to me is what is supposed to be working and what not. Maybe if you publish a changelog or something like that, it will be easier to help you testing.

---

### Post by Yuzem on 2010-02-08
> I think you should open a new thread to attract more testers.
The problem is that I will have to keep that thread updated with every new version in addition to the blog. Anyway I'm not sure about this, I will give it a little more time.
Bugs can be reported in [launchpad]("https://bugs.launchpad.net/figuritas") or by commenting on the blog.

> The only thing which is not clear to me is what is supposed to be working and what not.
When you open figuritas there is a link to the help page, you can read that to have an idea.
I have to add there how to set custom icons which is pretty easy:
1. Click on a movie or a director, character, etc... a new tab should open.
2. Click on the corresponding icon to open the icon selector.
3. Select an icon.

> Maybe if you publish a changelog or something like that, it will be easier to help you testing.
There is no changelog because it is the first version, I will add one with the next release. :)

---

### Post by micmic on 2010-02-15
Hi,
   I have this error using figuritas:

```
http://localhost:9009
Error: unrecognized override.ini path.
```

Can you help me?

Thanks in advance

---

### Post by Yuzem on 2010-02-15
You can try:
```
rm -r ~/.prism/figuritas
```

I had opened a new thread [here]("http://ubuntuforums.org/showthread.php?p=8832151")

Report anything related to figuritas there.

---

