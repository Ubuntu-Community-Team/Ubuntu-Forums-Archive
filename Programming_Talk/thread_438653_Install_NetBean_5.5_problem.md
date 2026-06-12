---
title: "Install NetBean 5.5 problem"
date: 2007-05-09
forum: Programming Talk
---

### Post by linhtinh321 on 2007-05-09
Hi , I got a problem while installing Netbean 5.5 : 

I have installed 3 packages from synaptic package manager : 
  + Netbeans5.5
  + Netbeans5.5-doc
  + Netbeans5.5-platform
The installation finished succesfully, however , when I start NetBeans from Applications -> Programming -> Netbean , it shows that Starting Netbeans for a while, then no thing show up. The starting netbeans window disappeared. 

I don't know what is the problem and how can I fix it. Please give me some advices. Thanks a lot.

---

### Post by hod139 on 2007-05-10
Make sure you also install and make default Sun's java.

---

### Post by linhtinh321 on 2007-05-11
> **hod139 said:**
> Make sure you also install and make default Sun's java.

Thank you for your reply, however , can you tell me clearly about install and make default Sun's java ? What does it mean ? Does it mean that I need to install java platform 6 first before install Netbeans IDE ? 
Regards.

---

### Post by samjh on 2007-05-11
> **linhtinh321 said:**
> Thank you for your reply, however , can you tell me clearly about install and make default Sun's java ? What does it mean ? Does it mean that I need to install java platform 6 first before install Netbeans IDE ? 
Regards.

Absolutely correct.

Open up the terminal and type this:
```
sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin
```sun-java6-jdk is the Sun JDK package, sun-java6-jre is the Sun Java Runtime Environment, and sun-java6-plugin is the web browser plugin (it will automatically install for various browsers).

You can alternatively install Java 5, by substituting the parts that say java6 with java5 in the above command.

Normally that will set your default Java to Sun Java.  But sometimes GCJ still remains as default.  To set your default Java package to Sun Java, type this into terminal:
```
sudo update-alternatives --config java
```You can then select the Java distribution you want to make default.

---

### Post by linhtinh321 on 2007-05-13
Thank samjh for your detailed help, I did as you said and now I can install JDK. However , I wonder how can I know the directory where java was installed in ? 
And , after install Java, I try to install NetBeans 5.5 from the repositories. After installation, I run NetBeans but it just appear the license aggreement  with a blank windows. Then nothing else pop-up. Hence , I still can not install NetBeans. 
Is there any additional configuration such as set variable path like in Windows ? and how can I do it ? 
Thanks for advices !

---

### Post by samjh on 2007-05-13
> **linhtinh321 said:**
> Thank samjh for your detailed help, I did as you said and now I can install JDK. However , I wonder how can I know the directory where java was installed in ?The most important parts are installed in /usr/lib/jvm directory.  There you will find a directory named java-6-sun-1.6.0.00 (if you installed Java 6).

> And , after install Java, I try to install NetBeans 5.5 from the repositories. After installation, I run NetBeans but it just appear the license aggreement  with a blank windows. Then nothing else pop-up. Hence , I still can not install NetBeans. 
Is there any additional configuration such as set variable path like in Windows ? and how can I do it ? 
Thanks for advices !The netbeans packages in the repositories don't actually install Netbeans.  They integrate netbeans into Ubuntu.

