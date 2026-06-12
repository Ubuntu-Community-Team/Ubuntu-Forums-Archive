---
title: "help with ATP sources"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by ERGOtruth on 2008-06-28
As might be expected from one posting in the absolute beginner forum, I have no idea what I'd doing.

I'm attempting to install World of Warcraft and a few other games on my newly ubuntu'd machine.  I read that the best way to do this was through a device called Wine.  In my search through the internet, I came across this page,

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and have been trying to follow the instructions listed there.

I've managed to open the Terminal Window and paste the code, the part I am stuck at is the one after that.  I don't have the faintest idea whaty  a repository of ATP sources is, and would be very happy to find out.

thanks for any potential help

---

### Post by cecure on 2008-06-28
Add this line to your apt sources (located in System > Administration > Software Sources > Third Party Software): 

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

:)

Then in a terminal type:
```
sudo apt-get update
```

and then
```

sudo apt-get install wine
```

:)

---

### Post by plucky on 2008-06-28
> **cecure said:**
> Add this line to your apt sources (located in System > Administration > Software Sources > Third Party Software): 

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

:)

Then in a terminal type:
```
sudo apt-get update
```

and then
```

sudo apt-get install wine
```

:)

Nooooo


Copy and paste that line into a terminal window and it will add a file in /etc/apt/sources.list.d called hardy.list,which is the same as adding a repository in sources.list.


Then do the last two commands will install **Wine**.


Good Luck

---

### Post by ERGOtruth on 2008-06-28
Thanks so much for responding so quickly.

I did find Software Sources, and was then able to locate the Third-Party Software tab.  Once there I clicked +Add..., but after trying several times to paste

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

and variations thereof, the +Add Source button is still greyed out and cannot be clicked.

where have I gone wrong?  and thank you for the support.

Edit- I have not yet attempted plucky's suggestion.






Edit2-  Thanks so much, it appears to be working now.  Very fancy

---

### Post by cecure on 2008-06-29
Plucky's solution should work.  Sorry about my mistake... I should have read the line better :)

---

