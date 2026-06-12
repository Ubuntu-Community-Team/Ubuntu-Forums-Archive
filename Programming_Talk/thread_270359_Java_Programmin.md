---
title: "Java Programmin"
date: 2006-10-03
forum: Programming Talk
---

### Post by christodoulos77 on 2006-10-03
Hello!

I'm new to linux and I have a little stupid question!
I want to program in Java.
Is the any easy graphical tool in Ubuntu 6.06 that I can use?

Thank!

---

### Post by Buffalo Soldier on 2006-10-03
> **christodoulos77 said:**
> Hello!

I'm new to linux and I have a little stupid question!
I want to program in Java.
Is the any easy graphical tool in Ubuntu 6.06 that I can use?

Thank!Installable thru apt-get (but have to enable multiverse and universe repository): [Anjuta](http://anjuta.sourceforge.net/) and [Eclipse](http://www.eclipse.org/).

Have to download and install by yourself: [Netbeans](http://www.netbeans.org/)

New to learning Java myself, but so far for the simple lessons I find gedit and terminal is sufficient.

P/S: to install Sun's JDK--> [https://help.ubuntu.com/community/Java?highlight=%28java%29](https://help.ubuntu.com/community/Java?highlight=%28java%29)

---

### Post by welshboy on 2006-10-03
I have to agree with BuffaloSoldier,

The way I got Java was to fire up Synaptic, (I assume you're using Ubuntu and not Kubuntu)
ensure that you have the Ubuntu 6.06 LTS (binary) repository set to multiverse and universe.

Then search for sun-java5, and select what you want to install
Once that's done, you'll need to type in the terminal the following command:

    sudo update-alternatives --config java

Which will then allow you to choose the right Java Run time, so that the programs compile with the correct version of java.  (Personally, I uninstalled gij just to be sure).

And you should then have a system ready for java development.  

In terms of editors, Eclipse is among the best out there, and it's a doddle to install, you just download it, and then decompress it to your home folder, (it's less hassle that way, especially when you download updates) and then you click on the Eclipse executable, (the icon for it is a KDE style cog i think).

You should then have a fully functional developement environment.  But gedit is good too, but Eclipse has loads of advanced features like decent debugging and Ant capabilities.

Hope this little rant has helped a little. 

If there's anything else I can do to help, please don't hesitate to ask.

welshboy.

---

### Post by christodoulos77 on 2006-10-03
How do I set Ubuntu to multiverse?

---

### Post by marcomangiante on 2006-10-03
Hello,
for ubuntu 6.06 click on this link:

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

for kubuntu 6.06 click on this:

[https://help.ubuntu.com/community/Repositories/Kubuntu]("https://help.ubuntu.com/community/Repositories/Kubuntu")

--
Regards,

Marco Mangiante

---

### Post by hod139 on 2006-10-04
I wrote a howto for installing eclipse and Sun's java available here: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

