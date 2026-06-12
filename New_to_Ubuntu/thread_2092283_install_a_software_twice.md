---
title: "install a software twice"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by FRKiran on 2012-12-07
I have recently begun to use ubuntu 12.10 and I have tried to install texlive on it.I will firs describe what I have done :   :(
I downloaded the files needed for installation from textlive sources in  folder named :texlive" in my home.then I opened a terminal and tryied to install texlive by the command:
```
[COLOR=red]sudo perl install-tl[/COLOR]
```There were some actions taking place and the everything finished with this massage:
```
See
   /usr/local/texlive/2012/index.html
 for links to documentation.  The TeX Live web site
 contains updates and corrections: http://tug.org/texlive.

 TeX Live is a joint project of the TeX user groups around the world;
 please consider supporting it by joining the group best for you. The
 list of user groups is on the web at http://tug.org/usergroups.html.


 Add /usr/local/texlive/2012/texmf/doc/man to MANPATH, if not dynamically determined.
 Add /usr/local/texlive/2012/texmf/doc/info to INFOPATH.

 Most importantly, add /usr/local/texlive/2012/bin/x86_64-linux
 to your PATH for current and future sessions.

 Welcome to TeX Live!
```Now for adding the PATH I opened another terminal and typed:"
```
sudo gedit /etc/environment
```In the gedit's window I add a part between the words that was present there before so 
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```changed to 
```
PATH="/usr/local/texlive/2012/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```But the program just dose not work because any attempt to run it will give the massage:
```
The program 'xelatex' is currently not installed. You can install it by typing:sudo apt-get install texlive-xetex
```normaly by using xelatex filename.tex I should be able to make a pdf of the text I intended to write.Then I chacked if the software were installed using the command:
```
locate textlive
```which gave me a long lists of items like:
```
usr/local/texlive/2012/texmf/doc/generic/elhyphen/anc-test.ltx
```Bus the strange thing is when I try to remove the installed software this will happen:
```
FBKIREN:~$ sudo apt-get remove texlive-*[LEFT]Package 'texlive-lang-english' is not installed, so not removed[/LEFT]
 The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 preview-latex-style ps2eps ruby ruby1.9.1 tex-gyre  ttf-marvosy
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```Instead of the second line there were a list of packages.So basically there was a list with the form:
 ```
Package 'package name' is not installed, so not removed
```Then repeated the installation process hoping to correct the mistakes.Now here is my questions:


[LIST=1]
[*]Did the software installed twice ? and so is there two of the same software installed on my computer? If yes how should I remove one of them?
[*]If the software has been installed why by trying to remove it the computer give the massage:"Package 'package name' is not installed, so not removed"?Where do you think the problem is?
[*]How can I add the PATHes that were in the third code I wrote above?
[/LIST]

---

### Post by audiomick on 2012-12-07
I think your problems are all basically to do with having installed, or tried to install, the program from a downloaded package instead of through the software centre. Did you look for the program in the software centre?

To be honest,  I don't know exactly what happens if you try and install something from the software centre that has already been installed without using the systems package management, i.e. from a downloaded package or similar. Despite not knowing exactly what this would do, I would try installing from the software centre. With some luck, this might solve all your problems. As I said, though, I don't know for sure that this is the best thing to do. That is just what I would do.

As a general rule, if you want to install a program, any program, always look for it in the software centre first. Install from there if you possibly can. Only if you cannot find a program in there, or if you definitely need a newer version than the one available there, should you consider installing by hand. If you need a program that isn't there, try to find a .deb package for it. These are installed by the systems package management.

---

### Post by Impavidus on 2012-12-07
In my case texlive was installed by default. This may not be the case in every installation (apparently not on yours), but you should be able to install (and add xetex to that if you like) with```
sudo apt-get install texlive
#sudo apt-get install texlive-xetex
``` xelatex is not included in texlive by default, therefore "xelatex filename.tex" doesn't work yet. "latex filename.tex" does.

As you didn't install using the package management system, the package management system is not able to uninstall texlive and says it's not installed. Most likely, however, it has been installed (just once).

My advice would be to undo your manual installation (most files are in /usr/local/texlive, just delete that directory, and check /etc, /var and your homedir for tex related stuff, although keeping a few files shouldn't harm and deleting the wrong ones will cripple your system, so be conservative), change your PATH back to what is was and install the packages texlive and texlive-xetex using apt-get.

Of course, if you insist on manual installation, you just have to manually install xetex and it should work. Installing xetex from the repository will automatically install texlive from the repository, giving you two installations, which is not very nice (it will work, but different versions may not cooperate nicely).

Finally, if you're missing latex packages you can have a look at packages like texlive-latex-extra, texlive-lang-whatever-language-you-want etc. Sometimes the latex packages in the repositories are seriously outdated and the more obscure ones may not be present at all, so you may have to install some individual packages manually in /usr/local/share/texmf/.

---

### Post by audiomick on 2012-12-07
> **Impavidus said:**
>  install the packages texlive and texlive-xetex using apt-get.
The software centre is a GUI front end for apt-get, effectively. Using apt in the  terminal is practically the same as using the software centre or synaptic package manager (not installed by default, available in the software centre or from the terminal with apt-get install synaptic , and my preference for installing things. )

> 
Finally, if you're missing latex packages you can have a look at packages like texlive-latex-extra, texlive-lang-whatever-language-you-want etc. Sometimes the latex packages in the repositories are seriously outdated and the more obscure ones may not be present at all, so you may have to install some individual packages manually in /usr/local/share/texmf/.

Do a search from "texlive" in the software centre (or synaptic) and you will get a great long list of these packages.

---