Here is what the package description says:
[quote=netbeans5.5 repository description]PLEASE NOTE: This is simply an installer package to insure that the NetBeans IDE is well integrated with your system. You *must* pre-downlown the NetBeans IDE tarball for this package to be installed correctly. You must have at least 263 MB of free space in /tmp (83 MB for the tarball and 180 MB to uncompress the tarball). From the NetBeans IDE 5.5 Download page:
[http://www.netbeans.info/downloads/all.php?b_id=2323](http://www.netbeans.info/downloads/all.php?b_id=2323)
Select the English(en) tgz Download Archive Distribution 82.8 MB
[http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1](http://www.netbeans.info/downloads/start.php?f_id=13710&lang_id=1)
and place the file at /tmp/netbeans-5_5.tar.gz (with root.root ownership).[/quote]So download the tarball from the link provided, and place it in /tmp as instructed with root root ownership.  And then, install the netbeans5.5 package from repositories.

I personally just use the binary installer provided by [www.netbeans.org](www.netbeans.org), and install it into the directory of my choice.  The installer creates a launcher on your desktop.

---

### Post by linhtinh321 on 2007-05-15
I tried 2 methods, but also got some problems.

        + For the installation with repositories, I pasted the file netbeans-5_5.tar.gz into the /temp file as in the instruction. After installation, there is just a license agreement with a blank windows. Nothing happened.
        + For using the bin file, the Netbeans start installing as normal process, and finish with a launcher on desktop. When I run netbeans, it start as normal, but end with a blank windows as below: 
--http://www.thomasnguyen.bravehost.com/1.png-- 
When I move the mouse in the blank windows, the pointer changes to "hand" pointer seems like it is pointing on a link. Then when I click, a new web page appear. 

Hence , I am wondering that the installation is fine, but my computer can not display the details in the Netbeans starting windows. Maybe this also happened with the license agreement windows. Does anyone know why this happen ? And how can I solve this ? Does it concerned with the graphic card driver ? I am using laptop IBM R52. 

Thanks for your advices.

---

### Post by samjh on 2007-05-15
Are you using Beryl?  Beryl is not compatible with Swing.

Apart from that, I can't think of any reason why you're having those problems.

---

### Post by linhtinh321 on 2007-05-15
I did not use Beryl. However, I used some openGL software. Do they affect the swing ?

---

### Post by samjh on 2007-05-16
Java and Swing have no problem with OpenGL, per se.  Only with Beryl.

Your problem is quite... interesting.  I've never come across it.  Sorry I'm not much of a help.

---

### Post by linhtinh321 on 2007-05-16
> **samjh said:**
> Sorry I'm not much of a help.

Don't say that. You helped me a lot ! I really appreciate your help ! Maybe my problem came from an incident when I play with Ubuntu. I've just started using Ubuntu for 3 weeks. Once again, thanks for you help. 
I'll try to ask somewhere else, hope can solve my problem. Then I will post the answer here.

---

### Post by linhtinh321 on 2007-05-17
I alreadly find the solution ! It's because of the "desktop effect" in Ubuntu. When I turn this off, Netbeans just works fine and now I can do Java programming in Ubuntu. I will try to find out whether there is an another solution to keep desktop effect on and Netbeans also works.

---

### Post by samjh on 2007-05-17
Wow, nice work.

The "desktop effects" use Compiz.  Beryl is an extension of Compiz.  I thought Sun had fixed Swing problems with Compiz with Java 6, but apparently not.

---

### Post by Levander on 2007-05-18
> **linhtinh321 said:**
> I alreadly find the solution ! It's because of the "desktop effect" in Ubuntu. When I turn this off, Netbeans just works fine and now I can do Java programming in Ubuntu. I will try to find out whether there is an another solution to keep desktop effect on and Netbeans also works.

What samjh is telling you is that the "desktop effects" you can activate in Feisty use Beryl to implement them.  And, Beryl is not working with the Swing.  Swing is one of Java's GUI libraries.  Netbeans uses Swing to implement it's GUI.

So, like you found out, you have to disable desktop effects (aka Beryl) to use Netbeans.

---

### Post by linhtinh321 on 2007-05-19
> **Levander said:**
> What samjh is telling you is that the "desktop effects" you can activate in Feisty use Beryl to implement them.  And, Beryl is not working with the Swing.  Swing is one of Java's GUI libraries.  Netbeans uses Swing to implement it's GUI.

So, like you found out, you have to disable desktop effects (aka Beryl) to use Netbeans.

I knew it.Thanks for your words. So, we just wait until Sun fix that problem.

---

