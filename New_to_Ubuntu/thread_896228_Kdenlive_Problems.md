---
title: "Kdenlive Problems"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Jengajam2 on 2008-08-21
1.Whenever I import a wmv video, the screen goes blank, it shows no video until i save it, and restart it.
2.It crashes alot when I try to open a saved project:
Bactrace:```
#0  0xb7f65410 in __kernel_vsyscall ()
#1  0xb760b99b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb683c1d3 in ?? () from /usr/lib/libxcb.so.1
#3  0xb683c83b in xcb_poll_for_event () from /usr/lib/libxcb.so.1
#4  0xb7668cc9 in ?? () from /usr/lib/libX11.so.6
#5  0xb7668e6f in ?? () from /usr/lib/libX11.so.6
#6  0xb766971f in _XEventsQueued () from /usr/lib/libX11.so.6
#7  0xb763d45e in XCheckTypedWindowEvent () from /usr/lib/libX11.so.6
#8  0xb797f8cc in QETWidget::translateConfigEvent ()
   from /usr/lib/libqt-mt.so.3
#9  0xb798d1f7 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#10 0xb79a4943 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#11 0xb7a1af02 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#12 0xb7a0184a in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#13 0xb7a01875 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#14 0x08183f35 in KdenliveDoc::updateTracksThumbnails ()
#15 0x08211522 in KdenliveDoc::qt_invoke ()
#16 0xb7a6b704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb7dfaaba in QSignal::signal () from /usr/lib/libqt-mt.so.3
#18 0xb7a8a7b2 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#19 0xb7a92936 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#20 0xb79ffc36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb7a01a5f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb6f72672 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb799028d in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#24 0xb79f2b19 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#25 0xb79a564b in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#26 0xb7a1af90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#27 0xb7a1ac8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#28 0xb7a017df in QApplication::exec () from /usr/lib/libqt-mt.so.3
#29 0x081c5a9e in main ()
``` Terminal:```
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
kdenlive: WARNING: KdenliveDoc::loadFromXML() document element has unknown tagName : kdenlivedoc
kdenlive: // DOCUMENT: /home/jengajam2/.kde/share/apps/kdenlive/recovery.kdenlive, version: 0.6
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: quarter_ntsc
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: quarter_ntsc
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
Error: "/var/tmp/kdecache-jengajam2" is owned by uid 1000 instead of uid 0.
kdenlive: KdenliveDoc in closeDocument()
kdenlive: deleting contents...
kdenlive: //  CLIP PRJECT LENGTH IS: 0
kdenlive:  + + +  Loading Time : 169ms
Error: "/tmp/ksocket-jengajam2" is owned by uid 1000 instead of uid 0.
kdenlive: +++++++++++  Generating scenelist start...  ++++++++++++++++++
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive: WARNING:  ++++ WARNING, UNABLE TO CREATE MLT PRODUCER
kdenlive: //////  LENGTH: 1
kdenlive: //  SCREEN length update: 1
kdenlive: WARNING: KdenliveDoc::loadFromXML() document element has unknown tagName : kdenlivedoc
kdenlive: // DOCUMENT: /home/jengajam2/Desktop/clint.kdenlive, version: 0.6
kdenlive:  + + RESET CONSUMER WITH PROFILE: hdv_1080_50i
kdenlive:  + + RESET CONSUMER WITH PROFILE: hdv_1080_50i
kdenlive: //  SCREEN length update: 0
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE 
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: hdv_1080_50i
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
kdenlive:  + + CREATING CONSUMER WITH PROFILE: hdv_1080_50i
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
kdenlive: KdenliveDoc in closeDocument()
kdenlive: deleting contents...
kdenlive: *** DOCUMENT adding clip: 3 Squares and an Ed.wmv
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive: //////  LENGTH: 16400
kdenlive: //  SCREEN length update: 16400
kdenlive: *** DOCUMENT adding clip: Gorillaz - Clint Eastwood.MP3
kdenlive: *** DOCUMENT adding clip: 3 Squares and an Ed.wmv
kdenlive: *** DOCUMENT adding clip: a_case_of_ed.wmv
kdenlive: *** DOCUMENT adding clip: An Ed in the Bush.wmv
kdenlive: *** DOCUMENT adding clip: an_ed_is_born.wmv
kdenlive: *** DOCUMENT adding clip: Boys Will Be Eds.wmv
kdenlive: *** DOCUMENT adding clip: Cleanliness is next to Edness.wmv
kdenlive: *** DOCUMENT adding clip: dear_ed.wmv
kdenlive: *** DOCUMENT adding clip: dim_lit_ed.wmv
kdenlive: *** DOCUMENT adding clip: dont_rain_on_my_ed.wmv
kdenlive: *** DOCUMENT adding clip: dueling_ed.wmv
kdenlive: *** DOCUMENT adding clip: EdEddandAway.wmv
kdenlive: *** DOCUMENT adding clip: Ed Edd n Eddy's Jingle Jingle Jangle.wmv
kdenlive: *** DOCUMENT adding clip: eeny_meeny_miney_ed.wmv
kdenlive: *** DOCUMENT adding clip: Every Which Way but Ed.wmv
kdenlive: *** DOCUMENT adding clip: floss_your_ed.wmv
kdenlive: *** DOCUMENT adding clip: for_the_ed_by_the_ed.wmv
kdenlive: *** DOCUMENT adding clip: gimme_gimme_never_ed.wmv
kdenlive: *** DOCUMENT adding clip: hand_me_down_ed.wmv
kdenlive: *** DOCUMENT adding clip: hands_across_ed.wmv
kdenlive: *** DOCUMENT adding clip: hot_buttered_ed.wmv
kdenlive: *** DOCUMENT adding clip: It Came From Outer Ed.wmv
kdenlive: *** DOCUMENT adding clip: know_it_all_ed.wmv
kdenlive: *** DOCUMENT adding clip: little_ed_blue.wmv
kdenlive: *** DOCUMENT adding clip: Look Before You Ed.wmv
kdenlive: *** DOCUMENT adding clip: Mission Ed-Possible.wmv
kdenlive: *** DOCUMENT adding clip: mommas_little_ed.wmv
kdenlive: *** DOCUMENT adding clip: my_fair_ed.wmv
kdenlive: *** DOCUMENT adding clip: No Speak da Ed.wmv
kdenlive: *** DOCUMENT adding clip: One Plus One Equals Ed.wmv
kdenlive: *** DOCUMENT adding clip: Out with the Old, In with the Ed.wmv
kdenlive: *** DOCUMENT adding clip: pain_in_the_ed.wmv
kdenlive: *** DOCUMENT adding clip: postcards_from_the_ed.wmv
kdenlive: *** DOCUMENT adding clip: ReadySetEd.wmv
kdenlive: *** DOCUMENT adding clip: rent_an_ed.wmv
kdenlive: *** DOCUMENT adding clip: Rock-a-byeed.wmv
kdenlive: *** DOCUMENT adding clip: sorry_wrong_ed.wmv
kdenlive: *** DOCUMENT adding clip: the_day_the_ed_stood_still.wmv
kdenlive: *** DOCUMENT adding clip: The Good, the Bad and the Ed.wmv
kdenlive: *** DOCUMENT adding clip: they_call_him_mr_ed.wmv
kdenlive: *** DOCUMENT adding clip: thick_as_an_ed.wmv
kdenlive: *** DOCUMENT adding clip: This Won't Hurt an Ed.wmv
kdenlive: *** DOCUMENT adding clip: Tinker Ed.wmv
kdenlive: *** DOCUMENT adding clip: Too Smart for his own Ed.wmv
kdenlive: *** DOCUMENT adding clip: urban_ed.wmv
kdenlive: *** DOCUMENT adding clip: video.mp4
kdenlive: *** DOCUMENT adding clip: WillWorkForEd.wmv
kdenlive: //  CLIP PRJECT LENGTH IS: 11623
kdenlive:  + + +  Loading Time : 1418ms
kdenlive: **********  FREED MEM FOR: 3 Squares and an Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Gorillaz - Clint Eastwood.MP3, COUNT: 0
kdenlive: **********  FREED MEM FOR: 3 Squares and an Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: a_case_of_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: An Ed in the Bush.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: an_ed_is_born.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Boys Will Be Eds.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Cleanliness is next to Edness.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dear_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dim_lit_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dont_rain_on_my_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dueling_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: EdEddandAway.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Ed Edd n Eddy's Jingle Jingle Jangle.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: eeny_meeny_miney_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Every Which Way but Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: floss_your_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: for_the_ed_by_the_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: gimme_gimme_never_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: hand_me_down_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: hands_across_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: hot_buttered_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: It Came From Outer Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: know_it_all_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: little_ed_blue.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Look Before You Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Mission Ed-Possible.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: mommas_little_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: my_fair_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: No Speak da Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: One Plus One Equals Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Out with the Old, In with the Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: pain_in_the_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: postcards_from_the_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: rent_an_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: sorry_wrong_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: the_day_the_ed_stood_still.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: The Good, the Bad and the Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: they_call_him_mr_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: thick_as_an_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: This Won't Hurt an Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Tinker Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Too Smart for his own Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: urban_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: WillWorkForEd.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: 3 Squares and an Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Gorillaz - Clint Eastwood.MP3, COUNT: 0
kdenlive: **********  FREED MEM FOR: 3 Squares and an Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: a_case_of_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: An Ed in the Bush.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: an_ed_is_born.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Boys Will Be Eds.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Cleanliness is next to Edness.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dear_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dim_lit_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dont_rain_on_my_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: dueling_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: EdEddandAway.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Ed Edd n Eddy's Jingle Jingle Jangle.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: eeny_meeny_miney_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Every Which Way but Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: floss_your_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: for_the_ed_by_the_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: gimme_gimme_never_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: hand_me_down_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: hands_across_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: hot_buttered_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: It Came From Outer Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: know_it_all_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: little_ed_blue.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Look Before You Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Mission Ed-Possible.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: mommas_little_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: my_fair_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: No Speak da Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: One Plus One Equals Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Out with the Old, In with the Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: pain_in_the_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: postcards_from_the_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: rent_an_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: sorry_wrong_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: the_day_the_ed_stood_still.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: The Good, the Bad and the Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: they_call_him_mr_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: thick_as_an_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: This Won't Hurt an Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Tinker Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: Too Smart for his own Ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: urban_ed.wmv, COUNT: 0
kdenlive: **********  FREED MEM FOR: WillWorkForEd.wmv, COUNT: 0
KCrash: Application 'kdenlive' crashing...
Unable to start Dr. Konqi

```
Any help will be greatly appreciated!

