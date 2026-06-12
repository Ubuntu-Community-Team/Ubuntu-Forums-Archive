---
title: "custom login sound"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by muted1987 on 2008-05-19
hey all i just worked out how to change the login sound so i thought id give it a go.

anyway i used mpg123 to convert my mp3 file to wav so that i could use it, although no sound is played when logging in now.

the only thing i can think of is that the file is to large and wont play is this right???


thanks jordan

---

### Post by nowin4me on 2008-05-19
> **muted1987 said:**
> 

anyway i used mpg123 to convert my mp3 file to wav so that i could use it, although no sound is played when logging in now.

the only thing i can think of is that the file is to large and wont play is this right???


I think it's the File type thats the problem try converting it into a .ogg

---

### Post by muted1987 on 2008-05-19
thx for the idea i tried anyway but it states that it has to be a valid .wav file when selecting the .ogg file

---

### Post by Joeb454 on 2008-05-19
If you go to System > Preferences > Sounds and choose the 2nd tab, this allows you to choose the sounds for logging in etc.

Though having found the files on the system, they are all .wav files so you should be ok with .wav's :confused:

---

### Post by muted1987 on 2008-05-19
yer this is why im comfused i am thinking of putting the .wav file in the same directory to see if that makes a difference ill post back with results

---

### Post by muted1987 on 2008-05-19
okay so moving it to /usr/share/sounds did not work im definetly thinking that the filesize is to big for a login sound. anyone know of any file size restriction??

---

### Post by Joeb454 on 2008-05-19
How big is your file? You may also want to check the file size of the default files (should be really easy now they're in the same dir ;)) To see if they are all a similar size :)

---

### Post by muted1987 on 2008-05-19
wow it is at 50meg (mp3 format at 5.3meg) whereas the other are all around 2meg or less definetly could be size problem

so much for listening to bob marleys exodus when i login :(

---

### Post by Joeb454 on 2008-05-19
:lolflag: Would it not work as an mp3 file then?

---

### Post by muted1987 on 2008-05-19
nope it specifically says it has to be wav file when you highlight others :( im not going to give up though lol ill stumble across the solution later when i stop looking as is always the way.

---

### Post by nowin4me on 2008-05-19
> **muted1987 said:**
> wow it is at 50meg (mp3 format at 5.3meg) whereas the other are all around 2meg or less definetly could be size problem

so much for listening to bob marleys exodus when i login :(

Can't you cut it down?

---

### Post by muted1987 on 2008-05-19
define cut down do you mean take a 10sec clip from the file ?? or shrink the wav file altogether..



also another thing i have found is that the login.wav has a link target and my file does not could this be anything to do with it?

---

### Post by Joeb454 on 2008-05-19
You could possibly use Audacity to cut the file size down to a specific part of the song that you want, then convert it to a wav and see what the file size is?

---

### Post by muted1987 on 2008-05-19
ok so im going to need a quick howto with audacity if you dont mind

---

### Post by Joeb454 on 2008-05-19
I've never used it properly myself sorry :( I just know of it, and I know it can do that

---

### Post by philinux on 2008-05-19
In the meantime. Use places>search for files

.wav in file system.

Tons to try and use. some good ones in open office.

---

### Post by nowin4me on 2008-05-19
> **muted1987 said:**
> define cut down do you mean take a 10sec clip from the file ?? or shrink the wav file altogether..



also another thing i have found is that the login.wav has a link target and my file does not could this be anything to do with it?

Yeah take a couple of mins of the song AND maybe save it as at a lower quietly that should help.

I am not sure on link target thing it could possible have somthing to do with it.

Also I don't now how to use Audacity.

---

### Post by muted1987 on 2008-05-19
ok found out it is definetly a filesize (thx to audacity and a bit of brain power) problem now what i would like to know is (yes youve guessed it) the size limit for system sounds

---

### Post by Joeb454 on 2008-05-19
Aim for 2Mb at first, because then you know it will work, plus I think that anything more than 15 seconds would get annoying after a while :p

---

### Post by nowin4me on 2008-05-19
> **muted1987 said:**
> ok found out it is definetly a filesize (thx to audacity and a bit of brain power) problem now what i would like to know is (yes youve guessed it) the size limit for system sounds

Well if you have a look at "login.wav" you will see it's 1.3MB so I am guessing the max would be 1.5MB I don't now thought.

---

### Post by muted1987 on 2008-05-19
ok ive got it to 2meg thats about 15 secs ima gonna levae it at that thanks fo everyones help

---

### Post by Joeb454 on 2008-05-19
Ok but first you have to let us know - did it work? :)

---

### Post by muted1987 on 2008-05-19
lol thats the one thing i forgot to do test it

okay so letme see ctrl+alt+backspace ... logging in.... sound plays hoorah 

yup works fine just the right length for my panels and widgets to start :guitar:

---

### Post by Joeb454 on 2008-05-19
Awesome :) Glad you got it sorted, might have to give it a go myself now...but just gotta choose a song

---

### Post by muted1987 on 2008-05-19
audacity was easy to use just highlight the parts before and after then clip you want and press delete so easy then just export it from file to wherever you want and if you need help converting from mp3 to wav let me know and ill help tehre to

---

### Post by Joeb454 on 2008-05-19
Thanks, I'll post back here when I've done it (probably some time later tonight)

Edit: Guess I'll have to convert some of my music to mp3's in order to do this :p

---

### Post by muted1987 on 2008-05-19
nope you wont have to convert anything to mp3 just .wav if there not already which you can do in three simple steps



1. in terminal sudo aptitude install mpg123

2. also in terminal navigate to folder .wav is in

3. also in terminal mpg123 -w file.wav file.mp3

renaming file to the name if the wav file


jsut note with that command you have to put what you want to convert to first

---

