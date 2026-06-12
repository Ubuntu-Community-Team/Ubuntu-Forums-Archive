---
title: "Install Beryl with beryl-installer (Dapper + ATI)"
date: 2006-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by hegenious on 2006-12-03
Most people that want to install the fabulous Beryl eyecandy on their desktop do find this to be a painstaking process.
Well, at least I do. 
Countless HOWTO's are written on the subject, and countless times did I wreck my desktop using them, because of just a little typo somewhere or some other bug introduced by the user or the author.
At that pont I started thinking 'wouldn't it be nice if I had a script that did it all automatically for me'.
I started writing a shell script (not good enough at other languages) right away. The script uses zenity to display nice dialogs.
I have tested it on my DELL Dimension (simply removed all beryl stuff and installed it again with my script) and I did two tests with beryl-installer after having done a clean Dapper install. 
This revealed a few bugs that I have fixed.

Anyway, what I need is feedback. Please help me improve the script by running it (or just by reading the code) and reporting back in this thread how it went for you or any improvement or bug you would like to mention.

---

### Post by figo2476 on 2006-12-03
Hi
Thx for the installer. Here is some feedbacks.

This option is not available. Please see --help for all possible usages.
Error: unable to open display (null)
./beryl-installer: line 97: [: ==: unary operator expected
This option is not available. Please see --help for all possible usages.
This option is not available. Please see --help for all possible usages.
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/source/Sources.gz](http://xgl.compiz.info/dists/dapper/main/source/Sources.gz)  404 Not Found
E: Some index files failed to download, they have been ignored, or old ones used instead.
This option is not available. Please see --help for all possible usages.
This option is not available. Please see --help for all possible usages.

* Perhaps my zenity doesn't have those options.
* xgl.compiz.info - the site is still down.

---

### Post by hegenious on 2006-12-05
thanks for the feedback.
corrected the error in line 97 (==)  ](*,)  but oddly enough I get no complaints from my shell when I use ==.

you can safely ignore the resolving errors, it still works.

I use the zenity as it is included with a fresh install of dapper, I think yours doesn't support the --pulsate or --auto-close options or perhaps the --progress option all together.

---

### Post by HokeyFry on 2006-12-06
when i ran your script xorg (i think is what runs at startup) freaked out about not being able to find a device or something, and i had to restore the original xorg.conf. just letting u know it didnt work for me... :(

---

### Post by deadspeak on 2006-12-06
is this for just dapper or will it work with edgy as well?

---

### Post by hegenious on 2006-12-07
just dapper

hokeyfry, thanks for trying.  did you go through the reconfigure of xorg?
it's the tricky part in the script I think. if the user makes input errors there, the script is not able to correct that and as long as dpkg exits gracefully, the script will assume everything went hunkey dorey

---

### Post by prelude6x6 on 2006-12-08
Im sorry, im a little nooby...
How do install this? it is supposed to install beryl? Just dont know how to do it

Ive tried installing beryl manually, but then it wont work:(

---

### Post by hegenious on 2006-12-16
> Im sorry, im a little nooby...
How do install this? it is supposed to install beryl? Just dont know how to do it

Ive tried installing beryl manually, but then it wont work

well being a noob is no problem to me, we must all start somewhere, don't we?  :p 

to answer your question: yes, when you run beryl-installer (it is attached to my first post, on top of this page) it will download necessary files and drivers and install beryl to your computer.
Download the "beryl-installer" file to your pc and in a console, type "sudo ./beryl-installer" w/o the quotes from the directory where you saved it to.

note: this only works on Dapper (ubuntu 6.06) and with an ATI video card.
it will NOT install beryl on Edgy! it will NOT install beryl on NVIDIA!

By the way, Edgy has built-in support for beryl/aiglx so it has become a little easier to install than it was on dapper.

note: you have to add the universe and multiverse repositories. You can do that through synaptic. Otherwise, the fglrx driver will not be found.

Please feel free to post any errors, suggestions or other feedback in this thread.

---

### Post by croftd on 2007-02-10
I had to log in as ROOT user by typing sudo -i

I then punched in:

bash

and ran the script. I didn't experience the errors. The script is still running - currently utilising apt-get to grab stuff. Very clever, I'll let you know how it goes!!

Dan.

[email]croftd@mac.com[/email]

---

### Post by Mmmbopdowedop on 2007-03-26
lol . . he posted that over 40 days ago . . . 

script must still be running :) 

:lolflag:

---

