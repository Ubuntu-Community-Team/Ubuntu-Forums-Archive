---
title: "Alias I liked for downloading"
date: 2009-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by tjtoml on 2009-03-09
I find myself using wget a lot to grab images and videos and the like quite a lot. I'm sure there are some pretty neat graphical ways to do this but I like using the command line, so I put together this alias to simplify the process a bit. 

This uses xclip to grab the text on your clipboard, so if you don't have it, grab it. 

```
$sudo apt-get install xclip
```

same with wget, though I'm fairly sure it comes in the default package list, so I can't imaging why you wouldn't have it. 

```
$sudo apt-get install wget
```

now for the alias:

```
$cd ~/
$gedit .bashrc

```

and add the line 

```
alias download='wget -c $(xclip -o)'
```

Save and exit. From now on when you open up a bash shell and have a url on your clipboard that you want to download, just type 
```
$download
``` 
and off you go.
 
Obviously, you can tweak the wget options to your heart's delight.

---

