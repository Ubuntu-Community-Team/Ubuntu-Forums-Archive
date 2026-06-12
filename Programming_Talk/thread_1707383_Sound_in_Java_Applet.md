---
title: "Sound in Java Applet"
date: 2011-03-15
forum: Programming Talk
---

### Post by sxe4ever on 2011-03-15
[FONT=Courier New][SIZE=4]I'm writing a game using a Java Applet and the game  runs fine in every operating system except when I put sound into it.  When the sound is put into it, it runs fine on every operating system  (including Mac) except Ubuntu where it won't  advance any further than where the sound clips are attempted to be played. I've edited the code where it now reads in the player's OS and if it's Linux it doesn't play the sound/music (still loads the files however), and it runs fine like this.

When I run the game through Eclipse the game runs, but the sound is delayed heavily if it plays at all, which it doesn't most of the time.

I'm not sure  if it's related at all, but when when I try to run Windows using  VirtualBox on Ubuntu the same thing happens.
[/SIZE][/FONT] [FONT=Courier New][SIZE=4]
If tried loading the sound files several different ways, with the most  recent way being AudioClips.

I've read a number of places that it's a compatibility issue with Iced Tea because it uses OpenJDK or something, but I want the game to be compatible with Iced Tea so that it's compatible with as many computers as possible without having to have special customizations made to computers. I am not using the OpenJDK for Eclipse but the actual Sun release... Sorry, I forgot it's name. 

Does anybody know what could be causing  this???[/SIZE][/FONT][FONT=Courier New][SIZE=4] Please & thank you for any information!!!!
[/SIZE][/FONT]

---

### Post by PaulM1985 on 2011-03-15
Have you got any code to show the sort of things that you are doing?  What are you using to play sound, AudioClip?

Does this example work:
[http://www.dreamincode.net/forums/topic/14083-incredibly-easy-way-to-play-sounds/](http://www.dreamincode.net/forums/topic/14083-incredibly-easy-way-to-play-sounds/)
?

Paul

---

### Post by sxe4ever on 2011-03-15
From the main public class:
AudioClip intro, currentsound;

From the init class:
try
{
   intro = getAudioClip(getDocumentBase(), "newintro.wav");
}
catch (Exception e) {}

Then when I'm wanting to play the song, where the program fails:
currentSound = intro;
currentSound.loop();

The example that you gave seems to be the same thing that I'm doing except they're using a URL instead of a file name and they also have a class dedicated to the sound clip. Would this make a big enough difference to justify it?

---

### Post by PaulM1985 on 2011-03-15
The main differences appear to be that you are using getAudioClip instead of newAudioClip.  You are also using getDocumentBase instead of getCodeBase.  I am not sure if these make too much of a difference, but it may be worth experimenting with.  getCodeBase would probably be the thing I looked closer at.  Do you know if getCodeBase and getDocumentBase return the same thing?

Also, you could create the URL and check that the URL is definately pointing at the song clip that you are expecting.

Paul

---

### Post by sxe4ever on 2011-03-17
It seems like the biggest difference between getAudioClip and newAudioClip is that the newAudioClip is used for URLs and getAudioClip is for relative file locations. I tried switching to newAudioClip however and using a URL instead of a relative file name, and had the same results as previously.

---

