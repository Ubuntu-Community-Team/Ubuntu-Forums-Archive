---
title: "Output size of DVD"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by klemperal on 2008-09-24
This might seem like a strange question, but are there settings within Ubuntu that determine the size of a DVD-5?  The reason I ask is because all of the avi to DVD programs on Linux give me a very small output size--usually about 2.5-2.7 gigs as appose to 4.3 something gigs.  Anyone else run into this or know how to fix the output size?

---

### Post by I Use Dial on 2008-09-24
You are trying to convert from an avi file to a DVD image file?

---

### Post by klemperal on 2008-09-25
Yes.  Both ManDVD and Devede have been giving me very small output sizes.  Nothing near 4.3 gigs.

---

### Post by I Use Dial on 2008-09-25
That's been my experience with Devede.  It just means you can fit more onto the DVD than you were planning.

---

### Post by Therion on 2008-09-25
Isn't .avi a compressed format?  
  
How big are the .avi files you're starting with, by the way?  Simply converting the .avi file isn't going to "balloon" back to full size.  Once the file is compressed, the data is lost.  You can't up-convert it.  Or am I misunderstanding your point?

---

### Post by I Use Dial on 2008-09-25
avi is a container format.  The final size of the DVD will depend on the original file size and quality.  You can also select the output settings of the DVD in devede.

---

### Post by klemperal on 2008-09-25
> **I Use Dial said:**
> You can also select the output settings of the DVD in devede.

Thats what I mean.  The output doesn't match up.  On Devede (or ManDVD for that matter) I set the output to be one thing, then it comes out much smaller.  I'll mess with it some more and see if i can't figure out the problem.  Thanks for the help, and let me know if you guys can think of anything else it could be.

---

### Post by I Use Dial on 2008-09-26
You mean the final DVD size stated in the Devede setup menu is not the same as the actual file size ends up being?  That is the same thing I get when I use the program.

---

### Post by klemperal on 2008-09-26
> **I Use Dial said:**
> You mean the final DVD size stated in the Devede setup menu is not the same as the actual file size ends up being?  That is the same thing I get when I use the program.

Exactly.  The same thing happens when I use ManDVD.  Thats why I'm asking if there is some sort of internal Linux/Ubuntu settings that determines what the size of a DVD-5 is...because it doesn't seem these programs correctly determine the size unless I'm missing something.

---

### Post by I Use Dial on 2008-09-26
> **klemperal said:**
> ...is some sort of internal Linux/Ubuntu settings that determines what the size of a DVD-5 is...

