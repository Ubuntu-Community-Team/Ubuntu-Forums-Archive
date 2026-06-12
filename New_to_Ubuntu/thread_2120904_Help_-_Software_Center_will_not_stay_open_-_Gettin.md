---
title: "Help - Software Center will not stay open - Getting warnings"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by Shallowmind on 2013-02-27
**This problem is SOLVED.  I tried to mark it as such, but I am not given the option in "thread tools".**

I'm not sure how to describe all this but here goes:

I tried to get a pdf viewer that would allow me to print.  The one I chose  has a price of $0.00.  So I clicked "buy".  This then went to another screen about setting up an account.  So I thought "heck with it,  I will find something else"  When I closed out of this screen I get an error (?  sorry unknown) and now the Software Center will not open.  It opens to a white screen and immediately goes away.

I'm having similar trouble with the update manager  I will try to post a screen shot:

I attached the screen shot.  I hope you can find it.  

Thanks

---

### Post by Shallowmind on 2013-02-27
OK. So I went into system setting to see if I could figure something out.  And this happened:  See screen shot that is attached:

And I did restart the computer previously.  No change!

---

### Post by schragge on 2013-02-27
Well, the error message says
> Malformed line 59 in source list /etc/apt/sources.list
Please open the terminal (**Ctrl**+**Alt**+**t**), run
```

grep '^[^#]' /etc/apt/sources.list{,.d/*}

``` and post the output here

---

### Post by Shallowmind on 2013-02-27
Thanks for the help.  This is what I got:

shallowmind@shallowmind-MS-7596:~$ grep '^[^#]' /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
/etc/apt/sources.list:deb [http://arcive.canonical.com/](http://arcive.canonical.com/) precise partner
/etc/apt/sources.list:deb-src [http://arcive.canonical.com/](http://arcive.canonical.com/) precise partner
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
grep: /etc/apt/sources.list.d/*: No such file or directory
shallowmind@shallowmind-MS-7596:~$ 


What you see above is exactly what I see in the terminal after I hit enter.

---

### Post by Shallowmind on 2013-02-27
Also for whatever reason I cannot copy and paste the command lines into the terminal.  I have done this before, but it will not do it now.  

It's good for my typing though ;)

---

### Post by Shallowmind on 2013-02-28
Little bump up.  Thanks for the help so far.

---

### Post by Shallowmind on 2013-02-28
Ok.  So I tried to open the Software Center again today and this is what I got:  See attachemnts please.

The second pic is what I got after I pressed "relaunch".

---

### Post by ikt on 2013-02-28
What happens if you do 'sudo apt-get update' and 'sudo apt-get upgrade' in terminal?

---

### Post by schragge on 2013-03-01
```

/etc/apt/sources.list:deb http://archive.canonical.com/ partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ partner
/etc/apt/sources.list:deb http://arcive.canonical.com/ precise partner
/etc/apt/sources.list:deb-src http://arcive.canonical.com/ precise partner

```
If these lines actually are in your */etc/apt/sources.list* as opposite to you having copied them wrong then this is the problem. Remove the first two and add missing [COLOR=red]h[/COLOR] in the 3rd and 4th. You should get
```

deb http://arc[COLOR=red]h[/COLOR]ive.canonical.com/ precise partner
deb-src http://arc[COLOR=red]h[/COLOR]ive.canonical.com/ precise partner

```

To edit the file, press **Alt**+**F2** and enter *gksudo gedit /etc/apt/sources.list*

---

### Post by Shallowmind on 2013-03-01
Thanks.  I will give it a try this evening and get back to you.

---

### Post by audiomick on 2013-03-01
> **schragge said:**
> ```

To edit the file, press **Alt**+**F2** and enter *gedit /etc/apt/sources.list*

Everything in /etc belongs to root, so you will need an instance of gedit with root priviliges. Do the command with gksudo before it.
[CODE]gksudo gedit /etc/apt/sources.list
```

> **Shallowmind said:**
> Also for whatever reason I cannot copy and paste the command lines into the terminal.  I have done this before, but it will not do it now.  

It's good for my typing though ;)

Are you using ctrl+shift+c and ctrl+shift+v ? You should also be able to selct "copy" and "paste" out of the edit menu or with a right click.

Another way that seems to work (I just tried it out here...) from the terminal to somewhere else and at least from this firefox window to the terminal is to highlight (click and run the mouse over) the text to be copied, and, leaving it highlighted, point to where it is to be copied to and click the middle mouse button (on my mouse, that is the wheel).

---

### Post by schragge on 2013-03-01
Thanks, **audiomick**.  Edited my post, too. I've had seen this advice somewhere here in forum, and copied it assuming gedit on Ubuntu somehow will ask you for password if you're trying to access a root owned file. I'm not using Ubuntu myself.

---

### Post by audiomick on 2013-03-01
> **schragge said:**
> ... assuming gedit on Ubuntu somehow will ask you for password if you're trying to access a root owned file. I'm not using Ubuntu myself.

No, I can't think of anything where that works. You always have to specifically invoke sudo (or gksudo for graphical applications) for anything at all where you need root priviliges. At least you do if you are starting things from a terminal.

When you start programs from the icons on the launcher (or out of the menus on older versions), programs like the software centre that need root priviliges will ask for a password automatically.

---

### Post by Shallowmind on 2013-03-01
> **ikt said:**
> What happens if you do 'sudo apt-get update' and 'sudo apt-get upgrade' in terminal?

I tried both commands.  Check the attachment to see what happened.

I said "Y" to the prompt.  It downloaded a bunch of things and then gave me the same warnings and problems.

---

### Post by Shallowmind on 2013-03-01
> **schragge said:**
> ```

/etc/apt/sources.list:deb http://archive.canonical.com/ partner
/etc/apt/sources.list:deb-src http://archive.canonical.com/ partner
/etc/apt/sources.list:deb http://arcive.canonical.com/ precise partner
/etc/apt/sources.list:deb-src http://arcive.canonical.com/ precise partner

```
If these lines actually are in your */etc/apt/sources.list* as opposite to you having copied them wrong then this is the problem. Remove the first two and add missing [COLOR=red]h[/COLOR] in the 3rd and 4th. You should get
```

deb http://arc[COLOR=red]h[/COLOR]ive.canonical.com/ precise partner
deb-src http://arc[COLOR=red]h[/COLOR]ive.canonical.com/ precise partner

```

To edit the file, press **Alt**+**F2** and enter *gksudo gedit /etc/apt/sources.list*

OK I pressed Alt+F2 and a screen in the "dash" came up.  I entered the command you have listed above.  The first time I did this I got the list you indicate.  But I could not change anything.  It would not let me delete or type in the listed items at all.  
I inadverdently lost that list and now I cannot get it at all!  

Thanks again

---

### Post by Shallowmind on 2013-03-02
Bump

---

### Post by Shallowmind on 2013-03-02
Thanks for all your help.  I kept doing the things mentioned here and it worked.  I really appreciate it.

Matt

---

