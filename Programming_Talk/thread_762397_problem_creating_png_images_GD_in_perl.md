---
title: "problem creating png images GD in perl"
date: 2008-04-22
forum: Programming Talk
---

### Post by diamantis13 on 2008-04-22
Hi!
I have Ubuntu 7.04, and I was trying to run a perl script that uses GD.pm. I re-installed a bunch of required packages (jpg,freetype,libpng etc) but I always get the error:
Can't locate object method "png" via package "GD::Image"
The script I am using is from GD's example:
           use GD;

           # create a new image
           $im = new GD::Image(100,100);

           # allocate some colors
           $white = $im->colorAllocate(255,255,255);
           $black = $im->colorAllocate(0,0,0);
           $red = $im->colorAllocate(255,0,0);
           $blue = $im->colorAllocate(0,0,255);

          # Put a black frame around the picture
           $im->rectangle(0,0,99,99,$black);


           # Draw a blue oval
           $im->arc(50,50,95,75,0,360,$blue);

           # And fill it with red
           $im->fill(50,50,$red);

           # make sure we are writing to a binary stream
           binmode STDOUT;

           # Convert the image to PNG and print it on standard output
           print $im->png;

---

### Post by Zugzwang on 2008-04-22
[http://www.google.de/url?sa=t&ct=res&cd=6&url=http%3A%2F%2Fgroups.google.com%2Fgroup%2Fperl.beginners%2Fbrowse_thread%2Fthread%2F4336073ff6f280f3&ei=QfANSJTtCIKW-AKaxdmJDA&usg=AFQjCNGtpMtA25tQJd0R-XnKcTfvxT0wzg&sig2=S9EGomfJxGwgq3R-W2zA6Q]("http://www.google.de/url?sa=t&ct=res&cd=6&url=http%3A%2F%2Fgroups.google.com%2Fgroup%2Fperl.beginners%2Fbrowse_thread%2Fthread%2F4336073ff6f280f3&ei=QfANSJTtCIKW-AKaxdmJDA&usg=AFQjCNGtpMtA25tQJd0R-XnKcTfvxT0wzg&sig2=S9EGomfJxGwgq3R-W2zA6Q")

---

