---
title: "[SOLVED] Backing up my DVD collection to an external hard drive"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2008-11-22
I've got quite a few DVDs in my collection that are getting scratched up and I'd like to back them up to my external hard drive.

I was wondering what applications are the best for backing up DVDs, which would allow you to back them up as an ISO or an mpeg file?

I found dvd::rip, but I don't think you can back them up to a .iso file. I'm pretty sure you can rip them to an mpeg file, but the set up is a little confusing.

What are your favorite dvd ripping programs, which allow you to rip to .iso and .mp4 (or whatever), and have an easy to use GUI?

---

### Post by davideotape on 2008-11-22
I have used handbrake in the past, when I was still on windows. I know there is a linux version, but not sure if it is gui or command line interface.

---

### Post by Skripka on 2008-11-22
Handbrake is a nice tool.

---

### Post by Lazy-buntu on 2008-11-22
I looked at the handbrake website, which should work fine for dvd > .mp4, but I don't think it supports dvd > .iso

I forgot to mention, too, I dual boot ubuntu and vista. So, it can be a windows or ubuntu app.

---

### Post by Lazy-buntu on 2008-11-22
Anyone have experience with Devede or ManDVD and ubuntu?

---

### Post by bryncoles on 2008-11-22
k9copy has a very user friendly gui (its built in KDE after all), it has no problems running in ubuntu, i have only ever used it to create iso files so cant say anything about mp4's or avi's or whatever. 

but i tend to save as iso's, then watch them in vlc player or burn them to disc. you can do either with an iso file!

---

### Post by Lazy-buntu on 2008-11-22
Thanks I'll try that. I installed ManDVD, dvd::rip, and Devede...all are pretty confusing when all I want to do is DVD > .ISO or DVD> .MP4

---

### Post by m_duck on 2008-11-22
k9copy is able to backup a DVD to ISO. I think it can also do MP4.

---

### Post by ronnielsen1 on 2008-11-22
+1 for k9copy

---

### Post by Lazy-buntu on 2008-11-22
Noob question: how do I completely uninstall ManDVD (I installed it from a .deb)?

---

### Post by Skripka on 2008-11-22
> **Lazy-buntu said:**
> Noob question: how do I completely uninstall ManDVD (I installed it from a .deb)?

It will be listed in Synaptic like any other package--remove as you would any other package in Synaptic.

---

### Post by m_duck on 2008-11-22
I think if it's installed from a deb it should appear in synaptic if you search for it. Then click the box next to it, mark for complete removal and click apply.

---

### Post by Lazy-buntu on 2008-11-22
That's what I thought, but I can't find it in synaptic lol.

I'll keep looking. Thanks for the quick reply.

---

### Post by Lazy-buntu on 2008-11-22
Getting back on topic :)

For those who like K9copy, what do or what would you use as a Windows equivalent?

---

### Post by prshah on 2008-11-22
> **Lazy-buntu said:**
> That's what I thought, but I can't find it in synaptic lol.

```
sudo dpkg -r packagename
``` Use tabcompletion if you have doubts about the package name.

I use gnomebaker (now no longer installed by default) to create .iso's. Then, if the ISO image is less than 4.7g, I use DVDisaster (it's in the repos) to stuff error-correction coding (RS02) into the ISO image. This allows fully transparent and software independent error recovery on most DVD drives, and is ignored on drives that don't support it, such as cheaper home DVD/DivX players.

---

### Post by m_duck on 2008-11-22
Just checked and "packagename" is mandvd so;
```
sudo dpkg -r mandvd
```should work. Or you could remove it in synaptic after searching for "man dvd".

---

### Post by Lazy-buntu on 2008-11-22
Yeah I found it after a restart-X

For those of you that recommended k9copy, do you have a favorite windows equivalent?

---

### Post by m_duck on 2008-11-22
I'm afraid I've not really done any DVD things in Windows - apart from watching them. I've briefly used [handbrake](http://handbrake.fr/) but I cannot remember if it can do ISO's or not. I think it is also necessary to use a program called dvd decrypter or something like that.

---

### Post by bryncoles on 2008-11-22
in windows i used to use dvd decrypter and clone dvd to do the same. clone dvd is pay-for software, but dvd decrypter isnt 

[http://www.dvddecrypter.org.uk/](http://www.dvddecrypter.org.uk/)

that links you to a burning tool you can use though instead of clone dvd, though id switched to ubuntu by the time that became an issue...

---

### Post by k3lt01 on 2008-11-22
DVD decryptor was the best Windows Application for what you want to do but it is now very out of date and wont decrypt newer DVDs or Blu-rays encoding properly.

Be very aware that DVD decrypter hasn't been worked on for about 3 or 4 years because it was found to be illegal to use such software to bypass DVD encryption.

DVD Shrink was also pretty good to cut them back to 4.7gb. If you have older DVDs use these two programs to achieve what you want in Windows.

K9Copy does the exact same thing in Linux and is only one program so it will save you time.

---

### Post by Ducatiboy Stu on 2008-11-22
If you want to rip current DVD's with DVDdcrypter, then download a utilities prog called Ripit4me

This will analyse the DVD and create a protected sector list that DVDdcryter will use to ripp current release DVD's...

---

### Post by ronnielsen1 on 2008-11-23
> 
For those who like K9copy, what do or what would you use as a Windows equivalent?
I do all my stuff in linux. I just use windows for an occasional game that wine won't run or the occasional web site. There's no need.

---

### Post by Teabicky on 2008-11-23
I use k9copy to create .iso images and acidrip to make mpegs, with good results.

---

### Post by m_duck on 2008-11-23
Another way I've just seen to back up the DVD to an ISO image is using "dd". Check it out [here](http://ubuntuforums.org/showpost.php?p=6174356&postcount=25).

There is some more info on the dd command [here](https://help.ubuntu.com/community/BackupYourSystem) in the Ubuntu docs.

---

