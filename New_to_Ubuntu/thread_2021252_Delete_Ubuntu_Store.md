---
title: "Delete Ubuntu Store"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by Coops Jim on 2012-07-08
I am attempting to work with senior citizens in my community and educate them on using computers. As ubuntu is a great user friendly, simple OS, I decided to use it in this project. After working with test runs, It was great except for one thing, the Ubuntu store. The Ubuntu store is full of 'unnecessary' apps. I looked into creating a filter to remove them, all I could come up with is a custom repository, that option is however out of my league. So all I could see that was left to do was delete the Ubuntu store or at least disable it from usage.

---

### Post by ronnysingh on 2012-07-09
You didn't mention the version of Ubuntu being used by you. You can remove Ubuntu apps by following steps described on this page :

[https://help.ubuntu.com/10.04/add-applications/C/removing.html](https://help.ubuntu.com/10.04/add-applications/C/removing.html)


Ubuntu software center is the apps directory in newer versions of Ubuntu but you can'tt delete it. You simply don't need to install any app if you don't need it.

---

### Post by alphacrucis2 on 2012-07-09
> **Coops Jim said:**
> I am attempting to work with senior citizens in my community and educate them on using computers. As ubuntu is a great user friendly, simple OS, I decided to use it in this project. After working with test runs, It was great except for one thing, the Ubuntu store. The Ubuntu store is full of 'unnecessary' apps. I looked into creating a filter to remove them, all I could come up with is a custom repository, that option is however out of my league. So all I could see that was left to do was delete the Ubuntu store or at least disable it from usage.

Set the users up with non administrative accounts.

---

### Post by Paqman on 2012-07-09
The Ubuntu repositories are massive (because they come direct from Debian). Tbh, I've never heard of anyone considering having such a wide range of choices as a problem, because you can use search to focus just on what you actually want.

If you set the users up as non-admin accounts they'd be able to browse, but couldn't install anything. If you remove the package software-center (note the US spelling of centre) then they won't be able to launch it at all, but an admin user could still use the command line to install packages, and Update Manager will still work.

---

### Post by Peripheral Visionary on 2012-07-09
Or as an alternative you could replace the Software Center with the Synaptic Package Manager which requires root access to install and remove software.

---

### Post by black veils on 2012-07-09
here is an alternative way...

Bodhi Linux has it's own useful but simpler software centre, it is a website [http://appcenter.bodhilinux.com/](http://appcenter.bodhilinux.com/)

to enable the use of it, like in Bodhi, this is what the project leader posted:

> The Bodhi Linux App Center utilises APTURL technology to allow users one click install for popular Linux software. We also ship with the Midori browser by default. If you are using a different Debian based distro and wish to have APTURL function in the Midori browser, the following is what I do to make it work on Bodhi:

In your ~/.local/share/applications directory create a file called:

mimeapps.list

For it's contents paste in:

[Added Associations]
x-scheme-handler/apt=apturl.desktop;

Finally we need to create one more file. In your /usr/share/applications make a file called:

apturl.desktop

For it's contents paste in:

[Desktop Entry]
Type=Application
Name=AptURL
Categories=Network;
MimeType=x-scheme-handler/apt;application/apt;
Exec=apturl %u
Terminal=false
NoDisplay=true

Note that you will need root access (or sudo) to create this second file in the proper location.

Restart Midori and now clicking on APTURL links should work (make sure you also have APTURL installed).

~Jeff Hoogland




---

### Post by Paqman on 2012-07-09
> **Peripheral Visionary said:**
> Or as an alternative you could replace the Software Center with the Synaptic Package Manager which requires root access to install and remove software.

Software Centre requires root to install and remove, the difference between them is that Software Centre allows you to browse without root and Synaptic doesn't.

---

### Post by mastablasta on 2012-07-09
why not educate them about the software repositories and safe install of software from internet instead of removing it (censoring it)? 
 
i intend to educate my kids on safe use of internet (media) instead of removing access to it because it's filled with "useless" stuff.

---

### Post by Curtis6767 on 2012-07-09
> **Coops Jim said:**
> I am attempting to work with senior citizens in my community and educate them on using computers. As ubuntu is a great user friendly, simple OS, I decided to use it in this project. After working with test runs, It was great except for one thing, the Ubuntu store. The Ubuntu store is full of 'unnecessary' apps. I looked into creating a filter to remove them, all I could come up with is a custom repository, that option is however out of my league. So all I could see that was left to do was delete the Ubuntu store or at least disable it from usage.

Us seniors will do all right with just a little bit of guidance on a* simple OS* such as Ubuntu. By default Ubuntu comes with 100's of unnecessary apps and it isn't likely that a few more in the Software Center will overwhelm the seniors in your community. Besides, and as has already been pointed out, only those with administrative privileges can install new apps from the Software Center. 

Just remember that seniors have been confronted with and had to deal with and learn new things for longer than you've probably been around. They'll do just fine learning Ubuntu but they may take issue with your condescending attitude.

---

