---
title: "Second drive dying. Do I have to reinstall Ubuntu?"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by dan14 on 2013-08-02
I installed Ubuntu to my 500G drive. I  made a 40G partition for it with  a 4G swap area. I formatted my second drive (160G) and put one partition  on it. After installing Ubuntu it appears that it is using both drives  for the operation system. The 160G drive is running very slow and the  disk utility program says it is overheating. If I try to copy a file to  it the machine slows to a crawl and takes 15 minutes to copy a 300meg  file to it.. 
  Is there a way to switch Ubuntu to only run on the  main drive and let me remove the second drive without reinstalling? I  have only been using Ubuntu for a few days but have everything set up the  way I want it and have 450G back on the main drive after restoring from  backups...
  It has been a rough week with this AND my car is dead in the garage. I am trying to fix them both ASAP and the Volvo is FULL of electrical gremlins.....:( A VERY good mechanic threw in the towel so I have to figure it out on my own. (But I will) ;)

Thanks for any help or advice...

Dan

---

### Post by Lars Noodén on 2013-08-02
Not really, the system stays on the drive it has been installed on.  Depending on how you have things set up, it might be easy to reinstall to the other drive yet still have your old data.  How you have your partitions set up will determine some of your options.  What is the output of [mount](http://manpages.ubuntu.com/manpages/raring/en/man8/mount.8.html)?

Also, before trying any experiments, be sure to make a working backup of your data.

---

### Post by cub on 2013-08-02
> **dan14 said:**
> I installed Ubuntu to my 500G drive. I  made a 40G partition for it with  a 4G swap area. I formatted my second drive (160G) and put one partition  on it. 

  It has been a rough week with this AND my car is dead in the garage. I am trying to fix them both ASAP and the Volvo is FULL of electrical gremlins.....:( A VERY good mechanic threw in the towel so I have to figure it out on my own. (But I will) ;)

Thanks for any help or advice...

Dan
What is the 160 GB partition for? Is it /home or anything else?

As for the Volvo, which model? ;) You could try the jagrullar.se forum.

---

