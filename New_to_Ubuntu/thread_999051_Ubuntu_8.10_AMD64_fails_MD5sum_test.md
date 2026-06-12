---
title: "Ubuntu 8.10 AMD64 fails MD5sum test"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by abrand888 on 2008-12-01
I have been using 8.04 32 bit until I bought a new computer and the cpu is a Q6600 cpu. Since the 6600 is a 64 bit processor, I wanted to try 8.10 64 bit version on my computer. I cannot get either the program win5mdsum or md5sum program to validate my download. The hash number cannot be compared. I have downloaded the 64-bit version on three different computer systems and the 64 bit version fails the hash test. I tried making cd-rw discs of three downloads on different computers and it fails to boot up.

Need help. Don't understand why I am getting failures.

The hash number either program returns is for the 386 version of 8.10. 

thanks

---

### Post by Het Irv on 2008-12-01
Can anyone else confirm this?

@abrand888:  When did this start happening?
Where are you downloading from?  
It sounds like you are getting a corrupted version when you download.

---

### Post by Elfy on 2008-12-01
I can't confirm - but did while you downloaded on 3 different systems did you use different sources for the downloads - or did you go to the same place?

I always download as torrents if possible - you shouldn't get a problem with corrupt downloads that way.

---

### Post by abrand888 on 2008-12-01
I download the same version 64 bit from different sites in my house. I even used utorrent in downloading the AMD version.I have TW Cable. I also downloaded the 64 bit version im my office straight and when I tried either versions of md5 either dos or win I got the same failure. I did take the version I downloaded and burnt a cd-rw but it just locks up after 30 seconds pass. The other weird thing is that md5 lists the hash numbers for thew 64 bit version and if you look sat the listing of the hash numbers what md5 reports foir the 64-bit version is really the hash numbers for the i386 8.10 version so they can't compare.

Hope this helps.

---

### Post by cmay on 2008-12-01
i can confirm this. i have had for the last 3 times i had to since 7.1.0 upgrade burn more than  5-6 cd to get one that was not corrupt- i only started to learn to remeber to check themd5 sumts after the first 7 cd i think. but it is happening a lot for me when i try download ubuntu from the home page. i found that going away from the dk mirror helped last time. i even have a tread on this. 

good luck with it .

---

