---
title: "Failure to launch Ubuntu Software Center"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by Karelvand on 2012-11-16
[FONT=Arial][SIZE=2]Hi, I'm new to Ubuntu and encountered a problem I could use some help with.
I've tried installing the R statistics package using the Ubuntu Software Center, however when I try to launch it, I get an error message telling me that the application has closed unexpectedly. 
When I click details it states the problem is the ' ExecutablePath'  and 'could not determine the package or source package name.' 
[/SIZE][/FONT][FONT=Arial][SIZE=2]
I've since managed to install R through: 
sudo apt-get install [/SIZE][/FONT][SIZE=3][FONT=Arial][SIZE=2]r-base

But I'd like the Software Center to run as well, as I'm still looking for a way to obtain the Rcmdr (GUI).

I have a feeling I'm lacking some depencies, but I don't know how to find out which ones (if so). Either that or there may be something wrong with my specific Ubuntu build, as it'd be fair to say that I wasn't too sure of what I was doing (though I was flying on default as far as possible). Thanks in advance for any help!

Karel[/SIZE][/FONT]
[/SIZE]

---

### Post by newb85 on 2012-11-16
First, Welcome to Ubuntu and the forums!

Installing with the Software Center or apt-get from the command prompt should give you the same result.  Dependency handling is the same under-the-hood.  I'm not sure why you had trouble when you installed through SC.  Perhaps a verbatim quote of the error message would be helpful.

The package name of the GUI you're looking for is r-cran-rcmdr, so you could install it thus:

```
sudo apt-get install r-cran-rcmdr
```

Again, you *should* be able to install it through SC and get the exact same result.

---

### Post by ibjsb4 on 2012-11-16
You may find it better to use Synaptic Package Manager

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

sudo apt-get install synaptic

---

