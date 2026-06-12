---
title: "cmdWhistle"
date: 2007-06-29
forum: Programming Talk
---

### Post by Shriike on 2007-06-29
I'm sorry if this is the wrong forum, didn't know where else to post this.
[http://www-128.ibm.com/developerworks/library/os-whistle/index.html?ca=dgr-lnxw97whistlework#download](http://www-128.ibm.com/developerworks/library/os-whistle/index.html?ca=dgr-lnxw97whistlework#download)
saw that article while cruising the web, I was intrigued, there are many things I'd like to be able to do with a simple whistle, preferably from some distance from my laptop
I got sndpeek installed ok (after much trouble) but now when I try to run "sndpeek --print --nodisplay  | perl cmdWhistl.pl -c" I get the error messages "[sndpeek]: warning: using different buffer sizes: 512 : 1024" and "seconds: Invalid argument at cmdWhistle.pl line 53."
if anyone thinks they could help me I'd appreciate it.

---

### Post by eexpress on 2007-08-08
[http://www.emacswiki.org/cgi-bin/alex/cmdWhistle.pl_patch](http://www.emacswiki.org/cgi-bin/alex/cmdWhistle.pl_patch)
here is some patch. 

i had modified the prel. and can excute. 

```
&#9742;  sndpeek --print | perl cmdWhistle.pl -c
enter a tone sequence:

```

2 whistles per 0.5s, but no data output after 4 seconds delay. seems data maybe those? :
```
25.00 25.00 _#_ 0 500000 _#_ <command here> _#_ <comment here>
```

[http://www.youtube.com/watch?v=x9jHReFtYgE](http://www.youtube.com/watch?v=x9jHReFtYgE)
here is some success video at OSX system.

sndpeek is already 1.3b version. works well.

---

### Post by RBerenguel on 2010-05-02
I also had problems with this, and documented the solution and usage in my blog: [Whistle control your computer (Linux & Mac OS)]("http://www.mostlymaths.net/2009/09/whistle-control-your-computer.html").

The solution basically boils down to two things:

[LIST=1]
[*]Add use Time::HiRes; as dependency in cmdWhistle.pl
[*]Replace time management subroutines getEpochMicroSeconds and getEpochSeconds as in
[/LIST]
```
sub getEpochSeconds {
   my ($seconds,  $microseconds) = Time::HiRes::gettimeofday;
   return($seconds);
}
```And similarly for the microseconds. With this, it works flawlessly in Mac OS, but has some mic problem in my Acer Aspire One (lower quality mic). In my post I also explained (albeit not very detailed) how to adjust several parameters to get more accuracy.

Ruben

---

