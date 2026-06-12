---
title: "Thunderbird 6"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alexvy13 on 2011-09-04
i deleted thunderbird 7 because hardly any themes or extensions work with it. How do i add thunderbird 6? I downloaded the tar.bz2 file from the mozilla site but i have no idea how to install it, could someone try it out and then tell me how to?
Thanks!

---

### Post by jbicha on 2011-09-04
Deleting the repository-installed Thunderbird and installing the version directly from Mozilla is neither recommended nor supported. Thunderbird 7 is intentionally in Oneiric since it will be final shortly before Ubuntu 11.10 is released (& Thunderbird 6 will then have known security vulnerabilities). Remember that Oneiric is in beta and is still not recommended for use on computers you are depending on to get stuff done.

I recommend you install the Add-on Compatibility Reporter [extension]("https://addons.mozilla.org/thunderbird/addon/add-on-compatibility-reporter/") (also available for Firefox). That will not help with some extensions which are binary extensions and need to be recompiled for every new Mozilla version. And there are some non-binary extensions which really are not compatible either.

---

### Post by alexvy13 on 2011-09-04
well i reinstalled thunderbird 7and set up two accounts but the "set up mail" icon wont go away.. i tried unity replace and restarting but it wont go away any ideas?

---

### Post by pressureman on 2011-09-04
I thought the "setup mail" icon was always there anyway...

I installed gnome shell to make it go away ;-)

---

### Post by cariboo on 2011-09-04
The setup mail option should disappear after an account is setup, see screen-shot.

---

### Post by Psychobudgie on 2011-09-04
Exact same behaviour here. I had assumed this was due to Thunderbird 7 still being in Beta.

---

### Post by mc4man on 2011-09-04
If you don't have libunity4 installed then it will remain on "Setup Mail.." (at least as seen here w/ Beta 1 install
By default libunity4 is not installed, nor a dep/recommend of thunderbird

[https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/832363](https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/832363)

---

### Post by Psychobudgie on 2011-09-04
> **mc4man said:**
> If you don't have libunity4 installed then it will remain on "Setup Mail.." (at least as seen here w/ Beta 1 install
By default libunity4 is not installed, nor a dep/recommend of thunderbird

[https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/832363](https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/832363)

libunity4 was removed from the repos on the 2nd September so will have to wait for a fix.

---

### Post by mc4man on 2011-09-04
> **Psychobudgie said:**
> libunity4 was removed from the repos on the 2nd September so will have to wait for a fix.

That it was, here is more current bug 
[https://bugs.launchpad.net/ubuntu/oneiric/+source/thunderbird/+bug/839154](https://bugs.launchpad.net/ubuntu/oneiric/+source/thunderbird/+bug/839154)

(if one wants it to work in the meantime then can be found here
[https://launchpad.net/ubuntu/+source/libunity/3.8.4-0ubuntu2](https://launchpad.net/ubuntu/+source/libunity/3.8.4-0ubuntu2)

---

### Post by alexvy13 on 2011-09-04
> **mc4man said:**
> That it was, here is more current bug 
[https://bugs.launchpad.net/ubuntu/oneiric/+source/thunderbird/+bug/839154](https://bugs.launchpad.net/ubuntu/oneiric/+source/thunderbird/+bug/839154)

(if one wants it to work in the meantime then can be found here
[https://launchpad.net/ubuntu/+source/libunity/3.8.4-0ubuntu2](https://launchpad.net/ubuntu/+source/libunity/3.8.4-0ubuntu2)


how exactly do i install this? I'm new to this and only know debs haha

also, i have libunity5..can i uninstall and then install this?

EDIT: i just tried it in synaptic and a whole bunch of stuff was about to be replaced...ill just wait for a fix..

---

### Post by alexvy13 on 2011-09-04
now i can't even get notifications :/ 
ithink i only get them when i have the thunderbird window open
is there a fix for this?
or a way i can minimize and hide it?

---

### Post by JonM33 on 2011-09-04
As long as the Lightning add-on works then I'm cool with it.

---

### Post by mc4man on 2011-09-04
> **alexvy13 said:**
> now i can't even get notifications :/ 
ithink i only get them when i have the thunderbird window open
is there a fix for this?
or a way i can minimize and hide it?
Don't believe I've seen that happen, (notification when TB isn't running),  I just start TB and min to the launcher

Atm the only thing(s) libunity4 does - 
initially on a B1 install the message drop down would always say 'setup mail', installing 4 allowed that to go 'normal'
If I then remove libunity4 the message dropdown stays normal, (expanded

Without libunity4, -  while I get OSD notifications, the message icon doesn't turn blue and no # shows on the TB icon in launcher. So just a very little to be gained after the initial fix of the message dropdown

---

