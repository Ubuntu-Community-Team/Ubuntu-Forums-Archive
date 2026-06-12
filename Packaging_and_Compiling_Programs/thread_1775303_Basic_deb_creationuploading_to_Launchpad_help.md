---
title: "Basic deb creation/uploading to Launchpad help"
date: 2011-06-04
forum: Packaging and Compiling Programs
---

### Post by inameiname on 2011-06-04
Okay so here is my dilemma. Firstly, I am not using source code, but binaries/custom debs and repacking them into the correct format to be able to upload them to a PPA. After several attempts, the following procedure does seem to work, however I do have two issues: 1. versioning needs some fixing (posted another thread about that on here though) 2. size if the finished deb shown on the PPA is no where near what it should be

Once again, this will successfully upload, so that isn't the issue. Its getting all of the juicy bits to transfer into the deb:

```

    1. Ensure I have generated, published, imported, and verified my PPA OpenPGP key
    2. Create a package directory named: ${PACKAGENAME}-${VERSION}~${YOURUNIQUEVERSIONNAME}
    3. Create a subdirectory in the package directory, named: ${PACKAGENAME}
    4. Create subdirectories/files in a subdirect of package direct. (if want /usr/bin/footool, "mkdir usr", "mkdir usr/bin" and "cp footool usr/bin").
       If using a current deb file, just copy all its subdirectories into ${PACKAGENAME}, excluding its DEBIAN subdirectory (leave for later)
    5. Compress the package directory into a tar.gz file, rename it: ${PACKAGENAME}_${VERSION}~${YOURUNIQUEVERSIONNAME}.orig.tar.gz
    6. cd /path/to/package directory
    7. dh_make -n -s -e your@emailaddress.com # this will create the DEBIAN subdirectory for the new deb being made
    8. dpkg-depcheck -d ./configure    # find dependencies, and once found, add to section in subdirectory DEBIAN/control in the package directory
    9. Edit changelog, copyright, control, rules, manpage (if want to adhere to policy, ensure name & email are = what's on record for your gpp key)
       Also be sure to change 'unstable' to the correct '${UBUNTUVERSION}'
       If using a current deb file, ensure the original DEBIAN subdirectory contents are put into the new 'DEBIAN' subdirectory
       If using a current deb file/making your own, create a debian/${PACKAGENAME}.install file, make it executable, and add the following:
        #!/usr/bin/make -f
        # add more lines like below when necessary
        <put_whatever_dirctory(s)_here>/ /
    10. debuild (is a wrapper which approx. equals: dpkg-buildpackage + lintian or linda + debsign) (choose one: 'debuild -S' is Launchpad-friendly)
        debuild # requires sig, builds tar.gz & deb, creates .changes & build files (rejected on Launchpad: must be source only to work)
        debuild -S    # requires sig, builds tar.gz, creates .changes & .build files (accepted on Launchpad: but not perfect)
        debuild -b # requires sig, builds deb, creates .changes & .build files (rejected on Launchpad: missing tar.gz)
        debuild -i -us -uc -S # no sig required, builds tar.gz, creates .changes & .build files (rejected on Launchpad due to missing sig)
        debuild -i -us -uc -b # no sig required, builds deb, creates .changes & .build files (rejected on Launchpad: missing tar.gz/sig.)
        dpkg-buildpackage -rfakeroot # requires sig, builds tar.gz & deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc # no sig required, builds tar.gz & deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -S # requires sign, builds tar.gz, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc -S # no sig required, builds tar.gz, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -b # requires sig, builds deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc -b # no sig required, builds deb, creates .changes, no .build (rejected on Launchpad)
        fakeroot debian/rules clean && fakeroot debian/rules binary # builds deb only
        lintian -Ivi ../yourpackage.changes # optional, to check the new deb package
    11. dput ppa:<yourppausername>/<yourppaname> <package.changes>    # optional, to upload to a Launchpad PPA

```I am fairly certain its step number 9 that is giving me issues, as I am using what might be called a workaround hack to transfer all the stuff from the old deb into this new one. For some reason its just not working. 

debuild -S must ignore the "override_dh_autio_install:" section of the DEBIAN/rules file.

Anybody?


UPDATE: 14 June 2011 - updated the above steps I use. Works for the most part, but I'm currently having trouble with '.orig.tar.gz' files with '.so' library files.

