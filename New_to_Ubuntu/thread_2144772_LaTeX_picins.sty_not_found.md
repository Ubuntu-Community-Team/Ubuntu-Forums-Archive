---
title: "LaTeX picins.sty not found"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2013-05-13
Hi,

seems that my system cant find the picins.sty file. So i went to google to solve the problem. 

The people said to download the picins.sty file from ctan - check
Than to copy it to /usr/share/texmf-texlive/tex/latex/ - IT WAS ALREADY THERE!
Than run sudo texhash - done

Still getting the error while the file is actually present in the folder ....

Can someone help me out?
Thanks

---

### Post by Impavidus on 2013-05-13
Remarkable. I never had a problem like that. If the file is there and you ran texhash it normally works.

I take it all (most) other LaTeX packages from /usr/share/texmf-texlive work fine? Also, are you positive the problem is it can't find your picins.sty, not that your picins.sty has the wrong version number? Because that frequently happens. Maybe you can post the first part of your log file. Also, if you compare the picins.sty from your system with the one from ctan, are they identical? Or different version number?

I just found the package on ctan. I see that it has a non-free license, which explains why it's not available from the repos. At least, it isn't mentioned in the description of one of the packages with LaTeX packages, nor is it part of TeXLive (it is part of MiKTeX). So I wonder how it got on your computer in the first place. Is this an office/university computer, administrated by someone else?

You could try downloading the .sty from ctan and store it in the same directory as your .tex file. I also see the package is over 20 years old, without any more maintenance. It doesn't really conform to the latest standards for packages. If you're not trying to compile some legacy code you may be better off with a more recent [alternative]("http://www.ctan.org/topic/text-flow"). I have heard people used the floatflt package with success.

---

### Post by Krabby.Linux on 2013-05-13
> **Impavidus said:**
> Remarkable. I never had a problem like that. If the file is there and you ran texhash it normally works.

I take it all (most) other LaTeX packages from /usr/share/texmf-texlive work fine? Also, are you positive the problem is it can't find your picins.sty, not that your picins.sty has the wrong version number? Because that frequently happens. Maybe you can post the first part of your log file. Also, if you compare the picins.sty from your system with the one from ctan, are they identical? Or different version number?

I just found the package on ctan. I see that it has a non-free license, which explains why it's not available from the repos. At least, it isn't mentioned in the description of one of the packages with LaTeX packages, nor is it part of TeXLive (it is part of MiKTeX). So I wonder how it got on your computer in the first place. Is this an office/university computer, administrated by someone else?

You could try downloading the .sty from ctan and store it in the same directory as your .tex file. I also see the package is over 20 years old, without any more maintenance. It doesn't really conform to the latest standards for packages. If you're not trying to compile some legacy code you may be better off with a more recent [alternative]("http://www.ctan.org/topic/text-flow"). I have heard people used the floatflt package with success.

Thanks for your post!

I got it! I dont know why but I had to copy it into the texmf-texlive folder AND the texmf folder. The totally stupid thing about it is that it has already worked before ...

I usually dont use this file anymore (It is needed for the \geometry options for latex documents) but I had a friend who needed some help with his document and my PC did not compile it!

Thanks!

---

