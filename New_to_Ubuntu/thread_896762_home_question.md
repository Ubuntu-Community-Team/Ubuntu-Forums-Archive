---
title: "/home question"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by ags40 on 2008-08-21
Is it safe (and logic) to have one dedicated partition for /home AND share it with two or three different Linux distros?

Thank you, very much.

---

### Post by snowpine on 2008-08-21
> **ags40 said:**
> Is it safe (and logic) to have one dedicated partition for /home AND share it with two or three different Linux distros?

Thank you, very much.

My understanding is that it's safe to do this if you use different usernames for each distro. If you use the same username, you will have different versions of software trying to share the same configuration folders. 

This is just based on what I've heard, though, not personal experience.

---

### Post by Thelasko on 2008-08-21
It doesn't sound like a good idea to me.  Some software stores configuration files in the /home folder, and that could cause some issues.

As snowpine mentioned, you might be okay if each distro has a different username.

May I ask, why do you want to do this?

---

### Post by timcredible on 2008-08-21
you can do this, and you can use the same username on all of them (although the UID is what's important, not the name).  the only issue is when you use distros that use different versions of the same window manager (like if they both use gnome), then the config files stored in your home directory (.gnome, .gnome2, etc.) can be misunderstood.

i only do this if each distro uses a different window manager (gnome, kde, xfce, etc.) so that i don't have to worry about the above issues.

---

### Post by Thelasko on 2008-08-21
> **timcredible said:**
> you can do this, and you can use the same username on all of them (although the UID is what's important, not the name).  the only issue is when you use distros that use different versions of the same window manager (like if they both use gnome), then the config files stored in your home directory (.gnome, .gnome2, etc.) can be misunderstood.

i only do this if each distro uses a different window manager (gnome, kde, xfce, etc.) so that i don't have to worry about the above issues.

Other pieces of software store data there too.  While it may be advantageous for something like Firefox, you might have issues with other programs.  Off the top of my head, I know Miro's configuration files aren't compatible from version to version, and you will have a lot of problems if you don't have the same version installed on each distribution.

---

### Post by ags40 on 2008-08-21
> **Thelasko said:**
> It doesn't sound like a good idea to me.  Some software stores configuration files in the /home folder, and that could cause some issues.

As snowpine mentioned, you might be okay if each distro has a different username.

May I ask, why do you want to do this?

Well, is just to simplify things. Tks.

---

### Post by Vivaldi Gloria on 2008-08-21
> **ags40 said:**
> Is it safe (and logic) to have one dedicated partition for /home AND share it with two or three different Linux distros?

I have never tried this but I'd really doubt if it'd work. Looks like a permission/owner hell to me. 

Where is bodhi.zazen when you need him? ;)

---

### Post by altonbr on 2008-08-21
I've personally never had a problem with it. The only problem you might have is mixing preferences, say Firefox 3.0.1 in Ubuntu and Firefox 2.0.0.15 in an older distro.

---

### Post by bodhi.zazen on 2008-08-22
> **Vivaldi Gloria said:**
> I have never tried this but I'd really doubt if it'd work. Looks like a permission/owner hell to me. 

Where is bodhi.zazen when you need him? ;)

LOL

Yes it can be done and the best advice was given by snowpine, use a unique username for each distro.

If you use the same user name with each distro you may have one of two problems.

1. Ownership problems. Users are tracked by UID (numbers) not names. The first user in Ubuntu has an UID of 1000. This is not true of all distros, however. Fedora for example the first user has a UID of 500. 

Thus, even though you use the same user name, the UID are different.

Now you *could* do a number of things to fix that, including assigning a UID of 1000 in Fedora for example (just edit /etc/passwd and /etc/groups).


2. Conflicting config or . files. Usually this is not an issue, but as Thelasko pointed out with Firefox conflicts may occur.

========

Personally I advise a shared data drive and give each distro a /home on the root partiton. You then link (or bind) to home :

ln -s /media/data/music /home/user_name/music
ln -s /media/data/documents /home/user_name/documents

and on.

For permissions, make files on your data drive owned my a shared group or use very lax permissions (chmod 777 /media/data)

---

### Post by Thelasko on 2008-08-22
> **bodhi.zazen said:**
> 

2. Conflicting config or . files. Usually this is not an issue, but as Thelasko pointed out with Firefox conflicts may occur.


Actually, in Firefox it might be advantageous to share configuration files, as Firefox tends to have fairly standard configuration files across all versions.  You would then have all of the same settings and bookmarks across all of your operating systems.  The problems that might occur in Firefox, mostly involve plugins like Flash, Java, etc.

It's other software that I'm more concerned about.  My example of software that might be a problem is Miro.  Every time I update Miro, it tells me it can't read the configuration files because they're from another version.  I'm sure there is other software where this is be a problem.  It's the software you don't anticipate that's the problem.  There could be a reference to a piece of software that's installed in one directory in Ubuntu and another one in Fedora.  It's amazing what gets stored in your /home directory sometimes.

---

### Post by Paqman on 2008-08-22
I use a single home partition for multiple distros. As has been said, just create a different user for each distro to avoid any hassles.

I prefer to have a single /home partition because /home has a habit of growing (i'm mostly thinking of Wine) and I find it easier to budget for hard drive use if it's all in one place. If you were using it for data as well then bodhi.zazen's suggestion to link everything to a common data partition makes sense.

---