UPDATE: 18 June 2011 - for the most part, I've figured things out. Look at the last posting of mine to show how I fixed the few issues I was having. Although, not really fixed; more, finding a workaround. Good enough for now.

---

### Post by inameiname on 2011-06-05
Bump.

---

### Post by uRock on 2011-06-05
Moved to *Packaging and Compiling Programs*.

---

### Post by inameiname on 2011-06-05
Oh sorry, I didn't even know there was a specific section for people with programs like this.

---

### Post by SevenMachines on 2011-06-05
As far as i know theres no way to upload manually pre-made deb binaries to a launchpad ppa. They're designed to take the source changes files generated by debuild and build from fully packaged 'debianized' source.

---

### Post by inameiname on 2011-06-06
Actually using my method above, it works, but just doesn't follow the /debian/rules addition that I added. As such, I was able to find how to trick it into uploading binaries without a source code, but it just doesn't quite turn out right. 

Oddly enough, trying 'dpkg-buildpackage -rfakeroot' instead of 'debuild -S', which does generate all the required files, including the '.changes' file, which is what gets looked at correctly in Launchpad but does not generate the proper deb file on my computer as it creates that on its servers, I found using 'dpkg-buildpackage -rfakeroot' does in fact build the deb the way I want, fully; although, it fails uploading to Launchpad. I don't know why one works, but not the other.

---

### Post by inameiname on 2011-06-08
Bump.

---

### Post by SevenMachines on 2011-06-08
Still a little confused at what you're trying to do here, but it does look like you are uploading package source, not a pre-packaged binary as i first thought, which was confusing. Packaged source can include prebuilt binaries. 

By DEBIAN/control you should mean debian/rules? when adding the lines
```
override_dh_auto_install: 
            cp -fv -R ${PACKAGENAME}/* $(CURDIR)/debian/${PACKAGENAME}/             
chmod -fv -R 755 $(CURDIR)/debian/${PACKAGENAME}/*
```
Difficult to tell without seeing your directory structure, build output, and so on whether this copy will work or not though.

---

### Post by inameiname on 2011-06-09
Understandable. Let me see if I can break it down for you just what I am asking. (FYI, yes, I meant to say /debian/rules, not /debian/control, and I updated the above to reflect that). And one thing to note is using 'debuild -S', it is accepted on Launchpad, but fails to make the deb with all the stuff I want in it, while using 'dpkg-buildpackage -rfakeroot', it does include all the stuff I want and actually makes the deb for me to see, but it fails to upload to Launchpad. Following the steps above, here is an example of what I am talking about:

```

1. Make a new folder, name it: foo-0.1~ppa1.
2. Inside foo-0.1~ppa1, make a new folder, name it: foo
3. Create a script called foo.sh, set it as executable, and put inside the subfolder: foo
4. Compress the new folder in tar.gz format: foo-0.1~ppa1
5. Rename the tar file: foo-0.1~ppa1.tar.gz to: foo_0.1~ppa1.orig.tar.gz
6. Go back to the new folder: foo-0.1~ppa1, 'cd' into it, and run the terminal command: dh_make -n -s -e your@emailaddress.com
7. Now inside that new folder: foo-0.1~ppa1, there is a 'debian' folder. Go into it, and edit changelog, copyright, control, rules, manpage, whatever
8. When editing the debian/rules file, add this at the end:

override_dh_auto_install:
    cp -fv -R foo/* $(CURDIR)/debian/foo/
    chmod -fv -R 755 $(CURDIR)/debian/foo/*

9. Two options:
- a. enter the terminal command: debuild -S
    - it will do everything required to generate the files needed to upload to a Launchpad PPA
- b. enter the terminal command: dpkg-buildpackage -rfakeroot
    - it will do everything required to generate the files needed to upload to a Launchpad PPA, however, it will fail. BUT WILL GENERATE the Deb to my liking
10. Now to upload that package I created from scratch: foo, to Launchpad: dput ppa:<yourppausername>/<yourppaname> /path/to/package/.changes

```


Again, this is what I want. It is possible, but the error I need help on is that extra 'override_dh_auto_install:' command in the debian/rules file I have seems to fail to copy over that 'foo' subfolder I created with the 'foo.sh' script inside. In other words, the actual juice of the package, the script itself, is not getting added, so the resulting deb created (either by Launchpad on Launchpad using the command: debuild -S OR on my computer using the command: dpkg-buildpackage -rfakeroot) does not have the script.

Hopefully that helps some as to what I am talking about.

---

