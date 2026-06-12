---
title: "Cannot remove suggestions in the Dash"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-18
Hello all

I'm trying to remove the suggested search results from the dash:

[[IMG]http://s23.postimg.org/6m6giq4xz/Screenshot_from_2014_05_18_21_02_58.jpg[/IMG]]("http://postimg.org/image/6m6giq4xz/")

So far I have tried:

System Settings > Security & Privacy > Search Tab > When Searching in the Dash, Include Online Search Results = OFF

I have also tried:

```
sudo apt-get remove unity-lens-shopping
```

I have since tried rebooting as well.

Recommendations on the Ubuntu Software Centre are also turned OFF.

The results still show in the Dash though.

---

### Post by staticn0de on 2014-05-18
Hi there, 

Give the following a go in terminal. It will disable Amazon lens

gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"

gsettings set com.canonical.Unity.Lenses remote-content-search none

---

### Post by christo3 on 2014-05-18
The most simple solution : sudo apt-get install kubuntu-desktop :D

---

### Post by Drowz0r on 2014-05-18
> **staticn0de said:**
> Hi there, 

Give the following a go in terminal. It will disable Amazon lens

gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"

gsettings set com.canonical.Unity.Lenses remote-content-search none

Okay, I did that, tried it with sudo at the front too. Did a reboot. No change :(

---

### Post by 3rdalbum on 2014-05-18
Those suggestions are from Ubuntu Software Center, not Amazon. Also, it doesn't need to go online to give suggestions which is why it still appears.

This tells you how to turn them off: [http://askubuntu.com/questions/227950/how-to-remove-the-ubuntu-software-center-suggestions-from-the-dash](http://askubuntu.com/questions/227950/how-to-remove-the-ubuntu-software-center-suggestions-from-the-dash)

---

### Post by Drowz0r on 2014-05-18
Lovely. That's a winner. Thanks.

---

