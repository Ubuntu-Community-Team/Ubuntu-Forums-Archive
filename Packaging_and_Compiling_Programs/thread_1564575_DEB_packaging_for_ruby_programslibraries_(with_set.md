---
title: "DEB packaging for ruby programs/libraries (with setup.rb)."
date: 2010-08-30
forum: Packaging and Compiling Programs
---

### Post by dv3500ea on 2010-08-30
I am trying to learn how to package ruby programs for Debian/Ubuntu.

I found out that the best way to do this is to use [ruby-pkg-tools]("http://pkg-ruby-extras.alioth.debian.org/ruby-pkg-tools/index.html") and [setup.rb]("http://proutils.github.com/setup/").

To test this out, I created a simple 'hello world' program in ruby, using the setup.rb structure. I checked that it installed and ran ok using the setup.rb installer ```
sudo ruby setup.rb install
```.

I then used dh_make to set up the debian directory with all of its control files: ```
dh_make -c gpl -s -b -p hello-ruby_1.0 -f ../hello-ruby_1.0.tar.gz
```. I edited the control files to fill in all of the metadata and edited debian/rules to:
```

#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/ruby-pkg-tools/1/class/ruby-setup-rb.mk

```
as explained [here]("http://pkg-ruby-extras.alioth.debian.org/ruby-pkg-tools/cdbs.html").

I then built the source and .deb packages using debuild:
```
debuild -us -uc
```

This created the packages but lintian gave a warning: 'empty-binary-package'. The .deb file had all of the correct metadata but none of the actual program data (there should have been 1 ruby library, 1 executable ruby program in /usr/bin and 1 man page).

Does anyone know what I'm doing wrong here? (I think I have written the debian/rules file wrong but I don't know how).

---

### Post by dv3500ea on 2010-09-02
bump.

---

### Post by SevenMachines on 2010-09-03
hi, i get no installed files too unless theres a versioned package too, ths may be your problem but you'd need to post control/rules files. 

debian/control:
> Source: hello-ruby
Section: unknown
Priority: extra
Maintainer: SevenMachines <SevenMachines@yahoo.co.uk>
Build-Depends: cdbs, debhelper (>= 7.0.50~)
Build-Depends-Indep: ruby-pkg-tools (>= 0.8), ruby1.8
Standards-Version: 3.8.4

Package: hello-ruby
Architecture: any
Depends: hello-ruby1.8
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>

Package: hello-ruby1.8
Architecture: any
Depends: ruby
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>

Note that there is now two packages, a 'dummy' package hello-ruby that has a dependency on a ruby-versioned package hello-ruby1.8. Maybe the ruby-pkg-tools cdbs stuff is very keen on versioning?

debian/rules:
> #!/usr/bin/make -f

include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/ruby-pkg-tools/1/class/ruby-setup-rb.mk


---

### Post by SevenMachines on 2010-09-03
I'm guessing ruby-pkg-tools strictly follows debian policy, wish it plopped out a warning though, its like staring at a blank wall :)
See [URL="http://pkg-ruby.alioth.debian.org/ruby-policy.html/"]Debian Ruby Policy
[/URL]
> **2.1 Module Package Names**

   Ruby module packages should be named for the primary module provided.  The naming convention for a module foo is libfoo-rubyX.Y for the package for the Ruby version X.Y.  
 Package that includes foo modules in /usr/lib/ruby/X.Y/ must be named as libfoo-rubyX.Y.  
 Since we don't have version independent module path ([Module Path, Section 1.6]("http://pkg-ruby.alioth.debian.org/ruby-policy.html/ch-ruby.html#s-paths")), you must package ruby modules for each ruby version even if the module is really version independent.  So, your choice is (1) package only for default version of ruby, or (2) package for each available versions of ruby.  XXX: We don't recommend that libfoo-ruby contains files for all available versions of ruby.  
 The package name libfoo-ruby should be used for a dummy package that depends on libfoo-rubyX.Y that is packaged for default version of ruby X.Y.  By using such a dummy package, user can easily follow upgrading.  


---

### Post by dv3500ea on 2010-09-03
Thanks, that works!

I knew there was something really simple I was missing. I hadn't split the package into a dummy and a version specific package, but once I did, it worked perfectly.

I'm glad I can finally package ruby programs and libraries after such an uphill struggle due to the sparse documentation (I intend to fix this by writing a HOWTO at some point).

---

### Post by SevenMachines on 2010-09-03
A howto may be a very good idea, both me and you didnt find it easily obvious so i imagine many others have/will have the same problem. There doesnt seem to be a wealth of documentation on this either, or i didnt find it anyway, the cdbs docs on ruby packaging with ruby-pkg-tools are pretty slight too

---

