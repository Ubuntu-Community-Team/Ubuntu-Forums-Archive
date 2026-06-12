---
title: "Where to install Netbeans"
date: 2013-01-29
forum: Programming Talk
---

### Post by desesperado on 2013-01-29
I need your expert help. I'm planning on installing Netbeans 7.2.1 on my Ubuntu 12.10. So far I've already installed JDK 7u11 without any problems and already downloaded Netbeans from Oracle site.

My question is this where should I install Netbeans? Should I accept the default /usr/local/netbeans-7.2.1 or should I change this path to my /home?

I'm questioning because someone told me not to install it in the default proposed installation path because later on, working with Netbeans I would not have permissions to write that folder thus disabling me from add Libraries to my projects, installing and uninstalling plugins to the IDE, and even with Glassfish server configuration.

I've googled in order to cast a light on my doubts to no avail. The only thing I found was this [http://forums.netbeans.org/ntopic37298.html](http://forums.netbeans.org/ntopic37298.html), at Netbeans forum which brought even some more doubts.

Can anyone help me?

---

### Post by r-senior on 2013-01-29
Netbeans should install plugins under your home directory, even if you install the base elsewhere but if I'm using anything for Java development from an archive, whether its Netbeans, Glassfish, Tomcat, Maven or similar, I put it under my home directory. It avoids any permission problems during development, especially servers, and is unaffected by OS upgrades and reinstalls.

It's still a good idea to keep projects and software separate and obviously servers should be properly installed and secured for testing and production use.

---

### Post by desesperado on 2013-01-30
First of all let me thank you, r-senior, for your prompt answer.

So, if I understood you correctly, providing I keep software (I think you are referring to the folder where Netbeans, Tomcat and Glassfish are installed) and projects folders separate, in your opinion I should install Netbeans, Tomcat and GlassFish in my home directory rather then on /usr/share or /usr/local because in these locations I’ll be more than likely to run into permissions problems down the line? Did I get it right?

---

### Post by r-senior on 2013-01-30
Yes, you *may* run into permission problems if you install in shared directories and you will lose them if you re-install the OS.

---

### Post by desesperado on 2013-01-30
Ok, I'll proceed accordingly and make the all installation in my home directory.

r-senior, once again I thank you for your advises and the time you lost on helping me. You've been a gentleman.

---

### Post by slickymaster on 2013-01-30
If you are the only user that will be using Netbeans, don't run the installer using **sudo** and you will be prompted to select installation directory defaulting to your user home folder.
Just in the case of having multiple users launching NetBeans from the same installation then you should run installer using **sudo** and select **/user/local** as the installation directory.

If you're going to opt to install it normally (not using sudo), don't forget to add the Netbeans' bin folder to your system path if you later on want to run it from the command line. You'll have to add the following line to your **.bashrc** file:
```
export PATH=$PATH:~/netbeans-7.2.1/bin
```

---

### Post by desesperado on 2013-02-01
Thank you for your advice slickymaster. I've already installed it in my home directory as r-senior advised.

I will now close this thread since my problem is solved.

---

