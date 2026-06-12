---
title: "error with apps."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-04-28
when i try to load apps. in the add/remove section it gives me this message:  E: dpkg was interrupted, you must manually run 'dpkg            --configure -a' to correct the problem  
          E:_cache->open(), please report
Can someone tell me how to reslove this problem and how to report it.

---

### Post by Oldsoldier2003 on 2008-04-28
> **edwin2105z said:**
> when i try to load apps. in the add/remove section it gives me this message:  E: dpkg was interrupted, you must manually run 'dpkg            --configure -a' to correct the problem  
          E:_cache->open(), please report
Can someone tell me how to reslove this problem and how to report it.

run this command

```
sudo dpkg --configure -a
```

then ```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```
and everything should be fine

---

### Post by Sef on 2008-04-28
Applications > Accessories > Terminal

then run ```
sudo dpkg --configure -a
```


Then run 

```
sudo apt-get update
```

thn 
```
sudo apt-get upgrade
```

You shouldn't have to run -f install.  It should just work.

---

### Post by BaffledMollusc on 2008-04-28
Just to expand on what the above poster said, in case you don't understand it.

You need to type the above commands in a terminal. You can open a terminal by going to Aplications->Acessories->Terminal (I think, I'm not on an Ubuntu PC at the moment).

---

### Post by Oldsoldier2003 on 2008-04-28
> **Sef said:**
> Applications > Accessories > Terminal

then run ```
sudo dpkg --configure -a
```


Then run 

```
sudo apt-get update
```

thn 
```
sudo apt-get upgrade
```

You shouldn't have to run -f install.  It should just work.

I usually toss in the install -f because it doesn't hurt and will in some cases mean the OP doesn't need to post again. :) Just means they can move on with business faster...

---

