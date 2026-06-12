---
title: "Cant update Ubuntu"
date: 2018-09-19
forum: New to Ubuntu
---

### Post by nycap on 2018-09-19
Hi all. I have an old machine with Ubuntu on it that was last updated in 2013.  When I try to run the updater it tells me that untrusted packages would have to be installed and the updater quits.  Any suggestions will be much appreciated.

---

### Post by again? on 2018-09-19
When a release reaches end of life the repositories are archived.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] distro-info --all -rf --days=eol**
Ubuntu 4.10 "Warty Warthog" -4526
Ubuntu 5.04 "Hoary Hedgehog" -4342
Ubuntu 5.10 "Breezy Badger" -4178
Ubuntu 6.06 LTS "Dapper Drake" -3355
Ubuntu 6.10 "Edgy Eft" -3800
Ubuntu 7.04 "Feisty Fawn" -3623
Ubuntu 7.10 "Gutsy Gibbon" -3442
Ubuntu 8.04 LTS "Hardy Heron" -2688
Ubuntu 8.10 "Intrepid Ibex" -3065
Ubuntu 9.04 "Jaunty Jackalope" -2889
Ubuntu 9.10 "Karmic Koala" -2701
Ubuntu 10.04 LTS "Lucid Lynx" -1960
Ubuntu 10.10 "Maverick Meerkat" -2354
Ubuntu 11.04 "Natty Narwhal" -2153
Ubuntu 11.10 "Oneiric Ocelot" -1960
Ubuntu 12.04 LTS "Precise Pangolin" -512
Ubuntu 12.10 "Quantal Quetzal" -1588
Ubuntu 13.04 "Raring Ringtail" -1697
Ubuntu 13.10 "Saucy Salamander" -1526
Ubuntu 14.04 LTS "Trusty Tahr" 209
Ubuntu 14.10 "Utopic Unicorn" -1155
Ubuntu 15.04 "Vivid Vervet" -971
Ubuntu 15.10 "Wily Werewolf" -790
Ubuntu 16.04 LTS "Xenial Xerus" 944
Ubuntu 16.10 "Yakkety Yak" -427
Ubuntu 17.04 "Zesty Zapus" -250
Ubuntu 17.10 "Artful Aardvark" -63
Ubuntu 18.04 LTS "Bionic Beaver" 1679
Ubuntu 18.10 "Cosmic Cuttlefish" 301
```
If your release is a negative value then it's EOL...

You can do an [EOL Upgrade]("https://help.ubuntu.com/community/EOLUpgrades") by changing your repositories
but is easier to do a fresh install of the latest recommended release.

If your release is not EOL, post the complete output of.
```
sudo apt update && sudo apt upgrade
```

---

### Post by Autodave on 2018-09-20
Every 2 years, a long term service release is made. 18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

---

