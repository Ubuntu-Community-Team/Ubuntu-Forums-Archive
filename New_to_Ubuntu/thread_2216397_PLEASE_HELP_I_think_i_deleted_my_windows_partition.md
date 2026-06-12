---
title: "PLEASE HELP I think i deleted my windows partition and all my files!!!!!!!!"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by aaaaaaaa2 on 2014-04-11
I installed ubuntu and now i dont see my windows partition. here a pic of gparted please tell me my files are still there anyone

---

### Post by oldos2er on 2014-04-11
How many hard disks does the system have? Other system specs would be nice to know too.

If you just have the one hard disk, stop using it. You can boot Ubuntu from DVD or USB, and try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover partitions.

---

### Post by aaaaaaaa2 on 2014-04-11
thanks for your help
its one hard drive and Im running ubuntu from a dvd now because somehow i managed to messed up the ubuntu installation on my drive so it wont load now.

I have no idea how to use test disk  i downloaded it but have no idea what to do next. how to open it or anything...... im really new to this thanks

---

### Post by oldos2er on 2014-04-11
I'd start going through the docs here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I've never personally had need to do any partition recovery, so maybe someone who has will be along to help you.

---

### Post by 23dornot23d on 2014-04-11
Just to ask for some information to start with ........ what type of files were in your windows partitions 
and how much of it would be irreplaceable to you ........

Is it like personal photos and documents that are either needed for Work or Study ....... or is it like games
and things that can be re-installed from disks you have ............

Because if it is very important data to you - the best thing in this situation might be to take this to a data
recovery specialist ...... or someone that understands fully how to go about using testdisk when the
only drive has been formatted and over written with another OS ....... because theres a chance the data is ok

If Ubuntu just wrote over the first 4 gig or so ....... which might just be the windows OS ..........

But the data may sit untouched .......... just initial thoughts ......... but I have recovered things using testdisk
in the past ....... and even when you are experienced with it - it can give back some results that take a lot
of time and study .......... other times if there was not much that changed the program will see the start and
end points for where the original partitions were ........ but the process can be long as it scans through
the full disk to find information about where the old system was on the disk.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

There is a step by step here - and by no means do I want you to use it by yourself - but it may be worth having a look 
through first to see how well you understand any of it ........

Someone walking you through it can be easier .... and I do not have the confidence as it been a long time since I last
had to use this piece of software.

Hopefully some one else will confirm whether its a good option in this case to continue or to get the disk to someone
that is experienced in recovery of data ........ again it may depend on what data is on there.

Photorec is another piece of software that searches for photos and docs and is made by the same people.

The link is also here if you want to have a look through it ........

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)


Depends  on what if anything got overwritten - with the OS ....... hopefully the  data is well up the drive structure and maybe it can
be recovered .......... best I can say for now - but as I say waiting is a option here ...... the data is going no where as long
as you do not start writing or messing with the drive as it is ..........

Sometimes a image copy or clone - or even rermoval of the drive and use another drive while that one gets sorted out

There are options .......... just thought I better say something ....... but am trying just to ensure you - so that you know what might 
be other options .......

So  the first question is .... how important is the information on the disk  to you ....... and could most of it be put back on from
disks ....... ?

Just done some searching and looked again at your partition table as someone let me know it may be lvm2 and possibly encrypted
this after searching on ......

(lvm2 pv  problems restoring after over writing windows)

[https://www.google.co.uk/search?q=lvm2+pv++problems+restoring+after+over+writing+windows&btnG=Search&client=ubuntu&channel=fs&oe=utf-8&gl=uk&](https://www.google.co.uk/search?q=lvm2+pv++problems+restoring+after+over+writing+windows&btnG=Search&client=ubuntu&channel=fs&oe=utf-8&gl=uk&)

I am not seeing a lot of good reports from it ........ but its looking more and more like a data recovery specialist .......  if its possible to recover it in this situation

Is this a laptop with one 700 gig drive ...... ? ( possibly Lenovo ThinkPad E330 Business Laptop Core i3-3120M IvyBridge 8GB)




[http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

[https://www.google.co.uk/search?q=ubuntu+format+recovery&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](https://www.google.co.uk/search?q=ubuntu+format+recovery&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

