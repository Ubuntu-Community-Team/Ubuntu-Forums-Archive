---
title: "sound in linux"
date: 2009-06-23
forum: Programming Talk
---

### Post by cmay on 2009-06-23
hi.
i would like to try creating a small command line media player. it should not do anything else than just play some audio files and i am not  experienced yet. so its for a learning experience. what is the best library to use  for this.  language is c. 

thanks.

---

### Post by Darkhack on 2009-06-23
The situation with sound in Linux has received a lot of criticism.  It can be rather messy at times.  There are two sound driver frameworks, Open Sound System (OSS) and Advanced Linux Sound Architecture (ALSA).  I wouldn't recommend writing directly to ALSA because the API is difficult and it only works on Linux and not FreeBSD or Solaris.  You should be okay with using OSS because even if the user is using ALSA, there is a compatibility layer in place.  But that still limits you to Unix-like operating systems.

Personally, I would use a cross platform library so that your program can work even on Windows and Mac.  There are lots of them available.  OpenAL, SDL, GStreamer, are all options.  I don't have much experience with any of them, so I couldn't tell you which I'd recommend.

---

### Post by x33a on 2009-06-23
take a look here:

[http://www.linux.com/archive/feature/124907](http://www.linux.com/archive/feature/124907)

i think you should go for ncurses.

---

### Post by cmay on 2009-06-23
> **x33a said:**
> take a look here:

[http://www.linux.com/archive/feature/124907](http://www.linux.com/archive/feature/124907)

i think you should go for ncurses.

next chapter in my book linux programming second edition is about ncurses. so i will look into this of course. 

thanks.

---

### Post by Mirge on 2009-06-24
Which book?

---

### Post by Thesuperchang on 2009-06-24
This may help you.

[http://www.oreilly.de/catalog/multilinux/excerpt/ch14-01.htm](http://www.oreilly.de/catalog/multilinux/excerpt/ch14-01.htm)

---

### Post by cmay on 2009-06-24
> **Mirge said:**
> Which book?
[http://www.wrox.com/WileyCDA/WroxTitle/productCd-0764544977,descCd-description.html](http://www.wrox.com/WileyCDA/WroxTitle/productCd-0764544977,descCd-description.html)
this one . and its the fourth edition i have. sorry. 
i took the edition number by mistake because i am reading the book advanced unix programming environment second edition by w richard stevens as well. which i can recommend  both of them. 

@Thesuperchang
thanks.

i studied the sources for the eject program in open solaris and  from the coreutils to figure out how a c program can interact with the dvd drive and thats the reason i want to try to create some thing that has to do wiht sound.  i know the usage of the headers used in the eject program is not enough or maybe even a good idea to use for making a small command line cd player. 

i just want to learn as much as possible but one thing is that having all those advanced options in the already existing commandline players is too confusing for me so i never actually used them. i want to have a commandline player that only can play random files from a given directory and quit when either told to or if someting goes wrong in the playback.  i use the rhytmh box audio player the same way when i listen to music its just all my music played in random order so i figure i would be happy for this little invention if i can make it work . 


thanks for the help every one.

---

### Post by monraaf on 2009-06-24
IMHO you should take a look at GStreamer. It's far easier to use GStreamer than interfacing yourself with all the different audio codec and soundsystem APIs.

---

