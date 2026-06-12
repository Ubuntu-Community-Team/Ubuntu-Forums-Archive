---
title: "How to run print driver setup command"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by wpshooter on 2008-06-27
I the readme file that is associated with the setup of print driver for a Lexmark Z611 printer the instructions say to run the following command from terminal. 

But when I try it, it does not work.  Can this command be run from a Ubuntu terminal ?  And if so, what am I doing wrong ?

sh z600cups-1.0-1.tar.gz.sh

Thank you.

---

### Post by phidia on 2008-06-27
As shell script should be capable of running.
Sometimes you need to type "./" before the command.
Also check the permissions and see if it's executable.

---

### Post by wpshooter on 2008-06-27
> **phidia said:**
> As shell script should be capable of running.
Sometimes you need to type "./" before the command.
Also check the permissions and see if it's executable.

I did all of that including trying to run a sudo and still no dice.

Is there something I am missing here ?  Should this command type run on a debian based O/S ?

Thanks.

---

### Post by phidia on 2008-06-27
Is there a README file in the directory created from unpacking? If so that should tell you what it will work with, and debian and all distros I know of will run shell scripts. That's what the "sh" is telling you this is. But even though they _can_ run a shell script the script itself may not be compatible, and probably isn't, with all distros.

I'm not sure why you approached this the way you did but the printer you are trying to get working is listed as unsupported at the best resource linux users have for printing (The Linux Foundation's openprinting database) you can view their summary of that printer [here]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_series_z611").

---

### Post by wpshooter on 2008-06-27
> **phidia said:**
> Is there a README file in the directory created from unpacking? If so that should tell you what it will work with, and debian and all distros I know of will run shell scripts. That's what the "sh" is telling you this is. But even though they _can_ run a shell script the script itself may not be compatible, and probably isn't, with all distros.

I'm not sure why you approached this the way you did but the printer you are trying to get working is listed as unsupported at the best resource linux users have for printing (The Linux Foundation's openprinting database) you can view their summary of that printer [here]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_series_z611").

This link says "works mostly"

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z611](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z611)

Which one am I to believe ?

Thanks.

---

### Post by phidia on 2008-06-27
Z611 is different than z611 and I have seen that printer makers do use lower/upper case to desiginate different models, but I don't know all the models available in the lexmark line.

---

