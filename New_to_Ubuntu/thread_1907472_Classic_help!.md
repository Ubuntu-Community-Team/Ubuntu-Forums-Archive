---
title: "Classic help!"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by marc11657 on 2012-01-11
Hi there, 

My webcam isn't working in Skype and I have tried most suggestions using the terminal. I came across this suggestion

Re: Webcam not showing in skype
scratch that.

works now.

I found instruction to go to system>preferences>main menus: applications>skype>properties and changed the command there to
Code:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
loads now with video



However I can't seem to find the option to go to:

system>preferences>main menus: applications>skype>properties

I am using ubuntu 11.10. Am I right in assuming that those menus are only available in the classic desktop of ubuntu? I have attempted the session fallback command in the terminal but the install fails as it can't find the package on drive E

Any help would be appreciated!

Thanks! Marc

---

### Post by gordintoronto on 2012-01-11
Does your webcam work in Cheese? If so, try opening a Terminal and enter the command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

You might need to install Cheese from the software centre. It provides simple picture-taking and recording video from a webcam.

Or, you could click on the Dash and search for "menu" to get the main menu program.

---

### Post by marc11657 on 2012-01-12
Thank you sooo much for your help! :-D

I keep getting this same error before skype loads... the webcam still doesnt work and works fine with cheese.


wilde@wilde:~$ bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4llcompat.so skype'
ERROR: ld.so: object '/usr/lib/libv4l/v4llcompat.so' from LD_PRELOAD cannot be preloaded: ignored.


any ideas?

---

### Post by gordintoronto on 2012-01-12
There are now two files! Since Skype is a 32-bit program, I suspect you should use this one: /usr/lib32/libv4l/v4lcompat.so

It's the same as before, with the insertion of "32".

The other one is:
/usr/lib/x86_64-linux-gnu/libv4l/v4lcompat.so

Unfortunately, I don't think I can test it. I have Ubuntu 11.10 installed on a cheap HP G62 laptop, and Skype's video works "out of the box," after installing Skype from the repositories.

---