### Post by SevenMachines on 2011-06-10
Unfortunately it all works fine for me with either
```
 $ dpkg-buildpackage -rfakeroot 
```or
```
 $ debuild -b -us -uc
```or even with
```
$ debuild -S
$ pbuilder-dist natty build  foo_0.1~ppa1.dsc
```either way
```
$ dpkg --contents foo_0.1~ppa1_amd64.deb 
drwxr-xr-x root/root         0 2011-06-10 09:30 ./
-rwxr-xr-x root/root         0 2011-06-10 09:29 ./foo.sh
drwxr-xr-x root/root         0 2011-06-10 09:29 ./usr/
drwxr-xr-x root/root         0 2011-06-10 09:29 ./usr/share/
drwxr-xr-x root/root         0 2011-06-10 09:29 ./usr/share/doc/
drwxr-xr-x root/root         0 2011-06-10 09:30 ./usr/share/doc/foo/
-rw-r--r-- root/root      1647 2011-06-10 09:28 ./usr/share/doc/foo/copyright
-rw-r--r-- root/root       141 2011-06-10 09:28 ./usr/share/doc/foo/changelog.gz
-rw-r--r-- root/root       179 2011-06-10 09:28 ./usr/share/doc/foo/README.Debian
```As an side note, since your using debhelper you dont need to override anything in debian/rules to do what you want. debhelper will match binary names in the control file with .install files in the debian directory. In this example you could have a file
debian/foo.install:
```
foo/foo.sh /usr/bin
```This would install to /usr/bin/foo.sh. Or you could have things like
```
foo/ /usr/share
```for instance would install the whole of the foo directory to /usr/share/foo

Do you have a link to the launchpad ppa that you've uploaded to? i cant replicate the problem at all here unfortunately

---

### Post by inameiname on 2011-06-11
Thanks for all of the suggestions, especially the use of a 'foo.install' file instead of tweaking /debian/rules. So far I have been able to successfully upload 8 packages into my PPA: ppa:inameiname/stable. Hopefully my versioning is correct. That is one of the issues I kept having, figuring out how to correctly version. 

Oddly, I have to manually change the versioning, as using dh_make, it always incorrectly gives the package name as:

${PACKAGENAME}-0.2 instead of ${PACKAGENAME}

and  the version number as:

-1ppa1~inameiname1 instead of 0.2-1ppa1~inameiname1

However, there are a few that still don't want to compile and package and fail. I don't really get why as it is the exact same procedures being used, just different files being copied over.

Anyway, here is my method I'm using, which is pretty much the same as before. I threw a simple function together into my 'bashrc' to make it easier to do repeatedly:

```

    1. Ensure I have generated, published, imported, and verified my PPA OpenPGP key
    2. Create a package directory named: ${PACKAGENAME}-${VERSION}~${YOURUNIQUEVERSIONNAME}
    3. Create a subdirectory in the package directory, named: ${PACKAGENAME}
    4. Create subdirectories/files in a subdirect of package direct. (if want /usr/bin/footool, "mkdir usr", "mkdir usr/bin" and "cp footool usr/bin").
       If using a current deb file, just copy all its subdirectories into ${PACKAGENAME}, excluding its DEBIAN subdirectory (leave for later)
    5. Compress the package directory into a tar.gz file, rename it: ${PACKAGENAME}_${VERSION}~${YOURUNIQUEVERSIONNAME}.orig.tar.gz
    6. cd /path/to/package directory
    7. dh_make -n -s -e your@emailaddress.com # this will create the DEBIAN subdirectory for the new deb being made
    8. dpkg-depcheck -d ./configure    # find dependencies, and once found, add to section in subdirectory DEBIAN/control in the package directory
    9. Edit changelog, copyright, control, rules, manpage (if want to adhere to policy, ensure name & email are = what's on record for your gpp key)
       Also be sure to change 'unstable' to the correct '${UBUNTUVERSION}'
       If using a current deb file, ensure the original DEBIAN subdirectory contents are put into the new 'DEBIAN' subdirectory
       If using a current deb file/making your own, create a debian/${PACKAGENAME}.install file, make it executable, and add the following:
        #!/usr/bin/make -f
        # add more lines like below when necessary
        <put_whatever_dirctory(s)_here>/ /
    10. debuild (is a wrapper which approx. equals: dpkg-buildpackage + lintian or linda + debsign) (choose one: 'debuild -S' is Launchpad-friendly)
        debuild # requires sig, builds tar.gz & deb, creates .changes & build files (rejected on Launchpad: must be source only to work)
        debuild -S    # requires sig, builds tar.gz, creates .changes & .build files (accepted on Launchpad: but not perfect)
        debuild -b # requires sig, builds deb, creates .changes & .build files (rejected on Launchpad: missing tar.gz)
        debuild -i -us -uc -S # no sig required, builds tar.gz, creates .changes & .build files (rejected on Launchpad due to missing sig)
        debuild -i -us -uc -b # no sig required, builds deb, creates .changes & .build files (rejected on Launchpad: missing tar.gz/sig.)
        dpkg-buildpackage -rfakeroot # requires sig, builds tar.gz & deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc # no sig required, builds tar.gz & deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -S # requires sign, builds tar.gz, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc -S # no sig required, builds tar.gz, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -b # requires sig, builds deb, creates .changes, no .build (rejected on Launchpad)
        dpkg-buildpackage -rfakeroot -us -uc -b # no sig required, builds deb, creates .changes, no .build (rejected on Launchpad)
        fakeroot debian/rules clean && fakeroot debian/rules binary # builds deb only
        lintian -Ivi ../yourpackage.changes # optional, to check the new deb package
    11. dput ppa:<yourppausername>/<yourppaname> <package.changes>    # optional, to upload to a Launchpad PPA

```Also, 'debuild -S' is still the only one that correctly puts the signature into the file AND results in a successful upload to Launchpad. 'dpkg-buildpackage -rfakeroot' does work in creating a deb on my computer, and signs it, but still won't upload to Launchpad. Not a big deal as the former works; just an observation.

