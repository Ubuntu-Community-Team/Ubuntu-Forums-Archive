---
title: "Problem installing in Ubuntu 11.04 in virtual box"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by psam3 on 2011-10-09
I am getting this error message when trying to install Restricted Extras: 
```
installArchives() failed: 
Extracting templates from packages: 34%
Extracting templates from packages: 69%
Extracting templates from packages: 100%

Preconfiguring packages ...


Extracting templates from packages: 34%
Extracting templates from packages: 69%
Extracting templates from packages: 100%

Preconfiguring packages ...


Extracting templates from packages: 34%
Extracting templates from packages: 69%
Extracting templates from packages: 100%

Preconfiguring packages ...

Setting up tzdata (2011k-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 tzdata

Setting up tzdata (2011k-0ubuntu0.11.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128
```

I also got the same error when trying to install updates. I am running inside oracle virtual box, can this have something to do with the error?

Thanks

---

### Post by vajorie on 2011-10-10
The installation of tzdata seems to be a problem. Try a 

```

sudo dpkg-reconfigure tzdata
sudo apt-get -f install

```

I also found this, so I'm putting it here before I forget [http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on](http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on) (if you decide to do what it says, be careful and be ready for a bit of a long night)

---

