---
title: "gedit, emacs or vi what should I be editing stuff with"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by SNIFFER_dog on 2011-10-23
Hi,

I've been fiddling with Ubuntu for a few weeks now and it's obvious that understanding the command line is essential. I have therefore purchased some books on bash and am slowly making my way through them and have picked up a lot of stuff.

The editing I've been doing while following the texts has been with gedit, but the books are starting to talk about using emacs or vi to edit the command line.

I realize they are both full of key sequences to do stuff, and so will take some dedicated effort to learn, while gedit seems pretty straight forward to use.

I'm a little confused over what program I should be using to edit scripts with and should I take the time to learn emacs or vi if I'm planning to do a little scripting in bash or even c++ etc.

I'm an absolute beginner and am looking for advice on what I should be using, so any tips would be appreciated.

SNIFFY

---

### Post by celticbhoy on 2011-10-23
Its really down to personal choice, but if you are planning to learn about Ubuntu rather than just using it, I would recommend that you do take a little time out to learn one non GUI text editor. You never know when it will come in handy if something breaks. I tend to just stick to Nano, but as I say its all about choice.

---

### Post by muteXe on 2011-10-23
nothing wrong with gedit, but it is good to be familiar with either vi(m) or emacs (or nano) for the times you might lose your front end and you wanna edit config files.

edit: beaten again :)

---

### Post by cgroza on 2011-10-23
You should take a look at "sed" too if your are planning on getting serious with shell programming.

---

### Post by SNIFFER_dog on 2011-10-23
Thanks for the advice, I've installed emacs and I think vim is also there too. emacs seems to come up as a gui not in the command line, so I'm doing something wrong there???

So far I've been editing the prompt in bash simply to get an idea of the that first. I understand that the prompt should be used and not made fancy but it's a starting place for me.

So far the different types of quotes ' ' or " " do indeed seem to cause different results and I'm still trying to understand the subtleties of them.

I will look into them and try and get a feel, as I understand if I break X then I might need to edit this way

Regards


SNIFFY

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
I agree with the others.  I like gedit a lot (leafpad, geany, etc...)  but they are GUI tools as the others have pointed out.  I agree that a familiarity with the command line tools is essential.  I messed up my desktop environment by tweaking with compiz too much, and needed to use vi to edit my session config file.  also learning the command line commands (like ls, rm, mv, etc....) are also very useful.  the "man" command is very useful for learning as well (ex. man vi) or using "--help" (ex. ls --help)
knowing your way around the file system is pretty essential, too.

---

### Post by krapp on 2011-10-23
I use nano and gedit to edit or look at the occasional configuration file, but anything that takes longer than a few minutes is worked on in Emacs!

---

### Post by E411 on 2011-10-23
Hi there,

Some time ago, I was a huge emacs fan. Hey it's not an editor, it's an operating system on its own! But then I started to use vi quite intensively a few months ago and now I'm totally convinced: it undoubtedly rocks.

---

### Post by conradin on 2011-10-23
Traditionaly, vi is on nearly every Unix linux computer out there, so if youre a technichian, you'll probably encounter / be forced to use vi at some point. If youre not in that situation, then I really like cream or gedit, which both work fine for daily use.

---

### Post by enkay009 on 2011-10-23
> **SNIFFER_dog said:**
> Thanks for the advice, I've installed emacs and I think vim is also there too. emacs seems to come up as a gui not in the command line, so I'm doing something wrong there???

You have to install emacs without X11 support. It's the emacs23-nox package.

---

### Post by dniMretsaM on 2011-10-23
I like Emacs personally, but its really up to you.
> **enkay009 said:**
> You have to install emacs without X11 support. It's the emacs23-nox package.

Or he could launch it with the [FONT=Courier New]emacs -nw[FONT=Verdana] command.[/FONT][/FONT]

---

### Post by SNIFFER_dog on 2011-10-24
Thanks for all your comments,

I will look into learning an alternative way to edit files through a none GUI enviroment.

I can confirm the ```
emacs -nw [filename]
``` command works with my setup, thanks again, now the long road to understaning this alternative method begins.

Regards


SNIFFY

---

