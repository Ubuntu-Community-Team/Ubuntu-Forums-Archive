---
title: "Creating a Evolution 2.32 PPA for Lucid/Maverick"
date: 2010-11-01
forum: Packaging and Compiling Programs
---

### Post by ThomasNovin on 2010-11-01
I'm thinking about organizing/creating a Evolution 2.32 PPA for use in Lucid LTS and Maverick.

Any volunteers that would like to help? I have built hundreds of packages from source during the years, including Evolution, but never created a PPA.

---

### Post by dmaxel on 2010-11-03
I have no experience with any of this, but I just wanted to say that I'd approve this project 500%! This would definitely help me. Everything in Ubuntu is pretty up-to-date...Evolution is the only senior citizen of them all. ;)

---

### Post by Ulyssess on 2010-11-04
Mathieu Trudel has builds in his test ppa: [https://launchpad.net/~mathieu-tl/+archive/build-tests](https://launchpad.net/~mathieu-tl/+archive/build-tests). Maybe you can contact him to see if he can use some help. On the other hand, he does not have updated builds for all the evolution packages in his repo (e.g. evolution-rss is missing). So another option would be to create a ppa which depends on Mathieu's and only provides the packages which he skips...

---

### Post by ThomasNovin on 2010-11-24
Haven't had much time for this since my post.

I noticed however that 2.32 is released for Natty.

[https://bugs.launchpad.net/maverick-backports/+bug/653619](https://bugs.launchpad.net/maverick-backports/+bug/653619)

[http://packages.ubuntu.com/natty/evolution](http://packages.ubuntu.com/natty/evolution)

Maybe this can help..

---

### Post by PelPix on 2010-12-08
Hey guys.  I was looking around and I wanted you to know that I found a ppa that has the newest stable evolution builds for maverick!

[https://launchpad.net/~suraia/+archive/ppa](https://launchpad.net/~suraia/+archive/ppa)

ppa:suraia/ppa

---

### Post by ThomasNovin on 2010-12-09
Looks promising. I wonder how I can add this PPA without getting all the packages, just Evolution?

Has anyone tested this version? Upgrading possible from 2.30 without any problem?

---

### Post by ThomasNovin on 2010-12-09
> **ThomasNovin said:**
> Looks promising. I wonder how I can add this PPA without getting all the packages, just Evolution?

Has anyone tested this version? Upgrading possible from 2.30 without any problem?

Wtf... I installed it after doing a backup. Didn't do a dist-upgrade after adding the PPA, instead selected just the packages I wanted to upgrade from Synaptic.

Started evolution from command-line and noticed that the upgrade process (+ moving from ~/.evoltution to ~/.local/share/evolution) seems to have went fine.

---

### Post by ThomasNovin on 2010-12-09
evolution-mapi doesn't work

```
$ sudo aptitude install evolution-mapi
The following NEW packages will be installed:
  evolution-mapi{b} libdcerpc0{a} libexchangemapi-1.0-0{a} libgensec0{a} libldb0{a} libmapi0{a} libndr-standard0{a} libndr0{a} 
  libregistry0{a} libsamba-hostconfig0{a} libsamba-util0{a} 
0 packages upgraded, 11 newly installed, 0 to remove and 32 not upgraded.
Need to get 4.116kB of archives. After unpacking 16,5MB will be used.
The following packages have unmet dependencies:
  evolution-mapi: Depends: libexchangemapi-1.0-0 (< 0.31) but 0.32.0-0ubuntu1~maverick1 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     evolution-mapi [Not Installed]                     



Accept this solution? [Y/n/q/?] 

```

---

### Post by JulenLanda on 2011-01-08
> **ThomasNovin said:**
> I wonder how I can add this PPA without getting all the packages, just Evolution?

I just copied evolution packages from Michael Kuhn's PPA to an standalone evolution PPA.

[https://launchpad.net/~julenlanda/+archive/evolution](https://launchpad.net/~julenlanda/+archive/evolution)
ppa:julenlanda/evolution

---

### Post by raztus on 2011-01-26
I, too, am getting the issue while trying to install exchange-mapi:


```
The following packages have unmet dependencies:
 evolution-mapi : Depends: libexchangemapi-1.0-0 (< 0.31) but 0.32.0-0ubuntu1~maverick1 is to be installed
E: Broken packages
```

---
UPDATE:
I'm able to install exchange-mapi if I force the version on libexchangemapi down to 0.30 (in synaptic package manager).  Of course, then the plugin fails to load:

```
(evolution:13028): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory

(evolution:13028): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory

(evolution:13028): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-mapi.so': /usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-mapi.so: undefined symbol: exchange_mapi_connection_get_default_folder_id

(evolution:13028): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-mapi.so': /usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-mapi.so: undefined symbol: exchange_mapi_connection_get_default_folder_id
```

---

### Post by ThomasNovin on 2011-01-26
> **raztus said:**
> I, too, am getting the issue while trying to install exchange-mapi:


```
The following packages have unmet dependencies:
 evolution-mapi : Depends: libexchangemapi-1.0-0 (< 0.31) but 0.32.0-0ubuntu1~maverick1 is to be installed
E: Broken packages
```

I have tried it in other ways and I can say it's not even close to being ready for production / every day use. Ok for testing and if you want to help out but as user one should find other solutions for now.

---

### Post by jpborjas on 2011-02-03
I'm using Julen's PPA, and everything installed just fine, however, I don't have Evolution-Exchange available as a protocol. I installed that package individually from the command prompt, and it does install just fine, but Evolution is not seeing it. Any ideas?

---

### Post by tednix on 2011-02-14
I hope that someone can get this working for the less experienced user like me.

Evolution 2.30.3 in Ubuntu 10.10 has a major problem; it doesn't import business names from Google contacts.  This thrashes a lot of my contact information.
After posting a bug report I'm told that it was fixed in version 2.32.

---

### Post by timbo-lino on 2011-02-15
Is there still no ppa for lucid?
I can only the Maverick in this ppa:
[https://launchpad.net/~julenlanda/+archive/evolution](https://launchpad.net/~julenlanda/+archive/evolution)

---

### Post by ThomasNovin on 2011-02-15
I think those still interested just have to wait for Ubuntu 11.04 which will have Evolution 2.32.2. I haven't found any single PPA which holds all packages that you need for a fully working Evolution.

[http://packages.ubuntu.com/natty/evolution](http://packages.ubuntu.com/natty/evolution)

(Ps. If anyone want's to try Evolution 3 it is included in some Gnome 3 live CD and also probably Fedora 15)

---

### Post by ThomasNovin on 2011-02-16
> **JulenLanda said:**
> I just copied evolution packages from Michael Kuhn's PPA to an standalone evolution PPA.

[https://launchpad.net/~julenlanda/+archive/evolution](https://launchpad.net/~julenlanda/+archive/evolution)
ppa:julenlanda/evolution

These are now out-of-date.

I made a new copy to my PPA

[https://launchpad.net/~konstigt/+archive/evolution](https://launchpad.net/~konstigt/+archive/evolution)

Fresh copy from Michael Kuhn's PPA.

I have never created a PPA before so I think there is some kind of signing key missing (you have to accept unsigned packages) but it works for me at least..

---

### Post by ThomasNovin on 2011-02-16
> **ThomasNovin said:**
> These are now out-of-date.

I made a new copy to my PPA

[https://launchpad.net/~konstigt/+archive/evolution](https://launchpad.net/~konstigt/+archive/evolution)

Fresh copy from Michael Kuhn's PPA.

I have never created a PPA before so I think there is some kind of signing key missing (you have to accept unsigned packages) but it works for me at least..

Now evolution-mapi actually works also!

---

### Post by ThomasNovin on 2011-02-17
My PPA was missing sqlite3 so a dist-upgrade would not be successful before (failed dependency). This is fixed now.

Edit: also libgtkhtml was missing, this was also fixed a few minutes later.

---

### Post by daprakas on 2011-02-19
Thanks a lot thomas.. I am using ur ppa for maverick it was hell without your ppa..

Can you please let me know why the calendar free/busy time doesnt work in mapi or how to make it work..

Also evolution-exchange doesnt show up in the server type also, Please let me know how to fix this two...

---

### Post by ThomasNovin on 2011-02-26
> **daprakas said:**
> Thanks a lot thomas.. I am using ur ppa for maverick it was hell without your ppa..

Can you please let me know why the calendar free/busy time doesnt work in mapi or how to make it work..

Also evolution-exchange doesnt show up in the server type also, Please let me know how to fix this two...

Free/busy I don't know, is it supposed to work? Does it work in other versions?

Have you installed the package evolution-exchange?

---

### Post by daprakas on 2011-02-27
Yes i have installed evolution-exchange , i think evolution mapi calendar should suppose to work on this release. Do you mean to say it never worked or you aren't the user of that feature ?

---

### Post by daprakas on 2011-02-27
Missing plugin build has some issues


(evolution:3042): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory

(evolution:3042): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory
** (evolution:3042): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:3042): DEBUG: MAPI listener is constructed with 1 listed MAPI accounts 

(evolution:3042): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory

---

### Post by ThomasNovin on 2011-02-27
> **daprakas said:**
> Missing plugin build has some issues


(evolution:3042): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory

(evolution:3042): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory
** (evolution:3042): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:3042): DEBUG: MAPI listener is constructed with 1 listed MAPI accounts 

(evolution:3042): evolution-plugin-lib-WARNING **: can't load plugin '/usr/lib/evolution/2.32/plugins/liborg-gnome-exchange-operations': libexchange-storage.so: cannot open shared object file: No such file or directory

Yep, looks like a problem. I don't use these features myself but anyone that needs it could contact the person who really created the packages, maybe it could be fixed.

Email contact could be found at [https://launchpad.net/~suraia/+archive/ppa/+packages](https://launchpad.net/~suraia/+archive/ppa/+packages), clicking any Evolution package.

---

### Post by daprakas on 2011-02-27
>>Yep, looks like a probl
Sad!!..  This ppa is totally broken for evolution exchange, MAPI without calendar is equal to IMAP+.. Good luck evolution and other ppa's none of them works for Exchange as a complete feature. They are all IMAP & POP only...

---

### Post by ThomasNovin on 2011-02-28
> **daprakas said:**
> >>Yep, looks like a probl
Sad!!..  This ppa is totally broken for evolution exchange, MAPI without calendar is equal to IMAP+.. Good luck evolution and other ppa's none of them works for Exchange as a complete feature. They are all IMAP & POP only...

You get what you pay for...

Natty will be released in 2 months, it will have this release, probably fully-working.

---

### Post by daprakas on 2011-03-02
free = bugs :))..

Nice quote..

---

### Post by ThomasNovin on 2011-05-03
I have removed my PPA because Natty is now released with the same version (but more complete and works better).

Also the original PPA from Michael Kuhn is emptied of Evolution-files.

---

