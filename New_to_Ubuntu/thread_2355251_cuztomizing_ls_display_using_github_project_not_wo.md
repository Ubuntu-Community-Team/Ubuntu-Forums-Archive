---
title: "cuztomizing ls display using github project not working as I would like"
date: 2017-03-10
forum: New to Ubuntu
---

### Post by jfab10 on 2017-03-10
I'm fairly new to this but I'm simply trying to use the [LS_COLORS extension]("https://github.com/trapd00r/LS_COLORS") so that my files are listed with different colors depending on their extension. I already it have it in my ~ directory under .dircolors as I followed the installation instructions on the page. I even made random files with different extension on the fly in ~ and they have the coloring as shown on the screenshot of the project page so I know it works, well partially.  However, this doesn't seem to take effect across the entire system as when I go to /mnt/c/Users/myname everything is light brown (extension 1:33 I know this because I have my shell prompt red so I was trying out different colors) ..there's not distinction between files and directories...none whatsoever. I've messed around with .bashrc so many times already I don't know what else to do. This isn't a necessity....but it'd be nice to group files by color...thanks a lot for your input

---

### Post by steeldriver on 2017-03-10
Hello and welcome to the forums

My first guess would be that /mnt/c/Users/myname is an external filesystem that doesn't support the file permission bits that dircolors is using to distinguish between the types (or is mounted with a mask that obscures them)

---

### Post by jfab10 on 2017-03-10
any way to get around this? I've even tried not using the project...just modifying the .bashrc as explained here 
[http://linux-sxs.org/housekeeping/lscolors.html](http://linux-sxs.org/housekeeping/lscolors.html) 
Does it not work because this is bash on windows and its not a native bash environment? 
Also, I forgot to mention if I don't use this project it goes back to its default colors, so blue for most things and blue but with green background for directories
so this project is allowing for sub filesystem to change the ls color...just not how I want it.. Thanks
[FONT=Tahoma][COLOR=#0000FF]



[/COLOR]

[/FONT]

---

