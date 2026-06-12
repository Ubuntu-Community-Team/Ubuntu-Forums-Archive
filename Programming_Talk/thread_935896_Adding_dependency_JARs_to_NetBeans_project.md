---
title: "Adding dependency JARs to NetBeans project"
date: 2008-10-02
forum: Programming Talk
---

### Post by jamescox84 on 2008-10-02
I have wrote a program that depends on another jar file. Is they a way to have this jar file bundle up in the programs jar. So I can just send the jar file to other users without the entire contents of the dist folder. Any help apriciated! Thanks!

---

### Post by themusicwave on 2008-10-02
If you add the dependency as a library, then when you run a build, Netbeans will create a dist folder.  Inside it you will have your application's Jar and a Lib folder.  Inside lib, will be all of your dependencies.   

From here, the user can execute your application just fine as long as they have both your jar and lib folder.  What I usually do at this point is zip or tar the whole dist folder and send that to them.  They uncompress it an run the jar and everything works just fine.

I know you want one single, jar file, but why not just send one compressed folder?  Is that really so bad?

There may be someway to merge the jars, but I honestly have never tried.

---

### Post by Tomosaur on 2008-10-02
I'm pretty sure there is a way to do it by modifying the manifest file before building, but to be honest it's so much easier just to stick stuff in the lib folder. Unless you want to mess about with Ant, then I'd just avoid trying to cram everything into the .Jar file. I am inclined to agree with the 'just send a compressed folder' route, really.

---

### Post by jamescox84 on 2008-10-02
OK, no problem I'll just do that. I just wondered weather it was simple or not. But yes, I suppose it can just be zipped and sent. Thanks for the replys!

---

