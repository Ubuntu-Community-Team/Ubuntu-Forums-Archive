---
title: "Ubuntu 12.04LTS has experienced an internal error"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by wolfie52 on 2012-12-30
I have Ubuntu 12.04LTS installed on my Dell netbook

I have been using ubuntu with no real problems for around 3 years. Recently a good friend updated my system to the version listed above.

I continue to get greying of screen and often such slow internet.

Now I get the following error message and I am completely stumped.

The following error after booting and I'd like to know how to fix it or  at least stop it from happening.  

ExecutablePath/usr/share/apport-gpu-error-intel.py

Sorry, Ubuntu 12.04 has experienced an internal error.
If you notice further problems, try restarting the computer.

The available options at this point are:
Send an error report to help fix this problem
Ignore future problems of this type

I have found one thread which is close to my problem but not identical. I have the most basic ability and would really appreciate any thoughts and views re the above.

Another windows appears as well that is labeled Apport at the top.  It  says, 'precise' is no longer under development, but technical support is  still available and will give you quicker results than filing a bug  here.  Also, if  you have a bug, we will give it higher priority if  you've gone through technical support channels first.  My choices at  this point are:

I don't know what to do.
Continue.  I already know of a patch to fix this problem.
Continue.  Yes, I have discussed this with technical support.
Continue.  I don't need technical support.
Please point me to where I can get technical support.

I do not know if this is related to the issue discussed above, but I'd  like to stop this from appearing also.  This issue continues to  persists, despite choosing any of the available options.

Thank you for any help!

Geoff

---

### Post by ibjsb4 on 2012-12-30
Sounds like this

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1020140](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1020140)

Fix here

[http://ubuntuforums.org/showthread.php?p=12426839](http://ubuntuforums.org/showthread.php?p=12426839)

And you may find gedit easier to use than nano.

```
sudo gedit /etc/default/apport
```

---

### Post by wolfie52 on 2012-12-30
Yes, thank you. I did read the link you referred me too, but concerned that the problem is not exactly the same. OK, that’s great you have directed me so I need to try this fix.

To get from the information you have sent, to inputting, how do I get to that position.

I am really sorry for being such a nerd

Geoff

---

### Post by ibjsb4 on 2012-12-30
> **wolfie52 said:**
> Yes, thank you. I did read the link you referred me too, but concerned that the problem is not exactly the same. OK, that&#8217;s great you have directed me so I need to try this fix.

To get from the information you have sent, to inputting, how do I get to that position.

I am really sorry for being such a nerd

Geoff

Not a problem Geoff

After you enter the above command in post#2 you will see this:

[ATTACH]229346[/ATTACH]

Simply change that "enabled=1" to "enabled=0"

Any other questions?  Just post  :)

---

### Post by wolfie52 on 2012-12-31
Thanks I really appreciate your help.

Now I need to find how and where I put that text to resolve my query!

Yes, I did say I was an idiot, but I really want to learn. 

Little by little I will.

many thanks for taking the time to help me, its very much appreciated.


Geoff

---

### Post by Wim Sturkenboom on 2012-12-31
Bypassing the error by disabling the reporting is a work around that does not solve the issue but only hides it.

I get a similar error message. In my case relating to my HP printer (hplip/firmware.py); till now it looks that after that error is shown the printer no longer works.

Note: this is just an observation, not a request for help.

---

### Post by wolfie52 on 2012-12-31
Thanks to both Wim and IBJSB4 for help and comments. OK I understand what you imply Wim. I would suspect (?) you have just left the error as it is something intermittent and does not affect unduly, the printing needs, but only on occasion? 

With that in mind do I consider leaving the suggested remedy as it is purely masking, or should I look for other answers. 

or should i take up kite flying.............its easier.............but maybe not as challenging!!

Geoff

---

### Post by vanadium on 2012-12-31
> **Wim Sturkenboom said:**
> Bypassing the error by disabling the reporting is a work around that does not solve the issue but only hides it.

That is correct. In previous versions of ubuntu, the same things also happened. However, in these versions, they were hidden by default.

What this tip says, is to disable the error report mechanism (apport), as it was by default in previous Ubuntu versions.

In order to really resolve these errors, we'd need deep knowledge into the operating system.

The errors indeed should not be an issue.

---

### Post by audiomick on 2012-12-31
> **ibjsb4 said:**
> 
And you may find gedit easier to use than nano.

```
sudo gedit /etc/default/apport
```


Nitpicking:

gedit is a graphical program, so you should use gksudo with it rather than sudo.

```
gksudo gedit /path/to/file
```

Here is why 
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by ibjsb4 on 2012-12-31
> **wolfie52 said:**
> With that in mind do I consider leaving the suggested remedy as it is purely masking, or should I look for other answers. 

Geoff

Its a known bug

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1020140](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1020140)

More here

[https://www.google.com/search?client=ubuntu&channel=fs&q=apport+bugs+launchpad+is+no+longer+under+development&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=apport+bugs+launchpad+is+no+longer+under+development&ie=utf-8&oe=utf-8)

---

### Post by wolfie52 on 2013-01-01
Thank you everyone, I really appreciate your help and support. Top drawer.

I will continue to read up on my knowledge of Ubuntu, and with the help you have all offered and provided, this will allow me to become less dependant upon basic info.

Happy New Year to you all


Geoff

---

### Post by ibjsb4 on 2013-01-01
Happy New Year  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

