---
title: "Hello, some questions about Emacs installation, Thanks in Advance"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by shewenhao on 2008-05-18
I followed this HOW TO to install the emacs and Latex together. But when I tried to start the emacs  21.4a (X11) I got this error message:

An error has occurred while loading '/home/shewenhao/.emacs';
File error:"Cannot open load file", "/usr/share/emacs/site-lisp/preview-latex/preview-latex.el"

And I checked the /usr/share/emacs/site-lisp folder, I did not find preview-latex folder. Any one could give me a tip? It seems like Ijust did not install the preview latex thing. But I do not know where is the problem??

Thanks lot!!

---

### Post by shewenhao on 2008-05-18
Adding some more detaisl:

The HOWTO I did follow is this one:

[http://ubuntuforums.org/showthread.php?t=80344](http://ubuntuforums.org/showthread.php?t=80344)

I followed this and I should installed preview-latex during this process. I did check:

shewenhao@shewenhao-laptop:~$ sudo apt-get install preview-latex
[sudo] password for shewenhao: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting auctex instead of preview-latex
auctex is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by shewenhao on 2008-05-18
I followed this HOW TO to install the emacs and Latex together. But when I tried to start the emacs 21.4a (X11) I got this error message:

An error has occurred while loading '/home/shewenhao/.emacs';
File error:"Cannot open load file", "/usr/share/emacs/site-lisp/preview-latex/preview-latex.el"

And I checked the /usr/share/emacs/site-lisp folder, I did not find preview-latex folder. Any one could give me a tip? It seems like Ijust did not install the preview latex thing. But I do not know where is the problem??

Thanks lot!!

Adding some more detaisl:

The HOWTO I did follow is this one:

[http://ubuntuforums.org/showthread.php?t=80344](http://ubuntuforums.org/showthread.php?t=80344)

I followed this and I should installed preview-latex during this process. I did check:

shewenhao@shewenhao-laptop:~$ sudo apt-get install preview-latex
[sudo] password for shewenhao:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting auctex instead of preview-latex
auctex is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by shewenhao on 2008-05-18
I do not know whether I should post this here in the Absolute beginner talk part of this forum. If this is not right place, please tell me where I should post it:)

---

### Post by Xiong Chiamiov on 2008-05-18
You can take a look at the preview-latex package in Synaptic and see where it has installed its files.  I don't use Synaptic, but I think it's one of the options in the bottom-left?

---

### Post by Xiong Chiamiov on 2008-05-18
From PM:
[quote=shewenhao]
But I did follow this step below and I am quitesure that I did install the preview-latexI found that

sudo apt-get install emacs21 emacs-extra emacs-goodies-el emacs auctex preview-latex xfonts-jmk

How do you think??
Thank you very much!
[/quote]

I wasn't asking if you had installed the package; I was curious where the package had installed **to**.  Since you said that the preview-latex folder isn't where emacs is looking for it, it should be somewhere else; we just have to link where it is to where emacs thinks it should be.  But first, we have to find it, and that's the information I was trying to get from you.

Please do a search in Synaptic for preview-latex, then select it and click Properties up at the top.  From there, go to the Installed Files tab, and copy and paste here what you see, preferably inside code tags.

---

### Post by shewenhao on 2008-05-22
thank you. i will do it tonight and I will tell you what I got from searching work later. Using windows now....

---

### Post by shewenhao on 2008-05-23
Hi, I am new in using Emacs. I got some problem on loading the Emacs. There is an error at beginning but after this the Emacs works OKAY.

But I really really want to know what is the problem. The error notification I got is:

[COLOR="Red"]An error has occurred while loading `/home/shewenhao/.emacs':                   
                                                                                
Symbol's function definition is void: hscroll-global-mode                       
                                                                                
To ensure normal operation, you should investigate and remove the               
cause of the error in your initialization file.  Start Emacs with               
the `--debug-init' option to view a complete error backtrace.[/COLOR]



Seems like the Symbol has some problem. Thanks in Advance:popcorn:

---

### Post by shewenhao on 2008-05-23
Any one knows about this? Or I posted it in wrong place? Thankyou!

---

