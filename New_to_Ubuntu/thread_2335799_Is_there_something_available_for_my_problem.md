---
title: "Is there something available for my problem ???"
date: 2016-09-01
forum: New to Ubuntu
---

### Post by walterwhite on 2016-09-01
hi guys , i download my files using 'zbigz', they are usually valid for 7 days (that means the download link is valid for lets just say 24 hours atleast ) so i can resume or pause the download any time (when i was a windows guy i used IDM to do that) , so i installed 'uget' but it's showing that 'zbigz' link is non-resumable too, 

So how can i get my IDM thingy back ?

hope you all understand coz my english sucks:(

---

### Post by TheFu on 2016-09-01
wget or curl?  Those are the main programs to download stuff on Linux. Both are highly script-able and you can schedule downloads to happen in the middle of the night using cron.  wget has been around for at least 20 yrs - it is amazing.  I know wget will let you limit the bandwidth used as well, to avoid sucking it all and impacting other network stuff.  Curl might be able to do that too - I don't know.  Would need to check the manpages for each command to learn that.''

Never heard of uget - sorry.

---

### Post by DogMatix on 2016-09-01
> **TheFu said:**
> 
Never heard of uget - sorry.

I bet you have? [uget]("http://ugetdm.com")

---

### Post by TheFu on 2016-09-01
> **DogMatix said:**
> I bet you have? [uget]("http://ugetdm.com")

Nope.  Not much of a GUI user here. Haven't used a DE much.  Us old guys have been doing things a certain way for 20+ yrs and haven't found a reason to change. ;)

I find that scripting works on servers better ... 1 file at a time, bandwidth controlled, stopped and restarted overnight, when the network isn't busy ... plus they don't have any GUI so wouldn't work.  Submitting batch tasks into queues for work as needed is something I've been doing a very long time.

Different use-cases from desktop-centric people. My desktop doesn't have storage for downloads. It is kept really lite - 13G used today.  That's what servers are for around here - storage.

---

### Post by DogMatix on 2016-09-01
Fair enough. I respect that.

---

