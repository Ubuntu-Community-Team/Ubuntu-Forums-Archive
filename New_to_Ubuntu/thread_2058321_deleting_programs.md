---
title: "deleting programs"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by jaedo71 on 2012-09-15
noob question:  How do I uninstall software in ubuntu?:popcorn:

---

### Post by mcduck on 2012-09-15
Same way as you install them, use the Software Center, Synaptic Package Manager, apt-get or which ever package management tool you prefer. :)

(With things installed outside of package management, it of course depends on how you installed it in the first place.)

---

### Post by oldfred on 2012-09-15
I prefer synaptic as it gives me the choice to not uninstall, if the list of other things is long.

Sometimes users uninstall a main or default application and then Ubuntu uninstalls just about everything. So check what else is uninstalled at the same time.

---

### Post by vasilbelarus on 2012-09-15
Synaptic really the best gui.
You can use > sudo apt-get remove package-name comand from terminal.

---

### Post by Bufeu on 2012-09-15
> **vasilbelarus said:**
> Synaptic really the best gui.
You can use  comand from terminal.
If you want to delete a program ***completely*** (including config files), use *sudo apt-get purge* instead.

---

### Post by critin on 2012-09-15
As has been said, uninstalling is easy any way you choose, but please read post #3 again carefully before deciding. 
> 
 **check what else is uninstalled at the same time.**

Other ways don't offer this option.  Synaptic is the smarter way if it's a default app.

---

### Post by josephmills on 2012-09-15
> **Bufeu said:**
> If you want to delete a program ***completely*** (including config files), use *sudo apt-get purge* instead.

lets not forget the -- before purge right ? 
```
sudo apt-get [COLOR="Red"]--[/COLOR]purge [COLOR="DarkOliveGreen"]remove[/COLOR] <name of app>

```


> noob question: How do I uninstall software in ubuntu?


here is a wiki 
[https://help.ubuntu.com/11.04/ubuntu-help/addremove-remove.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove-remove.html)

---

### Post by Bufeu on 2012-09-15
> **josephmills said:**
> lets not forget the -- before purge right ? 
```
sudo apt-get [COLOR=Red]--[/COLOR]purge [COLOR=DarkOliveGreen]remove[/COLOR] <name of app>

```


here is a wiki 
[https://help.ubuntu.com/11.04/ubuntu-help/addremove-remove.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove-remove.html)No, the command is *apt-get purge <package name>* (no "--").

---

### Post by GreatDanton on 2012-09-15
From the man pages 
>        --purge
           Use purge instead of remove for anything that would be removed. An
           asterisk ("*") will be displayed next to packages which are
           scheduled to be purged.  remove --purge is equivalent to the purge
           command. Configuration Item: APT::Get::Purge.


Regards.

---

### Post by newb85 on 2012-09-15
```
$ sudo apt-get purge <name of app>
```

and

```
$ sudo apt-get remove --purge <name of app>
```

and

```
$ sudo apt-get --purge remove <name of app>
```

are equivalent commands.

However,

```
$ sudo apt-get --purge <name of app>
```

would be invalid.

---

### Post by yoreei on 2012-09-15
I would also like to add that when you install software, most of the time some libraries that the program depends on are installed too but are not deleted when you remove the application with the methods from the other posts. To find and remove libraries which are no longer used type:
```
sudo apt-get autoremove
``` or install **bleachbit**
```
sudo apt-get install bleachbit
```
This is a GUI (a non-command-line interface with shiny buttons and images) program that helps you remove junk from you linux machine.

I also want to mention that you'd better not use two different package managers (apt-get synaptic etc). You should stick with only one of them. Everyone says this but I don't really know WHY you should.
 Anyways Ubuntu Software Center uses apt-get so just stick with it and **apt-get**

---

### Post by newb85 on 2012-09-15
> **yoreei said:**
> I also want to mention that you'd better not use two different package managers (apt-get synaptic etc). You should stick with only one of them. Everyone says this but I don't really know WHY you should.
 Anyways Ubuntu Software Center uses apt-get so just stick with it and **apt-get**

Synaptic, apt-get, and the Software Center are all compatible with one another.  I freely use all three--depending on what I'm doing and how much I know.  It's not usually a good idea to mix them with aptitude, which has a different method of storing system states.

---

### Post by HermanAB on 2012-09-16
Just bear in mind that unscrambling an egg is rather difficult...

I never uninstall anything.  If something is particularly annoying, I remove it from the menu system only.  Once a year, I install the latest version of Linux from scratch.

---

### Post by critin on 2012-09-16
> **HermanAB said:**
> Just bear in mind that unscrambling an egg is rather difficult...

I never uninstall anything.  If something is particularly annoying, I remove it from the menu system only.  Once a year, I install the latest version of Linux from scratch.


:popcorn:   Can I vote this as the best answer?

---

### Post by Scott Harrison on 2012-09-16
> **HermanAB said:**
> Just bear in mind that unscrambling an egg is rather difficult...

I never uninstall anything.  If something is particularly annoying, I remove it from the menu system only.  Once a year, I install the latest version of Linux from scratch.
Why?

Removing software isn't a difficult process, nor is time consuming, unlike reinstalling an OS every year? I'd have to spend an entire day rebuilding my main computer exactly the way I like it by doing that... Not at all preferable to the 10 seconds or so it takes to remove a program I no longer use/need.

---

