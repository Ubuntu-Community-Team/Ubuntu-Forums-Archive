---
title: "Google+ / Google chat users, help"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-09-17
The updates for oneric uninstalled the package google-talkplugin about a week ago, if i try and reinstall it now i notice theres a dependency missing lib32v4l-0 what are my options, do i have to do without my google webcam chat while i wait for google to update the package or can i work around it?

---

### Post by cariboo on 2011-09-17
There is a thread on this problem already, try the solution [here]("http://ubuntuforums.org/showpost.php?p=11252716&postcount=4")

---

### Post by CaptainMark on 2011-09-18
thanks ill have a look

---

### Post by 10Digits on 2011-09-18
it'll want the lib32v4l-0 dependency- which is not in ia32-libs dependency anymore...however I have a dummy .deb of lib32v4l-0 here ...provided to me by sgo. you can install this first and then run the plug-in....this might help or you could try to find the dependency yourself.
In anyways good luck to you....I have attached the dummy package BTW!

---

