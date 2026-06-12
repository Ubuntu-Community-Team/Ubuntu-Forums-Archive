---
title: "Using tape drives with Ubuntu? Advice please."
date: 2018-12-02
forum: New to Ubuntu
---

### Post by wheresthechocolate on 2018-12-02
Hi,

I have a lot of video and audio files to back up. They are stored on Windows NT formatted drives as most of the software I use is Windows based and my editing rig is Windows 7 based.

Up until now I have been backing these files up on external hard drives, but this is now just getting daft (and expensive).

I have therefore been investigating tape drives, particularly SAS based TFO drives. Second-hand refurbished drives can be bought for around £300-£500 (gbp).

However the driver and backup situation for tape drives on a consumer, non-server, versions of Windows appears poor to non existent and even on a server system looks like its not great. Also I don't want to have to splash out on a server just to back up my files!

My rig also boots into Ubuntu, its on an old version so I would need to update or reinstall, however I am wondering if it is possible to use Linux to perform a sensible tape based backup.

I would need to be able to:

[LIST]
[*]Use a non-RAID SAS PCIe interface so would need suitable Linux drivers for this. RAID SAS cards are expensive and unnecessary to just run a tape drive. 
[*]Use an LTO 4 possibly 5 tape drive connected to this, so would need backup software that works with such drives. 
[/LIST]

I do not want to use tar balls as I believe doing so would mean having to unarchive the entire tar just to get one file out.

I've posted this here rather than in a hardware or specialist forum as I have no idea how to go about any of the above and would need nice clear instructions on what to do. 

Initial setup costs for a tape base backup system are just crazy for new drives (£2,000+ for the latest LTO7 drives but to be honest the sky is really the limit here) and even refurbished drives are pricey. So I would need to be absolutely certain that using Linux is not only possible but practical without me pulling my hair out in frustration.

Many thanks in hope.

---

### Post by freemedia2018 on 2018-12-02
> I do not want to use tar balls as I believe doing so would mean having to unarchive the entire tar just to get one file out.

Fun fact, the name tar comes from "tape archive." Tapes aren't random access, which is probably obvious, but it means you have to seek through the tape to where the file you want is. I've never tried using a tape drive, but you can extract individual files from tar archives. 

You still have to read the whole tar until you get to the file you want, because that's how it is physically laid out on the tape.

---

### Post by wheresthechocolate on 2018-12-02
Hi,

Thanks for the post.

Yes I am aware that tapes are sequential rather than random access, however I thought that using a tar meant you have to read the *whole* archive off the tape - many TB - and then extract the file you need due to the way that tars are organised. 

There are some backup solutions that just allow you to read the file you want off the tape without having to put the whole archive back onto disk.

If I'm wrong then great, that's at less one less headache - of I suspect many to come. ](*,)

---

### Post by freemedia2018 on 2018-12-02
```
tar -xvf file.tar name-of-file-to-retrieve
```

Haven't tried it with paths, pretty confident that will work too. It does work with more than one file (if you like) so you don't have to go through the whole tape again for each one.

---

### Post by wheresthechocolate on 2018-12-02
Hi freemedia,

Do you use tapes as a backup media?

If so what hardware etc do you use please?

---

