---
title: "Adding things into the user folder with a DEB package? - Ubuntu"
date: 2010-08-28
forum: Packaging and Compiling Programs
---

### Post by hakermania on 2010-08-28
Hi all.
I know some basic things about building a DEB package, but I haven't really understand this single thing: How to add staff into the current user's folder, known also as $USER :lolflag:

Well, to the point now, I want to add some staff to the .config folder of the user, but when you create into the deb package the folders
/home/$USER/.config/staff_here
it actually creates a new folder at home directory with the name $USER (not the value of $USER variable)
So...I asked somewhere this question and i got as reply that you must create these directories on the first app run... But this is a bit mad, isn't it? If there are a lot of files that have to go to .config and not only some simple unix scripts, then you have to copy them from somewhere, which means that you have to place them somewhere temporarily and then move them from there to /home/$USER/.config....right?

But, the DEB package is being run with root privileges and the program as simple user privileges, how would I move the temp files (placed in places that only root can touch) into the .config folder with simple user privileges????:confused::confused:

thx for any replies in advance..My actual question is How to add some staff into the /home/$USER/.config using a DEB package. Thx

---

### Post by Dies on 2010-08-28
> **hakermania said:**
> 
So...I asked somewhere this question and i got as reply that you must create these directories on the first app run... But this is a bit mad, isn't it? 
No, it's not "mad". It's the correct way to do things.

> **hakermania said:**
> 
My actual question is How to add some staff into the /home/$USER/.config using a DEB package.
You should never do this.

---

### Post by hakermania on 2010-08-28
Where can I temporarily store the staff? Then the app on its first run will move these temp files into the .config ?

---

### Post by Bachstelze on 2010-08-28
> **hakermania said:**
> Where can I temporarily store the staff? Then the app on its first run will move these temp files into the .config ?

/usr/share, and you would not move them, you would copy them.  What if several users want to use the program?

But anyway, initial configuration is what default settings are for.  The dotfiles should only contain settings that override the defaults.

---

### Post by hakermania on 2010-08-28
Interesting...nice...Thank you!

---