This answer to that is probably not going to be offered up in the 'Absolute Beginner Talk' forum.  (o;

---

### Post by klemperal on 2008-09-26
Too true

---

### Post by Drakkor on 2008-09-26
I'm using DVD Shrink with wine,and it auto manages for a DVD5, usually about 4.36 gigs a disk. :)

---

### Post by mc4man on 2008-09-26
> unless I'm missing something. 

> How big are the .avi files you're starting with, by the way? Simply converting the .avi file isn't going to "balloon" back to full size. Once the file is compressed, the data is lost. You can't up-convert it

That pretty much answers it. Maybe I can expound on that a little for you.

I've never used either of those apps so I don't know how they do the 'conversion'.  The output size is solely determined by the encoding or transcoding method and settings of such in your app. And even then there is a 'ceiling'. Any size above which has no positive effect. (probably even a slight *additional loss* of 'quality'

In the case of the 'direction' you're going the 'ceiling' is the *minimum amount of **further** loss in quality and 'video information' *

If your app is doing the job to maximum efficiency the output size is the best it will ever need to be.(and can be

Edit; 

To put it in the perspective of ripping a dvd9 and encoding or transcoding to dvd5 size. (the other 'direction'

In this case the encoder used (or encoding method) and it's settings  determine the amount of info ('quality') lost to *reach the target size.*

And pretty much the same for mpeg2 to another format. There you may set a target size which will determine the settings and amount of info lost ('quality' or 'apparent quality') or you may adjust the quality settings  which will determine the output size. 
In these cases the efficiency of the encoder/encoding format also is a factor in both size and 'quality'

---

### Post by klemperal on 2008-09-26
Thanks for the clear and expanded answer.  Makes sense with what you were saying about the output not getting over a certain size if it reaches the best quality at a smaller size (hope i understood that right).  It just had me confused since the program said the output would be one thing but i was getting something else.  Anyway, thanks again for the answer.  I'm gonna mess with it some more.

---

### Post by clinto on 2008-10-02
Oh good, I see I'm not the only one.

I throw avis into devede, it tells me it will fill a 4.3gb disk, then when it's done it's only about 1.8gb filled, 2.5gb wasted space.  That's annoying.  I've been trying to guess the amount, but if you go over then it ends up screwing up.  I can't afford coasters.

If I can't find a solution to this I'm going to try convertxtodvd in wine, though i'm sure it won't work for one reason or another, without working with it for hours on end anyways.  I don't remember having issues with this and devede in the past.

I burn avis to disk because I my bandwidth is slow and I don't like watching movies and shows on a crappy crt.

---

### Post by tonybeccar on 2008-12-07
> **klemperal said:**
> Thanks for the clear and expanded answer.  Makes sense with what you were saying about the output not getting over a certain size if it reaches the best quality at a smaller size (hope i understood that right).  It just had me confused since the program said the output would be one thing but i was getting something else.  Anyway, thanks again for the answer.  I'm gonna mess with it some more.

Man, you were right in what you were saying, the output size of the avi file must be 4 gigabytes. It's not that the avi cannot reach a bigger size because it reached its top quality. For example look at convertxtodvd, the output sizes are always 4.3 gigabytes. Obviously there is a problem with devede. Also the quality obtained with a 2.8 gigabytes movie is quite lower than a 4.3 gb one. 

So i guess we'll just have to wait untill devede fix this problem.. Good luck!

---

### Post by tonybeccar on 2008-12-08
Sorry about my last message, i converted the same movie with convertxtodvd and created me a 4.3 gb movie that had worse quality than the one which i converted with devede and weighted 2.8 gb. I was wrong, the movie reached it's top quality. 

You can mark this problem as solved, there's nothing wrong with devede. In other words, this 'problem' is great! You can save a lot of space.

Good bye..!

---

### Post by tonybeccar on 2008-12-08
Sorry about my last message, i converted the same movie with convertxtodvd and created me a 4.3 gb movie that had worse quality than the one which i converted with devede and weighted 2.8 gb. I was wrong, the movie reached it's top quality. 

You can mark this problem as solved, there's nothing wrong with devede. In other words, this 'problem' is great! You can save a lot of space.

Good bye..!

---

### Post by Smiley Coyote on 2009-03-30
> **tonybeccar said:**
> Man, you were right in what you were saying, the output size of the avi file must be 4 gigabytes. It's not that the avi cannot reach a bigger size because it reached its top quality. For example look at convertxtodvd, the output sizes are always 4.3 gigabytes. Obviously there is a problem with devede. Also the quality obtained with a 2.8 gigabytes movie is quite lower than a 4.3 gb one. 

So i guess we'll just have to wait untill devede fix this problem.. Good luck!

This is an older thread so I apologize for resurrecting things that require lots of reading to get a grip on.  I am desperate for a solution however.

This author goes on to state that he doesn't get any higher quality with larger ISO's.  

When I had Windows I used ConvertXtoDVD and I don't know if it created temporary TS folder or ISO's because they were always discarded upon completion of a project.  My question is simply, since I used to get much larger DVD files and markedly higher quality when I used this program, doesn't it stand to reason that there is a way to convert AVI in Ubuntu into either such folders or an ISO without such loss of quality?

I did this with ConvertXtoDVD countless times and always got much higher quality output than I am getting so far with DeVeDe and so far with DeVeDe I am getting much smaller files than I was as well.  I am having a hard time believing there is not some relationship regardless of how many experts tell me otherwise.

---

### Post by halitech on 2009-03-30
with the new version of Devede, there should be a button to the right that says Adjust Disk Usage. Click that and it will automatically adjust the Video and Audio Rates to get you as close to full dvd size as possible. It will still be under 4.3 gig (mine usually come in at about 3.7-3.8) but should be better then what you are getting currently.

---

### Post by Smiley Coyote on 2009-03-30
Well well well.  What a difference having a relatively up to date system makes.  I have purveyed other similar threads to this and nearly every one ends up with some version of an expert saying it works for them with the inquirer complaining that it doesn't.

With four times the processing power that I had when I last tried Ubuntu and also Wine, and with four times the memory and significantly better graphics processing, it seems that Wine will actually work with my computer whereas it wouldn't with the Pentium 2 I WAS using last year.  Yeah, you heard me right - Pentium 2.

I have little doubt that some systems will not be able to simulate a Windows environment but since mine now can, I can now run ConvertXtoDVD with it to create an ISO about three times the size of the one I got with DeVeDe, created at about four times the bitrate, and lo and behold, THE QUALITY IS FAR SUPERIOR.

---

### Post by Smiley Coyote on 2009-03-30
> **halitech said:**
> with the new version of Devede, there should be a button to the right that says Adjust Disk Usage. Click that and it will automatically adjust the Video and Audio Rates to get you as close to full dvd size as possible. It will still be under 4.3 gig (mine usually come in at about 3.7-3.8) but should be better then what you are getting currently.

Thanks.  I'll try this.

---

