---
title: "How to add repository"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Paulo M. on 2008-05-31
Hello everyone!
Please, I need some help: I'm still a newbie in ubuntu, and I want to install an application I found in CVS at sourceforge.net (stylus toolbox 1.1) but I have 2 problems... In first place I don't know how to add (if needed) that repository ([http://stylus-toolbox.cvs.sourceforge.net/stylus-toolbox/Stylus%20Toolbox/](http://stylus-toolbox.cvs.sourceforge.net/stylus-toolbox/Stylus%20Toolbox/)) and either don't know how to install that application (I've already installed cvs in synaptic)
Can, anyone, please tell me how to?

Thanks in advance!

---

### Post by mkrahmeh on 2008-06-02
> **Paulo M. said:**
> ([http://stylus-toolbox.cvs.sourceforge.net/stylus-toolbox/Stylus%20Toolbox/](http://stylus-toolbox.cvs.sourceforge.net/stylus-toolbox/Stylus%20Toolbox/)) 

u need to add the URL to the list of sources in which ur pakcage manager search..this is done by
```
sudo kate /etc/apt/sources.list
```
which will open the file sources.list using the kate program (u can use any other text editor of ur choice)
then add the URL to the list of URLs and save the file..
hope this will work

---

### Post by atomkarinca on 2008-06-02
> **mkrahmeh said:**
> u need to add the URL to the list of sources in which ur pakcage manager search..this is done by
```
sudo kate /etc/apt/sources.list
```which will open the file sources.list using the kate program (u can use any other text editor of ur choice)
then add the URL to the list of URLs and save the file..
hope this will work

In Ubuntu Kate is not preinstalled. There are two ways:

1. Hit alt+f2 and type

```
gksudo gedit /etc/apt/sources.list
```

it will prompt you your password, copy and paste the repository address, save and exit. Open up a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

and now you can install that software

```
sudo apt-get install application-name
```

2. Go to System > Administration > Software Sources, under Third-Party Software tab click Add, copy and paste the repository address and select Add Source. The rest goes the same as the first one.

---

### Post by Sef on 2008-06-04
Moved to Absolute Beginners.

---

### Post by Paulo M. on 2008-06-04
Thank you very much both of you...
I guess the problem I had was not really concerning about adding repository.
I was making a mistake in trying to install the application in synaptic... as I was told that's not really like that!
But knowledge is always needed... and after all, I learn something else!

Thanks and...
all my best!

(and please, forgive for posting this one in the wrong place...and for not answering before, but, because the maintenance issue, I could not login in the forum yesterday and the day before)

:popcorn:

---

### Post by Joeb454 on 2008-06-04
Do you still have the issue?

If so is it with adding a repository or installing something **from** the repository?

---

### Post by Paulo M. on 2008-06-04
Hello again!
Well, in the end the problem wasn't about adding  repository, was about install an application in CVS.
But, the question here, got its finality - I learn how to add a repository witch was something I didn't know, and this way I learns how to do it.
So, here's my Thank You!

---

