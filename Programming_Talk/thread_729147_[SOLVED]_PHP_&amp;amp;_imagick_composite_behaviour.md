---
title: "[SOLVED] PHP &amp;amp; imagick composite behaviour irratic"
date: 2008-03-19
forum: Programming Talk
---

### Post by TimSC on 2008-03-19
I am doing some picture composition with imagick in PHP. I translate the image before I do the composition. Depending on the amount of translation, I can get the image or the script fails. If I translate +1000 in the horizonal direction I get a valid image. If I translate -1000 units, the script fails and I get a zero size result.

I would expect Imagick to throw an exception if there was a problem rather than just silently failing. Most strange.

I am using Imagick 2.1.1, Ubuntu 7.10, PHP Version 5.2.3, Apache 2.2.4, ImageMagick 6.2.4.

```
<?php 
	//phpinfo();

	//Create a blank blue image
	$image = new Imagick();
	$col = new ImagickPixel();
	$col->setColor  ("blue");
	$image->newImage( 640, 480, $col );
	$image->setImageFormat( 'png' );
	
	//Create a small green image
	$col->setColor  ("green");
	$image2 = new Imagick();
	$image2->newImage( 100, 100, $col );
	$image2->setImageFormat( 'png' );
	
	//Composit green image onto blue image
	$ImagickDraw = new ImagickDraw();
	$ImagickDraw->translate(-1000.0,0.0); //Translation step
	$ImagickDraw->composite(imagick::COMPOSITE_OVER,0,0,-1,-1,$image2);
	$image->drawImage( $ImagickDraw );

	//Output image
	header( "Content-Type: image/{$image->getImageFormat()}" );
	echo $image->getImageBlob( );
?>
```

Any ideas would be appreciated. Even "it works for me" would be helpful at this stage!

As to why I want to translate by -1000, I am doing some map alignment affine transforms and they can be quite complex - this is just a test case.

Regards,

TimSC

---

### Post by lapubell on 2008-03-19
well I have never done what you are doing your way, I usually generate the command line equivalent and do a system($command);.  Then doing the commands one at a time, I can see where the process failed and adjust accordingly.

I'm not a big fan of the php imagemagick plugin.  Sorry.

---

### Post by TimSC on 2008-03-20
I have logged this as a bug of Imagick - I will see if that gets me anywhere.

[http://pecl.php.net/bugs/bug.php?id=13443](http://pecl.php.net/bugs/bug.php?id=13443)

TimSC

---

### Post by TimSC on 2008-03-20
I have bitten the bullet and installed 6.3.9 from source. This fixed
the problem.

Looks like the repo for hardy heron 8.04 beta is still using the broken
version 6.2.4. It would be good to have a more recent imagemagick in 8.04.

TimSC

---

