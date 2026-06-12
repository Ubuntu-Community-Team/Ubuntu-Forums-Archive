---
title: "How to change default burning app in 12.04?"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by Pilot6 on 2012-06-07
In Nautilus there is no parameters for that any more. How can I change an application, which starts when I insert an empty DVD?

---

### Post by traditionalist on 2012-06-07
> **Pilot6 said:**
> In Nautilus there is no parameters for that any more. How can I change an application, which starts when I insert an empty DVD?

**1. **In Nautilus, right-click on any file with the desired filetype or extension, choose "Properties" from the context menu.
 **2. **The "Properties" dialog appears. Click on the "Open With" tab.
 **3.** Select the desired application for the given  filetype. All files with the same extension will now be opened with this  program by default.


[[IMG]http://img163.imageshack.us/img163/7137/custombackupisoproperti.th.png[/IMG]](http://img163.imageshack.us/i/custombackupisoproperti.png/)

---

### Post by Curtis6767 on 2012-06-07
System Settings/Details/Default Applications

Oops. That's not going to work for burning.

---

### Post by traditionalist on 2012-06-07
> **Curtis6767 said:**
> System Settings/Details/Default Applications


That will only work for some things. To change various other defaults you need to use Nautilus.

---

### Post by Pilot6 on 2012-06-07
> **traditionalist said:**
> That will only work for some things. To change various other defaults you need to use Nautilus.

In Nautilus there are no settings for that any more.

---

### Post by traditionalist on 2012-06-07
> **Pilot6 said:**
> In Nautilus there are no settings for that any more.

Did you read the reply I posted?  

[http://ubuntuforums.org/showpost.php?p=12006865&postcount=2](http://ubuntuforums.org/showpost.php?p=12006865&postcount=2)

If that does not work then there is something wrong with your nautilus.

---

### Post by Pilot6 on 2012-06-07
> **traditionalist said:**
> Did you read the reply I posted?  

[http://ubuntuforums.org/showpost.php?p=12006865&postcount=2](http://ubuntuforums.org/showpost.php?p=12006865&postcount=2)

If that does not work then there is something wrong with your nautilus.

Yes, I did. There is no problems with opening files.
But how can I 'right-click' an empty DVD?

---

### Post by traditionalist on 2012-06-07
> **Pilot6 said:**
> Yes, I did. There is no problems with opening files.
But how can I 'right-click' an empty DVD?

That is not a file that is a default action;

Go to "System settings",  "Details"; "Removable Media";

[[IMG]http://img84.imageshack.us/img84/3733/details019.th.png[/IMG]](http://img84.imageshack.us/i/details019.png/)

Choose what you want to do.

---

### Post by Pilot6 on 2012-06-07
Thanks. I just found it myself too.
Maybe you know where is the config file? Gnome changed a lot and it is hard to find things.

---

### Post by traditionalist on 2012-06-07
> **Pilot6 said:**
> Thanks. I just found it myself too.
Maybe you know where is the config file? Gnome changed a lot and it is hard to find things.

What config file?  There are config files for all sorts of things. What do you want to do?

You can edit your whole system if you wish ( although it is **[COLOR=Red]NOT[/COLOR]** advisable if you don't know what you are doing!) also, what file you use for various things depends on what system you are using.

A commonly used tool is Gconf editor  ( More info here;  [http://en.wikipedia.org/wiki/Gconf-editor](http://en.wikipedia.org/wiki/Gconf-editor)  )

To get it;
```
sudo apt-get gconf-editor
```As with any such configuration editor it must be used with great care and only if you know what you are doing.

---

### Post by mustafi05 on 2012-06-07
if you have installed k3b goto system settings>details>removable media> other media and select your removable media  and select k3b from dropdown menu of action. think that may solve your problem with simplicity.

---

### Post by traditionalist on 2012-06-07
> **mustafi05 said:**
> if you have installed k3b goto system settings>details>removable media> other media and select your removable media  and select k3b from dropdown menu of action. think that may solve your problem with simplicity.

No it wont, it merely confuses the issue. No programs are required to set up basic default actions.

Also, what you have posted is not what he wants to do. Please read the thread before you offer suggestions. Posting all sorts of irrelevant stuff just confuses people.

---

### Post by Pilot6 on 2012-06-08
I want to find the config file, where setting for default applications for removable media are stored. I looked in gconf, but did not find any.

---

### Post by ITisFraud on 2013-04-03
> **traditionalist said:**
> No it wont, it merely confuses the issue. No programs are required to set up basic default actions.

Also, what you have posted is not what he wants to do. Please read the thread before you offer suggestions. Posting all sorts of irrelevant stuff just confuses people.

No, he wants to know where the entry is stored.  So do lots of people that are reading this and don't have V 12.  There's a different answer to this for 10, etc.  The answer about settings works for 12, but not for other versions (and a lot of peeps will have multiple ones).

The only confusion was you when you told him to look at properties on a blank DVD and change the "Open with" entry, which it doesn't have.  The System->Settings...Removable Media isn't present in 10 and lower.  Wonderful, there's an applet for 12 that does that.  If someone would answer follow-on question about where that's stored, then people won't have to start a thread like this for every.stinking.version.

Unfortunately, Ubuntu development is starting to have a lot of Microshaft look and feel to it, imho.  Apps that don't do what you tell them to because they "know better", lone engineers deciding that they really would like something different impacting everyone for no good reason, etc.  This is real, real simple.  You stick a blank DVD into the system and the stupid Brasero DVD Copy applet comes up.  You're never going to use Brasero. How do you shut it up?

You use the removable media settings app in V 12.  Now, are we going to itemize how you do it in every version or is someone going to tell us where Nautilus stores the information?

---

### Post by ITisFraud on 2013-04-03
I found no way to do it from the GUI, but you can simply run this from the command line.  Pick the "media" tab.


nautilus-file-management-properties

---

### Post by d0006 on 2013-04-04
> **ITisFraud said:**
> I found no way to do it from the GUI, but you can simply run this from the command line.  Pick the "media" tab.
```
nautilus-file-management-properties
```
I thought I would try this but this command does not exist in 12.10 64-bit (live). Has it been deleted or do I have to install it?
[http://library.gnome.org/users/user-guide/stable/nautilus.html](http://library.gnome.org/users/user-guide/stable/nautilus.html) Doesn't work yet.
A search shows a man page but that is all.

Thanks

---

