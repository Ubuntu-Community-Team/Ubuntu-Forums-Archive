---
title: "New to 12.04LTS problems.."
date: 2012-08-30
forum: New to Ubuntu
---

### Post by CmdGabriel on 2012-08-30
Hi,
I just upgraded to the new 12.04LTS version and now i am completly lost.
I want to add a software source.... and wanted to choose configuration - administration (don't know if this is the right english translation) .. but instead of opening a admin window, the systems ask to install an expensive multiclientsupport utility...

Do I do somehting wrong or is ubuntu just screwed up..? ;)

Help! How to add a software source...


deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games


Thanks
Gabriel

---

### Post by lukeiamyourfather on 2012-08-30
Not sure how to do this with the graphical interface but you can do it in the terminal by editing the /etc/apt/sources.list file.

Google found this on the first try too.

[http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu](http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu)

---

### Post by NikTh on 2012-08-30
Hi , 
from graphical , you can add software sources via update manager. Click on Dash / Ubuntu icon up left and write **update manager** , open it click on **settings** and the go to **"Other Software"** and **add** your source. (the url you posted)

You can directly open the graphical window from terminal with this command 
```
gksudo software-properties-gtk
```Then you must run in terminal ```
sudo apt-get update
``` or close and open again the update manager to refreshing the sources.

Thanks

---

### Post by newb85 on 2012-08-31
NikTh is correct.

The Software Sources GUI is also accessible from the Software Center or Synaptic (if you install Synaptic).  In both of those, it's in the program's menu structure, so the easiest way to find it would be to use the HUD.

However, I've found that usually the quickest and easiest way to add a PPA is using the add-apt-repository command in the CLI.  It only needs one argument--the ppa you're adding--and takes care of GPG keys automatically.

Since it looks like you're experiencing the initial shock of switching from the Gnome2 interface to the Unity interface, I'll throw out a little advice.  Give Unity a chance.  There are many interfaces you can replace Unity with that will be more like what you're used to, and if, after you've tried Unity for a while, you still aren't satisfied, you can replace it.  

To this day, I'm very dissatisfied with the way Unity looks or the screen real estate it demands.  However, after using it a while, I find some some of its functionality indispensable.  The Dash keeps me from having to hunt a menu structure for the program I want and from having to hunt my folder structure for the file I want.  The HUD keeps me from having to hunt the programs' menu structures for the commands I want.  This I find unparalleled in any other DE.

---

### Post by CmdGabriel on 2012-09-01
Thanks all for your help. I added the software source now. 
But when I click in playdeb the systems asks, to open with which application.
i choose software center. softwrae center than says: Don find application.
Do i need to open the playdeb link with another application? (which one and where?)

---

### Post by uzumakifahim on 2012-09-01
> **CmdGabriel said:**
> Thanks all for your help. I added the software source now. 
But when I click in playdeb the systems asks, to open with which application.
i choose software center. softwrae center than says: Don find application.
Do i need to open the playdeb link with another application? (which one and where?)

You have added playdeb as a software source, that means from you'll use playdeb as a source of software. Playdeb is not a software itself. So, where are you clicking on playdeb? Please write your problem more clearly.

Thanks.

---

### Post by newb85 on 2012-09-01
If you're getting a game from PlayDeb's website, are following their [directions]("http://www.playdeb.net/updates/ubuntu/12.04/#how_to_install") exactly?  I'm not a gamer, so I'm afraid I can't offer any experience.

---

### Post by CmdGabriel on 2012-09-02
> **uzumakifahim said:**
> You have added playdeb as a software source, that means from you'll use playdeb as a source of software. Playdeb is not a software itself. So, where are you clicking on playdeb? Please write your problem more clearly.

Thanks.

Hi,
thanks for the help.
I am here: [http://www.playdeb.net/updates/Ubuntu/12.04/](http://www.playdeb.net/updates/Ubuntu/12.04/)

And I click on "Install now!"


... but I just tried again - and it worked. Don't know why today... ?

But thanks to all of you for the help!

Regards
Gabriel

---

### Post by newb85 on 2012-09-02
If your problem is solved, please mark the thread as solved.  At the top, "Thread tools>Mark thread as solved".

---

