---
title: "man: equivalent in ubuntu"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Offramp on 2008-09-15
Hi all,

I have been experimenting with kde variants of linux for about six months and have just switched to ubuntu (and ditched windows in the process!). In Konqueror I could type man: ls to view the ls man page - is there an equivalent functionality in ubuntu.

Cheers

---

### Post by halitech on 2008-09-15
just open a terminal and use the same command

---

### Post by JillSwift on 2008-09-15
Sure:

In Konqueror, type```
man:/ls
```

---

### Post by crazypenguin2008 on 2008-09-15
when i type man in ubuntu terminal it asks what manual page do you want

---

### Post by JillSwift on 2008-09-15
> **crazypenguin2008 said:**
> when i type man in ubuntu terminal it asks what manual page do you want
Yesh, you have to include the name of the command/executable, like:```
man ls
```

---

### Post by crazypenguin2008 on 2008-09-15
ahh i see...i knwo my way around terminal pretty well but after 5 years im still learning stuff...thanks!!

---

### Post by Offramp on 2008-09-15
Hi,

Thanks for the response.  I have been using the terminal for viewing, but became comfortable with the nicely formatted, version in Konqueror :)

I was hoping for a similar functionality in ubuntu (gnome desktop),

Cheer

---

### Post by niteshifter on 2008-09-15
Hi,

Is there the direct equivalent in Ubuntu (GNOME) default browser Firefox?
Sort of. When I enter:
```
man ls
```
into FF I'm taken to a web site ([http://unixhelp.ed.ac.uk/CGI/man-cgi?ls](http://unixhelp.ed.ac.uk/CGI/man-cgi?ls)) that gives me the stock man page. So, yes it does, if there's access to the internet at the moment. Konquerer doesn't need net access, it's pulling up from the local filesystem.

You can, as others pointed out use the terminal.

You can use Ubuntu's Help (handily located on the top panel) and type "man <command>" into the search box and go direct to the man page for <command>.

It should be noted that what we're discussing is a browser feature, not a property of the desktop environment. One can install Konquerer in GNOME.

But that would make a nifty addon for FF, I think.

---

### Post by Offramp on 2008-09-15
Thanks for the response (I have been using FF to do this as well). Ubuntus help worked well, and will do the trick.  I suppose what I am after is a gui to view man/info pages.  Ubuntu Help did not work so well for info pages (eg. info cpio).  The first page displayed correctly, but when I tried to navigate the page it simply shut down.

Cheer

---

### Post by JillSwift on 2008-09-15
> **Offramp said:**
> Thanks for the response (I have been using FF to do this as well). Ubuntus help worked well, and will do the trick.  I suppose what I am after is a gui to view man/info pages.  Ubuntu Help did not work so well for info pages (eg. info cpio).  The first page displayed correctly, but when I tried to navigate the page it simply shut down.

Cheerman: and info: are working fine for me in Konqueror.

Maybe it's the superfluous space?

---

### Post by mcduck on 2008-09-16
> **Offramp said:**
> Hi,

Thanks for the response.  I have been using the terminal for viewing, but became comfortable with the nicely formatted, version in Konqueror :)

I was hoping for a similar functionality in ubuntu (gnome desktop),

Cheer

Then use Yelp (Gnome's Help viewer). It can access manual and info pages as well. Just type press F1 to open Yelp and type man:yelp into the search field.

You can't do that in Nautilus since, unlike Konqueror, Nautilus is "just a file manager" and doesn't come with document viewer, web browser and kitchen sink. ;)

---

### Post by Trail on 2008-09-16
The "man:", "info:", "fish:", etc are named KIO slaves and are part of the KDE technology, so they don't `automagically' work on GNOME.

---

### Post by billgoldberg on 2008-09-16
> **crazypenguin2008 said:**
> ahh i see...i knwo my way around terminal pretty well but after 5 years im still learning stuff...thanks!!

You have been using the terminal for 5 years, but don't even know how to access a man page?

Something doesn't sound right.

---

### Post by Vivaldi Gloria on 2008-09-16
```
man man
```

---

### Post by Offramp on 2008-09-16
Thanks mcduck,

I had tried yelp previously, however it crashes when trying to navigate an info page (info:cpio -> use keyboard [also tried mouse] to select section and yelp closes).  I have since installed man2html to view local man pages through browser and am researching info2html as well. It is not really a big issue, I have just become used to reading this much info through a browser rather than a terminal

Cheers

---

### Post by Mornedhel on 2008-09-16
> **billgoldberg said:**
> You have been using the terminal for 5 years, but don't even know how to access a man page?

Something doesn't sound right.

This had me wondering as well. 5 years of navigating the terminal and not once did he come across man ? Just weird.

[quote=Offramp]I have just become used to reading this much info through a browser rather than a terminal[/quote]

The day you hose your xorg and have to do everything from tty1, you'll see why this can be a bad thing. Or even the day you open a shell on a remote Linux box through ssh. (And they wonder why I use emacs.)

---

### Post by malspa on 2008-09-16
How about simply installing Konqueror in Ubuntu and accessing the man pages the same way you're used to?

---

### Post by aos101 on 2008-09-16
Another option is the new [Ubuntu Manpage Repository](http://manpages.ubuntu.com/) which has all the man pages online.

---

