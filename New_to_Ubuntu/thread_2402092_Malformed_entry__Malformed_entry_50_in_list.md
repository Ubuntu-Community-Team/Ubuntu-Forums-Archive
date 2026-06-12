---
title: "Malformed entry : Malformed entry 50 in list"
date: 2018-09-26
forum: New to Ubuntu
---

### Post by sazeev on 2018-09-26
Hello folks!Day 3 in Ubuntu mate 18.04.Need help.
Tried to install couple of apps like Dropbox. Now says error opening the cache with red circle in panel bar. Software boutique doesnt launch.
Tried to solve by checking previously asked threads but couldn't. 
Tried these in the terminal

sajeev@sajeev-Inspiron-N4050:~$ find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list
```

     1    # deb cdrom:[Ubuntu-MATE 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main multiverse restricted universe
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic main restricted
     6    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic-updates main restricted
    11    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic universe
    17    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic universe
    18    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic-updates universe
    19    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic multiverse
    27    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic multiverse
    28    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic-updates multiverse
    29    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://it-mirrors.evowise.com/ubuntu/](http://it-mirrors.evowise.com/ubuntu/) bionic-backports main restricted universe multiverse
    37    # deb-src [http://np.archive.ubuntu.com/ubuntu/](http://np.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
    38    
    39    ## Uncomment the following two lines to add software from Canonical's
    40    ## 'partner' repository.
    41    ## This software is not part of Ubuntu, but is offered by Canonical and the
    42    ## respective vendors as a service to Ubuntu users.
    43    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
    44    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
    45    
    46    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
    47    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
    48    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
    49    # deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) main
    50    deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) main
```

/etc/apt/sources.list.d/flexiondotorg-ubuntu-telegram-bionic.list

```
     1    deb [http://ppa.launchpad.net/flexiondotorg/telegram/ubuntu](http://ppa.launchpad.net/flexiondotorg/telegram/ubuntu) bionic main
     2    deb-src [http://ppa.launchpad.net/flexiondotorg/telegram/ubuntu](http://ppa.launchpad.net/flexiondotorg/telegram/ubuntu) bionic main
```

/etc/apt/sources.list.d/skype-stable.list
```

     1    deb [arch=amd64] [https://repo.skype.com/deb](https://repo.skype.com/deb) stable main
```

/etc/apt/sources.list.d/google-chrome.list
```

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
```

/etc/apt/sources.list.d/costales-ubuntu-anoise-bionic.list
```

     1    deb [http://ppa.launchpad.net/costales/anoise/ubuntu](http://ppa.launchpad.net/costales/anoise/ubuntu) bionic main
     2    deb-src [http://ppa.launchpad.net/costales/anoise/ubuntu](http://ppa.launchpad.net/costales/anoise/ubuntu) bionic main
```

/etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-bionic.list
```

     1    deb [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) bionic main
     2    deb-src [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) bionic main
```
sajeev@sajeev-Inspiron-N4050:~$ 


Any comments ?

---

### Post by deadflowr on 2018-09-26
You need the distribution name.
The entry
```
deb-src http://linux.dropbox.com/ubuntu main
```
is missing which archive to pull from
Distributions can be a release name such as bionic, or a release class like stable or unstable or beta.

You would need to know that, as I have no clue.

Further note, I'm not sure the line in question is any good anyway, as the deb-src denotes that it's a source code repository.
Which means you would only have access to the source code for the packages that repository provides, and you would have to compile and make the package yourself.
And I'm not sure if dropbox releases it's source code...
Easy solution would be to disable it by adding a # symbol to the front of the line.
So it reads as this
```
#deb-src http://linux.dropbox.com/ubuntu main
```

---

