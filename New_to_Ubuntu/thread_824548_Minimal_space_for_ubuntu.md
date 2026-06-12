---
title: "Minimal space for ubuntu"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by snake444 on 2008-06-10
How much is the minimal space that requred to ubuntu hardy for installation? 
i want to make new partition and install to there hardy..

---

### Post by SunnyRabbiera on 2008-06-10
at base the system should take no more then 8GB...
It at least it needs least 4 GB of disk space

---

### Post by snake444 on 2008-06-10
Ok thanks you and my next question :
is there a way to mix two drives?
I have C:\ that is 6GB (windows installed here)
and E:\ that is 31GB
is there a way to do it together so that it will be C:\ 37GB?

i want to do one drive c: and after that i will install the ubuntu on a new partition that ill create

---

### Post by SunnyRabbiera on 2008-06-10
I would not really advise that, and on a drive that small I honestly cant recommend a dual boot.
the extra E drive is probably for back up, I would not mess with it.
If I were you I would try and see if its possible to get a larger HD before attempting a dual boot... a 60GB hard drive would be very cheap this day and age and if you have a XP disk I would use it to format the new drive initally and then install ubuntu later.

---

### Post by brian_p on 2008-06-10
> **snake444 said:**
> Ok thanks you and my next question :
is there a way to mix two drives?
I have C:\ that is 6GB (windows installed here)
and E:\ that is 31GB
is there a way to do it together so that it will be C:\ 37GB?

i want to do one drive c: and after that i will install the ubuntu on a new partition that ill create

A basic Ubuntu install will take about 2.2 GB. / only uses about 200 MB.

A couple of partitions on the smaller sized drive (/ and /var). The other drive partitioned to take the remainder of the file system. That should do it.

Edit: Thinking on. Unless you are going to go mad and install many very large packages having /home on the larger disk and the rest on the other disk would work ok.

---

### Post by wPwLUi3N on 2008-06-10
Why not give it the entire hard disk, it is totally worth it.

If you keep a windows partition, you are just limiting your true potential.

Though 4 GB should be enough

Good luck

---

### Post by gaffurabi on 2008-06-10
i am running on 4,8 gb space (ext3 fs) and it has been quite a while without problems

---

### Post by bodhi.zazen on 2008-06-10
> **snake444 said:**
> Ok thanks you and my next question :
is there a way to mix two drives?
I have C:\ that is 6GB (windows installed here)
and E:\ that is 31GB
is there a way to do it together so that it will be C:\ 37GB?

i want to do one drive c: and after that i will install the Ubuntu on a new partition that ill create

First Linux uses different terminology for partitions. You should familiarize yourself with Linux terminology (so as to not accidentally install into the wrong partition).

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Second, C: = your master drive. Windows will *always* install things onto the master drive *even if you try re-installing onto E:*. So the "only way" to do this is to change which drive is master and which is slave.

Typically you do this either from the BIOS or manually (by changing the jumpers). If you do this, however, you will not be able to boot windows, you will have to re-install.

Ubuntu will install into any  partition \o/

The "minimal" space I have installed Ubuntu into has been just under 50 Mb (DSU == Damm Small Ubuntu). That is not realistic as it has no graphical interface. A standard installation of Ubuntu takes 3.5 - 4.5 Gb.

To be honest, easiest solution for you is, IMO, make a 5-8 Gb space (you need a swap partition also) on E: and install Ubuntu there. Swap size, for you , IMO, should be 512 Mb. Put 4.5-7.5 Gb into /

---

### Post by snake444 on 2008-06-10
Ok thanks i now will go to do partition 5gb and installl ubuntu
i have expirience with ubuntu since 7.04
He need the ubuntu to browse internet and watch movies
but all the data (movies, music) is will be stored on the windows ntfs partition.
but i just need it because i install to friend, not to me

---

### Post by snake444 on 2008-06-11
I installed and now there is internet problem
The computer connected to a swtich and to the switch connected the modem (B-Focus roter 270PR) and another computer (windows XP)
when i go to firefox and try to enter google it writes in the status bar Waiting for\Connecting to and the page doesnt loads. but in the seccond computer the internet works.
how do i setup the internet?


edit:
I found that the only page that it loads is firefox.com
and all the pages that it reffers to like to download or about

maybe the firewall blocks the access to other sites except firefox.com?
how can i remove the block??

---

### Post by snake444 on 2008-06-11
Here is the same problem as i have [http://ubuntuforums.org/showthread.php?t=705398](http://ubuntuforums.org/showthread.php?t=705398)
can someone help me??
and from live cd it is connects only to firefox.com too.

---

