---
title: "Trying to install Skype!"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-07
Hi, 

I'm trying to download Skype, and when I try to open & install the package installer, I get a message that says "Wrong architecture i386" :confused:

I have version 8.1 of ubuntu...

Can anyone help me out with what that means and how to fix it?

I am no computer genius, so don't be afraid to dumb it down for me!! 

Thanks a lot!

---

### Post by PmDematagoda on 2008-06-07
Post the output of:-
```
uname -a
```

---

### Post by rampageoberon on 2008-06-07
Hmm, isn't skype available from the repository?

```
sudo aptitude search skype
```

if it finds it then install it using

```
sudo aptitude install skype
```

And are you using a 64bit machine?

---

### Post by OKnotOK on 2008-06-07
I am using a 64 bit computer, yes.

Should I able to go to 'add/remove' and get it? I typed in skype but didn't get a program. 

I'm not sure what I should be doing with that code....

---

### Post by hexanol on 2008-06-07
Well, the only thing I can say is that if you go on skype website, you can download a deb package on it.

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by socngill on 2008-06-07
Having same problem with Kubuntu 8.04.  Tried to sudo aptitude install Skype and Gsopcast but it fails to find either.

Tried downloading the tar.gz files for Sopcast but have been unable to install it.  It's on my desktop and I have no idea how to make the Terminal look in the right place :(

---

### Post by OKnotOK on 2008-06-07
> **hexanol said:**
> Well, the only thing I can say is that if you go on skype website, you can download a deb package on it.

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

That's exactly what I did. As I explained above, I got an error message when I tried to install it.

---

### Post by whitethorn on 2008-06-07
Hi,

It seems that the problem is that ur trying to install it on a 64 bit system. This webpage explains how to install skype on a 64 bit system

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

i386 = 32 bit systems

Oh and since you are using 8.04 then you just need to copy the top line on the webpage into a terminal.

---

### Post by OKnotOK on 2008-06-07
> **whitethorn said:**
> Hi,

It seems that the problem is that ur trying to install it on a 64 bit system. This webpage explains how to install skype on a 64 bit system

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

i386 = 32 bit systems

Oh and since you are using 8.04 then you just need to copy the top line on the webpage into a terminal.

Okay... I'll see what I can find out from that thread. 

Thanks a lot! :)

---

### Post by rampageoberon on 2008-06-07
> **OKnotOK said:**
> I am using a 64 bit computer, yes.

Should I able to go to 'add/remove' and get it? I typed in skype but didn't get a program. 

I'm not sure what I should be doing with that code....


Type that code in a "terminal" (by default a bash shell). 

```
Applications -> Accessories -> Terminal
```

And it looks like you were downloading the wrong installation package. You were trying to get x86 packages, you need packages for a 64 bit system

---

### Post by OKnotOK on 2008-06-07
> **whitethorn said:**
> Hi,

It seems that the problem is that ur trying to install it on a 64 bit system. This webpage explains how to install skype on a 64 bit system

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

i386 = 32 bit systems

Oh and since you are using 8.04 then you just need to copy the top line on the webpage into a terminal.

Thank you very much! This seems to be working now! 

I still have to register and actually try it... But so far so good!

Yay for Ubuntu!!!

---

