---
title: "HOWTO: Integrate yubnub with the command line."
date: 2007-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Taintedhero on 2007-11-30
Just a little guide I wrote because I think some people would find this to be useful. 

Using a combination of Surfraw, Yubnub, Firefox, and Yakuake.
(You can use tilda or really any terminal to do this with, I just had problems with tilda and yakuake seems a bit more stable)

First, lets get the needed files...
```

sudo apt-get install surfraw yakuake

```

Now. we need to configure our .bashrc
```

*Your Text Editor Here* ~/.bashrc

```

scroll all the way down and add. 
```
alias yb='sr yubnub'
```

Now, start Yakuake and press f12 to have your terminal drop down. Then type
```
yb g google.com
```

If firefox is open, this command will start a new tab and search google.com for google.com

There you go. up and running, just type yb "parameters here" from now on to use the power of yub nub to search the web very powerfully, very quickly.

For those not familiar with yub nub, it is a very powerful, pseudo-command line for the web.  For a bit of help using it. type 
```
yb ls
```
 to get a list of commands.

Good luck.

Note, you can use any webbrowser.  You just have to tinker with surfraw a little bit.

---

