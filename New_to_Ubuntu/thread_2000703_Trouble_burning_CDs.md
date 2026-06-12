---
title: "Trouble burning CDs"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by Brianbea on 2012-06-10
I haven't been able to burn CDs. I went to "Disk Utility" and it said there was an "Error ejecting media". The last time I burned a CD (a little over 2 months ago) there must have been an "unknown error". I clicked on "Details" and it said "No medium in drive".
Can someone PLEASE help me get rid of the icon that says there's still a CD?

---

### Post by drpjkurian on 2012-06-10
I did not get your persistant error message. please be more specific

---

### Post by anewguy on 2012-06-10
I think I may understand - please correct me if I'm wrong.  You had a CD in the drive and you ejected it, yet the icon still shows saying the CD is there.  It probably also still shows in nautilus.

I've also had this problem - something happens with a disk I'm recording to so that it gets an error.  I manually eject the CD and bingo - I'm stuck.  Sometimes putting the CD back in the drive and using "eject" from the nautilus menu helps, but sometimes I'm not given that option.  In my case I was using Brasero.  I got so tired of supposed media errors that I went to using k3b instead.

If this isn't your problem, please say so as I'm not trying to hijack the thread - I just thought it sounded like problems I've also had.

Dave ;)

---

### Post by Brianbea on 2012-06-10
I'm still having a hard time. It said:
 
"An error occurred while performing an operation on "CD Drive" (CRW-5232AX): The Operation failed"
 
By the way I AM usuing Brasero (if that helps). I'm not very experienced with computers. I'm still having a hard time so if anyone could help any further it would be greatly appreciated.

---

### Post by mapes12 on 2012-06-10
Try **K3B**. You will find it in Software Centre. I have found it to be more robust than Brasero.

---

### Post by anewguy on 2012-06-10
Yes, please do - that's why I mentioned it in my previous post.

---

### Post by Hari5g900 on 2012-06-10
Well. I don't think so. I had a long time on k3b. And I think Brasero was better than k3b. And some way or the other, It was more faster than k3b (for me that is):p
But I also think that it may be because of your CD ROM Drive. I once had this problem (on redhat using k3b) and I had to change my drive!:roll:

---

### Post by oklokl on 2012-06-10
sudo apt-get install k3b

k3b Setting
Advaned > Miscellaneous > Do not eject ...
[ATTACH]219481[/ATTACH]
Nautilus
 Remove the cd room

---

### Post by Peripheral Visionary on 2012-06-10
I never had that sort of trouble with *Xfburn* (the Xfce alternative to Gnome's *Brasero*). K3B is excellent if you have plenty of room for all the libraries of stuff it "pulls in" when you go to install it. But on a low-resource computer like mine, Xfburn is a good alternative to try first.

---

### Post by The Cog on 2012-06-10
I also use xfburn these days. It's never been any trouble for me.
Just remember that if it says the drive is empty, press the refresh button just below the burn device to make it re-check the drive.

K3b has never been any trouble for me either, but it does pull in many, many libraries as you install it.

xfburn is minimalist, very few options, it just works.

K3b is maximalist, more options than you can understand, although the defaults are always good.

Brasero has always been unreliable for me, I don't know why.

---

### Post by jmore9 on 2012-06-10
Did you try right clicking on the cd icon in the file manager ( the left side in the pane ) and selecting eject.  Sometimes ubuntu 12.04 will still show the disk mounted when it is not even in the drive.  Doing that clears the spot i guess , it works just fine afterwords.

---

