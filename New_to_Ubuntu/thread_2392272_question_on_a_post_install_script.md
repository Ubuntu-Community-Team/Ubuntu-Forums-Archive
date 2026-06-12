---
title: "question on a post install script"
date: 2018-05-18
forum: New to Ubuntu
---

### Post by dfortier77 on 2018-05-18
Hello all,
I have been dabbling with linux on, and off for years, and never made the full switch mostly due to work. Now that things have changed there it has afforded me more freedom, and I have committed to giving it at least three months as my daily driver. So in order to prepare for the inevitable newbie "OMG I borked it" I have started working on a post install script to speed up the process. I have managed to figure a bunch of things out that I think will get me where i wont to go for the most part, but getting files from gnome-look is a sticking point (first of many I'm sure :D ).

I'm would like to use Telinkrin for theme and icons, but i cant seem to get the download to work properly with wget. I got around the issue with the theme by downloading it from github instead, but that doesnt appear to be an option for the icons. The code i used is below and the path was just taken from right clicking on the download and "copy link location". I realize its just icons and i can easily install them manually, but i would also like to further my understanding of the process and linux.

```
wget -P /home/test/Downloads/Themes/Telinkrin/icons https://www.gnome-look.org/p/1230480/startdownload?file_id=1525107206&file_name=Telinkrin-icon-theme.tar.xz&file_type=application/x-xz&file_size=7707536&url=https%3A%2F%2Fdl.opendesktop.org%2Fapi%2Ffiles%2Fdownloadfile%2Fid%2F1525107206%2Fs%2F7c7ad37bcbd389c461c04c5430ea3a66%2Ft%2F1526684713%2Fu%2F455718%2FTelinkrin-icon-theme.tar.xz
```

Any insight would be greatly appreciated
thank you

Almost forgot. I'm on Ubuntu 18.04, if it makes a difference

---

### Post by TheFu on 2018-05-18
Many download sites require javascript to work, so wget cannot be used with those.
I wouldn't bother with the -P.  Why not just have your terminal and pwd correct?

Sorry, I don't know **anything** about themes. Desktop stuff is low on my priority.

---

### Post by Holger_Gehrke on 2018-05-19
The long URL you've got there goes through several levels of redirection. You can get the real URL of the file by using the network-analysis in Firefox web-developer tools. It's 
[https://dl.opendesktop.org/api/files/downloadfile/id/1525107206/s/5449db48c2a11a3af8d76541a8aef2d2/t/1526721431/u/455718/Telinkrin-icon-theme.tar.xz](https://dl.opendesktop.org/api/files/downloadfile/id/1525107206/s/5449db48c2a11a3af8d76541a8aef2d2/t/1526721431/u/455718/Telinkrin-icon-theme.tar.xz) 
Alternatively there's a link to a git-repository at the top of the page. That link is outdated, but a search on github finds the new URL ([https://github.com/gusbemacbe/Telinkrin-icon-theme](https://github.com/gusbemacbe/Telinkrin-icon-theme)) and you can either 'git clone' that or download a zip from [https://github.com/gusbemacbe/Telinkrin-icon-theme/archive/master.zip](https://github.com/gusbemacbe/Telinkrin-icon-theme/archive/master.zip) .

Holger

---

### Post by dfortier77 on 2018-05-19
Thanks Holger_Gehrke,
I have installed Firefox web tools, and will do some research on how to find the direct link you gave since I will probably have the same issue working with extensions. Not sure how i didn't find the new github page, because I did search for it after getting the 404 error on the link provided. I must have fat fingered something.

thanks again.

---

### Post by dfortier77 on 2018-05-19
TheFu
I may be misunderstanding your comment, but the -P is to redirect the download to the given directory, not for password.

thank you for the insight though.

---

