---
title: "google earth"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by blake7 on 2008-08-18
hi i have tryed to dowm load google earth it says choise an application

what do i do 

please cam you help 

thank for your time

---

### Post by billgoldberg on 2008-08-18
> **blake7 said:**
> hi i have tryed to dowm load google earth it says choise an application

what do i do 

please cam you help 

thank for your time

In a terminal (applications -> accessories -> terminal) copy/paste this:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Press enter, enter you password (you won't see how many digits you type) and press enter again.

If it is finished, copy/paste this:

```
sudo apt-get install googleearth
```

and press enter.

Once it is finished it will be in the applications menu.

---

### Post by blake7 on 2008-08-18
thanks for your rep;ay
but when i did it , it did not work

i got this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
a@a-laptop:~$ 

what do i do now.


cheers

---

### Post by mikewhatever on 2008-08-18
sudo dpkg --configure -a

---

### Post by billgoldberg on 2008-08-18
Just run that command in a terminal.

And redo the steps.

This error occurs when you close the windows while the program is still installing.

---

### Post by blake7 on 2008-08-18
thanks for all your timei 

regarding windows
and the only thing wrong with windows is it not open souce, other wise it lets people who have no intrest in how they work just get on with thier lives. 
that is a good thing. as much as i love you all i wuld be much happy going on my lap top doung the work and then moving on all this sudo stuff is just not ever going to work
is it????
would yo

---

### Post by billgoldberg on 2008-08-18
> **blake7 said:**
> thanks for all your timei 

regarding windows
and the only thing wrong with windows is it not open souce, other wise it lets people who have no intrest in how they work just get on with thier lives. 
that is a good thing. as much as i love you all i wuld be much happy going on my lap top doung the work and then moving on all this sudo stuff is just not ever going to work
is it????
would yo

Once your system is set up like you like it, there is no reason to use the command line interface.

It will just work then.

---

### Post by mikewhatever on 2008-08-18
> **blake7 said:**
> thanks for all your timei 

regarding windows
and the only thing wrong with windows is it not open souce, other wise it lets people who have no intrest in how they work just get on with thier lives. 
that is a good thing. as much as i love you all i wuld be much happy going on my lap top doung the work and then moving on all this sudo stuff is just not ever going to work
is it????
would yo

Use what works best for you.

---

### Post by blake7 on 2008-08-18
E: /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb: subprocess pre-installation script returned error exit status 1

wht does this mean
E: /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jre_6-06-0ubuntu1_all.deb: subprocess pre-installation script returned error exit status 1

---

### Post by hotrod6657 on 2008-08-18
with respect to the terminal there is almost always a graphical way to do everything in Ubuntu.  I don't know all the steps you would have to take to do specifically what you're trying to do without the terminal, but it can be done.

One of the reasons that the terminal gets used to much is because it makes it easier to ensure that the right thing gets done.  For example.  It would be much more difficult to get instructions on how to open the sources.list file and add the proper line than to just give the command.  It helps to put everyone on the same page.

In theory a command should do the exact same thing on your system no matter what you've done to it visually as on anyone else's system.

Window's tech support does the same sort of thing, last time i talked to them (long time ago) i spent most of my time in command line and using the run option on the start menu.  It was just easier than the tech person having to guide me through each click.

I'll see if i can't find out something about your errors now.

---

### Post by hotrod6657 on 2008-08-18
which version of Ubuntu are you using?

---

### Post by hotrod6657 on 2008-08-18
are those errors what you got when you re-ran the commands from the earlier reply?  If you didn't I would say redo both of those commands.  Make sure you say "y" when it asks you during the install and don't close terminal until you get the same prompt that it started with, that would mean it's done.

---

### Post by oldsoundguy on 2008-08-18
First you have to enable the sources or repositories.

System> Administration> Software Sources> 3rd party software> enable by checking what is there.

After that run (in terminal):
sudo apt-get update
sudo apt-get upgrade

(apparently the only source you are attempting to use is your dvd.)

Then go to Google and type in "ubuntu guide" .. find your operating system from the list and go to that page.  On that page will be some cut and paste commands for expanding your third party list and instructions on how to do so.
(there are also some very useful commands and "how-to" instructions on the pages.  Worth bookmarking and keeping.)

---

### Post by blake7 on 2008-08-19
thank you for your rely that does help. one last point millions of poeple use google earth  the bbc web ect  why is ubuntu not set up for the start for the most common activites

thanbk you agian for your time

---

### Post by philinux on 2008-08-19
Simply put this...

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by hotrod6657 on 2008-08-19
> **philinux said:**
> Simply put this...

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

ditto

---

### Post by blake7 on 2008-08-24
can someone in the future just make it one click to this,  iam mean come on google earh ever one on the world would want that and yet it even to do this one simple this a pain in the ****

---

