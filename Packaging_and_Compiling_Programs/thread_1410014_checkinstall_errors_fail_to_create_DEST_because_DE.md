---
title: "checkinstall errors: fail to create DEST because DEST doesn't exist?!?"
date: 2010-02-18
forum: Packaging and Compiling Programs
---

### Post by alphaniner on 2010-02-18
I'm trying to compile the latest openbox & lxde on 8.04.  When I get to the checkinstall stage, I get some weird errors.  Two completely different operations (the script **libtool** in the case of openbox, and **cp**ing some icons in the case of lxde) fail, apparently because the *destination* files don't exist.  In both cases, the exact failing command lines are printed out, and if I run them manually, they succeed.  And after this manual intervention, rerunning checkinstall completes successfully and a deb is created.

So I'm looking for any insight into
1) Why these commands fail in the first place.
2) Why files to be included in a deb have to be installed (to the location they would be placed by the deb) before the deb can be created.  Note that the failure is long before the step where the package would be installed, and anyhow I have checkinstall configured to not install, only create the deb.

---

### Post by SevenMachines on 2010-02-20
hi, i can't tell why the commands fail without any more output but it sounds suspiciously like the permissions problem checkinstall can often suffer from. the classic is

$checkinstall 
fails with destination doesnt exist since it tried to create a directory but couldnt because it doesnt have the right permissions

but,

$sudo checkinstall
this succeeds because it has the right to do whatever it wants

you could try sudo'ing it and see if the problems go away

---

### Post by alphaniner on 2010-02-25
FWIW, it was apparently a version issue.  Or that's my best guess, because I had no problems when I **checkinstall**ed the same packages in 9.04.  And I'm fair sure it wasn't a permissions issue, as I've become so inculcated with **sudo** over the years that I often use it when I'm logged in as root or **sudo -i**'d.  Thanks for the response though.

---

