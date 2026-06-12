---
title: "bash prompt?"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Matrix01 on 2012-01-08
You can launch Google Chrome browser by visiting the Application > Internet > Google Chrome. Or type the following command at a bash prompt:
google-chrome &

[http://www.cyberciti.biz/faq/fedora-ubuntu-debian-suse-linux-install-googlechromebrowser/](http://www.cyberciti.biz/faq/fedora-ubuntu-debian-suse-linux-install-googlechromebrowser/)

[http://linuxconfig.org/Bash_prompt_basics](http://linuxconfig.org/Bash_prompt_basics)

i found this webpage,
will u help me how to run chrome with bash prompt?

---

### Post by SuaSwe on 2012-01-08
Hi Matrix01,

I'm not exactly sure what you mean - are you looking to how you would launch Chrome using the bash prompt? You would do that by opening the command line as stated above (Applications > Accessories > Terminal I believe; Bash is the default Ubuntu shell) and typing in the text 'google-chrome &', as above - provided it is installed, of course!

Out of interest, why are you looking to launch it this way?

Edit: didn't see that it was a Fedora site you were looking at there. Having searched around, it appears the Ubuntu method would be to just type 'chromium-browser' (see e.g. [http://ubuntuforums.org/showthread.php?t=1385182](http://ubuntuforums.org/showthread.php?t=1385182)).

---

### Post by jjex22 on 2012-01-08
I also am unsure why you would launch graphical programs this way - launching from the terminal, means that they continue to run from the terminal; close the terminal, close the program. You also have twice as many windows open... If you're half as fussy as me this will annoy you.

If your in your desktop environment (well you are... chrome won't run from the CLI :) ) try pressing alt+f2 to open the run command prompt enter the name of the program and hit return - you can also select run as root, so there's no need to gksu.

if you were looking for an easy program selection tool for the cli, might I suggest pdmenu? it's a menuing system for the terminal - once installed, just type pdmenu to browse using the arrow keys to your browser and hit return - this will launch it Independently of the terminal, and whilst obviously slower than just typing the program, it's useful for finding things.

---

### Post by Paqman on 2012-01-08
> **jjex22 said:**
> I also am unsure why you would launch graphical programs this way

Normally the only reason would be if you were trying to troubleshoot a problem. Running things in terminal allows you to see the actual errors being produced.

---

### Post by jjex22 on 2012-01-08
> **Paqman said:**
> Normally the only reason would be if you were trying to troubleshoot a problem. Running things in terminal allows you to see the actual errors being produced.

Good catch paqman - I made the generalisation that the OP wouldn't need this info - quite right to correct me :)

---

### Post by Matrix01 on 2012-01-08
k@ubuntu:~$ google-chrome &
[1] 1572
k@ubuntu:~$ google-chrome: command not found

typed that in terminal,
and
above is output....
not working.

> **SuaSwe said:**
> Hi Matrix01,

I'm not exactly sure what you mean - are you looking to how you would launch Chrome using the bash prompt? You would do that by opening the command line as stated above (Applications > Accessories > Terminal I believe; Bash is the default Ubuntu shell) and typing in the text 'google-chrome &', as above - provided it is installed, of course!

Out of interest, why are you looking to launch it this way?

Edit: didn't see that it was a Fedora site you were looking at there. Having searched around, it appears the Ubuntu method would be to just type 'chromium-browser' (see e.g. [http://ubuntuforums.org/showthread.php?t=1385182](http://ubuntuforums.org/showthread.php?t=1385182)).

---

### Post by Matrix01 on 2012-01-08
pressed alt + f2,
nothing happened..

> **jjex22 said:**
> I also am unsure why you would launch graphical programs this way - launching from the terminal, means that they continue to run from the terminal; close the terminal, close the program. You also have twice as many windows open... If you're half as fussy as me this will annoy you.

If your in your desktop environment (well you are... chrome won't run from the CLI :) ) try pressing alt+f2 to open the run command prompt enter the name of the program and hit return - you can also select run as root, so there's no need to gksu.

if you were looking for an easy program selection tool for the cli, might I suggest pdmenu? it's a menuing system for the terminal - once installed, just type pdmenu to browse using the arrow keys to your browser and hit return - this will launch it Independently of the terminal, and whilst obviously slower than just typing the program, it's useful for finding things.

---

### Post by jjex22 on 2012-01-08
> **Matrix01 said:**
> pressed alt + f2,
nothing happened..

Sorry Matrix01, well the program should be called xfrun4, have a look in settings manager - keyboard - applications manager, and check xfrun4 is set to alt+f2, then add the program xfce4-settings-helper to autostart programs?

Failing that install dmenu or synapse and set it to alt and f2 in the applications manager. Hope this is helpful?

Reference - Toz and VTpoet [here]("http://ubuntuforums.org/showthread.php?t=1773019")

---

