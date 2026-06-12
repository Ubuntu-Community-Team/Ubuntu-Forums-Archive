---
title: "User Accounts - Can you limit access?"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by missmable on 2012-01-26
I set up a standard user account that does not have administrator privileges. Is there a way to control what changes a standard user can make to Ubuntu? Its running on several shared computers and I don't want them to install programs, change the desktop background, download files, saves files onto the computer, or access the internet because people have been messing with the computers. Is this possible?

---

### Post by Paqman on 2012-01-26
> **missmable said:**
> I don't want them to install programs, change the desktop background, download files, saves files onto the computer, or access the internet

Ok, first one is easy: Only users with admin privileges can install software.

After that, it gets tricky. It sounds like you want to operate in some kind of "kiosk mode" but without even having internet access, which is very unusual. 

It might be easier to get an idea of what you want by turning the question round: what exactly do you envisage the users using the machine for?

---

### Post by sudodus on 2012-01-26
I suggest that you let them use ***the guest session*** instead of an own user account. What is installed in the guest account will be deleted when logging out from it, so people can download files and create files only temporarily (while they are logged in).

But you'd better check that they can do what they need to do with the very limited guest account! Otherwise you can modify the user account(s) via the menu entry for user accounts.

---

### Post by mcduck on 2012-01-26
Depends on what desktop  you are using.

Gnome does have options for all those purposes, allowing you to lock pretty much any setting and to disable user from saving files. You'll have to do that manually through dconf, though, as Gnome's graphical tool for the purpose (Pessulus) hasn't been updated to GSettings/GTK3 yet...

As far as I know KDE should also have pretty good tools for creating Kiosk setups.

---

### Post by sudodus on 2012-01-26
... but I do not know how to log into guest session without logging into a regular account first :-/

Edit: In this link [[COLOR="Red"]_Customize guest session_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1566078") I found

"Up to Ubuntu 11.04 the guest session feature was provided by gdm-guest-session, an extension to the GNOME Display Manager (GDM) which was the default display manager in Ubuntu. This changed in Ubuntu 11.10, where LightDM is the default display manager, and you can now launch a guest session through a built-in LightDM feature. Unlike before you don't need to first log in as a regular user; ***a guest session in Ubuntu 11.10 can optionally be launched directly from the login screen***."

---

### Post by missmable on 2012-01-27
We installed Ubuntu on our work computers to use a particular software, FIJI (a.k.a. ImageJ), because it was far too spastic when run on Windows. We have a number of undergraduates who work in our lab and they're often up to no good on those computers - playing around on the internet, downloading all kinds of junk, etc. This is why I want to limit what they can do. 

They can do what they need to do for work with just FIJI and LibreOffice Calc. If they need to access the internet, it's only to download our files on one particular website. Maybe they can check their school email too. I don't mean to be draconian but they have screwed up computers in the past, compromising the work of anyone else who uses those computers. 

Does this help?

---

### Post by sudodus on 2012-01-27
Well, it should be easy to keep the students from surfing on the internet. Don't connect the computers to the internet! I mean no wired ethernet connection and no built-in wifi chip ;-)

For the rest of the demands, I suggest that you try using the guest session, and see if that would be at least approximately what you want. In that case, maybe you could use the link from my previous post to tweak it.

---

### Post by missmable on 2012-01-27
The problem with that is, people don't always log out when they leave. So they may save something on the computer, leave, and someone else will come along and log out, deleting everything. Is there a way to make them log on using their university email account? That way, they'd have to log out so they don't risk other messing around in their name.

---

### Post by missmable on 2012-01-27
Could we just limit them to a couple of websites?

---

### Post by sudodus on 2012-01-27
> **missmable said:**
> The problem with that is, people don't always log out when they leave. So they may save something on the computer, leave, and someone else will come along and log out, deleting everything. Is there a way to make them log on using their university email account? That way, they'd have to log out so they don't risk other messing around in their name.

I see what you mean, and I think you need to get a regular user account tweaked. This should be fairly easy with the built-in tools for ***User and Group administration*** in Ubuntu 10.04 LTS which is supported until April 2013.

> **missmable said:**
> Could we just limit them to a couple of websites? I guess so, maybe by configuring the firewall or some similar software on the computers or in the LAN. I have not done that myself, but I think many people here at the Ubuntu Forums know how to do such things. Let us hope someone comes in and tell us about that :-)

---

