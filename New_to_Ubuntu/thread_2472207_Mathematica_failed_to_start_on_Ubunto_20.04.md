---
title: "Mathematica failed to start on Ubunto 20.04"
date: 2022-02-20
forum: New to Ubuntu
---

### Post by sdantonio on 2022-02-20
I installed Mathematical 11.3 on Ubuntu 20.04. The icon appears in the "show applications" window. But when I click on the icon the hard drive spins a little bit then stops. I have no messages on the screen indicating a failure of any kind.  All other icons tested work fine and start their respective software.  I had no indications of any problems in the terminal window while installing

---

### Post by yetimon_64 on 2022-02-20
> **sdantonio said:**
> ...  I had no indications of any problems in the terminal window while installing

Try _launching_ it from the terminal, this may show some indication of why it is failing at launch.

Any application that fails without apparent reason should be tried from the terminal, this is a normal technique in Ubuntu/Linux for application launch issues. The terminal tends to show up any errors that occur, whereas the GUI often shows nothing at all.

---

### Post by sdantonio on 2022-02-21
Hi Yeti, Thanks for getting back to me.  This is what I have trying to start it from the terminal window

```
steven@steven-HP-Compaq-dx7400-Small-Form-Factor:~$ mathematica
/usr/local/Wolfram/Mathematica/11.3/SystemFiles/FrontEnd/Binaries/Linux-x86-64/Mathematica: symbol lookup error: /lib/x86_64-linux-gnu/libfontconfig.so.1: undefined symbol: FT_Done_MM_Var
steven@steven-HP-Compaq-dx7400-Small-Form-Factor:~$
```

When I look at permissions for this binary the owner is root.  I'm not sure if this is normal or not, but to get t he install to work I did have to  log in as root.  Otherwise it wouldn't install.

---

### Post by tea for one on 2022-02-21
mathematica 11 does not seem to be in the Ubuntu repositories?
Is there not a similar package in the repos that you can use?

Otherwise, are these links any use?
[https://community.wolfram.com/groups/-/m/t/1671470](https://community.wolfram.com/groups/-/m/t/1671470)
[https://wiki.archlinux.org/title/Mathematica#Troubleshooting](https://wiki.archlinux.org/title/Mathematica#Troubleshooting)
[https://askubuntu.com/questions/tagged/mathematica](https://askubuntu.com/questions/tagged/mathematica)

I do not have this application installed, only trying to offer some help.

---

### Post by sdantonio on 2022-02-21
I'll have to check into the links, thanks.  

Mathematica is kind of specialized for the physics and math communities, the  only other thing I know of that is even remotely comparable is Matlab and I don't even know if that's available for Linux.  And Mathematica even stands head and shoulders above Matlab

---

### Post by yetimon_64 on 2022-02-21
> **sdantonio said:**
> Hi Yeti, Thanks for getting back to me.  This is what I have trying to start it from the terminal window...

Have a look at the solutions in [[COLOR=#0000ff]--this link--[/COLOR]]("https://askubuntu.com/questions/1140921/wolfram-mathematica-after-upgrade-to-ubuntu-19-04-symbol-lookup-error-usr-lib") (link in blue text), it has the same error you posted noted, though it is a couple of years old.

I assume you are using a snap version of mathematica as like "tea for one" I couldn't find a version in the standard repositories. Is this correct ?

Good luck, yeti.

---

### Post by Topsiho on 2022-02-28
Mathematica and Matlab are both very expensive proprietary math packages, which I guess you are not going to find in the repositories.
In stead of Matlab you can use GNU Octave, which is (meant to be) a perfect clone of Matlab, just as Linux is of Unix. Octave is open source software.
How good Mathematica and Matlab/Octave are i don't know. Perhaps the most expensive is the best?

There are more possibilities: some people claim that the combination of Python3 and Numpy and Scilab is second to none.

Then you can look into Cantor and Sage.

As a (very oldfashioned) one time math teacher, I can only say that these packages are less useful than a good text on mathematics. Learning how to use a math package is a very time-consuming and hard work, only useful as long as you use that specific package, where learning the math itself is for your lifetime, and next generations that you educate.

But a good math package, that you use to get things done as a professional, or as a student to experiment, can of course be very useful, **only** if you understand the mathematical background of what you use it for.

Greetz, Topsiho

---

