---
title: "Using Grub to Make Windows boot first, no wubi."
date: 2012-07-21
forum: New to Ubuntu
---

### Post by hhhlga89 on 2012-07-21
I installed ubuntu alongside Windows 7, but now when the PC boots and it gives the option to pick what you want to enter into (Windows or Ubuntu) ubuntu is the os that automatically runs (after the 10 sec wait they give you to decide which OS you want to use.) I want to know how to change it so that windows 7 boots up first, so I guess change the order, please.

I was informed by a site to download 'Grub customizer' on Synaptic. I tried downloading it (Grub) with the ppa:danielrichter2007/grub-customizer, 

the youtube video I used to try to download the ppa is
[http://www.youtube.com/watch?v=q13R-h8wEdY&feature=plcp](http://www.youtube.com/watch?v=q13R-h8wEdY&feature=plcp)

He also has the vid I was trying to use to change the boot order:
[http://www.youtube.com/watch?v=In0-_VF5Pe8&feature=youtu.be](http://www.youtube.com/watch?v=In0-_VF5Pe8&feature=youtu.be)

In first video I got to (2:46) but when I click 'Mark for installation' a popup comes up and says that the 'chosen action also affects other packages' and that I must remove 'grub-gfxpayload-lists','grub-pc','grub2-common'.

Assuming these are already installed, which i'm guessing this indicates, why can't i find this in my os? Are they essentially the same as what i am trying to install? is it ok if i opt to remove them?

If anyone is able to help or give me another method of acheiving what i'm trying to do id be grateful thanks. n sorry if i got anything confused on here, me-absolute beginner :) .

---

### Post by NikTh on 2012-07-21
> **hhhlga89 said:**
> I installed ubuntu alongside Windows 7, but now when the PC boots and it gives the option to pick what you want to enter into (Windows or Ubuntu) ubuntu is the os that automatically runs (after the 10 sec wait they give you to decide which OS you want to use.) I want to know how to change it so that windows 7 boots up first, so I guess change the order, please.


Hi , 
please open a terminal (ctrl+alt+t) and copy-paste these commands(one at time) . You must hit "Enter" after each command.
First command will ask you for password , write it and know that password will not appear (for security reasons)
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update 
sudo apt-get install -y grub-customizer
```Find and open grub-customizer , and read this Great HOW TO : [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Thanks

---

### Post by hhhlga89 on 2012-07-21
> **NikTh said:**
> Hi , 
please open a terminal (ctrl+alt+t) and copy-paste these commands(one at time) . You must hit "Enter" after each command.
First command will ask you for password , write it and know that password will not appear (for security reasons)
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update 
sudo apt-get install -y grub-customizer
```Find and open grub-customizer , and read this Great HOW TO : [http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Thanks
when i typed the first command it said

"You are about to add the following PPA to your system:
 This PPA contains the latest release of Grub Customizer.


 More info: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")
Press [ENTER] to continue or ctrl-c to cancel adding it"

when I pressed enter it now says

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.wtJGLAEZrE --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 59DAD276B942642B1BBD0EACA8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: key 3F055C03: "Launchpad PPA for Daniel Richter" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

do you know why this is so?

---

### Post by NikTh on 2012-07-21
> **hhhlga89 said:**
> when i typed the first command it said

"You are about to add the following PPA to your system:
 This PPA contains the latest release of Grub Customizer.


 More info: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")
Press [ENTER] to continue or ctrl-c to cancel adding it"

when I pressed enter it now says

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.wtJGLAEZrE --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 59DAD276B942642B1BBD0EACA8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: key 3F055C03: "Launchpad PPA for Daniel Richter" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

do you know why this is so?

This is Ok.. proceed with other commands.
You just imported the PPA that includes Grub-Customizer program.

---

### Post by hhhlga89 on 2012-07-21
> **hhhlga89 said:**
> when i typed the first command it said

"You are about to add the following PPA to your system:
 This PPA contains the latest release of Grub Customizer.


 More info: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer]("https://launchpad.net/%7Edanielrichter2007/+archive/grub-customizer")
Press [ENTER] to continue or ctrl-c to cancel adding it"

when I pressed enter it now says

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.wtJGLAEZrE --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 59DAD276B942642B1BBD0EACA8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: key 3F055C03: "Launchpad PPA for Daniel Richter" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

do you know why this is so?
darnell@darnell-Inspiron-560:~$ [COLOR=Purple]sudo apt-get update[/COLOR]
E: Type 'b' is not known on line 2 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list
E: The list of sources could not be read.
darnell@darnell-Inspiron-560:~$ [COLOR=Purple]sudo apt-get install -y grub-customizer[/COLOR]
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
darnell@darnell-Inspiron-560:~$

---

### Post by hhhlga89 on 2012-07-21
x

---

### Post by NikTh on 2012-07-21
> **hhhlga89 said:**
> darnell@darnell-Inspiron-560:~$ [COLOR=Purple]sudo apt-get update[/COLOR]
E: Type 'b' is not known on line 2 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list
E: The list of sources could not be read.
darnell@darnell-Inspiron-560:~$ [COLOR=Purple]sudo apt-get install -y grub-customizer[/COLOR]
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
darnell@darnell-Inspiron-560:~$

Hmm... it seems that you have a problem here. 

Run these commands (one at time) and post back the results of last command only. 

```
sudo add-apt-repository --remove ppa:danielrichter2007/grub-customizer
sudo apt-get update
```**Please put the results of last command inside [CODE] tags , by highlighting the text and click [SIZE=3]#[/SIZE] symbol on top of message pane.**
Thanks

---

### Post by hhhlga89 on 2012-07-21
> **NikTh said:**
> Hmm... it seems that you have a problem here. 

Run these commands (one at time) and post back the results of last command only. 

```
sudo add-apt-repository --remove ppa:danielrichter2007/grub-customizer
sudo apt-get update
```**Please put the results of last command inside ```
 tags , by highlighting the text and click [SIZE=3]#[/SIZE] symbol on top of message pane.**
Thanks
[CODE]sudo add-apt-repository --remove ppa:danielrichter2007/grub-customizer
[sudo] password for darnell: 
You are about to remove the following PPA from your system:
 This PPA contains the latest release of Grub Customizer.


 More info: https://launchpad.net/~danielrichter2007/+archive/grub-customizer
Press [ENTER] to continue or ctrl-c to cancel removing it

Error: 'deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main' doesn't exist in a sourcelist file
darnell@darnell-Inspiron-560:~$ clear

darnell@darnell-Inspiron-560:~$ software-center
2012-07-21 10:12:20,230 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-07-21 10:12:20,234 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-07-21 10:12:20,498 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-07-21 10:12:20,633 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-07-21 10:12:20,961 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Type 'b' is not known on line 1 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list
2012-07-21 10:12:21,996 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1420, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1350, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 169, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 237, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 504, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 270, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 443, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 432, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
darnell@darnell-Inspiron-560:~$ clear

darnell@darnell-Inspiron-560:~$ sudo add-apt-repository --remove ppa:danielrichter2007/grub-customizer
[sudo] password for darnell: 
You are about to remove the following PPA from your system:
 This PPA contains the latest release of Grub Customizer.


 More info: https://launchpad.net/~danielrichter2007/+archive/grub-customizer
Press [ENTER] to continue or ctrl-c to cancel removing it

Error: 'deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main' doesn't exist in a sourcelist file
Error: 'deb-src http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu precise main' doesn't exist in a sourcelist file

```

---

### Post by drs305 on 2012-07-21
The grub-customizer source is its own file(s):

/etc/apt/sources.list.d/danielrichter2007-grub-customizer-precise.list

so you could just rm or mv it somewhere else. You may have an associated .save file as well.

---

