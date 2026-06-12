---
title: "synaptic on network"
date: 2005-01-05
forum: Repositories &amp; Backports
---

### Post by tiiim on 2005-01-05
i try this again

i have to run synaptic over a network so i type the ip in manually it loads from all the servers but does not display the packages. if i do it from apt-get it starts to download but hangs on the 0% if the progress any suggestions please....

---

### Post by lockenkeyster on 2005-01-05
can you post what you have in /etc/apt/sources.list ?

---

### Post by tiiim on 2005-01-05
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

```

---

### Post by lockenkeyster on 2005-01-05
sources look okay...

have you tried sudo apt-get update ?

---

### Post by tiiim on 2005-01-05
[QUOTE=lockenkeyster]sources look okay...

have you tried sudo apt-get update ?[/QUOTE]
 hangs on 16% on first list

---

### Post by lockenkeyster on 2005-01-05
weird...

the only time that has happened to me (or anything like it) is when I had a bad network connection...

1) are you running a firewall on your machine? (firestarter, etc.)

2) what connects to the outside on your network? (router, ...)

---

### Post by tiiim on 2005-01-05
[QUOTE=lockenkeyster]weird...

the only time that has happened to me (or anything like it) is when I had a bad network connection...

1) are you running a firewall on your machine? (firestarter, etc.)

2) what connects to the outside on your network? (router, ...)[/QUOTE]
 no firewall

it could be the firewall on the outside network cos im at uni so it might be that end... if is then either i email if not i just wait to im at home to download ne software....

---

### Post by lockenkeyster on 2005-01-05
the network's connection to the internet is my best guess, although it sounds kind of strange... have you ever had problems downloading things through this setup before? Like, maybe a really big file?

---

### Post by tiiim on 2005-01-05
[QUOTE=lockenkeyster]the network's connection to the internet is my best guess, although it sounds kind of strange... have you ever had problems downloading things through this setup before? Like, maybe a really big file?[/QUOTE]
 nope not at all

---

### Post by fng on 2005-01-05
Do you need a HTTP Proxy to surf the web?

---

### Post by tiiim on 2005-01-05
[QUOTE=fng]Do you need a HTTP Proxy to surf the web?[/QUOTE]
 i do!

under networking i use dchp but on firefox i have to have a proxy for the web.

---

### Post by fng on 2005-01-05
Go to a terminal and type :
```
$ sudo export http_proxy="http://proxy.ubuntu.org:8080"
$ sudo apt-get update
$ sudo apt-get install program
``` 
That should do the trick.

The only problem is, that the http_proxy var will be gonna, everytime you reboor, logout, or, ...  It is best to put it into bash.bashrc so it would get loaded everytime you login.

---

### Post by tiiim on 2005-01-06
[QUOTE=fng]Go to a terminal and type :
```
$ sudo export http_proxy="http://proxy.ubuntu.org:8080"
$ sudo apt-get update
$ sudo apt-get install program
``` 
That should do the trick.

The only problem is, that the http_proxy var will be gonna, everytime you reboor, logout, or, ...  It is best to put it into bash.bashrc so it would get loaded everytime you login.[/QUOTE]
 i dont have an export command...

---

### Post by tiiim on 2005-01-06
root@timscomp:/home/tim # apt-get update
```
Err http://security.ubuntu.com warty-security/main Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/main Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Release
  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/source/Release  Could not resolve 'proxy.ubuntu.org'
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by fng on 2005-01-06
try it without sudo.

---

### Post by tiiim on 2005-01-06
[QUOTE=tiiim]root@timscomp:/home/tim # apt-get update
```
Err http://security.ubuntu.com warty-security/main Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/main Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://security.ubuntu.com warty-security/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/main Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/restricted Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Packages
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Release
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Sources
  Could not resolve 'proxy.ubuntu.org'
Err http://archive.ubuntu.com warty/universe Release
  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/main/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/restricted/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/warty/universe/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-powerpc/Packages.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/binary-powerpc/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/main/source/Release  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/source/Sources.gz  Could not resolve 'proxy.ubuntu.org'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/warty-security/restricted/source/Release  Could not resolve 'proxy.ubuntu.org'
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```[/QUOTE]
 works without sudo in normal console but still get message concerning the servers

---

### Post by fng on 2005-01-06
you need to replace proxy.ubuntu.org with your own proxy :)
and 8080 with your own proxy's port

---

### Post by tiiim on 2005-01-06
[QUOTE=fng]you need to replace proxy.ubuntu.org with your own proxy :)
and 8080 with your own proxy's port[/QUOTE]
 bingo!

---

### Post by allouch on 2009-04-25
I have a direct connection to the internet, via DSL, however my synaptic package manager keeps on asking for proxy, how can i deal with that ?

here is what i usually get

ali@ali-laptop:~$ sudo apt-get update
[sudo] password for ali: 
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://lb.archive.ubuntu.com](http://lb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'proxy.aub.edu.lb'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'proxy.aub.edu.lb'
W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://lb.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'proxy.aub.edu.lb'

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

and what are the last 2 errors?

---

### Post by BlackZurface on 2009-04-26
[FONT=Verdana, Arial, Helvetica][FONT=Verdana, Arial, Helvetica][SIZE=2][COLOR=midnightblue]Points2shop is a great, easy to use online shopping site for ALL types
of products! So many members have fallen in love with points2shop, its hard to keep track. Of course, you probably want to know more about it, so here goes:

Its EASY to earn! You can earn points by checking out our huge list of surveys, trials, and signup sites! All you have to do is complete an offer! Once you've completed your offer you will receive points. Those points will add up with each and every offer you do! 100 points = 1.00$ usd. With these points, you can then shop on [www.amazon.com]("http://www.amazon.com/") . Find the items you wish to purchase, and place an order through the points2shop website using your points. Your order will be processed within two business days and shipped to your house usually within a week. All for free! 

It has thousands of offers for members to complete daily. Offers can range anywhere from 15 - 4000 points! Lots of offers at 100 points (Thats 1.00 for EACH offer!), On top of that they have many exclusive offers you will not find on other cash sites because they are points only. Points2Shop has tons of advertisers, even advertisers that aren't on most GPT sites.

All you have to do is complete some offers. Then when they receive the confirmation from advertisers (Usually in 30 minutes!) Points2Sho will automatically credit your account with the points. You do NOT need a credit card to join the site. Members are cashing out DAILY. Some members have already earned $500.00 in prizes!

If you sign up now (FREE MEMBERSHIP ALWAYS) you can verify your phone (just type your phone number into the 'verify phone' section on our website, click send, and your phone will ring with an automated message giving you a confirmation code. Type that into website and click confirm.) you will get 250 points for verifying your phone (RIGHT AWAY!) 

You don't get gift cards like some other sites but direct access to millions of products available on Amazon.com . Once you get the points you need, cash out to get something you want! Order any product and it will be send directly without charging you any shipping costs at all! (for products over 25$) All you have to do is go to the website, click Amazon redemption, search for a prize you like (you can get ANYTHING that amazon has on their site as long as you have enough points) click add to cart, and confirm your order placement. We ship out orders DAILY. 

You can also earn cash (paid by check, paypal and amazon gift cards) just by referring your friends! 

1$ for each referral    CLICK LINK AND JOIN TODAY!!!!!!!!!!!
_[http://www.points2shop.com/index.php?ref=uin1239413942](http://www.points2shop.com/index.php?ref=uin1239413942)_
[/COLOR][/SIZE][/FONT][/FONT]

---

