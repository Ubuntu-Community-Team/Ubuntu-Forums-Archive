---
title: "How to contribute a game?"
date: 2010-06-12
forum: Packaging and Compiling Programs
---

### Post by JakeFrederix on 2010-06-12
I've made a lovely scrabble-clone with Java (will work anywhere).
GUI is to die for, checks words at runtime and marks wrong words, stores score in an encrypted file.

Then I even managed to make this into a .deb package, so that it can be installed. Turns up in your applications-menu under "games" with a fitting icon.

Now it's time for the last step; actually making it available to others.
How do I go about doing that?

I have my own website, so I am going to post it there, but the goal is to get it into the software-center.

Kind regards,
Jake

---

### Post by ChrisB111 on 2010-06-13
I am no developer but I would get yourself a launchpad account and place it in a ppa (personal package archive). This will allow users to install and run it while you are getting it placed in the main ubuntu repos. 

After that I run dry, try the [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide) on the ubuntu wiki.

Good Luck,

Chris

---

### Post by JakeFrederix on 2010-06-13
That seems a bit overkill. Isn't launchpad meant to be more of a CVS?
I already have the code and the .deb. All I'm looking for is a way to upload it in the ubuntu repository.

Jake

---

### Post by SevenMachines on 2010-06-16
launchpad ppa's stand for 'personal package archive' and do exactly what it says on the tin, somewhere to put your packages where others can use them too, its not a bad place to start with a new package. 
to get something uploaded to ubuntu you should look through the [REVU process]("https://wiki.ubuntu.com/MOTU/Packages/REVU") where someone with upload privileges can look over, advise on any changes, and upload to the repository when ready.
or you could try to get it included in debian, which ubuntu would get once it syncs with debian

---

### Post by JakeFrederix on 2010-06-16
Launchpad is very daunting. I wouldn't know how to upload anything to it.
You should know, I only switched to Ubuntu about a year ago. Still very much of a windows-mentality going on. I expect things to go "done" when I do "click" :-p

Kind regards,
Jake

---

### Post by SevenMachines on 2010-06-17
hi, if you've 'debianized' your source code then you really have done the difficult part, the rest isnt too bad.

1. [Get a launchpad account]("https://help.launchpad.net/YourAccount/NewAccount") (if you havent already)

2. Sign the code of conduct, this is on your launchpad homepage, where it says ubuntero: no.

3. Add the gpg key you used to sign your package (the link is on your main launchpad homepage)

4. Create your ppa (its again on your homepage, one click :) )

5. Upload your package (theres instructions on the ppa page you've just created). essentially this is just dput-ing your .changes file that was created by running debuild on your package, something like (for me)
$ dput ppa:sevenmachines/ppa <source.changes>

The source package you've uploaded will now automatically build into the ppa (assuming there are no packaging problems) and be automatically available to anyone who adds your ppa. sometimes it will build straight away, sometimes it will be delayed for perhaps hours if the build farm has higher priority packages to build

---

### Post by dino99 on 2010-06-17
an other place: [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

but Launchpad is the first choice ):P

---

### Post by JakeFrederix on 2010-06-17
Stuck at "How to get the fingerprint"

enter "gpg --fingerprint" in a terminal and ...
nothing appears.

---

### Post by SevenMachines on 2010-06-17
I'm guessing you haven't set up your gpg key yet, packages need to be signed. for launchpad they need to be signed by you and the key added to your launchpad profile. for a step by step guide on creating and uploading a gpg key see
[https://help.launchpad.net/YourAccount/ImportingYourPGPKey](https://help.launchpad.net/YourAccount/ImportingYourPGPKey)

---

### Post by JakeFrederix on 2010-06-17
running debuild on my .deb file gives me;

debuild: fatal error at line 630:
cannot find readable debian/changelog anywhere!
are you in the source code tree?

I used "debuild mazegen_3.1-0.deb"

Kind regards,
Jake

---

### Post by Umang on 2010-06-18
Debian packaging isn't easy at first and requires you to read up a lot before you can actually do it. Shortcuts to building a debian package don't really work.

Read the whole guide (hopefully you've run dh_make on it once). If you have, then you should have a debian/changelog file. Otherwise make one using `dch -v 3.1-0` (which will create a changelog entry for the 3.1-0 version and let you edit it).  Also, you can simply run `debuild` instead of `debuild mazegen_3.1-0.deb`. 

If you plan to submit to Debian/Ubuntu, then you will need to either have the debian revision (the part after the `-`) as '1'. It should reach Ubuntu within a release cycle after it is uploaded to Debian. If you are submitting only to Ubuntu, then your revision should be something like '0ubuntu1'.

If you plan to submit to Debian, you should try to take help from the guys at Debian (who are very helpful). In your case, get help for Java specific things from the Debian Java Packaging Team ([http://pkg-java.alioth.debian.org/](http://pkg-java.alioth.debian.org/)). They may have an IRC chanell also (you'll have to check). Things not related to Java should be asked at debian-mentors (on the mailing list or the #debian-mentors chanell on OFTC).

---

