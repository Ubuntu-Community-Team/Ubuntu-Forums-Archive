---
title: "Help installing Leiningen"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by raymond17 on 2014-08-13
Hi,

I am a very new linux user, running Xubuntu. I am trying to install leiningen so I can then install Light Table. The issue I am coming across is that I am not sure where/ how to put the Lein script. The full instructions to install Leiningen are below:


[LIST]
[*][SIZE=2]Download the lein script. For Windows, download lein.bat.[/SIZE]
[*][SIZE=2]Place it on your $PATH where your shell can find it (eg. ~/bin).[/SIZE]
[*][SIZE=2]Set it to be an executable (chmod a+x ~/bin/lein).[/SIZE]
[*][SIZE=2]Run the Lein script (eg. "./lein" or "sh lein") without quotes.[/SIZE]
[/LIST]
[SIZE=2][/SIZE]So I am unsure which bin I should put this in. I tried making a bin folder where I had the lein file (Downloads) because I believe ~ is supposed to be wherever the terminal is currently pointed. That didn't work though so I searched around and a number of people said that scripts like this should be in /usr/local/bin . I do not seem to be able to move the file to that location however. 
[B]
Where specifically do I need to put the lein script for it to be a recognized command in the terminal?[/B]

---

### Post by coldraven on 2014-08-14
As a user you can only write files in your home folder and below. To copy files to /usr/bin you need to have root permission.
So there are two choices. 
1. Learn some Bash skills and use a terminal.
Tip: On the command line if you see the dollar sign you are logged in as a user, if you see the hash symbol you are logged in as root.
```
~$
~#

```
2. Use the file manager Thunar as root. See here for how to do it.
 **Remember that as root you can delete important system files and mess up your installation!**
So when you have done, quit Thunar to avoid mistakes.
[http://www.pcmediacenter.com.au/forum/topic/39182-add-open-as-root-to-thunar-in-xfce-46-arch-ubuntu/](http://www.pcmediacenter.com.au/forum/topic/39182-add-open-as-root-to-thunar-in-xfce-46-arch-ubuntu/)

Your files will be in /home/yourname/Downloads, so using Thunar click on Filesystem>Home>yourname>Downloads
Then copy the file, right click on it and change the permissions.

---

### Post by steeldriver on 2014-08-14
Personally I'd put stuff like that in $HOME/bin

You may need to create it if it doesn't already exist - in which case it will be added to your PATH automatically next time you log in

---

