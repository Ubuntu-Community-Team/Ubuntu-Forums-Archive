---
title: "Edit Win7 Home Premium ISO in Kubuntu"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by Feathers McGraw on 2013-04-23
Hi all,

I'm looking to do a fresh install of Windows 7 on my friend's laptop as a precursor to installing *buntu as part of a dual-boot for them.

Their licence key is for an OEM version of Windows 7 Home Premium.

I recently did this on my own computer, and unknowingly used an OEM ISO image to install Win7... which promptly had a tantrum when I tried to enter my OEM licence key.

After going through the fuss of searching for a Microsoft support number for ages, ringing tech support and watching a fairly clueless employee root around using remote assistance trying to activate a proprietary version with an OEM key, I am not keen on doing the same again. Eventually the tech guy gave me a new licence key for a proprietary version...but the experience was like pulling teeth.

*SO.*

I read [here]("http://social.technet.microsoft.com/Forums/en-US/w7itproinstall/thread/c805da6b-cbd2-4a40-9ea7-cc17391cf4bf") that it is possible to download the ISO file for a proprietary version of Win7 and modify the "ei.cfg" file, changing the "channel" value to "OEM", to create a disk that will work with an OEM licence key.

**Is there an easy way to edit the ISO file in Kubuntu?**

Many thanks,

Feathers

---

### Post by audunpoi on 2013-04-23
I used Iso master in the past, but it seems to have some bad reviews lately. Anyway it worked for me.

---

### Post by Mark Phelps on 2013-04-23
Not aware of any way to directly modify an ISO file.  The way this is usually done is as follows:
1) Extract the ISO file into its individual components
2) Modify the component(s)
3) Rebuild the ISO file from the modified component(s)

But ... if you want more details, suggest you check a Win7 forum: sevenforums.com -- as they have sections and tutorials that deal with this.

---

### Post by Feathers McGraw on 2013-04-23
Thank you both for the replies!
 



I actually tried ISO master before posting but I got the error "view failed, please change options/viewer".

After a bit of internet rummaging, I uncovered [this question on askubuntu](http://askubuntu.com/questions/228690/why-iso-master-editor-does-not-read-windows-images). Apparently **ISO master doesn't support UDF**.




Mark, I'll try your method. I'm sure I could do it in Windows but the objective is not only to get it done, but to learn how to do it in Linux so I don't have to use Windows!

Yes, I appreciate the irony of learning how to do it using a Windows boot disk...;)



Feathers

---

