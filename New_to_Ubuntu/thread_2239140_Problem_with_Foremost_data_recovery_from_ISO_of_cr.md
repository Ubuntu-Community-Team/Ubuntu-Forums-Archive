---
title: "Problem with Foremost data recovery from ISO of crashed hard drive."
date: 2014-08-12
forum: New to Ubuntu
---

### Post by carlos59 on 2014-08-12
Dear all, I started using ubuntu about 2 months ago and wont go back, it is amazing. Right now I have a problem with FOREMOST a piece of software I am using to attept recovering data from a ISO created with gnuddrescue from a crashed hard drive. I managed to get some of the pdfs, don´t know why it failed to retrieve all of them, anyway I don´t want to be too specific on this thread as it might not be in the right forum, therefore, I am asking help to know where to get the right support to Foremost and please move my thread if it is in the wrong place.

thanks a lot

Carlos

---

### Post by coffeecat on 2014-08-12
As you are fairly new to Ubuntu, you are fine here. The other appropriate place would be [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331"). If you find you are not getting replies here and you want your thread moved, simply use the "Report Post" button in your own post to send a move request to the staff area. 

As soon as I have posted, I'll amend your thread title to make it clear that you are asking for help with data recovery using Foremost. If you want the title changed from what I've changed it to, just post back.

---

### Post by carlos59 on 2014-08-12
A little bit more information...

I am trying to recover some text files, however I don´t know how to teach FOREMOST, how to find the files I need, I´ve been trying different settings on /etc/foremost.conf
but so far no success.

The files I´ve been trying to save are text, I am attaching one of those, maybe someone can tell how to make foremost work.

so far foremost works but gets a lot of garbage as the files does not seem to have enough information on how foremost should start and stop.

bellow is my foremost command that I´ve been trying after changing foremost.conf

foremost -i /source.iso -o destination -T -vd

[ATTACH]255414[/ATTACH]

Thanks for reading

---

### Post by carlos59 on 2014-08-12
Still me providing information about the problem...
there is another option, which is to get some sort of copy of the files I need which are in xml format, but still no success retrieving them, between many attempts configuring foremost.conf this is the last I tried:

    xml    n    50000    <?xml version="1.0" encoding="UTF-8"?>     </classe>

foremost reads the ISO file and generates a lot of xml files but most of them are garbage as it does not pay attention to the header and footer I provided.

attached is a correct xml as the ones I am digging in to get. I had to rename it as pdf per some sort of size limit on the upload portion of this message.

[ATTACH]255416[/ATTACH]

thanks a lot for any help.

---

