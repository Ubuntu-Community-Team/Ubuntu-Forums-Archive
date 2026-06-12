---
title: "How to get rid of grub rescue"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by majid5 on 2015-02-16
Dear Users,

I am a newcomer to ubuntu. I am using Ubuntu 12.04 on Linux 64. Accidently, I deleted some important data on my ubuntu. I tried to recover them. I also followed the procedures explained at this link ([https://www.youtube.com/watch?v=EncqYP1ijFg](https://www.youtube.com/watch?v=EncqYP1ijFg)). When I restarted my system corresponds to the link I got the following error
error: no such partition.
grub rescue>

I really need to back my deleted data. I would be greatly appreciated if anybody helps me


Thanks in advance

MD

---

### Post by majid5 on 2015-02-16
Dear Users,

I could flee from the grub rescue. Actually I followed the methods explained at my previous email.When I checked the folder in which my data was located I found that it is empty yet. I do not really know what I need to do. The removed data was very important for me.

Could you please guide me how can I recover my data?

Thanks in advance

MD

---

### Post by oldfred on 2015-02-16
You can see if deeper search in testdisk works.
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

If not then you can try photorec which also is part of testdisk. Photorec is slow. It took me overnight to run, does not find full file name, just files by extension, and if also finds deleted files. I have many text files that I saved daily. My backup was several weeks old. So I had many copies of .txt files that I had to first figure out which was which then do many compares to find changes.

      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by majid5 on 2015-02-16
Dear Oldfred,

Thank you very much for your suggestions. Actually, I used the "photorec" to recover my data. But, I have a bunch of files that when I opened them I faced just with some text. e.g. I wanted to back up some Fortran codes (.f90 extension) but I could not find any file with ".f90" extension.

Do you know how can we back up the Fortran codes files witg "photorec"?

I would be greatly appreciated if you share your comments.

Thanks in advance

---

### Post by oldfred on 2015-02-16
Somewhere photorec does show all the extensions it looks for. 
But if file looks like a txt file, it may just recover your files with the .txt extension or whatever they look like. If compiled files not sure then if not on list whether there is a way to recover.

I have not used any of the other recovery tools that scan drives, but they may have other choices?

---

