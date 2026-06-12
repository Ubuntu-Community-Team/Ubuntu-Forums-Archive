---
title: "suitable video editing programmes"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Benbow on 2008-09-30
I have tried Kino but it seems to be very buggy, crashes, stops working, will not start up etc so I have given up on this. I am about to try Cinelerra, does anyone have experience of this? Is it easy to use, does it have similar problems to Kino?
I am looking for a user friendly video package which will capture from the digicam, edit and have the facility to burn to dvd, similar to windows based systems. I am not particularly technical minded and I find it difficult to cope with programmes which need constant nursing and frequently fail midway through a session (very frustrating, especially when it wastes a couple of hours work).

---

### Post by AndrewTheArt on 2008-09-30
Cinelerra is notoriously difficult to learn how to use, but as far as I know it's pretty powerful.

I recommend kdenlive. It may not have all the features you want, but it's pretty easy to use, and reminds me of Windows Movie Maker.

---

### Post by Benbow on 2008-09-30
Hi
Kdenlive crashes -

benbow@benbow-desktop:~$ sudo kdenlive
[sudo] password for benbow: 
kbuildsycoca running...
Error: "/var/tmp/kdecache-benbow" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-benbow" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-benbow" is owned by uid 1000 instead of uid 0.
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
kdenlive: //  INIT EFFECT SEARCH
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
KCrash: Application 'kdenlive' crashing...
Unable to start Dr. Konqi
benbow@benbow-desktop:~$ sudo kdenlive
kbuildsycoca running...
Error: "/var/tmp/kdecache-benbow" is owned by uid 1000 instead of uid 0.
DCOP Cleaning up dead connections.
Error: "/var/tmp/kdecache-benbow" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-benbow" is owned by uid 1000 instead of uid 0.
kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
kdenlive: //  INIT EFFECT SEARCH
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive: 
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
KCrash: Application 'kdenlive' crashing...
benbow@benbow-desktop:~$

---

### Post by Gannon8 on 2008-09-30
Why do you need to run it as root? :confused:
Try removing "sudo" and run it again.

If that still does not work, try piviti

---

### Post by bobnutfield on 2008-09-30
> **AndrewTheArt said:**
> Cinelerra is notoriously difficult to learn how to use, but as far as I know it's pretty powerful.

I recommend kdenlive. It may not have all the features you want, but it's pretty easy to use, and reminds me of Windows Movie Maker.

This is correct information, Cinelerra is difficult to learn to use.  I have been using it for about a year and it does work and it is powerful.  It is not as polished as Adobe Premier Pro, and the features are more difficult to master, but it is almost as powerful.  Full length feature movies have been produced with Cinelerra.

---

