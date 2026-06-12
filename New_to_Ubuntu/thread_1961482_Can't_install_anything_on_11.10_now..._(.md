---
title: "Can't install anything on 11.10 now... :("
date: 2012-04-19
forum: New to Ubuntu
---

### Post by mdubs on 2012-04-19
So I was able to download wine last night but the SW center said that it was already installed after downloading... I don't know if that matters but that's where everything started.

Now, whenever I try to install something from the SW center, I get the following error:

[IMG]https://picasaweb.google.com/lh/photo/5JCJRyJYSWQQWVIWJ2NxFdMTjNZETYmyPJy0liipFm0?feat=directlink[/IMG]

If you can't see the picture, here's the link:
[https://picasaweb.google.com/lh/photo/5JCJRyJYSWQQWVIWJ2NxFdMTjNZETYmyPJy0liipFm0?feat=directlink]("https://picasaweb.google.com/lh/photo/5JCJRyJYSWQQWVIWJ2NxFdMTjNZETYmyPJy0liipFm0?feat=directlink")

The text in the "Details" box is:

```
Traceback (most recent call last): 
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 972, in simulate 
    trans.unauthenticated = self._simulate_helper(trans) 
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1096, in _simulate_helper 
    return depends, self._cache.required_download, \ 
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download 
    pm.get_archives(fetcher, self._list, self._records) 
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. 
```

I have no idea how to fix this. Any help is greatly appreciated.

---

### Post by Torgas Prim on 2012-04-19
I had the same problem. Someone on these forums pointed me to a command that fixes apt. Can't remember when or who. Sorry.
Maybe search for "apt fix" or something like that on google

---

### Post by josephmills on 2012-04-19
try
```
sudo apt-get -f install 
```
then try to install something

you might also need  ttf-mscorefonts-installer from what the error is saying but try sudo apt-get -f install 
might install it

---

### Post by mdubs on 2012-04-19
> **josephmills said:**
> try
```
sudo apt-get -f install 
```
then try to install something

you might also need  ttf-mscorefonts-installer from what the error is saying but try sudo apt-get -f install 
might install it

Ding ding ding! We have a winner! That fixed it.

Now... would you please be so kind as to tell me what that did and why it fixed my problem? I don't want to just fumble through the forums every time I have an issue. I'd like to learn this stuff as well.

Thanks for your help.

---

### Post by josephmills on 2012-04-19
> **mdubs said:**
> Ding ding ding! We have a winner! That fixed it.

Now... would you please be so kind as to tell me what that did and why it fixed my problem? I don't want to just fumble through the forums every time I have an issue. I'd like to learn this stuff as well.

Thanks for your help.

Sure what the -f does 


 -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.




hope that this helps could you make as solved 

basic you had dependency troubles and needed to fix them 

glad you got it going

---

### Post by audiomick on 2012-04-19
You might also like to know what "apt-get" does... ;)

[https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto")

It is more or less what is behind the GUI of the software centre and several othere similar graphical package management tools.

More here
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")

For the options, try looking at the man page. There is a man page for pretty much any command, so this is a good thing to know for future use. If you see a command that you want to find out about, go to a terminal and do
```
man command_name
```

In this case
```
man apt-get
```

What you get on a man page is often very concise and a little cryptic, but perservere with it. You can at least see what the command does, and usually figure out what the options do.

---

### Post by Torgas Prim on 2012-04-19
Thank you from me also. Nice info for future use :-)

---

