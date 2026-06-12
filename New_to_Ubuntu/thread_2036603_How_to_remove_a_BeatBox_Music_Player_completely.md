---
title: "How to remove a BeatBox Music Player completely"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by czgirb on 2012-08-02
How do I completely remove an application completely (incld. its settings) ?
The application called **BeatBox Music Player** and it can be found from the following URL: [http://www.webupd8.org/2012/02/elementary-music-player-beatbox-03.html](http://www.webupd8.org/2012/02/elementary-music-player-beatbox-03.html)
Cos every time I've tried to re-install the application, its previous settings still maintained.

I install it with the following command:
> 
*sudo add-apt-repository** ppa:sgringwe/beatbox***[I]
sudo apt-get update
sudo apt-get install beatbox
[/I]

At first I uninstall the application from USC ... since the previous library is still there,
So I've tried to use the following command:
> sudo apt-get --purge remove beatbox
And let **ubuntu tweak** to clean file **Janitor** and **re-start** the lappie ... but the result is the same

---

### Post by Elfy on 2012-08-02
You need to look in your home - there will be a hidden folder somewhere

In a terminal 

```
locate beatbox
```

check the locations in your home

---

### Post by hakermania on 2012-08-02
> **Elfy said:**
> You need to look in your home - there will be a hidden folder somewhere

In a terminal 

```
locate beatbox
```

check the locations in your home

This.

Also, keep in mind that the settings in general are being kept in the home directory of each user (never being removed when you remove a package), usually under ~/.config or under ~/.program_name

---

### Post by czgirb on 2012-08-02
Now! I found no **BeatBox** in my USC installed application
Why?

---

### Post by Elfy on 2012-08-02
Look for 

.cache/beatbox
.local/share/beatbox

---

