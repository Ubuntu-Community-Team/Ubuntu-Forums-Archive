---
title: "JAR to DEB"
date: 2013-02-15
forum: Packaging and Compiling Programs
---

### Post by Malsasa on 2013-02-15
Hello, i wanna package JAR to DEB. I am interested in Ubuntu Packaging but still confused in.

If I have a JAR, does it need any shell script included in the DEB later? Can somebody give me simple explanation? I follow this tutorial: [http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/) but I confused for what the **myapp.sh** is. 

In the core, I want this DEB later, can act like anoteher DEB packaged in Ubuntu. It can install app, place icon in menu, show description in USC, and can track dependency. How can I create it?

If I should create a shell script, what I should write in the script file? I have read the Ubuntu and Debian Packaging Guide, but i am confused. I am newbie but curious here  :) 

Thank you...

---

### Post by schragge on 2013-02-15
*myapp.sh* is a small wrapper script that invokes the JAR. According to Debian policy, Java applications should behave as ordinary binaries. For your application, the script obviously will be named differently. Please do not append .sh extension to it, see [Debian policy 10.4]("http://www.debian.org/doc/debian-policy/ch-files.html#s-scripts")

Have a look at [Debian Java policy]("http://www.debian.org/doc/packaging-manuals/java-policy/").

---

### Post by Malsasa on 2013-02-15
Thank you, I wanna read them and back here to ask you again :)

---

### Post by slickymaster on 2013-02-15
The [Maven 2 DEB Plugin]("http://mojo.codehaus.org/deb-maven-plugin/using-deb.html") can be used to produce a Debian package from any project that can be packaged as a JAR. Debian packages can be used on most Debian-based Linux Disributions including Ubuntu.

---

### Post by Malsasa on 2013-02-19
Hello slickymaster, 

I've given a page: [http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/](http://blog.noizeramp.com/2005/08/31/packaging-java-applications-for-ubuntu-and-other-debians/) by my friend in #ubuntu-indonesia IRC channel. I follow that, and works. By adding a complete mirror of Lintian's Tags pages, I have created my first DEB in my life. Surely, I have to **borrow** existing DEB in my /var archives that comes from official repo (high quality DEB) so my DEB actually same with that DEB in directory structure or configuration files ;) It is the easiest way for learning Ubuntu/Debian Packaging for me... Just **imitate** any existing DEB :) Use archive manager for open DEB contents.

I've installed VirtualBox 2 days ago and installed Maverick and Precise there. I tried to install my DEB on both OS, and works! Fine! I am so happy. Thank you...

But my DEB is still need some improvements :) Lintian says there is still many warnings (but no error). Thank you.

So, the solution is following that page and have Lintian pages :)

---

