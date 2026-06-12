---
title: "Downloading gimp"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by pennsylvania45 on 2013-02-10
I am trying to download gimp, but when I click on the link to go to the download center I get a popup that says "This link needs to be opened with an application" and asks me to choose an application.  I am totally new to ubuntu and have no idea what application I should use.  Can anyone help?  Thanks.

---

### Post by howefield on 2013-02-10
Why not install from the Ubuntu Software Centre ?

Much easier.

---

### Post by pennsylvania45 on 2013-02-10
> **howefield said:**
> Why not install from the Ubuntu Software Centre ?

Much easier.  Thats my problem. I click on the link to go to the software center and it says I need an application.

---

### Post by pennsylvania45 on 2013-02-10
Here is a screenshot.   Where it says "available on the software centre," I click that and the popup opens up.

Edit:  I see it now says to sent to Ubuntu software center.  It wasn't giving me that option before.  Ill try again and see if it works.

Edit: OK, it's working now.  I guess you can delete this entire thread.  Sorry about that.  Now I feel dumb. lol

---

### Post by howefield on 2013-02-10
After opening the Software Centre and searching for gimp, are you seeing something like in the screenshot, except where I have the remove button (because gimp is already installed), you would have an install button,

Alternatively you can open a terminal and type the following command,

```
sudo apt-get install gimp
```

---

### Post by howefield on 2013-02-10
Posted at the same time, try opening the Dash by pressing the Super (Windows) key or clicking on the top most icon in the launcher and search for Software Centre.

After a few letters have been type you should see the icon for the Software centre, click on it and search for gimp. Install from there.

---

### Post by pennsylvania45 on 2013-02-10
> **howefield said:**
> After opening the Software Centre and searching for gimp, are you seeing something like in the screenshot, except where I have the remove button (because gimp is already installed), you would have an install button,

Alternatively you can open a terminal and type the following command,

```
sudo apt-get install gimp
```

I tried that sudo apt command before but I got an error.  (But first I had to figure out how to open a command box).   I just tried it again and it worked.  Thanks

---

### Post by uzumakifahim on 2013-02-10
> **pennsylvania45 said:**
> Here is a screenshot.   Where it says "available on the software centre," I click that and the popup opens up.

Edit:  I see it now says to sent to Ubuntu software center.  It wasn't giving me that option before.  Ill try again and see if it works.

Edit: OK, it's working now.  I guess you can delete this entire thread.  Sorry about that.  Now I feel dumb. lol

From your screen shot, it seems that you are trying to download/install GIMP from apps.ubuntu.com. That's why when you are clicking on the button "Available on the Software Center", then it's asking like that.

Don't worry about that anymore, as you are new to Ubuntu. Just click on the Ubuntu Icon on the top left corner and write "Ubuntu Software Center". After opening this, write GIMP on the search box. You'll get result with desired GIMP. Simply select that, then you'll see a "install" button. Just click the install button.

Now GIMP is installed on Ubuntu and ready to be enjoyed.

---

### Post by deadflowr on 2013-02-10
> **pennsylvania45 said:**
> I tried that sudo apt command before but I got an error.  (But first I had to figure out how to open a command box).   I just tried it again and it worked.  Thanks

Personally, before I attempt to install any additional software on my system I run the Update Manager and get my system up to date.

You can do this in two simple ways.
Either use the gui update manager, open the top icon in the left-side launcher panel( this icon opens the Ubuntu menu system called dash) and type update. 
Depending on which version of Ubuntu you have it'll list either Software Updater(versions 12.10 and newer), or Update Manager(12.04LTS and older).
Software updater automatically reloads the package lists.
Update Manager will need to be refreshed, which is simple, just click on the 'check' box and let it run.
When it finishes updating the list, any new software updates will be listed. You can look over the list and see what's being updated, (and even click on the details to see why). Click on install to update.

The alternate method, is to use the terminal.(The command line)
simple do the same thing as before, but using command instead
```
sudo apt-get update
```
Again, this refreshes the package lists
```
sudo apt-get upgrade
```
This installs the updates

Sometimes packages won't install with the apt-get upgrade method(kernels as an example) So for this use
```
sudo apt-get dist-upgrade
```

I do this, for two reason. One to keep my system fresh, and two ( and really the real reason) to make sure the package I'm installing is the latest available for my system.

---

