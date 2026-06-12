---
title: "Help with my post install script"
date: 2014-01-31
forum: Programming Talk
---

### Post by absurdcakes on 2014-01-31
Hey guys, have been using Ubuntu for a decade but have just gotten into programming.

I'm writing this little script for bash which customizes my new ubuntu install.  Right now, it just installs and removes programs. So I'm modifying it right now. I want to be able to eventually include into this script (or make a new one), modifications to the GUI and keyboard bindings. I use XFCE btw, if anyone can help me with that, it'd be great.

Anyway, _**my main issue right now**_ is this. I run lines 

sudo apt-get install exaile
sudo apt-get remove firefox

But when I do this, the terminal asks me "Press Y to install", I want the script to be so automated, so I can just run it and leave the desktop without having to press y. How do I do that?

---

### Post by steeldriver on 2014-01-31
Hello and welcome to the forums

Have a look at the manual page for the apt-get command - in particular this command line option

```

       -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and
           run non-interactively. If an undesirable situation, such as
           changing a held package, trying to install a unauthenticated
           package or removing an essential package occurs then apt-get will
           abort. Configuration Item: APT::Get::Assume-Yes.

```

---

### Post by absurdcakes on 2014-01-31
What's the difference between -y -yes -assume-yes ?

So my script would have to be sudo apt-get install -y firefox   (For example)?

Or would it be:

sudo apt-get -y install firefox  ?


**Nevermind, I figured it out.

---

