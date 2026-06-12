---
title: "Problem installing GIMP 2.8 on Ubuntu 12.04."
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Vladimir Pavic on 2012-10-08
Dear friends, 
I have switched today from Ubuntu 10.04. to Ubuntu 12.04. It all works  fine - except for GIMP.  For some reason, I cannot have GIMP 2.8.  installed, neither by using Ubuntu Software Centre nor by pasting  commands into Terminal. What shall I do to have it installed?
Thank you in anticipation.

Vladimir

---

### Post by NikTh on 2012-10-08
Try to remove - purge the PPA you added , remove completely gimp and then add again the PPA (for 12.04) , update and then try to install GImp 2.8 

I assume the problem here is that you have updated gimp while you were in Ubuntu 10.04 (?)

---

### Post by audiomick on 2012-10-08
Are you trying to install the version of Gimp that is available from the software center? I can't check what the current version is, as this machine is still on 10.04.

Any rate, it seems that you are trying to install an older version than the one that would match 12.04. The dependencies that cannot be matched seem to be older than the versions of those packages that the OS has available.

---

### Post by Vladimir Pavic on 2012-10-09
*'Are you trying to install the version of Gimp that is available from the software center? I can't check what the current version is, as this machine is still on 10.04.'*

I presume that Ubuntu Software Centre (USC) for 12.04. has GIMP version 2.8. USC doesn't install any version. 

I wouldn't know how to delete previous PPA and install the new in Terminal. Any idea how to do it?

---

### Post by audiomick on 2012-10-09
> **Vladimir Pavic said:**
> I wouldn't know how to delete previous PPA and install the new in Terminal. Any idea how to do it?

Nope. Sorry.

If you are trying to install directly from the Software centre without having manually added a PPA, the you aren't using a PPA. The program would have been coming directly from the Ubuntu repositories (which are not PPA's.) PPA's are intended to allow users to provide software packages easily that have not (yet) been included in the main repository.
[https://help.launchpad.net/Packaging/PPA]("https://help.launchpad.net/Packaging/PPA")

If you have added a PPA, you can remove it via the "edit" menu in the software centre under "package sources"

---

### Post by NikTh on 2012-10-09
> **Vladimir Pavic said:**
> *'*

I presume that Ubuntu Software Centre (USC) for 12.04. has GIMP version 2.8. USC doesn't install any version. 

Hi , 

Gimp 2.8 is not available for 12.04 yet. You can add it by using an external PPA (and not official repositories). 

Gimp2.8 is available from the official repositories in Ubuntu **12.10** (will be released October 18th)

I presumed you added an external PPA and tried to install gimp from there cuz i can see newer packages will be installed and dependencies problems. 

If you take a look at attached image , you will see 
```
gimp : Depends : libgimp2.0 (<= 2.6.12-z) but 2.7.3-2010072701~ll is to be installed
```So either you added a PPA manually , or maybe you have proposed updates enabled. 

For PPA you can check software sources "Other software" 
```
gksudo software-properties-gtk
```and for precise-proposed updates , check if box is marked in the "Update" section. 

When you make any change then run in terminal 
```
sudo apt-get update
```Thanks

---

### Post by Vladimir Pavic on 2012-10-09
Somehow I fiddled around following your suggestions and i have got GIMP 2.8. INSTALLED! Works very well.

I am grateful to all of you :)

---

