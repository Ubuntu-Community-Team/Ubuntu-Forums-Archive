---
title: "Install 32-bit or 64-bit ubuntu 12.04"
date: 2012-05-31
forum: Recurring Discussions
---

### Post by zaigham_tt on 2012-05-31
Dear all,

i have Dell latitude D630 with 2GB Ram , 2.2 Ghz Core2Duo Processor and 120 GB hard drive.


My question is which Version of Ubuntu is best suited here 32-bit or 64-bit. and secondly what is the difference between them..

thanks,

---

### Post by carl4926 on 2012-05-31
Core2Duo are _64 but typically Ubuntu recommends 32 bit and since your machine isn't exactly a showstopper performance wise, using 32 bit isn't really a disadvantage. Unless you encode lots of video, you'll not notice any difference.
32 bit version may offer more compatibility with some software.

---

### Post by oldfred on 2012-05-31
Moved to recurring discussions.

I did install 64 bit on my 6 year old laptop with 1.5GB RAM and it works. If I try to load two large apps it goes to swap and turns grey for a few seconds. I think 32 bit would be better, but I wanted it to be the same as my Desktop which has 4GB.

---

### Post by Paqman on 2012-06-01
> **carl4926 said:**
> Core2Duo are _64 but typically Ubuntu recommends 32 bit and since your machine isn't exactly a showstopper performance wise


It's about the same as my desktop, just with less RAM. My machine rocks along on Ubuntu. The speed of your hard drive and your graphics card will affect performance more than that CPU or amount of RAM anyway.

> 
using 32 bit isn't really a disadvantage.

Sure, it'll work. It'll just be slower.

> 
Unless you encode lots of video, you'll not notice any difference.

Encoding video, compressing and extracting archives, encryption, opening some apps, etc, etc. Lots of common desktop tasks benefit from faster number crunching.

> 
32 bit version may offer more compatibility with some software.

Not in my several years of experience with 64-bit.

There is no advantage to using a 32-bit OS. Always use 64-bit on a 64-bit machine.

---

### Post by NadirPoint on 2012-06-01
64-bit only comes into play with over 3 gig of ram.  Use the 32-bit.

---

### Post by oldos2er on 2012-06-01
> **NadirPoint said:**
> 64-bit only comes into play with over 3 gig of ram.  Use the 32-bit.

Not true, 64-bit Ubuntu works wonderfully well on 2GB RAM; video-encoding and other CPU intensive tasks run measurably faster than they do on 32-bit.

If you have 64-bit capable hardware, use 64-bit software.

---

### Post by NadirPoint on 2012-06-01
> **oldos2er said:**
> video-encoding and other CPU intensive tasks run measurably faster than they do on 32-bit.
No, I think you are wrong, so unless you would care to post a link to some benchmark test results we'll just have to agree to disagree.

---

### Post by carl4926 on 2012-06-01
> **oldos2er said:**
> Not true, 64-bit Ubuntu works wonderfully well on 2GB RAM; video-encoding and other CPU intensive tasks run measurably faster than they do on 32-bit.

If you have 64-bit capable hardware, use 64-bit software.

Of course this is correct

---

### Post by thatguruguy on 2012-06-01
> **NadirPoint said:**
> No, I think you are wrong, so unless you would care to post a link to some benchmark test results we'll just have to agree to disagree.

Actually, you're wrong, and this has been covered repeatedly. Here's one [set of benchmarks]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1").

As a rule, it's better practice to post "I think you're wrong, and here's why (with reference to something bolstering your position)" than it is to say "I think you're wrong, now prove that you're right."  Don't make everyone else do your work for you. You can use google just as well as anyone else.

---

### Post by Paqman on 2012-06-01
> **NadirPoint said:**
> 64-bit only comes into play with over 3 gig of ram.  Use the 32-bit.

Common misconception. 64-bit does allow you to address more RAM, but it is also able to carry out calculations involving large numbers much quicker. That means that any computationally intensive task will run significantly faster on a 64-bit machine, regardless of how much RAM it has.

The Phoronix benchmarks posted above are pretty conclusive. [These ones]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1") are also interesting (if a little old), in that they show that even using PAE on a 4GB system doesn't do anything significant to bridge the gap. This shows how many tasks are dominated more by raw CPU power than by the amount of memory available.

When people say: "always use a 64-bit OS on 64-bit hardware" they say it for a reason.

