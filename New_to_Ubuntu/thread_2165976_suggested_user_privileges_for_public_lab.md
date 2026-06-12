---
title: "suggested user privileges for public lab"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by Kanefa on 2013-08-07
I've been setting up a public lab and have unfortunately will not be able to use the Guest account for this purpose.  I have set up a regular user and I was curious if there was any generic privileges I should let.  I'd like to keep the computers running and keep the things like inappropriate backgrounds to a minimum. 

Any suggestions would be appreciated, thanks.

---

### Post by lukeiamyourfather on 2013-08-07
Setup everything how you'd like it then make a copy of the home folder. Each time someone logs in copy the default home folder back. Only thing the users can screw up without root is stuff in the home folder which will get blown away at each login.

---

### Post by Kanefa on 2013-08-08
That's exactly what I want.

I'd imagine I would name the reusable home folder "default_student."  Is there a smart place to put this?  My lack of experience leads me to want to put it next to the rest of the users' home folders.  

Also, I think I would prefer to tack this on during log off, reboot, etc because we do have frequent power outages (the students work will be there till a manual log off).  That being said if that is not possible doing this would be fine at log in.  Is there a recommended place I could add my delete, mkdir, and cp?  

```
rm -rf /home/student
mkdir -p /home/student
cp -rf /home/default_student/* /home/student  
```

Thanks!

---

### Post by Kanefa on 2013-08-09
Today I looked into my second question, "where can I make these calls?"  It looks like "/etc/lightdm/lightdm.conf" has two variables called "session-setup-script" and "session-setup-script" where I can specify a script.  I haven't tried this yet.  My guess this will unearth more issues.

What I did try was putting together a bash script for the first time and found that the movie lessons I have in "/home/student/Videos" are to large.  I manually ran the script and after 17m it finished to to lack of space.  I need to figure out how to delete everything, but these large files.  I'll look into making their directories read-only, so the students can't muck them up).  Would that be the recommended method?

Also, from what I am reading is that the scripts called from "session-setup-script" and "session-cleanup-scripts" don't run from a specific user.  Optimally, I would like to only call this when the user student logs out.

---

### Post by lukeiamyourfather on 2013-08-12
Put the video files elsewhere and make their permissions read only. For example /material/videos instead of the home folder, or put them on a file server instead of the local machine. Not sure about where to put the script because I don't use lightdm, but it sounds like you're on the right track.

---

