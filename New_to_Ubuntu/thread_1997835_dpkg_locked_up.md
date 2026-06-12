---
title: "dpkg locked up"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by grantmcduling on 2012-06-05
I tried to install WINE last night and all went well until the program tried to connect to nchc.dl.sourceforge.net | 32.1.14.16|80 ...

It kept timing out and couldn't connect. NOw I think dpkg is stuck.  I got a message saying to run dpkg --configure -a but the same thing happened. Now I can't even get synaptec to run as it keeps going back to that command. 

How do I abort this?

---

### Post by matt_symes on 2012-06-05
Hi

Open a terminal and type 

```
sudo apt-get install -f
```

Post the results back here by highlighting the text in the terminal->right click->copy and pasting into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by grantmcduling on 2012-06-05
```
grant@grant-GQ565AA-ABG-SR5220AN:~$ sudo apt-get install -f
[sudo] password for grant: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
grant@grant-GQ565AA-ABG-SR5220AN:~$ 

```

---

### Post by grantmcduling on 2012-06-06
When I do the --configure -a in terminal, I seem to be getting stuck loggin on to SourceForge. Is there a problem with SourceForge? This seems to be the cause of my problems.

---

### Post by grantmcduling on 2012-06-06
When I run Synaptec to try and uninstall the offending application, it is stuck at 'configuring ttf-mscorefonts-installer'. Problem comes back to loggin on to source forge. I can't close the Synaptec window now.

I have had to resort to the REISUB trick with Alt and SysRq held down.

---

### Post by grantmcduling on 2012-06-06
I eventually worked it out: had to remove ttf-mccorefonts-installer with apt-get. Then I removed the offending app (Wine) with Synaptec. Seems fine now. I won't try Wine again as it leads to a hangover.

---

### Post by matt_symes on 2012-06-06
Hi

> I won't try Wine again as it leads to a hangover.

:popcorn: Whisky is worse.

I'm glad you got it fixed. Sorry i did not reply. I was asleep. Timezones....

Kind regards

---

