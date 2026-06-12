---
title: "iPod terminal program"
date: 2008-11-14
forum: Programming Talk
---

### Post by transmition on 2008-11-14
While I am fairly new to Ubuntu, this does not seem to be a fairly difficult task. Let me give you an explanation of my situation.

I have recently downloaded program called mpg123. While it can play mp3's fairly well, if you want to play a song, you must either navigate directly to the folder:

```
mpg123 ~/Music/iTunes/NOFX/"25 or 26 songs that were not good enough to go on our other albums"/"total bummer.mp3"
```

Or create a list of all your songs and play that.

My question, is that would it be possible to create a program or shell script that would present you with a list of options, say:

songs
artists
albums

where you would use the arrow keys to select your option. Then, the songs option would present you a list of all the mp3's in your Music directory, and by highlighting it and hitting enter, it would launch the command 
```
mpg123 ~/Music/"path of selected song"/"path of selected song"/"selected song.mp3"
```

If you are not familiar with the structure of the itunes style of managing songs (which this program would be based on, for all those people who copied an pasted their itunes folder into ubuntu)
it goes something like this: iTunes--> "Artist number one folder" "Artist number two folder" "Artist number three folder"

From Artist number one folder, it goes --> "Album number one folder" "Album number two folder" "Album number three folder"

From Album number three folder, it goes --> song1, song2, song3

So:
```
itunes-->Artists-->Albums-->songs
```


Should a user select the artists option, they would be presented with a list of all the artist folders in the itunes folder. They would then select one of the artists, and be taken to all the album folders within the selected artist folder.

If the user selected albums, then they would be presented all the album folders. Again, they would select an album, and be presented with all the mp3's in that folder. They would then select an mp3, to have it played by mpg123.

Can anyone give me any advice as to how I should go about doing this, or any places to look for information. Any help would be appreciated.

Also, if any of my above instructions were confusing, look at the music section on an iPod, it is virtually the same concept.

---

