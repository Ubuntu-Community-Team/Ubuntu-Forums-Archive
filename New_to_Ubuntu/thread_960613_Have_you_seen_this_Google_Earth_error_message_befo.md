---
title: "Have you seen this Google Earth error message before???"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-27
Ubunteros,

I upgraded my Ubuntu O/S from 7.10 to 8.04LTS.

I installed Google Earth (4.3.7284.3916 (beta)) and get this error message, please see attached picture. It reads:

"Google Earth could not contact the authentication server to activate your session.

The application will continue to operate but will only display data available locally (in cache).

So what can I do?

---

### Post by dracayr on 2008-10-27
well apparently the program can't connect to the google server. If your Internet connection is working, this means google's server was down.

dracayr

---

### Post by suomalainen on 2008-10-27
Yea I know. But I was looking through info on Googles website and they say there that Google Earth looks into IE's settings and looks those to connect.

I could not find a word on Ubuntu in order to trouble shoot this message.

I also WAS able to connect to google Earth using another machine...

---

### Post by philinux on 2008-10-27
Nothing at all to do with IE. More to do with their servers and you internet connection.

[http://earth.mercinova.com/start.htm](http://earth.mercinova.com/start.htm)

see the troubleshooting section.

Also reboot and try again.

---

### Post by eolson on 2008-10-27
Yep!  What Phillinux said.   Try again and it will probably be o.k.  Works fine here.   At least it did last night.

---

### Post by eolson on 2008-10-27
Just checked it and working fine.   It could also have been the servers at the source the Google uses.   The license the data from somebody else.

---

### Post by suomalainen on 2008-10-27
From:

[http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron](http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron)

Quote!

You must open this link using Internet Explorer browser if you use Windows Operating System.

---

### Post by eolson on 2008-10-27
Are you using Ubuntu or Windows.

I installed it on Ubuntu using Synaptic.

---

### Post by philinux on 2008-10-27
> **suomalainen said:**
> From:
 
 [http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron](http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron)
 
 Quote!
 
 You must open this link using Internet Explorer browser if you use Windows Operating System.
Nah, just used user agent switcher FF addon. I got page load error the first click.

---

### Post by suomalainen on 2008-10-27
I didn't install it from Synaptic cause it wasn't there.

Now I try to un-install it and the commands don't un-install it via terminal.

Is there a terminal command I can use to see/find where exactly google earth is?

---

### Post by eolson on 2008-10-27
It's in synaptic now,  I just checked.  Just type google into the search window.

btw ... I'm just using firfox without useragentswitcher.

---

### Post by eolson on 2008-10-27
Just thought of something else .... Do you have all of your repositories activated?   It's not in the Ubuntu one.

---

### Post by suomalainen on 2008-10-27
Thanks eolson, but from the attached screenshot which one do I want to install?

I'm lost.

---

### Post by eolson on 2008-10-27
Both of them,  but I think if you check the top one it will include the bottom automatically.

---

### Post by suomalainen on 2008-10-27
I don't know? Sorry lost again. What are repositories???

---

### Post by eolson on 2008-10-27
They are where all the software is stored.   I think you have them all selected though because Google earth is showing in your screenshot and I think it's in the medibuntu repo.

---

### Post by suomalainen on 2008-10-27
Eolson, I installed the google files you told me to and then went to Application -->Internet and google earth was not there.

---

### Post by eolson on 2008-10-27
Hmmmm....Should be.   At this point I think I'd do a restart and hope it shows up.  Worth a try.   If that doesn't work, try uninstalling them and then reinstall.

---

### Post by suomalainen on 2008-10-27
I went to:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To install medibuntu if this is repository you mean and got this message:


pa@pa-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for pa:
--16:32:09--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.
pa@pa-desktop:~$ 

What now?

---

### Post by eolson on 2008-10-27
Go to 
   applications > add remove

at the top of the screen is a window titled show:
  click on it and select "all available applications"

that will enable all the repositories.

---

### Post by suomalainen on 2008-10-27
This is already that way.

What now?

---

### Post by eolson on 2008-10-27
Try uninstalling and reinstalling googleearth using synaptic.  It should show up under
   Applications
     Internet.

If it doesn't,  I don't know.

---

### Post by suomalainen on 2008-10-27
But I already have un-installed google earth.

---

### Post by eolson on 2008-10-27
O.K.  Go to Synaptic and try to reinstall it and see if it shows up.

Sorry for the delay, had to step out for a bit.

---

### Post by suomalainen on 2008-10-27
We already did this. That's why I sent you the screenshots. You told me to install them both but they don't install google earth.

---

### Post by eolson on 2008-10-27
O.K.  Go to synaptic and in the upper left corner is the reload button.  click on it and then do a search on Google and see if any more or newer packages show up.  If the do, install them.

---

### Post by suomalainen on 2008-10-27
I already did that too and nothing........

I'm really lost.... now....

---

### Post by eolson on 2008-10-27
Me too!   Hope somebody else has an idea.  If you installed it with synaptic, it should be under the applications > internet.

---

### Post by suomalainen on 2008-10-27
I didn't use synaptic. I used terminal commands. then the problems I noted in the beginning of this post appeared so I un-installed google earth.

---

### Post by eolson on 2008-10-27
Did you re-install it with synaptic?   I seem to remember that you did, but maybe not.

---

### Post by cariboo on 2008-10-27
You guys are going about the whole thing the wrong way, it has nothing to do with installing and uninstalling Google Earth. Reinstalling programs is the Windows way of doing things. You have to totally remove a program in Ubuntu so that means that in Synaptic you right-click on the program then click completely remove, or in a terminal:

```
sudo apt-get --purge googleearth
```

In this case to fix the problem, before all the re-installation, you have to delete ~/.googleearth. This configuration file would have been recreated the next time you started Google Earth, and it would have worked the way it is expected to

To find the file go to Places-->Home Folder then press Ctrl-h to view hidden files and directories.

Jim

---

### Post by suomalainen on 2008-10-27
cariboo907, Thanks for the info. I'm away from the PC but expect to give your advice a try in a hour or two and will report results a.s.a.p.

Maybe you can also answer why I cannot see GoogleEarth in Synaptic Package Manager. I'm just not seeing it there.

Thanks again for the input and Ill advise as soon as possible.

---

### Post by suomalainen on 2008-10-27
I got Google Earth un-installed but cannot find it in Synaptic package manager.

What now?

---