I will continue to experiment, and try and add the remaining debs I have I want to upload to Launchpad.

---

### Post by inameiname on 2011-06-11
Unfortunately I am still having issues uploading a few packages into my PPA. Its actually quite odd how some packages fail, and some don't. I have even tested it with just one file in the package and one time it works, and one time it doesn't. Even odder is I have to check every made deb on Launchpad to make sure everything is there. On a few, like those I've tried below, it might complete successfully, but there are files missing / files not the same size as the originals.

Anyway, I have got it down to just four, though. If you or anybody has any idea how to get these in there, that would be great. I'll attach the three smaller ones of the four (the other (gtk-jzintv) can be found here: [http://gnome-look.org/content/show.php/gtk-jzintv++%28Intellivision+Emulator%29?content=141124]("http://gnome-look.org/content/show.php/gtk-jzintv++%28Intellivision+Emulator%29?content=141124")). And using the method I have done before, it should work, just like all of the others that I've done using that method. I had to tar the original debian files because this site doesn't allow for deb attachments.

---

### Post by inameiname on 2011-06-14
Bump...

I have figured out the trouble I'm having with trying to upload nautilus-kill-thumbs and nautilus-kill-metamac. Using 'debuild -S' to get them ready for upload to the PPA, they are accepted and build correctly. However, when reviewing the actual debs, I noticed the file: /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so (and 'libnautilus-kill-metamac.so' respectively) from the orig.tar.gz are missing in both the tar.gz and the debian file created on Launchpad. Looking into this further, I found the following:

'debuild -S', 'dpkg-buildpackage -rfakeroot -S', and 'debuild -i -us -uc -S' fails to correctly add the '.so' files in their respective folders in the tar.gz/debian files. Thus, its something in the way 'dpkg-buildpackage' builds the new source file, which apparently misses the library files (.so files).

However, 'debuild -b', 'dpkg-buildpackage -rfakeroot -b', and 'debuild -i -us -uc -b' does correctly inside the debian files made. Unfortunately, this command provides no source, which doesn't satisfy the 'source only' requirement to upload to a PPA.

I tried another file just for fun, and found all of the .so library files were missing from it as well, which leaves me to believe those files are having trouble copying over for some reason.

---

### Post by inameiname on 2011-06-18
While this doesn't work for all packages, and I still get some that won't upload, no matter what I do, such as the latest Bleachbit, this is how I fixed those few files:

For nautilus-kill-thumbs and nautilus-kill-metamac, I simply compressed the files: /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so and 'libnautilus-kill-metamac.so' in each and set a postinst script to have it untarred after installed since /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so (and 'libnautilus-kill-metamac.so' respectively) wouldn't go into it. Its very weird way to do it, I know, but it works just fine.

