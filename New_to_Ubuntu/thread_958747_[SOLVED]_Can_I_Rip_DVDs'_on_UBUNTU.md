---
title: "[SOLVED] Can I Rip DVDs' on UBUNTU?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Teabicky on 2008-10-25
Please treat me as a complete idiot (without too much abuse).  I am very new to linux and ubuntu, having used windows for at least 17 years (i think).  

How can I rip dvds using Ubuntu? Is it just a case of installing a program via the GUI (a newly learnt term) or is  it a more complex procedure?

---

### Post by panhandle on 2008-10-25
Welcome to the Ubuntu community!

See this thread: 

[http://ubuntuforums.org/showthread.php?t=936203](http://ubuntuforums.org/showthread.php?t=936203)

Should get you going.

---

### Post by ad_267 on 2008-10-25
See this: [https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

There's plenty of options availabe. If you want to make a copy you can use k9copy to make an iso image of the dvd and then brasero or k3b to burn the image to disc.

---

### Post by Teabicky on 2008-10-25
Thanks, I'll try that.

---

### Post by lhb1142 on 2008-10-25
I am a relative Ubuntu "newbie" myself. I tried some of the Linux programs but I either could not understand the instructions thereto or otherwise had problems so here is what I did.

First I went to the Synaptics Package Manager and searched for Wine. When that program came up, I downloaded and installed it.

Next I "Googled" DVDShrink, found the installation file (which is for Windows), downloaded and installed it.

Then I "Googled" DVDFab HD Decrypter, downloaded and installed it.

Now when I want to copy and perhaps shrink a DVD, first I try DVDShrink alone. If that works (and it does much of the time), fine.

If not, I run DVDFab HD Decrypter which copies but does not shrink the DVD. Then I run DVDShrink and find the requisite VIDEO_TS file contained within the DVD Fab folder in the Home Folder and shrink it.

Then I just burn the resultant VIDEO_TS file.

It takes a bit of time but I find it relatively easy.

One word of caution: ONLY use DVD Fab HD Decrypter; the "pay" (even trial) version of DVD Fab does not work properly in Ubuntu. And do not try to change any of its configurations. You will only freeze your computer necessitating a restart.

I hope this helps you. :lolflag:

---

### Post by Duck2006 on 2008-10-25
> DVD Shrink

There is a linux ver of DVD shrink, so you don't need wine to install it.

---

### Post by Sweet Spot on 2008-10-31
> **Duck2006 said:**
> There is a linux ver of DVD shrink, so you don't need wine to install it.

Where might one find this Linux Version ? I can't find it anywhere. I've seen xDVD Shrink and aDVD Shrink, and the Vamps stuff, but not an official DVD Shrink made for Linux. I'd love to not have to install WINE just for that.. 

Doug

---

### Post by Duck2006 on 2008-10-31
When i ran DVD shrink i install it from automatix, Automatix is dead now, this may help you out with installing DVD shrink

[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=How+to+install+DVD+shrink&sa=Search](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=How+to+install+DVD+shrink&sa=Search)

[http://www.afterdawn.com/software/video_software/dvd_rippers/dvd_shrink.cfm](http://www.afterdawn.com/software/video_software/dvd_rippers/dvd_shrink.cfm)

---

### Post by Sweet Spot on 2008-10-31
That first link is the standard Windows version of it, which I already have installed via WINE (just did it, though it's not working properly, won't read the drive). 

I'm abou t99.999% sure that there is no official Linux version of DVD Shrink considering that development of the original stopped a few years ago.  Anything else would just be other devs building upon the original code, if anything. 

I just wish  could get this version working though.

---

### Post by m_duck on 2008-10-31
I like dvd::rip (sudo apt-get install dvdrip). However there are loads of options to change but there are some good tutorials on the web. Also, acidrip is worth a look.

---

### Post by Sweet Spot on 2008-10-31
> **m_duck said:**
> I like dvd::rip (sudo apt-get install dvdrip). However there are loads of options to change but there are some good tutorials on the web. Also, acidrip is worth a look.


Unless these programs have undergone some major changes, none of them have ever worked for me, only DVD Shrink. Occasionally I've had to run DVD FAB Decryptor in order to get the ISO to play nicely with DVD Shrink, but I can count the amount of times on one hand. All the others were far too complicated to try and set up, and yielded zero results. 

With DVD Shrink, all I ever have done is shrunk it, and then right clicked on it and selected write to disc. Has always been very handy.

---

### Post by LowSky on 2008-10-31
i use acid rip to rip all my DVD to Xvid

---

### Post by Sweet Spot on 2008-10-31
I'm not ripping DVD's for fun to play on the PC, it's to archive my collection. I have a lot of DVD's and don't want to pay for them again once they're scratched to hell (not like I don't take care of them, but you never know), so everything is backed up to ISO and then burned.  

I just downloaded K9Copy and so far, it's not working. When I hit open, it gives me an error message which says "Can't open disc" (which is listed as DVD-RW DVR-215D (/dev/scd0)  And when I go to devices, it says it can't detect anything, and then crashes when I close that window. Not such a keen program IMO, but I wasn't expecting much else. 

Doug

---

### Post by lhb1142 on 2008-10-31
:) Okay, let me explain a bit further: of the programs mentioned here, the best ones I have found are DVDFab HD Decrypter, the free version, which is the only version that will run under Wine (currently 5.1.0.0), DVD Shrink 3.2, installed and run under Wine, and, when necessary, k9copy 1.2.3, an "official" Linux program.

Now here is how I archive copy-guarded discs: First I run DVDFab HD Decrypter. This will produce AUDIO_TS and VIDEO_TS folders. Only the VIDEO_TS folder is necessary for further processing. This will NOT be compressed by DVDFab HD Decrypter but will be full-sized. If the VIDEO_TS folder is 4.472MB or less, fine. Just burn that. If it is larger, further processing is necessary (unless you want to use an expensive dual-layer blank disc). Make especial note: you MUST NOT attempt to modify, investigate, or manipulate DVDFab HD Decrypter IN ANY WAY or the program will freeze. Just copy, then okay the copied successfully message, click on Finish, and then close the program.

DVDFab HD Decryter will "break" the copy-guarding and will produce a DVDFab folder in your Home Folder. Within that, you will see a folder called Full Disc. Within THAT, you will find the title of the disc you copied and within THAT you will find the necessary VIDEO-TS folder. (A Temp and sometimes a Log folder are also produced in the main DVDFab folder; these can be ignored and/or deleted.) You'll also see an AUDIO_TS folder which will be empty. Ignore it. (Always ignore AUDIO_TS folders.)

In the event that the VIDEO_TS folder is larger than 4.472MB, I then generally use DVD Shrink on that resultant VIDEO_TS folder (using the Open Files section on DVD Shrink) to compress the folder. (DVD Shrink's default compression is to 4.464MB; personally I have set the Custom shrink option to 4.472MB but the difference is minor.)

MOST of the time, DVD Shrink will produce a VIDEO_TS folder which is 4.472 (or 4.464) MB in size; occasionally it will not and when you attempt to burn a disc, you will see a warning message apprising you of that fact. (When processing is finished, even prior to trying to burn, at the top you will also see the resultant size along with a red line at the end of the green line which shows the processed size; if you see this red line, you cannot burn a single-layer disc. The line at the top MUST be all green.)

Now there are two things you can do: one is to eliminate a soundtrack or an "extra" program. This will lessen the size of the folder.

But often that is not what you want to do. If that is the case, and you want the entire original disc copied as is, run k9copy on your original VIDEO_TS folder, the one that was originally produced by DVDFab HD Decrypter. Now you are going to have to mess around - k9copy thinks you want to process a disc. YOU have to "tell" it that you want to process a folder AND that you want the resultant items to be produced as another folder, not an ISO file. (After you set those parameters, just click on "copy" which you will find on an icon that says DVD. Run your cursor over the icons until you see the word Copy.)

After k9copy a has done its thing, THEN use DVD Shrink (again) to compress the VIDEO_TS folder that k9copy has produced - not the VIDEO_TS folder that was produced by DVDFab HD Decrypter. Generally, you will see DVD Shrink say that the folder it produces will be 97% - 100% of that k9copy-produced VIDEO_TS folder. (k9copy doesn't appear to always shrink the VIDEO_TS file completely.)

(When I make other VIDEO-TS folders, either with DVD Shrink alone, or with k9copy and DVD Shrink, I specify that the resultant produced folder should appear within DVDFab. This is not necessary - you can send that folder anywhere you want - just remember where you sent it! - but, by placing everything within that DVDFab folder, I find it easier to find just what I'm looking for!)

After all that, then you will have a VIDEO_TS folder of 4.472MB or less and you can burn that.

It sounds complicated - and I guess it is! I wish DVDFab (Fengtao) would produce a Linux-compatible "pay" (full) version. DVDFab is a great program; I formerly used it under Windows and it works really, really well. There are lots of customizable parameters within it which are quite self-explanatory. Sadly, though I have written to them several times, they have not produced such a program nor does DVDFab HD Decrypter run in any way under Linux (with Wine) other than its basic default method.

But, while all the above can take quite a bit of time, using one, two, or all three programs has NEVER failed to produce a good clean copy and this applies regardless of the "copy-guard" method used (ARccOS, RipGuard, whatever).

ALL of these programs I suggest are good and well-designed programs - believe me, they are! - and, if you TAKE THE TIME to look around them, and perhaps play with them a bit, you should really have no problems at all in figuring out what is necessary to do to use them correctly.

By the way, I am a Ubuntu Linux "newbie" myself, having only started using the program this past June (after 10 hours of frustration in attempting to use that @#$!% Windows Vista Home Premium on a new computer; previous to that I had only used earlier versions of Windows so that's all I knew). I am not a computer "geek," just an ordinary user with no special computer knowledge at all. And, I'm 65 years old! If I can figure all this out, ANYONE here ought to be able to do so too!  :popcorn:

---

### Post by coldcoffee on 2008-10-31
I have k9copy and have used it to rip and burn DVD's. I know it will rip DVD's preserving all the menu options, including easter eggs. It would rip to a file size of 4.3GB and burn to a blank DVD that would play on my home DVD player. I know I downloaded and installed libdvdcss2 and w32codecs packages before it did work. Now what other dependencies were already installed that it may have relied on I cannot tell you. I do know it is quite capable to rip and burn  high quality DVD backups.

After fooling around further with it I found I could rip DVD's to Xvid, DivX and some other video formats in real good quality in file sizes of around 650 to 700MB size with various sound formats such as ACC3 or AC3 or whatever that one is as well as LAME and quite a few others. I don't know off the top of my head, been a while since I have used it. I know it is a very capable ripping and burning tool all by itself when the right dependencies are met. I just wish someone who really knew would come out and say this is what you need for it to all work. I had it working splendidly, mostly luck and some researching. I was about a year ago when I set it all up.

I didn't need any other application period. It did it all for me. I just thought I would drop in and say this. I know this really isn't helping, other than the fact that yes, k9copy will do that if you can get all the dependencies met. I was pretty much lucky when I got it up and running.

As far as ripping the DVD's I remember selecting one audio source in the menu though. I would select all the video files. Shoot, I really don't remember all that, I know I could remember if I fired it up. Message me and I will get back with you on that. It is late, and the beers are kicking in.  I am sure you can find a tutorial if you do a Google search explaining that part. The kicker is going to be figuring out all the packages/dependencies you need to make it work.

k9copy will do just what you want though, if you can get everything else installed it needs to do it. I know, I have it working. In fact, I have a bootable 7.10 iso from a bootable cd I made somewhere with it working fantastically.

Good luck

---

### Post by Sweet Spot on 2008-11-04
Those last two posts are useful, but only as a last, last resort I think. I've never had to do anything else up to this point, except use DVD Shrink and then right click and burn. I'm not nearly as motivated to get those other things rolling, given that I never had to reach such heights of desperation. 

That said, upon starting up a new session, DVD shrink sees the DVD and is reading the name I believe, because when I go to "open dvd" it reads the name. But the error message I'm getting is :  "Failed to initialize ASPI device".  Then after a while, I get a message saying that the software installed (dvd) has the option to run upon installation etc..  I click no, and then another box pops up asking if I want to play the DVD with Movie Player...  I clicked on yes, but it didn't play it anyway. 

After this, I go back to re-open the movie in DVD Shrink, but now instead of it reading the name of the movie, it simply gives me a drive letter (F:) and fails to initialize the ASPI device again. 

Is this perhaps a WINE issue ? I'm about ready to try Ubuntu 8.04 again. 

D

---

### Post by Sweet Spot on 2008-11-04
Now I get a message saying "Can not read E:/ Bad device type"

Off to work.

---

### Post by deearar on 2008-11-04
The pay version of DVDFab (platinum) does indeed work under Wine, but it takes a good amount of configuration in order to do so. You basically need to download the wine source and recompile it, and then the pay version of DVDFab will work. There is a bug report at WineHQ regarding this issue.

---

### Post by Teabicky on 2008-11-08
I'm using acid rip with good results, I tried k9copy but found I could only seem to use it to make .iso files, which is useful anyway.

---

