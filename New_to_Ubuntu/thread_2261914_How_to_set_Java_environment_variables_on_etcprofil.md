---
title: "How to set Java environment variables on /etc/profile?"
date: 2015-01-21
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-21
I am trying to set up JDK environment variables so I can run IntelliJ IDEA IDE. I am new to Linux in general but googled and found that I needed both of these lines after the .bashrc file in Home:

 export JDK_HOME=/home/name/Applications/Java/JDK/jdk1.8.0_31 
export JAVA_HOME=/home/name/Applications/Java/JDK/jdk1.8.0_31 

However, I still received the same error that I need to point to a JDK when I tried to run the IDE. I then came across this: [https://stackoverflow.com/questions/14199937/cannot-launch-intellij-idea12-in-ubuntu-12-using-desktop-link](https://stackoverflow.com/questions/14199937/cannot-launch-intellij-idea12-in-ubuntu-12-using-desktop-link), where it says I need to place the above commands on /etc/profile. I found /etc/profile.d instead and I tried to add the commands after the bash_completion.sh file but I don't have write permissions so it could not save.

P.S. I am new to both programming and Linux (I have been told that programmers prefer UNIX systems so I might as well get used to it). I am currently learning my first programming language, Java. Any tips/advices regarding anything to do with learning/understanding Java/Linux, such as commands to manage JDK versions and whether the environment variables I am setting up are system-wide or current user only? I've heard that creating symbolic links makes something easier but I don't know what or how.

---

### Post by Holger_Gehrke on 2015-01-22
Have you tried executing these two export commands in a shell and then starting IDEA in that shell ? I am asking because the values imply that you've installed the JDK by hand in a rather unusual place instead of using a JDK installed from the repositories.

---

### Post by steeldriver on 2015-01-22
... agreed, making **system-wide** profile changes (i.e. via /etc/profile or /etc/profile.d/) referring to a particular **user's** home directory seems like a bad idea

---

### Post by monkeybrain20122 on 2015-01-22
Try add this line 

```
export PATH=$JAVA_HOME/bin:$PATH

```

I don't think you need to put those lines in /etc/profile. In fact .profile in the user's account overrides /etc/profile if I am not mistaken.

---

### Post by garycheng12 on 2015-01-22
> **Holger_Gehrke said:**
> Have you tried executing these two export commands in a shell and then starting IDEA in that shell ? I am asking because the values imply that you've installed the JDK by hand in a rather unusual place instead of using a JDK installed from the repositories.

I'm not sure how--do I just copy the 2 commands and paste them on the terminal? I installed JDK by hand (from the site) on the Home partition because I accidentally deleted the Java folder in the default location while running several commands to uninstall Java completely (I found that OpenJDK gave me problems and wanted to delete that as well as any traces of Java installed to prevent a cesspool of problems and start from a clean slate). I didn't know how to get permissions to create an empty Java folder to the default location where applications are installed to install JDK into so I just installed it in the Home partition. I figured this would be easier for me to manage and in the event that I screw up the OS by tinkering too much, if I reformat I can just use the already installed Java on the Home partition and avoid these problems of installing and setting up Java.

Is there a problem with installing JDK via Oracle's site instead of through repositories? I read that applications installed from repositories tend to be behind compared to installing via the website. As a Windows user, it is always recommended to update a program if it is not up-to-date. For Linux, it seems that people are not as eager to do that as the newest versions may not be fully compatible with the Linux distribution. How often is this the case and what is recommended?

---

### Post by monkeybrain20122 on 2015-01-22
> **garycheng12 said:**
> 
Is there a problem with installing JDK via Oracle's site instead of through repositories? I read that applications installed from repositories tend to be behind compared to installing via the website. As a Windows user, it is always recommended to update a program if it is not up-to-date. For Linux, it seems that people are not as eager to do that as the newest versions may not be fully compatible with the Linux distribution. How often is this the case and what is recommended?

No, JAVA is kept up to date. For most purpose Openjdk and Oracle java are the same (openjdk is the standard even for Oracle's Java since openjdk7) However there are some applications that for whatever reasons require oracle java (e.g  some of Oracle's products) It is possible to install multiple versions of java and switch between them with a mechanism called 'update-alternatives' in Debian based distros such as Ubuntu. There is even a gui to do the switch called galternatives (in the repo) 

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by garycheng12 on 2015-01-22
Out of curiosity, how would I go about uninstalling Java from where I installed it (in the Home partition)? Since I manually installed it, I can't run the command that I would run if it was a package I installed from a repository. I don't think I can just delete the Java directory--what if by manually installing it to a folder, it installs other files that are outside of the folder that would be left behind if I were just to delete the Java folder?

---

### Post by monkeybrain20122 on 2015-01-22
In the home folder it is easy to 'uninstall', just delete all the installed files.

---

### Post by Holger_Gehrke on 2015-01-23
> **garycheng12 said:**
> Out of curiosity, how would I go about uninstalling Java from where I installed it (in the Home partition)? Since I manually installed it, I can't run the command that I would run if it was a package I installed from a repository. I don't think I can just delete the Java directory--what if by manually installing it to a folder, it installs other files that are outside of the folder that would be left behind if I were just to delete the Java folder?

Unless you called one of the installed programs with 'sudo', it would not have the necessary permissions to write outside your $HOME. So you can just delete it.

---

