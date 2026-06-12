---
title: "[SOLVED] Virus protection --- Linux and dual-boot Windows"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by raequin on 2008-06-02
I am dual booting Hardy and Vista on my laptop.  What should I do for protection from viruses while running Ubuntu?  I am concerned about both the Linux install, and putting viruses on my Windows install while having the NTFS drives mounted.

I (obviously?) don't know much about viruses.  It seems important to know what could happen in this respect to Windows while I am running Ubuntu.  Could viruses get on the NTFS drives while I'm using Linux, and then when I next run Vista they start doing their evil thing?

Then there's always the question of Linux viruses.  Do you consider it necessary to protect my system from them?

---

### Post by bumanie on 2008-06-02
There are about 30 known linux viruses and they are already protected against at the kernel level. If you are going to share files with the ntfs partition it may be a good idea to run an anti-virus scan on any files that you will move from ubuntu to vista, prior to moving them. You can get clamav via synaptic or you can get linux version of avg free and I think avast free have a linux version also.

---

### Post by Xiong Chiamiov on 2008-06-02
There are no Linux viruses in the wild.  There've been one or two created in labs, but they were patched out of existance a long time ago.

Because of the nature of permissions and such (not to mention that Windows executables have to run through Wine), you don't have to worry about giving your Windows partition viruses either while running Ubuntu.

If you really feel like it, there are Linux versions of ClamAV and avast!.  They're mainly just to scan files for Windows viruses so you know if things are clean or not before you pass them on to your friends.

---

### Post by duckville on 2008-06-02
I guess, depending on the sites you access it possible to download a win virus on your linux system. But that virus would nout be able to harm you. Once it does not have x permissions (execute) you're fine. I guess (in theory) if that file does get onto a windows partition e.g. if you unknowingly copy it there, then access the same file while in windows....

N.B: that's just in theory, it's a long shot and it's just from the top of my head.
I think if you had a windows AV product it would see the file as a virus when you try to access it. so it may cancel out my theory.... or does it:

what if your AV does not scan every file as you open it...? just a thought.

---

### Post by rraj.be on 2008-06-02
In ubuntu you need not wory about any virus.

For a virus to be executed first it should be active on your system.

That is it should be under control of any external active controller like a java script or a auto run program..

Even if you get a windows virus in ubuntu you can identify it because in ubuntu each downloaded item will be under your knowledge and nothing happens hidden.

When you boot into your windows almost there wont be any virus spreading from ubuntu to windows, because , even if they are present, they wont be active.

You should run it explicitly to infect your system.

Hence there is no need for you to worry about this problem.

---

### Post by lisati on 2008-06-02
[LIST=1]
[*]Your Linux installation is unlikely to be hurt by a Linux virus
[*]Your Windows installation is unlikely to be hurt by a Windows virus while you're using Linux
[/LIST]
It is, however, still possible to store a Windows virus on your Linux installation, just be careful not to pass it on!

If you want reassurance there are AV programs that come in Linux versions.

---

### Post by tom56 on 2008-06-02
As long as you have an up to date antivirus program running in Windows (I recommend AVG Free) then you'll be fine.

---

### Post by raequin on 2008-06-02
Thank you all.  That is what I was looking to learn.

---

### Post by ukripper on 2008-06-02
if you need more info and want to try CLAMAV which is quiet popular and robust open source and also picks up Linux and Windows viruses.

here is the link
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

