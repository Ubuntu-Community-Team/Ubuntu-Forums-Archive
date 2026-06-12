---
title: "Textwrangler ubuntu alternative"
date: 2011-11-15
forum: Programming Talk
---

### Post by eipgene on 2011-11-15
I just started to use Ubuntu after 3 years with Mac.. I'm still trying to find a textwrangler alternative in Ubuntu but couldn't find one yet.. I read this post: [http://ubuntuforums.org/showthread.php?t=358014](http://ubuntuforums.org/showthread.php?t=358014) and installed Geany. Unfortunately Geany doesn't have the function to allow me save my scripts directly to a server. That's probably one of the most helpful and convenient feature of Textwrangler.. 

Someone mentioned mounting the server and I talked this to my colleague and was told this won't work for my computer at home..

While I still can use editors and then transfer the file through SFTP.. I'd love to be able to use something like Textwrangler.. 

Please let me know if anyone has a good idea of how to solve this "problem".

Thanks guys.

---

### Post by karlson on 2011-11-15
> **eipgene said:**
> 
Someone mentioned mounting the server and I talked this to my colleague and was told this won't work for my computer at home..

Maybe.  Maybe not.  Most people won't allow it.

> 
While I still can use editors and then transfer the file through SFTP.. I'd love to be able to use something like Textwrangler.. 


Have you considered Eclipse Application Server?

---

### Post by eipgene on 2011-11-15
> **karlson said:**
> Maybe.  Maybe not.  Most people won't allow it.



Have you considered Eclipse Application Server?

I'm not familiar with Eclipse... and I feel that's a bit complicated to use..

---

### Post by 11jmb on 2011-11-15
I believe that tramp in emacs lets you ftp/sftp pretty easily.

---

### Post by ofnuts on 2011-11-15
> **eipgene said:**
> I just started to use Ubuntu after 3 years with Mac.. I'm still trying to find a textwrangler alternative in Ubuntu but couldn't find one yet.. I read this post: [http://ubuntuforums.org/showthread.php?t=358014](http://ubuntuforums.org/showthread.php?t=358014) and installed Geany. Unfortunately Geany doesn't have the function to allow me save my scripts directly to a server. That's probably one of the most helpful and convenient feature of Textwrangler.. 

Someone mentioned mounting the server and I talked this to my colleague and was told this won't work for my computer at home..

While I still can use editors and then transfer the file through SFTP.. I'd love to be able to use something like Textwrangler.. 

Please let me know if anyone has a good idea of how to solve this "problem".

Thanks guys.In the KDE desktop the KDE utilities (Kate text editor, KDiff3 comparator, the Dolphin and Konqueror file explorers and some others) can handle files and directories directly to/from ftp/sftp.

---

### Post by eipgene on 2011-11-15
> **11jmb said:**
> I believe that tramp in emacs lets you ftp/sftp pretty easily.

I'm trying to install tramp from this tutorial:
[http://www.gnu.org/s/tramp/#Installation](http://www.gnu.org/s/tramp/#Installation)

I downloaded it, unpack it and created the symbolic link. However, when I tried command ./configure --with-contrib. This is the message I got that has one error 


root@localhost:/usr/local/share/emacs/tramp# ./configure --with-contrib
configure: Tramp 2.2.3
checking for gmake... no
checking for make... make
checking for reasonable make version... ok
checking whether make sets $(MAKE)... yes
checking for emacs... yes
checking for emacs flavor... emacs
checking for emacs gvfs support... yes
checking for emacs gateway support... yes
checking for emacs utilities support... no
checking for emacs version... ok
checking for base64.el... ok
checking for format-spec.el... linked to contrib directory
checking for password.el... linked to contrib directory
checking for socks.el... linked to contrib directory
checking for makeinfo... no
configure: error: makeinfo not found


What's going on here in the last line..? With this error, I can't move to next step..

---

### Post by memilanuk on 2011-11-16
I think Komodo Edit does what you're looking for... cross platform (Windows, Mac, Linux) too.

---

### Post by whitethorn on 2011-11-16
So you can sftp the files but you can't mount the folder locally? Why not give it a try, you can use nautilus or sshfs. Here's a thread of someone trying to get it to work. 

[http://ubuntuforums.org/showthread.php?t=1748938](http://ubuntuforums.org/showthread.php?t=1748938)

The main problem is just getting the server mounted. Once you get it mounted you should be able to use whatever text/IDE editor you want. So focus on that first.

Oh and take a look at the plugins available for geany. :)

---

### Post by 11jmb on 2011-11-16
> **eipgene said:**
> 
What's going on here in the last line..? With this error, I can't move to next step..

I'm honestly not sure what that error is, but tramp is bundled in emacs since version 22.3, so you should be able to just use it out of the box (I'm assuming you installed version 23)


I must forewarn you, though, that emacs will take a bit of getting used to. Its keyboard commands are very different, and there is a learning curve, but it is also very useful and powerful when you get the hang of it. If you are looking for something else, you might be a bit more comfortable with gedit. It is a simple editor that will not take much getting used to, and you can also use it to edit remote files (not quite as elegantly as with emacs, though)

---

