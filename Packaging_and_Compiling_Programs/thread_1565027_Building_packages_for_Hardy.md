---
title: "Building packages for Hardy"
date: 2010-08-31
forum: Packaging and Compiling Programs
---

### Post by slakkie on 2010-08-31
All,

I have a smallish issue. I'm unable to build packages for Hardy (both binary and source):

```


$ pkg-build-deb hardy
I: Building the build Environment
I: extracting base tarball [/var/cache/pbuilder/hardy-i386-base.tgz]
I: creating local configuration
I: copying local configuration
I: mounting /proc filesystem
I: mounting /dev/pts filesystem
I: Mounting /home/wesleys/sbox/ubuntu/update-manager/hardy
I: Mounting /var/cache/pbuilder/ccache
I: policy-rc.d already exists
I: Obtaining the cached apt archive contents
Reading package lists...
Building dependency tree...
Reading state information...
passwd is already the newest version.
The following extra packages will be installed:
  debootstrap libssl0.9.8 wget
Suggested packages:
  pbuilder-uml
Recommended packages:
  cowdancer devscripts fakeroot sudo
The following NEW packages will be installed:
  debootstrap libssl0.9.8 pbuilder wget
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3342kB of archives.
After this operation, 9802kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libssl0.9.8 wget debootstrap pbuilder
E: There are problems and -y was used without --force-yes
I: Copying back the cached apt archive contents
I: unmounting /var/cache/pbuilder/ccache filesystem
I: unmounting /home/wesleys/sbox/ubuntu/update-manager/hardy filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build/24628 and its subdirectories


# pkg-build-deb is just a shell function I made:
pkg-build-deb () {
        _pkg-build "$1"
}


_pkg-build () {
        local dist="$1"
        shift
        [ -z "$dist" ] && echo "No distro given" && return 1
        if [ ! -e /var/cache/pbuilder/"$dist" ]
        then
                echo "No pbuilder environment for $dist" >&2
                return 1
        fi
        if [ ! -d "./debian" ]
        then
                echo "Unable to find the debian directory in this directory" >&2
                return 1
        fi
        DIST="$dist" pdebuild --use-pdebuild-internal --configfile $HOME/.pbuilderrc "$@" -- --debootstrapopts --keyring=/etc/apt/trusted.gpg
        return $?
}

```

Everything from jaunty upwards (perhaps intrepid as well, but didn't test it) works just fine.

---

### Post by Bachstelze on 2010-08-31
Maybe the signing key for hardy is different? I don't have any problems using

```
sudo DIST=hardy pbuilder build foo.dsc
```

With the .pbuilderrc on [https://wiki.ubuntu.com/PbuilderHowto#Multiple%20pbuilders](https://wiki.ubuntu.com/PbuilderHowto#Multiple%20pbuilders)

---

### Post by slakkie on 2010-08-31
> **Bachstelze said:**
> Maybe the signing key for hardy is different? I don't have any problems using

```
sudo DIST=hardy pbuilder build foo.dsc
```

With the .pbuilderrc on [https://wiki.ubuntu.com/PbuilderHowto#Multiple%20pbuilders](https://wiki.ubuntu.com/PbuilderHowto#Multiple%20pbuilders)

I use the same pbuilderc.. Difference between you and me is that your call differs from mine. I use pdebuilder and you pbuilder.

Get update-manager's source from hardy, cd into the src dir (update-manager-0.xxx.xx) and then run pbuilder (and/or pdebuilder).

I don't get to the part of signing the package..

---

### Post by slakkie on 2010-08-31
I think I solved it.. 

```

sudo pbuilder login  --save-after-login

aptitude install gpgv

```

Now, wait & see :)

And it works.

---

### Post by mathew001 on 2010-08-31
Hi all...
can anyone share the updated version in ubuntu...
Thanks in advance

---