---

### Post by marcelmasi on 2008-12-19
I probably have the same issue. I can work with kdenlive without any problems. Storing and loading works in the beginning. However, as soon as the project gets larger, loading the project will crash kdenlive. I tried with kdenlive 0.5 and 0.6, it doesn't matter. The project shows up a very very short instant, but then it crashes.
I thought it could be something with the thumbnails, since once when I removed them by hand in the project file, it could load it. However .. that worked only once and the crash thing isn't deterministic.
The console output is the same as yours. The backtrace only shows this:

[SIZE="1"][FONT="Courier New"]This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents
creation of proper backtraces, or the stack frame was seriously corrupted
in the crash.

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb66a56c0 (LWP 12557)]
[New Thread 0xb2dfeb90 (LWP 12586)]
[New Thread 0xb35ffb90 (LWP 12585)]
[New Thread 0xb4fccb90 (LWP 12584)]
[New Thread 0xb47cbb90 (LWP 12583)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb5e6193a in ?? () from /usr/lib/libavformat.so.1d
#0  0xb5e6193a in ?? () from /usr/lib/libavformat.so.1d
#1  0x00000000 in ?? ()[/FONT][/SIZE]

any ideas?

---

### Post by marcelmasi on 2008-12-19
I just tested with kdenlive 0.7 on Gentoo. Same issue there: when you have 2 video tracks with avi's and some image-clips and an mp3 on an audio track everything works fine. Save, exit the program, restart kdenlive and open the project again results in a crash.

btw: why do they write absolut paths an not relative paths into the project files?!

---

