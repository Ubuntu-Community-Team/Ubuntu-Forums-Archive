---
title: "Building 32bit apps with pbuilder on amd64?"
date: 2006-10-30
forum: Packaging and Compiling Programs
---

### Post by xopher on 2006-10-30
How can I build 32bit apps with pbuilder on amd64? Ive looked at some guides for debian, but if someone could explain it all to me more simple, Id really appreciate it.

I have a running amd64 pbuilder already, which works like a charm.

Thanks!

---

### Post by RAOF on 2006-10-30
Yup.  I've just recently set one up, although that was during Edgy testing (so it might be easier for you ;)).

Basically, the single command you want is 
```
sudo pbuilder create --distribution edgy --debootstrapopts --arch=i386 *any other options*
```

That (eventually) worked for me (Debootstrap had problems downloading all the i386 packages, I don't know why).

---

### Post by xopher on 2006-10-31
Thanks! Ive stumbled upon that cmd a few times, but nice making sure!

Edit; well, having some problems, I guess its my pbuilderrc not being as it should. ](*,)  Could you post yours?

This is mine:

```
## Overrides /etc/pbuilderrc

# Default distribution
DISTRIBUTION=edgy
COMPONENTS="main restricted universe multiverse"

# Repositories
MIRRORSITE=http://fi.archive.ubuntu.com/ubuntu
OTHERMIRROR="deb ${MIRRORSITE} ${DISTRIBUTION}-updates ${COMPONENTS}|deb ${MIRRORSITE} ${DISTRIBUTION}-security ${COMPONENTS}"
#OTHERMIRROR="deb ${MIRRORSITE} ${DISTRIBUTION}-updates ${COMPONENTS}|deb ${MIRRORSITE} ${DISTRIBUTION}-security ${COMPONENTS}"

# For build results

BUILDRESULT=${HOME}/pbuilder/edgy32/result

# Hooks for chroot environment
HOOKDIR=${HOME}/pbuilder/edgy32/hook.d

# Mount directories inside chroot environment
BINDMOUNTS=${BUILDRESULT}

# Bash prompt inside pbuilder
export debian_chroot="pbuild$$"

# For D70results hook
export LOCALREPO=${BUILDRESULT}

# Always include source package
DEBBUILDOPTS="-sa"
```

---

### Post by xopher on 2006-10-31
Oh, and this is the error Im getting:

```
sudo pbuilder32 create --debootstrapopts --arch=i386
W: Build-result Directory /home/xopher/pbuilder/pbuilder32/result does not exist
Distribution is edgy.
Building the build environment
 -> running debootstrap
/usr/sbin/debootstrap
E: No such script: http://fi.archive.ubuntu.com/ubuntu
pbuilder: debootstrap failed
 -> Aborting with an error
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//17046 and its subdirectories

```

---

### Post by xopher on 2006-10-31
And here's my pbuilder32,

```
#!/bin/sh
# script from Jamin W. Collins  BTS: #255165
# name this script 'pbuilder-woody', 'pbuilder-sid', 'pbuilder-sarge' etc.
#
# The script currently contains a minor, but harmless error
# See https://launchpad.net/distros/ubuntu/+source/pbuilder/+bug/57284

OPERATION=$1
DISTRIBUTION=`basename $0 | cut -f2 -d '-'`
PROCEED=false
BASE_DIR="/var/cache/pbuilder"
RESULT_DIR="/home/xopher/pbuilder"
case $OPERATION in
   create|update|build|clean|login|execute )
      PROCEED=true
      ;;
esac
if ( $PROCEED == true ) then
   shift
   sudo /usr/sbin/pbuilder $OPERATION \
      --basetgz $BASE_DIR/$DISTRIBUTION/base.tgz \
      --distribution $DISTRIBUTION \
      --configfile $BASE_DIR/$DISTRIBUTION/pbuilderrc \
      --aptconfdir $BASE_DIR/$DISTRIBUTION/apt.config \
      --buildresult $RESULT_DIR/$DISTRIBUTION/result $@

else
   echo "Invalid command..."
   echo "Valid commands are:"
   echo "   create"
   echo "   update"
   echo "   build"
   echo "   clean"
   echo "   login"
   echo "   execute"
   exit 1
fi

```

---

### Post by xopher on 2006-10-31
Allright, seems like this longsome monolog is getting to an end;

> StevenK xopher: Right, it's pbuilder. --debootstrapopts --arch=i386 won't work, but --debootstrapopts --arch --debootstrapopts i386 will.

creating the base.tgz atm, hope it will work allright ;)

Thanks all!

---

### Post by xopher on 2006-10-31
Allright, works as it should.

Now, is there a way I can use pdebuild for building with my newly created pbuilder32?

Well, Im sure there is, but how do I do it? :)

---

### Post by RAOF on 2006-10-31
Yup.  Well, actually...

What I have is a whole bunch of different pbuilderrc files, which sort the build output into nice informative directories.

So I tend to run things like
```
pdebuild --configfile ~/.pbuilderrc-edgy-i386-multimedia
```

For added bonus marks, you can use a bash alias.  Something like
```

alias pdebuild32='pdebuild --configfile ~/.pbuilderrc-i386'

```

---

### Post by xopher on 2006-11-01
Allright, thanks a million! *off to compiling* -> :cool:

---