### Post by ajgreeny on 2008-12-01
> The other weird thing is that md5 lists the hash numbers for thew 64 bit version and if you look sat the listing of the hash numbers what md5 reports foir the 64-bit version is really the hash numbers for the i386 8.10 version so they can't compare.You have lost me there, I'm afraid, but the md5sum for your amd64 desktop iso should be **f9cdb7e9ad85263dde17f8fc81a6305b** and for the i386 it should be [B]24ea1163ea6c9f5dae77de8c49ee7c03.
[/B]
These hashes are from[B] [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[/B]Where did you get your numbers from, because as you can see they are totally different.  Or have I totally misunderstood your question and statement.

---

### Post by Elfy on 2008-12-01
Just downloaded the amd iso from [http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/) and the resulting md5sum matches what is expected.

---

### Post by abrand888 on 2008-12-01
I did the md5sum on the iso version of the i386 8.10 of Ubuntu and what you wrote was the same for the 386 iso but when I did a coimpare it stated the sums were different. So I can't go further if the sums are different. I can try it again in my house or tommorrow AM. at my office.

Thanks.

I will compare the md5sms of the 64 bit again tonight.

---

### Post by hyper_ch on 2008-12-01
use bittorrent to download it... it will auto-check each chunk for a hash sum.

---

### Post by markbuntu on 2008-12-01
Try a cd-r instead of a cd-rw and burn at the lowest speed possible if you ever get a good download. I use the MIT mirror and have never had a problem.

---

### Post by abrand888 on 2008-12-01
Hi Forestpixie and hyper_ch,

I clicked on your link downloaded the iso file and the md5sums were different. I then installed Bittorrent and my download is very bad. In the logger screen it stated the following :


[2008-12-01 22:57:44]  *** ubuntu-8.10-alternate-amd64.iso: PIECE 297 FAILED HASH CHECK
[2008-12-01 22:58:13]  *** ubuntu-8.10-alternate-amd64.iso: PIECE 549 FAILED HASH CHECK
[2008-12-01 22:58:13]  *** ubuntu-8.10-alternate-amd64.iso: PIECE 490 FAILED HASH CHECK
[2008-12-01 22:58:43]  *** ubuntu-8.10-alternate-amd64.iso: PIECE 1304 FAILED HASH CHECK
[2008-12-01 23:00:45]  *** ubuntu-8.10-alternate-amd64.iso: PIECE 1375 FAILED HASH CHECK
[2008-12-01 23:01:09]  Banned 85.124.169.154:62541

As you can see the original Ubuntu iso is corrupted. I did more downloads that ever and all cannot pass md5sum test. I also downloaded last week the same file in utorrent and the file would not pass the hash test.

I look forward to your thoughts.  Thanks.

Abrand888

---

### Post by Douche223 on 2008-12-01
Free Apple MacBook!

[http://istuff.freepay.com/?r=46051897](http://istuff.freepay.com/?r=46051897)

[http://istuff.freepay.com/?r=46051897](http://istuff.freepay.com/?r=46051897)

[http://istuff.freepay.com/?r=46051897](http://istuff.freepay.com/?r=46051897)

[http://istuff.freepay.com/?r=46051897](http://istuff.freepay.com/?r=46051897)

[http://istuff.freepay.com/?r=46051897](http://istuff.freepay.com/?r=46051897)

[http://istuff.freepay.com/?r=46051897](http://istuff.freepay.com/?r=46051897)

---

### Post by abrand888 on 2008-12-02
Hi,

This morning before going to work I downloaded two copies of Ubuntu 64-bit operating system using bittorrent, one copy stated a hash problem, the other seemingly clean but when I ran winmd5sum, neither one was able to be compared, it stated sums are different.

---

### Post by hyper_ch on 2008-12-02
where did you get the .torrent files from?

You can get them all here from the tracker: [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by abrand888 on 2008-12-02
Hi,

On the original download page on the right I clicked on bitorrent and there were on the bottom of the next page all the iso files with the word torrent so I downloaded the amd64 iso using bitorrent twice and the sums didn't compare.
I will download tonight your link. I started again in my office but it choked our internet connection, so I stopped

---

### Post by hyper_ch on 2008-12-02
if you got the .torrent file from ubuntu.com then it should be the right one... no clue what you do but bittorrent does hash-check the chunks :(

---

### Post by Elfy on 2008-12-02
I would be wondering about my internet connection if I'd had that much trouble downloading iso's from different sources.

Whereabouts are you and what sort of connection do you have to the internet?

---

### Post by abrand888 on 2008-12-03
Hi,

I downloaded both versions Ubuntu 8.10, 32-bit and 64-bit. There were no hash errors at all with either version. I downloaded both versions using bitorrent. I then ran winMD5sum and it didn't even recognize the hash numbers for either version listed below. The only numbers it recognized were the ones listed below :

md5sum for your amd64 desktop iso should be f9cdb7e9ad85263dde17f8fc81a6305b
and for the i386 it should be 24ea1163ea6c9f5dae77de8c49ee7c03.. 

I decided to try and burn the downloaded images to cd-rw because they are safer to use and it starts booting and all I get for either version is a white screen. I did see the languages and the Ubuntu rectangle going across the screen and then all I got is a white screen no mouse at all.

I have Time Warner Cable and my download speeds are between 400 - 500 kbs which is fast. I have downloaded these iso so many times but the mdsums are different than what is published and none of the iso can compare the hash info at all. Am I doing something wrong ? I checked and the Intel Q6600 is 64 bit processor. Could my graphics card be the culprit ? 

My graphics card is a ATI Radeon 3650 with 1GB ram on the card.

I am using the 32-bit version of Ubuntu 8.04 and I don't have any problems 
running a livecd.

I am interested in being able to evaluate and use the 8.10 version but I am stuck for the 
moment.

This is the data of the torrent hash info 
===================================================================================

	INFO HASH					TORRENT NAME


82dc538278c54912f5b4f5da2bb9f17d577081d2	ubuntu-8.10-desktop-amd64.iso


33820db6dd5e5928d23bc811bbac2f4ae94cb882	ubuntu-8.10-desktop-i386.iso


BIT TORRENT DOWNLOAD INFORMATION


Thanks

abrand888

---

### Post by ctarwater on 2008-12-03
Wish I could help, but I just want to confirm the difficulty downloading Intrepid.

You can read about my previous issues in the thread I sorta hijacked [here]("http://ubuntuforums.org/showthread.php?t=997964&highlight=md5sum").

In short I had problems no matter the source, no matter the mirror, and even with torrents.

But I tried downloading from a different setup in the house and it finally worked.

---

### Post by abrand888 on 2008-12-03
My humble opinion is that the 8.10 version is corrupted worldwide
and it should be looked into immediately yu Ubuntu.org . At this time I wonder if I order a free cd of the operating system, will it even work. I think I will follow this route and see what happens. Since I got the 32-bit version of 8.04 working I will stay with it because if I am using the livecd version to go online, using a 32-64 bit version might be moot.

However if someone  comes up with a method to download a version that works, I will appreciate it vfery much.

abrand888

---

### Post by Elfy on 2008-12-03
Well I only tried once, to be true, and had no problem with an iso download from the release site. That said I always use torrents to download and have never had a problem with any of those either.

I would go with the free cd if you are having this much trouble with your downloads.

---

### Post by abrand888 on 2008-12-03
Hi forestpixie,

I downloaded five different iso downloads,,4 with bittorrent and utorent and all the downloads were bad.

---

### Post by Elfy on 2008-12-03
Yes I understand that - unfortunately, was really just saying that it's not a global phenomenon ;)

Perhaps, as I said, you will be better off with the preburnt and free cd from canonical. I certainly don't profess to undernstand the ins and outs of the internet and downloading files, but I would hazard a guess that the problem is, in some way, at your end.

Especially given that you have downloaded 5 different iso from, I assume, completely different sources.

---

### Post by Het Irv on 2008-12-03
I am gonna have to agree with forestpixie here. I think the problem has to do with something closer to home, but it could be that the image on one or two mirrors is corupt.  That would cause some people to have problems and some not to.  Or it may be dropped packets while downloading.

Either way the Pre-Burnt CD's should work perfectly, and if they don't it may be a problem generating the hash.

---

### Post by abrand888 on 2008-12-03
I downloaded many iso files not only at my house on different computers but I also downloaded iso files at work that is about 30 miles from my house. Perhaps there are some sites that have a problem with their iso files and I found them.

---

### Post by Elfy on 2008-12-03
Cool so that's narrowed it down a bit more then :)

Did you use this page to access any of the iso's or torrents?
[http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

---

### Post by abrand888 on 2008-12-03
yes. MDsuums didn't compare.

---

### Post by hyper_ch on 2008-12-04
when did you compare the md5 sum?

---

### Post by abrand888 on 2008-12-04
I ran the winMD5sums program after the download finished in windows and I also used the md5sum in dos in the directory where it is stored and it failed.

---

### Post by hyper_ch on 2008-12-04
just checking... after you burn the iso to a cd then then md5 the cd it would have a different md5sum :) you did it the right way. Still with torrent you should get a correct image.

---

### Post by abrand888 on 2008-12-05
Hello everyone,

I was able to make a cd-rw disc of the iso file 8.10 i386 and it worked on my system in my office, on a hp in my house but not on the Intel system.  I then checked the hash numbers of this iso and they didn't compare but it worked. I then tried it on my laptop with the same antenna system I use on my Intel and it worked both versions 8.04 and 8.10. Some how the 8.10 seemed brighter on my laptop screen.

I ordered a AMD 64 Ubuntu 8.10 as I give up trying to download the 64 bit version. There is something not right but I was unsuccessful so I ordered a cd and hope to see what happens. Incidentally the 8.10 version I burned a cdr would not boot up on my Intel but the 8.04 version boots up. I think it may be a dvd player problem and will investigate it over the weekend. I have four writers to test 8.10.

Thanks all for your help.

---

### Post by JasonSpradlin82 on 2008-12-28
Honestly, and I don't know why this would be, but it seems automatic that a torrent download has a different md5sum hash than the direct download. 

Ubuntu lists the md5sum hash for 8.10-desktop-i386 as:

```
24ea1163ea6c9f5dae77de8c49ee7c03
```

However, the tracker for ubuntu's torrent is:

```
33820db6dd5e5928d23bc811bbac2f4ae94cb882
```

Seems to me there is probably something extra with the torrent download that changes it... also the torrent download listed at 715,592 KB while the direct download was at 715,584 KB.  

It would be nice if somebody who knows would weigh in on this topic.

-----------------------

Ok it was posting here that made me realize that those two hashes are of different lengths, and a quick bit of research uncovered that the "tracker" hash I listed is an Info Hash -- 20-byte SHA1 hash, whereas the Ubuntu hash given on their site is an md5 hash.

-----------------------

Still doesn't account for the difference in file size between the two ISOs

---

### Post by abrand888 on 2008-12-29
Hi,

Today I just receive two Ubuntu 8.10 CD's from Canonical. I am at my office so I popped each cd and noted that one cd 8.10 didn't even recognize that I have a wired connection and when I clicked on network connection it stated I was disconnected. So I went to edit edit connections it stated AUTOetho it stated never and was greyed out and couldn't get rid of never in edit mode.

The second cd found my wired connection and I was able to go on line immediately. How can I determine if it is 32 bit or 64 bit ?

Why should one version recognize my wired connection and the other not ?

Also how can I run MDSums on either cd ?

I imagine that running a few tests will prove something since I received two definitive cd's

Thanks

---

### Post by xyberxyx on 2009-01-09
Hi,

I just tried downloading 64 bit 8.10 image and am getting checksum errors. When I found this post, I have to agree that it looks we have multiple mirror sites with corrupted files ( I have tried 3 different sites).  

Here is the checksum that is generated:
f9cdb7e9ad85263dde17f8fc81a6305b

If anyone has been successful with a 64 bit 8.10 download - can you indicate which site you used.

---

### Post by Elfy on 2009-01-09
f9cdb7e9ad85263dde17f8fc81a6305b you're generated md5sum
f9cdb7e9ad85263dde17f8fc81a6305b the md5sum from [http://www.mirrorservice.org/sites/releases.ubuntu.com/8.10/MD5SUMS](http://www.mirrorservice.org/sites/releases.ubuntu.com/8.10/MD5SUMS)

They match.

---

### Post by markbuntu on 2009-01-09
I got a good Intrepid 64bit download from the MIT mirror but that was weeks ago.

---

### Post by abrand888 on 2009-01-13
I just downloaded Ubuntu 8.10 64 bit, the mdsums seem to be the same as in previous thread but I cannot get winmd5sum to compare properly and I am getting the white screen of death. So far I have downloaded at least sixc times with no luck.

Something is very wrong.

---

