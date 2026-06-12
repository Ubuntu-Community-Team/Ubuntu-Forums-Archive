---
title: "What do you think about the 5 minute sudo window?"
date: 2009-01-31
forum: Recurring Discussions
---

### Post by stoogiebuncho on 2009-01-31
Hi All,

I'm fairly new to linux, and one thing I've been wondering about for some time is why, when you enter a command with 'sudo', it doesn't just run that command with root access, but basically gives everything root access for five minutes.

I'm sure the problem is simply that I don't understand how this is really working, but if I enter my password to install some updates, and then, a minute or two later, open some system settings that requires root access, it opens right up without asking for the password again.

What's the reasoning for this 5 minute window?  Is it a security risk?

---

### Post by sirebral on 2009-01-31
Let's take a look at the news.

The most recent virus attack on MacOSX was a cracked software that contained a virus.  It infects the computer when the person installs the software (password required).

The most recent virus attack on Win is a small script that modifies the the OS works and displays a deceitful window when a USB is plugged in (Autoplay).  If the person clicks on the wrong icon, the virus installs.

In the two events only one virus attacked the OS before it was fully installed.  The Conficker virus.

Yes.  It is a security measure.

---

### Post by jimmy the saint on 2009-01-31
Often, when you run a command, it sets off a series of actions, all of which require root access, or access to files that require permissions to edit.  If sudo was only valid for one command, then the sudo "window" closed immediatetely, you would have to authorize every file placement, edit and every other action one at a time.  I think it is a matter of practicality more than anything.

---

### Post by emarkd on 2009-01-31
I'm quite comfortable with the default 5 minute timeout.  Hopefully the posts above have made clear the security implications of lengthening or disabling this feature, but if you really want to you can do it.  Google will help you.

---

### Post by stoogiebuncho on 2009-01-31
> **jimmy the saint said:**
> Often, when you run a command, it sets off a series of actions, all of which require root access, or access to files that require permissions to edit.  If sudo was only valid for one command, then the sudo "window" closed immediatetely, you would have to authorize every file placement, edit and every other action one at a time.  I think it is a matter of practicality more than anything.

Ah, that makes sense.  I wasn't that concerned with the security issue myself - I just wondered why it was created that way to begin with.  Thanks for the responses, everyone.

---

### Post by HermanAB on 2009-01-31
In the greater scheme of things, 5 minutes is very short.  Even bacteria can only go through one or two generations in that time.  Also bear in mind that it is only the operator that invoked sudo that gets root access, not everybody.

Cheers,

H.

---

### Post by 3rdalbum on 2009-02-01
Without the timeout, every new convert from Windows would be begging us about how to disable sudo :-)

---

### Post by calrogman on 2009-02-21
> **HermanAB said:**
> In the greater scheme of things, 5 minutes is very short.  Even bacteria can only go through one or two generations in that time.  Also bear in mind that it is only the operator that invoked sudo that gets root access, not everybody.

And that anything you run only gets root privileges if you run it through sudo anyway, you just don't need a password in the 5 minutes, you still need sudo.

---

### Post by jerome1232 on 2009-02-21
> **jimmy the saint said:**
> Often, when you run a command, it sets off a series of actions, all of which require root access, or access to files that require permissions to edit.  If sudo was only valid for one command, then the sudo "window" closed immediatetely, you would have to authorize every file placement, edit and every other action one at a time.  I think it is a matter of practicality more than anything.

Actually no, if you run a command as root everything that command invokes also has root permissions. For example if I call vim then envoke a shell command from within vim, the commands will be run as root, regardless of the timeout.

In the grand scheme of things it's not an issue, and if you don't like it, it's easily changed. (I thought the timeout was 15 minutes by default...)

---

### Post by theozzlives on 2009-02-21
> **3rdalbum said:**
> Without the timeout, every new convert from Windows would be begging us about how to disable sudo :-)

They already are :lolflag:

---

### Post by lukjad on 2009-02-21
> **stoogiebuncho said:**
> What's the reasoning for this 5 minute window?  Is it a security risk?

The main security risk I can see is if someone were to try and install a program or run a command on your computer. They would have to have physical access to your computer and you would have to not be there to stop them.

In this respect, my home computer is fairly secure. The only other person who is in the house with me is my mom, and she couldn't do any harm to my computer if she wanted to. (But someday I hope she will be able to so that I can brag about my "leet" mom. ;) ) So, for home, there really isn't that much of an issue. However, I also have Ubuntu installed at school. There is definitely a risk there, because people with knowledge about computers, and in some cases malicious intent, have physical access to my computer. I just make sure to lock my screen (CTRL+L) every time I leave my PC.

---