---

### Post by oldos2er on 2012-06-01
> **NadirPoint said:**
> No, I think you are wrong, so unless you would care to post a link 

Again? This forum (Recurring Discussions) is full of them. Perhaps you could post a link validating your claim?

---

### Post by TheGuyWithTheFace on 2012-06-01
It seems to me this is a theme for a lot of computer science. The old way, 32 bit, is more stable. The new way, 64 bit, is controversial. I believe, however, that 64 bit is the future. As programs and operating systems *coughWINDOWScough* become more and more power hungry, more and more memory is needed. 32 bit works fine... for now. 64 bit, while it may have had a bumpy start, is steadily improving. Give it a few years, I'll bet all new computers will be 64 bit! (If they arn't already, It's been a while since I bought a new computer)

---

### Post by oldos2er on 2012-06-01
In my opinion it's stable now (I'm referring to Linux, I know nothing of Windows), and "controversial"? Don't see anything like that.

---

### Post by TheGuyWithTheFace on 2012-06-01
Ah, I was actually talking about windows. A couple months ago, when I was debating on whether or not to try linux, I saw several benchmarks indicating that in windows, at least, 32 bit was more stable. Of course, since windows tends to stay largely the same for years at a time, so I wouldn't be surprised anymore if it's a bit behind!

---

### Post by NadirPoint on 2012-06-02
Any potential performance increase seen under 64-bit is going to be a predominantly application specific phenomenon.  A good analysis of the specific scenario would call for soliciting the user's requirements.

[https://docs.google.com/viewer?url=http%3A%2F%2Fpapers.scotttrent.net%2F64bitSoftwarePerformanceMisconceptions.pdf](https://docs.google.com/viewer?url=http%3A%2F%2Fpapers.scotttrent.net%2F64bitSoftwarePerformanceMisconceptions.pdf)

Use the right tool for the job.

---

### Post by philinux on 2012-06-02
OP read the benchmarks above and this one and make your own mind up.

Me I run 64 bit on 2 machines both with 2 gig ram. One a desktop other acer 1410.

 [http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by thatguruguy on 2012-06-02
> **NadirPoint said:**
> Any potential performance increase seen under 64-bit is going to be a predominantly application specific phenomenon.  A good analysis of the specific scenario would call for soliciting the user's requirements.

[https://docs.google.com/viewer?url=http%3A%2F%2Fpapers.scotttrent.net%2F64bitSoftwarePerformanceMisconceptions.pdf](https://docs.google.com/viewer?url=http%3A%2F%2Fpapers.scotttrent.net%2F64bitSoftwarePerformanceMisconceptions.pdf)

Use the right tool for the job.

It's neat that you've cited a paper written 9(!) years ago.  Unfortunately, the paper you cited doesn't really bolster your earlier claim:
> **NadirPoint said:**
> 64-bit only comes into play with over 3 gig of ram.  Use the 32-bit.

If you had bothered to actually read the paper you cited, you'd note that on page 5 of the paper the author classifies the claim that "There is no benefit to running 64-bit
programs on small memory systems" as a myth.

Moreover, you also made the following statement in response to the claim that video-encoding and other processor-intensive tasks ran faster in a 64-bit OS than 32-bit:
> **NadirPoint said:**
> No, I think you are wrong, so unless you  would care to post a link to some benchmark test results we'll just have  to agree to disagree.
You've been provided benchmarks, but haven't responded to them. Instead, you provided a link to the 9-year-old technical paper which, as noted, doesn't really support your position.

At this point, wouldn't it just be easier for you to admit that you're wrong and thank the other participants in this thread for the education?

---

### Post by weasel fierce on 2012-06-02
I've used 64 bit for a few years now, and I have a hard time thinking of the last time I ran into an issue.

Besides, doesn't Ubuntu have some sort of compatibility trick nowadays anyway?

---

### Post by NadirPoint on 2012-06-02
> **thatguruguy said:**
> At this point, wouldn't it just be easier for you to admit that you're wrong and thank the other participants in this thread for the education?
No, because good advice in systems issues like this is preceded with an evaluation of the specific application(s), requirements and objectives, non of which a pompous "I'm right, you are wrong"  windbag would be interested in.

It's rarely an easy either-or black-or-white answer.

---

### Post by oldfred on 2012-06-02
OP can decide. 

Thread is degenerating.

---

