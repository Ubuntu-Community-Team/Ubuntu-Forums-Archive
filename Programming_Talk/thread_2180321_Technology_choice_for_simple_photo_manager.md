---
title: "Technology choice for simple photo manager"
date: 2013-10-12
forum: Programming Talk
---

### Post by frank.bommeli on 2013-10-12
Hi all

I have a hobby project in mind: 
a simple photo manager for Ubuntu desktop. (no phone or tablet)

The main feature would require:
 - moving, copying files
 - renaming files and folder.
 - reading, writing exif data from / to jpeg fies.
 - generating thumbnails from large original jpeg pictures

I would like to integrate it with Ubuntu i.e.,
 - integrated to the launcher
 - when connecting my camera I should have the possibility to start my application

These are, I think, the relevant information to the application.

I have problem to make up my mind about which technology I should use.

 - I'm a Java developer. Thus I could make the application in Java.

 - On the other hand, apparently QML, Javascript and C++ are the recommended way to write apps for Ubuntu, But I know nothing (almost) about these technologies. And I know that it will be extremly time consuming until I can get some results.

 - I first thought Python was the way to go on the desktop, but after researching [http://developer.ubuntu.com/](http://developer.ubuntu.com/) I rather got the impression it is deprecated.

Are there other technologies I should consider?

Is there a killing criterion which could help me decide about the technology choice?

Do you have some input to help me decide?

Thanks a lot

---

### Post by tgalati4 on 2013-10-12
I would first evaluate the existing applications:

[http://lifehacker.com/5877908/the-best-photo-management-app-for-linux](http://lifehacker.com/5877908/the-best-photo-management-app-for-linux)

[http://www.techradar.com/us/news/software/applications/8-of-the-best-photo-managers-for-linux-692441](http://www.techradar.com/us/news/software/applications/8-of-the-best-photo-managers-for-linux-692441)

Make a list of things that you like and don't like from the existing photo managers.

Pick the one that is closest and then look at the source code and the developer's website and see what development tools are being used.

That's how I would do it.

---

### Post by frank.bommeli on 2013-10-13
Thank your for your replay  tgalati4
I considered most of the existing applications you suggested. (I did however not know Fotoxx)
Most of these have a lot of features, which are interesting, but they mainly fail in managing multiple source for the pictures. The local pictures and the backup. The backup having, in my case about 30K pictures, The local repository only the pictures of the current year. So I always have problems finding older pictures :(

As of now I played around for a while with qml. But I think it would take me too long to learn qml, javascript and C++. For now I tend to go for java / javafx.

---

### Post by tgalati4 on 2013-10-13
I think performance is the issue that the other photomanagers keep the local library small.  Otherwise it would take several seconds to scan the database (if it was huge) for every operation.  So it might be possible to either modify one of the existing managers to scan and keep active the entire photo archive, or write your own.   You might have to go down a few programming paths before you find a workable solution.  

I would also search the web for performance issues on each of the major photo managers to see which one performs best and look at that application for programming architecture.

---

### Post by ofnuts on 2013-10-14
> **frank.bommeli said:**
> 
Most of these have a lot of features, which are interesting, but they mainly fail in managing multiple source for the pictures. The local pictures and the backup. The backup having, in my case about 30K pictures, The local repository only the pictures of the current year. So I always have problems finding older pictures :(

Your backup is not a backup but an archive.... two very different concepts...

---

