---
title: "Firefox: Limit Download Speeds"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by jason6g on 2008-08-24
ok! so I solved my issue, and after searching around, I've decided to make a how to :D

install trickle:

```
sudo apt-get install trickle
```

once you have that installed, all you need is a download link.

I use download helper extension in firefox to download tv show episodes, so I get the download link that way.

to download this picture:

[IMG]http://www.google.com/intl/en_ALL/images/logo.gif[/IMG]

you would use this code:

```
sudo trickle -d 60 wget http://www.google.com/intl/en_ALL/images/logo.gif
```

explanation of code:

sudo - give rights

trickle - call trickle

-d 60 - this is where you limit the download speed. -d 10 limits it to 10k and -d 100 limits it to 100k

since I have verizon dsl, my max dl speed is usually 90k so I limit it to 60k - leaving 30k for general web browsing.

you may also use -u 100 to limit upload speeds, or both to limit them both:

```
sudo trickle -d 60 -u 10 wget http://www.google.com/intl/en_ALL/images/logo.gif
```

wget - wget will look familiar once you use the command, its what you see when you install stuff via the terminal.

[http://ww](http://ww).... - this is the download url. if you are downloading say "ubuntu8.04.iso from ubuntu.org, you would use this:

```
sudo trickle -d 60 wget http://www.ubuntu.org/ubuntu8.04.iso
```

should be pretty easy to use.

i have yet to come across a pretty graphical way of doing this, but I dont mind.

as I find stuff out, I will post more here :D



------------------

original issue:

Scenario:

I am downloading several large files that will take a few hours.

I would like to limit those files to say 60% of my connection (so if my max download speed is 100k - I want to limit it to 60k for those files)

I wish to do this so I may still browse other pages without waiting longer than usual for them to load.

I know transmission has this option that works very nice, you simply type in the max speed you wish, and it limits it. Wondering if anyone knows of something that will easily do this (hopefully avoiding several command lines like trickle).

Thank you in advance!

---

### Post by theRightNee on 2008-08-24
i believe you just need to get a firefox plug-in that would act as a download manager and then would be able to control the download speed

---

### Post by jason6g on 2008-08-24
have any specific links? I've searched for an extension, but everything seems to be for windows :/

---

### Post by jason6g on 2008-08-24
bump :/

---

### Post by sstusick on 2008-08-24
I'd rather have the files download as fast as possible and then continue on with your work when they're finished. 

But to each his own..

---

### Post by zamadatix on 2008-08-24
if oyu go to the addon site for firefox 9oyu can just google firefox addons) you should be able ot find a download manager no problem. though i think firefox will set asid a percentage for the webpage and it wont load that much slower (of course im running 12mbps here with buckeye cable)

---

