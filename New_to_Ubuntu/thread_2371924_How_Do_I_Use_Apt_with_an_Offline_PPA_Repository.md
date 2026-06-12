---
title: "How Do I Use Apt with an Offline PPA Repository?"
date: 2017-09-19
forum: New to Ubuntu
---

### Post by rob-a-saurus on 2017-09-19
Hello,

I'm a Linux noob but a longtime Windows/DOS user.
I'm running Ubuntu Trusty on an air-gap network (see below).
 
As a baseline, I'm already able to use apt with an offline Ubuntu repository to install anything that's available in the Ubuntu repos:  main, restricted, multiverse, and universe.  My offline Ubuntu repository is stored on a USB hard drive.  I'm having difficulty doing the same thing with a PPA repository.
 
My setup is:
 
A.  Windows 7 PC connected to Internet through corporate network.
B.  Ubuntu (Trusty) PC on "air-gap" network.
 
I want to use apt to install KiCad 4 ([http://kicad-pcb.org/download/ubuntu/](http://kicad-pcb.org/download/ubuntu/)) on my air-gap Ubuntu PC.
 
I've done the following on the Windows PC:[INDENT]1.  I setup pyapt-mirror, [https://launchpad.net/pyapt-mirror](https://launchpad.net/pyapt-mirror), on my Windows PC.
2.  I pointed pyapt-mirror to the KiCad repo:  [http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu](http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu) trusty main
3.  I ran pyapt-mirror and successfully downloaded the PPA to my Windows PC.
4.  I copied the local mirror from my Windows PC to a USB hard drive.[/INDENT]
 
I've done the following on the Ubuntu PC:[INDENT]5.  Moved the USB hard drive to my Ubuntu PC and used 'tree -d' to confirm that the PPA is visible:
```
[FONT=lucida console]/media/<user>/<volname>/ppa.launchpad.net/js-reynaud/kicad-4/ubuntu
&#9500;&#9472;&#9472; dists
&#9474;   &#9492;&#9472;&#9472; trusty
&#9474;       &#9492;&#9472;&#9472; main
&#9474;           &#9492;&#9472;&#9472; binary-amd64
&#9492;&#9472;&#9472; pool
    &#9492;&#9472;&#9472; main
        &#9500;&#9472;&#9472; k
        &#9474;   &#9500;&#9472;&#9472; kicad
        &#9474;   &#9500;&#9472;&#9472; kicad-doc
        &#9474;   &#9500;&#9472;&#9472; kicad-i18n
        &#9474;   &#9492;&#9472;&#9472; kicad-library
        &#9492;&#9472;&#9472; w
            &#9500;&#9472;&#9472; wxpython3.0
            &#9492;&#9472;&#9472; wxwidgets3.0[/FONT]
 
14 directories
```
 
6.  I created the sources list file like this:  ```
sudo gedit /etc/apt/sources.list.d/sources.list
```
7.  In that file, I added this string (the only string in the file):
   ```
deb file:///media/<user>/<volname>/ppa.launchpad.net/js-reynaud/kicad-4/ubuntu trusty main
```
Note that I opened Ubuntu Software Center and selected Edit -> Software Sources… -> Other Software.. and I can see my new entry:  ```
file:///media/<user>/<volname>/ppa.launchpad.net/js-reynaud/kicad-4/ubuntu trusty main
```
8.  In a terminal I typed:   ```
sudo add-apt-repository –yes ppa:js-reynaud/kicad-4
```
   After a few seconds it responds:
      > Cannot add PPA: 'ppa:js-reynaud/kicad-4'.
      Please check that the PPA name or format is correct.[/INDENT]
 
I need some suggestions for what to try next.
 
Thanks,
 
-Rob

---

### Post by QIII on 2017-09-20
What is the purpose for the air gap between your Ubuntu machine and the Windows machine on your corporate network?

---

### Post by rob-a-saurus on 2017-09-20
QIII,

At my company, all the engineering computers are on an air-gap network.  Email and web is only available on our "Corporate Network".  Most engineers have two computers on their desks, one for each network.  Normally, all USB ports are disabled on both networks and they've established a tedious process for moving files between networks.  I have special permission to use USB to get this experiment going.

-Rob

---

### Post by QIII on 2017-09-20
Then my next question has to be this:  Have you engineers knocked this around among yourselves under the watchful eye of your supervisors?  This sounds like just the sort of thing that those "tedious" processes are intended to guard against.  This appears to represent an activity your employer went to a great deal of effort to avoid.  What good are those security efforts if an easy bypass is devised? If you can figure out how to do this, can't others use what you find out?

My concern is this:  Given the intended purpose of an air-gap network, your question appears to be a large component of an instructional discussion of how to defeat such an arrangement.  Your intentions are above board, no doubt.  But what of those of nefarious intent who may read this later?

It seems to me that those who devised the network would be the best to discuss this with -- a discussion that can take place within your organization with no threat of compromise -- rather than random, anonymous people on a public forum.

Closed for further staff review.

---

