---
title: "gstreamer &amp; webcam"
date: 2010-04-02
forum: Programming Talk
---

### Post by hamid_m on 2010-04-02
hi , I want save video and sound from webcam and save them in avi format , I use this command but not work , how can fix it 
```

gst-launch v4l2src device=/dev/video0 ! queue ! videorate ! xvidenc !queue !alsasrc device=hw:0,0  ! audioconvert  ! queue ! avimux  ! filesink location=test.avi

```

---

### Post by hamid_m on 2010-04-03
anyone plz help me in this case ](*,)

---

### Post by SledgeHammer_999 on 2010-04-03
This isn't a programming issue. Please ask it here-->[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

