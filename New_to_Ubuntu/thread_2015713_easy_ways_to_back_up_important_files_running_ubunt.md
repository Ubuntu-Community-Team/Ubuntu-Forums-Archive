---
title: "easy ways to back up important files running ubuntu 12.04"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by zirgut on 2012-07-03
I have reached a point with a graphics/sound issue where  I am being advised to reinstall ubuntu. As I have never done a re-installation before and have never bothered to backup files before I am wondering if there is an easy way of doing it. I was going to backup them up on a CD disc. Also with the re-installation do I have to delete the existing version first or does downloading the new copy make this unnecessary? Thanks for the help

---

### Post by llamabr on 2012-07-03
sticking it on a disk will be fine, unless it's too much data.  Otherwise, stick it somewhere else.

Yes, the installation will take care of your old version.

---

### Post by zirgut on 2012-07-04
Ok thanks but what I need to know is do I have to go to photos and save each folder separately and then the next and do the same with music and then with documents. This would take a long time. Also actually what is the saving process. What commands does one perform to transfer the files to the disc? I am sure this is exceedingly elementary stuff but that is where I am at. Thanks

---

### Post by llamabr on 2012-07-04
[http://lmgtfy.com/?q=ubuntu+howto+backup+home+directory](http://lmgtfy.com/?q=ubuntu+howto+backup+home+directory)

---

### Post by Zill on 2012-07-04
> **llamabr said:**
> [http://lmgtfy.com/?q=ubuntu+howto+backup+home+directory](http://lmgtfy.com/?q=ubuntu+howto+backup+home+directory)
:-)

---

### Post by zirgut on 2012-07-04
Thanks for the link. Looks good I will study it later. I had tried googling it before but got more confused by what I read.

---

### Post by lukeiamyourfather on 2012-07-04
It would help to know how much information you need to backup. A CD or DVD might work, or might not if you need to backup more information than they can store. An easier option might be a USB flash drive (again, depends on how much you need to backup).

---

### Post by Zill on 2012-07-04
> **zirgut said:**
> ...As I have never done a re-installation before and have never bothered to backup files before I am wondering if there is an easy way of doing it. I was going to backup them up on a CD disc...
I am slightly concerned that you have "never bothered to backup files before" as this seems to indicate that your data is unimportant to you.  Hard drives can, and do, fail and so you can lose your data at any time, not just when re-installing.  If your data is important to you then I suggest you should implement a regular backup routine to ensure that you can *always* restore your data if the worst comes to the worst.

Re backup tools, the problem is that there are so many different methods available, that work in different ways, that there is no "one size fits all" solution.  At its simplest level, you can simply burn copies of your folders or files directly to a CD or DVD.  However, there are other backup methods that allow data compression and incremental backups etc, which reduce the size of backup files.  Backup routines *can* be manual or scheduled and so, if configured correctly, can run automatically with no user intervention.

I suggest you read the info thrown up by the Google search listed above and and also the Ubuntu Documentation entitled [BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem"), as this will help you clarify exactly what you want to do and establish the best way to do it.

---

### Post by zirgut on 2012-07-04
Thanks one and all for your input. I do not have huge amounts of data. Perhaps most important are the collection of family photographs. Do not know how much off hand in terms of Mbs. Will check out the links. Thanks

---

### Post by Zill on 2012-07-05
> **zirgut said:**
> ...Perhaps most important are the collection of family photographs...
I would hate to lose *my* collection of photographs and so I regard backups as essential!

Having said that, photographs are generally jpegs which are already in a compressed format so there is no real benefit in further compressing them for backup purposes.

If you just want to backup photos then you could simply burn them directly to one or more CD/DVDs as suggested earlier.

Alternatively, if you want a "real" backup solution, you may like to take a look at [LuckyBackup]("http://www.techrepublic.com/blog/products/review-luckybackup-for-linux-systems/1379") - its in the repos.

---

### Post by afixane on 2012-07-05
You can use BackInTime, it's in Repository. Or, if you're familiar with command line stuff, use rsync.

---

### Post by zirgut on 2012-07-05
I am beginning to pullout the few remaining bits of hair I have and feel completely incompetent. Just about everything I read is so full of technical terms that my mind clouds over and even trying to do something like burn my photos onto a CD has got me frustrated and bewildered. Some things work really well for me on Ubuntu but other things seem confusing. Can anybody tell me how to get my photos onto a CD. I normally use shotwell but maybe that is irrelevant.

---

### Post by jmfal on 2012-07-05
Hi zirgut

I use K3B, open it, click on pictures folder on left ,, they will appear in box to right, double click on file and it will be loaded to current project below.

Right below will tell you how  much available space out of ...
click burn, load disc, tada.

---

### Post by Hadaka on 2012-07-05
Easy way to save your pictures ...

1.  insert a blank CD in the cdrom drive
2. at popup box choose..do Nothing
3. close that box
4. click on home folder...left ubuntu launcher bar
5. Home folder box will  show all your different folders and devices...on left panel
6. drag and drop the My Pictures folder to the cd disc symbol under devices...left panel
7. default cd burner box will show...choose write to disc..upper right of box
8. choose BURN....lower left of default cd burn box.

all your pictuers are now burned on to the cd

* replace CD symbol with USB symbol if you choose to save to a usb stick

---

### Post by zirgut on 2012-07-07
Thank you thank you for that concise and straightforward explanation. I finally got it to work.It took longer because I had buggered something up in the process of trying previously. But now everything is backed up and I have re-installed ubuntu and back to normal.
Thanks to everyone for their help and advice. I have to say being a novice and virtually illiterate in computer terminology it can be very difficult to follow advice cos I just don't understand stuff. 
I finally discovered the back up facility in 12.04, the Deja Dup thing in system settings. I mean I just don't go into system settings stuff unless there is some compelling reason. Nobody mentioned that which surprises me. Even then it is not so straight forward to use.  I mean exactly where to store stuff.
Just personally I find that if there was more explanation available on how to use the various programmes and features on Ubuntu it would help enormously.I am sure I am not the only one who struggles. I have spent many hours in this process of trying to sort out the sound and graphics problem and I see it as a learning experience but I am sure it would put off many people from using Ubuntu.
However thanks again to all the help I could not have done without all you folks out there.

---

