---
title: "emacs slow startup"
date: 2006-05-28
forum: Programming Talk
---

### Post by rplantz on 2006-05-28
I used Options->Customize Emacs to create a ~/.emacs file that provides me a larger font size. When emacs starts, it takes 6 - 7 seconds to resize the window then fill it with the larger text. I'm running this on an amd64 athlon 3200. The same thing in gedit is instantaneous.

---

### Post by kunnk on 2006-05-29
I have exactly same problem btw. My main programming language is java but i tried to learn a little more lisp (just for fun, not for real coding of course). Installed emacs and slime. Because default emacs is ugly i tried some customizations like changing font and colors, after that emacs startup is terribly slow.

---

### Post by Zippo1000 on 2006-05-29
Exactly the same problem here.
I used Emacs on Dapper Drake for a few months. I always made the updates and then suddenly the emacs startup became very slow. I think it has something to do with Gnome, because with other window managers like IceWM, Fluxbox or LarsWM there's no problem.
I also recognized that the startup is very slow when you have customized emacs, like font size, window size, ...

Perhabs someone has a solution to the problem! I think it has something to do with Gnome as I wrote above, but I'm not sure, and especially no expert in this.

Please help,
Zippo

---

### Post by harfooz on 2006-06-04
Try this line in your .emacs file:
```

(modify-frame-parameters nil '((wait-for-wm . nil)))
```

There is some request to the window manager that is not sending a response back to emacs. This line fixed the problem for me. 

Hope this helps,
Clint

---

### Post by Burke on 2006-06-05
Awesome! I've been wondering about that! Thanks very much.

---

### Post by bites on 2006-06-05
eey.. thanks Harfooz!  It's been a while since I used emacs, but I had this problem as well :)

---

### Post by rplantz on 2006-06-05
[QUOTE=harfooz]Try this line in your .emacs file:
```

(modify-frame-parameters nil '((wait-for-wm . nil)))
```[/QUOTE]

Thank you! BTW, placing the line at the end of my .emacs file did not work; I had to place it at the beginning.

---

### Post by toojays on 2006-06-06
By the way, this is [bug 23005](https://launchpad.net/distros/ubuntu/+source/emacs21/+bug/23005/+index).

---

### Post by lukew on 2007-01-04
> **harfooz said:**
> Try this line in your .emacs file:
```

(modify-frame-parameters nil '((wait-for-wm . nil)))
```

There is some request to the window manager that is not sending a response back to emacs. This line fixed the problem for me. 

Hope this helps,
Clint

Great Stuff! Thank You!!

If you have lots of emacs customisation you can byte compile the el files into elc files to make you custom code run quicker!

Luke

```


(defun lw:byte-compile-directory(directory)
  "Byte compile every .el file into a .elc file in the given directory.  See
`byte-recompile-directory'."
  (interactive
   (list
    (read-file-name "Lisp directory: ")))

  (byte-recompile-directory directory 0 t))
```

---

### Post by robbiemorrison on 2007-02-12
Hi all

My experience is somewhat similar to that discussed earlier:

  - 1 second to load Emacs when connected to university
    ethernet

  - 6 seconds to load Emacs without ethernet

  - 1 second to load Emacs whenever some unknown and
    evidently insecure WLAN in my apartment block was
    detected

  - Gnome also equally slow to start, particularly the
    first icon on the splashscreen (whatever that is)

  - emacs -q and/or -nw make no difference to speed

  - adding the following line to ~/.emacs did nothing
    (modify-frame-parameters nil '((wait-for-wm . nil)))

  - instantaneous response : $ hostname
    takes several seconds  : $ hostname --short

My fix was to modify /etc/hosts as follows:

    127.0.1.1  sojus  # was 'robbie-laptop'

My domain name is sojus.****.tu-berlin.de.  The phrase
'robbie-laptop' arose from the Live Ubuntu DVD install
process.  At one point I naively entered:

    computer name = robbie-laptop

Later during the install /etc/hostname was modified to
achieve ethernet connectivity (but /etc/hosts remained
unexamined and untouched):

    sojus  # was 'robbie-laptop

It is my belief that the request for a computer name
during installation should be more explicit and state
that the domainname is sought and not some cute
identifier.

My system details for the record:

  - hardware      : Toshiba Tecra A2 330 laptop
    part no       : PTA20A - 028002
    purchase      : 27-Aug-2004
    some specs    :

  Celeron mobile 1.4 GHz / 512 MB RAM (originally 256 MB)
  10/100 ethernet (Intel 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83))
  802.11b/g WLAN (Intel PRO/Wireless 2200BG Network Connection (rev 05))

  - distro        : Ubuntu 6.10
  - kernel        : 2.6.17-10-generic

  - emacs version : 21.4.1
    package       : emacs 21-0ubuntu2
    fonts         : default fonts used, no .Xdefaults or elisp modifications

Hope this helps.  Many thanks, as always, to the Linux
community.

Robbie Morrison

---

### Post by robbiemorrison on 2007-02-27
Hi all -- more info on my earlier post.

> My fix was to modify /etc/hosts as follows:
>
> 127.0.1.1 sojus # was 'robbie-laptop'

This is not correct, for background see man (5) hosts

The modified line should read:

```
127.0.1.1 sojus.domain.name sojus # was 'robbie-laptop'
```

Confirm changes with:

```
$ hostname
$ hostname --short
$ hostname --long
```

My earlier comment about the install process for Ubuntu 6.10 stands. I believe the request for a computer name could be better described and should not provide a default based on one's login name.

cheers -- Robbie Morrison

---

