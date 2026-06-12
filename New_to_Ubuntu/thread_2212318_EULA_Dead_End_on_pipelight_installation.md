---
title: "EULA Dead End on pipelight installation"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by yonster on 2014-03-20
I was entering the commands given to install pipelight at the _fds-team.de/cms/pipelight-installation.html_, and after the third line a EULA agreement came up for mcrosoft silverlight as per the instructions, the problem was that I was completely unable to enter *anything* into the terminal at that point, such as typing "y" to consent to the agreeement that the instructions gave.  Anyone else had this problem?

---

### Post by deadflowr on 2014-03-20
I've never had a problem consenting to EULA's in a terminal.
Most likely you need to navigate them with tab, arrow keys.

I installed pipelight sometime ago
(a month ago, maybe)
and don't even remember the EULA.
Though, I'm sure it was there.

---

### Post by Vladlenin5000 on 2014-03-20
Indeed. The usual mistakes are trying to use the mouse or typing. As written above you need the TAB and arrow keys (plus Enter when appropriated) to navigate and select the options. It's the same as when installing the Microsoft TrueType fonts included in the restricted-extras package (and others).

---

### Post by deadflowr on 2014-03-20
Some else to think about is that once you add a ppa, you can install the packages via the software center or synaptic if you want.
(Simply search for them in the program search box; ie, search for pipelight)
Those usually have EULA agreement fields that can be navigated with a mouse.

---

### Post by yonster on 2014-03-20
Ya, that was definitely the problem, however from there it was on to the next NIGHTMARE in trying to switch the 'user agent overrider' that the next step required. I had a problem with every line... first it rejected the '(' that was in the command, then it didn't like the capital letters (as shown in the command) in firefox, then linux.  Next it said the program linux wasn't installed, but was relieved they gave the command to install it... only to hit the next wall after attempting the next command.  But this time, unlike the previous times, it didn't give me any clue what the problem was.  At least prior to that it would say "sytax error near unexpected token '('", or "No command 'Firefox' found, did you mean Command 'firefox'..."  *This* time it spits back (verbatim):

(process:5513): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size ==0' failed

Anyone have any idea what THAT's all about?????

---

### Post by deadflowr on 2014-03-20
Isn't user switching an addon within firefox?
You shouldn't need to use a command line for that.

---

### Post by yonster on 2014-03-20
All I know is that the very last line of the FDS team instructions is "please note that you will need to install a user agent switcher for most plugins/pages to get them working."

---

### Post by deadflowr on 2014-03-20
Go here
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)
Click install.
Then you should now have the user agent override icon somewhere on firefox, either in the bottom panel or up top.
It has a dropdown icon, click that and it should list preferences.Click on that.
simply copy and paste this
```
Firefox 15/Windows: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:15.0) Gecko/20120427 Firefox/15.0a1
Safari/OSX: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_3) AppleWebKit/534.55.3 (KHTML, like Gecko) Version/5.1.3 Safari/534.53.10

```
into the bottom of that.
Those entries should show up at the bottom of the user agent override.

---

### Post by yonster on 2014-03-20
Thanx for your help DF, I got close, but in the end the archive manager kept saying an error occured when I tried to open Silverlight.  It could just be my screwy computer, or maybe because I'm using lubuntu from the cd as a live user... who the heck knows!! For now, I've definitely had enough "*_fun!_*", but I *certainly* appreciate your effort to help out!

---

### Post by rbmorse on 2014-03-20
> ...maybe because I'm using lubuntu from the cd as a live user...     That would have been helpful to know at the beginning.

---

### Post by deadflowr on 2014-03-20
> **yonster said:**
> Thanx for your help DF, I got close, but in the end the archive manager kept saying an error occured when I tried to open Silverlight.  It could just be my screwy computer, or maybe because I'm using lubuntu from the cd as a live user... who the heck knows!! For now, I've definitely had enough "*_fun!_*", but I *certainly* appreciate your effort to help out!

That's okay, at least now you have a better understand of what not to do, and if you feel like tackling it again, you know where to come.
Good Luck, in which ever way you go.

---

### Post by mqchael on 2014-03-21
Hi,

your problem is that you try to run Pipelight from a live CD. Silverlight needs xattr to work properly and the RAM / tmpfs filesystem which is used on such live CDs does not support xattr. You need to use a patched kernel to enable xattr on tmpfs. If you want to try pipelight without installing it to your normal hard disk, you can use our live CD which already ships everything preinstalled: [http://repos.fds-team.de/pipelightos/releases/pipelightos-alpha1.iso](http://repos.fds-team.de/pipelightos/releases/pipelightos-alpha1.iso) (see [http://repos.fds-team.de/pipelightos/releases/README](http://repos.fds-team.de/pipelightos/releases/README) for more information). 

The only disadvantage of the image is that we use Debian wheezy as base system and the slightly outdated kernel of Wheezy has some problems with recent Nvidia graphic cards. We might update to a more recent kernel in the future.

---

### Post by yonster on 2014-03-21
Thanx Mqchael, I suspected that might be part of the problem, but am too clueless overall to know (obviously).  Appreciate it ;).

---

