---
title: "Installing Matlab in ubuntu 11.10"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by bustamanteg on 2012-01-18
HI everyone, 

I am trying to install Matlab in Ubuntu 11.10.  In the guides I get it says that you should open the terminal, go to the matlab folder and run 

sudo ./install
sudo /install

but there is no install file in that folder. I have looked everywhere and still don't find the install file. I also looked for hidden files. This is the  MATLAB R2010b. 

Please help!

---

### Post by Double.J on 2012-01-18
hi there, I'm guessing you've downloaded a source package - typically ending in .tar.gz or .tar.bz2?

The instructions you were given may have changed over time, it's always good to check the readme of the package. by looking in the package in the terminal and running
```

nano -w README.TXT

```

use the ls command to look around the folder just in case it isn't called readme :)

hope it helps!

---

### Post by Double.J on 2012-01-18
I just noticed in the software centre that Matlab is in the repos, was there a reason you didn't want to use this version?

---

### Post by bustamanteg on 2012-01-19
Thanks for your reply. I am sure I read the readme file, and it did not have any useful information....

How do you install from the "repos". Is it something like 

sudo apt-get matlab?

Thank you.

---

