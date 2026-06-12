---
title: "Create install CD"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by japhyr on 2008-06-11
I started using ubuntu from a 7.04 install dvd.  I spent 9+ hours yesterday downloading and installing 7.10 and 8.04.  Is there a way to create a dvd I could use to re-install 8.04 if I ever need to start over from scratch?

---

### Post by wolfen69 on 2008-06-11
[AptOnCD]("http://aptoncd.sourceforge.net/") is probably what you want. you can find it in synaptic.

---

### Post by stchman on 2008-06-11
> **japhyr said:**
> I started using ubuntu from a 7.04 install dvd.  I spent 9+ hours yesterday downloading and installing 7.10 and 8.04.  Is there a way to create a dvd I could use to re-install 8.04 if I ever need to start over from scratch?

If you downloaded the .iso form Ubuntu then create a CD and you are good to go.

---

### Post by JoshuaRL on 2008-06-11
I've heard great things about Remastersys.  I think that is more like what you're talking about.  That will let you do a reinstall back to a good configuration.

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

**EDIT**

That link didn't work for me.  [This link is from Wikipedia.](http://en.wikipedia.org/wiki/Remastersys)

**/EDIT**

---

### Post by valmorel on 2008-06-11
If you are in the UK, you might consider checking out the Linux magazines currently on the bookshelves, as I am pretty sure one of them comes with a bootable installation DVD for 8.04 this month :-)

---

### Post by cosine352 on 2008-06-11
look at this link
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by japhyr on 2008-06-11
Thanks for all the feedback.  I'll check these out and make myself a backup.  Regarding the magazines, I saw that some of them have dvd's, but those magazines were ~$15, as opposed to ~$5 without dvd's.

---

### Post by shailendra on 2008-06-11
Hi,
The simplest way is to download the ISO file and burn it on a CD. It is very quick. Hardly takes one hour.

---

### Post by alienexplorers on 2008-06-11
The repository for remartersys is:
> deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
Load the file from synaptic and start it using:
> sudo remastersys backup name.iso
This creates a backup of your entire system and everything loaded on it.
Be prepared for a very large file to be made.  Needs a DVD to load the .iso file on.

---

### Post by japhyr on 2008-08-16
I finally took the time to start this process.  I successfully created a HH liveCD from the download, and checked it.  That's nice to have.

I downloaded remastersys through Synaptic, and would like to verify that I am about to use it correctly.  I want to back up my system with all the programs and settings I have downloaded, but not my local data.  I think the way to do that is

```
sudo remastersys dist
```
and then back up my home folder separately, with settings but no data.

Does that sound correct?  I also don't really understand what the cdfs option does.  Do I want to use that at all?

---

