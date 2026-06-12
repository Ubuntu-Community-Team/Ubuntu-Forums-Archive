---
title: "no software centre or updates."
date: 2012-01-09
forum: New to Ubuntu
---

### Post by sogeking99 on 2012-01-09
something seems to be wrong with my ununtu here. I click software centre and it says please reinstall software database package. and also update manager wont find anything, says check internet conenction

i'm on 11.04

Thanks.

---

### Post by philinux on 2012-01-09
> **sogeking99 said:**
> something seems to be wrong with my ununtu here. I click software centre and it says please reinstall software database package. and also update manager wont find anything, says check internet conenction

i'm on 11.04

Thanks.

Open a terminal and post back any errors from this.

sudo apt-get update

---

### Post by sogeking99 on 2012-01-09
Here is the output. [http://paste.ubuntu.com/798533/](http://paste.ubuntu.com/798533/)

---

### Post by wolfen69 on 2012-01-09
> **sogeking99 said:**
> Here is the output. [http://paste.ubuntu.com/798533/](http://paste.ubuntu.com/798533/)

In the future, you can paste directly to a post here in the thread. Just click the code icon "#", and paste into that.

---

### Post by wildmanne39 on 2012-01-09
Hi, > [http://dwarftherapist.com/apt/dists/maverick/universe/source](http://dwarftherapist.com/apt/dists/maverick/universe/source)this is either not on the server or the server is down, you can open synaptic click on settings>repositories>other sources then uncheck that ppa or remove it.
Thanks

---

### Post by sogeking99 on 2012-01-09
> **wildmanne39 said:**
> Hi, this is either not on the server or the server is down, you can open synaptic click on settings>repositories>other sources then uncheck that ppa or remove it.
Thanks

ok thanks. Any idea why my software centre disappeared?

---

### Post by oldos2er on 2012-01-09
Are you using Natty? Remove all the 'maverick' references in your sources.list with ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by sogeking99 on 2012-01-11
Do you mean just the word, or the whole line?

---

### Post by spacecheck on 2012-01-11
> **sogeking99 said:**
> Do you mean just the word, or the whole line?
If you upgraded to Natty, you no longer need the lines pertinent to maverick, so you can simply remove each entire line related to maverick.

If it works for you, don't forget to use the thread tools to mark the thread Solved.

Good luck!

---

### Post by sogeking99 on 2012-01-11
Ok I removed all lines with maverick. How can I get my software centre back?

---

### Post by BC59 on 2012-01-11
To be sure that you are using only Natty repositories open the Software Center and check in the tab Other Software if everything is OK.
Then run in a terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sogeking99 on 2012-01-11
I can't open the software centre, thats my problem, says I need to reinstall software database package?

---

### Post by bluexrider on 2012-01-11
I had an issue like this one once. This is how I solved it.


Make a backup copy of the hidden cache file
```
sudo cp ~/.cache/software-center ~/.cache/software-center.backup

```

Remove the hidden cache file
```
sudo rm -rf ~/.cache/software-center
```


Run the program
```
sudo /usr/bin/software-center %u
```

---

### Post by BC59 on 2012-01-11
Try this
```
sudo apt-get install --reinstall software-center
```

or ```
sudo apt-get install synaptic
``` and install software center from there

---

### Post by sogeking99 on 2012-01-14
> **BC59 said:**
> Try this
```
sudo apt-get install --reinstall software-center
```

or ```
sudo apt-get install synaptic
``` and install software center from there

Sorry for late reply, yes that worked. :)

Wonder why it disappeared in the first place?

---

### Post by BC59 on 2012-01-15
The Software Center has many dependencies to other packages. So if you remove an application, sometimes affects other ones depending to it's packages. Or during the regular system update, a new package depending to the center was not correctly installed.

---

