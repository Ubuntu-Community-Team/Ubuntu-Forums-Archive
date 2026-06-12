---
title: "Ubuntu Software don't show packages from repo"
date: 2019-02-28
forum: New to Ubuntu
---

### Post by babahcv on 2019-02-28
Hello everybody.
I have my repository with some packages, but I can`t find this packages from Ubuntu Software (gnome-software Ubuntu 18.04).  Maybe somebody know how I can enable this repository in Ubuntu Software?

Also I have mirrors of official repos, but I don`t see it on Ubuntu Software too.

---

### Post by Frogs Hair on 2019-02-28
Hello and Welcome

Avaiable repositories are listed in software & updates. If you would like a more comrehensive package listing install synaptic and look at the status setting. ```
sudo apt install synaptic  
```

---

### Post by babahcv on 2019-02-28
Thank you!)
I know about synaptic, but I need to show packages from my repo in gnome-software for other (non IT) users.

---

### Post by babahcv on 2019-03-07
Also i can't find software in gnome-software from next repos 
ppa:openshot.developers/ppa

 ppa:webupd8team/sublime-text-3
 ppa:ubuntugis/ubuntugis-unstable 


[IMG]https://gitlab.gnome.org/GNOME/gnome-software/uploads/c1300412acec08e5ab5564e859ea1c60/Screenshot_from_2019-03-07_09-36-26.png[/IMG]

---

### Post by monkeybrain20122 on 2019-03-07
It never does, now it has more but still missing a lot. On the other hand it has a lot paid junks and snaps which are not in synaptic. 
> 
[COLOR=#000000]I know about synaptic, but I need to show packages from my repo in gnome-software for other (non IT) users.[/COLOR]

You don't have to be an "IT user" to use synaptic, it is pretty easy to use. When I started using Ubuntu (10.04) I was a total newbie and I learned how to use synaptic immediately, at that time there was no Software centre or the likes. "IT users" probably use command line exclusively. :)

---

### Post by deadflowr on 2019-03-07
I wonder if the sublime ppa for xenial is a cause of issues in Software.
Try disabling that ppa, since it hasn't been updated for bionic (and no new updates for it anywhere in almost 2 years now.)
Since I assume you already have sublime installed turning off the ppa (if only temporarily) should not have adverse affects.


Oh, there is also no UbuntuGIS unstable ppa for bionic so turn that off.

---

