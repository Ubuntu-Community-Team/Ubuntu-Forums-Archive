---
title: "Python PIL problem"
date: 2007-04-14
forum: Programming Talk
---

### Post by cisforcojo on 2007-04-14
I am using the PIL and have this code (very simple):

import Image
pic = Image.open('image.jpg')

pic.show()

runs 'fine' but show() does nothing. Perhaps I am doing something wrong but in the tutorial it says that this should display the file?

---

### Post by WW on 2007-05-17
I just tried something similar.  When I try to use the show() function, I get the error "sh: xv: command not found".

[This tutorial]("http://www.pythonware.com/library/pil/handbook/introduction.htm"), after mentioning the show() functon, says
> 
(The standard version of show is not very efficient, since it saves the image to a temporary file and calls the xv utility to display the image. If you don't have xv installed, it won't even work. When it does work though, it is very handy for debugging and tests.)

The program **xv** is not installed in dapper, and I couldn't find a package for it. I do have imagemagick installed, which provides the **display** command, so as a hack, I made a symlink:
```

sudo ln -s /usr/bin/display /usr/local/bin/xv

```
Now running **xv** actually runs **display**, and the show() function works.

I have /usr/local/bin in my PATH. If you don't, and you don't want to bother setting it up, you could make the symlink in /usr/bin:
```

sudo ln -s /usr/bin/display /usr/bin/xv

```

---

### Post by cisforcojo on 2007-05-18
I just did as you suggested but no dice. I also have imagemagick installed and do have /usr/bin/display but I get the exact same turnout as before (nothing). The program just runs and finishes and doesn't display anything.
That 'xv' bit is interesting though. I also don't have it installed nor is there a .deb for it.

---

### Post by brunomfs on 2007-06-07
> **WW said:**
> I just tried something similar.  When I try to use the show() function, I get the error "sh: xv: command not found".

[This tutorial]("http://www.pythonware.com/library/pil/handbook/introduction.htm"), after mentioning the show() functon, says

The program **xv** is not installed in dapper, and I couldn't find a package for it. I do have imagemagick installed, which provides the **display** command, so as a hack, I made a symlink:
```

sudo ln -s /usr/bin/display /usr/local/bin/xv

```
Now running **xv** actually runs **display**, and the show() function works.

I have /usr/local/bin in my PATH. If you don't, and you don't want to bother setting it up, you could make the symlink in /usr/bin:
```

sudo ln -s /usr/bin/display /usr/bin/xv

```

Bumping to say it worked for me! :)

Thnx a lot!

---

### Post by emrahustun on 2008-02-26
pic.show() works. 
and something else. what about closing:)
how can we close that window with python?

thanks.

---

### Post by ronsheely on 2008-03-28
I tried something similar with xloadimage which can be installed using the Synaptic package manager or apt-get. After installing, I applied the following symbolic link.

    sudo ln -s /usr/bin/xloadimage /usr/bin/xv

Then you can display an image by xv <image filename>. However, xloadimage dumps a lot of status to stdout, so I use ImageMagick display like WW suggested above.

---

### Post by nick_h on 2008-03-28
I use Eye of Gnome which is installed by default.
```
sudo ln -s /usr/bin/eog /usr/bin/xv
```

---

### Post by Angelachen on 2010-01-18
I saw the following information posted by Emrahustun. I am wondering if anybody has realized this function closing this picture with python after showing a picture. My current research needs to realize this function. Please give me some advice. I will very appreciate it.
:)


pic.show() works. 
and something else. what about closing:)
how can we close that window with python?

thanks.
 		                   		  		  		 		 			 				__________________
				Emrah ÜSTÜN
[www.emrahustun.com]("http://www.emrahustun.com/")
:)

---

### Post by rosencrantz on 2010-02-10
@WW: There's an XV package for openSuSE - so I'd be surprised if there's nothing for Ubuntu - but it's a very old app, nevertheless

@angelachen:
what about brute force killing the image with popen:
os.popen('killall display') or os.popen('killall xv'), probably combined with a sleep or wait statement before that?

---

### Post by mvineetmenon on 2013-04-24
> **nick_h said:**
> I use Eye of Gnome which is installed by default.
```
sudo ln -s /usr/bin/eog /usr/bin/xv
```

Worked for me!
Thanks.

---

### Post by codemaniac on 2013-04-24
Old thread. Closed.

---

