---
title: "Developing with Dajaxice on Ubuntu 10.04"
date: 2014-01-26
forum: Programming Talk
---

### Post by tobiz on 2014-01-26
I'm trying to develop a python application using Eclipse under ubuntu 10.04 with the goal of running the final app on a Raspberry Pi. I'd like to use Python-Dajaxice but have found that on 10.04 there are basic problems having installed it from the standard repositories.  Basically the python import of "from dajaxice.decorators import dajaxice_register" says that dajaxice_register is unresolved, in fact it's not in the dajaxice.decorators module (I've inspected the source).  Question is could I install a later version of dajaxice up to any version that works with the python version on 10.04; I guess later versions of dajaxice do include dajaxice_register.  I don't want to upgrade python on my development machine as it is also my main desktop machine (which has all the updates applied) since doing so is likely to lead to other untold problems I don't want (and I'm quite happy running 10.04 for all the daily chores of life these days).  Help would be much appreciated.

---

### Post by TheFu on 2014-01-26
Can't really help with python dependency issues. I am not a python dev. Being on a non-supported platform is dangerous to you and those computing devices on the same LAN.

10.04 desktop has been de-supported for years. Anything you'd do to make it work would be all on you.

10.04 server has a little over another year of support left. I'll be migrating those machines to 12.04 server in the next few months.  "Support" means that security patches are back ported, but new features are NOT included. Support is about stability first so any other changes are avoided.

Stock 12.04 desktop gets 5 yrs of support and you CAN run a different GUI, if that is the core issue - something like XFCE is close to what 10.04 has. That is what I do (not a fan of Unity) At the login screen, just choose which GUI you want - the previously selected GUI will be the default.

OTOH, if the target for this code is a 10.04 server, then you really are stuck, unless you use the python equivalent of Ruby's RVM or Perlbrew to manage the complete python environment.  Doing so **is** a best practice in those other languages. Modifying the built-in language version is a dangerous thing to other packages on the box, after all.

Hope this helps, but it probably did not. Sorry.

---

### Post by tobiz on 2014-01-26
TheFu,
Thanks for the response.  My ultimate gaol is to run the python app on a Raspberry Pi, I just use ubuntu desktop for 'light' development.  Since the LAN is mine the issues re security are understood and under control.  My experience of upgrading is that it can lead to problems and now with ubuntu upgrading means a serious change to the gui; not what I want at the moment.  My preference to an in-situ upgrade is just have another machine, when it's bedded in transfer the data and retire the old one.  Not the cheapest policy but avoids many of those awkward moments when "why doesn't that work?" and "where's that gone!".  It rather sounds like my best option is to abandon ubuntu/Eclipse and develop directly on the RasPi; not nice but leaves my 10.4 in a clean state.

---

