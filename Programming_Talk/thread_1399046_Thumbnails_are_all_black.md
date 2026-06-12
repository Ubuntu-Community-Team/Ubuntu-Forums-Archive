---
title: "Thumbnails are all black?"
date: 2010-02-05
forum: Programming Talk
---

### Post by PartisanEntity on 2010-02-05
Hi all,

I am in the process of finishing off my final project for my web development course.

I am just about done, but have the following issue:

I have a php script that takes raw pixel data from a Flash movie, and creates a JPEG image.

So far so good, all works, and the images are stored.

But:

I also want to generate thumbnails and have them saved in another folder.

This is where I am having problems. The thumbnails come out completely black:

[PHP]<?php
//get the session id from the flash movie
session_id($_POST['myID']);
session_start();

	//for normal images
	$data = explode(",", $_POST['img']);
	$width = $_POST['width'];
	$height = $_POST['height'];
	$image=imagecreatetruecolor( $width ,$height );
	$background = imagecolorallocate( $image ,0 , 0 , 0 );
	//Copy pixels
	$i = 0;
	for($x=0; $x<=$width; $x++){
		for($y=0; $y<=$height; $y++){
			$int = hexdec($data[$i++]);
			$color = ImageColorAllocate ($image, 0xFF & ($int >> 0x10), 0xFF & ($int >> 0x8), 0xFF & $int);
			imagesetpixel ( $image , $x , $y , $color );
		}
	}
	  
	//generate todays date and time for the filename  
	$today = date("Ymdgi");
	
	//combine date and username
	$filename = $today.'_'.$_SESSION['username'];
	
	//Output image and save it with the filename we generated
	$save = '../images/cars/'.$filename.'.jpeg';
	
	header( "Content-type: image/jpeg" );
	ImageJPEG( $image, $save, 100 );
	
	//clean up
	imagedestroy( $image );
	
	$thumb = '../images/cars/'.$filename.'.jpeg';
	
	$new_thumb = imagecreatefromjpeg($thumb);
	
	//list the width and height and keep the height ratio.

	list($srcwidth, $srcheight) = getimagesize($thumb);
	
	//calculate the new size
	
	$newwidth = $srcwidth / 2;
	
	$newheight = $srcheight / 2;
	
	$new_thumb = imagecreatetruecolor($newwidth,$newheight);
	//$background = imagecolorallocate( $new_thumb ,0 , 0 , 0 );
	//imagefill($new_thumb, 0, 0, $color);
	
	//resizing

	imagecopyresized($new_thumb, $thumb, 0, 0, 0, 0, $newwidth, $newheight, $srcwidth, $srcheight);

	$thumbsave = '../images/cars/thumbs/'.$filename.'.jpeg';
	
	header( "Content-type: image/jpeg" );
	ImageJPEG( $new_thumb, $thumbsave, 100 );
	
	//clean up
	imagedestroy( $new_thumb );

?>

[/PHP]

I have no idea why this is happening, as I find these GD functions somewhat confusing.

Can anyone spot what I am doing wrong?

Thanks very much, if it helps, I have attached what a proper image looks like after being saved, and whats happening to the thumbnails.

---

### Post by Linteg on 2010-02-05
Well, you are trying to resize a string ($thumb) and store it as an image ($new_thumb).
Take a look at the [php manual entry for imagecopyresized]("http://php.net/manual/en/function.imagecopyresized.php").

---

