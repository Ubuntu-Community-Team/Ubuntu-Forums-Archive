---
title: "How do I update Cheese?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Sailorcancer on 2008-09-27
The webcam application.  I noticed that the one I downloaded from the add/remove section was out of date.  So I went to the official site and downloaded the newer version, but I have no clue how to install it.

I downloaded the pack to my desktop.  Any help would be great thanks!

---

### Post by Nepherte on 2008-09-27
Here's a .deb version: [http://www.getdeb.net/app/Cheese](http://www.getdeb.net/app/Cheese) Just download and double click.

---

### Post by Flimm on 2008-09-27
If I were you, I would download Cheese from getdeb.net:
[http://www.getdeb.net/app/Cheese](http://www.getdeb.net/app/Cheese)

It's not the very latest version (2.23.92 instead of 2.24), but it's packaged for Ubuntu, which means all you have to do to install it is double click.

---

### Post by Sailorcancer on 2008-09-27
Thanks!

Also I still have one last question.

For some reason my webcam is weird with Cheese.  Like if I open the program and I can see myself the next time I open it I can not see myself.  Any fix?

---

### Post by Naiki Muliaina on 2008-09-27
If you want the very latest 2.24, follow the follow this :)

Open terminal and cd to the unpacked cheese folder, if youve unpacked it to your desktop it should be:

```
cd Desktop/cheese-2.24.0
```

Your command line should now look like this:

```
nai@WispMint ~/Desktop/cheese-2.24.0 $ 
```

This means your terminal is in your cheese folder. Now run configure, make, make install.

```

./configure
make
make install
```

After the config youll prolly see text whizz up the screen for a minute, its just making the 'makefile'.

Hope that helps!

---

### Post by Sailorcancer on 2008-09-27
> **Naiki Muliaina said:**
> If you want the very latest 2.24, follow the follow this :)

Open terminal and cd to the unpacked cheese folder, if youve unpacked it to your desktop it should be:

```
cd Desktop/cheese-2.24.0
```

Your command line should now look like this:

```
nai@WispMint ~/Desktop/cheese-2.24.0 $ 
```

This means your terminal is in your cheese folder. Now run configure, make, make install.

```

./configure
make
make install
```

After the config youll prolly see text whizz up the screen for a minute, its just making the 'makefile'.

Hope that helps!

Thanks!  I got this error:
```

configure: error: Your intltool is too old.  You need intltool 0.40.0 or later.
```

Also how do you get the line space for the commands?

---

### Post by Naiki Muliaina on 2008-09-27
The most recent intltool in the Ubuntu repos is 0.37.1. Youll have to download it install that manually too. If your a newbie to Linux, it may be easier for you to take whats been suggested .deb wise. If not you may have to route about google for the download yourself. I think ive seen 0.41 somewhere on the web but not sure where. If i come across it ill post the link.

Also what do you mean 'line space' in terminal?

---

### Post by dadsbrkn on 2008-09-27
You can easily install the latest version using this web based app installer,its called Appnr.  [http://appnr.com]("http://appnr.com") Then search for cheese.

---

### Post by Sailorcancer on 2008-10-01
> **Naiki Muliaina said:**
> The most recent intltool in the Ubuntu repos is 0.37.1. Youll have to download it install that manually too. If your a newbie to Linux, it may be easier for you to take whats been suggested .deb wise. If not you may have to route about google for the download yourself. I think ive seen 0.41 somewhere on the web but not sure where. If i come across it ill post the link.

Also what do you mean 'line space' in terminal?

Sorry for taking so long to get back.  

I mean this kind of space:

```
./configure
make
make install
```

How do you make it go down a line in the terminal.

---

### Post by skralljt on 2008-10-21
You don't make it go down a line.  Those are three separate commands.  You enter each line seperately.

---

### Post by jseiser on 2008-10-21
Read Kmandla tutorial its great, 

[http://kmandla.wordpress.com/2008/09/16/howto-build-software-updates-in-ubuntu/](http://kmandla.wordpress.com/2008/09/16/howto-build-software-updates-in-ubuntu/)

---

