---
title: "Install cinelerra"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by woodchimp on 2012-11-28
Hi
I am trying to install Cinelerra. I have read the forums and the answers do not work. 
I have run **ppa:cinelerra-ppa/ppa**and that worked thendid the sudo-apt update; however I still cannot see it in "Apps for download"

Could someone explain how I down load and install Cinelerra?

Thank you

regards

---

### Post by holycow131415 on 2012-11-28
you should be able to do

sudo apt-get install cinelerra

in the terminal since you added the ppa and updated.

---

### Post by evilsoup on 2012-11-28
> **woodchimp said:**
> thendid the sudo-apt update; however I still cannot see it in "Apps for download"

Just want to check. You did actually use
```
sudo apt-get update
```
right? Then it should show up in the software centre. Holycow's solution should also work.

Be warned that, while cinelerra is currently the best NLE in Linux (IMO), it's still pretty bad & crashy.

---

### Post by monkeybrain2012 on 2012-11-28
BTW, if you check the ppa the name of the package is not cinelerra, but cinelerra-cv

so you should do the following

```
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra-cv
```

EDITED: you don't need the first command if you have already added the ppa, but I am not sure if you have since I don't understand what you meant by "I have run ppa:cinelerra-ppa/ppa" It is a repository to add to your software sources, not a command to "run".

---

### Post by woodchimp on 2012-11-28
Thank you everybody who replied.

 MonkeyBrain2012  was right, I used cinelerra-cv and it installed straight away. I am sorry for being a ludite.

regards

---

