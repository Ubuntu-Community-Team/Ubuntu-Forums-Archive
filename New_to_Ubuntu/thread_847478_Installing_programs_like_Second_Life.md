---
title: "Installing programs like Second Life"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by elzorroviejo on 2008-07-02
OK, I am trying to install Second Life on this machine. I get to their download page, click download and firefox starts doing its thing. A window pops open asking me what to do with the download. The default option is to let the Archive manager deal with it. Seeing as how the d/l is a tar.bz2 package, I figured I'd let the default handle things. However, once the d/l is finished, the Archive Manager asks what to do. I tell it to extract the from the tar.bz2 file and to put it all in a folder in /usr. It churns away for a bit and then pops up with a failure notice. When I look to see what is happening behind the scenes, I see that the Archive Manager doesn't have the appropriate permissions. So, the graphic interface tool is pretty much worthless, and that means I will have to do this via the command line/terminal. 

As a newbie to Linux, I am a little shaky with command line stuff. I think this calls for 
[CENTER]sudo apt-get install secondlife_i686_1_19_1_4.tar.bz2[/CENTER]
yes? Except that when I ran that I got 
[CENTER]Building dependency tree       
Reading state information... Done
E: Couldn't find package secondlife_i686_1_19_1_4.tar.bz2[/CENTER]

So, what am I doing wrong? 

Thanks for any help/feedback.

---

### Post by hyper_ch on 2008-07-02
Try getdeb:  [http://www.getdeb.net/app.php?name=Second+Life](http://www.getdeb.net/app.php?name=Second+Life)

---

### Post by cmnorton on 2008-07-02
I do not recall a case where I used apt-get install and specified a file name, tar or other kind of file. apt-get install, I believe, is to be used with the package name, but not the version of the file. 

If you go with the .bz2 file, then you are unpacking, configuring, and then making source. 
If you use apt-get install, you are going after what's in the repositories.

---

