---
title: "Eclipse-- Error opening editor!"
date: 2007-10-16
forum: Programming Talk
---

### Post by nimafl on 2007-10-16
I updated my eclipse from Eclipse 2.2 to Eclipse 3.3. I downloaded the tar from the eclipe.org site. Before I did anything I removed my previous version of eclipse using the Synaptic package manager. 

I followed the directions from this site

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)


 But when I open eclipse and I link it to my OLD workspace I actually get this error
when I try to do anything(open project, go to help contents)

Here is an attachment. Anyone have similar problems?



[ATTACH]46553[/ATTACH]

---

### Post by tenmillionmilesaway on 2007-10-17
eclipse stores some of its plugin data in your workspace, in the .metadata folder (its hidden, press ctrl-H to show hidden folders) Your best bet would be to delete this .metadata folder.  This will probably allow you to start eclipse but afaik you wont see your project(s).  You will need to import them/create them again.  Note that you wont actually lose any of your java code by deleting .metadata but you may want to make a backup of your workspace incase something goes wrong.

Richard

---

### Post by nimafl on 2007-10-17
Thank you for replying to my post


I did what you told me to do. I went into my workspace. Deleted the .metafile folder. When I started eclipse up. This is what I got.


[ATTACH]46659[/ATTACH]



and



[ATTACH]46660[/ATTACH]



I also was not able to create a new Java project. When I clicked on the new project. The wizard popped up. I selected Java project and I clicked next. Nothing occurred when I clicked next! It did not allow me to create a new java project. Also when I imported my files into my workspace, I got the same problem as my first post.   

Thanks for the try though.

---

### Post by tenmillionmilesaway on 2007-10-18
Im not really sure what that is. Does it let you create new projects if you use a different workspace?  If so I would just use a different one and the create new projects and copy the code over.

---

### Post by #Reistlehr- on 2007-10-19
You never succesfully cleaned out the old eclipse files. I've had this problem before. I dont know where apt/synaptic install too, so i cant tell you where to delete from, but when i compiled from source, i put it in /opt and i had to delete files in ~/.eclipse ~/workspace and /opt/eclipse

remember if you are using the GUI to delete the files, to press ctrl+h to view the hidden files. You can backup the ~/workspace folder and import the projects later, although it will give you a version mismatch code when you import them. I had to go through and dleete all the extra .svn .cache and such from each dir in the project. 

Thats the only reason i dont like eclpise

---

### Post by chr on 2007-10-19
can you please specify how to delete the files, because i'm quite new to linux and couldn't figure it out. i have exactly the same problem as the quy above.

i have removed and the reinstalled eclipse again, deleted my workspace, but i still get the same errormassage as in post 3.

hope someone can help

best regards

christoph

---

### Post by chr on 2007-10-20
Hello,

isn't there somebody who has the same problem and who can provide some information? i'm really stuck with this problem now.

best regards

chr

---

### Post by chr on 2007-10-20
hello again,

i have now found out that there should be a problem with gij, which is automatically installed when upgrading to 7.10.

but it would be really nice if someone could specify, which files i have to remove now. i tried to remove and reinstall eclipse a few times now, but i always  get the same error message (like in post 1 and 3).

hope someone can help

best regards

chr

---

### Post by chr on 2007-10-21
ok,

if there is anybody who is interested i have found a solution for the problem.

after 7.10 is install there is a wrong path from eclipse to the /etc/eclipse folder.

in order to get eclipse to work again you need to change /usr/lib/jvm/java-gcj with /usr/lib/jvm/java-6-sun.

after that eclipse will work again.

hope you find it usefull.

best regards

chr

---

### Post by tenmillionmilesaway on 2007-10-21
You can the do the Java switch thing with ```
sudo update-alternatives --config java
```

Richard

---

### Post by chr on 2007-10-21
> **tenmillionmilesaway said:**
> You can the do the Java switch thing with ```
sudo update-alternatives --config java
```

Richard

that won't work. i tried it out.

eclipse will irgnore that information, it just referes to the path in etc/eclipse.

chr

---

### Post by tenmillionmilesaway on 2007-10-21
Ok, didn't know that.  When i install eclipse I usually get the latest version from the eclipse site and run it out of my home directory.

Richard

---

### Post by djtecha on 2007-10-21
that worked wonders for me thanks a lot! it also allowed me to get ant to run my graphics!!!

---

### Post by g3orge_florin on 2008-03-30
hello !

i use eclipse for c\c++ ...and i have the same problem "can't open the editor error" .
i have the Kubuntu 7.10 .... and this problem appear unexpectelly .... it was working fine and then it started that error to appear ...pls help !

---

### Post by socialday on 2008-07-19
Ok~ ! 

  Is there anyone could tell me the steps how to do ~!
You can give me a simple steps for guiding!

 Thanks anyway~!
:popcorn:
  JunJie Zhu

---

