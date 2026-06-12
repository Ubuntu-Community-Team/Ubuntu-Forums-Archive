---
title: "/Home Preserve"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by ~chinook~ on 2008-07-13
I want to do a fresh install of Ubuntu Studio from my regular Ubuntu install. However, I was wondering if the option is available to preserve home in ubuntu studio?

Thanks,

Chinook

---

### Post by ajgreeny on 2008-07-13
You do not really need to do a fresh install unless you want to for other reasons than simply to get ubuntu studio.  You can simply use apt-get or synaptic and install ubuntustudio-desktop and you should end up in exactly the same position.  You will also have all the apps you have already added to straight ubuntu and won't need to reinstall any of them again, which you might if you do a fresh install.

---

### Post by ~chinook~ on 2008-07-13
Yeah I know. I just wanted to do a fresh install to clean some stuff up at the same time.

---

### Post by ajgreeny on 2008-07-13
OK, got you loud and clear.  If you already have a separate /home partition, no problem.  Just chose manual partitioning when the install gets to that part and make sure you set your current /home as the new /home, and also that it is not checked in the *Format* button.

If you don't have a separate /home partition already then you will either need to make one with the instructions [here]("http://www.psychocats.net/ubuntu/separatehome"), or I suppose you could try using the whole contents of your current ubuntu partition as your new /home and then delete all the old files from old root when it is in your new /home.  I have absolutely no idea about that last suggestion- it came to me as I was typing so I don't know if there are any ghastly problems to doing that which I have not thought about, but, if you have a good backup of your current home contents, it could be worth trying, I just have no experience of that situation.

Let us know if you try and it works, or even if it doesn't, as it may be useful for others in the same position in future.

---

### Post by ~chinook~ on 2008-07-13
What I decided to do was repartition and install on a smaller section. Then I will grab the files I need out of the old partition and wipe it.

---

