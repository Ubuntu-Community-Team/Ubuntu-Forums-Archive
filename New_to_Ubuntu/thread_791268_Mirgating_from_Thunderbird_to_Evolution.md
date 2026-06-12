---
title: "Mirgating from Thunderbird to Evolution"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Metal Mick on 2008-05-12
Hi everyone,

I've been using Thunderbird for a few years as my mail client in Win XP.

I want to take the plunge and migrate to Ubuntu for the majority of things I like and need to do.

I also like to keep my emails and generally refer to them from time to time, although rarely do I go back more than a year.

Is there a way I can bring my emails into Evolution? Or similar, even T'Bird in Ubuntu would suffice.

All suggestions will be gratefully received.

Regards,

Michael P

---

### Post by quibbler on 2008-05-12
> **Metal Mick said:**
> Hi everyone,

I've been using Thunderbird for a few years as my mail client in Win XP.

I want to take the plunge and migrate to Ubuntu for the majority of things I like and need to do.

I also like to keep my emails and generally refer to them from time to time, although rarely do I go back more than a year.

Is there a way I can bring my emails into Evolution? Or similar, even T'Bird in Ubuntu would suffice.

All suggestions will be gratefully received.

Regards,

Michael P

Hi Michael,

Use Synaptic Package Manager to install Thunderbird.

System-Administration-Synaptic Package Manager

search for Thunderbird.

Regards quibbler

---

### Post by MaxVK on 2008-05-12
quibbler is on the money. Install Thunderbird, its miles better than Evolution in any case.

If you feel you need to have a calendar as well (a common requirement with email applications, you can always install Sunbird, which comes as an add-on for Thunderbird or a standalone application. Alternatively search for Rainlendar2, which is an excellent calendar.

Regards

Max

---

### Post by florus on 2008-05-12
You can copy all your old data into Thunderbird in Ubuntu. Look under Application Data in Windows and copy the relevant files to the .mozilla-thunderbird directory in Ubuntu, overwriting the existing files. You will need to make your hidden files visible for this.

---

### Post by gdkeene on 2008-05-12
Another advantage of Thunderbird is that if you dual boot you can access your emails from either Windows or Ubuntu.  Just put your Thunderbird profile on an NTFS partition (even the Windows one) and make sure your profile for both Windows and Ubuntu uses that folder for mail.  Voila, it doesn't matter if you're using Windows or Linux, any emails you download will be available in the other.

---

### Post by ugm6hr on 2008-05-12
> **gdkeene said:**
> Another advantage of Thunderbird is that if you dual boot you can access your emails from either Windows or Ubuntu.  Just put your Thunderbird profile on an NTFS partition (even the Windows one) and make sure your profile for both Windows and Ubuntu uses that folder for mail.  Voila, it doesn't matter if you're using Windows or Linux, any emails you download will be available in the other.

The "profile" folder is what needs to be copied, and accessing the same profile folder from dual OS is a good idea.  I actually use [http://www.fs-driver.org/](http://www.fs-driver.org/) to access my Linux partition profile from Windows.

The folder will be called something like wehplnb6u.default, which can be copied to /home/username/.mozilla-thunderbird/

---

### Post by MaxVK on 2008-05-12
> **gdkeene said:**
> Another advantage of Thunderbird is that if you dual boot you can access your emails from either Windows or Ubuntu.  Just put your Thunderbird profile on an NTFS partition (even the Windows one) and make sure your profile for both Windows and Ubuntu uses that folder for mail.  Voila, it doesn't matter if you're using Windows or Linux, any emails you download will be available in the other.

I spent quite a while doing this when I first migrated from Windows. I already had a data partition in Windows, so I left that where it was and used it as the location for the mail profiles. Both Windows and Ubuntu shared the mail (and the Firefox bookmarks for that matter) and everything went well.

In the end Windows went for good and I migrated the mail to my home folder, but its an excellent method if you dual boot.

---

### Post by Metal Mick on 2008-05-12
Hi all,

many thanks for the advice and opinions, especially regarding the relative worth of Evolution vs T'Bird.

I did have some knowledge of preserving emails in T'Bird but it's great to have a little more.

I think I'll be okay now. The files structure of Linux generally has me a little bit stumped, but the post here has helped tremendously.

Take care of yourselves,

Michael P

---

