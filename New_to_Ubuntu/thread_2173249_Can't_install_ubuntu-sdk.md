---
title: "Can't install ubuntu-sdk"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by tirab on 2013-09-08
Hi.

I've been trying to install the ubuntu-sdk with the command line commands given
on [http://developer.ubuntu.com/get-started/#step-write-app](http://developer.ubuntu.com/get-started/#step-write-app). However after using these ubuntu-sdk does not install
due to missing dependencies.

After I type in sudo apt-get update I noticed that the repository which sudo add-apt-repository ppa:ubuntu-sdk-team/ppa adds
cannot be found i.e. a page not found 303 error occurs.

Any ideas.
Thanks

---

### Post by claracc on 2013-09-09
No problem, finding this ppa repository [https://launchpad.net/~ubuntu-sdk-team/+archive/ppa](https://launchpad.net/~ubuntu-sdk-team/+archive/ppa) in launchpad, so perhaps the 404 not found error was a temporarily  disability of server.

Any case, have you read the specific notes for each ubuntu version?, I think this is important because they tell about conflicting dependencies, what ubuntu are you running?. 

Depending on what ubuntu version you run, there are packages that need to be upgraded too (notes speak about QT4 and QT5)

---

### Post by tirab on 2013-09-09
Hi. Thanks for the help. 

I am running ubuntu 13.04. When I run sudo apt-get update I get the following :

Failed to fetch [http://ppa.launchpad.net/ubuntu-sdk-team//ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-sdk-team//ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found

I Just tried this again now and the same message occurs.

Again, thanks for the help.

---

### Post by claracc on 2013-09-10
When I click on the url provided: [http://ppa.launchpad.net/ubuntu-sdk-team//ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-sdk-team//ubuntu/dists/raring/main/binary-i386/Packages) I also obtain the 404 not found error, it means that the requested software packages is not in the server.

The url you provided is a malformed one, the address is [http://ppa.launchpad.net/ubuntu-sdk-team//ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-sdk-team//ubuntu/dists/raring/main/binary-i386/Packages) , note there is some missing between ubuntu-sdk-team/ and /ubuntu , the possibilities are:

 ```
Index of /ubuntu-sdk-team
[ICO]	Name	Last modified	Size
[DIR]	Parent Directory	 	-
[DIR]	experimental/	22-Jan-2013 09:18 	-
[DIR]	ppa/	08-Jan-2013 20:33 	-
[DIR]	staging/	08-Jan-2013 18:49 	-
[DIR]	testing/	17-Jan-2013 09:58 	-
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80
```

As you can see you have to select experimental, ppa, staging or testing, depending of what repository you want to add. I think you have missed the ppa part.

Try to add again the repository in the correct way.

---