For gtk-jzintv, I got rid of some of the excess stuff inside the original deb (the creator it didn't make it very well, but no big deal), and using the idea from those first two above, compressed the one folder and one 'exe' (which exes were causing errors just like '*.so' files in other two), and used a postinst script to untar them afterwards. Again, good enough.

Finally, for pygtranslator, I realized the original debian package had put the pygtranslator python script inside /usr/local/bin, and when Launchpad tried to remake it on their servers, an error came up because of the folder /usr/local. Therefore, I just changed it to be put in /usr/bin/, just as all the other apps, and that worked just fine. 

Since I figured these out, and sort of have a grasp on this, even though its not 100 percent, I'll mark this as solved.

---

### Post by linuxsalute on 2011-08-19
> **inameiname said:**
> While this doesn't work for all packages, and I still get some that won't upload, no matter what I do, such as the latest Bleachbit, this is how I fixed those few files:

For nautilus-kill-thumbs and nautilus-kill-metamac, I simply compressed the files: /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so and 'libnautilus-kill-metamac.so' in each and set a postinst script to have it untarred after installed since /usr/lib/nautilus/extensions-2.0/libnautilus-kill-thumbs.so (and 'libnautilus-kill-metamac.so' respectively) wouldn't go into it. Its very weird way to do it, I know, but it works just fine.

For gtk-jzintv, I got rid of some of the excess stuff inside the original deb (the creator it didn't make it very well, but no big deal), and using the idea from those first two above, compressed the one folder and one 'exe' (which exes were causing errors just like '*.so' files in other two), and used a postinst script to untar them afterwards. Again, good enough.



Finally, for pygtranslator, I realized the original debian package had put the pygtranslator python script inside /usr/local/bin, and when Launchpad tried to remake it on their servers, an error came up because of the folder /usr/local. Therefore, I just changed it to be put in /usr/bin/, just as all the other apps, and that worked just fine. 

Since I figured these out, and sort of have a grasp on this, even though its not 100 percent, I'll mark this as solved.
Actually - I am the author of GTK-jzintv. Sorry for the sloppiness. I  coded it in about 10 minutes and didn't really think anyone would take  much of an interest or I would have polished it with care. I plan on  developing it again in the near future if people still have a genuine  interest. Also Ubuntu gave me a long hard time trying to get it included  in the repository so that also made me stop. 64 bit will be on the way  soon....

---

### Post by inameiname on 2011-08-20
> **linuxsalute said:**
> Actually - I am the author of GTK-jzintv. Sorry for the sloppiness. I  coded it in about 10 minutes and didn't really think anyone would take  much of an interest or I would have polished it with care. I plan on  developing it again in the near future if people still have a genuine  interest. Also Ubuntu gave me a long hard time trying to get it included  in the repository so that also made me stop. 64 bit will be on the way  soon....

Well, hey, there. It is a nice little app. Thanks. Intellivision was a great system and your program should be there with the rest of the old system emulators in the official repos. :) It is a shame Ubuntu does that. I've ran across others with pretty cool things that Ubuntu ignores until you go through tons of hoops to get it up and all good with them. But I guess that's to be expected, as they don't want to throw up something that might not be stable or safe.

Anyway, it's cool. I can understand a bit of sloppiness. Especially for something that few might actually find really cool. It was just one of those programs I happened to surf about one night when I thought of some classic Intellivision games and was curious if there was an Intellivision emulator for Linux and GTK-jzintv was what came up, And it fits the bill quite well. All I ended up tweaking was to move a few things around here and there so as to have it go into the right Main Menu spot, as well as tweaking the original debian into a way so I can upload it to a PPA for easier distribution to my many machines I support. Nothing very pretty, but it works. Feel free to check that out if you want.

FYI, not only did I add your package to my PPA, but I also threw it up on Gnome-Look as well just for the heck of it. I find that place a great little source for those random packages you cannot find easily elsewhere.

[http://gnome-look.org/content/show.php/gtk-jzintv++%28Intellivision+Emulator%29?content=141124]("http://gnome-look.org/content/show.php/gtk-jzintv++%28Intellivision+Emulator%29?content=141124")


Feel free to let me know if you do get a chance to tweak it and/or update it in the near future. I'll be happy to update your packages in the places I've uploaded them. And if you are interested in spreading it some more, I do have a few other good places in mind that are always looking for those random little packages such as these. 

Thanks again! Especially since now I can easily kick butt on Pole Position, Frogger, and Snafu!

---

