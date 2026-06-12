---
title: "playable dvd creation issues"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by fractalman on 2012-10-10
I'm trying to create a dvd for a friend to play on his dvd player but i'm not having much luck, i have been googling for a few days and have tried all the guides i can find but i am not having much luck.

the original video is in an mp4 format, i have used transmegeddon to convert to mpeg and avi, neither of these will play if i stick them straight on a disc

i have tried using devede to create the film and then burnt it to disc as an iso but that just gave me disc error messages

i have tried using brasero to create a video project but when it starts converting to mpeg2 it freezes at 3 or 4 mib and just does nothing,  

are there any packages or codecs i might need that do not ship with ubuntu? i am using natty 11:04

i know the dvd writer works as i can put stuff on disc and watch it on my laptop


which programme is best for making a dvd that will work on all players?

thanks

---

### Post by androssofer on 2012-10-10
> **fractalman said:**
> I'm trying to create a dvd for a friend to play on his dvd player but i'm not having much luck, i have been googling for a few days and have tried all the guides i can find but i am not having much luck.

the original video is in an mp4 format, i have used transmegeddon to convert to mpeg and avi, neither of these will play if i stick them straight on a disc

i have tried using devede to create the film and then burnt it to disc as an iso but that just gave me disc error messages

i have tried using brasero to create a video project but when it starts converting to mpeg2 it freezes at 3 or 4 mib and just does nothing,  

are there any packages or codecs i might need that do not ship with ubuntu? i am using natty 11:04

i know the dvd writer works as i can put stuff on disc and watch it on my laptop


which programme is best for making a dvd that will work on all players?

thanks

try installing ubuntu restricted extras..

or convert the mp4 to mpeg2 yourself, then use brasero..

guide: [http://www.ehow.com/how_5957587_convert-mp4-mpeg_2-ubuntu.html](http://www.ehow.com/how_5957587_convert-mp4-mpeg_2-ubuntu.html)

---

### Post by sandyd on 2012-10-10
> **fractalman said:**
> I'm trying to create a dvd for a friend to play on his dvd player but i'm not having much luck, i have been googling for a few days and have tried all the guides i can find but i am not having much luck.

the original video is in an mp4 format, i have used transmegeddon to convert to mpeg and avi, neither of these will play if i stick them straight on a disc

i have tried using devede to create the film and then burnt it to disc as an iso but that just gave me disc error messages

i have tried using brasero to create a video project but when it starts converting to mpeg2 it freezes at 3 or 4 mib and just does nothing,  

are there any packages or codecs i might need that do not ship with ubuntu? i am using natty 11:04

i know the dvd writer works as i can put stuff on disc and watch it on my laptop


which programme is best for making a dvd that will work on all players?

thanks
I have found DeVeDe to be quite unfaliable.

---

### Post by fractalman on 2012-10-10
Sorry, i should have added i already have ubuntu-restricted extras

I tried winff as suggested and it converts to mpeg fine but when i try and use brasero to create a dvd brasero freezes at 131mb like it did with the other files i tried to convert

---

### Post by fractalman on 2012-10-10
I'm getting the same issue on my laptop too, when it starts converting the video to mpeg2 with brasero it freezes at 131mib

any ideas?

are there any other programmes i can use to burn a dvd that will work on a dvd player?

---

### Post by redkirk on 2013-03-11
> **sandyd said:**
> I have found DeVeDe to be quite unfaliable.

Installing DeVeDe removes the Medibuntu files:

libavformat52
libpostproc51
libswscale0

Last time I installed DeVeDe it broke my Medibuntu.  When I tried to repair it I ended up making a new installation of Ubuntu/Medibuntu.#-o](*,)

Is there a better answer to this question?

---

