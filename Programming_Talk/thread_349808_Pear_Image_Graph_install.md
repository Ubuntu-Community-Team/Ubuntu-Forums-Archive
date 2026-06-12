---
title: "Pear Image_Graph install"
date: 2007-01-30
forum: Programming Talk
---

### Post by braddcadd on 2007-01-30
Can anyone help me installing the pear::Image_Graph module?  I installed it through Synaptic.  I also have the Ubuntu Pear package installed.

When I make the following call (after I include Graph.php correctly):
```
$Graph =& Image_Graph::factory('graph', array(400, 300)); 
``` 

I get the following when brosing localhost:
```

Warning: main(Image/Color.php): failed to open stream: No such file or directory in /usr/share/php/Image/Canvas/Color.php on line 33

Fatal error: main(): Failed opening required 'Image/Color.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/php/Image/Canvas/Color.php on line 33

```

But I've checked this location and find the files in place.  I even chmod 777 all files in the webserver and /usr/share/php/Image/Canvas/ to now avail.

Thanks for any help.

---

### Post by braddcadd on 2007-01-30
Well I gave up on pear.  Now I am trying to get phplot working.  I installed libphp-phplot from the Ubuntu packages.  But it requires GD to be working.  I checked phpinfo() and GD (evidently) is not working on my machine.

The best advice I have right now is the following fron php.net:
> 
To enable GD-support configure PHP --with-gd[=DIR], where DIR is the GD base install directory. To use the recommended bundled version of the GD library (which was first bundled in PHP 4.3.0), use the configure option --with-gd. GD library requires libpng and libjpeg to compile.


Chime in if anyone can help me "configure PHP --with-gd[=DIR]".  I am at a loss.  Is this in the apache2.conf file?

---

### Post by apoth on 2007-04-18
Probably too late for you, but I had the same issue with Image_Graph. I had to do two things:

1. Download [Image_Color from the pear website](http://download.pear.php.net/package/Image_Color-1.0.2.tgz) and extract it to an Image folder in /usr/share/php/Image/Canvas. That got me past the first error, which you had.

2. Create a Fonts directory in /usr/share/php/Image/Canvas and copy into it /var/lib/defoma/fontconfig.d/B/Bitstream-Vera-Sans-Mono.ttf and then declare I was using that font as

```
$Font =& $Graph->addNew('font', 'Bitstream-Vera-Sans-Mono');
```

---

### Post by lightstream on 2008-02-13
Thanks apoth for posting that, it got me up and running with Image_Graph =D

Oh... I also ran into a problem with ImageAntialias function (or however it's cased) not existing; it seems it is only available with some versions of GD. I'm pretty sure I installed my GD using **apt-get install php5-gd**. You can edit the PEAR files to wrap any calls to this function in a function_exists() check, according to [this bug report]("http://pear.php.net/bugs/bug.php?id=8776") (which worked for me, obviously).

---

