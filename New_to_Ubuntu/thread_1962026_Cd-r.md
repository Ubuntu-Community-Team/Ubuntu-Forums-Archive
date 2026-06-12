---
title: "Cd-r ?"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by jbalazs on 2012-04-20
I have my MRI pictures on a CD-R disk I can open it 
in Windows but I can't open it in Ubuntu 10.04
is there a way to open it in Ubuntu 10.04  ???
Thanks

---

### Post by Paqman on 2012-04-20
Can you see the files on the disk? What format are they in? Generally speaking Ubuntu should have no trouble opening image files off a CD.

---

### Post by cortman on 2012-04-20
I'm assuming you're saying you cant open the pictures to view them? Maybe a format you don't have a program for, what's the file extension?
Or are you saying you cannot open the CD in the file browser?

---

### Post by audiomick on 2012-04-20
Can you see anything at all on the CD with the file browser in Ubuntu?

Viewing the pictures might not be possible. It depends on how it is set up to work. If you can see picture files on the DVD, you might be able to open them with an Image viewer other than whatever windows tool it is that the DVD is set up for.

---

### Post by audiomick on 2012-04-20
> **Paqman said:**
> Generally speaking Ubuntu should have no trouble opening image files off a CD.

This is true, but I have encountered a case where there were X-ray pictures on a DVD that couldn't be read by an Ubuntu install. I don't remember details as it wasn't my DVD and it was a while back. At the time I was sure there must be a way around the problem, but didn't have a chance to look into it.

---

### Post by jbalazs on 2012-04-20
> **cortman said:**
> I'm assuming you're saying you cant open the pictures to view them? Maybe a format you don't have a program for, what's the file extension?
Or are you saying you cannot open the CD in the file browser?

extension .exe

---

### Post by Curtis6767 on 2012-04-20
Is this executable file on the CD loaded and then used to view the MRI?

---

### Post by jbalazs on 2012-04-20
> **Curtis6767 said:**
> Is this executable file on the CD loaded and then used to view the MRI?

Yes it is

---

### Post by Paqman on 2012-04-20
Sounds like what you've got there is a self-extracting archive. I believe wine should be able to handle that. Install [wine]("apt:wine") and try again.

---

### Post by ronaldbrijo on 2012-04-20
There could be folder in the cd that contains the pictures...

An exe file can only be run in a windows environment.

---

### Post by Jerry N on 2012-04-20
> **ronaldbrijo said:**
> There could be folder in the cd that contains the pictures...

An exe file can only be run in a windows environment.

I just had a look at my wife's ct scan disk from last fall (using Windows) and I did find a folder of pictures but they were just the raw pictures without anything to connect them together.  They could be viewed in xnview but I don't know their format.  It appears that the only way to get anything useful is to run the viewer, a Windows executable. I am not sure if Wine will help - it will be necessary to have the entire disk structure available to the viewer.  

Jerry

---

