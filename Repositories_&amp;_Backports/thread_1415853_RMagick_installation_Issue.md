---
title: "RMagick installation Issue"
date: 2010-02-25
forum: Repositories &amp; Backports
---

### Post by aliov_85 on 2010-02-25
Hi, I'm trying to install ImageMagick for ruby(RMagick).

When I do: "sudo gem install rmagick", I get the following:

> 
Building native extensions.  This could take a while...
ERROR:  Error installing rmagick:
	ERROR: Failed to build gem native extension.

/usr/bin/ruby1.8 extconf.rb
checking for Ruby version >= 1.8.5... yes
checking for gcc... yes
checking for Magick-config... yes

Warning: Found more than one ImageMagick installation. This could cause problems at runtime.
         /usr/local/bin/Magick-config reports version 6.5.6 Q16 is installed in /usr/local
         /usr/bin/Magick-config reports version 6.5.1 Q16 is installed in /usr
Using 6.5.6 Q16 from /usr/local.

checking for ImageMagick version >= 6.3.5... yes
checking for HDRI disabled version of ImageMagick... yes
checking for stdint.h... yes
checking for sys/types.h... yes
checking for wand/MagickWand.h... no

Can't install RMagick 2.12.2. Can't find MagickWand.h.
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
	--with-opt-dir
	--without-opt-dir
	--with-opt-include
	--without-opt-include=${opt-dir}/include
	--with-opt-lib
	--without-opt-lib=${opt-dir}/lib
	--with-make-prog
	--without-make-prog
	--srcdir=.
	--curdir
	--ruby=/usr/bin/ruby1.8


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/rmagick-2.12.2 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/rmagick-2.12.2/ext/RMagick/gem_make.out


Any Idea?

Best Regards

---

